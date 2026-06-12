---
title: "MySQL query to return date?"
date: 2009-01-15
forum: Programming Talk
---

### Post by vishzilla on 2009-01-15
I would like to know if its possible to return dates for entries older than a month for example.

---

### Post by cl333r on 2009-01-15
A quick google yields:

[http://www.tizag.com/mysqlTutorial/mysql-date.php](http://www.tizag.com/mysqlTutorial/mysql-date.php)

---

### Post by vishzilla on 2009-01-16
I didn't make myself clear. I have these entries in the tables with timestamps ranging for the last 3 months. How can I return entries older than a month ignoring the recent one month entries. I am using Perl to access the database

---

### Post by sunset_studies on 2009-01-18
please post the 'table create' code so we can see what type of column is being used to store the dates. :)

---

### Post by CodeBird on 2009-01-18
SELECT columns FROM table WHERE date_column < DATE_SUB(now(), INTERVAL 1 MONTH); 

this should be it unless u used a weird type for the date_column

---

