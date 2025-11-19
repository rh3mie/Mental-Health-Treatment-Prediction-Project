# Mental Health Risk in Tech: Predictive Modeling and Fairness Analysis
By Rheymar Devera, Animesh Bose & Abeezar Babuji

University of Maryland, INST452

## Project Overview
This project analyzes mental-health risk factors in the tech industry using survey data from [Open Sourcing Mental Health [OSMH](https://osmhhelp.org/research.html). Here, we build machine-learning models to predict whether an individual is likely to seek mental-health treatment, to explore predictive performance, fairness across age groups, and bias mitigation techniques. This allows workplaces to understand mental-health risks and how different workplace factors affect well-being, adjusting policies for better awareness and accessibility to treatment.

## Tools and Libraries Required
- ```R```, ```tidyverse```, ```dplyr```, ```ggplot2```: Cleaning and visualizing data
- ```caret```: For training and creating ML models for prediction
- ```corrplot```: For understanding relationships between variables
- ```pROC```: To analyze and compare ROC curves, and calculate AUC or other statistical tests.
- ```fairmodels```/ ```DALEX```: Libraries for conducting fairness evaluations across models

## Key Variables
- ```Age```: Respondent's age
- ```Gender```: Self-identified gender
- ```Country```: Respondent's resident country
- ```State```: state of respondent's residency
- ```self_employed```: Whether the respondent's self-employed
- ```remote_work```: Whether the respondent works remotely
- ```tech_company```: Whether the respondent works at a tech company
- ```treatment```: Whether the respondent has sought mental-health treatment
- ```work_interfere```: How often mental-health issues interfere with work
- ```benefits```: Whether the employer provides mental-health benefits
- ```care_options```: Awareness of mental-health care options available
- ```wellness_program```: Availability of workplace wellness programs
- ```seek_help```: Whether employees are encouraged to seek help
- ```anonymity```: Whether anonymity is protected when seeking treatment
- ```leave```: How easy it is to take medical leave for mental-health reasons
- ```mental_health_consequence```: Expected consequences of disclosing mental-health issues
- ```phys_health_consequence```: Expected consequences of disclosing physical-health issues
- ```coworkers```: Comfort discussing mental-health issues with coworkers
- ```supervisor```: Comfort discussing mental-health issues with supervisors
- ```mental_health_interview```: Willingness to discuss mental health during hiring interviews
- ```phys_health_interview```: Willingness to discuss physical health during interviews
- ```mental_vs_physical```: Whether mental health is treated the same as physical health
- ```obs_consequence```: Whether respondent has observed others being penalized for mental-health disclosure
- ```comments```: Any extra input from the respondent about the survey

## Project Workflow

### 1. Data Cleaning and Preprocessing
- Removed irrelevant fields (```timestamp```, ```state```, ```comments```)
- Filtered valid age range (18-100) since there were negative and high outlier values
- Standardized and recoded gender categories
- Cleaned missing data in ```work_interfere``` and ```self_employed```
- Factored categorical features for model use

### 2. Exploratory Data Exploration
Created visualizations to understand relationships between work conditions and mental-health treatment. 
- Stacked bar plot to show how many people reported work interference and what proportion actually sought treatment
- Stacked bar chart comparing remote work and the proportion who received treatment
- Box plot comparing the spread of age and who said yes or no to receiving treatment
These plots reveal how workplace environment and age influence help-seeking behavior.

### 3. ML Models
Trained three supervised classification models using caret with 5-fold cross-validation. Tuned and evaluated using ROC, sensitivity, and specificity.
- Decision Tree
- Support Vector Machine (SVM)
- K-nearest Neighbors (KNN)

Cross-validation and test-set performance metrics used (results visualized using bar charts for comparison):
- AUC
- Accuracy
- Sensitivity
- Specificity

### 4. Fairness and Bias Analysis
Used ```fairmodels``` and ```DALEX``` to evaluate whether models showed bias on ```AgeGroup```. This check tested:
- Predictive Equity
- Statistical Parity Ratio
- False Positive/ False Negative Rate differences
Bias mitigation was performed on the KNN model in hopes of reducing disparity between age groups. This was implemented by putting different prediction cutoffs for the younger group at 0.4 and the older group at 0.5. This improved fairness metrics without damaging overall accuracy.

## Key Takeaways
- Several workplace variables strongly correlate with treatment-seeking
- The Decision Tree model generally performed better than the SVM and KNN models
- Bias mitigation through threshold adjustments is effective
- Mental health in tech is influenced by both personal and workplace factors, with them all affecting outcomes in some way

Overall, machine learning models can help identify mental-health risk patterns among tech workers (and people in general), allowing companies to learn from them and implement policies for better care and intervention. It is also important to ensure fairness across groups for ethical and effective real-world use.
