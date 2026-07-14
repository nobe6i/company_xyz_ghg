# 🌿 Company XYZ: 2023 Corporate Carbon Footprint Analytics

An automated data pipeline and reporting tool designed to calculate, analyze, and visualize Company XYZ’s Greenhouse Gas (GHG) emissions across Scope 1, Scope 2, and Scope 3 frameworks for 2023.

---

## 📊 Project Overview

This repository houses the data processing infrastructure used to consolidate utility, operational, and supply chain data into a unified carbon accounting model. By automating emission calculations, this project provides actionable insights to drive Company XYZ toward its net-zero sustainability milestones.

### Emissions Scope Framework
Our methodology strictly aligns with the **GHG Protocol Corporate Standard**:
* **Scope 1 (Direct Emissions):** Stationary combustion from facility operations (e.g., Natural Gas consumption at the Alameda and Salt Lake City sites).
* **Scope 2 (Indirect Emissions):** Purchased electricity across corporate facilities, adjusted using regional grid emission intensity factors.
* **Scope 3 (Other Indirect Emissions):** Upstream and downstream value chain impacts, currently tracking **Category 5: Waste Generated in Operations** (Garbage, Recycling, and Organics routing).

---

## 🛠️ Tech Stack & Dependencies

The pipeline relies on a comprehensive suite of Python libraries to ingest unstructured billing documents, extract underlying tables, align dates, and output audited visualizations and sheets:

### Data Ingestion & Unstructured Document Processing (OCR & PDF Parsing)
* **`ocrmypdf` & `pytesseract`:** For optical character recognition to transform scanned utility invoices into searchable, machine-readable text assets.
* **`pdf2image`:** Converts PDF pages into high-resolution image formats for localized downstream OCR array scanning.
* **`pdfplumber` & `pypdf` (`PdfReader`):** Programmatic table and text extraction from digital PDF utility bills and waste ledger receipts.

### Core Engineering & Chronological Processing
* **`pandas` & `numpy`:** Relational data structures, inner joining across staggered timelines, and core multi-variable array calculations.
* **`os`, `glob`, & `re`:** Low-level file system manipulation, mass directory pattern matching, and complex regex parsing for document-bound metadata extraction.
* **`datetime`:** Time-series validation and standardized temporal index matching.

### Analytics & Visual Data Design
* **`matplotlib.pyplot` & `seaborn`:** For drafting high-DPI trend analysis, statistical scatter plots, and multi-layered monthly emissions stackplots.

### Spreadsheet Architecture & Typography 
* **`openpyxl`:** Complete styling control of Excel workbook cells including `Font`, `PatternFill`, `Alignment`, `Border`, `Side`, and dynamic `get_column_letter` widths to eliminate structural text truncations.

---

## ⚙️ Pipeline Methodology

### 1. Data Merging & Temporal Alignment
Because utility billing cycles, waste pick-up intervals, and telemetry logs arrive at different frequencies and row counts, the core script runs strict **inner joins** on validated date ranges. This eliminates dangling indices and ensures every layer of the stack plot shares identical mathematical dimensions.

### 2. Formatted Visualizations
The script compiles all three scopes into a clear, publication-quality stacked area chart. It bypasses global canvas states to write directly to disk without resource wiping:
```python
fig.savefig('outputs/co2e_emissions_stackplot.png', dpi=300, bbox_inches='tight')
---
