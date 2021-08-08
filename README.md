# Autorec
## Auto Encoders meet collaborative filtering
this is a recommender system based on a technique that is called denoising autoencoders. one of the applications of denoising autoencoders is in the pictures. basically in this technique we are going to pass in a noisy image as input and the autoencoder will reconstruct the whole image.

if we consider the user-movie-rating matrix as an image, then the ratings in the matrix would be like pixels of an image and the missing ratings are like missing pixels of the image. so first of all we need to build a N * M matrix where N is the number of users and M is the number of movies. values of this matrix are ratings of the users. we consider this matrix as a noisy input to the autoencoder. in the preprocess2sparse file I created this matrix and I used 90% of the dataset for training, and 10% for testing.

## Calculating cost
in this matrix we don't have any missing values, there are just zeros. but we know that zeros represent missing values. so the key here is to build the cost function by using a mask. only if the input is non-zero should be contributed to the cost. in the best case

## Experiments
The experiment is performed on movielens-100k dataset. I used the slightly different configurations as the original paper: hidden units = 700, use L2-regularization, 90% train, 10% test, activation function = tanh, and I also used dropout technique.

The best training loss :

Keras loss = 0.7520 

MSE = 0.5599


The best validation loss :

Keras loss = 0.9505 

MSE = 0.7526


first picture: Keras loss function

second picture: my custom-loss function (MSE)

![image](https://user-images.githubusercontent.com/67679543/128638520-847c0d42-7fab-43de-bdaf-53f200d315cd.png)

![image](https://user-images.githubusercontent.com/67679543/128638539-8f8a2859-6e78-42ae-94f1-eb79044302d0.png)


