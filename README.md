# Fraud Detection System Using Machine Learning

A comprehensive machine learning project for detecting fraudulent financial transactions using advanced classification algorithms and feature engineering techniques.

## Project Overview

This project develops a robust fraud detection model for a financial company to identify fraudulent transactions in real-time. The solution uses Random Forest classification to achieve high accuracy while minimizing false positives, making it suitable for production deployment.

### Key Achievements
- **98.96% Recall** - Catches nearly all fraudulent transactions
- **96.95% Precision** - Minimizes false alarms to reduce customer friction
- **99.70% AUC Score** - Near-perfect discrimination ability
- **Only 4 missed frauds** out of 385 in test set

## Problem Statement

To develop a predictive model for identifying fraudulent transactions and derive actionable insights to help financial institutions:
- Minimize financial losses from fraud
- Reduce false positives that impact customer experience
- Provide real-time fraud detection capabilities
- Identify key fraud indicators for preventive measures

## Dataset

The dataset contains financial transaction records with the following features:

| Feature | Description |
|---------|-------------|
| `step` | Time unit (1 step = 1 hour) |
| `type` | Transaction type (PAYMENT, TRANSFER, CASH_OUT, DEBIT, CASH_IN) |
| `amount` | Transaction amount |
| `nameOrig` | Customer initiating the transaction |
| `oldbalanceOrg` | Origin account balance before transaction |
| `newbalanceOrig` | Origin account balance after transaction |
| `nameDest` | Destination account |
| `oldbalanceDest` | Destination balance before transaction |
| `newbalanceDest` | Destination balance after transaction |
| `isFraud` | Target variable (1 = fraud, 0 = legitimate) |
| `isFlaggedFraud` | System-flagged suspicious transactions |

## Methodology

### 1. Data Cleaning
- Handled missing values (removed 1 row with incomplete data)
- Detected and analyzed outliers (kept them as they represent real high-value transactions)
- Verified data quality and consistency

### 2. Exploratory Data Analysis
- **Fraud Distribution**: Identified severe class imbalance (fraud rate < 1%)
- **Transaction Type Analysis**: TRANSFER and CASH_OUT transactions most prone to fraud
- **Amount Patterns**: Most frauds occur in ₹50K-₹200K range
- **Balance Patterns**: Fraudulent transactions often drain accounts completely
- **Time Patterns**: Higher fraud rates during late-night/early-morning hours

### 3. Feature Engineering
Created new features to capture fraud patterns:
- `balanceChange_Orig`: Change in origin account balance
- `balanceChange_Dest`: Change in destination account balance
- `isNewBalanceOrigZero`: Flag for completely drained accounts
- `isNewBalanceDestZero`: Flag for destination account drainage
- `errorBalanceOrig`: Mathematical inconsistencies in balance calculations
- `errorBalanceDest`: Destination balance anomalies
- `amount_to_oldbalance_ratio`: Transaction to balance ratio
- Time-based features for temporal patterns

### 4. Data Preprocessing
- Label encoding for categorical features
- Train-test split (75-25 ratio)
- Feature scaling using StandardScaler
- SMOTE (Synthetic Minority Over-sampling Technique) to handle class imbalance

### 5. Model Development
Trained and compared multiple models:
- **Logistic Regression**: Baseline model
- **Random Forest Classifier**: Final selected model
- Evaluated using precision, recall, F1-score, and AUC-ROC

## Model Performance

### Random Forest (Final Model)

| Metric | Score |
|--------|-------|
| Accuracy | 99.99% |
| Precision | 96.95% |
| Recall | 98.96% |
| F1-Score | 97.95% |
| AUC-ROC | 99.70% |

### Confusion Matrix Results
- **True Negatives**: 317,415 (correct legitimate predictions)
- **True Positives**: 381 (correct fraud detections)
- **False Positives**: 12 (false alarms)
- **False Negatives**: 4 (missed frauds)

### Why Random Forest?
Random Forest outperformed Logistic Regression by:
- Maintaining excellent fraud detection (98.96% recall)
- Achieving significantly higher precision (96.95% vs 70.69%)
- Reducing false alarms by 87% (12 vs 96 false positives)
- Providing better customer experience with fewer legitimate transactions flagged

## Key Fraud Predictors

The top 5 features for fraud detection:

1. **errorBalanceOrig** - Mathematical inconsistencies indicating transaction tampering
2. **amount_to_oldbalance_ratio** - Transactions using >70% of balance signal account draining
3. **balanceChange_Orig** - Large negative values indicate significant fund extraction
4. **isNewBalanceOrigZero** - Account emptying (80% of frauds completely drain accounts)
5. **type_encoded** - TRANSFER transactions are 800× riskier than PAYMENT transactions

## Technologies Used

- **Python 3.**
- **Data Analysis**: pandas, numpy
- **Visualization**: matplotlib, seaborn
- **Machine Learning**: scikit-learn
- **Imbalanced Data**: imbalanced-learn (SMOTE)
- **Statistical Analysis**: statsmodels

## Results & Insights

### Business Impact
- **Fraud Prevention**: Catches 98.96% of fraudulent transactions
- **Cost Reduction**: Minimizes false positives, reducing investigation costs by 87%
- **Customer Experience**: Only 12 false alarms per 317,427 legitimate transactions
- **Risk Mitigation**: Identifies high-risk transaction patterns for preventive action

### Actionable Recommendations
1. **Enhanced Monitoring**: Apply stricter security checks for TRANSFER and CASH_OUT transactions
2. **Risk Scoring**: Flag transactions that drain >70% of account balance
3. **Time-Based Alerts**: Increase monitoring during late-night hours
4. **Balance Verification**: Implement real-time balance consistency checks
5. **Amount Thresholds**: Special scrutiny for transactions in ₹50K-₹200K range

## 🔮 Future Enhancements

- [ ] Deep Learning models (Neural Networks, LSTM for sequential patterns)
- [ ] Real-time fraud detection API
- [ ] Ensemble methods combining multiple models
- [ ] Anomaly detection using unsupervised learning
- [ ] Integration with live transaction streams
- [ ] Dashboard for monitoring fraud metrics
- [ ] A/B testing framework for model updates


---

⭐ **If you found this project helpful, please consider giving it a star!**
