# Consensus Clustering 

## Method

Algorithm is run multiple times to produce soft clusters. We want to find a final consensus clustering that represents the "consensus" across all clusterings. 


## Consensus Metrics

The following consensus metrics can be used. You would use these. **Median average deviation** most widely used, but it is biased towards symmetric distribution. (i.e. if your distrib is not symmetric, its not a reliable metric).

### Median average deviation

Source: http://amstat.tandfonline.com/doi/abs/10.1080/01621459.1993.10476408
Source: https://www.r-bloggers.com/absolute-deviation-around-the-median/

Defined as:

$$ MAD = b M_i (|x_i - M_j(x_j)|) $$

Specifically, perform this $MAD$ calculation on the COSINE DISTANCES between a pair of patients $a$ and $b$ from each run. 

-----

### Interquartile range

$(75th percentile) - (25th percentile)$

-----


### $S_n$

$S_n$ is an alternative to MAD. 

$$S_n = c ~ med_i \{med_j | x_i - x_j | \}$$.

For each $i$ we compute the median of $\{ | x_i - x_j |; j=1, ...n \}$. This yields $n$ numbers, the median of which gives our final estimate $S_n$. 

#### using $S_n$ in consensus clustering

For each run, we measure the cosine distance between two patients $i$ and $j$. Let $d_r$ be the cosine distnace between $i$ and $j$ in run $r$. We get the distance matrix

----


### $Q_n$

$Q_n$ is an alternative to MAD. Addresses the discontinuity issue that can happen with MAD and $S_n$. Here you are essentially replacing the median with the absolute value of the difference. 

$$ Q_n = d \{| x_i - x_j | ; i<j \}_{(k)} $$

----



from http://web.ipac.caltech.edu/staff/fmasci/home/astro_refs/BetterThanMAD.pdf

-------
-------

## Final consensus clustering on distance matrix

Once you get a distance matrix $M$, and consensus metric matrix $C$, $S_n$, $Q_n$, etc. 

1. Cluster $M$ using a clustering method of your choice
2. For each cluster evaluate the consensus metric:
	- to tell you consensus of each specific cluster
		* average $C$: average MAD for the people in the cluster (every person shoul dhave)
		* average $S_n$: average $S_n$ for all people in the cluster
		* average $Q_n$: average $Q_n$ for all people in the cluster
		* diameter of the cluster the patients are in
	- to tell you consensus of the *overall* final clustering
		* distance between the cluster centers


-----
-----

*Other stuff* 

* alternatives to MAD: 
	http://web.ipac.caltech.edu/staff/fmasci/home/astro_refs/BetterThanMAD.pd`



