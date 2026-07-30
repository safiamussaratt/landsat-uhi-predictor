# Landsat UHI Predictor

Machine learning pipeline for predicting Urban Heat Island (UHI) intensity in Islamabad, Pakistan using Landsat-9 satellite imagery. The project derives NDVI, NDBI, and NDWI spectral indices via Google Earth Engine and benchmarks five models — Linear Regression, Random Forest, Gradient Boosting, MLP, and a 1D-CNN (PyTorch) — against Land Surface Temperature (LST).

## Research Article

A detailed research article covering the methodology and findings from this project is in progress and will be linked here once published.

## Overview

Urban Heat Islands occur when urban areas experience significantly higher temperatures than surrounding rural areas, largely due to land cover changes and reduced vegetation. This project builds a data science pipeline that:

1. Pulls Landsat-9 imagery for Islamabad from Google Earth Engine
2. Computes spectral indices that describe land cover characteristics:
   - **NDVI** (Normalized Difference Vegetation Index) — vegetation health/density
   - **NDBI** (Normalized Difference Built-up Index) — built-up/urban surfaces
   - **NDWI** (Normalized Difference Water Index) — surface water/moisture
3. Uses these indices as predictors of Land Surface Temperature (LST)
4. Trains and compares multiple machine learning models to determine which best predicts LST/UHI intensity

## Models Benchmarked

| Model | Type |
|---|---|
| Linear Regression | Classical/baseline |
| Random Forest | Ensemble (tree-based) |
| Gradient Boosting | Ensemble (tree-based) |
| MLP (Multi-Layer Perceptron) | Neural network |
| 1D-CNN (PyTorch) | Neural network |

## Data Source

- **Imagery:** Landsat-9 satellite data
- **Study area:** Islamabad, Pakistan
- **Processing platform:** Google Earth Engine (GEE)

## Repository Structure

```
landsat-uhi-predictor/
├── README.md
└── LICENSE
└── ds_project.ipynb   # Main notebook: data extraction, preprocessing, indices, modeling, evaluation
└── fig_eda.png
└── fig_eval.png
└── fig_hotspot.png
└── fig_rq_analysis.png
```

## Getting Started

### Prerequisites

- Python 3.x
- A Google Earth Engine account (for imagery/index extraction) — [sign up here](https://earthengine.google.com/)
- Jupyter Notebook / JupyterLab

### Suggested dependencies

```bash
pip install earthengine-api geemap numpy pandas scikit-learn torch matplotlib seaborn
```

### Running the project

1. Clone the repository:
   ```bash
   git clone https://github.com/safiamussaratt/landsat-uhi-predictor.git
   cd landsat-uhi-predictor
   ```
2. Authenticate with Google Earth Engine:
   ```python
   import ee
   ee.Authenticate()
   ee.Initialize()
   ```
3. Open and run `ds_project.ipynb` in Jupyter:
   ```bash
   jupyter notebook ds_project.ipynb
   ```

## Methodology

1. **Data acquisition** — Query Landsat-9 imagery over Islamabad via GEE
2. **Preprocessing** — Cloud masking, scaling, and band selection
3. **Feature engineering** — Compute NDVI, NDBI, and NDWI from spectral bands
4. **Target extraction** — Derive Land Surface Temperature (LST) from thermal bands
5. **Modeling** — Train and evaluate five models (Linear Regression, Random Forest, Gradient Boosting, MLP, 1D-CNN) to predict LST from the spectral indices
6. **Evaluation** — Compare model performance (e.g., RMSE, R²) to identify the strongest predictor of UHI intensity

## Results

See `ds_project.ipynb` for detailed evaluation metrics, visualizations, and model comparisons.

## License

This project is licensed under the [MIT License](LICENSE).

## Author

[safiamussaratt](https://github.com/safiamussaratt)
