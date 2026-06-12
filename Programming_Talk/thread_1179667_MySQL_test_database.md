---
title: "MySQL test database"
date: 2009-06-05
forum: Programming Talk
---

### Post by JohnE1 on 2009-06-05
Ubuntu 9.04 Desktop
LAMP Server installed via Synaptic Package Manager's (SPM) Tasksel option

I have LAMP installed and MySQL server loads on boot-up, but when I 'show databases' I don't see the 'test' database. How can I add it? (Yes, I have searched SPM for it.)

This is what I see.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.25 sec)


TIA!  (Thanks in advance!)

JohnE1

---

### Post by unknownPoster on 2009-06-05
did you create the database? if you did not create it, it won't be there...

```


CREATE DATABASE databaseName;


```

This link has been very helpful to me in the past. [http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)

---

### Post by JohnE1 on 2009-06-05
> **unknownPoster said:**
> did you create the database? if you did not create it, it won't be there...

```


CREATE DATABASE databaseName;


```

This link has been very helpful to me in the past. [http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)

No. I was under the impression it came with MySQL.
I feel kinda stupid now. I'll create my own.

Thanks for replying!

JohnE1

---

