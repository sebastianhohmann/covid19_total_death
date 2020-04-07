# covid19_total_death
Estimating Covid-19 mortality from official statistics on total deaths

Analysis by 

- Andrea Galeotti (https://andreagaleottiblog.wordpress.com/)

- Sebastian Hohmann (https://sebastianhohmann.github.io/)

- Paolo Surico (https://sites.google.com/site/paolosurico/)

Additional contributors

- Luis Fonseca (https://luispfonseca.com/) for the analysis of Portugal

- Riccardo Trezzi for the analysis of Italy

Objective

This project aims at estimating Covid-19 mortality from official statistics on total deaths. We aim to constantly update the analysis as new data becomes available. We also aim to add robustness checks and alternative estimates in an effort to accurately determine Covid-19 deaths. The results of the analysis are regularly updated in this [article](https://www.dropbox.com/s/tkusww74gd5qbzc/DeathCount_final_GHS.pdf?dl=0).

We would like to replicate the analysis for as many countries as possible. If you have data or you know where we can access data in a country, please share them with us. We are happy to replicate the analysis, share the results with you, and update the analysis so that other people can access this information.
If you have the data and you want to perform the analysis yourself, in what follows you will find all material you need. However, we would appreciate if you share with us the results, with a summary of how you conducted the analysis. In particular, with explicit reference to changes in the codes or methodology. This is to assure that results are comparable across countries. 
 
Methodology

We estimate Covid-19 mortality for several countries. We always use two inputs:

(i) Official numbers for total mortality (not just Covid-19) in a country. 

(ii) Official numbers for total Covid-19 mortaliy. 

We carry out the following steps:

1) Taking as the starging point the day of the year before the first Covid-19 death, we compute, for each of the years 2015-2020, the cumulative total of deaths. 

2) Using the cumulative totals, we compute daily growth rates for each year 2015-2019. 

3) We take the average of the growth rates of the previous five years. (An earlier version of our work had reversed steps 2) and 3), that is rather than computing growth for each of the past five years separately and then averaging, we first averaged the cumulative totals and computed the daily growth from this. This change alters our results only very marginally. Please see the commit history of this repository for the earlier versions). 

4) We fix the number of people that died on the day before the first Covid-19 death was recorded in 2020 and extrapolate this number forward using the average growth rate computed in 3). This yields what we  call the "counterfactual" for 2020. 

5) We add the official number of Covid-19 deaths from (ii) to the counterfactual created in 4).

6) The difference between the actually observed total number of deaths in (i) and the counterfactual in 4) is our estimate for Covid-19 mortality. The difference between (i) and 5) are excess deaths in 2020 that are not designated official Covid-19 deaths.

Please see the folders for each country for examples on how this method is implemented in python.