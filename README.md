
# Welcome to Titanic Analysis repository 🌊🛳️

## About 📝

This is a Mini-Project for NTU SC1015 (Introduction to Data Science and Artificial Intelligence) which explores a dataset on the passengers of the Titanic from [Kaggle](https://www.kaggle.com/datasets/yasserh/titanic-dataset), proudly presented by **A139 Team 1**.

The [datasets](https://github.com/Mystic1611/SC1015-Titanic-Analysis/tree/master/datasets) folder contains the datasets in CSV format used by the notebooks at different junctures of the walkthrough. For the description of the variables in the datasets, kindly refer to the [variable description file](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/variables%20description.md).

The Mini-Project has been broken down into 9 different portions which should be viewed in the following order:

 1. [**Data Extraction & Cleaning**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/1.%20data-extraction-and-cleaning.ipynb) 🧹
 2. [**Exploratory Data Analysis on Categorical Variables**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/2.%20data-eda-categorical.ipynb) 🔍
 3. [**Exploratory Data Analysis on Numerical Variables**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/3.%20data-eda-numerical.ipynb) 🔎
 4. [**Decision Tree**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/4.%20machine-learning-decision-tree.ipynb) 🌲
 5. [**Data Upsampling**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/5.%20machine-learning-upsampling.ipynb) ⬆️
 6. [**Random Forest**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/6.%20machine-learning-random-forest.ipynb) 🎲🌲
 7. [**Support Vector Machine**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/7.%20machine-learning-svm.ipynb) 📈
 8. [**Attempt at Removing Outliers to Improve Models**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/8.%20machine-learning-removing-outliers.ipynb)  🗑️ 
 9. [**Conclusion**](https://github.com/Mystic1611/SC1015-Titanic-Analysis/blob/master/9.%20conclusion.ipynb) 🏁

 ## Contributors 👪
 - Lim Haozheng [@aaron-limm](https://github.com/aaron-limm)
 > **Contributions**: Data extraction, Exploratory Data Analysis, Decision Tree, Data Upsampling
 - Leong Wei Hong [@weihonglwh](https://github.com/weihonglwh)
 > **Contributions**: Data Cleaning, Exploratory Data Analysis, Support Vector Machine
 - Lee Kian Han, Nicholas [@n-nicholas-s](https://github.com/n-nicholas-s) 
 > **Contributions**: Exploratory Data Analysis, Random Forest, Removal of Outliers

## Problem Statement ❓

- Are we able to predict one's survivability on the Titanic based on its attributes so that it can be used for future maritime disaster rescue aids to improve survivability?
- Would Decision Tree, Random Forest or Support Vector Machine yield a better model?

## Machine Learning Algorithms Used 🧠

- Decision Tree 🌲
- Random Forest 🎲🌲
- Support Vector Machine 📈

## Data Extraction and Cleaning 🧹

### Procedures 📜
- Extracted raw dataset from [`OG-Titanic-Dataset.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/OG-Titanic-Dataset.csv)
- Filling null values using median for numerical data and mode for categorical data
- Removed variable(s) with majority null values
- Performed feature engineering and created 3 new variables as follows:

| Variable     | Description | 
| ----------- | --------------------------- |
| Family_Size | Family Size of the passenger|
| Alone   | Identifies if the passenger is travelling alone|
| Initial | Initial/Title of the passenger (Mr, Mrs, etc.)

- Export modified dataset to [`cleaned-data.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/cleaned-data.csv)

## Exploratory Data Analysis on Categorical Variables 🔍

### Procedures 📜
- Identify percentage and ratio of each categorical variable
- Explore each categorical variable against `Survived`
- Determine categorical predictors for machine learning as follows:
1. `Sex`
2. `Pclass`
3. `Embarked`
4. `Alone`
- Export dataset with categorical predictors to [`categorical-predictors.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/categorical-predictors.csv)

## Exploratory Data Analysis on Numerical Variables 🔎

### Procedures 📜
- Visualise numerical data with boxplots and histograms
- Explore each numerical variable against `Survived`
- Determine numerical predictors for machine learning as follows:
1. `Fare`
2. `Parch`
3. `Family_Size`
- Export dataset with categorical predictors to [`numeric-predictors.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/numeric-predictors.csv)

## Decision Tree 🌲

### Procedures 📜
- Combine [`categorical-predictors.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/categorical-predictors.csv) and [`numeric-predictors.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/numeric-predictors.csv) to get the dataset required for machine learning
- Using `OneHotEncoder` from `sklearn` module to convert categorical variables to numeric value for Decision Tree
- Plot results (accuracy, TPR, TNR, FPR, FNR) on confusion matrix for both train and test
- Export OneHotEncoded machine learning data to [`machine-learning-data-ohe.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/machine-learning-data-ohe.csv)

## Data Upsampling ⬆️

### Procedures 📜
- Upsample the amount of data entries to balance the number of entries with survivors and casualties.
> **Reason**: To reduce FNR since most entries are casualties.
- Re-create decision tree model with upsampled data
- Plot results (accuracy, TPR, TNR, FPR, FNR) on confusion matrix for both train and test
- Export OneHotEncoded and upsampled machine learning data to [`machine-learning-data-ohe-upsampled.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/machine-learning-data-ohe-upsampled.csv)
> **Findings**: Upsampling the data indeed reduced the high FNR previously.

## Random Forest 🎲🌲

### Procedures 📜
- Create model from OneHotEncoded and upsampled machine learning data using default settings of Random Forest
- Use `GridSearchCV` from `sklearn` module to perform hyperparameter tuning and find best setting for Random Forest
- Plot results (accuracy, TPR, TNR, FPR, FNR) on confusion matrix for both train and test
- Compare Random Forest model against Decision Tree model
> **Findings**: Random Forest yields a better model than Decision Tree.

## Support Vector Machine (SVM) 📈

### Procedures 📜
- Create model from OneHotEncoded and upssampled machine learning data using default settings of SVM
- Use `GridSearchCV` from `sklearn` module to perform hyperparameter tuning and find best setting for SVM
- Plot results (accuracy, TPR, TNR, FPR, FNR) on confusion matrix for both train and test
- Compare SVM model against Random Forest model
> **Findings**: SVM yields a better model than Random Forest and is the best among the 3 models used in this case.

## Attempt at Removing Outliers to Improve Models 🗑️

### Procedures 📜
- Identify and remove outliers from OneHotEncoded and upsampled machine learning data
- Export dataset without outliers to [`machine-learning-data-ohe-upsampled-no-outliers.csv`](https://github.com/weihonglwh/SC1015-Titanic-Analysis/blob/master/datasets/machine-learning-data-ohe-upsampled-no-outliers.csv)
- Create models on all 3 machine learning algorithms using the new dataset
- Compare difference before and removing outliers
> **Findings**: Removing outliers degraded the quality of all 3 models, which could possibly be because around 20% of the dataset was removed, resulting in a lack of data to build an accurate model.

## Conclusion 🏁

- The SVM model is the best model of the 3 we created
- We are 84.8% confident that survivability can be predicted with the predictors we chose earlier using SVM, therefore it is possible to predict one's survivability using those predictors
- `Fare` and `Sex` are highly correlated with `Survived`
> Females 👩 tend to have a much more likely chance of survival and those that pay a higher fare 💵 also has higher chance of survival.
- Found limitations of models and ways to improve are as follows:

| Limitation  | Improvement | 
| ----------- | --------------------------- |
| Only 1 model per algorithm might not be the best model | Usage of ensemble methods by combining several base models to produce one optimal model |
| Not all machine learning algorithms explored   | Explore all machine learning algorithms like neural network as they might produce a better model |
| Relatively smaller dataset | Use a larger dataset |

## Takeaways from Project🛍️

- Usage of upsampling to reduce bias in decision
- Random Forest and SVM
- Hyperparameter Tuning
- Usage of GitHub
- Importance of documentation of changes

## References

https://www.kaggle.com/datasets/yasserh/titanic-dataset
https://scikit-learn.org/stable/modules/svm.html
https://scikit-learn.org/stable/modules/generated/sklearn.utils.resample.html
https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html
https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html
