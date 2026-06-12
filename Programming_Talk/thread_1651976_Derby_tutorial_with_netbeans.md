---
title: "Derby tutorial with netbeans"
date: 2010-12-24
forum: Programming Talk
---

### Post by shababhsiddique on 2010-12-24
Hello there.

I am a newbie java programmer. I am trying to use the derby database offered with netbeans. i have create a database but how do i do the following

1) access database elements from a cli java application.
 a) how to create rows from the application and do queries.
2) access multiple tables. i.e relational database. (preview a query in a table instead of a single table.)



i came from c++ and it seems like the world is 10 times the size here!.

if you have a simple derby tutorial explaining all tasks it would be awesome.

thanks in advance.

---

### Post by r-senior on 2010-12-24
Java applications access relational databases like Derby, MySQL or Oracle using a common API called JDBC, so you need to look for [JDBC tutorials]("http://download.oracle.com/javase/tutorial/jdbc/index.html"). Accessing any database through JDBC is basically the same, although the URL you use for connections differs.

The main interfaces/classes in JDBC that you will be dealing with are Connection and Statement, with Resultset if you are querying.

Rather than starting with Derby, I'd suggest setting up MySQL so that you can use the client tools (MySQL Query Browser for example) to examine what you are doing and fiddle with test data.

---

### Post by shababhsiddique on 2010-12-28
> **r-senior said:**
> Java applications access relational databases like Derby, MySQL or Oracle using a common API called JDBC, so you need to look for [JDBC tutorials]("http://download.oracle.com/javase/tutorial/jdbc/index.html"). Accessing any database through JDBC is basically the same, although the URL you use for connections differs.

The main interfaces/classes in JDBC that you will be dealing with are Connection and Statement, with Resultset if you are querying.

Rather than starting with Derby, I'd suggest setting up MySQL so that you can use the client tools (MySQL Query Browser for example) to examine what you are doing and fiddle with test data.

Thanks ... i almost forgot about posting here. I got a nice solution on the web about jdbc. And finally was able to use it with my program.

---

