---
title: "MySQL Locate database file"
date: 2014-04-26
forum: Programming Talk
---

### Post by cp43tcW on 2014-04-26
Hello, can someone please explain how I can find where, in what directory, on my computer is a database I create in mySQL stored? I am using Ubuntu 12.04.2 LTS. I just installed sql server and client. I want to open my bash terminal navigate to where the databases are located and open a database and tables in a text editor such as nano. When I go into SQL and write ```
mysql>show databases;
``` where are those databases located?

---

### Post by SeijiSensei on 2014-04-26
The databases are stored in /var/lib/mysql, but they are in a binary format.  You cannot examine them with a text editor.

What you can do is create a plain-text "dump" of the databases using mysqldump like this:
```
mysqldump -u root -p --all-databases > mydump.sql
```
You can then examine the output file mydump.sql with a text editor.

---

