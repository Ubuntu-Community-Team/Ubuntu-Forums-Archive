---
title: "[mySQL] Where to I start? Which packages do I need?"
date: 2008-11-11
forum: Programming Talk
---

### Post by NovaAesa on 2008-11-11
Hi all,

I'm looking to learn a bit of mySQL as I've just gotten a summer job at a software engineering firm and one of the technologies they use is SQL. Even though I don't start for another week or so, I want to get a head start with learning so that when I start there they see that I have had the initiative to learn outside the job and that I am motivated and enthusiastic. There is a possibility of part time work after the summer if my skills are good enough and I work well with the time, so I really want to get the best chance of continuing on.

Anyway, I've been looking around the web, and I can't find many Ubuntu-specific instructions about how to go about installing mySQL. I did a bit of a search in synaptic as well, but there are tons of packages that have stuff to do with SQL so I have no idea which ones to use. If anyone could point out which packages I need for local development that would be excellent. (I don't really want to set up a server or anything like that quite yet)

Also, if anyone has come across good tutorials or anything like that those would also be welcome (I've googled and they all the ones I found seem pretty mediocre and assume prior relational database knowledge, of which I have none).

Cheers,
-NovaAesa

---

### Post by drubin on 2008-11-11
Take a look at my sig for installing php/apache there is mysql specific information there as well.

---

### Post by dwhitney67 on 2008-11-11
I believe this should do the trick to get mySQL installed:
```
sudo apt-get install mysql-server
```

You did not specify which language you will be using at your new job.  If it is C++, then I recommend that you consider installing the mySQL C++ library:
```
sudo apt-get install libmysql++-dev
```

---

### Post by pmasiar on 2008-11-11
You have two separate problems: learning to **administer** MySQL, and learn to use SQL as data access/manipulation language.

I assume that you will not be DB admin (summer intern during Xmass! nice), so you need to learn SQL. Wikipedia is good start, and check also wikiversity. If you don't want to dive into DB admin tasks, don't: use SQLite, which has in 99% same SQL interface. There is no single SQL, but many dialects, programmers usually try to ignore differences unless they need the performance.

You need to learn language bindings for SQL which company uses, there are zillions of them, you better ask what they use.

Get any books from your local public library, and buy "SQL pocket guide" from O'Reilly - for $10 it is excellent value.

---

### Post by NovaAesa on 2008-11-11
Thanks for the replies everyone.

> **dwhitney67 said:**
> You did not specify which language you will be using at your new job.

They are using Java, so I'm thinking that there should be a bindings in the Java library? There appears to be java.sql but nothing specific to mySQL.
 	
[QUOTE=pmasiar]
I assume that you will not be DB admin (summer intern during Xmass! nice), so you need to learn SQL. Wikipedia is good start, and check also wikiversity. If you don't want to dive into DB admin tasks, don't: use SQLite, which has in 99% same SQL interface.[/quote]
Yes that's right, I'm pretty sure that they wouldn't be wanting to do any admin stuff. I'll check out SQLite and see how that goes as well.

[QUOTE=pmaisiar]Get any books from your local public library, and buy "SQL pocket guide" from O'Reilly - for $10 it is excellent value.[/QUOTE]
I just got a copy of "Teach Yourself MySQL in 21 Days", it's a bit old but I didn't cost me a cent, so hopefully it will be informative enough to get me on the right track with actually learning all the commands and what-not.

---

### Post by Kilon on 2008-11-11
hey there I am very new with MySQL as well, I have bought this book which is very informative.


[IMG]http://ecx.images-amazon.com/images/I/414YP5A16AL._BO2,204,203,200_PIsitb-sticker-arrow-click,TopRight,35,-76_AA240_SH20_OU02_.jpg[/IMG]

[http://www.amazon.co.uk/Beginning-My...182495&sr=1-16](http://www.amazon.co.uk/Beginning-My...182495&sr=1-16)

I will be following your thread with a lot of attention , it is a subject that interests me a lot

---

### Post by achelis on 2008-11-11
There are different ways to access databases from Java.

Starting out I'd probably focus on learning the basics of MySQL, rather than worrying about how to write Java programs accessing the database.

This link might be of help with the installation:
[http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html]("http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html")

I used JPOX which is an OR-mapper for Java. It has been replaced by DataNucleus, here is a tutorial (haven't tried the tutorial myself):
[http://www.datanucleus.org/products/accessplatform/guides/jdo/tutorial.html]("http://www.datanucleus.org/products/accessplatform/guides/jdo/tutorial.html")

Another popular OR-mapper for Java is Hibernate:
[http://www.hibernate.org/152.html]("http://www.hibernate.org/152.html")

Briefly and not very precisely an OR-mapper is a 'tool' which helps you map objects from your Java-model to tables in your database (i.e. a mysql database).

Another way is using JDBC. This is lets you get down and dirty with the actual sql in your Java code.
[http://java.sun.com/docs/books/tutorial/jdbc/index.html]("http://java.sun.com/docs/books/tutorial/jdbc/index.html")

I think JDBC is the best place to start if you want to do some Java<->MySQL stuff. There is not as much happening under the hood, and OR-Mappers can be tricky to set up.

Good luck with the job :)

---

