# UK Commercial Building Energy Assessment & Optimization

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An end-to-end data analytics and commercial optimization assessment of two years (35,040 half-hourly intervals) of electricity consumption data for a UK commercial facility operating under a Time-of-Use (ToU) tariff structure.

The analysis evaluates building energy performance, isolates an unmonitored operational Building Management System (BMS) control failure, quantifies weather-normalized efficiency shifts using Ordinary Least Squares (OLS) regression, decomposes energy cost drivers, resolves kVA capacity exceedances, and outlines a prioritized implementation roadmap.

---

## 📸 Key Findings at a Glance

| Metric | Year 1 (2024/25) | Year 2 (2025/26) | Operational Variance |
| :--- | :--- | :--- | :--- |
| **Total Import Volume** | 990,104 kWh | 1,072,975 kWh | **+8.37%** (+82,871 kWh) |
| **Total Spend** | £186,038 | £215,663 | **+15.92%** (+£29,625) |
| **Weather-Expected Volume** | 990,104 kWh | 981,203 kWh | **+9.35%** Weather-Adj. Shift (+91,772 kWh) |
| **Unoccupied Mean Load** | 93.95 kW | 105.33 kW | **+12.11%** (+60.4% post-Jan 12 fault) |
| **Peak Demand (kVA)** | 303.21 kVA | 343.79 kVA | **+13.38%** (11 breaches >320 kVA limit) |
| **Average Power Factor** | 0.938 | 0.917 | **-2.24%** (dipped to 0.855 min) |

---

## 💡 Executive Summary & Critical Insights

### 1. Operational Anomaly Detection (Jan 12, 2026 Control Fault)
* **Step-Change Identification**: The site was operating **8.98% more efficiently** in Year 2 until **Monday, January 12, 2026**, when a control override/setback failure occurred.
* **Unoccupied Baseload Jump**: Overnight and weekend baseline demand stepped up from **82.22 kW** to **131.89 kW** (+49.67 kW continuous excess load).
* **Direct Financial Loss**: Incurred **190,311 kWh** in excess consumption and **£36,038** in unnecessary energy cost across 5.5 months. Rectifying this fault yields **£36,000–£72,000/year** in recurring savings.

### 2. Weather Normalization Analysis
* Year 2 was 10.9% milder in heating degree days ($\text{HDD}_{15.5} = 1,851.9$ vs $2,079.0$).
* An OLS regression model trained on Year 1 baseline data ($R^2 = 0.682$) projected an expected Year 2 consumption of **981,203 kWh**.
* The true weather-normalized operational deterioration was **+91,772 kWh (+9.35%)**, confirming that efficiency loss was driven by internal control failures rather than weather dynamics.

### 3. Tariff & Cost Decomposition
* The +£29,625 (+15.92%) annual spend increase was mathematically decomposed into:
  1. **Unit Rate Inflation**: **+£12,014 (+6.46%)** from ToU rate increases across Red, Amber, and Green bands.
  2. **Volume Growth**: **+£16,523 (+8.88%)** driven by the post-Jan 12 control fault.
  3. **Capacity Charges**: **+£1,088 (+0.59%)** from higher agreed capacity rates (£0.095 $\rightarrow$ £0.105/kVA/day) and kVA exceedance penalties.

### 4. Power Factor Correction & Capacity Limits
* The facility experienced **11 half-hourly capacity exceedances** exceeding the **320 kVA Agreed Import Capacity** (peaking at 343.79 kVA).
* Real active power ($303.50\text{ kW}$) never exceeded 320 kW. All exceedances were caused by degraded power factor ($\text{PF} \approx 0.855\text{--}0.898$) during morning plant restart windows (08:00–09:30).
* **Corrective Proof**: Restoring site power factor to $\ge 0.95$ via a 60 kVAR capacitor bank reduces peak apparent power to $319.47\text{ kVA}$, completely eliminating **100% of capacity exceedances** without requiring load curtailment.

---

## 🎯 Actionable Implementation Roadmap

| # | Action Item | Priority | Est. CapEx (£) | Est. Annual Savings (£/yr) | Simple Payback |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | **BMS Setback & Override Audit** | P1 - High | £0 – £500 | £36,000 – £72,000 | **< 1 Week** |
| **2** | **Morning HVAC Plant Staggering** | P2 - Medium | £0 – £1,000 | £2,000 – £5,000 | **1–2 Months** |
| **3** | **Power Factor Correction (PFC) Unit** | P2 - Medium | £4,000 – £8,000 | £3,000 – £6,000 | **12–18 Months** |
| **4** | **Automated BMS Exception Alerts** | P3 - Ongoing | £1,500 – £3,000 | £5,000 – £10,000 | **< 6 Months** |
| **TOTAL** | **Full Portfolio Investment** | — | **£9,000 (Avg)** | **£69,500 / year** | **1.6 Months** |

---
## 🚀 Quick Start

### Google Colab
Launch the pipeline instantly in your browser with zero setup:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1YKIQpaAJOi8OQYSqbNwae80M6RlL3tdQ?usp=sharing)

---
## 📁 Repository Structure

```text
├── energy_dataset.xlsx      # Raw synthetic half-hourly dataset
├── building_energy_performance_analytics.ipynb # Baseload jump & fault quantification, Degree-day OLS regression model, ToU band analysis & cost waterfall, kVA limit breaches & PFC proof, Financial cashflow & Gantt schedule
├── requirements.txt                            # Python dependencies
├── README.md                                   # Executive summary & documentation
├── plots/
    ├── daily_consumption_trend.png
    ├── baseload_and_power_factor.png
    ├── weather_normalization_comparison.png
    ├── peak_kva_vs_capacity.png
    ├── cost_decomposition_waterfall.png
    ├── kw_vs_kva_power_factor_scatter.png
    └── cumulative_cashflow_projection.png
```

---
## 🛠️ Tech Stack & Requirements
* Python 3.9+
* Data Processing: pandas, numpy
* Statistical Modeling: statsmodels (OLS Regression)
* Visualization: matplotlib, seaborn
* Spreadsheet Ingestion: openpyxl
---
## 📝 License
Distributed under the MIT License. See `LICENSE` for details.
