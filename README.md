# Amazon-India-Sales-Dashboard-Power-BI
# 📊 Amazon India Sales Dashboard — Power BI

A 3-page interactive Power BI dashboard analyzing **120K+ orders** and **₹78.59M in revenue** from Amazon India (Apr–Jun 2022).

---

## 🖼️ Dashboard Preview

### Page 1 — Sales Performance
![Sales Performance Dashboard]
(<img width="1367" height="770" alt="Screenshot 2026-06-08 004350" src="https://github.com/user-attachments/assets/6b88f264-bd62-4653-8fd5-225c43fc31a7" />
)

### Page 2 — Product Analysis
![Product Analysis Dashboard]
(<img width="1363" height="772" alt="Screenshot 2026-06-08 004459" src="https://github.com/user-attachments/assets/175fd9af-c07c-403d-98e2-3ccec7aa1815" />
)

### Page 3 — Regional Analysis
![Regional Analysis Dashboard]
(<img width="1365" height="766" alt="Screenshot 2026-06-08 004554" src="https://github.com/user-attachments/assets/58c1d419-9616-4a4a-962b-5140231629cc" />
)

---



---

## 📌 Key Insights

| Metric | Value |
|--------|-------|
| Total Revenue | ₹78.59M |
| Total Orders | 120,378 |
| Avg Order Value | ₹652.88 |
| Cancellation Rate | 14.2% |
| Top State | Maharashtra (₹13.3M) |
| Top Category | Set (50% of revenue) |
| Peak Month | April 2022 (₹28.8M) |
| Amazon Fulfilled | 69.1% of orders |

---

## 📁 Dataset

| File | Description | Rows |
|------|-------------|------|
| `Amazon_Sale_Report.csv` | Main orders data — status, category, state, B2B flag | 128,975 |
| `International_sale_Report.csv` | Overseas customer sales | ~37K |
| `Sale_Report.csv` | SKU-level stock inventory | ~9K |
| `May-2022.csv` | Platform-wise pricing (Amazon, Flipkart, Myntra etc.) | — |
| `P__L_March_2021.csv` | MRP vs Transfer Price — margin analysis | — |
| `Expense_IIGF.csv` | Business expense tracker | — |
| `Cloud_Warehouse_Compersion_Chart.csv` | Shiprocket vs Increff warehouse cost comparison | — |

> ⚠️ Raw data files are not included in this repo due to size. The dataset is available on [Kaggle](https://www.kaggle.com/).

---

## 🛠️ Tools & Skills Used

- **Power BI Desktop** — report building, visuals, slicers
- **Power Query (M)** — data cleaning, date parsing, custom columns
- **DAX** — calculated measures (KPIs, rates, CALCULATE, DIVIDE)
- **Data Modeling** — table relationships via SKU key
- **Excel / CSV** — raw data source

---

## 📐 Dashboard Pages

### Page 1 — Sales Performance
- 5 KPI cards: Revenue, Orders, Qty Sold, Avg Order Value, Cancelled Orders
- Sales Trend Over Time (daily line chart)
- Top 10 States by Revenue (bar chart)
- Sales by Category (bar chart)
- Order Status Distribution (donut chart)
- World map — order locations
- Slicers: Date range, Category, State

### Page 2 — Product Analysis
- 4 KPI cards: Categories, SKUs, Qty Sold, Revenue
- Category Contribution Treemap
- Top 10 Products by Revenue (SKU level)
- Sales by Product Size (bar chart)
- Sales by Style (bar chart)
- Product Performance Detail Table (Category × Qty × Revenue)

### Page 3 — Regional Analysis
- 4 KPI cards: States (48), Cities (7K), Orders, Revenue
- State Wise Revenue Map
- Top 10 States by Revenue (bar chart)
- Top 10 Cities by Revenue (bar chart)
- State Wise Performance Table (drill-down)
- Slicers: Date, State, City

---

## 🧮 DAX Measures

```dax
Total Revenue = SUM(Amazon_Sale_Report[Amount])

Total Orders = COUNTROWS(Amazon_Sale_Report)

Cancelled Orders = 
CALCULATE(
    COUNTROWS(Amazon_Sale_Report),
    Amazon_Sale_Report[Status] = "Cancelled"
)

Cancel Rate = DIVIDE([Cancelled Orders], [Total Orders])

Avg Order Value = DIVIDE([Total Revenue], [Total Orders])

B2B Revenue = 
CALCULATE(
    [Total Revenue],
    Amazon_Sale_Report[B2B] = TRUE
)

Amazon Fulfilled % = 
DIVIDE(
    CALCULATE([Total Orders], Amazon_Sale_Report[Fulfilment] = "Amazon"),
    [Total Orders]
)
```

---

## 🔧 Power Query Steps Applied

1. Changed `Date` column type → Date (MM-DD-YY format)
2. Removed junk columns (`Unnamed: 22`, `promotion-ids`, `index`)
3. Standardized `ship-state` → UPPERCASE for consistent mapping
4. Added custom `MonthYear` column → `Date.ToText([Date], "MMM-YY")`
5. Added `MonthNum` column → `Date.Month([Date])` for correct sort order
6. Removed blank rows from `Amount` column

---

## 📂 Repo Structure

```
amazon-india-sales-dashboard/
│
├── README.md
├── screenshots/
│   ├── page1_sales_performance.png
│   ├── page2_product_analysis.png
│   └── page3_regional_analysis.png
│
└── Amazon_Sales_Dashboard.pbix   ← (optional, upload if under 100MB)
```

---

## 👤 Author

**Rahul Chauhan**  
B.Sc. Data Science | Aspiring Data Analyst  
📍 Mumbai, India

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](www.linkedin.com/in/rahul-chauhan-8b82012b1)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-black?logo=github)](https://github.com/rcrahul0001-web)

---

## 📜 License

This project is for educational/portfolio purposes. Dataset credits to original source.
