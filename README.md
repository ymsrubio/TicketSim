# TicketSim: Municipal 8888 Ticketing System Simulation & SLA Breach Analytics

**TicketSim** is a synthetic data generation and data science analytics ecosystem modeling municipal 8888/311-style civic complaint ticketing systems under resource constraints and extreme weather disruptions (typhoon shocks).

---

## 📁 Repository File Map

```text
TicketSim/
├── data/                                 # Generated benchmark datasets
│   ├── departments.csv                   # 5 city departments (capacity & storm vulnerability)
│   ├── citizens.csv                      # 10,000 registered citizens
│   └── tickets.csv                       # 3,199 synthetic municipal complaint tickets
├── docs/
│   └── documentation.md                  # Full model research & data specification
├── notebooks/
│   ├── 02_synthetic_data_generator.ipynb # Poisson & Log-Normal synthetic data engine (Steps 1–6)
│   └── 03_eda_and_sla_breach_analysis.ipynb # Exploratory Data Analysis & SLA Breach Notebook
└── .learning/                            # Interactive HTML study guides for learners
    ├── 01-step-3b-timeline-notes.html
    ├── 02-step-3c-grid-notes.html
    ├── 03-step-4-ticket-engine-notes.html
    ├── 04-step-5-6-export-notes.html
    ├── 05-eda-ticket-1-notes.html
    ├── 06-eda-ticket-2-notes.html
    └── 07-eda-ticket-3-notes.html
```

---

## 🚀 Recent Implementations

- **Synthetic Data Generator** (`notebooks/02_synthetic_data_generator.ipynb`):
  - **Step 1 & 2**: Fixed seed (`SEED = 42`), 5 departments, 10,000 citizens with $L_{\text{civic}}$ engagement scores.
  - **Step 3B & 3C**: 30-day timeline with $L_{\text{storm}}$ decaying typhoon shock (1.0 peak at 2026-08-15) and 150-row simulation grid (`df_grid`).
  - **Step 4**: Poisson ticket arrival engine ($\lambda = \text{base} + (\text{base} \times L_{\text{storm}} \times \text{vulnerability})$) & weighted citizen raffle drum $\rightarrow$ 3,199 synthetic tickets.
  - **Step 5 & 6**: Log-Normal SLA resolution engine (storm backlog delays up to 76h), hidden variable removal (`L_storm` & `L_civic` dropped), and CSV export to `data/`.

- **EDA & SLA Breach Analysis** (`notebooks/03_eda_and_sla_breach_analysis.ipynb`):
  - **Ticket 1 (Data Ingestion)**: Ingested datasets, parsed datetimes, and merged tickets with department capacities.
  - **Ticket 2 (The Baseline)**: Performed data hygiene audit (`0` nulls, `0` duplicates) and generated department workload bar chart and resolution time KDE histogram.
  - **Ticket 3 (Temporal Anomaly)**: Plotted 30-day daily ticket time-series line chart with peak typhoon shock annotation at `2026-08-15` (491 tickets).
