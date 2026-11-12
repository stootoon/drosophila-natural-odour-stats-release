# drosophila-natural-odour-stats-release
Some analysis code for Gong et al. 2027 

## Installation

```bash
git clone https://github.com/stootoon/drosophila-natural-odour-stats-release.git
cd drosophila-natural-odour-stats-release
pip install -e .
```

This installs the `dnos` package and its dependencies.

## Data

The GC-MS odour data are read directly from a public Google Sheet (see
`dnos/src/data.py` and `dnos/src/ripeness.py`), so an internet
connection is needed the first time each notebook is run.

## Layout

```
dnos/
  src/
    data.py        loaders for the noni (D. sechellia), pandan (D. erecta) and D. melanogaster datasets
    common.py      odour selectors (PC score, variance, random), figure helpers
    erecta.py      pandan ripeness classification (L1 logistic regression + odour selectors)
    sechellia.py   noni ripeness regression (Lasso + odour selectors), PC1-derived ripeness
    ripeness.py    noni ripeness on independently-assessed fruit: classification and regression variants
    paths.py       output paths
    label_axes.py  figure panel labelling (vendored from https://github.com/stootoon/label_axes)
    chem_pca_plus_PCscore.m   original MATLAB implementation of the PC score
  analyses/
    erecta-demo.ipynb          runs the pandan analysis and makes figs/erecta*.pdf
    sechellia-demo.ipynb       runs the noni analysis and makes figs/sechellia*.pdf
    ripeness-demo.ipynb        runs the independent-ripeness analysis and makes figs/ripeness*.pdf
    noni-random-forest.ipynb   random-forest classification of fruit type from shared odours
  figs/                        figure outputs
```

Run any notebook from `dnos/analyses/` with Jupyter; each regenerates
its figures into `dnos/figs/`.
