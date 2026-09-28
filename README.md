# Earnings Announcement Effects on Options Implied Volatility

Independent research investigating whether options expiring shortly after a company's earnings announcement carry higher implied volatility than later-dated options on the same stock.

## Problem

Is implied volatility higher for options expiring near a company's earnings date than for options expiring later, well past it? And how does implied volatility vary as earnings announcements approach?

## Approach

Pulled live option chains and earnings dates for 31 large-cap tickers across technology, financials, healthcare, energy, and consumer sectors (e.g. AAPL, JPM, UNH, XOM) via the yfinance API. Classified options as near-term or far-term relative to each ticker's next earnings date, then found the at-the-money (ATM) strike per ticker and term to get the most reliable implied volatility reading. Engineered a variance-decomposition metric ("event variance") to isolate the earnings-specific effect from the stock's normal volatility term structure, and validated it with a one-sided t-test. Built an automated daily pipeline that locks in the same near-term option per ticker and tracks its implied volatility through the earnings announcement.

## Result

Implied volatility for near-term options is significantly higher than for far-term options around earnings (p = 0.01). Daily tracking shows implied volatility rising as each earnings date approaches and dropping sharply afterward.

## Contents

- `earnings_iv_study.ipynb` — full analysis: data collection, ATM implied volatility computation, statistical testing, visualization, and the daily tracking pipeline

Note: the daily tracking pipeline appends to local log files that update continuously and aren't included in this repo. The relevant cells are here for reference; reproducing that part requires rerunning the pipeline yourself.

## Tools

Python, yfinance, Pandas, SciPy (t-test), Matplotlib
