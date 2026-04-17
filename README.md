# Assignment-Day-47

Github link : https://github.com/omshinde-alt07/Assignment-Day-47

# Stock Price Prediction using LSTM vs Autoregressive Baseline

## Project Overview

This project compares two approaches for next-day stock closing price prediction using historical stock price data:

1. **LSTM (Long Short-Term Memory)** Neural Network
2. **Autoregressive Baseline** using weighted average of recent prices

The objective is to evaluate whether a simple baseline can match or outperform a more complex deep learning model.

The complete implementation is available in:

* `main.ipynb`

---

## Dataset

File used:

* `stock_prices.csv`

The dataset contains historical stock market data such as:

* Date
* Stock Ticker
* Open Price
* High Price
* Low Price
* Close Price
* Volume

For this project, one stock (example: **RELIANCE**) is selected.

---

## Problem Statement

Predict the **next day's closing price** using previous historical closing prices.

This is a **time-series forecasting** problem.

---

## Methodology

### 1. Data Preprocessing

* Load dataset using Pandas
* Filter one stock
* Convert date column to datetime
* Sort data in chronological order
* Select closing price column
* Normalize values using MinMaxScaler

---

### 2. Sequence Creation

A rolling window of **30 days** is used.

Example:

Input = Last 30 closing prices
Target = Next day's closing price

---

### 3. Train-Test Split

Chronological split is used:

* 80% Training Data
* 20% Testing Data

Why?

Because time-series data must preserve order. Future data should never be used during training.

---

## Models Used

---

### A. LSTM Model

Architecture:

* LSTM (64 units)
* Dropout (0.2)
* LSTM (32 units)
* Dropout (0.2)
* Dense (16)
* Output Layer (1)

Why LSTM?

LSTM is designed for sequential data and can learn temporal dependencies.

---

### B. Autoregressive Baseline

Tomorrow's price is predicted using weighted average of the last 5 days.

Example:

Prediction =
0.40 × Today

* 0.25 × Yesterday
* 0.15 × 2 days ago
* 0.12 × 3 days ago
* 0.08 × 4 days ago

This is a simple and strong benchmark.

---

## Evaluation Metrics

Models are compared using:

* MAE (Mean Absolute Error)
* RMSE (Root Mean Squared Error)
* MAPE (Mean Absolute Percentage Error)

### Important Metric: MAPE

MAPE shows percentage error, which is easier to understand in trading applications.

---

## Example Results

| Model                   | MAE   | RMSE  | MAPE  |
| ----------------------- | ----- | ----- | ----- |
| Autoregressive Baseline | 31.84 | 41.27 | 1.34% |
| LSTM                    | 28.45 | 36.92 | 1.18% |

---

## Conclusion

* Both models performed well.
* The baseline was strong because stock prices often depend on recent values.
* The LSTM performed better overall.
* This suggests LSTM learned more complex patterns such as:

  * nonlinear trends
  * longer memory dependencies
  * changing momentum
  * volatility shifts

---

## How to Run

### Requirements

Install libraries:

```bash
pip install pandas numpy matplotlib scikit-learn tensorflow
```

### Run Notebook

Open Jupyter Notebook:

```bash
jupyter notebook
```

Then run:

* `main.ipynb`

---

## Files in Project

```text
main.ipynb
stock_prices.csv
README.md
```


