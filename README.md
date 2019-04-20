# Logistic-regression-model-for-predicting-customer-churn
This project builds a logistic regression model to predict customer churn (i.e. whether a customer shifts to another network or not, called churn or no-churn respectively) for a telecommunications company.

# Data set
The data set consists of three separate .csv files. The file 'churn_data.csv' contains customer ID wise churn information.The file 'customer_data.csv' contains customer ID wise information about the customer, their billing preferrences, their address etc. The third file 'internet_data.csv' contains customer ID wise information on internet usage.

# Data preprocessing
Firstly, the three separate .csv files are loaded as Pandas DataFrames and subsequently merged on 'CustomerID' column to create a single master DataFrame. 
Subsequently, various string type categorical columns are mapped to numerical vaues and dummy variables are created for other categorical variables.
Then, a few repetitive columns are dropped and the DataFrame is checked for outliers and null values. No significant outliers are found and the rows with null values are dropped. This is followed by standardization of the data set to centre it at mean 0 and with a standard deviation of 1.

# Model building
A logistic regression model is built using the statsmodels.api library's Generalized Linear Model module with Binomial family.
A correlation matrix is then built and plotted to spot highly correlated variables. After dropping highly correlated features, Recursive Feature Elimination (RFE) is used to further narrow down the number of relevant features to 13. A final model is built after choosing a final set of features.

# Model evaluation
The overall accuracy of the model is found to be 80.33%. Further, an ROC curve was plotted and the Area Under Curve (AUC) was found to be 0.73.

# Optimal cutoff point
The final model evaluated although had a high accuracy but also a very high sensitivity and low specificity. Therefore, an optimal cutoff point was found for the logistic regression model by plotting the accuracy, sensitivity and specificity for various values of the cutoff parameter (C). The optimal C was found from the intersection point of accuracy, sensitivity and specificity plotted and was used to predict final outcomes with an overall accuracy of ~75%.
