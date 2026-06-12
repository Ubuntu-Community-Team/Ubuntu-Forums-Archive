---
title: "mySQL will only let me use backticks (not single or double quotes)"
date: 2010-10-16
forum: Programming Talk
---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-10-16
What the hell is going on here?

```
SELECT * FROM "table";
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '"table"' at line 1

 SELECT * FROM 'table';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''table'' at line 1

SELECT * FROM `table`;
(table prints normally here)

12 rows in set (0.00 sec)


```The error happens both in the mysql client, phpmyadmin, and all my php scripts. How do I make it accept single and double quotes?

Phpmyadmin has this to say about the mySQL installation

```
Server: Localhost via UNIX socket
Server version: 5.1.50
Protocol version: 10
User: root@localhost
MySQL charset:                    UTF-8 Unicode            (utf8)
```

---

### Post by Some Penguin on 2010-10-16
...why are you using quotes at all?  Normally, it's

```

SELECT blah FROM table_name

```

with no quotes until the WHERE clauses.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-10-16
Because there's a space in the table.

---

### Post by Some Penguin on 2010-10-16
Short answer:
[Method and why.]("http://www.pythian.com/news/13811/mysql-and-quoting/")

Better answer:
Rename the table to have a normal name that doesn't require MySQL-specific workarounds.

---

