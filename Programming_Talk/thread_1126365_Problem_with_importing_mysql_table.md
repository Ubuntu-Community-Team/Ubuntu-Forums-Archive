---
title: "Problem with importing mysql table"
date: 2009-04-15
forum: Programming Talk
---

### Post by dispyfan on 2009-04-15
Hi, I'm trying to import the wikipedia database in my Mysql installation for a project. I have this strange error:
```
ERROR 1064 (42000) at line 4: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-------------------------------------------------------


DROP TABLE IF EXIS' at line 1

```

Here's the head of the file:

```


-- MySQL dump 8.23
--
-- Host: 10.0.0.240    Database: enwiki
---------------------------------------------------------
-- Server version	4.0.40-wikimedia-log

--
-- Table structure for table `pagelinks`
--

DROP TABLE IF EXISTS `pagelinks`;

```

What is the problem?
Nobody on the internet has this problem, so I don't really know what I can do to fix it.

Thanks in advance!
Cristian

---

### Post by unutbu on 2009-04-15
On line 4, put a space after the first two hypens.

See [http://dev.mysql.com/doc/refman/5.1/en/comments.html](http://dev.mysql.com/doc/refman/5.1/en/comments.html)

---

