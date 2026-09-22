# Auto Loan Securitisation Analytics

## Project Overview

This project presents an end-to-end analytics framework for an **Auto Loan Securitisation Portfolio**, developed using **Microsoft Power BI, DAX and Excel**.

The solution integrates portfolio, delinquency, vintage, credit-risk, ECL, waterfall, stress-testing and investor-reporting analytics into a single reporting framework.

The objective is to provide a structured and repeatable approach for monitoring portfolio performance, credit risk, transaction cash flows and reporting requirements.

---

## Key Technologies

* **Power BI** – Data modelling, dashboards and interactive reporting
* **DAX** – Financial, portfolio and risk calculations
* **Power Query** – Data preparation and transformation
* **Microsoft Excel** – Independent ECL and waterfall validation
* **Row-Level Security (RLS)** – Regional data access control

---

## Data Sources

The project uses four primary datasets:

1. **Auto Loan Securitisation Data**

   * Loan characteristics
   * Borrower information
   * Vehicle information
   * Current balances
   * Credit-risk fields
   * ECL fields

2. **DPD Snapshot History**

   * Delinquency days
   * DPD buckets
   * Cure and roll flags
   * Repossession and write-off indicators

3. **Dynamic Monthly Performance**

   * Monthly balances
   * Defaults
   * Losses
   * Recoveries
   * Prepayments
   * Collections
   * Collection efficiency

4. **Static Pool / Vintage Data**

   * Vintage performance
   * Cumulative defaults
   * Gross and net losses
   * Recoveries
   * Pool factor
   * Marginal loss rates

---

## Data Model

A star-schema architecture was implemented in Power BI.

### Dimension Tables

* `DimLoan`
* `DimBorrower`
* `DimVehicle`
* `DimGeography`
* `DimDate`
* `DimDPDBucket`

### Fact Tables

* `FactMonthlyPerformance`
* `FactDPDSnapshot`
* `FactDynamicLoss`
* `FactStaticPool`

This structure supports consistent filtering, calculations and portfolio analysis.

---

## Power BI Dashboard Pages

The final Power BI solution contains **10 interactive dashboard pages**:

### 1. Executive / Portfolio Overview

Provides a high-level view of portfolio size, balances, loan activity and key risk indicators.

### 2. Time & Portfolio Performance

Includes MTD, QTD, YTD, MoM, YoY and rolling portfolio performance analysis.

### 3. Waterfall & Tranche Allocation

Analyses collections, senior and mezzanine allocations, equity residuals, OC/IC ratios, reserves and transaction triggers.

### 4. Pool Summary

Provides portfolio-level balance, loan count and pool characteristic analysis.

### 5. Delinquency & Early Warning

Monitors current, 30+, 60+ and 90+ DPD, delinquency trends, DPD distribution and trigger indicators.

### 6. Vintage Analysis

Analyses portfolio performance by vintage and months-on-book, including cumulative losses and marginal loss rates.

### 7. IFRS 9 / ECL

Calculates and analyses Expected Credit Loss using PD, LGD and EAD, including Stage 1, Stage 2 and Stage 3 analysis.

### 8. Stress Testing & What-If

Evaluates portfolio sensitivity under different default, recovery, prepayment and interest-rate assumptions.

### 9. Investor Reporting

Provides six reporting sections:

* Pool Summary
* Delinquency Report
* Loss & Recovery Report
* Prepayment Report
* Waterfall Report
* Trigger Status

### 10. Rating Agency Data Tape

Provides loan-level and pool-level statistics required for portfolio surveillance and validation.

---

## Key Analytics

The model contains **80+ DAX and financial measures**, including:

* Current Balance
* Total Outstanding
* Active Loans
* Defaulted Loans
* Original Balance
* MTD / QTD / YTD
* MoM / YoY
* Rolling 3M / 12M
* WAC
* WAM
* WALA
* Weighted Average LTV
* Weighted Average CIBIL
* Weighted Average DTI
* 30+ / 60+ / 90+ DPD
* Delinquency percentages
* Vintage loss metrics
* Marginal Loss Rate
* PD / LGD / EAD
* IFRS 9 ECL
* ECL Variance
* ECL Coverage
* Waterfall allocations
* OC / IC ratios
* Reserve Adequacy
* Transaction triggers
* Stress-adjusted ECL
* What-If scenario measures

