# 🛒 Product Sales Forecasting

A machine learning pipeline to forecast daily retail sales across 365 stores using historical sales data, store attributes, and temporal features.

- **Live Demo:** https://product-sales-forecasting-ditj.onrender.com
  - *Note: The free tier sleeps after 15 min of inactivity. First request after sleep takes ~30-60 sec to wake up — please be patient on your first visit.*
- **Tableau Dashboard:** https://public.tableau.com/app/profile/sruthi.s6388/viz/ProductSalesForecasting_17768358106560/DeepDiveStoreRegion
- **Technical Blog (Medium):** https://medium.com/@sruthiswathandran/from-raw-csv-to-live-api-a-retail-sales-forecasting-journey-d38146002b1b

---

## 📋 Problem Statement

Retail businesses need accurate sales forecasts to optimize inventory, staffing, marketing campaigns, and long-term strategy. This project builds a forecasting model that predicts daily sales for any store based on its characteristics (store type, location, region) and day-level features (date, holiday flag, discount flag).

## 🎯 Target Metric

- **Primary:** RMSE (Root Mean Squared Error)
- **Secondary:** MAE, MAPE, R²

## 🏆 Final Results

| Model | MAE | RMSE | MAPE | R² |
|-------|-----|------|------|-----|
| **XGBoost (production)** | **8,994** | **13,239** | **26.9%** | **0.572** |
| LightGBM | 9,157 | 13,425 | 28.1% | 0.560 |
| Random Forest | 9,696 | 14,445 | 29.4% | 0.491 |
| Linear Regression (baseline) | 10,831 | 15,653 | 31.1% | 0.402 |

## 🔍 Key Findings from EDA

1. **Store Type is the strongest predictor** (F = 35,123) — S4 stores earn 2.2x more than S2 on average.
2. **Discounts boost sales by ~32%** (H1 confirmed statistically significant).
3. **Holidays REDUCE sales by ~19%** — counter-intuitive but consistent with store closures on public holidays.
4. **Weekend lift is ~23%** — Sunday is the single best day of the week.
5. **Region has weak effect in average**, but R1 dominates top performers (8 of top 10 stores are in R1).

## 🏗️ Tech Stack

- **Analysis:** Python, Pandas, NumPy, SciPy
- **Modeling:** scikit-learn, XGBoost, LightGBM
- **Visualization:** Matplotlib, Seaborn, Tableau Public
- **Deployment:** Flask, Gunicorn, Render

## 📂 Project Structure

```
sales_forecasting/
├── notebooks/
│   ├── 01_EDA_and_Hypothesis_Testing.ipynb
│   └── 02_Modeling.ipynb
├── models/
│   ├── xgboost_sales_model.pkl
│   ├── label_encoders.pkl
│   └── feature_columns.pkl
├── deployment/
│   ├── app.py
│   └── templates/
│       └── index.html
├── requirements.txt
├── runtime.txt
├── Procfile
├── .gitignore
└── README.md
```