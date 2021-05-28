segundo previo
================

## nombre: ZHARICK SALDAÑA

## codigo: 1950085

## introduccion

La base de datos Theoph, tiene 132 filas y 5 columnas de datos de un
experimento sobre la farmacocinética de la teofilina. Boeckmann, Sheiner
y Beal (1994) informan datos de un estudio del Dr. Robert Upton sobre la
cinética del fármaco antiasmático teofilina. Doce sujetos recibieron
dosis orales de teofilina y luego se midieron las concentraciones
séricas en 11 puntos de tiempo durante las siguientes 25 horas. Y las
variables están representadas en la data de la siguiente manera: -
Subject: un factor ordenado con niveles 1, …, a 12 e identifica al
sujeto sobre el que se realizó la observación. El orden se da según como
va aumentando la concentración máxima de teofilina observada. - Wt: peso
del sujeto (kg). - Dose: dosis de teofilina administrada por vía oral al
sujeto (mg / kg). - Time: tiempo desde la administración del fármaco
cuando se extrajo la muestra (horas). - conc: concentración de teofilina
en la muestra (mg / L).

## primer punto:

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.3     v purrr   0.3.4
    ## v tibble  3.1.1     v dplyr   1.0.6
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   1.4.0     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(dplyr)
```

## base de datos de teofilina

agrupada por sujetos de estudio

en la tabla de tiempo podemos observar quien tiene mayor y menor
promedio, podemos ver que el de mayor prmedio es el sujeto 1 con: 5,95;
y el de menor promedio el del sujeto 7 con: 5,865455.

## tiempo de toma de muestra vs concentracion (teofilina)

``` r
library(tidyverse)
DF1 <- mutate(Theoph, Razon_Time_conc=Time/conc)
Conglomerado_tiempo <- DF1 %>%dplyr::filter(Time>=0.25 & Time<=1)
library(dplyr)
DF2 <- DF1 %>% select(Time, Dose) %>% summarize_all(sd)
```

en la tabla DF2 obervamos la variacion estandar de los sujetos en este
tiempo, los resultados obtenidos son: tiempo de 6.925952 y dosis de
0.7180742.

## promedio de concentracion

``` r
library(dplyr)
library(tidyverse)
DF3 <- DF1 %>% select(Time, Wt) %>% summarize_all(sd)
```

en la tabla DF3 podemos observar una comparacion entre el tiempo y el
peso del sujeto (Kg) obtenindo una desviacon estandar o sd: time
6.925952 y weight 9.133181
