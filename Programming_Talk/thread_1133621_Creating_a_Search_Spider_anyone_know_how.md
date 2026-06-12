---
title: "Creating a Search Spider anyone know how?"
date: 2009-04-23
forum: Programming Talk
---

### Post by thenetduck on 2009-04-23
Hi 

I am interested in making my own search spider (just to say I made one). I tried doing google searches for the subject but I just get information about PageRank. I'm looking for information on how to create a search spider with c++ or c or whatever and how to run one.

Does anyone either know where to start or have a good resource about this subject? I'm a self taught programmer so haven't been able to rely on schooling for this type of thing. 

Thanks, 

The Net Duck

---

### Post by Kilon on 2009-04-23
> **thenetduck said:**
> Hi 

I am interested in making my own search spider (just to say I made one). I tried doing google searches for the subject but I just get information about PageRank. I'm looking for information on how to create a search spider with c++ or c or whatever and how to run one.

Does anyone either know where to start or have a good resource about this subject? I'm a self taught programmer so haven't been able to rely on schooling for this type of thing. 

Thanks, 

The Net Duck

I guess we are talking about a metacrawler ?

[http://en.wikipedia.org/wiki/Metacrawler](http://en.wikipedia.org/wiki/Metacrawler)

---

### Post by Kilon on 2009-04-23
maybe something like this ?

[http://www.cs.uiowa.edu/~asignori/helios/](http://www.cs.uiowa.edu/~asignori/helios/)

by the way it include the source in the download and is written in C. Should be enough.

---

### Post by tatw on 2009-04-23
You can make a score system for searches.

For example

If title include searched keyword
Add Score 40
If domain 
Add Score 70
If description
Add Score 30
If keyword 
Add Score 20
If in HTML
Add Score 25
If In Headers like h1, h2 in HTML
Add Score 15
If in <p>
Add Score 10 

and you can score all results and you can order by score

---

### Post by cabalas on 2009-04-23
It might be worth having a look at [nutch]("http://lucene.apache.org/nutch/") - which is an open source search engine - it has a crawler component that you can look at.

---

