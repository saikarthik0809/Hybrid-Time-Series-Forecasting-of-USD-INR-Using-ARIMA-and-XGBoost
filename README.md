# USD/INR Exchange Rate Forecasting using Hybrid ARIMA + XGBoost Model

## 📈 Overview
This project presents a hybrid machine learning and statistical approach to forecasting the USD/INR exchange rate. Traditional models like ARIMA are effective for modeling linear dependencies but struggle with nonlinear patterns. By combining ARIMA with XGBoost, we capture both linear and nonlinear components to significantly improve prediction accuracy.

---

## 🔧 Methodology

### 1. Data Preprocessing
- Historical USD/INR exchange rate data (~6,000 business days)
- Resampled to business-day frequency, cleaned for duplicates
- Stationarity enforced using Augmented Dickey-Fuller test and first-order differencing

### 2. ARIMA Modeling
- `auto_arima()` selected ARIMA(5,1,3) for baseline forecasting
- Residuals from ARIMA were computed for further modeling

### 3. Residual Modeling with XGBoost
- Features engineered:
  - Lagged exchange rates (`lag1`, `lag2`)
  - Short/medium returns (`return1`, `return5`)
- XGBoost trained on residuals
- Final forecast: `Hybrid = ARIMA + XGBoost(predicted residuals)`

---

## 📊 Results

| Model        | MSE       |
|--------------|-----------|
| ARIMA Only   | 0.1001    |
| Hybrid Model | **0.0057** |

- > ✅ 90% reduction in error using the hybrid model
- Feature importance: `lag1`, `return1`, `return5` were most predictive
- Visual backtest showed hybrid forecast closely tracked real exchange rate trends

---

