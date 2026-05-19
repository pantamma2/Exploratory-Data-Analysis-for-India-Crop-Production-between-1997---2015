# Exploratory Data Analysis on India Crop Production

> A comprehensive exploratory data analysis of India's crop production data spanning 19 years (1997–2015), covering 24 states, 300+ districts, and 55+ crops across all major growing seasons.

---

## explains

1. Which states produce the most crops nationally?
2. Which crops dominate production by volume?
3. How has total production changed year over year?
4. Which season contributes the most to production?
5. Which crop dominates each season?
6. Which states are most yield-efficient?

---

## Dataset Overview

| Feature | Details |
|---|---|
| Source | India Agriculture Production Dataset (Kaggle) |
| File | `apy_1.csv` |
| Raw Rows | 73,827 |
| Cleaned Rows | 73,754 |
| Columns | State, District, Crop Year, Season, Crop, Area, Production |
| Time Period | 1997 – 2015 |
| Seasons | Kharif, Rabi, Autumn, Summer, Whole Year, Winter |

---

## Data Cleaning Approach

### Missing Values
- **1,096 rows** had missing Production values (1.48% of dataset)
- Instead of blindly dropping rows, a careful 3-step strategy was used:

| Step | Method | Rows Filled |
|---|---|---|
| 1 | Observed NaN distribution by Area, State, Season, Crop | — |
| 2 | Checked if same State+Crop+Season had data elsewhere | 1,023 fillable |
| 3 | Filled using **median of State + Crop + Season** group | 1,023 rows |
| 4 | Dropped only truly unfillable rows | 73 dropped |

**Result: 99.9% of data preserved**

### Why this approach?
- Simple row deletion would remove important large-area records
- Season context matters like Rice in Kharif is not equal to Rice in Rabi
- Median is robust to outliers in production data

---

## 📈 Key Findings

### 1. Top States by Production
Uttar Pradesh leads nationally by total production volume, followed by Andhra Pradesh and West Bengal. The top 3 states together account for a significant share of national output.

### 2. Top Crops
Sugarcane dominates production by volume — producing several times more than the second-ranked crop. This is expected given sugarcane's high biomass yield per acre.

### 3. Year-over-Year Trend
Production shows an overall upward trend from 1997 to 2015, with notable dips in specific years likely corresponding to drought conditions.

### 4. Season-wise Production
Whole Year and Kharif seasons together account for the majority of national production. Winter season has the smallest contribution.

### 5. Dominant Crop per Season
- **Kharif** → Rice / Sugarcane
- **Rabi** → Wheat
- **Whole Year** → Sugarcane
- **Summer** → Rice

### 6. Yield Efficiency
High total production ≠ high yield efficiency. Some smaller states show higher yield per area unit than the high-volume states — indicating better farming practices or crop selection.

---

##  Tech Stack

| Tool | Usage |
|---|---|
| Python 3.10 | Core language |
| Pandas | Data loading, cleaning, groupby analysis |
| NumPy | Numerical operations |
| Matplotlib | Line charts, bar charts, trend plots |
| Seaborn | Heatmaps, distribution plots |
| Scikit-learn | Label encoding for correlation analysis |
| Jupyter Notebook / VS Code | Development environment |

---

##  How to Run

### 1. Clone the repository
```bash
git clone https://github.com/pantamma2/india-crop-production-eda.git
cd india-crop-production-eda
```

### 2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Add the dataset
- Download `apy_1.csv` from [Kaggle](https://www.kaggle.com/datasets/srinivas1/agriculturein-india)
- Place it in the root folder

### 4. Run the notebook
```bash
jupyter notebook eda.ipynb
```

---

##  Project Structure

```
india-crop-production-eda/
├── eda.ipynb           # Main analysis notebook
├── new_df.csv          # Cleaned dataset (output)
├── apy_1.csv           # Raw dataset (download separately)
├── assets/             # Chart screenshots
│   ├── top_states.png
│   ├── top_crops.png
│   ├── yearly_trend.png
│   ├── season_production.png
│   ├── state_crop_heatmap.png
│   └── correlation_heatmap.png
└── README.md
```

---

##  Visualizations

| Chart | Insight |
|---|---|
| Horizontal bar — Top States | UP leads production nationally |
| Horizontal bar — Top Crops | Sugarcane dominates by volume |
| Line chart — Year Trend | Overall upward trend 1997–2015 |
| Bar chart — Season Production | Whole Year + Kharif dominate |
| Bar chart — Top Crop per Season | Crop varies significantly by season |
| Horizontal bar — Yield Efficiency | Efficiency ≠ volume |
| Heatmap — State × Crop | Identifies high-value state-crop pairs |
| Correlation Heatmap | Area strongest predictor of Production |

---

##  Future Work

- [ ] Power BI dashboard for interactive exploration
- [ ] Random Forest model to predict crop production
- [ ] District-level deep dive analysis
- [ ] Drought year impact analysis (rainfall correlation)
- [ ] Crop recommendation system by state and season

---

##  Author

**Suryanarayana Murthy Chilukuri**
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/suryanarayana-murthy-chilukuri-a88107235)
[![GitHub](https://img.shields.io/badge/GitHub-pantamma2-black?logo=github)](https://github.com/pantamma2)
