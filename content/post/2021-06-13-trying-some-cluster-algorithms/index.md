---
title: Trying some Clustering Algorithms - Part 1
author: Toto
date: '2021-06-13'
slug: []
categories: ["R", "Cluster"]
tags:
  - Clusterization
  - R
meta_img: images/image.png
description: Studies about Clustering Algorithms
draft: false
---

# Introduction

The main reason for starting this study is a car parts problem. Here is the situation:

I have a thousands of service orders for vehicles and I want to understand what parts appear more often together. For example, what parts are frequently in the same service order as a, let's say, battery?


# Definition

Basically, we have a matrix with the relative frequencies between the components we want to cluster. This matrix is called _Adjacency Matrix_ and these characteristics lead us to a _non directed weighted graph approach_.

> A weighted graph or a network is a graph in which a number (the weight) is assigned to each edge. Such weights might represent for example costs, lengths or capacities, depending on the problem at hand. Such graphs arise in many contexts, for example in shortest path problems such as the traveling salesman problem.
>
> [Wikipedia](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)#Weighted_graph)


# Techniques for Clustering Weighted Graphs

Given the fact that I have no idea from where to start, I'm gonna try some existing R packages.

One widely used package is the [igraph Package](https://igraph.org/r/)

Reading the manual files, I've decided to go with walktrap, wich creates clusters based on short random walks between edges [igraph Walktrap](https://igraph.org/r/doc/cluster_walktrap.html).


First, let's experiment and understand the example from the documentation:

```{r, walktrap_example, echo = TRUE}
library(tidyverse)
library(igraph)
library(ggplot2)

g <- make_full_graph(5) %du% make_full_graph(5) %du% make_full_graph(5)
g <- add_edges(g, c(1,6, 1,11, 6, 11))
cluster_walktrap(g)
ggplot(g)
plot(g)

```

```{r echo=TRUE}
library(ggplot2)
ggplot(Orange, aes(x = age, 
                   y = circumference, 
                   color = Tree)) +
  geom_point() +
  geom_line() +
  guides(color = FALSE) +
  theme_bw()
```




