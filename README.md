# Graph-Linguistic Fusion: Using Language Models for Wikidata Vandalism Detection

<img align="right" src="data/imgs/system_scketch_new.png" alt="drawing" style="width:300px;"/>

This repository includes resources to reproduce training and evaluation procedure for the paper
**Graph-Linguistic Fusion: Using Language Models for Wikidata Vandalism Detection** (accepted to ACL'25 Industry track) from data collection to model training and evaluation. 

- The full paper already available: TBD
- The model inference logic is to be implemented in 
[![Knowledge Integrity repo](https://img.shields.io/badge/GitLab-repo-orange)](https://gitlab.wikimedia.org/repos/research/knowledge_integrity)
- Prepared dataset and artifacts: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15492678.svg)](https://doi.org/10.5281/zenodo.15492678)

## Experiments reproducing:

#### 1. Data collection:
`notebooks/01_data_collection.ipynb` includes the data collection process. We use Wikimedia Data Lake to collect the data. In particular we collect revisions metadata, content changes, English labels and ORES scores for comparison.

#### 2. MLM tuning and feature extraction:
`notebooks/02_text_model_training.ipynb` includes the MLM tuning process. We use the [Hugging Face Transformers](https://huggingface.co/docs/transformers/index) library to train the model. GPU is needed for training. We used AMD Radeon Pro WX 9100 16GB GPU. The notebook includes data loading, data splitting logic, along with content processing (extracting content changes, mapping Wikidata IDs to English labels, etc.). In the end the finetuned model is used to calculate the scores for revisions not included in the training set.

#### 3. Final classifier training:
`notebooks/03_classifier_model_training.ipynb` includes the final classifier training process. We use the [CatBoost](https://catboost.ai/en/docs/concepts/python-reference_catboost) library to train the model. The notebook includes data loading, data splitting logic, along with content processing. We train three configurations: only metadata, only text features and both metadata and text features. The final model is saved in the `models` folder.

#### 4. System Validation:
`notebooks/04_validation.ipynb` includes the system validation process. It includes all the metrics and plots presented in the paper. 


## Citation: 
**Graph-Linguistic Fusion: Using Language Models for Wikidata Vandalism Detection**
```
TBD
```