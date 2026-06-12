---
title: "Sharing violations on variables?"
date: 2013-03-20
forum: Programming Talk
---

### Post by KJC1995 on 2013-03-20
I was wondering if someone can explain sharing violations on variables, web pages and database tables on a shared database.  What does this mean and how to avoid it.  I've been programming for 13 years and I haven't heard of this before.

---

### Post by ofnuts on 2013-03-20
A sharing violation happens when two pieces of code try to both gain access to the same 'object' at the same time while only one can because at least one of them has requested exclusive access (for files, for instance, you don't want two processes to write to the same file at the same time). This is a specific error because the same access tried at another time can succeed (for files, this isn't the same thing as "file not found" or "no access rights"). Note that either competitor can get the error, the one requesting exclusive access as well as the one allowing share. The error just says that their mutual requests are incompatible. So you can have:


[LIST]
[*]A makes an access request allowing share while B makes an exclusive request 
[*]A wins, B gets a sharing violation error 
[*]If C comes along and also makes a request allowing share it will succeed since it is compatible with A sharing access. 
[/LIST]
 
or 

[LIST]
[*]A makes a access request allowing share while B makes an exclusive request 
[*]B wins, A gets a sharing violation error 
[*]If C comes along and also makes a request allowing share it will get a sharing violation error since it is incompatible with the exclusive access by B 
[/LIST]
  
Some languages support locks on variables update, and DB systems normally support some form of exclusive access to update tables or lines in tables.

---

### Post by slickymaster on 2013-03-21
On what databases are concerned, I would advise you to read these articles:

[Database Locking: What it is, Why it Matters and What to do About it]("http://www.methodsandtools.com/archive/archive.php?id=83")
[Data Concurrency and Consistency]("http://docs.oracle.com/cd/E14072_01/server.112/e10713/consist.htm")

---

