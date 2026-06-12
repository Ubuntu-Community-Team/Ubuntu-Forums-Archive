---
title: "UTF-8 in MySQL and RAM usage"
date: 2007-10-23
forum: Programming Talk
---

### Post by Henaro on 2007-10-23
Hello everyone~

Not too sure whether or not to put this here or general help, so I apologize if I have made a mistake. 

So anyways, a few quick questions on MySQL.  When I'm setting up a TEXT column I usually let the Collation default to "latin1_swedish_ci".  But I've been wanting to input Russian and Japanese characters into the DB lately.  So far the Japanese characters work, but I was wondering if I should make the column UTF-8.  

Also, something I've just realized.  I've always had an mysql server installed on my desktop.  And I've always used up a lot of RAM (506 MB  on average).  I just assumed it was compiz-fusion, firefox, exaile, screem (while running XFCE4) and went on with my life.  But ever since I did a clean install with out mysql I've seen that number decrease greatly (-100 MB).  And only recently have I reinstalled mysql server that I've seen it jump back up.  Does MySQL really use up that much RAM?  Or am I imagining it?

---

### Post by LaRoza on 2007-10-23
MySQL is a server, and will use RAM. I don't know how much it uses though.

You can use UTF-8 if you want. If you should, I don't know. Sorry.

---

### Post by slavik on 2007-10-24
it might be loading the tables/databases into RAM ...

---

