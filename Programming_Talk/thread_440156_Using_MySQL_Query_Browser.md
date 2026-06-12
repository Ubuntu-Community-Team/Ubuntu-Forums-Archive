---
title: "Using MySQL Query Browser"
date: 2007-05-11
forum: Programming Talk
---

### Post by tc101 on 2007-05-11
I have installed mySQL,  MySQL Query Browser and MySQL Administrator.  

When I go to MySQL Query Browser/ Open Connection Editor it asks for Username, Password and Hostname.  I assume I can use any username and password I want.  What should I put in for hostname?  I just made on up, callinf it "t" and when I tried to open the connection I got this message:

Could not connect to host 't'.
MySQL Error Nr. 2005
Unknown MySQL server host 't' (1)

Also, in the connection editor it asks for schema.  What should I put there?

---

### Post by heimo on 2007-05-11
If you have mysql-server installed on the same computer, use localhost as hostname. Also you need to use username and password for the database - I think it's by default root and password is empy. You don't have to choose schema, I think you can choose it after login.

---

### Post by tc101 on 2007-05-11
Thanks heimo.  I'm in.  It feels so good.

---

### Post by tc101 on 2007-05-11
Under help for MySQL Query Browser, I am able to open the  Quick Start Guide, but when I click on Help/Contents nothing happens.  How do I get that to work?

Is there a good tutorial somewhere on line?

---

### Post by heimo on 2007-05-11
I haven't used it for a very long time, but you can find all kind of documentation for MySQL here:
[http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by tc101 on 2007-05-11
Thanks.  That has everything I need.

---

### Post by tc101 on 2007-05-11
If I want a handy front end for creating tables in mysql, is open office database the easiest thing to use?

If so, I have a question about setting it up to read the mysql db.  You can connect open office db to an existing mysql database using either ODBC or JDBC.  Which is easier?   I tried doing it with JDBC and it said the jdbc drive was not loaded. Where do I get it.

Finally, is it proper forum etiquite to ask a series of related question like this in one topic, which stated off being about Using MySQL Query Browser, or is it better to start a new topic?

---

### Post by heimo on 2007-05-11
> **tc101 said:**
> If I want a handy front end for creating tables in mysql, is open office database the easiest thing to use?
I'd try mysql-admin.

> **tc101 said:**
> 
If so, I have a question about setting it up to read the mysql db.  You can connect open office db to an existing mysql database using either ODBC or JDBC.  Which is easier?   I tried doing it with JDBC and it said the jdbc drive was not loaded. Where do I get it.
I don't know. But you can get one or both of those at [http://www.mysql.com/](http://www.mysql.com/)

> **tc101 said:**
> 
Finally, is it proper forum etiquite to ask a series of related question like this in one topic, which stated off being about Using MySQL Query Browser, or is it better to start a new topic?
I think it's fine to ask a series of related questions as far as not wondering too far from topic and making long threads where information is hard to find for the next person. Generally, I think it's best to keep number of topics low in one thread, so that thread title and content match. But my opinions are not official policy.

---

