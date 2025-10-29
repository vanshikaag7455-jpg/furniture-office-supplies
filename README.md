# Furniture & Office Supplies — Sales Analysis

## Overview

This repository contains a small analytical project focused on sales data for a furniture and office-supplies business. The work is primarily an Excel-based exploratory analysis and dashboarding exercise designed to transform cleaned sales data into actionable insights: top-selling products, revenue trends, seasonal behavior, and performance by category/region.

This is an early project / learning exercise intended to demonstrate data cleaning, analysis, visualization, and story-telling through a dashboard and a short presentation.

## Goals

- Understand historical sales performance across products, categories, and regions.
- Create concise KPIs (Total Revenue, Units Sold, Average Order Value, Margin if available).
- Build a dashboard that supports quick business questions: "Which products are driving revenue?", "How are sales trending month-over-month?", "Are there clear seasonal peaks?"
- Produce visualizations and a short presentation summarizing findings and recommendations.

## Repository structure

Top-level folders (what's included in this repo):

- `Cleaned Data/` — Cleaned source datasets used for the analysis (CSV or Excel worksheets). These are the canonical inputs for the dashboard and outputs. Expect files like cleaned_sales.csv or cleaned_sales.xlsx.
- `dashboard/` — Files used to create interactive or static dashboards. This may contain an Excel workbook with pivot tables/charts, or exported PNGs of charts. If additional dashboarding tools were used (Power BI / Tableau), those project files would be found here.
- `Final Presentation/` — A short slide deck summarizing the analysis, key charts, conclusions, and recommendations for stakeholders.
- `Output/` — Generated outputs from the analysis: charts, CSV exports, summary tables used in the presentation.
- `LICENSE` — Project license (please read for reuse rules).

If you open the repository and a folder appears empty, it may be because large binary files were not checked in; check the original project directory for the expected Excel files.

## Data description (what to expect)

The analysis uses cleaned sales data. Typical columns you can expect:

- OrderID — Unique identifier for each order or invoice.
- OrderDate — Date of the order (YYYY-MM-DD or Excel date).
- ProductID / ProductName — Product identifiers and names.
- Category / Subcategory — Product grouping.
- Quantity — Units sold per line item.
- UnitPrice — Price per unit.
- Revenue / Sales — Calculated as Quantity * UnitPrice (sometimes present as a column).
- CustomerID / Region — Customer or geographic metadata used for segmentation.

If margins or cost columns are present (Cost, GrossMargin), additional profitability KPIs were produced.

## Analysis performed

The project follows a standard analysis pipeline:

1. Data inspection and validation — check for missing values, date ranges, duplicate orders.
2. KPI calculation — compute Total Sales, Units Sold, Average Order Value, Orders Count, and (if cost data exists) Gross Margin.
3. Time-series analysis — monthly and weekly sales trends, year-over-year comparisons, seasonality.
4. Product / category analysis — top products by revenue, units sold, and growth/decline trends.
5. Regional / customer segmentation — sales by region, customer cohorts, and channel if available.
6. Dashboard and visualization — pivot charts, bar/line plots, heatmaps, and summary cards for KPIs.

Typical questions the analysis answers:

- What are the top 10 products by revenue and by units sold?
- How have monthly sales trended over the period in the dataset?
- Are there strong seasonal effects (e.g., peaks in Q4)?
- Which categories/regions are underperforming or overperforming?

## Dashboard

The `dashboard/` folder contains the interactive workbook and exported images used for stakeholder consumption. The dashboard typically contains:

- KPI cards (Total Revenue, Units Sold, AOV, Orders)
- Time series chart (Monthly Revenue)
- Top products bar chart
- Category/Region breakdown (stacked bar, treemap or map)
- Filters/slicers for time range, product category, and region (Excel slicers or dashboard controls)

How to view:

1. Open the Excel file in `dashboard/` (e.g., `Sales_Dashboard.xlsx`) with Excel 2016+ (or Excel Online). Enable macros if the workbook relies on small macros — the README author should note if macros are required.
2. Use the slicers and pivot filters to interact with the charts.

If the dashboard was built in Power BI or Tableau, open the corresponding `.pbix` or `.twbx` file in the appropriate application.

## Final presentation

The `Final Presentation/` folder contains a concise slide deck (PDF or PowerPoint) summarizing:

- Objective and dataset
- Key findings (top products, trends, anomalies)
- Visuals supporting conclusions
- Business recommendations (inventory adjustments, promotional timing, focus categories)

Use the PDF/PPTX to present to stakeholders; the charts in `Output/` are sized for slides and may be embedded in the deck.

## Reproducing the analysis

There are two typical ways to reproduce the project depending on your tooling preference:

Option A — Excel-only (recommended if you only have the Excel files):

1. Open the files in `Cleaned Data/` and the workbook in `dashboard/`.
2. Refresh pivot tables (Data -> Refresh All) to recalculate KPIs from the cleaned data source.
3. Export charts as images (right-click -> Save as Picture) if you want to add them to slides.

Option B — Python-based reproduction (if you want automated rebuilds). The repository does not currently include Python scripts, but the steps below can be used to reproduce the analysis using pandas/matplotlib (add scripts to automate):

PowerShell example to create a virtual environment and install minimal packages:

```powershell
python -m venv .venv; .\.venv\Scripts\Activate.ps1; pip install --upgrade pip; pip install pandas matplotlib seaborn openpyxl
```

Example minimal script outline (create `scripts/rebuild_analysis.py`):

- Read cleaned Excel/CSV from `Cleaned Data/` with pandas.
- Compute KPIs and save summary CSVs to `Output/`.
- Produce and save charts as PNG files to `Output/`.

If you'd like, I can add these scripts to the repository to automate the full pipeline.

## Key assumptions and limitations

- The analysis assumes the datasets in `Cleaned Data/` are the final cleaned extracts (i.e., data cleaning steps were already applied). If not, a data-cleaning notebook or script should be added.
- Date formats and timezone normalizations are assumed to be consistent. If multi-year or multi-region timestamps exist, confirm alignment.
- If cost or margin data is missing, profitability analysis is not performed.

## Recommendations & next steps

Short-term:

- Add a small `scripts/` folder with one Python script to regenerate the `Output/` figures and summary CSVs automatically.
- Add a simple `requirements.txt` or pinned dependencies to enable reproducible runs.
- If the dashboard is heavily used, migrate to Power BI or a small web app (Streamlit) for easier sharing and scheduled refreshes.

Medium-term:

- Build automated ETL from the raw data source into the `Cleaned Data/` location and schedule a nightly refresh.
- Add basic tests to validate data quality (no negative quantities, no missing dates, revenue equals quantity * unit price).

Analytical improvements:

- Customer segmentation using RFM analysis.
- Product-level forecasting (simple ARIMA/Prophet or an ML model) for inventory planning.
- Promotion lift analysis using before/after comparison or A/B if the data supports it.

## Contribution & contact

If you want to contribute or extend this project:

- Fork the repository and open a pull request describing your change.
- For data/format changes, include sample output in `Output/` and update this README with reproduction steps.

Author: (original project owner)

If you want me to extend this repository (add scripts to automate the pipeline, add tests, or create a Python notebook), tell me which automation you prefer and I will implement it.

## License

This project includes a `LICENSE` file at the repo root — please consult it for reuse and redistribution terms.

---

Small note: I kept descriptions general because the repository appears to be an Excel-first project with the main artifacts in the folders listed above. If you want, I can now:

1) Inspect the actual files in `Cleaned Data/`, `dashboard/`, and `Output/` and update the README with concrete filenames and a sample of the columns present.
2) Add a small Python script to automatically produce the KPI CSV and the main charts used in the presentation.

Tell me which of these you'd like next and I will proceed.
