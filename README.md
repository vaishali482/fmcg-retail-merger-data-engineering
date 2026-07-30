# Enterprise Data Consolidation Pipeline for an FMCG Retail Merger

An end-to-end Data Engineering project built on the Databricks Lakehouse Platform that simulates a real-world merger and acquisition (M&A) scenario in the FMCG retail industry. The project consolidates data from two independent retail companies into a unified Lakehouse using the Medallion Architecture, enabling scalable analytics and business intelligence.

---

# Business Scenario

A leading FMCG retail company acquires a smaller retailer. Both organizations maintain separate operational systems with different schemas, naming conventions, and data quality standards. The business requires a centralized data platform that integrates these disparate datasets into a single source of truth for reporting and analytics.

This project demonstrates how a modern Data Engineering pipeline addresses these challenges by implementing an enterprise-grade ETL workflow using Databricks.

---

# Objectives

- Consolidate data from multiple retail companies.
- Implement a scalable Medallion Architecture.
- Standardize heterogeneous schemas.
- Improve data quality through cleansing and validation.
- Build a dimensional model for analytical reporting.
- Enable business users to query data using natural language with Databricks Genie.

---

# Solution Architecture

```
                           Retail Company A
                                  │
                           Retail Company B
                                  │
                  ────────────────┼────────────────
                                  │
                                  ▼
                        Amazon S3 (Raw Files)
                                  │
                                  ▼
                    Databricks Lakehouse Platform
                    Apache Spark • Delta Lake
                                  │
         ┌────────────────────────┼────────────────────────┐
         │                        │                        │
         ▼                        ▼                        ▼
   Bronze Layer             Silver Layer             Gold Layer
   Raw Delta Tables     Cleaned & Standardized     Star Schema
                                                     │
                           ┌─────────────────────────┴────────────────────┐
                           ▼                                              ▼
                    BI Dashboard                                Databricks Genie
```

---

# Technology Stack

| Category | Technology |
|----------|------------|
| Programming | Python |
| Query Language | SQL |
| Distributed Processing | Apache Spark |
| Cloud Storage | Amazon S3 |
| Data Platform | Databricks |
| Storage Format | Delta Lake |
| Data Architecture | Medallion Architecture |
| Data Modeling | Star Schema |
| Visualization | BI Dashboard |
| AI Analytics | Databricks Genie |

---

# Medallion Architecture

## Bronze Layer

Stores raw data exactly as received from the source systems.

Tables

- customers
- products
- orders
- gross_price
- bronze_orders

---

## Silver Layer

Applies data quality rules and business transformations.

Operations performed

- Data cleansing
- Schema standardization
- Null handling
- Duplicate removal
- Data type conversion
- Business rule validation

Tables

- customers
- products
- orders
- gross_price
- silver_orders

---

## Gold Layer

Creates business-ready datasets optimized for analytics.

Dimension Tables

- dim_customers
- dim_products
- dim_date
- dim_gross_price

Fact Tables

- fact_orders

Semantic Layer

- sb_dim_products
- sb_dim_gross_price
- sb_fact_orders

Views

- vw_fact_orders_enriched

---

# ETL Workflow

1. Upload raw retail datasets to Amazon S3.
2. Load data into Bronze Delta tables.
3. Validate schema and perform data quality checks.
4. Transform and standardize data in the Silver layer.
5. Build fact and dimension tables in the Gold layer.
6. Generate business KPIs.
7. Visualize insights through BI dashboards.
8. Query business data using Databricks Genie.

---

# Data Model

The Gold layer follows a Star Schema for analytical workloads.

```
                    dim_customers
                           │
                           │
dim_products ─────────► fact_orders ◄──────── dim_date
                           │
                           │
                    dim_gross_price
```

---

# Key Features

- End-to-End ETL Pipeline
- Multi-source Data Integration
- Amazon S3 Data Ingestion
- Databricks Lakehouse
- Apache Spark Transformations
- Delta Lake Storage
- Medallion Architecture
- Data Quality Validation
- Schema Harmonization
- Duplicate Detection
- Star Schema Modeling
- Business KPI Generation
- BI Dashboard Reporting
- Databricks Genie Integration

