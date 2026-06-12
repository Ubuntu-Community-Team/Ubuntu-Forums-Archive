---
title: "SIMPLE mysql c++"
date: 2009-03-22
forum: Programming Talk
---

### Post by smarmo on 2009-03-22
I've been trying to find a decent tutorial on how to access a mysql database from a c++ program. I keep coming across mysql++, the 'mysql c++ api' but I also keep reading that it's very complicated. All I want to be able to do is connect to the mysql server, run queries, store the result (if any) in variables or an array, and then close the connection. Can I do this by simply using the mysql c api within a c++ program? If so, can anyone provide examples or point me to a tutorial? Or would that be even more complicated than just using mysql++? If so, does anyone know of a good uncomplicated tutorial on mysql++? Thanks in advance.

---

### Post by cabalas on 2009-03-22
Have you seen this tutorial for mysql++? [http://tangentsoft.net/mysql++/doc/html/userman/tutorial.html](http://tangentsoft.net/mysql++/doc/html/userman/tutorial.html)

---

### Post by dwhitney67 on 2009-03-22
> **smarmo said:**
> ...All I want to be able to do is connect to the mysql server, run queries, store the result (if any) in variables or an array, and then close the connection...

:o  Wow, I did not realize one could do additional things with a database other than what you stated above!

A good place to get started with MySql++ is here:  [http://tangentsoft.net/mysql++/doc/html/refman/index.html](http://tangentsoft.net/mysql++/doc/html/refman/index.html)

If you have any specific questions after you have attempted to code an application, please post it here.

Good luck!

---

### Post by smarmo on 2009-03-22
> **dwhitney67 said:**
> :o  Wow, I did not realize one could do additional things with a database other than what you stated above!

Sarcasm is not a very polite way to respond to someone asking for your help.

---

### Post by dwhitney67 on 2009-03-22
> **smarmo said:**
> Sarcasm is not a very polite way to respond to someone asking for your help.
What gave you the impression I was attempting to be polite?  Next time I will just give the "deer in the headlights" look.  That way you will not get offended.

---

### Post by smarmo on 2009-03-22
> **cabalas said:**
> Have you seen this tutorial for mysql++? [http://tangentsoft.net/mysql++/doc/html/userman/tutorial.html](http://tangentsoft.net/mysql++/doc/html/userman/tutorial.html)

I have read that tutorial and I think I get everything now.

Now I just need to know what options to use when compiling with g++. Also, in the section at the bottom of that page, "Concurrent Queries on a Connection"... Is that saying that I can't run a query, do stuff with the results, then run another query with the same connection? Seems like a very annoying limitation. Or have I misunderstood?

---

### Post by smarmo on 2009-03-22
> **dwhitney67 said:**
> What gave you the impression I was attempting to be polite?  Next time I will just give the "deer in the headlights" look.  That way you will not get offended.

If you don't have anything helpful to say, then please leave me alone.

---

### Post by dwhitney67 on 2009-03-22
> **smarmo said:**
> If you don't have anything helpful to say, then please leave me alone.
I did provide some helpful information (a link to the MySql++ docs).

If you do not want my help, then fine.  Go cry to mommy and I will leave you alone.

---

### Post by smarmo on 2009-03-22
> **dwhitney67 said:**
> [QUOTE=smarmo;6940418]...All I want to be able to do is connect to the mysql server, run queries, store the result (if any) in variables or an array, and then close the connection.:o  Wow, I did not realize one could do additional things with a database other than what you stated above![/QUOTE]

What I was referring to, by the way, is when APIs try to include all sorts of built-in functions for manipulating the database when running a query could do the same thing. All I want is the basics of how to talk to the database from my program.

---

### Post by dwhitney67 on 2009-03-22
I've included a tar-ball with a collection of wrapper-classes around the MySql++ API.

Take a look at the DatabaseManager class to get an idea of how to setup the connection and to issue queries.

The DatabaseResult class is used to peer into the MySql++ query results.

---

### Post by smarmo on 2009-03-22
I think I have found everything that I needed. [This tutorial]("http://blog.code-head.com/a-tiny-mysql-tutorial-c-and-mysql-example") helped me more than the other one. It's simpler and easier to understand.

---

