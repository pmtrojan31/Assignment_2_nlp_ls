# Why the manual implementation is different from Scikit-Learn's TfidfVectorizer():

The IDF values were different. For example for the word "the", since it appears in every document, the IDF value should have been log(3/3) = 0. However, using the TfidfVectorizer(), we see that the IDF value is 1. The reason is that a different formula is used by this Scikit-Learn class:

(count_of_term_t_in_d) * ((log ((NUMBER_OF_DOCUMENTS + 1) / (Number_of_documents_where_t_appears +1 )) + 1)

This is followed by normalization of all the IDF values. 

The formula I used in the manual implementation is:

log ((NUMBER_OF_DOCUMENTS) / (Number_of_documents_where_t_appears))