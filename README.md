Overview of the data:

The data set we are considering is related to the PBS(pharmaceutical Benift Scheme) and MBS(Medicare benifit Scheme) data. Here we have patient ID, sex, age, sate and sequence length. So, we will be predicting which type of benifit scheme does the patient have.
We will be using keras LSTM model to do the predictions.

Data Normalization and Conversion:

Data is normalized using MinMaxScaler method that is imported from sklearn.preprocessing. 

we will create features_set and labels list. There are 16322 records in training data. A loop is executed that starts from 91st record and stores all the previous rcords from the traing set into features_set list and the 91st record is stored in the labels list.

These lists are converted into arrays using numpy array. 

In order to train our LSTM model, we need our data in three dimensional format. Where, the first dimension is number of rows in the dataset, second dimension is number of time steps and last dimension is indicators.
So here our first dimension is 16322, second dimension is 90 and third dimension is 3.

DATA SPLITTING:

we are splitting our data into test and train sets using test_train_split function from sklearn.model_selection. Our data is split into 80% train and 20% test.

CREATING THE MODEL:

As the first step in creating the model, a Sequentisal class is instantiated. Later, LSTM layers are added to the created model.
Input layer and hidden layers are given with relu activation function. Where as, sigmoid activation function is given to the out put layer.

Four hidden layers.Units fro the Input layer is taken as 32 and for the hidden layer 150 is taken. default value is considered for the learning rate.
Drop out layer with value 0.2 is added to the hidden layers to avoid the overfitting.

While compiling our model, binary_classentrophy is taken as the loss function and rmsprop as optimzer, to optimize the algorithm.

TRAINIG THE MODEL:

To train our model, fit method is used on the model and it is passed into x_train and y_train sets. with the batch_size 1024.

MAKING THE PREDICTIONS:

Predict method is called onto our model.
As our data is scaled initially, our LSTM predictions are also scaled. So, we need to reverse the scaled predictions back to original values. For that we will be using inverse_transform method.

CROSS VALIDATION:

We will be using StratifiedKFold from scikit-learner.The training dataset is split into 10 folds. Then the performance for each model is printed.
