
# University projects
# Predicting future energy use of a household

### Jupyter notebook Link : 
## Goal

Predicting the energy usage in of the house based on 20+ factors including signals obtained from the sensors around the house. The goal is to use regression to predict the energy usage. 

### Steps followed 

- Step 1 : Loading the necessary libraries such as Numpy, Pandas and sklearn.
- Step 2 : Loading the .csv file dataset into a pandas dataframe.
- Step 3 : Data.info() is used to gain preliminary information about the data such as the attributes, their non-null counts and the data type of the values stored for the attributes. This step is essential for data cleaning by converting the attribute to an appropriate data type.
![describe](https://github.com/user-attachments/assets/2fa3146f-3582-46bb-93c3-2d2f68d73a18)
- Step 4 : Describing the dataset reveals insights into the mean, standard deviation in the values, min & max which is useful in understanding the shape of data. Appliances is our target variable.
![info](https://github.com/user-attachments/assets/db77a98a-8856-4908-9ecc-e708f77fbffd)
- Step 5 : Visulalizing the skewness of the data is important as it helps as prepare the data by scaling so as to get accurate predictions hence plotting histogram of the data for each attribute .
![hist](https://github.com/user-attachments/assets/7e36bb9c-f7f0-4151-9933-f6afb29ea678)
- Step 6 : Observing the histograms give us an idea about the shape 
         
   a) The appliances is Right skewed.

   b) T4 and T8 has similiar influence

   c) Rv1 and RV2 seem to be irrelevant as they are evenly distributed

- Step 7 : To predict the accurate usage it is the best practice to use only relevant attributes and redundancy will decrease the performance of the model, hence finding the correlation between the attributes is necessary and then producing a heat map with it so that it is easier to read.
![heatmap](https://github.com/user-attachments/assets/35136579-9361-45fa-92a8-364145ba17d3)
- Step 8 : Next step for data cleaning is dealing with the outliers. Boxplot is used to identify the extent of outliers.
![appliances](https://github.com/user-attachments/assets/4b868da6-f9b9-473b-9d69-47d68189654b)
![other](https://github.com/user-attachments/assets/fde4e1c8-f86c-4f06-82d4-0c4f653a3a33)
- Step 9 : Removing the outliers.
      
      a) Dropping the outliers based on the box plot analysis as majority data lies in the scale of 0 to 200
      b) The attributes of T6,T9, Visibility, pressure, Tdewpoint, Rh_1,RH_2 seems to be irrelevant as analyzed by heatmap above.

- Step 10 : Splitting the training and test data in the rato of 80:20. Random state is introduced so that if you run a different instance to get the same data to be split you shoudl use the same state.

      x_train, x_test, y_train, y_test = train_test_split(X, Y, test_size=0.2, random_state = 42) 

- Step 10 : Scaling the data is important so that the range of all the values in a dataset is of same range as regression analysis is mathematical and prediction is done on slope of the line, this is necessary.

      from sklearn.preprocessing import StandardScaler
      scaler = StandardScaler()
      scaler.fit(x_train)
      x_train = scaler.transform(x_train)
      x_test = scaler.transform(x_test

# Evaluation of model

Evaluation of linear regression is as follows
      
      LinearRegression() 
      Average Error(Mean Absolute Error)       : 19.2971 degrees
      Variance score R^2  : 27.15%
      Accuracy            : 68.97%


Evaluation of SVR model is as follows

      SVR() 

      Average Error(Mean Absolute Error)       : 17.6548 degrees
      Variance score R^2  : 28.56%
      Accuracy            : 74.11%
      The accuracy of the model is 74.11%

Following inferences can be drawn from the output

##### [1] SVR performs better than simple linear regression.
##### [2] Skweness of Applicanes i.e. Target variable is not taken into consideration.
\
Further tuning of the model will result into better model prediction.
