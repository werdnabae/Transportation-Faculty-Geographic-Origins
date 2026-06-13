# Geographic Origins of U.S. Transportation Faculty

Code and data for the paper:

**"Global Sources of the U.S. Transportation Research Workforce"**

Andrew J. Bae. *Transportation Research Interdisciplinary Perspectives* **38** (2026) 102096.

[![DOI](https://img.shields.io/badge/DOI-10.1016%2Fj.trip.2026.102096-blue)](https://doi.org/10.1016/j.trip.2026.102096)

**Paper:** <https://www.sciencedirect.com/science/article/pii/S2590198226002617>

This repository contains data and code for a descriptive study of the **geographic sourcing of U.S. transportation faculty** within civil engineering departments.

The project examines where faculty capacity is trained and how upstream geographic origins relate to entry into the U.S. academic labor market. The emphasis is on **descriptive measurement of capacity, pipeline balance, and cohort change**, rather than causal inference.

The repository is designed to be **fully reproducible on its own**.

## Quickstart (uv)

This project uses [uv](https://docs.astral.sh/uv/) for environment and dependency management.

```bash
# 1. Install uv (https://docs.astral.sh/uv/getting-started/installation/)
curl -LsSf https://astral.sh/uv/install.sh | sh

# 2. Create the environment and install dependencies (uv reads pyproject.toml)
uv sync

# 3. Launch the analysis notebook
uv run jupyter lab analysis.ipynb
```

`uv sync` automatically provisions the Python version pinned in `.python-version`
and installs the dependencies declared in `pyproject.toml`. Running the notebook
end to end regenerates all figures and the appendix table from the provided data
files.

## Project scope and contributions

Using a harmonized roster of transportation-focused faculty across ranked U.S. universities, this project documents:

* The geographic composition of faculty capacity by **undergraduate (UG) country of origin**
* How upstream geographic sourcing has shifted across **PhD completion cohorts**
* How undergraduate origins relate to the **U.S. state location of first faculty appointments**

All results are descriptive and are not interpreted causally.

## Data description

### `data_transportation_faculty.xlsx`

This repository includes a copy of the faculty dataset used in the analysis, provided here in full to support **standalone reproducibility**.

Below we summarize the elements necessary to understand and reproduce the analyses in this project.

**Contents**

* `People`: faculty-level roster and education histories
* `University Rankings`: institution-level prestige tiers used to classify institutions

**First tenure-track hire convention**  
If `First_Hire` is missing, the faculty member’s **current institution is treated as their first tenure-track hire institution**.

**Primary origin measure used in this project**  
Analyses in this repository use **undergraduate country (`UG_Country`)** to characterize upstream geographic origins. PhD country is retained in the dataset for consistency with related work but is not the primary origin measure analyzed here.

The dataset contains no private or confidential information and is derived entirely from publicly available sources.

### `first_hire_school_to_state.csv`

This file provides an institution-level mapping from **first tenure-track hire institution to U.S. state**.

Each row maps an institution name to its U.S. state. State assignments are derived from the first tenure-track hire institution name in the faculty roster. When first tenure-track hire information is missing, the faculty member’s **current institution is used as a proxy**, consistent with the first tenure-track hire convention described above; the analysis notebook applies this fallback before joining to this crosswalk.

This file is used to support **state-level aggregation and geographic analyses** of faculty placement patterns.

## Analysis notebook

### `analysis.ipynb`

The Jupyter notebook reproduces all analyses and figures reported in the associated paper, including:

* Data cleaning and harmonization
* Geographic origin grouping based on UG country
* Aggregate composition plots
* Cohort trend analyses by PhD year
* Mapping and aggregation of first tenure-track hire outcomes by U.S. state

The notebook is intended to run end to end using the provided data files.

## Data sources and limitations

* Data were compiled from publicly available sources (departmental directories, laboratory pages, CVs, and professional profiles)
* The sample is restricted to transportation-focused faculty in CEE departments at U.S. universities included in the U.S. News civil engineering rankings
* Geographic origin reflects the **location of awarding institutions**, not citizenship or migration status

All results are descriptive summaries of observed patterns.

## Reproducibility

All results in the associated manuscript can be reproduced using the data files and notebook in this repository. No private, proprietary, or confidential data are used.

## Citation

If you use this dataset or code, please cite the paper:

> Bae, A. J. (2026). Global sources of the U.S. transportation research workforce. *Transportation Research Interdisciplinary Perspectives*, 38, 102096. https://doi.org/10.1016/j.trip.2026.102096

BibTeX:

```bibtex
@article{Bae2026GlobalSources,
  title     = {Global sources of the U.S. transportation research workforce},
  author    = {Bae, Andrew J.},
  journal   = {Transportation Research Interdisciplinary Perspectives},
  volume    = {38},
  pages     = {102096},
  year      = {2026},
  doi       = {10.1016/j.trip.2026.102096},
  publisher = {Elsevier},
}
```

A machine-readable [`CITATION.cff`](CITATION.cff) is also provided, from which GitHub renders a "Cite this repository" button.

## License

This repository is released for academic and research use. Redistribution of the anonymized data is permitted with attribution.
