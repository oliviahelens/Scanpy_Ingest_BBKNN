# Scanpy_Ingest_BBKNN
Single-cell RNA-seq data integration using Scanpy's ingest() and BBKNN, following the scverse tutorial. Demonstrates PCA-based label transfer and batch correction on PBMC and pancreas datasets.

## Overview

Two integration approaches are compared:

- **ingest** — asymmetric integration that maps labels and embeddings from an annotated reference onto query data using PCA and nearest-neighbor lookup
- **BBKNN** (Batch Balanced k-Nearest Neighbours) — symmetric integration that builds a batch-corrected neighborhood graph by finding neighbors within each batch independently

### Datasets

- **PBMCs** — 3k processed reference (`pbmc3k`) mapped onto 68k reduced dataset (`pbmc68k`)
- **Pancreas** — four human pancreas studies (Baron, Muraro, Segerstolpe, Wang) with 14,693 cells across 19 cell types

## Setup

### Requirements

- Python 3.10+
- GitHub Codespaces (4-core / 16 GB RAM recommended) or local environment

### Installation

```bash
python3 -m venv .venv
echo ".venv/" > .gitignore
source .venv/bin/activate
pip install 'scanpy[leiden]' pooch scikit-image bbknn ipykernel
python -m ipykernel install --user --name=venv --display-name "Python (.venv)"
```

### Running

Open the notebook in VS Code or Jupyter, select the **Python (.venv)** kernel, and run all cells.

## Key Dependencies

| Package | Purpose |
|---------|---------|
| scanpy | Core scRNA-seq analysis and `ingest()` |
| anndata | Annotated data matrices |
| bbknn | Batch-balanced nearest neighbors integration |
| pooch | Tutorial data retrieval |
| scikit-image | Required by Scrublet |

## References

- Polański, K. et al. BBKNN: fast batch alignment of single cell transcriptomes. *Bioinformatics* 36, 964–966 (2020).
- Wolf, F.A., Angerer, P. & Theis, F.J. SCANPY: large-scale single-cell gene expression data analysis. *Genome Biology* 19, 15 (2018).
- McInnes, L., Healy, J. & Melville, J. UMAP: Uniform Manifold Approximation and Projection for Dimension Reduction. *arXiv* 1802.03426 (2018).
- Baron, M. et al. A Single-Cell Transcriptomic Map of the Human and Mouse Pancreas Reveals Inter- and Intra-cell Population Structure. *Cell Systems* 3, 346–360 (2016).
- Muraro, M.J. et al. A Single-Cell Transcriptome Atlas of the Human Pancreas. *Cell Systems* 3, 385–394 (2016).
- Segerstolpe, Å. et al. Single-Cell Transcriptome Profiling of Human Pancreatic Islets in Health and Type 2 Diabetes. *Cell Metabolism* 24, 593–607 (2016).
- Lotfollahi, M. et al. scGen predicts single-cell perturbation responses. *Nature Methods* 16, 715–721 (2019).