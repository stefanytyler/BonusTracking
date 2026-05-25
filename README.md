# Pinnacle Bonus Intelligence Dashboard
## README & User Guide
*Sales Performance & Bonus Tracking System — For VP of Sales & Department Team Leads*

---

## 1. Overview

The Pinnacle Bonus Intelligence Dashboard is a two-file system — a standalone HTML dashboard and an Excel data template — that gives the VP of Sales and department team leads real-time visibility into quota attainment, bonus accruals, and tier standings. No server, no IT setup, and no internet connection required.

The system is designed for HR and sales leadership to track, adjust, and communicate bonus performance across departments, teams, and individuals throughout the month, quarter, and year.

**What's included:**
- `sales_bonus_dashboard.html` — the interactive dashboard
- `sales_bonus_template.xlsx` — the data file you edit to update the dashboard
- `README.md` — this document

**Key capabilities:**
- Company-wide KPIs: overall quota attainment, total bonus accrual, reps at or above quota, and gold-tier achievers
- Department standings with drill-down to teams and individual reps
- Monthly, quarterly, and yearly period toggle — all calculated from a single data file
- Configurable bonus tier structure (thresholds, percentages, and accelerator multipliers)
- No-code updates: edit the Excel template and re-upload to refresh everything

---

## 2. Quick Start

**Step 1 — Open the Excel template**

Open `sales_bonus_template.xlsx`. You will see four sheets along the bottom tab bar:
- Instructions — overview (also in the file)
- Reps — one row per sales representative
- Tiers — bonus tier thresholds and percentages
- Goals — company-level targets by period

**Step 2 — Fill in your rep data**

Go to the Reps sheet and replace the sample data with your actual team. Each row is one rep. Do not change the column headers in row 2. See Section 3 for a full column reference.

> ⚠️ Department and Team names must be spelled and capitalized identically across all rows. Any variation — even a trailing space — will create a separate group in the dashboard.

**Step 3 — Open the dashboard**

Open `sales_bonus_dashboard.html` in a modern web browser. Chrome or Edge is recommended. Double-clicking the file will open it directly — no installation needed.

**Step 4 — Upload your file**

Click the **Upload Excel File** button at the top of the dashboard. Select your completed `sales_bonus_template.xlsx` file. The dashboard will parse it immediately and render all charts, tables, and drill-downs. Nothing is sent to any server — all processing happens locally in the browser.

**Step 5 — Refresh when data changes**

Whenever you update the Excel file, return to the dashboard and upload the new version using the same Upload button. The entire dashboard will re-render with the latest data.

---

## 3. Reps Sheet — Column Reference

The Reps sheet is the primary data source for all dashboard calculations. Columns are fixed — do not insert, delete, or rearrange them.

| Col | Column Name | Description |
|-----|-------------|-------------|
| A | Rep Name | Full name of the sales representative |
| B | Role | Job title (e.g. AE, Sr. AE, SDR, BDR, Partner AE) |
| C | Department | Must match exactly across all rows for grouping to work |
| D | Team | Sub-team within the department |
| E | Team Lead | Name of the team lead (used in drill-down labels) |
| F | Base Salary ($) | Annual base salary used to calculate bonus estimates |
| G | Monthly Quota ($) | Revenue quota target for the current month |
| H | Monthly Actual ($) | Revenue actually closed in the current month |
| I | Q Quota ($) | Quarterly revenue quota target |
| J | Q Actual ($) | Quarterly revenue actually closed |
| K | YTD Quota ($) | Year-to-date quota target |
| L | YTD Actual ($) | Year-to-date revenue closed |
| M | Notes | Optional free-text notes (not shown in dashboard) |
| N | Active (Y/N) | Set to N to exclude a rep from all calculations |

> ℹ️ Attainment % and bonus estimates are calculated automatically by the dashboard. You do not need to enter these — only enter the raw quota and actual figures.

**Adding and removing reps:**
- To add a rep: add a new row below the last entry. All columns must be filled (except Notes).
- To remove a rep temporarily: set column N (Active) to `N`. The rep will be excluded from all calculations but the row is preserved.
- To remove a rep permanently: delete the entire row.
- Do not leave blank rows between data rows — this can cause the parser to stop reading early.

---

## 4. Tiers Sheet — Bonus Configuration

The Tiers sheet defines how attainment percentages map to bonus payouts. The dashboard reads this sheet on every upload, so you can change the tier structure at any time without touching the HTML file.

| Tier | Attainment | Bonus % | Accelerator / Notes |
|------|------------|---------|---------------------|
| Gold | ≥ 110% | 15% of base salary | 1.5× at 120%+, 2× at 130%+ |
| Silver | 100–109% | 10% of base salary | Standard rate (1×) |
| Bronze | 80–99% | 5% of base salary | Standard rate (1×) |
| Below Target | < 80% | No bonus | PIP review triggered |

