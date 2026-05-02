# 2025 Ultimate Skiing Trip by Data Science 🎿

> *"Four broke uni students from Monash with zero skiing experience walked into a datathon. They came out with a flight booked to Mt. Stirling."*

**Team HDCML (How Deep Can Monkeys Learn)** | Inter-University Datathon 2025

---

## About This Repository

The original notebook was submitted during the datathon itself under time pressure. After the competition, I took the initiative to revisit the project independently — cleaning up the code, removing redundancies, standardising the analysis structure, and adding proper documentation. The original submission is preserved on the main branch. This branch (`improved`) reflects my own post-datathon improvements.

---

## The Mission

We are four first-time skiers from Monash University who needed to answer one very important question:
**Which Australian ski resort should broke uni students with absolutely no skiing experience visit, and when?**

We did what any self-respecting data science team would do — we threw machine learning at it.

---

## Approach

### Step 1 — Mountain Selection (EDA)

We evaluated **9 Australian ski resorts** on the metrics that actually matter to beginner skiers:

| Factor | Why it matters |
|---|---|
| **Distance from Monash** | We are broke. Fuel costs money. |
| **Weekly lift pass price** | Still broke. |
| **Crowdedness per beginner/intermediate trail** | We crash. We need space. |

Using historical visitation data (2014–2024) and publicly available resort info, we scored each mountain and landed on **Mt. Stirling** — cheap lift passes ($469/week), only 233 km from campus, and blissfully uncrowded.

### Step 2 — Week Selection (ML Forecasting)

With Mt. Stirling locked in, we needed the optimal week. We modelled the 2025 ski season using three approaches:

- **Prophet** — Facebook's time-series forecasting library; great at capturing annual temperature seasonality and long-term trends
- **LSTM** — a recurrent neural network for comparison; struggled with long seasonal cycles but included for the vibes
- **Hybrid RF + XGBoost** — a Random Forest classifier (rain/no rain?) followed by an XGBoost regressor (how much rain?) for rainfall forecasting

The models agreed: **Week 3 of the 2025 ski season** is the sweet spot — cold enough for good snow, low crowds, and (relatively) less rain.

---

## Dataset

- **BOM Climate Data** — daily temperature and rainfall records from 7 weather stations near Australian ski resorts (2010–2024)
- **Resort Visitation Data** — weekly visitor counts across 9 resorts (2014–2024)

Both datasets were provided by **Allianz** for the Inter-University Datathon 2025 and are **not included in this repository** (see `.gitignore`).

---

## Repo Structure

```
ski_resort_analysis_hdcml.ipynb   # main notebook — the full analysis
data/                             # dataset (gitignored, not distributed)
README.md
.gitignore
```

---

## Running the Notebook

```bash
pip install pandas numpy matplotlib seaborn prophet scikit-learn xgboost tensorflow
jupyter notebook ski_resort_analysis_hdcml.ipynb
```

You will need the Allianz dataset Excel file placed at `data/2025 Allianz Datathon Dataset.xlsx`.

---

*Made with questionable sleep schedules and an excess of enthusiasm by Team HDCML.*
