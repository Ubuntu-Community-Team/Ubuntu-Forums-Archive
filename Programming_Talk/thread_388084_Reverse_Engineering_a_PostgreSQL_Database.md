---
title: "Reverse Engineering a PostgreSQL Database"
date: 2007-03-19
forum: Programming Talk
---

### Post by charlie. on 2007-03-19
Please suggest a tool to reverse engineer a PostgreSQL database into an entity-relationship-diagram (ERD) or equivalent?

Ideally, I'm looking for a simple ERD or UML class diagram in a format that is easy to work with. (i.e. SVG, PDF or any common UML file format)

Yeah, I'll be the first to admit that MS SQL Server's ERD feature rocks, despite the bugs. (Not that a fancy diagram feature is enough to outweigh the benefits PostgreSQL offers over MS SQL.)

Thanks,
Stephen

---

### Post by angelmartinezn on 2007-03-19
Just, the best:  PostreSQL Manager


[http://www.sqlmanager.net/en/products#postgresql](http://www.sqlmanager.net/en/products#postgresql)


Good Luck!

---

### Post by charlie. on 2007-03-19
No points earned for recommending a proprietary software that only supports Windows.

Suggestion *NOT* appreciated.

---

### Post by charlie. on 2007-03-19
If someone can confirm that what I am looking for does not exist in the open source world, I'd appreciate that information. My response would be a proposal for Google's Summer of Code 2007 - with my professional work load, I need a nice 'n easy project to submit.

(I have a student number and I am registered for some modules at a university so, technically, I am elligable for SOC 2007.)

---

### Post by _duncan_ on 2007-03-20
A couple of years ago I used an Eclipse plug-in called "Azzurri Clay Database Modeling" to reverse engineer an existing PostgreSQL 7.4 database. It was able to recreate a rough dataflow diagram. I had to edit the resulting diagram manually coz there were a lot of criss-crossing arrows, but the database components and relationships were picked up correctly. The Eclipse version at the time was 3.0 (not sure about this). That was the first and last time I used the plug-in.

There were a lot of changes to PostgreSQL, Java and Eclipse already since then. Not sure if Azzurri kept up with these developments. Anyway, if you're desperate, here's a link to their website:

[[COLOR="Blue"]Azzurri Website[/COLOR]]("http://www.azzurri.jp/en/software/clay/")

BTW, I did not explore the features of the plug-in fully , so I don't know what format the resulting diagram was stored in.

---

### Post by helmi03 on 2009-07-29
DbVisualizer - [http://minq.se/products/dbvis/download/](http://minq.se/products/dbvis/download/)

---

### Post by Mirge on 2009-07-29
Last response was over 2 years ago, btw...

---

### Post by StunnerAlpha on 2009-07-29
> **Mirge said:**
> Last response was over 2 years ago, btw...
So what? Some guy possibly 4 years from now could have the same issue and find this thread from google. The spreading of knowledge is what we should be encouraging...

---

### Post by JAlexoid on 2009-09-06
> **StunnerAlpha said:**
> So what? Some guy possibly 4 years from now could have the same issue and find this thread from google. The spreading of knowledge is what we should be encouraging...
Exactly how I got here, just now :)

---

### Post by karbonatok on 2011-09-14
> **JAlexoid said:**
> Exactly how I got here, just now :)
so did I:)

---

### Post by slavik on 2011-09-14
Hey you, yes, you, the one in the future. It is probably 2013 now and if you are reading this, then some of human language survived. If this is still a discussion that is needed, open a new thread. I would suggest worrying about repopulating Earth first, though (if that piece of rock is still around).

---

