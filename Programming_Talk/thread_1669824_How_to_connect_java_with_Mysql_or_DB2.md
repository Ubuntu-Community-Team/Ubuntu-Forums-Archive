---
title: "How to connect java with Mysql or DB2?"
date: 2011-01-18
forum: Programming Talk
---

### Post by scott_tiger on 2011-01-18
[FONT=Arial][SIZE=4]I want to do a project for which i need to establish the connection b/w the frontend (java in my case) and backend ([/SIZE][/FONT][SIZE=4]Mysql or DB2) , but i don't know the procedure??Can anybody help?

Java programs are mostly in GUI(ie i am using swings and awt package) , any code or any IDE that provide direct connection to database without a code by just few clicks of buttons??[/SIZE]

---

### Post by r-senior on 2011-01-18
Have a search for JDBC and DAO. The question comes up quite often - it's just knowing what to search for.

If you have to seamlessly switch between databases, you might also consider the abstract factory pattern or a dependency injection framework like Spring. Spring also has a few JDBC template classes that take a lot of the tedium out of writing DAOs.

As far as a few clicks goes, I think Netbeans allows you to generate (Java Persistence Architecture) JPA classes from database tables. Think of a JPA entity manager as a generic DAO. Expect to need to modify the classes it generates though, which means understanding what they do, which could mean it was quicker to write the DAOs by hand.

---

