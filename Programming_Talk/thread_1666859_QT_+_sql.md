---
title: "QT + sql"
date: 2011-01-14
forum: Programming Talk
---

### Post by Bencz on 2011-01-14
Hi!!!!

I'm wondering how I can work with QT + SQL.

To make more clear my doubts, I'll try to explain :)

My doubt is, how can I do for the program to read a specific thing in a database, and this information go to read a label.

Eg->

DB:
Name | Age |  e-mail  |
 Ale | 100 |   null   |
 Zeh |  23 |  zeh@a.a |

Window:

Search: Ale

Name: Ale
Age: 100
E-Mail: null

Thanks for the help.

---

### Post by WthIteh on 2011-01-14
> **Bencz said:**
> Hi!!!!

I'm wondering how I can work with QT + SQL.

To make more clear my doubts, I'll try to explain :)

My doubt is, how can I do for the program to read a specific thing in a database, and this information go to read a label.

Eg->

DB:
Name | Age |  e-mail  |
 Ale | 100 |   null   |
 Zeh |  23 |  zeh@a.a |

Window:

Search: Ale

Name: Ale
Age: 100
E-Mail: null

Thanks for the help.
[http://doc.qt.nokia.com/latest/qt4-sql.html](http://doc.qt.nokia.com/latest/qt4-sql.html)

---

### Post by Vaphell on 2011-01-14
[http://doc.qt.nokia.com/4.7/qsqlquery.html](http://doc.qt.nokia.com/4.7/qsqlquery.html)

```
QSqlQuery query("SELECT country FROM artist");
     while (query.next()) {
         QString country = query.value(0).toString();
         doSomething(country);
     }
```

query is constructed from a string, so you can put your parameter there (remember to sanitize input [http://xkcd.com/327/](http://xkcd.com/327/)), iteration through the results gives you access to data and you can do whatever you want with it.

edit: follow WthIteh's link to get the broader picture

---

