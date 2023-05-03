# Synthesis of Alaska seismic models - Continental Lithosphere
This repository contains the data products from the Alaska synthesis paper on continental lithosphere, including crustal thickness models and velocity structural domains (domain outlines and key velocity cluster boundaries).

Reference of the paper: Yang, X., Mann, M., Fischer, K., Jadamec, M., Wei, S., Pavlis, G., & Schaeffer, A. (in review). Synthesis of the Seismic Structure of the Greater Alaska Region: Continental Lithosphere. AGU Monograph

## 1. Supplementary information file
The folder "summary_supplement_file" contains the summary file "AlaskaSynthesis_ContinentalLithosphere_SUPP.pdf" for all supplementary figures and Table S1. Table S1 is included in the summary file and as a separated excel table: "Table-S1_seismicnetworks.xlsx".

## 2. Data sets/products

### 2.1 Crustal thicknesses: this folder contains the average crustal thickness using single station measures and multi-station measurements.

* SingleStation_Mohodepths_final_nouncertainty.txt: the average of Moho depths from multiple models that provide single station measurements, including Veenstra et al. (2006), Rossi et al. (2006), Miller et al. (2018), Zhang et al. (2019), and Mann et al. (2022). Columns: latitude, longitude, depth (km)
* SingleStation_Mohodepths_final_withcertainty.txt: the average of Moho depths from multiple models with uncertainties considered in averaging. Columns: latitude, longitude, depth (km), std (km)
* MultiStation_Mohodepths_final_nouncertainty.txt: the average of Moho depths maps from multiple models that provide the Moho depths at binned grids, including Haney et al. (2020), Mann et al. (2022), and Gama et al. (2022a). Columns: latitude, longitude, depth (km)
* MultiStation_Mohodepths_final_withuncertainty.txt: the average of Moho depths maps from multiple models that provide the Moho depths at binned grids, with uncertainties considered in averaging. Columns: latitude, longitude, depth (km), std (km)

### 2.2 Products from velocity model clustering analysis.

* edges_allmodels_samegrid.pk: This is a Python pickle file containing the detected boundaries from the velocity clusters of eight shear-wave velocity models, including Ward and Lin (2018), Jiang et al. (2018), Martin-Short et al. (2018), Feng and Ritzwoller (2019), Berg et al. (2020), Yang and Gao (2020), Nayak et al. (2020), and Gama et al. (2022b). The data is stored in one dictionary that can be loaded as:

```python
with open('edges_allmodels_samegrid.pk','rb') as f:
    edgesall_samegrid=pickle.load(f)
depth_labels=list(edgesall_samegrid.keys())
for d in depth_labels:
	edges=edgesall_samegrid[d]
    vecx=edges['x']
    vecy=edges['y']
    		
    for e in range(len(edges['data'])):
        grad=edges['data'][e] #gradient data/matrix (2d) for each velocity model.
```

* boundary_crust.txt and boundary_mantle.txt: manually picked key structural lineaments (for crust and mantle) from the cluster boundaries with more than 3 votes (more than 3 velocit models have detected the boundaries). The file is good for GMT line plots in longitude and latitude order for each line segments.

* outlines_crust.txt and outlines_mantle.txt: manually picked key structural domains (for crust and mantle) outlined by the cluster boundary lineaments. The file is good for GMT line plots in longitude and latitude order for each outline/polygon.

* plots_domains.ipynb: Jupyter notebook to plot the key structural domains and boundaries. This notebook needs some utility functions (read GMT lines) from *SeisGo*, which can be installed with ```pip install seisgo```. See https://github.com/xtyangpsp/SeisGo.git for detailed instruction/introduction of *SeisGo*. It also needs *Cartopy* and *MATPLOTLIB* packages.

