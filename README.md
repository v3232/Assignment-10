# Assignment-10

## Overview of the Analysis

The purpose of the analysis is to create a machine learning model to identify the credit worthiness of the borrowers of a financial firm using its existing historical data on lending. This data has different aspects such as loan amount, debt-to-income ratio, interest etcetera which was used to obtain the respective credit wothiness. All the healthy loans are termed as '0' and the high-risk loans as '1'. This particular peice of categorized information is taken as the label and the rest of the available data as the features to feed the machine learning algorithm.
There are 77536 samples available in the data in total out of which 75036 are healthy loans and 2500 are high-risk loans.

The data is initially classified into two sets - one for training the model and the other for testing it.  This is done using the 'train_test_split' function. 

The 'LogisiticRegression' classifier model is  used as the machine learning algorithm. The part of the data obained through spliting for the training process is fed to the model for having it trained through the method *.fit*. This model is then used to predict the label classification of the test data features through the method *.predict* to compare with the respective labels from the original data to understand its efficiency.

The imbalance in the quantity of samples in the data of either groups present would make the process of classification less effective. One solution to this is to increase the number of data points of the group with lesser number so that the quantity of the data could be even on both sides. This is carried out using the 'RandomOverSampler' function. It adds random data points to lesser populated group to make the numbers even. In this case,the '1's are brought up to data points same as that of '0's. A second machine learning model is created similar to previous one with this resampled data. The process of feeding the training data and obtaining the prediction with the LogisticRegression is repeated to obtain the output with the classification of the test samples.  


## Results
Let the model processing the original data be called ```Machine Learning Model 1``` and the latter with the modified oversampled data be ```Machine Learning Model 2```.

* Machine Learning Model 1:
    * Accuracy : 0.9520479254722232
    * Precision : '0' - 1.00,  '1' - 0.85
    * Recall : '0' - 0.99, '1' - 0.91


* Machine Learning Model 2:
    * Accuracy : 0.9936781215845847
    * Precision : '0' - 1.00,  '1' - 0.84
    * Recall : '0' - 0.99, '1' - 0.99

### Summary

The selection of a model to use is subjective to the problem that the model is trying to resolve. In this scenario, the bank is trying to classify the loans as good loans and high-risk loans. Both the models have preformed well in identifying good loans with high precision and recall values. 
However in the perspective of the money lending business, it is important to understand the high-risk loan with the most accuracy so that the business will not loose money. Therefore, we need to emphasize on having the false negetives of '1's to be as minimum as possible (or the recall of '1' be maximum). In this context, we can say that the Machine Learning Model 2 is better than Machine Learning Model 1 here.

Even thought the numbers look good with the aforementioned model, I will not recommend either of these models for processing. Machine Learning Model 2 with RandomOversampling definitely gives good prediction when compared with the test data labels, but as the added datapoints for balancing are random, it could corrupt the model. This will result in further producing bad results. It will be a better choice to have synthetic data resampling algorithm like 'SMOTE' to  be used instead of  RandomOverSampling. The data points added on for the balance with this algorithm is closer to the actual ones and hence not disrupting the essence of the data.
