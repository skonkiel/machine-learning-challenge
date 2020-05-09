# machine-learning-challenge
This project explores different machine learning models to determine which may be best to identify exoplanets from NASA data.

This repository contains four Jupyter notebooks—one per model—and copy of the source data in CSV format. If you'd like to experiment with these notebooks, simply `git clone` or download this repo to a computer that has `pandas`, `scikit-learn`, and `Jupyter` installed.

## Selecting the models
Two types of models were chosen, based on their ability to assist in feature selection or accurately classify values given a training set.

* Feature selection: [`Decision Tree Classifier`](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html#sklearn.tree.DecisionTreeClassifier) and [`Random Forest Classifier`](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
* Classification: [`SVC`](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html#sklearn.svm.SVC) (a type of [Support Vector Machine](https://scikit-learn.org/stable/modules/svm.html) and [`K Nearest Neighbor`](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#sklearn.neighbors.KNeighborsClassifier)

## Preparing the models
1. Determined feature importances by running `Decision Tree` and `Random Forest` models. The features that showed the most promise were: `'koi_fpflag_co', 'koi_fpflag_nt', 'koi_fpflag_ss', 'koi_model_snr', 'koi_prad', 'koi_prad_err2', 'koi_duration_err2'`.
2. Used the features to train the `K Nearest Neighbors` and `SVC` models.
3. Used `GridSearchCV` to hypertune the models and boost performance.
4. Tested the models (adding and removing features, running model with and without GridSearchCV) to confirm that feature selection was appropriate.


## How the models performed

### SVC 
Model accuracy began at ~`0.60`. Using only important features identified by the Random Forest model, it improved to `0.857`. This was achieved using a train-test split of 80-20 and the default SVC kernel (`rbf`). Using `linear` and `poly` kernel settings were resource and time intensive.

SVC appears to be the better choice for potential planet classification, having especially high precision for identifying false positives.

### K Nearest Neighbors
Achieved model accuracy of `0.866` with `k=17`.

Even with GridSearchCV tuning and supposedly high scores, the model did not actually classify planets (as determined by a manual review of the classifications).


## Future work
* Test other models
* Visualize results of all models


## Data source
* [Exoplanet Data Source](https://www.kaggle.com/nasa/kepler-exoplanet-search-results)