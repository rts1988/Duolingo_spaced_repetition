# Duolingo_spaced_repetition

Introduction
Duolingo is a popular ed-tech company that gamifies language learning. It has a freemium business model, so increasing student engagement is vital.

As part of its plan for increasing student engagement, Duolingo predicts how well a student might have retained the meanings and usage of words, and constructs a model of student’s memory to produce targeted practice sessions that review words before they are forgotten, and maximize retention (see below image). These indicators allows learners to better plan their study time, encouraging better retention, and therefore increasing motivation to continue using Duolingo.

image.png

Fig.1 -Duolingo strength meter
This series of notebooks is the code for a capstone project in predicting how well a student has remembered a word to fill in the strength meters for every word the student has learned, based on a replication dataset published by B. Settles and B. Meeder. 2016. A Trainable Spaced Repetition Model for Language Learning. In Proceedings of the Association for Computational Linguistics (ACL), pages 1848-1858.

In my capstone, using the dataset provided, the following questions are explored:

Q1) What makes words difficult or easy for a student to remember?

In addition to the sparse lexeme tags provided in the dataset, a number of word-based features are considered, such as the IDF of the word in English, the lexical similarity of the word in the language being learned, and the learner's native language, and word embeddings.

Classical machine learning techniques such as logistic regression, SVM, kNN, decision trees, ensemble techniques such as random forests, XGBoost, and finally, neural nets are trained and compared.

The test set for Q1 consists of words not seen in the training data.

Q2) What learning habits increase a student's retention?

Although the dataset only spans a short time, student performance as a function of time is encoded in daily average features in a manner similar to a time series, and added to the best model of Q1 to see how prediction performance improves.

The test set for Q2 consists of students not seen in the training data.

Q3) The cold-start problem: Duolingo is always adding new language courses, might good predictions based on learnings from Q1 and Q2 be possible for a NEW LANGUAGE?

The best model from Q2 is tested on two new languages courses unseen by the model.

The dataset spans 14 days of students learning second languages through Duolingo’s gamified system and has 12.8 million records and 12 variables.

Feature sets:

How well a word is retained depends on the word itself, and the student’s individual learning pace and capacity. The following features were provided in the dataset.

Interaction features: includes total number of times a student has seen the word , the number of times it was correctly recalled, the number of times incorrectly recalled.

Lexeme tag features: meant to capture the inherent difficulty of each particular word.

In the dataset, the lexeme string has a format like below: "surface form/lemma<pos><modifiers>"

For instance hombre/hombre<n><m><sg> - where hombre ('man' in Spanish) has a lemmatized form 'hombre', is a noun (<n>), and has modifier tags <m> and <sg>

Link for dataset download: https://paperswithcode.com/dataset/duolingo-spaced-repetition-data

Data dictionary:

p_recall - proportion of exercises from this lesson/practice where the word/lexeme was correctly recalled
timestamp - UNIX timestamp of the current lesson/practice
delta - time (in seconds) since the last lesson/practice that included this word/lexeme
user_id - student user ID who did the lesson/practice (anonymized)
learning_language - language being learned
ui_language - user interface language (presumably native to the student)
lexeme_id - system ID for the lexeme tag (i.e., word)
lexeme_string - lexeme tag (see below)
history_seen - total times user has seen the word/lexeme prior to this lesson/practice
history_correct - total times user has been correct for the word/lexeme prior to this lesson/practice
session_seen - times the user saw the word/lexeme during this lesson/practice
session_correct - times the user got the word/lexeme correct during this lesson/practice
Here 
 

In the rest of this notebook, we will clean the downloaded dataset, and do some preliminary EDA to understand the breadth and depth of the data.

The dataset was downloaded to my Google drive, and is now copied to the notebook.
