# Recommender-System-based-on-user-clickstream

## Aim
The primary objective of this project is to build an efficient **News Recommender System** that can attract
more users. The recommender system will provide suggestions to new and old users. The recommender
system is divided into two cases:

* **User profile not available :** In this case, the bot will recommend the user with a set of diverse
articles. It is similar to the classical cold start problem, i.e. when a new user joins, the system does
not have any initial information regarding the user profile. 
* **User profile available:** User profile is the information of clickstream data, like articles read by the user and time spent on it.
In this we recommend articles using various methods.

## Clickstream data
Once the user starts consuming news stories, (s)he leaves behind a
clickstream which can be then used to uncover user interests and provide personalized
recommendations. In this project we will not use clickstream data of any real website;
we will try to generate it using some of the assumptions discussed in the report. We generated a user clickstream data which contains
the following attributes:

  * User ID - ID given to each unique user on the app
  * Session ID - Refers to each new visit of the user on the app
  * Article ID - A unique ID given to each article
  * Click - Takes the value ‘Yes’ if the article has been clicked by the user, otherwise no.
  * Time spent - Time spent by the user on a particular article in seconds
  * Rating - Rating of an article ranging from 1 to 5. Correlated with time spent.

## Recommender systems
* **Content-based recommendation systems (CBRS)** -
These systems recommend items with similar content from the ones the user liked in the
past. In this type of RS, the clickstream based user profile (up) represents the user interests.
I have implemented the following two approaches for content-based system :
  * **Tfidf based approach** - A tfidf_matrix containing each word and its TF-IDF score with regard
to each document was generated and the cosine similarity of the whole corpus with user read
articles was further calculated. Thus, each new item is compared to user profile, and the most
similar articles are recommended. It minimizes the cold start problem: new items can be
suggested before being rated by a substantial number of users as opposed to collaborative
filtering.
  * **Topic Modeling based approach** - LDA (Latent Dirichlet Allocation) model is used on
the cleaned/preprocessed news articles. The articles were represented in terms of Topic Vector
and users in terms of the Topic Vector of read articles. We then calculated the similarity of
cosines between read articles topic vector and total articles topic vector and give
recommendations based on the same.

* **Collaborative recommendation systems**-
Collaborative recommendation systems use an approach that focuses on the relations
between users or articles. The underlying assumption of the collaborative filtering approach is
that if a person A has the same opinion/taste as a person B on a set of items, A is more likely to
have B’s opinion for a given item than that of a randomly chosen person. Thus, the
recommended articles are selected from users who have read similar articles based on their
history. We cannot use collaborative recommenders in the beginning as there won't be
significant user information to perform the recommendation.following two approaches for user-based collaborative 
filtering are implemented:

    * **Collaborative filtering based on user similarity score** - users vs document
rating matrix is created and useed it to find the cosine similarity between different users. then estimate the
unknown rating by taking weighted average and then recommend 10 articles based on the
estimated ratings.

    * **Collaborative filtering based on matrix decomposition/SVD** - The user vs article
rating matrix is calculated and reduced its dimensions using Singular Value Decomposition method. The
user vs article matrix was then re-calculated to recommend articles based on the estimated
ratings.

## Evaluation
* Silhouette Score - For validation of the K-means clustering algorithm, silhouette score has been calculated to decide
the optimum number of clusters to be formulated from the data

* NDCG Score - To calculate the score of each recommender system





## Acknowledgments

* I would like to acknowledge the significant contributions of my peers Prerna, Nevil and Himanshu to this project.
