\# Retina Severity Classification



A deep learning project for five-class retinal disease severity classification using fundus images from the APTOS and EyePACS datasets.



The project uses a pretrained EfficientNet-B0 model with transfer learning and class-weighted cross-entropy loss to address the substantial class imbalance present in the dataset.



> \*\*Note:\*\* This is a research/portfolio machine-learning project and is not a clinically validated diagnostic system.



\---



\## Project Overview



Retinal disease severity classification is a challenging image classification problem because the dataset contains a strong imbalance between severity classes.



This project explores an end-to-end deep learning pipeline covering:



\- Dataset integration and preparation

\- Image path validation

\- Stratified train/validation splitting

\- Image preprocessing and augmentation

\- Class imbalance handling

\- Transfer learning with EfficientNet-B0

\- Mixed-precision GPU training

\- Validation using accuracy and macro-F1

\- Per-class evaluation

\- Confusion matrix analysis



The final experiment combines images from the APTOS and EyePACS datasets into a five-class classification problem.



\---



\## Severity Classes



The model predicts five severity classes:



| Class | Description |

|---|---|

| 0 | Severity 0 |

| 1 | Severity 1 |

| 2 | Severity 2 |

| 3 | Severity 3 |

| 4 | Severity 4 |



The project treats the task as a five-class image classification problem.



\---



\## Dataset



The combined dataset contains \*\*38,770 retinal images\*\*:



| Source | Images |

|---|---:|

| APTOS | 3,662 |

| EyePACS | 35,108 |

| \*\*Total\*\* | \*\*38,770\*\* |



The class distribution is highly imbalanced, with Severity 0 representing the majority of the images.



The dataset is \*\*not included in this repository\*\*. Users should obtain the datasets from their respective official sources and place the images in the expected local directory structure.



\---



\## Data Split



A stratified train/validation split was used:



| Split | Images |

|---|---:|

| Training | 32,954 |

| Validation | 5,816 |



The split preserves the relative class distribution across the two subsets.



> The current experiment uses an image-level split. Patient-level independence could not be verified because patient identifiers were not available in the combined data used for this project.



\---



\## Model



The final model is based on:



\*\*EfficientNet-B0 with ImageNet pretrained weights\*\*



The original classification head was replaced with a five-class output layer.



```text

EfficientNet-B0

&#x20;     ↓

Feature extraction

&#x20;     ↓

Dropout (0.2)

&#x20;     ↓

Linear layer

&#x20;     ↓

5 severity classes





