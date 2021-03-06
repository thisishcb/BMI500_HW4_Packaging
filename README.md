# BMI500_HW4_Packaging

## Cluster and Packaging

### Chenbin Huang

## Run Main Program:
```
python run_packages.py
```


## Dataset
Dataset is the Iris dataset from sk-learn, which essentially is the datatset from [UCI Iris Data Set](https://archive.ics.uci.edu/ml/datasets/iris).  
The data set has150 datapoints with 4 attributes for each data point, and one label for each data point as its class.  
Other information included in the dataset are not used.  

## Algorithm
The data will be decompolized to 2D data with PCA and clustering with KMeans.  

## Performance Analysis
The estimated performance:
> test was done on cluster

* Timing: 1.506 s  
* CPU Usage: 2.3%  
* Mem Usage: 0.0909 G (approximatly 91M) 

*Performance may vary based on the actual environment that the program ran on.*

## Installation of the Package
### Install from cloud
try:
```
pip install https://github.com/soyhcb/BMI500_HW4_Packaging/raw/main/dist/BMI500HW4-0.0.2-py3-none-any.whl
```
or 
```
pip install https://github.com/soyhcb/BMI500_HW4_Packaging/raw/main/dist/BMI500HW4-0.0.2.tar.gz
```
install via `.whl` file is preferred in newer version of pip.

### Install from local

Clone the repository or download the `.whl` or `.tar.gz` file from `./dist/` folder, then run  
```
pip install {Path_To_File}
```
> you have to manually change `{Path_To_File}` to the actual path to file

## Requirements

This package requires  `scikit-learn` and `matplotlib` which will be automatically installed if the package is installed via `pip`.  
If memory and cpu allocation test is needed, `psutil` is also required. 
> `psutil` will not be installed with this package natively, because it has no affection to the main program. `psutil` should be manually installed via `pip` or `conda` only if performance test is required.

## Functions and Example

### Import 

to import the library correctly, try
```
from BMI500HW4.cluster import Cluster
```
if this fails, the package is noy installed correctly.

### Initialization
An instance should be created ar first to initialize data and other functions.  
```
clst = Cluster()
```
function `Cluster()` takes no parameters.

### Apply Kmeans
simply run 
```
clst.kmeans_sk()
```
will run the Kmeans algorithm and return the clustering results. the results will be stored. Run this function again will return the clusterig result rather than calculate again.  

### Predict
After the first time running of `kmeans_sk()`, the model is also stored, the cluster of 2d-array input can be calculated with `predict()`.  
Since the original data has four dimensions, the default input should has four dimensios for each data point. (four dimensional data will be transformed to 2-dimensional with the same PCA projection.)  
```
clst.predict([[1,2,3,4],[2,2,3,1],[10,10,10,10]])
```

### Visualization
The result can also be visualizaed, the visualization has two parameters:  
`groundtruth`: bool; False by default. If True, will plot the clusters with groundtruth. If False, will plot the predicted clusters by kmeans.  
`save`: str; None by default. Path to the file to save the figure. The figure will not be saved unless the path is specified.  
```
clst.visualization(False, "./fig.pdf")
```

### Examples
one example is provided as `run_packages.py`
```
python run_packages.py
```