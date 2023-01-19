# Cardiovascular_classification

# Problem Statement : 

The dataset is from an ongoing cardiovascular study on residents of the town of Framingham, Massachusetts. The classification goal is to predict whether the patient has a 10-year risk of future coronary heart disease (CHD). The dataset provides the patients’ information. It includes over 4,000 records and 17 attributes. Each attribute is a potential risk factor. There are both demographic, behavioral, and medical risk factors.


# Data Description : 

**Demographic**
• Sex: male or female("M" or "F")
• Age: Age of the patient;(Continuous - Although the recorded ages have been truncated to whole numbers, the concept of age is continuous)

**Behavioral**
• is_smoking: whether or not the patient is a current smoker ("YES" or "NO")
• Cigs Per Day: the number of cigarettes that the person smoked on average in one day.(can be considered continuous as one can have any number of cigarettes, even half a cigarette.)

**Medical( history)**
• BP Meds: whether or not the patient was on blood pressure medication (Nominal)
• Prevalent Stroke: whether or not the patient had previously had a stroke (Nominal)
• Prevalent Hyp: whether or not the patient was hypertensive (Nominal)
• Diabetes: whether or not the patient had diabetes (Nominal)

**Medical(current)**
• Tot Chol: total cholesterol level (Continuous)
• Sys BP: systolic blood pressure (Continuous)
• Dia BP: diastolic blood pressure (Continuous)
• BMI: Body Mass Index (Continuous)
• Heart Rate: heart rate (Continuous - In medical research, variables such as heart rate though in fact discrete, yet are considered continuous because of large number of possible values.)
• Glucose: glucose level (Continuous)

**Predict variable (desired target)**
• 10-year risk of coronary heart disease CHD(binary: “1”, means “Yes”, “0” means “No”) - DV(Dependent VAriable).

Checking first 5 and last 5 rows

![Screenshot (73)](https://user-images.githubusercontent.com/67784512/211741807-3d94daf3-9aa5-431f-be16-de36b103d882.png)

Checking data info to check any null values found

![Screenshot (74)](https://user-images.githubusercontent.com/67784512/211742624-bcb6be9e-9132-439f-af73-24a4d3de4b3c.png)

**Missing value treatment**

we found that some columns contain null values. So we has to treating it with median or mean, for this problem we use median.

# EDA : Exploratory Data Analysis

Visualizing all numerical features using dist plot to check how data are distributed(like data points are positive skewed or negative skewed).

We also plot boxplot for numerical features to check any outliers are in our variables. And, we found except 'age' column, remaining all columns contains outliers.

we treating the outlier in numerical variables to median using Interquartile range method.

After treating the numerical features, we move to categorial features.

Check the value counts for independent categorical variables.

And we convert all categorical variables into 0 and 1 type, to easy our job.

After doing this all checking the Multicollinearity to check how data points are correlated each other.

Plot the heatmap using seaborn library and checking how much variables are correalted each other.


![Screenshot (75)](https://user-images.githubusercontent.com/67784512/211758913-7ea91963-14d4-4604-8f08-a1ac01b3fb55.png)


We found that some variabels are correlated, so we treat it using VIF(variance Inflation Factor).

# Model building part

Before moving to model building part we has to scale our dataset. Here, we use MinMaxScaler()

separting independent variables and dependent variable.

spliting our dataset into to train and test.

Checking our dependent variable value counts.

 And, we found that our dependent variable has class imbalanced. So we has to handle it before moving to model building part.
 
 Handling class imbalance by Oversampling followed by removing tomek link.
 
 Define a function to train the input model and print evalution matrix.
 
 Fitting multiple algorithms to test which model given better result and how they act.
 
 1. Logistic Regression
 2. Naive Bayes Classifier
 3. Support vector Classifier
 4. Random Forest Classifier
 5. XGBoost Classifier
 6. KNN Classifer
 
 
 # Conclusion :
 
 If we want to completely avoid any situations where the patient has heart disease, a high recall is desired. Whereas if we want to avoid treating a patient with no heart diseases a high precision is desired.
 
Assuming that in our case the patients who were incorrectly classified as suffering from heart disease are equally important since they could be indicative of some other alignment, so we want a balance between precision and recall and a high f1 score is desired.

Since we have added synthetic datapoints to handle the huge class imbalance in training set, the data distribution in train and test are different so the high performance of models in the train set is due to the train-test data distribution mismatch and not due to overfitting.

Best performance of Models on test data based on evaluation metrics for class 1: 
1. Recall - SVC
2. Precision - Naive Bayes Classifier
3. F1 Score - Logistic Regression, XGBoost
4. Accuracy - Naive Bayes Classifier
 
 **Support vector classifier gave the best Recall of 71%.**





















