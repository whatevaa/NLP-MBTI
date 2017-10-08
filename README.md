# Coding Challenge - Data Scientist - NLP

This repository was created to host the challenge for Data Scientist - NLP roles at
Chance.

## Evaluation

This is a non-exaustive list of the aspects that we will consider:

* Code organization
* Problem solving
* Code readability
* Chosen solutions
* Version control practices


## Problem - MBTI prediction

On this task you will have to create a model to predict MBTI personality types
from posts. If you don't know what MBTI is, see [MBTI basics]( 
http://www.myersbriggs.org/my-mbti-personality-type/mbti-basics/home.htm?bhcp=1)

### Details

For this task you can use any language of your choice, but we recommend the use
of some of the following: python, jupyter, scikit-learn. You will have
to :
* Create a local git repository
* Download the dataset for this task [here](
    https://www.kaggle.com/datasnaek/mbti-type)
* Create an NLP machine learning algorithm that determines a person personality type based on a set of posts. You can use the model of your preference.
* Train your model, expose it through an API (function), and describe
    how to access it.

## Usage

1. Start a git repository with ```git init```
1. Do your magic on your local machine, trying to commit often
1. Add at the end of this README a small descriptions about your choices.
1. Run ```git bundle create YOURNAME.bundle HEAD ```
1. Send the generated file by email to tech-interview@chance.co


##Design choices
I) Data exploration
* After some tries, I choose to load the dataset with panda read_csv to avoid delimiter problems between header (,) and data (where I need to choose ," as delimiter because there is already coma in the posts content).
* I have created a dictionnary with MBTI type and numerical value (index) to map later the "type" column of train and test set in order to have numerical values.
II) Data cleaning
* I have removed all the url in the posts content in order to facilitate the work ok CountVectorizer()
III) Data preparation: Bag of words
* Given the time I have choosen to use existing functions for the vectorization, the occurencies count (CountVectorizer) and normalization (Tf-idf).
* I have choosen to contruct a test set of 25% of the origin dataset and so a train set of 75% of the origin dataset.
IV) Models
* I have choosen to execute several classifier because results were not satisfying:
	>> MultinomialNB which is pretty used for text classification
	>> SGDClassifier, on of the more used for text classification and that give better results
	>> Logistic regression, also frequently used
V) Improve Bag of Words and redo models
* As my classification accuracies were not good even after several models, I choose to add modifiction in CountVectorizer parameters to improve the text treatment and quality of the words dictionnary by:
	>>adding english stop words
	>>adding in the word dictionnary group of two words
	>>removing words that appear in more than 50% of the posts
	>>removing words that appear in less than two posts
