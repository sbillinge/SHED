---
title: 'SHED: Streaming Heterogenous Event Data Tracking with Provenance'
tags:
  - Python
  - provenance
  - streaming data
  - pipelines
authors:
  - name: Christopher J. "CJ" Wright
    orcid: 0000-0003-2522-7028
    affiliation: 1
  - name: Songsheng Tao
    orcid: 0000-0002-7565-3503
    affiliation: 1
  - name: Simon J. L. Billinge^[Corresponding author]
    orcid: 0000-0002-9734-4998
    affiliation: "1, 2"
affiliations:
 - name: Department of Applied Physics and Applied Mathematics, 
                  Columbia University, New York, NY 10027
   index: 1
 - name: Brookhaven National Laboratory, Upton, NY 11973
   index: 2
date: 27 October 2020
bibliography: paper.bib

---
# Summary

The SHED package provides a python based software framework for 
real time analysis of streaming data with provenance.  It is highly
flexible, allowing analysis pipelines to be built for any variety of
experimental data that is arriving in a time series.  It allows straightfoward
serialization of the pipeline, and the analysis results, for storage in databases
with provenance information that allows analyses later to be pulled from the databases,
adapted if desired, and rerun.

# Statement of Need

The accelerating rate of data coming from modern scientific experiments
enable completely new classes of experiments to be carried out such as
*in situ* and *operando* measurements of time-dependent phenomena.
Many current and planned world class experimental facilities such as
x-ray synchrotron sources produce mountains of data.
Real-time processing of these large volumes of data can be made possible by streaming
data processing, where the data is processed and reduced as it is being collected.
While many streaming data processing systems exist [@silva:2007][@davison:2014] few handle
the heterogeneity which is prevelent in many experimental environments.  For
example, x-ray synchrotrons support thousands of users per year doing a wide
array of bespoke experiments and measurements.
Additionally, few streaming systems track the provenenace of the processed
data, creating reproducibility and discoverability concerns.

``SHED`` is a Python package for handling heterogeneous streaming data and
the tracking of the provenance of the produced results.
The ``SHED`` API translates data coming from a streaming experiment
into python objects
which are passed into data processing pipelines written using the ``streamz``
library.  It expects data in the form of the Bluesky Event Model schema,
which is a flexible open-source document model suitable for scientific
time-series experiments.  The Bluesky event model is 
used by nearly all of the beamlines at the National Synchrotron Light Source-II 
(NSLS-II) as well as at other facilities.  
``SHED`` also provides translation from the python objects flowing through
a ``streamz`` pipeline back into the Event Model enabling the use of data visualization
and storage tools written for the Event Model.
In addition to the translation features SHED passively tracks the provenance
of produced data, capturing the data processing pipeline, data unique IDs,
and the order of data insertion into the pipeline.
The pipeline is caputred in a way which is both human and machine readable
enabling searching and comparison of analyzed data sets.
An extendable system also captures information about the software environment
in which the pipeline ran, including the conda environment, allowing in principle
data analysis campaigns to be serialized into a database then later rerun 
recovered and rerun or adapted and then rerun and restored.

``SHED`` is designed to provide a bridge between the data collected from 
high throughput experiments if they are, or can be put, into event model form
(such as data from NSLS-II experiments),
and the NSLS-II's data visualization and storage tools.
This system has been used to write x-ray scattering data processing 
pipelines currently used in production at the NSLS-II XPD and PDF beamlines
(28-ID-2 and 28-ID-1, respectively).


# Citations

Citations to entries in paper.bib should be in
[rMarkdown](http://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html)
format.

For a quick reference, the following citation commands can be used:
- `@author:2001`  ->  "Author et al. (2001)"
- `[@author:2001]` -> "(Author et al., 2001)"
- `[@author1:2001; @author2:2001]` -> "(Author1 et al., 2001; Author2 et al., 2002)"

# Figures

Figures can be included like this: ![Example figure.](figure.png)

# Acknowledgements

This work was supported as part of GENESIS: A Next Generation Synthesis Center, 
an Energy Frontier Research Center funded by the U.S. Department of Energy, 
Office of Science, Basic Energy Sciences under Award Number DE-SC0019212

# References
