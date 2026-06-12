---
title: "Database programming - what alternatives?"
date: 2009-02-26
forum: Programming Talk
---

### Post by Crabro on 2009-02-26
I used to be a dBase then Foxpro programmer (with some Visual Foxpro experience) in an earlier life. My home accounts program was written, oh, 16 years ago in FoxPro. It suits me - I tailored it to what I need, minimum keystrokes, and so on.

Recently I discovered Ubuntu, and I now am a total convert, except for one thing - you have guessed - my home accounts program. It works fine under Wine, except when I try to print then it cannot see my network attached printer (hp business inkjet 1100). I have to then switch to XP just for the printing - ouch, that hurts!

I was thinking this should be reported as a bug to the Wine team, but decided that I am probably the only person in the whole world that wants to print using FoxPro 2.6 under Wine to a NAP...

I have recently been looking into writing another home accounts program. I have looked at OpenOffice.org Base and played around with the macros. However I have not got much further than 'Hello World'. I cannot discover simple things such as how to alter the properties of objects or manipulate table data.  I have a feeling this may not be possible, or the way to go.

I then read about GAMBAS, but it seems that does not yet hook into data very well. I guess I would have to run a mySQL server, and I am feel this is going too far for a home accounts program.

Has anyone any suggestions to what I could look at please? I know there are account programs in the repositories, but I want to write something! ;)

Dick

---

### Post by ajackson on 2009-02-26
For standalone databases you can use SQLite.

As for languages most will have drivers for SQLite (or MySQL), Java and Python definitely do (I've used both with a SQLite DB), I'd imagine Mono (C#) does as well.

Having never seen FoxPro syntax I can't tell you which language is most similar but speaking from my current experience Python is very easy to pick up, you can use Glade for GUI design (if you don't want to use tkinter or pyGtk that is).

This forum has a fair few Python, Java, C# and C (I'll add C++ in with C) developers so getting help for one of those languages shouldn't be a problem.

---

### Post by stevescripts on 2009-02-26
+1 re SQLITE

---

### Post by dgoosens on 2009-02-26
... and you can not even print out a PDF ?

otherwise, I agree on SqLite...
however, I personally prefer MySQL as it is a real database...

---

### Post by cb951303 on 2009-02-26
I think SQLite + Mono would be a good choice.

EDIT: Or something like openoffice.org base for gnome [http://www.gnome-db.org/](http://www.gnome-db.org/)

---

### Post by ssam on 2009-02-26
maybe [Glom]("http://www.glom.org/").

---

### Post by s1ightcrazed on 2009-02-26
I would also recommend sqlite - python has good bindings for it. 
No need for a 'real' database unless you expect this little accounting program to have multiple connections and need concurrent write access from multiple sources. If not then sqlite will work fine.

---

### Post by Crabro on 2009-02-26
> **s1ightcrazed said:**
> No need for a 'real' database unless you expect this little accounting program to have multiple connections and need concurrent write access from multiple sources.

Well, there are two uf us; myself AND my wife...

I am going to have a good look at all these proposals. Providing I can keep my development and database files on my server, then I am happy to adopt whichever gives me the least learning curve. I have played with Python, and it probably would not take too long to get to grips with it. I have also programmed MS Access databases using VBA and from what I have seen GAMBAS is not that too dissimilar in principal. Best of all, the GAMBAS language construct looks very similar to Foxpro.

So, can I assume from the fact that no-one has commented otherwise, there is not much opportunity for using macros within OpenOffice.org?

Dick

---

### Post by soltanis on 2009-02-26
SQLite will handle fine even with two separate users of the same database; it implements write locks (writes aren't concurrent) but you can have multiple accesses at the same time (concurrent read is supported).

No, macros are basically a dead end. They're pointless anywhere when there are tons of good languages (like Python) specifically suited to doing what you describe. C#/Java/C++/C are also usable, but I wouldn't use them here since they add extra complication (especially C; super assembler is not what you want for a personal database program). Python will get the job done, fast, with minimal setup and extra code. Perl has equal (or greater) power, if you're into that, for doing the same.

---

### Post by Can+~ on 2009-02-26
I also agree with the sqlite proposal, specially with the sqlite3 bindings for Python. Sqlite is specially suited for small applications where 1 or a small group of people share a db, so it will be fine.

[Documentation]("http://docs.python.org/library/sqlite3.html")

tiny example:

[PHP]#!/usr/bin/python

import sqlite3

conn = sqlite3.connect("/tmp/example.db")
curs = conn.cursor()

curs.execute("""CREATE TABLE IF NOT EXISTS pet_store (name TEXT, owner TEXT)""")
curs.execute("""INSERT INTO pet_store VALUES ('Fluffy', 'Robert')""")

conn.commit()
curs.close()[/PHP]

Retrieving:

[PHP]import sqlite3

conn = sqlite3.connect("/tmp/example.db")
curs = conn.cursor()

results = curs.execute("""SELECT * FROM pet_store""")

for result in results:
	print result

curs.close()[/PHP]

---

### Post by kalaharix on 2009-02-28
Gambas rocks. I don't do sprites, graphics, musack, CGI, video (sad really) but can drool over a couple of megabytes of raw data. Gambas suits my needs just dandy. I probably would not use it for software intended for distribution but for own use there is nothing like it. The IDE is quite simply the best available in Linux (and written in Gambas).

SQLite is great though in essence only does text fields. I don't have a problem storing accounting numbers as text and in fact used to do this in VB6. Setting up MySQL is not difficult and it is obviously more powerful. SQLite is single user.

The one thing you have to accept with Gambas (as with much of open software) is that the documentation is brief and pitched at the competent user. That can make it a slow learn for the likes of me. But worth the effort.

rgds

---

