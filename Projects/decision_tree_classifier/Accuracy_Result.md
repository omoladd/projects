### Accuracy

- **Accuracy:** 0.8705, which means the model correctly predicts the outcome for approximately 87.05% of the instances in the test set.

### Classification Report

- **Precision, Recall, and F1-Score for Class 0 (Not subscribed):**
    - **Precision:** 0.93 (93% of the predicted "not subscribed" were actually correct)
    - **Recall:** 0.92 (92% of the actual "not subscribed" were correctly identified)
    - **F1-Score:** 0.93
- **Precision, Recall, and F1-Score for Class 1 (Subscribed):**
    - **Precision:** 0.46 (46% of the predicted "subscribed" were actually correct)
    - **Recall:** 0.48 (48% of the actual "subscribed" were correctly identified)
    - **F1-Score:** 0.47
- **Macro Average:** Averages the precision, recall, and F1-score of both classes equally.
    - **Precision, Recall, F1-Score:** 0.70
- **Weighted Average:** Averages the precision, recall, and F1-score weighted by the number of true instances for each label.
    - **Precision, Recall, F1-Score:** 0.87

### Confusion Matrix

- **True Positives (TP):** 528 (Correctly predicted "subscribed")
- **True Negatives (TN):** 7344 (Correctly predicted "not subscribed")
- **False Positives (FP):** 608 (Incorrectly predicted "subscribed" when it was "not subscribed")
- **False Negatives (FN):** 563 (Incorrectly predicted "not subscribed" when it was "subscribed")

### Analysis

1. **Class Imbalance:**
    - The model performs well in predicting "not subscribed" (class 0) but poorly in predicting "subscribed" (class 1).
    - This disparity suggests a class imbalance in the dataset, with many more instances of "not subscribed" than "subscribed."
2. **High Accuracy but Low F1-Score for Class 1:**
    - The overall accuracy is high (87%), but this is mainly due to the performance on the dominant class (class 0).
    - The F1-score for class 1 is low, indicating that the model struggles with correctly identifying positive instances.

There seems to be an oversampling case where the model performs well in predicting "not subscribed" (class 0) but poorly in predicting "subscribed" (class 1). To mitigate this problem I balanced the class weights but didn’t see much improvement in the model accuracy. So bagging ensembling technique is carried out. 

**Result of Bagging Ensembling Technique**

### Accuracy

- **Before:** 0.8705
- **After:** 0.8951

The overall accuracy of the model increased from 87.05% to 89.51%, indicating that the bagging technique improved the general performance of the model.

### Classification Report

### Class 0 (Majority Class)

- **Precision:** Increased from 0.93 to 0.93 (slightly improved)
- **Recall:** Increased from 0.92 to 0.96 (noticeable improvement)
- **F1-score:** Improved from 0.93 to 0.95

Class 0's performance has improved in recall and F1 Score, meaning the model is better at correctly identifying instances of class 0.

### Class 1 (Minority Class)

- **Precision:** Increased from 0.46 to 0.63 (significant improvement)
- **Recall:** Slightly decreased from 0.48 to 0.47 (small decrease)
- **F1-score:** Increased from 0.47 to 0.54 (noticeable improvement)

The precision for class 1 has improved significantly, meaning the model is better at correctly identifying true positives for class 1. The recall slightly decreased, but the overall F1-score, which balances precision and recall, has increased, indicating an overall better performance for the minority class.

### Macro Average

- **Precision:** Increased from 0.70 to 0.78
- **Recall:** Stayed the same at 0.70, but closer to 0.72
- **F1-score:** Increased from 0.70 to 0.74

The macro average shows improvement in precision and F1-score, indicating a better balance in performance across both classes.

### Weighted Average

- **Precision:** Increased from 0.87 to 0.89
- **Recall:** Increased from 0.87 to 0.90
- **F1-score:** Increased from 0.87 to 0.90

The weighted averages also show an overall improvement in the model’s performance, indicating that the bagging technique has positively impacted the model’s ability to predict both classes correctly.

### Conclusion

Overall, bagging has improved the model’s performance, especially in terms of precision and F1-score for the minority class (class 1). The increase in overall accuracy and weighted averages indicates that the model is now more robust and better at handling the imbalanced nature of the dataset. Despite the slight decrease in recall for class 1, the overall performance enhancements suggest that bagging has made your model more reliable and effective.