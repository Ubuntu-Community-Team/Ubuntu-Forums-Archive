---
title: "How to export an sql file to excel/calc"
date: 2011-03-12
forum: Programming Talk
---

### Post by skytreader on 2011-03-12
I'm making a db-driven web app and I would like to give my users the option to download their db into excel/calc.

So...is there a (hopefully free) lib/api to easily export to excel/calc? I'm using MySQL.

In case there isn't one, I've managed to export it into a CSV file* (using SELECT INTO OUTFILE). However, I still need to give my users this file. I'm using XAMPP and I've figured that the files save to xampp/mysql/data/dbname. How do I let them download this?

(*which, in turn can be exported to calc, at least [and excel, I've heard]. That will have to do until I have more time to write a script that gives them an ods or xls instantly.)

---

