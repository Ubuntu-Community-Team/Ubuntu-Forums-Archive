---
title: "New to Linux - Database project on the cards"
date: 2017-05-29
forum: New to Ubuntu
---

### Post by 1e-d on 2017-05-29
Hey everyone, 

Really value forums like this, and have been lurking for a little while. 

I have some very limited experience with Linux having used Ubuntu a tiny bit as a kid, and installing linux mint to get myself out of a windows install disk pickle last week.  

I want to write a database program that performs a few certain (basic maths) HVAC calcs and stores the data for a wide range of circumstances for an engineering application. I have some limited coding experience (fairly comfortable with VB) and am comfortable learning a new language. The Google-fu is strong with this one but I need a push in the right direction (and some opinions). I haven't yet decided on whether I want a web front end or not. 

I wanted to give this project a go in Linux, but want to know what the collective thoughts are about which language to use and which compiler (?) is best. If you had minimal coding experience and wanted to write a database, where would you start?  

Cheers, 
1e-d.

---

### Post by SeijiSensei on 2017-05-29
I prefer PostgreSQL as an SQL server though MySQL is more popular.  I write most applications in PHP which has built-in support for PG (and pretty much every other SQL server on the planet).  For me, a web form would be the easiest solution. A simple app would present an HTML form to the user with the fields to be filled in.  When the information is submitted it would be written to the database, along with the results of the calculations to be performed, and the result displayed to the user as a web page.

Any of the forms used on this site are examples since the vBulletin forum code is written in PHP with a database back-end.

PHP is a scripting language and is not compiled.  That's true for most languages used in these sorts of applications like perl and Python.  

You can install the complete "LAMP stack" of Apache, MySQL and PHP with the command
```
sudo apt-get install lamp-server^
```
See [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by shridhar-kapshikar on 2017-05-30
I too prefer PostgreSQL as an SQL server through MYSQL which is most popular. If you're asking for which language and compiler then the answer is **Python.** Note- the choice of language varies from person to person. 

It is easy to learn and you can achieve most of the stuff with writing a very minimal line of codes in python.Python does support to add/modify/update the database queries.[B] 

See [/B][https://www.tutorialspoint.com/python/python_database_access.htm](https://www.tutorialspoint.com/python/python_database_access.htm)

BR, Shridhar.

---

