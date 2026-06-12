---
title: "how does google work...indexing pages"
date: 2008-12-11
forum: Programming Talk
---

### Post by badperson on 2008-12-11
Okay,
I should probably know this, and I think I have an idea; but google indexes the content of webpages (dynamic sites also) and places that content on their own servers, so when you do a google search, you're searching through their database, correct? 
bp

---

### Post by jimi_hendrix on 2008-12-11
i think you are correct...i think it goes

webcrawler rips page -> parse for title -> stick in server

---

### Post by jespdj on 2008-12-12
Yes, that's basically how Google works. They have hundreds of thousands of servers around the world, and they use very sophisticated software and algorithms, for example [MapReduce](http://en.wikipedia.org/wiki/MapReduce). They only hire the smartest elite programmers - it's very hard to get a job at Google.

See: [Google spotlights data center inner workings](http://news.cnet.com/8301-10784_3-9955184-7.html)

From that article:
> ...that would mean Google has more than 200,000 servers, and I'd guess it's far beyond that and growing every day.

---

### Post by Cracauer on 2008-12-13
> **badperson said:**
> Okay,
I should probably know this, and I think I have an idea; but google indexes the content of webpages (dynamic sites also) and places that content on their own servers, so when you do a google search, you're searching through their database, correct? 
bp

Of course they use a suitable index representation so that they don't run
`grep <searchterm> /mnt/bigdrive/the/iternet/*.*`
every time you hit them.

The algorithm to support the word-based search is pretty trivial.

The meat of google's cleverness is in the ranking.

For small web pages they actually store a local copy of the whole thing. For bigger ones they index on the fly.

---

### Post by pmasiar on 2008-12-13
> **Cracauer said:**
> The meat of google's cleverness is in the ranking.

For small web pages they actually store a local copy of the whole thing. For bigger ones they index on the fly.

Index on the fly? Kidding, right? 

Meat of Google cleverness is [http://en.wikipedia.org/wiki/Bigtable](http://en.wikipedia.org/wiki/Bigtable) - proprietary database system storing results, and [http://en.wikipedia.org/wiki/Google_File_System](http://en.wikipedia.org/wiki/Google_File_System) to store the data on computer clusters - and the scripts (big part written in Python BTW) managing the deployment.

Ranking is only the icing on the cake.

---

### Post by slavik on 2008-12-13
google also keeps track of how often pages change, so if a page changes often, it will index it more often.

---

### Post by Mickeysofine1972 on 2008-12-13
If your interested in making a search that you can use on your own site the i recommend using mysqls FULLTEXT indexing features along side the soundex functions available in PHP.

heres a example in the one of the sites I did lately :

[http://www.northumberland.ac.uk](http://www.northumberland.ac.uk)

take a look at the course finder on the left which uses exactly that, you can even miss spell stuff and it will suggest the right spelling if it exists.

Mike

---

### Post by aszxcv on 2008-12-13
[http://highscalability.com/google-architecture](http://highscalability.com/google-architecture)

---

