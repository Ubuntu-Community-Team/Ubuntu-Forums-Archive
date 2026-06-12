---
title: "MySQL Issues"
date: 2011-08-20
forum: Programming Talk
---

### Post by KdotJ on 2011-08-20
Hey all, I know this seems like a broad question but I just wanted to know if anyone had an ides on an answer. I wrote a **very** simple script to run to create a table in mySQL database.

This is the contents of the script, named: CreateLines.sql
```
CREATE TABLE  Lines (
  id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(20) NOT NULL,
  colour VARCHAR(12) NOT NULL
  );
```

To use it, I cd'd to the directory in the terminal, then fired up mysql. I used the following statement to run it:

```
mysql> source CreateLines.sql
```

But it throws an error straight away saying:

```
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'Lines 

CREATE TABLE  Lines (
  id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  na' at line 1

```

This should be pretty straight forward :/
Any ideas?
Thanks in advance

---

### Post by Bachstelze on 2011-08-20
'Lines" is a keyword, so you need to enclose it in backticks to use it literally:

```
CREATE TABLE `Lines` (
  id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(20) NOT NULL,
  colour VARCHAR(12) NOT NULL
  );
```

---

### Post by KdotJ on 2011-08-20
Thanks! I literally just realised this haha. I'm assuming it's not a good idea to use reserved words as table names anyhow?

---

### Post by dazman19 on 2011-08-22
yeh some clown at work make a table called lock. we had the same issues. All the SQL we generate we actually generate it with the ` character around the table name.. in this case `lock` that is how all your naming should be sent to the database. Do the same thing for database names aswell.

---

