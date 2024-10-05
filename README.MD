# Rusty Bargain Used Cars Analysis

# Table of Contents


- [Rusty Bargain Used Cars Analysis](#rusty-bargain-used-cars-analysis)
- [Table of Contents](#table-of-contents)
  - [Project Objective](#project-objective)
  - [Project Structure and Steps](#project-structure-and-steps)
  - [Tools and Techniques Utilized](#tools-and-techniques-utilized)
  - [Specific Results and Outcomes](#specific-results-and-outcomes)
    - [1. Data Exploration and Preprocessing](#1-data-exploration-and-preprocessing)
    - [2. Model Training and Evaluation](#2-model-training-and-evaluation)
    - [3. Model Speed and Performance Analysis](#3-model-speed-and-performance-analysis)
    - [4. Hyperparameter Tuning](#4-hyperparameter-tuning)
    - [5. Final Model Selection](#5-final-model-selection)
    - [Key Insights](#key-insights)
  - [What I Have Learned From This Project](#what-i-have-learned-from-this-project)
  - [How to use this repository](#how-to-use-this-repository)


## Project Objective 
Rusty Bargain is developing a mobile application to estimate the market value of used cars. The aim of this project is to build a machine learning model to accurately predict car prices based on historical data, technical specifications, and trim levels. The primary goals are to optimize the model for:
- Prediction quality
- Speed of prediction
- Time required for training

[back to top](#rusty-bargain-used-cars-analysis)

## Project Structure and Steps
1. **Data Loading and Exploration**
   - Load the dataset and perform an initial examination.
   - Understand the features, such as vehicle type, registration year, gearbox, power, model, mileage, registration month, fuel type, brand, and other relevant attributes.
   
2. **Data Preprocessing**
   - Handle any missing or incorrect values.
   - Perform feature engineering if necessary.
   - Prepare data for model training by encoding categorical variables and scaling the features.

3. **Model Training and Evaluation**
   - Train different models with various hyperparameters, including at least:
     - **Linear Regression**: Baseline for comparison.
     - **Decision Trees and Random Forests**: Explore tree-based models.
     - **Gradient Boosting Algorithms (LightGBM, CatBoost, XGBoost)**: Compare their performance and training times.
   - Evaluate models using RMSE (Root Mean Squared Error) as the metric.
   - Compare models based on accuracy, training time, and prediction speed.

4. **Analysis and Optimization**
   - Analyze model performance and identify the best model based on the predefined criteria.
   - Fine-tune hyperparameters to improve performance.
   - Compare boosting algorithms with random forests and other simpler models.

[back to top](#rusty-bargain-used-cars-analysis)

## Tools and Techniques Utilized
- **Python Libraries**: `pandas`, `scikit-learn`, `LightGBM`, `CatBoost`, `XGBoost`
- **Model Evaluation Metrics**: RMSE, training time, and prediction speed
- **Data Preprocessing Techniques**: Handling missing values, encoding categorical features, and scaling data
- **Machine Learning Models**: Linear Regression, Decision Tree, Random Forest, Gradient Boosting (LightGBM, CatBoost, XGBoost)

[back to top](#rusty-bargain-used-cars-analysis)

## Specific Results and Outcomes

### 1. Data Exploration and Preprocessing
- The dataset contained **13 features**, including both categorical (e.g., `VehicleType`, `Brand`) and numerical variables (e.g., `Power`, `Mileage`).
- No missing or duplicate values were found, and the initial data quality was generally high.
- After analyzing the features, **outliers** in certain columns (such as `Power` and `RegistrationYear`) were handled to improve model training.
- Categorical features were encoded using **One-Hot Encoding (OHE)** to allow models to process non-numeric data.

### 2. Model Training and Evaluation
- **Linear Regression**: Used as a baseline model to understand how simple the relationship between features and the target (`Price`) is.
  - **RMSE**: Around **3400 Euros**, indicating moderate error for this basic model.
  - **Training Time**: Very low; linear regression models are quick to train.
  
- **Decision Tree and Random Forest**: Introduced more complexity with tree-based models to capture non-linear relationships.
  - **Decision Tree**:
    - RMSE: Around **2700 Euros**, showing improvement over linear regression.
    - Performance was sensitive to the `max_depth` hyperparameter.
  - **Random Forest**:
    - RMSE: Approximately **2000 Euros**, with better generalization compared to Decision Trees.
    - **Training Time**: Longer than Decision Trees but still manageable.

- **Gradient Boosting Models (LightGBM, CatBoost, XGBoost)**:
  - All gradient boosting models outperformed the simpler models, achieving **RMSE** values between **1700 and 1900 Euros**.
  - **LightGBM**:
    - RMSE: Around **1800 Euros**.
    - **Training Speed**: Faster than other boosting models, making it a preferred choice for large datasets.
  - **CatBoost**:
    - RMSE: Approximately **1750 Euros**.
    - **Advantage**: Handles categorical features natively, requiring less preprocessing.
  - **XGBoost**:
    - RMSE: Close to **1900 Euros**.
    - Performed comparably to LightGBM but took longer to train.
  - **Comparison to Baseline**: All boosting models demonstrated significant improvement in prediction accuracy over linear regression and random forests.

### 3. Model Speed and Performance Analysis
- **Training Time**: 
  - Linear regression was the fastest to train, followed by decision trees and random forests.
  - **LightGBM** had the best training speed among gradient boosting models.
  - **CatBoost** required more time than LightGBM but was efficient in handling categorical data.
- **Prediction Speed**: 
  - All gradient boosting models were efficient in making predictions after being trained.
  - LightGBM offered the best trade-off between training time and prediction accuracy.

### 4. Hyperparameter Tuning
- Random forests and gradient boosting models were tuned for `max_depth`, `n_estimators`, and learning rates.
- Tuning significantly improved the RMSE of models, especially for gradient boosting algorithms.

### 5. Final Model Selection
- Based on the **RMSE** scores, **training time**, and **prediction speed**, the **LightGBM** model was chosen as the final model.
- The model achieved an RMSE of around **1800 Euros**, making it both accurate and efficient for predicting car prices.

### Key Insights
- **Importance of Data Preprocessing**: Handling outliers and encoding categorical data were crucial for model performance.
- **Gradient Boosting Superiority**: Gradient boosting models (especially LightGBM and CatBoost) performed better than simpler models like linear regression and random forests.
- **Trade-offs Between Accuracy and Speed**: While boosting models provided high accuracy, they also required more time for training. LightGBM stood out as a balanced choice.

[back to top](#rusty-bargain-used-cars-analysis)

## What I Have Learned From This Project 

- **Modeling and Evaluation**: Gained experience in training multiple models, evaluating them using RMSE, and understanding the trade-offs between various machine learning algorithms.
- **Hyperparameter Tuning**: Learned to fine-tune hyperparameters to improve model performance while maintaining a balance between training time and prediction speed.
- **Working with Tree-Based Models and Boosting Techniques**: Developed skills in using and comparing different tree-based models and boosting techniques such as LightGBM, CatBoost, and XGBoost.
- **Data Preprocessing and Feature Engineering**: Improved competence in preparing data for modeling, handling categorical variables, and ensuring features are scaled appropriately for different algorithms.
- **Handling Non-Normal Data and Transformations**:
  - Learned techniques for addressing skewed or non-normal distributions in features, including:
    - **Box-Cox Transformation**: Used to stabilize variance and make the data more normally distributed.
    - **Square Root Transformation**: Applied to reduce skewness in positively skewed features.
    - **Winsorization**: Managed outliers by limiting extreme values to a defined percentile, enhancing model robustness.
    - **Truncation**: Capped extreme data points based on certain thresholds to reduce the impact of outliers.
    - **Censoring Techniques**: Used for cases where data is only partially observed, helping to improve prediction accuracy by handling such scenarios effectively.
  - Implemented these techniques to achieve better model performance by making feature distributions more suitable for modeling.

[back to top](#rusty-bargain-used-cars-analysis)

## How to use this repository

1. **Clone the repository** <br>
git clone https://github.com/realdanizilla/Rusty-Bargain.git
2. **Install Dependencies:**  
Navigate to the repository directory and install required Python packages. <Br>
(cd Rusty-Bargain pip install -r requirements.txt)
3. **Run the Jupyter Notebook:**<br>
Open the `.ipynb` notebook for data analysis and exploration.
4. **Explore the Data**:  
Follow through the notebook to see data preprocessing, analysis, and model building for predicting Instacart basket compositions. 

5. **Customize and Experiment**:  
Modify code sections to test different models or analysis techniques as desired.

[back to top](#rusty-bargain-used-cars-analysis)