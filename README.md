In this project, I will try to explore the Wine Reviews Dataset. It contains 130k of reviews in Wine Reviews. And at the end of this notebook, I will try to make simple text summarizer that will summarize given reviews. The summarized reviews can be used as a reviews title also.I will use Spacy as natural language processing library for handling this project.  

### OBJECTIVE

The objective of this project is to build a model that can create relevant summaries for reviews written on Wine reviews. This dataset contains above 130k reviews, and is hosted on Kaggle.

### WHAT IS TEXT SUMMARIZATION

![image](https://github.com/sandeepkumarnaini/Text-Summarization-using-Spacy/assets/146559532/80ea33d2-8ca9-4721-8ea5-a7da09d21495)

Text summarization is the process of distilling the most important information from a source (or sources) to produce an abridged version for a particular user (or users) and task (or tasks).

###  Types of Text Summarization Methods
Text summarization methods can be classified into different types.

![image](https://github.com/sandeepkumarnaini/Text-Summarization-using-Spacy/assets/146559532/720bddff-31b2-4bda-be13-6c9df0b73659)

1. Based on input type:
   
   i.  Single Document, where the input length is short. Many of the early summarization systems dealt with single document summarization.
   
   ii. Multi Document, where the input can be arbitrarily long.

2. Based on the purpose:
    
    i. Generic, where the model makes no assumptions about the domain or content of the text to be summarized and treats all inputs as 
        homogeneous. The majority of the work that has been done revolves around generic summarization.
   
    ii. Domain-specific, where the model uses domain-specific knowledge to form a more accurate summary. For example, summarizing 
        research  papers of a specific domain, biomedical documents, etc.
   
    iii. Query-based, where the summary only contains information which answers natural language questions about the input text.

3. Based on output type:

      i. Extractive, where important sentences are selected from the input text to form a summary. Most summarization approaches today 
          are extractive in nature.

      ii. Abstractive, where the model forms its own phrases and sentences to offer a more coherent summary, like what a human would 
           generate. This approach is definitely a more appealing, but much more difficult than extractive summarization.

# 1. Import Packages

# 2. Import Dataset
In this section, I will load the desired dataset for this notebook. This dataset has huge number of reviews. It will be hard to work with full dataset. So I will randomly sample the dataset into smaller chunks for easy purpose

# 3. Text preprocessing
In this step, I will be using Spacy for preprocessing text, in others words I will clearing not useful features from reviews title like punctuation, stopwords. For this task, there are two useful libraries available in Python. 1. NLTK 2. Spacy. In this notebook, I will be working with Spacy because it is very fast and has many useful features compared to NLTK. So without further do let's get started!

Before normalizing text-----

Tart and snappy, the flavors of lime flesh and rind dominate. Some green pineapple pokes through, with crisp acidity underscoring the flavors. The wine was all stainless-steel fermented.

After normalizing text-----

Tart and snappy, the flavors of lime flesh and rind dominate. Some green pineapple pokes through, with crisp acidity underscoring the flavors. The wine was all stainless-steel fermented.
Now we can see our text is more manageable. This will help us to explore the reviews and later making summarizer.

We are also seeing that there are some punctuation and stopwords. We also don't need them. In the first place, I don't remove them because we are gonna need this in future when we will make summarizer. So let's make another column that will store our normalized text without punctuation and stopwords.

# 3.1 Clean text before feeding it to spaCy 

Reviews description with punctuatin and stopwords---

Aromas include tropical fruit, broom, brimstone and dried herb. The palate isn't overly expressive, offering unripened apple, citrus and dried sage alongside brisk acidity.

Reviews description after removing punctuation and stopwrods---

aroma include tropical fruit broom brimstone dry herb . palate overly expressive offer unripened apple citrus dry sage alongside brisk acidity .
Wow! See! Now our text looks much readable and less messy!

# 4. Distribution of Points
In this section, I will try understand the distribution of points. Here points mean number of upvote the description got in social media(such as facebook,twitter etc).

![image](https://github.com/sandeepkumarnaini/Text-Summarization-using-Spacy/assets/146559532/3bd1d661-ff4f-48de-9f73-e4a5a3d292e8)

The description of points lies between 80 to 100 mostly. Majority of the description got points between 80 to 100.

# 5. Analyze reviews description
In this section, I will try to analyze wine description. In Wine Reviews, the wine description plays a vital role. A good description can make your wine stand out. It also helps get a reviews faster. Lastly, It will help you get some points. Let's see what we can find in the wine description.

![newplot](https://github.com/sandeepkumarnaini/Text-Summarization-using-Spacy/assets/146559532/ffcb0bf4-d0c5-4514-b058-f099a11ac04d)

# 6. Description Summarizer

In this step, I will try to make a description summarizer. There is a huge amount of research going for text summarization. But I will try to do a simple technique for text summarization. The technique describes below.

# 6.1 Convert Paragraphs to Sentences
We first need to convert the whole paragraph into sentences. The most common way of converting paragraphs to sentences is to split the paragraph whenever a period is encountered.

# 6.2 Text Preprocessing
After converting paragraph to sentences, we need to remove all the special characters, stop words and numbers from all the sentences.

# 6.3 Tokenizing the Sentences
We need to tokenize all the sentences to get all the words that exist in the sentences

# 6.4 Find Weighted Frequency of Occurrence
Next we need to find the weighted frequency of occurrences of all the words. We can find the weighted frequency of each word by dividing its frequency by the frequency of the most occurring word.

# 6.5 Replace Words by Weighted Frequency in Original Sentences
The final step is to plug the weighted frequency in place of the corresponding words in original sentences and finding their sum. It is important to mention that weighted frequency for the words removed during preprocessing (stop words, punctuation, digits etc.) will be zero and therefore is not required to be added

# 6.6 Sort Sentences in Descending Order of Sum
The final step is to sort the sentences in inverse order of their sum. The sentences with highest frequencies summarize the text.

Now we have written the function let's try to summarize some descriptions.

Original Text:

Savory dried thyme notes accent sunnier flavors of preserved peach in this brisk, off-dry wine. It's fruity and fresh, with an elegant, sprightly footprint.

Summarized text:

Savory dried thyme notes accent sunnier flavors of preserved peach in this brisk offdry wine Its fruity and fresh with an elegant sprightly footprint

That's awesome! We successfully made a simple wine review description summarizer.
