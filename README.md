# Predicting Neurofeedback-Associated Brain Network Reorganization from Resting-State Functional Connectivity in Major Depressive Disorder

This repository contains the computational analysis pipeline accompanying a study of individual brain-network reorganization following real-time fMRI neurofeedback in major depressive disorder (MDD).

The analysis models intervention-associated changes in resting-state functional connectivity as individual brain-network state transitions and evaluates whether the dominant pattern of subsequent network reorganization can be predicted from baseline functional connectivity.

The workflow includes resting-state fMRI data auditing and quality control, 216-region cortical and subcortical parcellation, functional-connectivity estimation, network-level transition modeling, principal component analysis, leakage-free nested cross-validated Ridge regression, permutation testing, and exploratory neurobehavioral analysis using depressive symptom change.
## Analysis Workflow

```text
Preprocessed resting-state fMRI
        ↓
Dataset audit and quality control
        ↓
216-ROI parcellation
(Schaefer-200 + Tian-16)
        ↓
ROI-to-ROI functional connectivity
        ↓
8 functional systems
        ↓
36 within- and between-system connectivity features
        ↓
Rest2 − Rest1 brain-network transition
        ↓
Principal component analysis
        ↓
Dominant transition pattern (PC1)
        ↓
Nested LOOCV Ridge prediction
        ↓
Permutation testing
        ↓
Exploratory association with MADRS symptom change

```

## Repository Structure 

| Notebook | Purpose |
|---|---|
| `01_dataset_audit.ipynb` | Audits participant availability, paired Rest1/Rest2 imaging, metadata, and imaging quality control. |
| `02_parcellation_216roi.ipynb` | Extracts resting-state time series using the Schaefer-200 cortical and Tian-16 subcortical parcellations. |
| `03_functional_connectivity.ipynb` | Constructs ROI-level functional-connectivity matrices and 36 network-level connectivity features. |
| `04_prediction.ipynb` | Models the dominant brain-network transition using PCA, nested LOOCV Ridge regression, and permutation testing. |
| `05_neurobehavioral_outcomes.ipynb` | Examines the exploratory association between the dominant neural transition and MADRS symptom change. |
| `06_neurofeedback_run_audit.ipynb` | Audits the availability of intermediate neurofeedback training-run imaging data. |

## Data and Privacy

The neuroimaging and clinical data used in this study are not included in this repository. The data originate from an existing human-subject neurofeedback dataset and are not publicly redistributed here because of participant privacy and data-use considerations.

This repository contains analysis code only. Participant-level neuroimaging data, clinical measurements, derived participant-level outputs, and other potentially identifying research data should not be committed to this repository.

## Software Requirements

The analysis was implemented in Python using Jupyter notebooks.

Major Python packages used in the workflow include:

- `numpy`
- `pandas`
- `scipy`
- `nibabel`
- `nilearn`
- `scikit-learn`
- `statsmodels`
- `matplotlib`

The neuroimaging inputs used by the analysis were preprocessed AFNI residual functional datasets in HEAD/BRIK format.

Exact package versions and a reproducible environment specification will be added prior to the final code release.

## Usage

The notebooks are organized according to the analysis workflow and are intended to be followed in numerical order:

1. `01_dataset_audit.ipynb` — identify paired imaging sessions and apply dataset quality-control criteria.
2. `02_parcellation_216roi.ipynb` — extract 216-region resting-state time series.
3. `03_functional_connectivity.ipynb` — construct ROI-level and network-level functional-connectivity representations.
4. `04_prediction.ipynb` — characterize the dominant network transition and perform leakage-free predictive modeling.
5. `05_neurobehavioral_outcomes.ipynb` — evaluate the exploratory relationship between network transition and depressive symptom change.
6. `06_neurofeedback_run_audit.ipynb` — audit availability of intermediate neurofeedback-run data.

The notebooks currently reference local dataset locations and therefore are not expected to run without access to the corresponding source data and appropriate path configuration.

## Project Status

This repository accompanies an ongoing research manuscript on computational modeling of neurofeedback-associated brain-network transitions in major depressive disorder.

The analysis workflow is complete, while the manuscript and code documentation remain under review. Repository contents may therefore be updated prior to the final archived release.

## Citation

A formal citation will be added following manuscript publication or public preprint release.

If you use or build upon this code before a formal citation is available, please reference this repository and contact the author for the appropriate citation information.

## Author

Saima Ahmed Rahin  
Tandy School of Computer Science  
The University of Tulsa 
