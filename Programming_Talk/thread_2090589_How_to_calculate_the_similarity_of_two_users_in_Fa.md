---
title: "How to calculate the similarity of two users in Facebook?"
date: 2012-12-02
forum: Programming Talk
---

### Post by ldaneil on 2012-12-02
Hi, all , 

I am working on a project about data mining. my company has  given me 6 million dummy customer info of facebook. I was assigned to  find out the similarity between any two users. can anyone could give me  some ideas how to deal with the large community data? Thanks in advance :confused::confused::confused::confused::confused::confused:

Problem : I use the status info  &  hashtag info(hashtags are  those words highlighted by user) as the two criteria to measure the  similarity between two different users. Since the large number of users,  and especially there may be millions of hastags & statuses of each  user. Can anyone tell me a good way to fast calculate the similarity  between two users? I have tried to use FT-IDF to calculate the  similarity between two different users, but it seems infeasible. can  anyone have a very super algorithm or good ideas which could make me  fast find all the similarities between users? 



  For example:
  user A's hashtag = {cat, bull, cow, chicken, duck} 

user B's hashtag ={cat, chicken, cloth} 

 user C's hashtag = {lenovo, Hp, Sony}


  clearly, C has no relation with A, so it is not necessary to  calculate the similarity to waste time, we may filter out all those  unrelated user first before calculate the similarity. in fact, more than  90% of the total users are unrelated with a particular user. How to use  hashtag as criteria to fast find those potential similar user group of  A? is this a good idea? or we just directly calculate the relative  similarity between A and all other users? what algorithm would be the  fastest and customized algorithm for the problem?

---

### Post by carnivroar on 2012-12-02
I have no idea but I came across this book a while ago:

[http://www.amazon.com/Mining-Social-Web-Analyzing-Facebook/dp/1449388345/ref=sr_1_6?ie=UTF8&qid=1354507220&sr=8-6&keywords=data+mining](http://www.amazon.com/Mining-Social-Web-Analyzing-Facebook/dp/1449388345/ref=sr_1_6?ie=UTF8&qid=1354507220&sr=8-6&keywords=data+mining)

---

### Post by ofnuts on 2012-12-03
Do you need to find the similarity between two specific users? Or find others users similar to one specific user? Maybe your problem is an application of [cluster analysis]("http://en.wikipedia.org/wiki/Cluster_analysis") (two users are "similar" if they belong to the same cluster) . Coding this kind of things efficiently is difficult (requires very good background in math), and you should look for specialized software.

---

### Post by monkeybrain2012 on 2012-12-03
I think the general approach involves representing each user as a vector in some N-dimensional vector space where each dimension represents an attribute (depending on its nature can be a score or some binary variable) N = the number of attributes of interests, and then the similarity can be represented by either the distance between the two vectors or the angle between the two vectors (the normalized inner product)

A nice book is 'knowledge discovery with support vector machines", it may be a bit theoretical but I prefer a conceptual rather than a cook book approach. It uses R and weka, both free software and run in Ubuntu (though the versions in the repo are old, R has a ppa, weka is very easy to download from the website and doesn't need installation)

---

### Post by ldaneil on 2012-12-27
> **carnivroar said:**
> I have no idea but I came across this book a while ago:

[http://www.amazon.com/Mining-Social-Web-Analyzing-Facebook/dp/1449388345/ref=sr_1_6?ie=UTF8&qid=1354507220&sr=8-6&keywords=data+mining](http://www.amazon.com/Mining-Social-Web-Analyzing-Facebook/dp/1449388345/ref=sr_1_6?ie=UTF8&qid=1354507220&sr=8-6&keywords=data+mining)
Thanks very much anyway.

---

### Post by ldaneil on 2012-12-27
> **ofnuts said:**
> Do you need to find the similarity between two specific users? Or find others users similar to one specific user? Maybe your problem is an application of [cluster analysis]("http://en.wikipedia.org/wiki/Cluster_analysis") (two users are "similar" if they belong to the same cluster) . Coding this kind of things efficiently is difficult (requires very good background in math), and you should look for specialized software.
Thanks for your reply.  I need to find the related similarity value between all users, then according to the similarity value to build a graph(similarity =0 means no link between the two users), finally using this graph go through the fast unfold community detection algorithm to find the clusters of the social website.

---

