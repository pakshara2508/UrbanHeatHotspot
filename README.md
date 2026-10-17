# 🌡️ UrbanHeatHotspots: Urban Heat Hotspot Predictor

### Identifying relatively warmer urban locations in Bengaluru using satellite data and machine learning.

## 📌 Project Overview

UrbanHeatHotspots is a machine-learning prototype designed to identify relatively warmer locations across a sampled area of Bengaluru, Karnataka, India.

Urban areas can experience elevated surface temperatures because of built-up surfaces, limited vegetation, and changes in land cover. This project uses satellite-derived environmental measurements and machine learning to explore the spatial distribution of land surface temperature and identify potential heat hotspots.

The project includes an interactive dashboard for visualizing temperature patterns, vegetation, built-up surface indicators, and model predictions.

## 🎯 Objectives

- Analyze satellite-derived land surface temperature across sampled locations in Bengaluru.
- Explore the relationship between surface temperature, vegetation, and built-up surface characteristics.
- Train a machine-learning model to estimate land surface temperature.
- Identify relatively warmer sampled locations for further investigation.
- Present results through an interactive visualization dashboard.

## 🛰️ Data Sources

**Primary data source:** USGS Landsat 8 Collection 2 Level-2 imagery, accessed and processed using Google Earth Engine.

- [Google Earth Engine](https://earthengine.google.com/)
- [USGS Landsat Missions](https://www.usgs.gov/landsat-missions)
- [Landsat 8 Collection 2 Level-2 dataset documentation](https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2)

The project uses Landsat imagery from 2025 to derive environmental measurements for sampled locations in Bengaluru.

### Variables

| Variable | Description |
|---|---|
| Latitude | Latitude of the sampled location |
| Longitude | Longitude of the sampled location |
| LST_C | Estimated land surface temperature in degrees Celsius |
| NDVI | Normalized Difference Vegetation Index, an indicator of vegetation |
| NDBI | Normalized Difference Built-up Index, an indicator associated with built-up surfaces |

The sampled data was exported from Google Earth Engine and processed using Python.

## 🤖 Machine Learning Approach

The project uses a **Random Forest Regression** model implemented with scikit-learn.

### Model inputs
- Latitude
- Longitude
- NDVI
- NDBI

### Prediction target
- Land surface temperature (`LST_C`)

### Model evaluation

In one spatial validation experiment, the model using latitude, longitude, and NDVI was compared with a model that also included NDBI.

| Model | Mean Absolute Error (MAE) | R² Score |
|---|---:|---:|
| Without NDBI | 1.168°C | -0.001 |
| With NDBI | 0.830°C | 0.446 |

In this experiment, adding NDBI reduced the MAE by approximately 29%.

These results come from one geographic holdout and should be treated as preliminary rather than evidence of performance across all locations or dates.

## 🗺️ Interactive Dashboard

The JupyterLab dashboard provides visualizations for:

- Observed land surface temperature
- Observed heat hotspots
- Predicted land surface temperature
- Predicted hotspots
- NDVI vegetation patterns
- NDBI built-up surface indicators
- Model performance comparisons
- Individual sampled-location values

The hotspot threshold is defined as the 80th percentile of observed land surface temperatures in the sampled dataset.

## 🛠️ Technologies Used

- Python
- JupyterLab
- Google Earth Engine
- pandas
- NumPy
- scikit-learn
- Matplotlib
- ipywidgets
- Joblib

## 📂 Project Files

The repository contains the project's code, processed data, and trained model, depending on the files uploaded.

- `.ipynb` — Jupyter Notebook containing project code and/or dashboard.
- `urban_heat_data_improved.csv` — Processed dataset.
- `urban_heat_model_improved.pkl` — Saved Random Forest model.
- `README.md` — Project documentation.

## 🚀 How to Run the Project

1. Install Python and JupyterLab.
2. Install the required libraries:

   ```bash
   pip install pandas numpy scikit-learn matplotlib ipywidgets joblib
   ```

3. Download or clone this repository.
4. Place the notebook, CSV dataset, and saved model in the appropriate working directory.
5. Open the notebook in JupyterLab.
6. Run the notebook cells in order, beginning with the setup and data-loading cells.
7. Follow the notebook instructions to display the interactive dashboard.

Additional setup may be required depending on the notebook's imports and environment.

## ⚠️ Limitations

- Land surface temperature is not the same as air temperature measured by a weather station.
- The analysis uses satellite imagery from a limited time period rather than continuous observations.
- Hotspots are defined relative to the sampled dataset's 80th-percentile temperature threshold, not an official public-health danger threshold.
- NDBI is an indicator of built-up surface characteristics, not a direct measurement of building density.
- The reported validation metrics come from one geographic holdout.
- The model has not been established as a real-time forecasting or public-health warning system.
- Additional dates, geographic validation regions, and independent ground observations would be needed for stronger evaluation.

## 🔮 Future Improvements

- Validate the model across multiple dates and geographic regions.
- Incorporate additional environmental and urban land-cover data.
- Improve cloud and image-quality filtering.
- Compare model performance using additional evaluation methods.
- Develop a more accessible web-based dashboard.
- Explore independent ground-based temperature observations for validation.

## 👥 Intended Users

The prototype may support exploratory analysis by students, researchers, urban planners, and environmental analysts investigating urban surface-temperature patterns.

## 📚 References

1. Google Earth Engine: https://earthengine.google.com/
2. USGS Landsat Missions: https://www.usgs.gov/landsat-missions
3. Landsat 8 Collection 2 Level-2 Dataset: https://developers.google.com/earth-engine/datasets/catalog/LANDSAT_LC08_C02_T1_L2
4. scikit-learn Random Forest Regressor: https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html

---

**UrbanHeatHotspots** is an exploratory machine-learning prototype demonstrating how satellite-derived environmental data can help analyze urban surface-temperature patterns.
