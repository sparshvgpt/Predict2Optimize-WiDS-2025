# Predict2Optimize-WiDS-2025 Midterm Report
## Overview
In this project, we are aiming to build a simple end to end pipeline designed to turn noisy market data into optimal investment decisions.
We attempt to predict future returns first using ML techniques, then optimize based on those predictions.
The project is divided among 5 weeks:
### Week 1 — Financial Data & Feature Extraction
**Goals**
- Become familiar with NumPy, Pandas, Matplotlib.
- Download daily price data using `yfinance`.
- Compute daily returns and construct basic rolling features.
### Week 2 — Baseline Models and Linear Predictors
**Goals**
- Predict next-day returns using simple regression models.
- Establish performance baselines.
### Week 3 — Neural Networks and Walk-Forward Prediction
**Goals**
- Train a small MLP to predict returns.
- Set up a rolling, walk-forward evaluation loop.
### Week 4 — Portfolio Optimization \& Robust Extensions
**Goals**
- Convert predicted returns into portfolio weights via Markowitz optimization.
- Study the convex optimization formulation underlying portfolio construction.
- Extend the classical model toward simple forms of robust optimization.
### Week 5 — Integration and Final Backtest
**Goals**
- Combine your predictor with your optimizer into a full pipeline.
- Evaluate the strategy over time and interpret results.

---

So far, I have succesfully completed the foundational phases (week 1 and week 2) of the project in which we learned how to use the `yfinance` python module, learned how to analyze finanical data, implemented some standard financial models and did some basic backtesting.

---

## Week-wise work done and concepts learned:

## Week 1

The primary objective of Week 1 was to set up the analysis environment, acquire real-world financial data, and perform fundamental feature extraction and visualization. The work establishes a foundation for building quantitative models by understanding the properties of asset prices, returns, and volatility.

**Concepts Learned**
- OHLCV Data: Understanding the standard format for equity data.
- Analysis of Returns - Simple Returns: The percentage change in price, and Log Returns: The primary metric used in quantitative finance due to statistical properties
- Rolling Window Features - To avoid lookahead bias, features are generated using rolling windows.
- Risk Metrics : Downside Deviation: Volatility calculated only using negative returns, Maximum Drawdown (MDD): The largest percentage drop from a peak to a trough, Value at Risk (VaR): Probabilistic estimate of maximum loss over a specific horizon.

**Work done**
- Environment Setup & Data Acquisition.
- Data Sourcing and Data Cleaning using `yfinance` and `pandas`.
- Feature Engineering : Returns Calculation and Volatility Analysis.
- Visualization : Price vs. Moving Average, Log Returns, Rolling Volatility
- Bonus Analysis : Volume vs. Volatility and Seasonality effects on the stock price

## Week 2

The primary objective was to build machine learning models to predict the next day's (time t+1) asset return using only information available at time t. A major component of this week was doing evaluation and backtesting to avoid "look-ahead bias".

**Concepts Learned**
- Difficulty of Return Prediction : Financial time series are inherently noisy. Because daily returns fluctuate around zero with high variance, simply predicting 0.0 every day is a surprisingly difficult baseline to beat mathematically.
- Time-Series Cross-Validation (Walk-Forward) and understood why random splits fail.
- Feature Engineering for Time Series : Constructed a feature matrix containing only previous information to predict next day returns
- Model Classes : Naive Baselines, Parametric Models (Linear/Ridge) and Non-Parametric Models (Random Forest).

**Work done**
- Data Preparation & Feature Construction : Loaded historical data for AAPL, computed Log Returns for numerical stability and made a strictly forward-looking feature set.
- Model Implementation : Zero Predictor, Rolling Mean Predictor, Linear Regression (OLS), Ridge Regression and Random Forest.
- Evaluation & Results Analysis : The closeness of all scores to the zero predictor validates the Efficient Market Hypothesis.
