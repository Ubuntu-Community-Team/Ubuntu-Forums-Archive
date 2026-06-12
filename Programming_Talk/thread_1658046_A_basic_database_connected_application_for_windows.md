---
title: "A basic database connected application for windows"
date: 2011-01-02
forum: Programming Talk
---

### Post by kanishkdudeja on 2011-01-02
I need to develop a basic application which connects to a database..

which can be run on windows..

what should i use ?

java ? 

or mayb the gtk toolkit?

---

### Post by idi0tf0wl on 2011-01-02
Are you trying to develop a GUI application that can work with databases and run on Windows? I'd say Java is your best bet, but folks around here know I'm biased. The next thing I'll recommend is Ruby, but its viability is going to depend on your planned consumer base. GTK isn't something I'd look into if you're looking for a one-size-fits-all codebase. What's the haps?

---

### Post by juancarlospaco on 2011-01-02
Python

---

### Post by kanishkdudeja on 2011-01-02
yeah..

its a gui application..

the main problem is it needs to run on several pcs..

it will be transported from one place to another via a usb drive..

the main problem is if the database gets updated at one workstation it should get stored in the pendrive..

so that it can be used on another workstation..

can i sumhow embed the database in the jar file..

so that the user only needs to store the jar file in the pen drive..

and can use that jar file in different places ?

---

### Post by juancarlospaco on 2011-01-02
SQLite

---

### Post by kanishkdudeja on 2011-01-02
ok so can i embed sql lite into a java application?

---

### Post by smuthavarapu on 2011-01-02
Do you really need to use Database ? 
Did you consider File Management, as it can be stored in USB and you can port with your pendrive from PC to PC.
You can use Java to read and write from Files.
I mean to say is, instead Database, use Files to write and Read and you can reuse, if your data is less.

---

### Post by kanishkdudeja on 2011-01-02
well i do need to use database..

as i need to perform join operations on several tables..

and i need to perform several complex queries as well..

---

### Post by Newbie2910 on 2011-01-02
Definitely use a real database such as SQLite or MySQL.  Don't waste your time with junk like MS-Access.  It is not intended for storage of critical data.

I would recommend doing your coding in .Net which runs on both Windows and Linux (Mono).  I have done this extensively and am very happy with this method.  One code base, two platforms.

---

### Post by kanishkdudeja on 2011-01-02
can you telme how to embed mysql or sql lite in java ?

any tutorials ? 

or any links can u give ?

---

### Post by Barrucadu on 2011-01-02
Why do you need to embed the database? Can't the program just work with the database file on the pen drive?

---

### Post by kanishkdudeja on 2011-01-02
i dont know. Can it work? Will be great if it can.

---

### Post by MadCow108 on 2011-01-02
how about reading a bit about sqlite3 yourself
[http://www.sqlite.org/](http://www.sqlite.org/)
there are also java wrappers:
[http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers](http://www.sqlite.org/cvstrac/wiki?p=SqliteWrappers)

mysql or postgresql are probably not very well suited for embedded kind of applications.

maybe you can also do with a non-relational db like couchdb mongodb or redis?

---

### Post by smuthavarapu on 2011-01-02
Did you hear about Java DB, which can be embedded in Application itself, Unfortunately i have not worked on it, but may be worth trying.
[http://www.oracle.com/technetwork/java/javadb/overview/index.html](http://www.oracle.com/technetwork/java/javadb/overview/index.html)

---

### Post by kanishkdudeja on 2011-01-02
ok..thanks guys..:)

---

