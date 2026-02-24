# pipeline_data_integration

## 📌 Project Overview
This project consists of a modular **ETL (Extract, Transform, Load) pipeline** designed to ingest, normalize, and unify sales data from disparate sources (JSON and CSV).

The goal was to solve a real-world data integration challenge where two corporate branches ("Empresa A" and "Empresa B") utilized different systems with incompatible schemas. The pipeline standardizes column names, handles missing data gracefully, and consolidates thousands of records into a single source of truth for downstream analytics.

## 🚀 Key Features

* **Heterogeneous Data Ingestion**:
    * Extracts data from semi-structured **JSON** files and structured **CSV** files.
    * Implements **Factory Methods** (`@classmethod`) to decouple object creation from data extraction logic.

* **Data Transformation & Normalization**:
    * **Schema Mapping**: Standardizes inconsistent column headers (e.g., mapping *"Nome do Item"* to *"Nome do Produto"*).
    * **Data Joining**: Merges two distinct datasets into a single object for unified processing.
    * **Null Handling**: Utilizes robust `get()` logic to handle schema evolution (e.g., missing "Data da Venda" fields) without breaking the pipeline.

* **Object-Oriented Architecture**:
    * **Encapsulation**: Uses private methods (e.g., `__leitura_json`, `__transformando_dados_tabela`) to hide internal implementation details.
    * **Modularity**: Separates business logic (`processamento_dados.py`) from execution flow (`fusao_mercado_fev.py`).

## 📂 Project Structure

```bash
├── data_raw/                  # Raw input files (JSON and CSV)
├── data_processed/            # Final consolidated CSV output
├── notebooks/
│   └── exploracao.ipynb       # EDA and prototyping
├── processamento_dados.py     # Base ETL Class module
├── processamento_dados_desafio.py # Refactored ETL Class (Factory Pattern & Encapsulation)
├── fusao_mercado_fev.py       # Orchestrator script for the base module
└── fusao_mercado_fev_desafio.py   # Orchestrator script for the refactored module
