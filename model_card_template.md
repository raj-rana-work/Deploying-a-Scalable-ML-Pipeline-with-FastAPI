# Model Card
For additional information see the Model Card paper: https://arxiv.org/pdf/1810.03993.pdf

## Model Details
This model is a RandomForestClassifier built to predict whether an individual's annual income is above or below $50K.
The model uses the preprocessing functions provided in the MLOps starter kit, including one-hot encoding for categorical features and label binarization for the target variable.
The trained model and encoders are stored in the model/ directory.

## Intended Use
This model is intended for educational use as part of the Udacity Machine Learning DevOps program.
It demonstrates how to build a reproducible ML pipeline, train a model, evaluate performance, and serve predictions through an API.

## Training Data
The model was trained using the U.S. Census Income dataset.
The data includes demographic and work-related attributes such as:

-workclass

-education

-marital status

-occupation

-race

-sex

-native country

-hours per week

-capital gain/loss

The dataset was split into:

-80% training

-20% testing

Categorical features were one-hot encoded, and the salary label was binarized (<=50K or >50K).

## Evaluation Data
The evaluation data comes from the 20% test split.
This data was processed with the same encoder and label binarizer fitted on the training data.
Slice-based evaluation was also performed for every unique value in each categorical feature, and results were written to slice_output.txt.

## Metrics
The primary evaluation metrics are:

Precision: 0.7419
Recall: 0.6384
F1 Score: 0.6863

These metrics reflect how well the model identifies individuals earning over $50K.
Slice-based metrics show how the model performs for specific groups, such as by workclass, education, race, and sex.
These results help identify potential differences in performance across demographics.

## Ethical Considerations
The dataset contains sensitive demographic attributes.
Models trained on this data may reflect biases present in the original census records.
Using this model in real-world decision-making could reinforce inequities related to race, gender, and socioeconomic status.

## Caveats and Recommendations
-The dataset is from 1994 and may not represent current populations.

-No fairness or bias mitigation techniques were applied.

-Random forests offer little interpretability.

-Additional work such as hyperparameter tuning, calibration, and fairness evaluation could improve overall performance.

-If deployed, the model should be monitored for drift and regularly retrained with updated data.