**Columns in the Tiers sheet:**
- **Tier Name** — the display label used throughout the dashboard (Gold, Silver, etc.)
- **Min Attainment %** — the minimum attainment a rep must reach to qualify for this tier
- **Max Attainment %** — the maximum attainment for this tier (use 999 for open-ended top tier)
- **Bonus % of Base** — the percentage of annual base salary paid as bonus
- **Accelerator Multiplier** — applied on top of the bonus percentage (1.0 = no change, 1.5 = 50% uplift)
- **Tier Color (hex)** — the hex color code used to display this tier in the dashboard

> ℹ️ If the Tiers sheet is missing or empty, the dashboard falls back to the default structure shown above. It is strongly recommended to keep the Tiers sheet populated.

---

## 5. Goals Sheet — Period Targets

The Goals sheet stores company-level targets for each period. It provides context for company-wide targets displayed in the KPI summary.

**Columns in the Goals sheet:**
- **Period Type** — enter `monthly`, `quarterly`, or `yearly` (lowercase)
- **Period Label** — a readable label such as *June 2025*, *Q2 2025*, or *FY 2025*
- **Company Revenue Goal ($)** — total revenue target for the period
- **Headcount Target** — planned headcount for the period
- **Gold Tier Target (# reps)** — how many reps you are targeting for gold tier achievement
- **Notes** — optional free text

---

## 6. Dashboard Navigation

**Period toggle**
The Monthly / Quarterly / Yearly buttons at the top right control which quota and actual columns are used for all calculations. Switching period re-computes every number on the page — no re-upload needed.

**Tabs:**
- **Executive Overview** — company KPIs, department attainment bar chart, tier distribution, and bonus accrual breakdown
- **Departments** — ranked department list; click any department to drill into its teams
- **Teams** — card view of all teams across all departments
- **Individuals** — full rep list with department filter; sorted by attainment
- **Tier Structure** — shows the loaded tier configuration and a sample bonus calculation

**Drill-down flow**

The Departments tab supports a three-level drill-down:
1. Click a department row to see its teams
2. Click a team row to see individual rep performance
3. Use the back arrow at the top to navigate back up

---

## 7. Roles & Permissions

**VP of Sales**
- Full visibility across all departments, teams, and individuals
- Can modify the Tiers sheet to adjust bonus structures before re-distributing the file
- Responsible for maintaining the master Excel template and distributing the dashboard HTML to team leads

**Department team leads**
- Upload the same Excel file to see the full dashboard
- Can filter the Individuals tab to their department for focused review
- Should not modify the Tiers or Goals sheets without VP approval

> ⚠️ There is no login or role-based access control in this file-based system. If you need to restrict what a team lead can see, provide them with a filtered copy of the Excel file containing only their department's rows.

---

## 8. Troubleshooting

| Issue | Solution |
|-------|----------|
| Dashboard shows no data after upload | Check that your file has sheets named exactly `Reps`, `Tiers`, and `Goals` (case-sensitive) |
| A department is missing from the charts | Ensure the Department column (C) is spelled consistently — any variation creates a separate group |
| Bonus estimates look wrong | Review the Tiers sheet — confirm Min/Max Attainment and Bonus % columns are numbers, not text |
| A rep appears even though they left | Set column N (Active) to `N` for that rep and re-upload the file |
| Charts don't appear after upload | Try a different browser. Chrome and Edge are recommended |
| Period toggle doesn't change numbers | Confirm that Q Quota, Q Actual, YTD Quota, and YTD Actual columns (I–L) are filled in |

**Browser compatibility:**
- Chrome 90+ — recommended
- Edge 90+ — recommended
- Firefox 88+ — supported
- Safari 14+ — supported
- Internet Explorer — not supported

---

## 9. Tips & Best Practices

- Lock columns A–E on the Reps sheet in Excel (Format Cells > Protection) to prevent accidental edits to names, departments, and teams.
- Use Excel's data validation on column C (Department) and D (Team) to create dropdown lists — this prevents spelling inconsistencies.
- At the start of each month, update columns G and H (Monthly Quota and Monthly Actual). At quarter-end, update I and J. At year-end, update K and L.
- Keep a dated backup of the Excel file each month (e.g. `sales_data_2025_06.xlsx`) so you can reload historical snapshots at any time.
- The dashboard and template can be stored on a shared drive (SharePoint, Google Drive, etc.) so anyone with access can download and use them.

---

*Pinnacle Bonus Intelligence Dashboard — Internal HR & Sales Leadership Use Only*
