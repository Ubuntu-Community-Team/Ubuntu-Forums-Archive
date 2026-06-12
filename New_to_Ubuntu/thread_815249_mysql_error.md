---
title: "mysql error"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by rajaram_s on 2008-06-01
I finally recovered my root password and am logging into mysql using the command

mysql -u root -p

and enter the password when prompted.

it logs in, as usual and whatever command I type, be it create, insert, delete or select it shows the error:

ERROR 1046 (3D000): No database selected

What could be the problem?

---

### Post by Monicker on 2008-06-01
You must tell mysql what database you wish to work with.

For example;

```
mysql> use mysql;
mysql> use test;
mysql> use mynewdatabase;
```

Once you have selected a database to use, then you can use your sql statements for that particular database.

---

### Post by rajaram_s on 2008-06-01
Thank you so much....... it worked.... It all arose because of my bits and pieces of knowledge of sql....
but what are databases?
can I create any table in any database? sorry if am askin silly stuff.... just give me some beginners switching guide from sql to mysql please...

---

### Post by Monicker on 2008-06-01
Databases contain one or more tables which are used to organize the information.

[http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/]("http://www.devshed.com/c/a/MySQL/Beginning-MySQL-Tutorial/")

I would also recommend that you install the gui tools for working with mysql.

mysql administrator
mysql query browser

---

### Post by rajaram_s on 2008-06-01
Thank you for the link..... I wanna try it the command line way only.... and I am sure I cab do it,,,,

---

