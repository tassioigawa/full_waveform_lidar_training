[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1mwo_VEygStPw2yjnq87YEIjyxOjthsGl#scrollTo=LWtQkS-LeNTq)

# full\_waveform\_lidar\_training

ARSET Full Waveform LiDAR Training - Part 1 notebook: A comprehensive Python notebook for processing and analyzing NASA GEDI L1B (Global Ecosystem Dynamics Investigation Level 1B) full waveform LiDAR data using Google Colab.

## Overview

This repository provides tools for working with GEDI L1B geolocated waveform data to analyze forest structure and vegetation characteristics. GEDI is a full-waveform LiDAR instrument aboard the International Space Station that provides high-resolution observations of Earth's 3D structure between 51.6°N and 51.6°S latitudes.

-----

## Features

### Data Processing

  - Automated GEDI L1B data discovery using NASA Earthdata APIs
  - Spatial filtering by bounding box coordinates
  - Quality filtering for high-quality Full Power beam shots only (`BEAM0101`, `BEAM0110`, `BEAM1000`, `BEAM1011`)
  - Automatic retry mechanism to find granules with quality data in your area of interest
  - Smart file management with cleanup of files containing no useful data

### Analysis Capabilities

  - Statistical shot selection based on elevation characteristics (standard deviations from mean)
  - Individual waveform extraction and visualization for detailed analysis
  - Interactive mapping with satellite imagery basemap and shot location highlighting
  - Quality assessment with retention rate statistics and beam-specific analysis

### Visualizations

  - Elevation distribution analysis with statistical overlays
  - Individual waveform plots showing elevation profiles and amplitude returns
  - Interactive maps with elevation-colored shots and highlighted selections
  - Quality control dashboards showing processing success rates

-----

## Requirements

  - Google Colab or Jupyter Notebook environment
  - NASA Earthdata Login account (free registration required)
  - Python libraries: `earthaccess`, `h5py`, `geopandas`, `matplotlib`, `folium`

-----

## Quick Start

This section provides a detailed guide to setting up and running the GEDI L1B processing notebook in Google Colab from scratch.

### 0\. Open in Google Colab

Click the "Open in Colab" badge at the top of this README to launch the notebook directly in your browser.

### 1\. Clone the GitHub Repository

To access the notebook and any supplementary files, clone the repository into your Colab environment. Run the following command in a code cell:

```python
!git clone https://github.com/savcooley/full_waveform_lidar_training.git
```

### 2\. Install Required Libraries

Install the necessary Python libraries using pip. Run the following command in a code cell:

```python
!pip install earthaccess h5py geopandas matplotlib folium
```

### 3\. Mount Your Google Drive

Mounting your Google Drive allows the notebook to save output files and access data you may have stored. You will be prompted to authorize Colab to access your drive.

```python
from google.colab import drive
drive.mount('/content/drive')
```

### 4\. Authenticate with NASA Earthdata

To download GEDI data, you need a NASA Earthdata account. If you don't have one, you can [register for free](https://urs.earthdata.nasa.gov/users/new). Run the authentication cell in the notebook, which will prompt you for your Earthdata credentials.

### 5\. Define Your Study Area

Set your area of interest (AOI) by defining a bounding box with geographic coordinates.

```python
aoi_bbox = [min_longitude, min_latitude, max_longitude, max_latitude]
```

### 6\. Run the Notebook

Execute the remaining cells in the notebook to perform the data download, processing, and visualization.

-----

## Study Area Configuration

### Define your Area of Interest (AOI)

```python
aoi_bbox = [min_longitude, min_latitude, max_longitude, max_latitude]
```

### Example: Bankhead National Forest, Alabama

```python
aoi_bbox = [-87.41, 34.15, -87.35, 34.18]
```

-----

## Waveform Analysis

The notebook includes a specialized module for analyzing individual GEDI waveforms:

  - Select shots based on elevation characteristics (e.g., ±1.2 standard deviations from mean)
  - Extract and plot individual waveforms showing elevation vs. amplitude
  - Create interactive maps highlighting selected shots among all quality data
  - Analyze vegetation structure using raw L1B waveform returns

-----

## Applications

  - **Forest structure analysis**: Canopy height and vertical profile assessment
  - **Vegetation mapping**: Species classification and biomass estimation
  - **Terrain analysis**: Ground return identification and topographic mapping
  - **Algorithm development**: Testing new waveform processing approaches
  - **Educational purposes**: Learning full waveform LiDAR data analysis

-----

## GEDI Mission Information

The Global Ecosystem Dynamics Investigation (GEDI) is a NASA Earth science mission that provides global measurements of forest structure and topography. GEDI data helps scientists understand:

  - Forest carbon storage and dynamics
  - Biodiversity habitat characterization
  - Climate change impacts on ecosystems
  - Sustainable forest management practices

### Key Specifications:

  - **Spatial Resolution**: \~25m footprint diameter
  - **Coverage**: Global between 51.6°N and 51.6°S
  - **Temporal Coverage**: April 2019 - present (with gap from March 2023 - April 2024)
  - **Measurement Capability**: Full waveform returns with sub-meter vertical resolution

-----

## License

This project is open source and available under the [MIT License](https://www.google.com/search?q=https://github.com/savcooley/full_waveform_lidar_training/blob/main/LICENSE).
