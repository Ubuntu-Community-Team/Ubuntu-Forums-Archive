---
title: "mysql query execution time"
date: 2008-04-11
forum: Programming Talk
---

### Post by krish_kooll on 2008-04-11
i want to know how to obtain the execution time of a mysql query using java programming.
and also how to abort the query if the time exceeds

---

### Post by Zugzwang on 2008-04-11
You don't provide much detail here.

Assuming that you connect using JDBC, you can set a maximum time of a query by calling the setQueryTimeout() function of a Statement object: [http://java.sun.com/j2se/1.5.0/docs/api/java/sql/Statement.html]("http://java.sun.com/j2se/1.5.0/docs/api/java/sql/Statement.html")

Profiling of Queries is not supported by all JDBC drivers but please see chapter 4 of the Connector/J documentation for that: [http://dev.mysql.com/doc/]("http://dev.mysql.com/doc/") (section: Debugging/Profiling)

---

