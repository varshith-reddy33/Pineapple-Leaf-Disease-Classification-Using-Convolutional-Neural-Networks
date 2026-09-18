# Pineapple Leaf Disease Classification Using CNN

A deep learning project for classifying pineapple leaf images into four classes using a Convolutional Neural Network (CNN).

## Project Overview

Pineapple plants can be affected by diseases such as Fusarium Rot, Leaf Blight and Mealy Bug Wilt. This project investigates whether a CNN can classify pineapple leaf images into different health conditions based on visual patterns.

The project was developed as part of the **M507 Methods of Prediction** module.

## Problem

The objective is to classify pineapple leaf images into four classes:

* Fusarium Rot
* Healthy
* Leaf Blight
* Mealy Bug Wilt

The project uses image preprocessing and a CNN-based classification approach.

## Dataset

The project uses the **Pineapple Leaf Disease Dataset**, containing field-acquired pineapple leaf images.

Dataset characteristics:

* 4,476 images
* 200 unique specimens
* 4 classes
* 50 specimens per class
* Average of approximately 22 images per specimen
* Images collected in Vazhakulam, Kerala, India
* Images captured using multiple camera devices

### Dataset source

Raj, S., Prakash, N. and Malik, N. (2026).
*Pineapple Leaf Disease Dataset: Field-Acquired Images for Deep Learning-Based Plant Health Assessment*. Zenodo.

Dataset: https://zenodo.org/records/21893516

The dataset is **not included in this repository** because of its size.

## Data Splitting

Multiple images were collected from the same physical specimen. Therefore, the dataset was split at the **specimen level** rather than randomly splitting individual images.

For each class:

* 20 specimens → Training
* 5 specimens → Validation
* 5 specimens → Test

The final image distribution was:

| Split      | Images |
| ---------- | -----: |
| Training   |  1,796 |
| Validation |    434 |
| Test       |    441 |

No specimen overlap was found between the three splits.

## Data Preprocessing

The images were:

1. Loaded from the dataset
2. Converted to RGB
3. Resized to 128 × 128 pixels
4. Normalised to a range of 0–1
5. Converted into numerical class labels

## Model

A simple Convolutional Neural Network was developed using TensorFlow/Keras.

The architecture contains:

* Convolutional layers
* Max pooling layers
* Flatten layer
* Dense layer
* Dropout layer
* Four-class softmax output layer

The model was intentionally kept relatively simple so that the individual components and experiments could be clearly understood.

## Experiments

Ten CNN configurations were compared by changing parameters such as:

* Dropout rate
* Dense-layer size
* Convolutional filter size
* Learning rate
* Batch size

Validation accuracy was used for model selection, while the test set was kept unseen during the experiment comparison.

The best-performing configuration was:

**Batch Size 64**

Best validation accuracy:

**59.45%**

## Final Results

The selected CNN was evaluated on the unseen test set.

| Metric                | Result |
| --------------------- | -----: |
| Test Accuracy         | 68.48% |
| Test Loss             | 1.1091 |
| Test Images           |    441 |
| Incorrect Predictions |    139 |

### Classification Performance

| Class          | Precision | Recall | F1-score |
| -------------- | --------: | -----: | -------: |
| Fusarium Rot   |      0.76 |   0.34 |     0.47 |
| Healthy        |      0.74 |   0.93 |     0.83 |
| Leaf Blight    |      0.54 |   0.48 |     0.51 |
| Mealy Bug Wilt |      0.69 |   0.95 |     0.80 |

The model identified Healthy and Mealy Bug Wilt images more consistently, while Fusarium Rot and Leaf Blight were more difficult to distinguish.

## Error Analysis

A confusion matrix and incorrectly classified test images were examined to understand the model's errors.

The results show that some disease classes have visually similar characteristics, leading to confusion between disease categories.

The field-acquired nature of the dataset also introduces variations in lighting, background and camera equipment.

## Limitations

The model has several limitations:

* The dataset contains images from a specific collection location.
* The number of specimens is relatively limited.
* Disease classes can have visually similar characteristics.
* Field conditions introduce variation in lighting, background and camera equipment.
* The model should be considered a screening approach rather than a replacement for professional agricultural diagnosis.

## Future Improvements

Possible improvements include:

* Increasing the number of specimens and field images
* Collecting images from additional locations
* Using images from a wider range of environmental conditions
* Improving classification of Fusarium Rot and Leaf Blight
* Investigating data augmentation
* Comparing the CNN with transfer-learning approaches
* Exploring explainability techniques such as Grad-CAM

## Technologies

* Python
* TensorFlow
* Keras
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* Pillow
* Jupyter Notebook

## Repository Structure

```text
pineapple-leaf-disease-classification/
│
├── README.md
├── Methods_of_Prediction.ipynb
├── requirements.txt
├── .gitignore
│
├── data/
│   └── README.md
│
└── images/
    ├── sample_classes.png
    ├── class_distribution.png
    ├── training_validation_accuracy.png
    ├── confusion_matrix.png
    └── error_analysis.png
```

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/pineapple-leaf-disease-classification.git
cd pineapple-leaf-disease-classification
```

### 2. Install the dependencies

```bash
pip install -r requirements.txt
```

### 3. Download the dataset

Download the Pineapple Leaf Disease Dataset from Zenodo.

The dataset should be extracted locally.

### 4. Update the dataset path

Open `Methods_of_Prediction.ipynb` and update the dataset path in the configuration cell.

```python
downloads_path = "YOUR_DATASET_PATH"
```

### 5. Run the notebook

Open the notebook using Jupyter:

```bash
jupyter notebook
```

Then run the notebook cells from beginning to end.

## References

Raj, S., Prakash, N. and Malik, N. (2026). *Pineapple Leaf Disease Dataset: Field-Acquired Images for Deep Learning-Based Plant Health Assessment*. Zenodo.

Abadi, M. et al. (2016). 'TensorFlow: A system for large-scale machine learning'. *Proceedings of the 12th USENIX Symposium on Operating Systems Design and Implementation*.

Chollet, F. (2015). *Keras*.

Pedregosa, F. et al. (2011). 'Scikit-learn: Machine Learning in Python'. *Journal of Machine Learning Research*, 12, pp. 2825–2830.
