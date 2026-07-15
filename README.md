# 📊 Facebook Ads vs Google AdWords — A/B Test & Budget Allocation Analysis

[![View Live Slides](https://img.shields.io/badge/View-Stakeholder_Ready_Report-1E8F73?style=for-the-badge)](https://rakeshkpradhan15-hub.github.io/facebook-vs-adwords-ab-test/)

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-EDA-yellow)
![SciPy](https://img.shields.io/badge/SciPy-Hypothesis%20Testing-orange)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

**A statistically-grounded answer to a real marketing budget question: should ad spend go to Facebook or Google AdWords?**

---

## Table of Contents
- [Overview (STAR)](#overview-star)
- [The Recommendation](#the-recommendation)
- [Data](#data)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Skills Demonstrated](#skills-demonstrated)
- [Tools & Libraries](#tools--libraries)
- [Repository Structure](#repository-structure)
- [How to Run](#how-to-run)
- [Limitations & Next Steps](#limitations--next-steps)
- [About Me](#about-me)

---

## Overview (STAR)

**Situation:**
A company runs parallel ad campaigns on Facebook and Google AdWords with a fixed, limited marketing budget. Leadership has no data-backed way to decide which platform deserves more spend — decisions were being made on raw averages and channel familiarity, not evidence.

**Task:**
Analyze 1,000 paired campaign-day records across both platforms, build the business metrics that actually reflect return on spend (not just clicks or views), and determine whether any observed performance gap between platforms is statistically real or just random variation — then turn that into a clear budget recommendation.

**Action:**
- Cleaned and validated the dataset (type casting, null/duplicate checks, date parsing)
- Ran exploratory analysis across CTR, conversion rate, cost-per-click, and cost-per-conversion for both platforms
- Engineered a **cost-per-conversion** metric to unify performance and spend into one comparable number
- Bucketed conversions on a shared scale so platforms were judged consistently, not relative to themselves
- Tested each metric for normality (`normaltest`) and equal variance (`Levene's test`) before choosing between an **independent t-test** or **Mann-Whitney U test** — rather than defaulting to one method regardless of fit

**Result:**
Found that Facebook converts at ~3x the rate of AdWords at a ~37% lower cost per conversion, while AdWords delivers ~2x the reach at a lower cost-per-click. All five tested metrics showed statistically significant differences (p < 0.05) between platforms, turning a "which one feels better" debate into a defensible, evidence-based budget recommendation.

---

## The Recommendation

> **Prioritize Facebook for conversion-focused campaigns. Use AdWords for low-cost reach and awareness.**

| Metric | Facebook | AdWords | Winner |
|---|---|---|---|
| Avg. Views per Campaign | 2,152 | 4,771 | AdWords (~2x reach) |
| Click-Through Rate (CTR) | 2.28% | 1.28% | **Facebook** |
| Conversion Rate | 32.7% | 10.8% | **Facebook** |
| Avg. Cost per Click | $4.31 | $2.27 | AdWords |
| Avg. Cost per Conversion | $15.23 | $23.97 | **Facebook** |
| Total Conversions (period) | 11,975 | 5,933 | **Facebook** |
| Statistical Significance | p < 0.05 on all 5 metrics tested | | ✅ Confirmed, not noise |

---

## Data

- **Source:** [A/B Testing Marketing Campaign Dataset, Kaggle](#) *(https://www.kaggle.com/datasets/shubhamdamai/ab-testing-analysis-facebook-vs-adword)*
- **Size:** 1,000 daily records, 2021–2023, tracked in parallel for both platforms
- **Fields:** views, clicks, conversions, CTR, conversion rate, cost-per-click, cost-per-ad
- **Quality:** No missing values or duplicates; dates verified and cast to datetime for trend analysis

## Methodology

1. **Data cleaning & validation** — type casting, duplicate/null checks, derived `year`/`month` fields
2. **Exploratory analysis** — distribution plots, correlation matrix, monthly trend lines for CTR and conversion rate
3. **Metric engineering** — built cost-per-conversion as the single number combining performance and spend
4. **Fair-comparison bucketing** — shared Low/Medium/High conversion bands across both platforms
5. **Hypothesis testing** — normality → variance → correct test selection (t-test vs. Mann-Whitney U) across 5 metrics, rejecting the null hypothesis that platform doesn't matter

## Key Findings

- AdWords drives **~2x more impressions** but converts at a third of Facebook's rate — a reach/awareness channel, not a conversion engine, in this dataset
- Facebook converts **~3x more efficiently** at a **37% lower cost per conversion**
- Facebook's lead in average daily conversions holds across **all three years**, not just in aggregate
- The gap is **statistically significant**, not sampling noise — the difference between "AdWords looked worse" and "AdWords is worse for this objective, with evidence behind it"

## Skills Demonstrated

| Category | Specific Skills |
|---|---|
| **Data Wrangling** | Cleaning, type casting, null/duplicate handling, datetime parsing with `pandas` |
| **Exploratory Data Analysis** | Distribution analysis, correlation matrices, trend analysis with `Matplotlib` / `Seaborn` |
| **Statistical Inference** | Normality testing, variance testing, hypothesis test selection, p-value interpretation with `SciPy` |
| **Business Metric Design** | Translating raw ad data into decision-ready metrics (cost-per-conversion) |
| **Communication** | Turning statistical output into a plain-language, actionable business recommendation |

## Tools & Libraries

`Python` · `pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `SciPy` (`normaltest`, `levene`, `ttest_ind`, `mannwhitneyu`) · `Jupyter Notebook`

## Repository Structure

```
├── AD Campaign Analysis.ipynb   # Full analysis: EDA → metrics → hypothesis testing
├── CSV_Data/
│   └── ab_testing_dataset.csv   # Source dataset
├── README.md                    # You are here
```

## How to Run

```bash
git clone <repo-url>
cd ad-campaign-ab-test
pip install -r requirements.txt
jupyter notebook AD_Campaign_Analysis.ipynb
```

## Limitations & Next Steps

- This is observational campaign-day data, not a controlled randomized experiment — audience overlap and seasonality aren't fully isolated
- p-values show significance but not magnitude; next iteration adds effect sizes (Cohen's d / rank-biserial correlation) alongside them
- Planned: rebuild the cost-per-conversion comparison as an interactive Power BI/Tableau dashboard for non-technical stakeholders

## About Me

I'm Rakesh, a Data Analyst with a BCA background and specialised training in Artificial Intelligence and Data Analytics from CTTC Bhubaneswar (MSME , Government of India ). I work at the intersection of Python, SQL, and Power BI to help businesses extract clarity from complexity. My approach is simple: clean the data, understand the story it's telling, and build something a decision-maker can actually use.
Over the past year I've completed end-to-end analytics projects covering sales analytics, supply chain optimisation, demand forecasting, customer behaviour analysis. I've built interactive Power BI dashboards that track KPIs in real time, developed machine learning models, and performed EDA that uncovered insights not visible in raw reports. Every project was driven by one question: what decision does this data need to support?
Right now I'm actively building in the data space — sharpening my skills in Azure, advanced SQL, and ML deployment while seeking my first full-time role in Data Analytics, Business Intelligence, or Data Visualisation. I want to work with a team that believes data is not just a report — it's a competitive advantage.
If you're hiring a data analyst who is hungry, technically solid, and genuinely curious about what the numbers mean — let's talk. DM me here or write to rakeshkpradhan15@gmail.com.

---
⭐ If you found this project useful, consider starring the repo.
