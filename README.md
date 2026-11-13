# Supply Chain Logistics Analytics Dashboard (Excel)

**By MD. Sakib Al Hasan** · [Portfolio](https://sakibzzz641.github.io) · [GitHub](https://github.com/sakibzzz641) · [LinkedIn](https://www.linkedin.com/in/sakibzzz641)

---

![Excel](https://img.shields.io/badge/Excel-Dashboard-217346) ![Power Query](https://img.shields.io/badge/Power%20Query-Data%20Cleaning-F2C811) ![PivotTables](https://img.shields.io/badge/PivotTables-Slicers-217346) ![VBA](https://img.shields.io/badge/VBA-Dashboard%20Buttons-5C2D91) ![Data](https://img.shields.io/badge/Data-Supply%20Chain%20Logistics-1F4E79) ![License](https://img.shields.io/badge/License-MIT-green)

## Summary

I turned **9,215 supply-chain orders** (29.5M units, 1,540 freight rates, 19 plants) into a **7-page interactive Excel dashboard** that answers questions about orders, products, customers, freight cost, warehouses and delivery risk.

[![Overview Dashboard](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/2_overview.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/2_overview.png)

### 🎥 Video Walkthrough

[![Watch the walkthrough on YouTube](https://img.shields.io/badge/%E2%96%B6%20Watch%20the%20Walkthrough-YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](YOUR_VIDEO_LINK)

- **Dataset:** Supply-chain logistics case data with 7 tables (US$15.6M warehouse cost)
- **Type of analysis:** Descriptive + diagnostic operations and risk analysis
- **Tools:** Power Query, PivotTables, PivotCharts, slicers, and short VBA macros for the dashboard buttons

**What I built**

- **Overview:** 8 KPIs and a business-at-a-glance view of plants, carriers, ports and cost
- **Orders:** volume, late-order rate, and transit time by carrier
- **Products and Customers:** top products, plant coverage and customer concentration
- **Freight:** rate per kg by weight, carrier and service, plus transit time
- **Warehouses:** cost per unit, daily capacity and VMI links by plant
- **Key Takeaways:** 8 insight cards that write the finding and a recommended action from the live data

Every analysis page has its own slicers, so the numbers and charts update together. Header buttons let you fit the dashboard to the screen, refresh the data and exit full screen.

**Key insights**

- **98%** of orders ship from one port (PORT04)
- **97%** of units ship from one plant (PLANT03), which also carries about **95%** of warehouse cost
- The **top 10 customers place 68%** of all orders
- The busiest carrier (V444_0, 68% of orders) is also the **least reliable** (2.9% late)

**Biggest lesson:** a good dashboard does not show more charts, it shows the one risk a manager needs to act on first.

No coding needed to use it: open the file, click a slicer, and every KPI and chart on that page updates.

---

## Table of Contents

01. [Business Problem](#business-problem)
02. [Dataset](#dataset)
03. [Dashboard Pages](#dashboard-pages)
04. [Key Insights](#key-insights)
05. [Recommendations](#recommendations)
06. [How I Built It](#how-i-built-it)
07. [Dashboard Buttons (VBA)](#dashboard-buttons-vba)
08. [How to Use](#how-to-use)
09. [Repository Structure](#repository-structure)
10. [Skills Demonstrated](#skills-demonstrated)
11. [What I Learned](#what-i-learned)
12. [Future Improvements](#future-improvements)
13. [Author](#author)

---

## Business Problem

A supply-chain team ships products from plants through ports to customers using several carriers and service levels. The data sits in seven separate tables, so management struggles to answer questions like:

- How many orders do we ship, and how many arrive late?
- Which ports, plants and customers do we depend on too much?
- Which carriers are slow, late or expensive?
- How does freight cost change with shipment weight?
- What do warehouses cost, and how much capacity do plants have?

This dashboard answers these questions with one page per topic, filters for plant, port, carrier, service level, customer and product, and a Key Takeaways page that says what to do next.

---

## Dataset

- **Source:** supply-chain logistics case workbook (raw file in `Raw_Data/`)
- **Tables:** orders, freight rates, warehouse costs, warehouse capacities, products per plant, VMI customers, plant ports
- **Size:** 9,215 orders, 2,035 plant–product links (1,540 unique product IDs), 19 plants, 1,540 freight rate slabs
- **Main fields:** Order ID, Origin Port, Carrier, Service Level, Plant Code, Customer, Product ID, Unit quantity, Weight, Ship-ahead and Ship-late days, Rate, Mode, Transit days

| Metric                  | Value        |
|-------------------------|--------------|
| Orders                  | 9,215        |
| Units shipped           | 29,513,315   |
| Total weight            | 183,118 kg   |
| Avg units per order     | 3,203        |
| Avg weight per order    | 19.9 kg      |
| On-time orders          | 97.9%        |
| Late orders             | 2.1%         |
| Avg ship-ahead days     | 1.9          |
| Avg transport time      | 1.7 days     |
| Warehouse cost          | $15,633,222  |
| Avg freight rate        | $2.89        |

**Data notes**

- All orders share a single order date (26 May 2013), so the data has no time trend. Analysis is by plant, port, carrier, customer and product instead.
- All 9,215 orders are Non-VMI, so the VMI order share is 0% and the VMI-type chart on the Customers page has only one value.
- One row in the plant–product table has an unknown plant code (`CND9`) that matches none of the 19 plants. It is a source data error and is left out of the counts.

---

## Dashboard Pages

All pages share one sidebar, one layout and one colour theme. Each analysis page has a KPI strip, six charts and a slicer panel.

### 1. Overview

Business performance at a glance.

- 8 KPI cards: orders, units, weight, avg weight per order, ship-ahead days, late %, warehouse cost, transit days
- Orders by plant and by carrier
- Service level share (donut)
- Units by origin port, orders by weight slab, warehouse cost by plant

[![Overview](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/2_overview.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/2_overview.png)

### 2. Orders

Volume, carriers and delivery timing.

- KPIs: orders, ship-ahead and ship-late days, late %, on-time %, transit days
- Orders by origin port and weight slab (Pareto charts)
- Late order % by carrier
- Transit time by carrier and ship-ahead days by service level

[![Orders](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/1_orders.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/1_orders.png)

### 3. Products

Product mix and plant coverage.

- Top 10 products by units, weight and orders
- Units by plant (Pareto)
- Units by service level
- Average units per order by plant

[![Products](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/3_products.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/3_products.png)

### 4. Customers

Who orders and how concentrated it is.

- Top 10 customers by orders, units and weight
- Orders by weight slab
- Orders by plant and VMI type (all orders are Non-VMI in this data)
- Average order size of the top customers

[![Customers](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/4_customers.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/4_customers.png)

### 5. Freight

Rates, lanes and transit time.

- KPIs: 1,540 rate slabs, average, lowest and highest rate, minimum charge, transit days
- Average rate by weight slab and by carrier
- Rate slabs by mode (air vs ground)
- Minimum charge by origin port, transit days by carrier, rate by service code and mode

[![Freight](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/5_freight.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/5_freight.png)

### 6. Warehouses

Plant cost and capacity.

- KPIs: 19 active plants, 5,791 daily capacity, $0.72 average cost per unit, 2,035 plant–product links, 14 VMI links
- Cost per unit and daily capacity by plant
- Orders and products per plant
- Plants by cost band and VMI links by plant

[![Warehouses](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/6_warehouses.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/6_warehouses.png)

### 7. Key Takeaways

What the data says and what to do about it.

- 6 headline KPIs and 8 insight cards
- Each card shows a big number, a headline, a short explanation and a recommended action
- Risk cards turn maroon, and the text follows the slicers on the other pages

[![Key Takeaways](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/raw/main/Dashboard_Screenshots/7_key_takeaways.png)](https://github.com/sakibzzz641/Supply_Chain_Logistics_Analytics_Dashboard_Excel_and_VBA/blob/main/Dashboard_Screenshots/7_key_takeaways.png)

Every analysis page has its own slicers in the right-hand panel (8 on five pages, 5 on Warehouses).

---

## Key Insights

**1. Everything runs through one port.** PORT04 handles 98% of orders and 99% of units.

| Origin port | Orders | Units       |
|-------------|--------|-------------|
| PORT04      | 9,041  | 29,267,834  |
| PORT09      | 173    | 245,133     |
| PORT05      | 1      | 348         |

**2. One plant carries the business and the cost.** PLANT03 ships 97% of units, handles 8,541 of 9,215 orders (93%) and accounts for $14.8M of the $15.6M warehouse cost (95%). It also covers 781 of the 2,035 plant–product links (38%). Only 7 plants show orders on the Overview page, even though 19 plants are active.

**3. A few customers place most orders.** The top customer places 976 orders (10.6%), and the top 10 customers together place 68%. The top customer by orders is not the top customer by units, so account priority depends on the measure used.

**4. The busiest carrier is the least reliable.**

| Carrier | Orders | Late orders | Avg transport days |
|---------|--------|-------------|--------------------|
| V444_0  | 6,264  | 2.9%        | 2.0                |
| V444_1  | 2,097  | 0.4%        | 1.05               |
| V44_3   | 854    | 0.0%        | 1.29               |

**5. Freight rate depends heavily on weight.** The cheapest band is 100+ kg and the most expensive is 50-100 kg.

| Weight band | Avg rate per kg |
|-------------|-----------------|
| 0-5 kg      | $2.69           |
| 5-10 kg     | $1.29           |
| 10-20 kg    | $1.82           |
| 20-30 kg    | $2.36           |
| 30-50 kg    | $3.77           |
| 50-100 kg   | $5.42           |
| 100+ kg     | $0.13           |

**6. Two carriers look like outliers.** V444_7 charges $128.03/kg (87x the $1.47 median) and V444_9 takes 14.0 days (7x the 2.0-day median).

**7. Service mix is heavily skewed.** DTP carries 78% of units, CRF 13% and DTD 9%. About 85% of orders weigh under 25 kg.

---

## Recommendations

- **Build a fallback port.** With 98% of orders on PORT04, any disruption stops almost everything.
- **Line up a backup plant for key products.** Check capacity at PLANT03 and review idle plants such as PLANT01 (220 products, no orders in this data).
- **Agree service levels with the top 10 customers** and watch their late rate closely.
- **Review the carrier V444_0 SLA.** It moves 68% of orders, so even a small late rate matters. Shift volume if the gap stays.
- **Check carrier V444_7 before using it.** A rate 87x the median is either a premium service or a data error.
- **Consolidate shipments into heavier weight bands** where the rate per kg is much lower.

---

## How I Built It

1. **Loaded and cleaned the data with Power Query**
   - Loaded each of the 7 sheets as its own query so the model refreshes in one click
   - Checked data types, blanks, duplicates and key matches before building anything
   - Added two helper fields: an **order weight slab** (0-25, 25-50, 50-100, 100-200, 200+ kg) and a **freight weight band** (0-5, 5-10, 10-20, 20-30, 30-50, 50-100, 100+ kg)
2. **Built PivotTables** (one per chart) and **PivotCharts**, with real Top 10 filters and sorted rankings.
3. **Chose chart types to fit the data:** horizontal bars for long IDs, Pareto charts for concentration, lollipop charts with a log scale for outliers, a line for ordered weight bands and donuts for shares.
4. **Added slicers** to every analysis page and connected them to that page's PivotTables.
5. **Designed the layout:** sidebar navigation, KPI cards, a 3 x 2 chart grid, a slicer panel and one teal, maroon and cream colour theme.
6. **Audited the dashboard** and fixed what was hard to read: hidden slicer filters, single-value charts and outlier-flattened axes.
7. **Added the Key Takeaways page** with shares, medians and ratios that turn into plain-language findings and actions.
8. **Added the dashboard buttons** (see below).

---

## Dashboard Buttons (VBA)

Five short VBA macros power the buttons, so the file is saved as **.xlsm**.

| Button            | What it does                                              |
|-------------------|-----------------------------------------------------------|
| Fit to screen     | Hides the ribbon and fits the dashboard to the window     |
| Refresh data      | Refreshes the Power Query tables and all PivotTables      |
| Exit full screen  | Brings the Excel interface back                           |
| Refresh takeaways | Rewrites the Key Takeaways text for the current filters   |
| Key Takeaways (sidebar) | Opens the Key Takeaways page                        |

The other six sidebar buttons are plain hyperlinks, and everything else (PivotTables, charts, KPIs, slicers) works without code.

---

## How to Use

1. Download the dashboard file from the `Workbook` folder of this repository.
2. Open it in **Microsoft Excel 365 or 2016+** (Windows recommended; slicers and macros need the desktop version). Click **Enable Content** if Excel asks. Macros are only needed for the buttons.
3. Set the zoom to **100%**, or press **Fit to screen**.
4. Use the **sidebar** to switch between the seven pages.
5. Click the **slicers** on the right to filter by plant, port, carrier, service level, customer or product. Click the funnel icon on a slicer to clear it.
6. Press **Refresh data** after the source data changes, and **Refresh takeaways** to update the insight cards.

---

## Repository Structure

```
.
├── Workbook/
│   └── supply-chain-logistics-dashboard.xlsm   # the dashboard
├── Raw_Data/
│   └── Supply chain logisitcs problem.xlsx  # original dataset
├── Dashboard_Screenshots/
│   ├── 1_orders.png
│   ├── 2_overview.png
│   ├── 3_products.png
│   ├── 4_customers.png
│   ├── 5_freight.png
│   ├── 6_warehouses.png
│   └── 7_key_takeaways.png
├── LICENSE
└── README.md
```

---

## Skills Demonstrated

- Data cleaning and transformation with **Power Query**
- Summarising data with **PivotTables** and **PivotCharts**
- Interactive reporting with **slicers**
- Basic **VBA** for dashboard buttons
- **KPI design:** late %, on-time %, share of total, concentration and rate per kg
- **Dashboard design:** layout, colour, chart selection and storytelling
- **Risk analysis:** spotting port, plant, customer and carrier dependency
- Business analysis: turning findings into recommended actions

---

## What I Learned

- A dashboard is not about charts, it is about showing the right risk to the right person quickly.
- Check how many distinct values a field has before charting it. Single-value fields make useless charts.
- Always clear slicers before judging a chart, because a hidden filter can make a chart look broken.
- A single outlier can flatten a whole chart, and a log scale fixes it.
- Splitting a large dashboard into focused pages is easier to read than one crowded page.

---

## Future Improvements

- Add trend charts once the data covers more than one order date
- Link orders to freight rates to estimate the real freight cost per order
- Move the model to Power Pivot with DAX measures
- Add a scenario view, for example *what if PORT04 is disrupted?*
- Rebuild the dashboard in Power BI for comparison

---

## Author

**MD. Sakib Al Hasan**

Explore my projects, technical skills, and professional profile.

![Email](https://img.shields.io/badge/Email-sakibzzz641%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white) [![GitHub](https://img.shields.io/badge/GitHub-sakibzzz641-121013?style=flat&logo=github&logoColor=white)](https://github.com/sakibzzz641) [![LinkedIn](https://img.shields.io/badge/LinkedIn-sakibzzz641-0077B5?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/sakibzzz641) [![Portfolio](https://img.shields.io/badge/Portfolio-Visit%20Website-0A66C2?style=flat&logo=googlechrome&logoColor=white)](https://sakibzzz641.github.io/)

---

*If you find this project useful, feel free to star the repository and share your feedback. What would you add to this dashboard?*
