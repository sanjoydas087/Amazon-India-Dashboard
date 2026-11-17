# Amazon India Management Dashboard (Excel)
 
An interactive, app-style Excel dashboard built from **10,000 Amazon India orders** for a non-technical manager. Every number, chart, insight and answer is a live formula that reads the raw data, so the whole workbook updates when the data or the Year filter changes.
 
> Built as a data analyst portfolio project based on the **Sapphire IQ** brief (requested by Manoj for Ravi, the manager).
 
---
 
## Business problem
 
Ravi needs to know, without reading formulas or raw tables:
 
- How are sales and profit performing over time?
- Which categories and products drive the business, and which lose money?
- How much revenue is lost to returns and cancellations?
- Which payment methods, fulfilment channels and states matter most?
- Where are sales heading in the next 3 to 6 months, and how far can the forecast be trusted?
- Where exactly is the problem, how much money is at risk, and what should be done first?
---
 
## Dataset
 
| Item | Detail |
| --- | --- |
| Rows | 10,000 orders |
| Period | 01 Jan 2024 to 30 Aug 2026 |
| Columns | 13: Order_ID, Order_Date, Category, Product, Quantity, Unit_Price_INR, Discount_Pct, Total_Sales_INR, Profit_INR, Payment_Method, Fulfillment, Order_Status, Ship_State |
| Order status | Delivered, Shipped, Returned, Cancelled |
 
Headline result (all years): **total sales Rs 1,557.9 lakh**, **net profit margin about 23.7%** (profit divided by net sales).
 
---
 
## What is inside the workbook
 
| Sheet | What it does |
| --- | --- |
| **Dashboard** | One sheet, 7 pages, one frozen menu bar, one Year dropdown (cell R2). Tiles, 17 charts, tables, insights |
| **Problems_Actions** | Problem map, ranked priorities, editable management targets, 19-problem register (what happened, why, what to do), 100% brief coverage check |
| **QnA_75** | 75 questions and live answers (15 per section) with a PROBLEM / WATCH / OK / INFO status |
| **Calc** | The calculation engine: KPIs, auto-extracted lists, monthly trend, forecast engine, what-if, data checks |
| **Data** | The raw 10,000 orders |
| **Notes** | Definitions, assumptions and limits |
 
### The 7 dashboard pages
 
1. **Overall Sales and Profit**: total sales, profit, orders, units, average order value, margin, monthly trend, year-wise bars
2. **Category and Products**: category sales, profit and units, Top 10 products, lowest-margin products
3. **Order Status and Loss**: delivered, shipped, returned, cancelled, return and cancellation rates, revenue lost, category hot spots
4. **Payment and Geography**: payment method, fulfilment method and state performance
5. **Outlook and Forecast**: data cut-off, method comparison, backtests, gross vs net forecast, expected profit, what-if
6. **Insights and Actions**: auto-written insights and 3 recommended actions
7. **Diagnostic Q&A**: 15 questions, each answered as *what happened, why, what to do*
---
 
## Key features
 
- **Fully dynamic.** Dropdown year filter; every KPI, table, chart and sentence is a formula. No hard-coded results.
- **Auto-extracted lists.** Categories, products, payment methods, fulfilment methods and states are pulled from the data with array formulas, so new values appear by themselves.
- **Forecast with proof.** Compares three methods (**ETS**, **seasonal naive**, **3-month moving average**) on 14 backtests (6 fixed origin and 8 rolling origin) using MAPE, MAE, bias and RMSE. The best method is chosen automatically and shown with a roughly 90% range.
- **Data cut-off rule.** If the last month has under 90% of its days, it is excluded from training so a partial month never looks like a sales drop.
- **Gross vs net.** Forecasts both gross sales (every order placed) and net sales (Delivered + Shipped only), plus expected profit.
- **Problem register.** 19 business checks against editable targets, with severity (HIGH / MEDIUM / LOW) and profit at risk. Overlapping problems are not counted twice.
- **Built-in data checks.** Eight reconciliation checks confirm every table adds up to the total sales.
- **What-if.** Type a percentage cut in lost orders and see recovered revenue and extra profit.
---
 
## Key definitions
 
| Term | Meaning |
| --- | --- |
| Total Sales (gross) | Sum of Total_Sales_INR for all orders placed |
| Net Sales | Total_Sales_INR of Delivered + Shipped orders |
| Profit Margin % | Profit divided by Net Sales (returned and cancelled orders carry zero profit) |
| Revenue lost | Total_Sales_INR of Returned + Cancelled orders |
| Rs lakh | Rupees divided by 100,000 |
 
---
 
## How to use
 
1. Download `Amazon_India_Dashboard_App.xlsx` and open it in **Microsoft Excel 2016 or newer** (Excel 365 is best, because the forecast uses `FORECAST.ETS`).
2. Enable editing and let the workbook calculate.
3. Use the **menu bar in row 3** of the Dashboard to jump between pages.
4. Use the **Year dropdown (cell R2)** to filter pages 1 to 4. The monthly trend, year table and forecast always use all years by design.
5. Open **Problems_Actions** to see which problems are active and how much profit is at risk. Change the blue target cells (D30 to D43) to test other limits.
6. Open **QnA_75** and filter the Status column to PROBLEM or WATCH.
To use your own data, paste it into the **Data** sheet from cell A1 using the same 13 columns (up to row 20,000). The named ranges are already set up.
 
---
 
## How it works
 
```text
Data sheet  ->  named ranges (d_sales, d_status, d_date ...)
            ->  Calc sheet (SUMIFS / COUNTIFS / INDEX-MATCH / FORECAST.ETS)
            ->  Dashboard, Problems_Actions, QnA_75 (display only, no calculations)
```
 
Only the Data sheet, the Year dropdown, the what-if cell and the target cells hold typed values. Everything else is a formula.
 
---
 
## Tools and skills shown
 
- Microsoft Excel: named ranges, SUMIFS, COUNTIFS, AVERAGEIFS, INDEX/MATCH, RANK, SUMPRODUCT, array formulas, FORECAST.ETS, HYPERLINK, data validation, conditional formatting, charts
- Time-series forecasting and backtesting (MAPE, MAE, bias, RMSE)
- KPI design, dashboard layout for non-technical users, business storytelling
- Data validation and reconciliation checks
---
 
## Known limitations
 
- Excel cannot hide the other dashboard pages when a menu item is clicked without a macro, so the menu **scrolls** to the page. An optional macro for page hiding was prepared but is untested.
- Targets in Problems_Actions are common-sense defaults, not company rules. Replace them with real limits.
- Profit at risk figures are simple estimates, not forecasts.
- The forecast is only as reliable as its backtest error (MAPE) shown on page 5.
---
 
## Repository contents
 
```text
.
|-- Amazon_India_Dashboard_App.xlsx   # the dashboard workbook
|-- README.md
`-- docs/                             # optional: screenshots and the build guide
```
 
Add screenshots of each dashboard page to `docs/` and link them here, for example:
 
```markdown
![Overview](docs/page1_overview.png)
```
 
---
 
## Author
 
**Sanjoy Das**
Fresher Data Analyst | Kolkata, India
B.E. in Electrical Engineering, Jadavpur University | BEE Certified Energy Auditor
Data analyst internships: InlignX Global Pvt. Ltd. and Unified Mentor Pvt. Ltd.
 
Connect: [LinkedIn](https://www.linkedin.com/) | [GitHub](https://github.com/)
 
*(Replace the two links above with your own profile URLs.)*
