# Topographic Potential Tool (Python)

**Developer:** [Yan Zhong](https://sites.google.com/view/yanzhong-geo), [University of Geneva](https://c-cia.ch/)  
**E-mails:** yan.zhong@unige.ch | yan.zhong.geo@gmail.com  
**Toolbox file:** `Topographic Potential Python.atbx`  
**Last updated:** 22.01.2026  
**Language:** English  
**Coding language:** Python  
**Operating System:** Windows (ArcGIS 10.0 or later, including ArcGIS Pro)  
**Installation Time:** ~1 second  

---
## Overview
This Python script extracts **topographic potential (TP) areas** from a DEM using point locations and a **area of interest (AOI)**.  

For each input point, the script:  
1. Snaps the point to the nearest **flow accumulation maximum**.  
2. Delineates the **watershed**.  
3. Calculates **minimum elevation** in the watershed.  
4. Computes **flow length** and **slope (tan α)**.  
5. Filters flow paths by **AOI** and slope thresholds (`tan_min`, `tan_max`).  
6. Saves a TP raster per point.

---

## Inputs

| Parameter | Type | Description |
|-----------|------|-------------|
| DEM | Raster | Digital Elevation Model |
| Flow Direction | Raster | D8 flow direction raster |
| ROI | Raster | Region of interest mask |
| Points | Point Feature Class | Pour points for extraction |
| tan_min | Float (optional) | Minimum slope threshold (default = 0.1) |
| tan_max | Float (optional) | Maximum slope threshold (default = 1.5) |
| Output Folder | Folder | Directory to save TP rasters |
| snap_dist | Float (optional) | Snap distance in meters (default = 500) |

---

## Outputs

| Output | Type | Description |
|--------|------|-------------|
| TP_<OID>.tif | Raster | Slope-filtered topographic potential raster for each point |

---

## Workflow

1. Prepare DEM, flow direction, AOI, and points.  
2. Set parameters (`tan_min`, `tan_max`, `snap_dist`, output folder).  
3. Run the script:  
   - Snap points → Delineate watershed → Compute min elevation → Calculate flow length → Filter by slope & ROI → Save TP raster.  
4. Check output folder for `TP_<OID>.tif` rasters.  

> Notes: Warnings appear if no pixels meet slope criteria for a point.