---

# Business KPIs

- Total Revenue
- Monthly Sales Trend
- Regional Sales Performance
- Top Selling Products
- Product Category Performance
- Customer Segmentation
- Inventory Analysis
- Supplier Performance
- Revenue Growth

---

# Repository Structure

```
fmcg-retail-merger-data-engineering/
│
├── README.md
├── LICENSE
├── requirements.txt
│
├── assets/
│   ├── dashboards/
│   │   └── AtliQon_Sales_BI/
│   │       ├── 01_AtliQon_Sales_BI.png
│   │       ├── 02_Dashboard.png
│   │       ├── 03_Dashboard.png
│   │       ├── 04_Dashboard.png
│   │       └── 05_Dashboard.png
│   │
│   ├── screenshots/
│   │   ├── pipeline.png
│   │   ├── medallion.png
│   │   └── dashboard.png
│   │
│   └── architecture/
│       ├── architecture.png
│       └── architecture.drawio
│
├── cloud/
│   └── aws/
│       └── s3/
│           ├── bucket_s3.md
│           └── child_company_dp.md
│
├── notebooks/
│   └── databricks/
│       ├── 1_Setup/
│       │   ├── dim_data_table_creation.py
│       │   ├── setup_catalog.py
│       │   └── Utilities.py
│       │
│       ├── 2_Dimension_data_processing/
│       │   ├── 1_customer_data_processing.py
│       │   ├── 2_products_data_processing.py
│       │   └── 3_pricing_data_processing.py
│       │
│       ├── 3_Fact_data_processing/
│       │   ├── 1_full_load_fact.py
│       │   └── 2_incremental_load_fact.py
│       │
│       ├── 4_gold_layer/
│       │   └── gold.png
│       │
│       ├── 5_silver_layer/
│       │   └── silver.png
│       │
│       └── 6_bronze_layer/
│           └── bronze.png
│
├── data/
│   ├── parent_company/
│   │   └── incremental_load/
│   │       ├── bronze/
│   │       ├── silver/
│   │       ├── gold/
│   │       └── analytics/
│   │
│   └── child_company/
│       ├── bronze/
│       ├── silver/
│       ├── gold/
│       └── analytics/
│
├── src/
│   └── pipeline/
│       └── medallion.png
│
├── BI/
│   └── dashboard/
│
└── docs/
    ├── databricks_project.excalidraw
    ├── medallion_architecture.md
    └── project_architecture.png

```

---

# Skills Demonstrated

- Data Engineering
- ETL Pipeline Development
- Apache Spark
- Databricks
- Delta Lake
- Amazon S3
- Python
- SQL
- Data Modeling
- Star Schema Design
- Data Quality Engineering
- Enterprise Data Integration
- Business Intelligence
- Analytics Engineering

---

# Future Enhancements

- Incremental Data Loading
- Change Data Capture (CDC)
- Delta Live Tables
- Apache Airflow Orchestration
- GitHub Actions CI/CD
- Unity Catalog Governance
- Great Expectations Data Validation
- Spark Structured Streaming
- Automated Monitoring and Alerting

---

# Screenshots

Include screenshots of:

- Amazon S3 Bucket
- Databricks Workspace
- Bronze Tables
- Silver Tables
- Gold Tables
- Unity Catalog
- ETL Pipeline Execution
- BI Dashboard
- Databricks Genie
- Star Schema

---

# License

This project is developed for educational and portfolio purposes. The datasets used are synthetic and simulate an enterprise FMCG retail merger scenario. No proprietary or confidential business data is included.

---
## 📊 Live Dashboard

Explore the interactive dashboard here:

🔗 (https://dbc-c9b33a49-7383.cloud.databricks.com/dashboardsv3/01f182ecb03b19939dea4d06fadab573/published?o=7474653988214033)
