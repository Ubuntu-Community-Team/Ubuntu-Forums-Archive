---
title: "SQL statement for export to XLS"
date: 2011-08-10
forum: Programming Talk
---

### Post by lordadi on 2011-08-10
Hi,

I have a client who wants a daily xls file of a DB from my MySQL server. I could do this manually through phpMyAdmin but would rather not.

I was trying to find the SQL statement that can be used to export the DB to an xls file. I didn't get anywhere so, I turn to you for help. How can I do this? I would like to script it and have it run on a cronjob.

Thanks!

---

### Post by Bachstelze on 2011-08-10
Judging by the time it takes PhpMyAdmin to generate a XLS file compared to a SQL file, I would hazard a guess that it uses some PHP to transform the data in XLS format, and not a simple SQL statement. You could look at the PhpMyAdmin code to see how it does it, or google. It gives me this [http://www.hotscripts.com/forums/php/20549-export-mysql-excel.html](http://www.hotscripts.com/forums/php/20549-export-mysql-excel.html)

---