### 2.3 Major faults and terrane boundaries.
These files are from Colpron et al. (2007), downloaded from Yukon Geological Survey (https://data.geology.gov.yk.ca/Compilation/2#InfoTab).

## 3. Key references:
* Veenstra, E., Christensen, D. H., Abers, G. A., & Ferris, A. (2006). Crustal thickness variation in south-central Alaska. Geology, 34(9), 781–784. https://doi.org/10.1130/G22615.1

* Berg, E. M., Lin, F. C., Allam, A., Schulte-Pelkum, V., Ward, K. M., & Shen, W. (2020). Shear velocity model of Alaska via joint inversion of rayleigh wave ellipticity, phase velocities, and receiver functions across the Alaska transportable array. Journal of Geophysical Research: Solid Earth, 125 , e2019JB018582. 

* Colpron, M., Nelson, J. L., & Murphy, D. C. (2007). Northern Cordilleran terranes and their interactions through time. GSA Today, 17(4), 4. https://doi.org/10.1130/GSAT01704-5A.1

* Feng, L., & Ritzwoller, M. H. (2019). A 3-d shear velocity model of the crust and uppermost mantle beneath Alaska including apparent radial anisotropy. Journal of Geophysical Research: Solid Earth, 124 , 10468-10497. doi: 10.1029/2019JB018122

* Gama, I., Fischer, K. M., & Hua, J. (2022a). Mapping the Lithosphere and Asthenosphere Beneath Alaska With Sp Converted Waves. Geochemistry, Geophysics, Geosystems, 23(10), e2022GC010517. https://doi.org/10.1029/2022GC010517

* Gama, I., Fischer, K. M., Dalton, C. A., & Eilon, Z. (2022b). Variations in Lithospheric Thickness Across the Denali Fault and in Northern Alaska. Geophysical Research Letters, 49(24), e2022GL101256. https://doi.org/10.1029/2022GL101256

* Haney, M. M., Ward, K. M., Tsai, V. C., & Schmandt, B. (2020). Bulk Structure of the Crust and Upper Mantle beneath Alaska from an Approximate Rayleigh‐Wave Dispersion Formula. Seismological Research Letters, 91(6), 3064–3075. https://doi.org/10.1785/0220200162

* Jiang, C., Schmandt, B., Ward, K. M., Lin, F., & Worthington, L. L. (2018). Upper mantle seismic structure of Alaska from rayleigh and s wave tomography. Geophysical Research Letters, 45 , 10,350-10,359

* Mann, M. E., Abers, G. A., Daly, K. A., & Christensen, D. H. (2022). Subduction of an Oceanic Plateau Across Southcentral Alaska: Scattered-Wave Imaging. Journal of Geophysical Research: Solid Earth, 127(1). https://doi.org/10.1029/2021JB022697

* Martin-Short, R., Allen, R., Bastow, I. D., Porritt, R. W., & Miller, M. S. (2018). Seismic imaging of the Alaska subduction zone: Implications for slab geometry and volcanism. Geochemistry, Geophysics, Geosystems, 19 , 4541-4560.

* Miller, M. S., O’Driscoll, L. J., Porritt, R. W., & Roeske, S. M. (2018). Multiscale crustal architecture of Alaska inferred from P receiver functions. Lithosphere, 10(2), 267–278. https://doi.org/10.1130/L701.1

* Nayak, A., Eberhart-Phillips, D., Ruppert, N. A., Fang, H., Moore, M. M., Tape, C., Christensen, D. H., Abers, G. A., Thurber, C. H., Eberhart-Phillips, D., Ruppert, N. A., Fang, H., Moore, M. M., Tape, C., Christensen, D. H., Abers, G. A., & Thurber, C. H. (2020). 3D Seismic Velocity Models for Alaska from Joint Tomographic Inversion of Body‐Wave and Surface‐Wave Data. Seismological Research Letters, 91(6), 3106–3119. https://doi.org/10.1785/0220200214

* Rossi, G., Abers, G. A., Rondenay, S., & Christensen, D. H. (2006). Unusual mantle Poisson’s ratio, subduction, and crustal structure in central Alaska. Journal of Geophysical Research: Solid Earth, 111(B9), 9311. https://doi.org/10.1029/2005JB003956

* Ward, K. M., & Lin, F. C. (2018). Lithospheric structure across the alaskan cordillera from the joint inversion of surface waves and receiver functions. Journal of Geophysical Research: Solid Earth, 123 , 8780-8797. doi: 10.1029/2018JB015967

* Yang, X., & Gao, H. (2020). Segmentation of the Aleutian‐Alaska Subduction Zone Revealed by Full‐Wave Ambient Noise Tomography: Implications for the Along‐Strike Variation of Volcanism. Journal of Geophysical Research: Solid Earth, 125(11), 1–20. https://doi.org/10.1029/2020JB019677

* Zhang, Y., Li, A., & Hu, H. (2019). Crustal Structure in Alaska From Receiver Function Analysis. Geophysical Research Letters, 46(3), 1284–1292. https://doi.org/10.1029/2018GL081011
