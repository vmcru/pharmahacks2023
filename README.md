# pharmahacks2023

based on the following [paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7390976/)

## What it does
Boosting is an ensemble technique that attempts to create a strong classifier from a number of weak classifiers.

## How we built it
We followed instructions from documentation on scikit learn and XGBoost packages in order to build and test our models. The code was written in python in a Google Colab notebook. 

For data processing, we converted labels > 90 to 0 (sufficient) and labels <= 90 to 1 (insufficient). We then used three feature selection techniques, namely SelectKBest, SelectFromModel, and SequentialFeatureSelection, to select the most informative features. 

### Sequential Feature Selection
Our feature selection process follows a greedy approach, selecting the best performing feature (accuracy) until specified number of features selected. We picked the fewest number of features with the largest cross validated accuracy. We generated one feature set for each model.

## Challenges we ran into
Finding ways to do feature selection for each model was quite tricky. We ended up having to test many things manually in a greedy fashion in order to get optimal results for each model. 

Another challenge was our initial approach to solving the classification problem. We initially tried to predict the percent value  and then select sufficient or insufficient based on the threshold set by the paper. However this resulted in subpar predictions for all tested models. However, once we changed our models from regression based to directly binary classification, we were able to eliminate that source of error and yield better results overall. 

## Accomplishments that we're proud of
We wanted to see if it was possible to get similar results using data that was only available 3 days into the experiment instead of all 5 days since the goal of the paper was to see how early they could begin making predictions about the 10th day. In the paper they compared what was possible on the 7th day with the 5th day. We were able to show that similar levels of accuracy were possible on the 3rd day which would be economical in terms of resources used to generate the data. In other words, we reduced the cost of the prediction by a considerable amount. 

## What we learned
Data preprocessing makes a huge difference in the way our model works. In just changing the nature of what we are predicting while maintaining the same goal, we can increase performance by an impressive amount. 

## What's next for Boosting Algorithms for Stem Cell Content Prediction
A new avenue to take for the project could be to improve models using hyper parameter tuning using other methods. We could also incorporate more feature selection methods to narrow down to better results.  
