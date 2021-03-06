# README.md #

Last updated: 20190410 <br>
Contact Name: Sheila Saia <br>
Contact Email: ssaia at ncsu dot edu <br>

This is the README file for the spatial directory (swat_svi_python_anlysis > data > spatial) of the GitHub repository titled ['paper-yadkin-swat-svi-study'](https://github.com/sheilasaia/paper-yadkin-swat-svi-study). For additional details on these data and the associated publication, visit the perviously mentioned GitHub repository.

## 1. Data Availability ##
Data assocated with the spatial directory is available for download on [Google Drive](https://drive.google.com/drive/folders/1zWioj-AI2iY1CkmvYIksyQNnrpdL3i_B?usp=sharing).

## 2. File Descriptions & Metadata ##

**Filename**: yadkin\_subs\_albers.shp <br>
**Short description**: This shape file contains the 28 YPD subbasin boundaries as delineated by SWAT. This file was generated by SWAT and then projected to the United States of America Contiguous Albers Equal Area Conic USGS projection to ensure more accurate area calculations later on. <br>
**Metadata**: We obtained the Yadkin-Pee Dee River Watershed (YPD) subbasin boundaries from [Suttles et al. (2018)](https://www.fs.usda.gov/treesearch/pubs/56780), projected these boundaries to USA Contiguous Albers Equal Area Conic USGS projection using ESRI ArcGIS, and calculated the area of each subbasin. 'Area' column is in units of hectares. 'AREA_KM2' was calculated by dividing 'Area' by 100 using the raster calculator; thus, it is in units of km<sup/>2</sup>. <br>
**Variable Descriptions**:<br>
'OBJECTID' - YPD subbasin number, ranges from 1 to 28
'GRIDCODE' - YPD subbasin number, ranges from 1 to 28
'Subbasin' - YPD subbasin number, ranges from 1 to 28
'Area' - Subbasin area (hectares)
'AREA_KM2' - Subbasin area (km<sup/>2</sup>)<br>

**Filename**: yadtracts\_30m <br>
**Short description**: This raster file contains the boundaries of census tracts within the YPD watershed at a 30 x 30m resolution. <br>
**Metadata**: We downloaded the US-wide 2010-2014 census tract SVI data from the ATSDR website (https://svi.cdc.gov/data-and-tools-download.html) and projected this to USA Contiguous Albers Equal Area Conic USGS projection using ESRI ArcGIS. We then clipped the US-wide census tract SVI data to the YPD boundary (see out-most boundary of yadkin\_subs\_albers.shp). Last we used ESRI ArcGIS to convert this vector data to a 30 x 30 m grid where each raster value corresponds to the US census tract [FIPS code](https://www.census.gov/quickfacts/fact/note/US/fips).  <br>
**Variable Descriptions**:<br>
'Rowid' - Row identificaion number<br>
'VALUE' - Arbitrary number assigned to each unique census tract <br>
'COUNT' - Number of 30 x 30 m grid cells per census tract<br>
'GEOID' - Census tract FIPS number as assinged by the US Census<br>
'AREA_KM2' - Area of the full census tract (km<sup/>2</sup>)<br>
'YAD_AREA_KM2' - Area of census tract in the YPD (km<sup/>2</sup>), note that some census tracts lay on the edge of the YPD boundary such that this area is smaller than 'AREA_KM2'<br>

**Filename**: yadlu\_1992.tif <br>
**Short description**: This raster file contains the 1992 National Land Cover Dataset (NLCD) land use classes for the YPD watershed at a 30 x 30m resolution. <br>
**Metadata**: We downloaded 1992 NLCD dataset from the website (https://catalog.data.gov/dataset/usgs-national-land-cover-dataset-nlcd-downloadable-data-collection) at a 30 x 30 m resultion grid. The projection of this file is USA Contiguous Albers Equal Area Conic USGS. We used a raster mask of the YPD boundary (see out-most boundary of yadkin\_subs\_albers.shp) along with the ESRI ArcGIS 'extract by mask tool' to select NLCD data for the YPD only. We used the raster calculator equation '([COUNT] x 30 x 30)/(1000 x 1000)' to find the to find the area ('AREA_KM2') in km<sup/>2</sup> of each land use in the YPD. We calculated percent area for each land use (AREA_PERC) use using the equation '([AREA_KM2] / (19748195 x 30 x 30) / (1000 x 1000)) x 100'. There are a total of 19748195 cells in the YPD. See 1992 NLCD metadata (https://catalog.data.gov/dataset/usgs-national-land-cover-dataset-nlcd-downloadable-data-collection) for complete description of the land uses classes included in this dataset. <br>
**Variable Descriptions**:<br>
'OID' - Row identification number<br>
'VALUE' - 1992 NLCD land use class value<br>
'COUNT' - Number of 30 x 30 m grid cells in each NLCD land use class<br>
'DESCRIPTIO' - 1992 NLCD land use class description <br>
'AREA_KM2' - total area of land use in each class in the YPD (km<sup/>2</sup>)<br>
'AREA_PERC' - percentage of each land use class in the YPD (%)<br>

**Filename**: yadlurec\_1992 <br>
**Short description**: This raster file was created using by reclassifying (i.e., combining) land use categories from yadlu\_1992.tif so they could be compared to the 2060 data. We used the ESRI ArcGIS raster calculator and exported the summary table to caculate watershed wide land use classes and save these data to yadkin\_lu\_baseline\_reclass\_1992.txt (see 2.5.2).<br>
**Metadata**: We used the ESRI ArcGIS 'reclassify' tool to reclass yadlu\_1992.tif land use  so they could be compared to projected land use data. The agriculture class includes 1992 NLCD classes 82, developed class includes 1992 NLCD classes 21-23, and 85, lowland hardwood includes 1992 NLCD classes 91, mixed forest includes 1992 NLCD classes 43, nonstocked includes 1992 NLCD classes 31-33 and 81, pine includes 1992 NLCD classes 42, upland hardwood includes 1992 NLCD classes 41, water includes 1992 NLCD classes 11, and wetland includes 1992 NLCD classes 92 (see yadlu\_1992.tif attribute data or NLCD metadata for description of each 1992 NLCD land use class value). The projection of this file is USA Contiguous Albers Equal Area Conic USGS.
 <br>
**Variable Descriptions**:<br>
'Rowid' - Row identification number
'VALUE' - Reclassified (i.e., to match projection classes) land use value.<br>
'COUNT' - Number of 30 x 30 m grid cells in each reclassified (i.e., to match projection classes) land use class<br>
'DESCRIPTIO' - Reclassified (i.e., to match projection classes) land use description <br>
'AREA_KM2' - total area of land use in each class in the YPD (km<sup/>2</sup>)<br>
'AREA_PERC' - percentage of each land use class in the YPD (%)<br>


**Filename**: yadluA\_2060.tif <br>
**Short description**: This raster file represents the 2060 land use under the MIROC 8.5 scenario as described in Saia et al. (2019) and [Suttles et al. (2018)](https://www.fs.usda.gov/treesearch/pubs/56780). These data came from the USFS Southern Research Station's Forest Futures report as described in further detail in Saia et al. (2019) and Suttles et al. (2018). We used the ESRI ArcGIS raster calculator and exported the summary table to caculate watershed wide land use classes and save this data to yadkin\_lu\_miroc8\_5\_2060.txt (see 2.5.2).<br>
**Metadata**: These data were obtained from the US Forest Service Southern Research Station Forest Futures project as described in Suttles et al. (2018) and Saia et al. (2019) and are associated with the Cornerstone A scenario. See the associated GitHub repository [('paper-yadkin-swat-svi-study')](https://github.com/sheilasaia/paper-yadkin-swat-svi-study) for more information. The projection of this file is USA Contiguous Albers Equal Area Conic USGS. <br>
**Variable Descriptions**:<br>
'Rowid' - Row identification number
'VALUE' - Land use value.<br>
'COUNT' - Number of 30 x 30 m grid cells in each reclassified land use class<br>
'DESCRIPTIO' - Land use description <br>
'AREA_KM2' - total area of land use in each class in the YPD (km<sup/>2</sup>)<br>
'AREA_PERC' - percentage of each land use class in the YPD (%)<br>

**Filename**: yadluB\_2060.tif <br>
**Short description**: This raster file represents the 2060 land use under the CSIRO 8.5 scenario as described in Saia et al. (2019) and [Suttles et al. (2018)](https://www.fs.usda.gov/treesearch/pubs/56780). These data came from the USFS Southern Research Station's Forest Futures report as described in further detail in Saia et al. (2019) and Suttles et al. (2018). We used the ESRI ArcGIS raster calculator and exported the summary table to caculate watershed wide land use classes and save this data to yadkin\_lu\_csiro8\_5\_2060.txt (see 2.5.2).<br>
**Metadata**: These data were obtained from the US Forest Service Southern Research Station Forest Futures project as described in Suttles et al. (2018) and Saia et al. (2019) and are associated with the Cornerstone B scenario. See the associated GitHub repository [('paper-yadkin-swat-svi-study')](https://github.com/sheilasaia/paper-yadkin-swat-svi-study) for more information. The projection of this file is USA Contiguous Albers Equal Area Conic USGS. <br>
**Variable Descriptions**:<br>
'Rowid' - Row identification number
'VALUE' - Land use value.<br>
'COUNT' - Number of 30 x 30 m grid cells in each reclassified land use class<br>
'DESCRIPTIO' - Land use description <br>
'AREA_KM2' - total area of land use in each class in the YPD (km<sup/>2</sup>)<br>
'AREA_PERC' - percentage of each land use class in the YPD (%)<br>

**Filename**: yadluC\_2060.tif <br>
**Short description**: This raster file represents the 2060 land use under the CSIRO 4.5 scenario as described in Saia et al. (2019) and [Suttles et al. (2018)](https://www.fs.usda.gov/treesearch/pubs/56780). These data came from the USFS Southern Research Station's Forest Futures report as described in further detail in Saia et al. (2019) and Suttles et al. (2018). We used the ESRI ArcGIS raster calculator and exported the summary table to caculate watershed wide land use classes and save this data to yadkin\_lu\_csiro4\_5\_2060.txt (see 2.5.2).<br>
**Metadata**: These data were obtained from the US Forest Service Southern Research Station Forest Futures project as described in Suttles et al. (2018) and Saia et al. (2019) and are associated with the Cornerstone C scenario. See the associated GitHub repository [('paper-yadkin-swat-svi-study')](https://github.com/sheilasaia/paper-yadkin-swat-svi-study) for more information. The projection of this file is USA Contiguous Albers Equal Area Conic USGS. <br>
**Variable Descriptions**:<br>
'Rowid' - Row identification number
'VALUE' - Land use value.<br>
'COUNT' - Number of 30 x 30 m grid cells in each reclassified land use class<br>
'DESCRIPTIO' - Land use description <br>
'AREA_KM2' - total area of land use in each class in the YPD (km<sup/>2</sup>)<br>
'AREA_PERC' - percentage of each land use class in the YPD (%)<br>

**Filename**: yadluD\_2060.tif <br>
**Short description**: This raster file represents the 2060 land use under the Hadley 4.5 scenario as described in Saia et al. (2019) and [Suttles et al. (2018)](https://www.fs.usda.gov/treesearch/pubs/56780). These data came from the USFS Southern Research Station's Forest Futures report as described in further detail in Saia et al. (2019) and Suttles et al. (2018). We used the ESRI ArcGIS raster calculator and exported the summary table to caculate watershed wide land use classes and save this data to yadkin\_lu\_hadley4\_5\_2060.txt (see 2.5.2).<br>
**Metadata**: These data were obtained from the US Forest Service Southern Research Station Forest Futures project as described in Suttles et al. (2018) and Saia et al. (2019) and are associated with the Cornerstone D scenario. See the associated GitHub repository [('paper-yadkin-swat-svi-study')](https://github.com/sheilasaia/paper-yadkin-swat-svi-study) for more information. The projection of this file is USA Contiguous Albers Equal Area Conic USGS. <br>
**Variable Descriptions**:<br>
'Rowid' - Row identification number
'VALUE' - Land use value.<br>
'COUNT' - Number of 30 x 30 m grid cells in each reclassified land use class<br>
'DESCRIPTIO' - Land use description <br>
'AREA_KM2' - total area of land use in each class in the YPD (km<sup/>2</sup>)<br>
'AREA_PERC' - percentage of each land use class in the YPD (%)<br>

## 3. scratch Directory ##
This folder is intentially left blank as it is required to run the Python scripts included in this GitHub repository. See the associated GitHub repository [('paper-yadkin-swat-svi-study')](https://github.com/sheilasaia/paper-yadkin-swat-svi-study) for more information.
