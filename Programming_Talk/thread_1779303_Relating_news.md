---
title: "Relating news"
date: 2011-06-10
forum: Programming Talk
---

### Post by RobikShrestha on 2011-06-10
We are supposed to do a minor project. In this project we need to collect news from various sources and create a webpage in which the related news articles are grouped together. I have googled for algorithms, but they are too vague and do not specify the exact algorithms. Can anyone help me with some algorithms or links to algorithms. We would be very grateful.

---

### Post by simeon87 on 2011-06-10
What precisely do the algorithms need to do?

There exist libraries already for scraping the content and you could then build a classifier system that determines what content is "related" (e.g., composed mostly of the same words). What are your own ideas on how the system is supposed to work?

---

### Post by RobikShrestha on 2011-06-10
What we are trying to do is to collect news from various RSS feeds. Then categorize them in broad categories like: sports and politics. Then, considering that most of the related news get published on the same date, we would use the algorithms to find out whether they are related or not. 
By relation, we mean, they may be different publications of same news, an extension on the news, or some news of similar concerns. eg: news concerning public revolution in one Arab country is related to the same in another Arab country.

We plan to do this in java. Where are the libraries available? Can we directly use them, are they open source? If they are not in java, may be we would have to understand the algorithm and write our own codes in java.

Our plans:
The algorithms,  suggest KEYWORDS.
The keywords are searched for in all the categorized documents.
The frequency of occurrence is used to finally decide, whether or not the documents are related.

---

### Post by simeon87 on 2011-06-10
> **RobikShrestha said:**
> What we are trying to do is to collect news from various RSS feeds. Then categorize them in broad categories like: sports and politics. Then, considering that most of the related news get published on the same date, we would use the algorithms to find out whether they are related or not. 
By relation, we mean, they may be different publications of same news, an extension on the news, or some news of similar concerns. eg: news concerning public revolution in one Arab country is related to the same in another Arab country.

We plan to do this in java. Where are the libraries available? Can we directly use them, are they open source? If they are not in java, may be we would have to understand the algorithm and write our own codes in java.

Our plans:
The algorithms,  suggest KEYWORDS.
The keywords are searched for in all the categorized documents.
The frequency of occurrence is used to finally decide, whether or not the documents are related.

I'm sure there are RSS libraries for Java, you'll need to evaluate them to see which one suits your needs. But any basic one will do I think: you just need to get some facts and content from each item in the RSS feed. This should be easier than literally scraping the content from webpages.

You can then store them and do further processing on them. You can then analyze the text of each news item and calculate what you need to know.

---

### Post by RobikShrestha on 2011-06-10
Thanks for the reply. 
I was also looking to do some research on existing algorithms on finding RELATED NEWS. If you can, please help.

---

### Post by simeon87 on 2011-06-10
I would expect it to involve some data mining algorithms. But we don't do homework, per forum rules.

---

### Post by RobikShrestha on 2011-06-10
Well, the homework part is not to develop new algorithms. Rather, it is a research project and finally we are supposed to implement existing algorithms in java. But I can't find the algorithms. I have come up with a few of my own, like I have modified the page Rank algorithm of google to suit our purpose. But I can't find others.

---

