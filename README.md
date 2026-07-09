# Spatial Optimization and Travel Demand Analysis of Urban Ropeway Integration

## Project Overview
This repository contains the computational framework and spatial analysis codebase for evaluating the travel demand implications of introducing an aerial ropeway as a supplementary transit mode in a constrained urban environment. The core objective is to simulate traffic flow dynamics and map spatial demand constraints using open-source mapping data and raster-based population layers. 

## Methodology
The computational framework transforms static spatial data into a dynamic routing environment:
* Spatial Mapping: Demand data relies heavily on mapping destination points to accurately reflect traffic convergence. For localized modeling, K-Means clustering was applied to a sample population to derive 69 representative centroids.
* Network Construction: OpenStreetMap road networks are extracted and mapped as directed graphs using OSMnx.
* Baseline Routing: Shortest-path routing is computed using Dijkstra's algorithm across the network.
* Constraint Modeling & Comparison: The transit intervention is modeled by imposing strict surface constraints on the underlying corridors. Edge-by-edge comparisons of the pre- and post-constraint networks classify roads into Demand Relief (Green), Demand Gain (Red), and Unchanged (Blue) categories.  

## Key Results & Demand Redistribution
The spatial optimization model successfully simulated the network disruption caused by the transit integration at both a localized and macro-district scale.
### Micro-Scale Model (Sample Data Integration):
The localized model analyzed a network graph of 5,835 edges.  
* Demand Relief (Green): 896 edges (15.35% of the network) experienced reduced traffic, successfully diverting 4,156 units of demand away from congested baseline routes.
* Demand Increase (Red): 1,885 edges (32.31% of the network) absorbed 4,932 units of diverted demand. These edges show high concentration along parallel lanes and perpendicular approach roads.
* Unchanged (Blue): 3,054 edges (52.34% of the network) remained unaffected by the intervention.
### Macro-Scale Model (GHSL District Scale-Up):
Scaling up the model using the 200m resolution Global Human Settlement Layer (GHS-POP) expanded the graph to 36,971 total edges.
* Demand Relief (Green): The relief footprint drastically expanded to 18,459 edges (49.93% of the network). This displaced 2,757,017 routed paths, mathematically validating that bypassing the primary central bottleneck provides relief to almost half of the transitional road network.
*  Demand Increase (Red): 10,436 edges (28.23% of the network) experienced an influx of 2,754,345 demand units. The proportion of these edges remains remarkably stable across scales (32.31% micro vs. 28.23% macro), proving that diverted feeder flows consistently merge onto the same critical access streets.
*  Unchanged (Blue): 8,076 edges (21.84% of the network) remained structurally unaffected.  
