---
title: "Workbench Tutorial"
date: 2010-04-28
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-04-28
Hello there,

I would like to learn SQL (on the long term i'd like to create databases for online game projects). I'm new to this.
I downloaded Workbench, and i also found a tutorial PDF, but it's for the Windows version and it looks different.

Question 1: is there a good free tutorial available for SQL (frontend)?
Question 2: do i need to have a server connection? I basically want to work locally for as long as i am learning of course.

Thanks!
B.

---

### Post by jesuisbenjamin on 2010-04-29
hello there,

since i got no answer i found some more information myself on the internet. My questions are partially answered and more problems popped up in the meantime.

Concerning the question of tutorial, i am starting to assume i cannot go further with my current tutorial because i cannot connect to a server.

Now from [this documentation]("http://www.linux.com/learn/tutorials/293621:get-to-know-mysql-workbench") i found out that i can used my localhost as a server.
Accordingly to the above introduction i installed mysql-client and mysql-server.

Following step 1 however, connecting to localhost fail with the following message: 
```
Test connect failed
Couldn't load library libmysqlclient_r.so: libmysqlclient_r.so: cannot open shared object file: No such file or directory
```
...which is a bit confusing.

As to my first question of a tutorial, this short introduction together with the PDF i downloaded earlier show a ["Workbench Main Page"]("http://www.linux.com/images/stories/workbench_main.png") which i do not have on my version 5.1.18.
How come?

So basically--as you may have guessed--i don't understand the first thing about SQL and workbench. But since this is all new to me and since there is no good overview of how SQL works (client-server relationship) and what it can do and how other languages manipulate the data on SQL -- i may as well completely be missing the point.

Anyway i started, it's the most important part perhaps... 

Thanks for your support.

---

### Post by jesuisbenjamin on 2010-04-30
Ok, the more i investigate in this the more i am confused.

I downloaded Workbench, MysqlAdministrator, Emma etc. I could connect with the second but cannot do much, not even save a table. There is no documentation online that matches my version of Workbench or that explains how to connect to localhost and create a table.

In short, the whole MySql frontend concept seems very much esoteric :-k. Is there anyone to tell me how to start working with MySQL in a gui?

Thanks.
B.

---

### Post by soltanis on 2010-04-30
Well basically SQL is a relational database schema (there are many implementations and not all of them are compatible). You do need a SQL server if you plan on making or manipulating any databases.

It's really used more for storing customizable information for programs (especially web programs) as opposed to just being a database that you fiddle around with. Everyone I know of who used it inevitably used it from within the context of a program -- not for manipulating data as a stand-alone.

That being said you can use it for that. But I know nothing about the frontends you're talking about.

---