---

## IFRS 9 ECL Framework

The project uses the core:

**ECL = PD × LGD × EAD**

The ECL analysis includes:

* Stage 1
* Stage 2
* Stage 3
* Total ECL Provision
* Calculated ECL
* ECL Variance
* ECL Variance %
* ECL Coverage

The ECL calculations are independently cross-checked using Excel.

---

## Waterfall Analysis

The waterfall model follows the defined payment priority:

**Total Collections → Senior Fees → Senior Interest → Senior Principal → Mezzanine Interest → Mezzanine Principal → Equity Residual**

The model also monitors:

* Senior OC
* Mezzanine OC
* Senior IC
* Mezzanine IC
* Delinquency trigger
* Cumulative loss trigger
* Reserve adequacy
* Credit enhancement
* Allocation validation

An independent Excel waterfall validation is included.

---

## Stress Testing

The stress-testing framework includes adjustable parameters for:

* Default Rate Multiplier
* Recovery Rate Haircut
* Prepayment Speed Change
* Interest Rate Shock

Additional scenarios evaluate the effect of PD and LGD shocks on portfolio ECL.

---

## Row-Level Security

Regional Row-Level Security was implemented using the following roles:

* `RLS_Central`
* `RLS_East`
* `RLS_North`
* `RLS_South`
* `RLS_West`
* `RLS_All`

The roles were tested to confirm that regional data access operates according to the defined filters.

---

## Validation & Controls

The project includes multiple validation controls.

### Power BI Validation

* Loan ID completeness
* Pool ID completeness
* Current Balance completeness
* EAD completeness
* Rating Agency Data Tape validation
* Waterfall allocation validation

### Excel Validation

#### ECL Crosscheck

Calculates:

`PD × LGD × EAD`

and compares the result with the Power BI/source ECL provision.

#### Waterfall Validation

Compares:

`Total Collections - Total Waterfall Allocated`

The expected reconciliation result is zero, subject to minor rounding differences.

#### DAX Measure Dictionary

Documents the project's DAX measures, categories, business purpose, calculation logic and outputs.

---

## Repository Structure

```text
Auto Loan Securitisation Analytics/
│
├── README.md
│
├── PowerBI/
│   └── Auto_Loan_Securitisation_Analytics_Final.pbix
│
├── Excel/
│   └── Auto_Loan_Securitisation_Analytics_Validation.xlsx
│
├── Report/
│   └── Auto_Loan_Securitisation_Analytics_Report.pdf
│
├── Presentation/
│   └── Auto_Loan_Securitisation_Analytics_Presentation.pptx
│
├── Data/
│   ├── auto_loan_securitisation_data.csv
│   ├── dpd_snapshot_history.csv
│   ├── dynamic_loss_monthly.csv
│   └── static_pool_vintage_data.csv
│
└── Documentation/
    └── DAX_Measure_Dictionary.xlsx
```

---

## Project Deliverables

The completed project includes:

* 10-page Power BI dashboard
* Star-schema data model
* 80+ DAX and financial measures
* IFRS 9 ECL engine
* Waterfall and tranche analysis
* Vintage analysis
* Delinquency and early-warning analysis
* Stress testing and What-If analysis
* Investor reporting
* Rating agency data tape
* Regional RLS
* Excel ECL validation
* Excel waterfall validation
* DAX measure dictionary
* Detailed project report
* Final presentation

---

## Key Outcomes

The solution provides an integrated framework for:

* Portfolio performance monitoring
* Credit-risk analysis
* Delinquency surveillance
* Expected credit loss analysis
* Transaction cash-flow monitoring
* Stress testing
* Investor reporting
* Rating-agency reporting
* Data-quality validation
* Regional data access control

---

## Disclaimer

This project is an analytical and educational implementation based on the supplied project datasets and assumptions. It is intended to demonstrate data analytics, financial modelling, securitisation reporting and risk-monitoring capabilities and should not be interpreted as investment, credit or financial advice.

---

## Author

**Smit Mahendra Patel**

**Project:** Auto Loan Securitisation Analytics
**Tools:** Power BI | DAX | Excel | Power Query
