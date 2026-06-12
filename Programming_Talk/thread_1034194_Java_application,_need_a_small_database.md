---
title: "Java application, need a small database"
date: 2009-01-08
forum: Programming Talk
---

### Post by Shonof on 2009-01-08
Hey,

I have a java app that need a databse. i know whow to use mysql and excel, but i don't  want the user of this app to install these. on his/her personal computer. We already tried to do it with Text-I.O. but that didn't work very well.

I don know how other programms solve these problems. I hope someone can help me.

---

### Post by myrtle1908 on 2009-01-08
Sounds like you want an embedded database for your Java Application.  Take a look at Derby ... [http://db.apache.org/derby/](http://db.apache.org/derby/), specifically embedded deployment.

_Embedded Deployment:_ *"Refers to Derby being started by a simple single-user Java application. With this option Derby runs in the same Java virtual machine (JVM) as the application. Derby can be almost invisible to the end user because it is started and stopped by the application and often requires no administration."*

---

### Post by jespdj on 2009-01-08
Note that Sun provides [JavaDB](http://developers.sun.com/javadb/), which is essentially Apache Derby, which is included with the Sun Java JRE.

Another one you could use is [HSQLDB](http://hsqldb.org/).

---

### Post by stevescripts on 2009-01-08
Along with those previously mentioned, you might want to take a look at
SQLite - [http://www.sqlite.org/](http://www.sqlite.org/)

---

### Post by drubin on 2009-01-08
> **jespdj said:**
> Note that Sun provides [JavaDB](http://developers.sun.com/javadb/), which is essentially Apache Derby, which is included with the Sun Java JRE.

Another one you could use is [HSQLDB](http://hsqldb.org/).

+1 for HSQLDB i have used to for a relatively large number of records/load and it handles pretty well. 

It is easy to use. simple backup procedures. (almost a single file). light weight and is pure java so doesn't require the user to install any 3rd party apps/libs you can just bundle it with your application.

---

### Post by SupaSonic on 2009-01-09
> **stevescripts said:**
> Along with those previously mentioned, you might want to take a look at
SQLite - [http://www.sqlite.org/](http://www.sqlite.org/)

SQLite is good.
FireBird is also pretty good.
As is HSQLDB.

---

### Post by curvedinfinity on 2009-01-09
SQLite is excellent and has great APIs in all of the languages I've used it with.

---

### Post by drubin on 2009-01-09
> **curvedinfinity said:**
> SQLite is excellent and has great APIs in all of the languages I've used it with.

Have you ever worked with it with Java? Vs HSQldb? 

> **SupaSonic said:**
> SQLite is good.
FireBird is also pretty good.
As is HSQLDB.

Out of all the db's I have worked with I have found FireBird to be the the most shocking to work with. I am not sure if it is the API's the front end applications but I just hated working with it.

---

### Post by txcrackers on 2009-01-11
If you want a full-fledged SQL database, HSQLDB is probably your best bet. Very light, but good enough on the bells and whistles to be a very serious embedded solution.

If you're just going for more simple object-type storage, I'd strongly suggest Oracle's Berkeley DB for Java. It has several, very easy to use approaches, doesn't have quite the overhead of full-blown SQL, and you can use annotations on your objects to directly store and retrieve them.

Both of these will scale well, but you should check their capacity specs to ensure that your application is compatible.

---

### Post by Shin_Gouki2501 on 2009-01-11
ignoring your problems i would suggest ( without any details , did you give any?) you try using XML.
Its quite easy to map from Java objets to xml and the other way arround.

---

### Post by drubin on 2009-01-11
> **Shin_Gouki2501 said:**
> ignoring your problems i would suggest ( without any details , did you give any?) you try using XML.
Its quite easy to map from Java objets to xml and the other way arround.

Horrid solution.. why not just sterilize the whole data list into a output stream and read it all back at once.

DB's are optimized for searching/sort/indexing records bassed on single columns/attributes.

---

### Post by drubin on 2009-01-12
> **Shin_Gouki2501 said:**
> ignoring your problems i would suggest ( without any details , did you give any?) you try using XML.
Its quite easy to map from Java objets to xml and the other way arround.

/me shivers at that thought....

xml based DB's :(  xml is nice for configs (any others any one can think of)

---

