**AI-Driven Sentiment Arbitrage Engine**

_Quantitative Backtesting with FinBERT NLP & yFinance_

**Project Overview**
This project develops a high-frequency data pipeline that transforms qualitative financial news into quantitative trading signals.
By leveraging FinBERT, a Large Language Model (LLM) specialized for the financial domain; the engine identifies market "mood" to automate Buy/Sell decisions.
The core objective was to test the correlation between news-driven sentiment spikes and T+1 price action for high-volatility equities.

**Technical Stack**
NLP Engine: ProsusAI/finbert (HuggingFace Transformers)
Data APIs: YahooFinance (Market Prices) & Google News RSS (Sentiment Input)
Execution Logic: Python (Pandas, NumPy)
Visualizations: Matplotlib

**Quantitative Methodology**
To ensure institutional-grade integrity, the model implements:
**Sentiment Quantification**: Headlines are mapped to a continuous scale (Positive: 1, Neutral: 0, Negative: -1) weighted by the model's confidence score.

**Look-Ahead Bias Mitigation:** Utilized .shift(1) logic to ensure signals are based strictly on "Yesterday’s" data, 
replicating real-world execution where a trader acts on the previous close's information.

**Thresholding:** Established a $\pm0.2$ sentiment trigger to filter out market noise and execute only on high-conviction news events.

**Performance & Post-Mortem Analysis**
Final Strategy Return: -5.39%
Market Return: -0.34%
Alpha Generated: -5.05%

**Strategic Review:**
While the strategy generated a negative Alpha of -5.05% during the testing window, the project yielded critical insights into Market Decoupling:
1. **Macro vs. Micro:** The underperformance suggests that during the testing period, the ticker was driven by macro-economic factors (e.g., interest rate volatility)
   rather than idiosyncratic news sentiment.
   
3. **Signal Lag:** The -5% variance highlights the importance of liquidity and the "speed of news," suggesting that for high-cap stocks,
   sentiment may be priced in faster than the T+1 execution window allows.
   
**Future Optimizations**

**Intraday Execution:** Transitioning from daily closes to hourly intervals to capture sentiment alpha before it decays.

**Regime Switching:** Integrating a Volatility Filter (ATR) to disable the sentiment engine during high-beta market sell-offs.

**Multi-Source Aggregation:** Incorporating Reddit (r/wallstreetbets) and X (Twitter) API data to contrast institutional news with retail sentiment.
