---
title: "php/python with MSsql"
date: 2009-10-02
forum: Programming Talk
---

### Post by jonabyte on 2009-10-02
Hello,
I am looking to develop a web front for an MSsql database server i work with and would like to develop it with php, python or another scripting language hosted on a Linux server.
Has anyone had experience with this kind of thing, I just want to display the tables and maybe have the ability to sort the data for end users.

Any suggestions are welcome!

---

### Post by CyberJack on 2009-10-02
Have you looked at the Mssql part of the php website?
[http://us3.php.net/manual/en/book.mssql.php](http://us3.php.net/manual/en/book.mssql.php)
Here you can find all available functions (including examples).

A full connect and query example can be found on the mssql_query function page.

I have no experience with python so I can't help you with that.

---

### Post by unutbu on 2009-10-02
Python resources to interact with Microsoft SQL Server are listed here: [http://wiki.python.org/moin/SQL](http://wiki.python.org/moin/SQL) Server.

---

### Post by chrisjsmith on 2009-10-02
From experience, PHP's SQL Server module is much more reliable than the python native SQL Server drivers.  

DO NOT USE ODBC - It's hell.

---

### Post by jonabyte on 2009-10-04
thanks for the replies, I was hoping for a tutorial, but I will read through the manuals.

---

