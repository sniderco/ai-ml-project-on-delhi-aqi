# Behavioral Alpha: Sentiment × Trader Behavior Analysis

## 📌 Overview

This project explores how market sentiment (Fear & Greed Index) interacts with **trading behavior** to influence **profitability and risk**.
We combine sentiment data with trade-level data to:

* Build **daily behavioral features** (PnL, win rate, trade activity, positioning)
* Compare **Fear vs Greed regimes**
* Segment **behavioral regimes** (e.g., high vs low activity)
* Train **simple predictive models** for next-day outcomes

> ⚠️ Note:  segments represent **behavioral regimes (days)**, not individual traders.

---

## 📂 Dataset

* `fear_greed_index.csv` → sentiment score + classification
* `historical_data.csv` → trade-level data (price, size, side, PnL)

---

## ⚙️ Setup

### 1. Clone the repository

```bash
git clone  (https://github.com/sniderco/trader_analysis/blob/main/project1.ipynb)  
cd behavioral-alpha
```

### 2. Create virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate      # macOS/Linux
venv\Scripts\activate         # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

If `requirements.txt` is missing:

```bash
pip install pandas numpy matplotlib scikit-learn
```

---

## ▶️ How to Run

### Option A: Jupyter Notebook

```bash
jupyter notebook
```

Open:

```
notebooks/analysis.ipynb
```

Run cells top-to-bottom.

---

### Option B: Python Script

```bash
python main.py
```

---

## 🧪 Pipeline (What Happens)

1. **Preprocessing**

   * Convert timestamps → daily level
   * Align sentiment with trading data

2. **Feature Engineering**

   * Daily PnL, win rate
   * Trade activity (`trade_count`)
   * Position size (`avg_trade_size`, `median_trade_size`)
   * Long/Short ratio

3. **Analysis**

   * Compare **Fear vs Greed** regimes
   * Behavioral segmentation:

     * High vs Low leverage (proxy)
     * Frequent vs Infrequent activity
     * Consistent vs Inconsistent performance

4. **Modeling**

   * Classification: next-day profitability (profit/loss)
   * Regression: next-day PnL volatility

---

## 📝 Methodology

- Merged sentiment data (Fear & Greed Index) with trade-level data on a daily basis  
- Engineered behavioral features:
  - Daily PnL, win rate  
  - Trade activity (`trade_count`)  
  - Position sizing (`avg_trade_size`, `median_trade_size`)  
  - Long/Short ratio  
- Segmented data into behavioral regimes:
  - High vs Low leverage (proxy using trade size)  
  - High vs Low trading frequency  
  - Consistent vs Inconsistent performance  
- Built simple predictive models:
  - Classification → next-day profitability (profit/loss)  
  - Regression → next-day PnL volatility  

---

## 📊 Key Insights

- **Higher trading activity during Greed does not necessarily improve profitability**, indicating potential overconfidence  
- **Fear regimes exhibit higher variability in PnL**, suggesting increased market uncertainty and noise  
- **Behavioral features (trade size, frequency, win rate) are more informative than sentiment alone** in explaining outcomes  

---

## 💡 Strategy Recommendations

- **Risk Control in Greed**  
  During high-greed regimes, reduce position size and avoid excessive trading, as increased activity does not proportionally improve returns  

- **Selective Trading in Fear**  
  Participate during fear periods only when trading activity stabilizes, avoiding panic-driven volatility  

- **Focus on Behavioral Discipline**  
  Maintain consistent trade sizing and avoid reactive overtrading, as disciplined regimes tend to show better performance stability  

## 🤖 Models

* Random Forest Classifier → predict next-day profit bucket
* Random Forest Regressor → predict next-day volatility

Evaluation:

* Accuracy (classification)
* MAE / R² (regression)

---

## ⚠️ Limitations

* No explicit **trader/account ID** → cannot model individual behavior
* Trade size used as **leverage proxy**
* No transaction costs or slippage
* Market conditions may confound sentiment effects

---

## 🚀 Future Improvements

* Add lag features (t-1, t-2)
* Use rolling statistics (momentum, volatility)
* Backtest rule-based strategies
* Build dashboard (Streamlit)

---

## 🧠 Key Takeaway

> Sentiment influences behavior, but **behavioral execution** plays a larger role in determining outcomes.

---

## 👤 Author

Snigdha Singh
B.Tech | Data Science Enthusiast
