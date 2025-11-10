# Beyond Expert Foresight: Data‑driven Forecasting of Emerging Technologies from Global Signals
TL;DR. This repository hosts code and data for forecasting 36‑month trajectories of application‑focused emerging technologies using big, heterogeneous signals (publications, patents, social media, and macro indicators) and deep sequence models (LSTM, GRU, Transformer, TCN) evaluated under leakage‑safe protocols. Results show deep models can beat strong classical baselines on several domains, extending reliable planning horizons for technology strategy and governance.

# What’s here

Dataset (2000–2024, monthly): Ten application‑focused technologies curated from contemporary industry foresight, with series for journal articles & patents (Lens), macro & science‑policy indicators (World Bank, OECD), and developer attention (Hacker News).
Forecasting targets: Monthly journal‑article counts per technology (chosen for timeliness and cross‑domain consistency).
Models: LSTM, GRU, Transformer, and TCN, each trained under three multi‑horizon regimes: S1 Direct multi‑step, S2 Recursive 1‑step, S3 Recursive H‑step (free‑running/BPTT).
Evaluation: Expanding‑window time‑series cross‑validation, SMAPE as the headline metric, moving‑block bootstrap significance tests vs seasonal ARIMA, with FDR correction across technologies. 

# Data overview

Technologies (10): 3D Printing, Autonomous Vehicles, Digital Twins, Generative AI, Generative Agritech, Metaverse, Misinformation, New Programming Models, Renewable Energy, Sustainable Technologies. Domains align with contemporary industry prediction lists used to scope application‑focused areas.

# Sources:

Publications & Patents: monthly counts via Lens.

Socio‑economic covariates: World Bank & OECD indicators (e.g., GDP, GERD, access to electricity), aligned to monthly grid without look‑ahead.

Social attention: Hacker News posts/comments.

# Methods at a glance

Training strategies:

S1 Direct multi‑step — single pass predicts the full H‑step vector.

S2 Recursive 1‑step — train 1‑step, roll out recursively.

S3 Recursive H‑step (free‑running/BPTT) — optimize directly for free‑running rollouts.

Architectures: LSTM, GRU, Transformer, TCN (dilated causal conv).

Validation: Expanding‑window blocked CV; headline metric SMAPE; uncertainty via MC‑dropout. Significance vs ARIMA using moving‑block bootstrap (ℓ=5, B=10,000) with BH FDR control across technologies.
