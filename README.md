# Particulate Matter Capture by Urban Trees in Dublin

Replication package for the capstone thesis *Particulate matter capture by urban trees
in Dublin: species variation, leaf trait drivers and implications for urban forestry*
(Conor Walsh, Trinity College Dublin).

This repository contains the R analysis, the QGIS project, and the cleaned datasets
needed to reproduce the figures, tables and statistical results reported in the thesis.

## What this study does

The study uses Witness Tree Project (WTP) SEM-EDX particle data from two botanic gardens
(Trinity College Botanic Garden, TCDBG, 2022–2025; National Botanic Gardens Glasnevin,
NBG, 2024–2025) to compare how 21 tree species capture airborne PM10 and PM2.5. It tests
whether leaf traits (trichomes, surface texture, leaf size, leaf angle, leaf habit,
canopy density) explain interspecific differences in capture, fits linear mixed-effects
models with species as a random effect, ranks species by a composite performance score,
and sets the results against a city-wide QGIS analysis of how close Dublin's street trees
sit to major roads.

## Repository structure

```
.
├── README.md
├── LICENSE
├── .gitignore
├── Witness_tree_analysis_R.Rmd        Main analysis notebook (run this)
├── Witness_Tree_analysis.qgz          QGIS project (road-exposure / spatial analysis)
├── sessionInfo.txt                    R version and exact package versions used
└── data/
    ├── clean_data/
    │   ├── NBGall.xlsx                 Cleaned NBG PM data
    │   └── masters_all_years.xlsx     Cleaned TCDBG PM data (all years)
    ├── witness_tree_qgis.csv          Per-species summary used in the map figures
    └── traits_clean.csv               Species-level leaf trait classifications
```

## How to reproduce

1. Install R (version 4.4 or later) and RStudio.
2. Clone or download this repository and open it as the working directory (open the
   `.Rmd` in RStudio; the working directory should be the repository root).
3. Open `Witness_tree_analysis_R.Rmd`. The first code chunk installs any missing
   packages automatically, so no manual package setup is needed.
4. Knit the notebook, or run the chunks in order from top to bottom. Figures and tables
   are written to `data/outputs/` (created automatically on the first run).

The notebook reads the four data files in `data/`. It sets a random seed (`set.seed(42)`)
so results are reproducible.

## Software

- R 4.4 or later
- Key packages: tidyverse, ggplot2, lme4, lmerTest, emmeans, performance, rstatix,
  viridis, patchwork, broom. A full list with versions is in `sessionInfo.txt`.
- QGIS 3.40.4 for the spatial analysis.

## Spatial analysis note

`Witness_Tree_analysis.qgz` is the QGIS project file. It stores the layer styling and
map layouts but not the underlying spatial layers. The source tree datasets are the
publicly available local-authority records:

- Dublin City Council tree dataset: https://data.gov.ie/dataset/trees
- Dún Laoghaire–Rathdown, South Dublin and Fingal County Council open tree datasets
  (available from the respective council open-data portals and data.gov.ie)

Road network data is from OpenStreetMap. To rebuild the spatial analysis, add these
layers to the QGIS project and re-run the road-distance classification described in
Section 2.5 of the thesis.

## Data availability

The cleaned PM datasets in this repository are derived summaries of the Witness Tree
Project SEM-EDX exports. The raw SEM-EDX export files are held by the Witness Tree
Project and are available on request. For questions about the data or the analysis,
contact the author.

## Citation

If you use this code or data, please cite the thesis:

> Walsh, C. (2025) *Particulate matter capture by urban trees in Dublin: species
> variation, leaf trait drivers and implications for urban forestry.* Capstone thesis,
> Trinity College Dublin.

## Acknowledgements

This work uses data from the Witness Tree Project, Trinity College Botanic Garden and the
National Botanic Gardens, Glasnevin. SEM-EDX imaging was carried out at the iCRAG
laboratory, Trinity College Dublin.

## Licence

Code is released under the MIT Licence (see `LICENSE`). The datasets are shared for the
purpose of reproducing this study; please contact the author and credit the Witness Tree
Project before reusing them in other work.
