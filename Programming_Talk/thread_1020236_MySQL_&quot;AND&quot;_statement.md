---
title: "MySQL &quot;AND&quot; statement"
date: 2008-12-23
forum: Programming Talk
---

### Post by Dr Small on 2008-12-23
I can't think of what this statement is called to find and documentation on it, to learn how to use it. So I am asking if anyone knows the proper term for the MySQL "AND" statement.

Basically, I need to learn how to use it properly, but I can't find any documentation on it, since the word is "and"...

Any clues would be appreciated.

---

### Post by bluestriker on 2008-12-23
Well, if you want a MySQL query to meet more than one condition, you would use AND:

```
$q = mysql_query("SELECT `name` FROM `population` WHERE `location` = '".$location."' AND `language` = '".$language."'");
```

---

