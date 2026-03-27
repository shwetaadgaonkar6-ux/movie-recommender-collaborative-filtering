# movie-recommender-collaborative-filtering

# 🎬 Movie Recommender System — Collaborative Filtering

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat&logo=jupyter)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-red?style=flat&logo=scikit-learn)
![NumPy](https://img.shields.io/badge/NumPy-Computing-013243?style=flat&logo=numpy)
![pandas](https://img.shields.io/badge/pandas-Analysis-150458?style=flat&logo=pandas)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)

---

## Introduction

Every time Netflix suggests your next binge or Spotify builds your weekly playlist, a recommender system is working behind the scenes. This project pulls back the curtain on how they actually work.

Using the **MovieLens 100K dataset** — 100,000 ratings from 943 users across 1,682 movies — I designed, implemented, and evaluated five collaborative filtering algorithms entirely from scratch. No recommender libraries. Just Python, linear algebra, and a lot of curiosity about what makes one method better than another.

The question I set out to answer: *does complexity always beat simplicity?* The results were more interesting than I expected.

---

## Technologies Used

| Tool | Purpose |
|------|---------|
| Python 3.x | Core language |
| Jupyter Notebook | Development & presentation |
| pandas | Data loading and wrangling |
| NumPy | Matrix operations and vectorisation |
| scikit-learn | Train/test splitting, similarity metrics |
| Matplotlib | Performance visualisation |

---

## Features

- 5 recommendation algorithms built from scratch — no Surprise, no LightFM
- Robust fallback strategies for sparse neighbourhoods
- Systematic hyperparameter tuning — K neighbours and λ blending weight
- Head-to-head evaluation using MAE and RMSE
- Clean performance comparison table across all methods
- Inline visualisation of results

---

## The Five Methods

| # | Method | Core Idea |
|---|--------|-----------|
| 1 | User Average | Predict using the user's own mean rating |
| 2 | Item Average | Predict using the item's mean rating |
| 3 | User KNN-CF | Find similar users, borrow their ratings |
| 4 | Item KNN-CF | Find similar items, borrow their ratings |
| 5 | Hybrid CF | Blend User KNN + Item KNN with tuned λ |

Methods 3–5 include fallback logic for cold-start scenarios where neighbours have no relevant ratings.

---

## How I Built It

**1. Data pipeline**
Loaded and parsed the MovieLens 100K tab-separated files into a structured pandas DataFrame, then constructed a dense user-item rating matrix using NumPy.

**2. Baseline models**
Implemented user average and item average predictors — deceptively simple, surprisingly competitive benchmarks.

**3. KNN collaborative filtering**
Computed full user-user and item-item similarity matrices. For each prediction, identified the K most similar neighbours with relevant ratings and aggregated their scores.

**4. Hybrid model**
Combined User KNN and Item KNN predictions using a weighted parameter λ, tuned systematically to find the optimal blend.

**5. Evaluation**
Measured MAE and RMSE against a held-out test set, restricted to items with 30+ training interactions for statistical reliability.

**6. Optimisation**
Iteratively tuned K and λ — not guesswork, but structured experimentation — to drive down error metrics.

---

## What I Learned

- Collaborative filtering at a mathematical level — not just the concept, but the mechanics
- Why sparse data is the real enemy of KNN-based methods
- That a well-tuned simple baseline can outperform a poorly-tuned complex model
- How similarity metric choice quietly shapes everything downstream
- The discipline of fair evaluation — why test set design matters as much as the model
- NumPy vectorisation: the difference between code that runs in seconds vs. minutes

---

## How It Could Be Improved

- **Matrix Factorisation (SVD/ALS)** — better suited to sparse, high-dimensional data
- **Neural Collaborative Filtering** — richer user and item representations via embeddings
- **Cold start strategy** — content-based fallback for users or items with no history
- **Similarity metric comparison** — cosine vs Pearson vs adjusted cosine, benchmarked
- **Scale testing** — validate on MovieLens 1M or 10M to test real-world performance
- **API deployment** — serve recommendations via FastAPI or Flask
- **Implicit feedback** — extend beyond explicit ratings to clicks, views, and dwell time

---

## How to Run

### Install dependencies
```bash
pip install numpy pandas scikit-learn jupyter matplotlib
```

### Clone and run
```bash
git clone https://github.com/shwetaadgaonkar6-ux/movie-recommender-collaborative-filtering.git
cd movie-recommender-collaborative-filtering
jupyter notebook movie_recommender.ipynb
```

Then: `Kernel → Restart & Run All`

### What to expect
- MAE and RMSE for each method printed to console
- Performance comparison table in the summary section
- Visualisation plots rendered inline

---

## Dataset

[MovieLens 100K](https://grouplens.org/datasets/movielens/100k/) by GroupLens Research, University of Minnesota.
100,000 ratings · 943 users · 1,682 movies · Scale: 1–5

---

## Author

**Shweta Adgaonkar**


[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/shweta-adgaonkar-b852a6223)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-black?style=flat&logo=github)](https://github.com/shwetaadgaonkar6-ux)
