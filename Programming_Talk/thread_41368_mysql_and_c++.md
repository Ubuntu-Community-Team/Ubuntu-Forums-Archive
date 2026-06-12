---
title: "mysql and c++"
date: 2005-06-13
forum: Programming Talk
---

### Post by vintem on 2005-06-13
Hello everyone,

if I'm to acces a mysql database from within a C++ program, I should #include something. What is this something and how can I get this file (or these files) installed?
Is it possible via Synaptic Package Manager?
Thank you very much for your replies.

---

### Post by Sniffer on 2005-06-13
Explain better!!!!!!!!!!!!!!!!!!!

Do you mean Mysql and MySQLCC (Control Center)?? You can check the Ubuntu Guide to know how to install it by Synaptic...

Are you tryng to develop some access program in C++??

---

### Post by vintem on 2005-06-13
Sorry for not being clear. 
I want to write a program in C++ that is able to query a table, to add records to this table, etc. The table is in a MySql database.
I know there are some header-files to #include, to get the program working with a mysql database. But I don't know exactly what the header-files are and how I should install them with Synaptic Package Manager.
MysqlCC has nothing to do with it, I suppose, as it is the control center for Mysql.

I hope this is a better explanation of my question. Thanks for replying.

---

### Post by LordHunter317 on 2005-06-13
[QUOTE=vintem]Sorry for not being clear. 
I want to write a program in C++ that is able to query a table, to add records to this table, etc. The table is in a MySql database.
I know there are some header-files to #include, to get the program working with a mysql database. But I don't know exactly what the header-files are and how I should install them with Synaptic Package Manager.
MysqlCC has nothing to do with it, I suppose, as it is the control center for Mysql.

I hope this is a better explanation of my question. Thanks for replying.[/QUOTE]
 You need to install libmysqlclient-dev, which will give you the C programming interface.

You may also want to look at [http://mysqlcppapi.sourceforge.net/](http://mysqlcppapi.sourceforge.net/).

Don't use libsqlplus1, as it's unmaintained and not standard C++.

---

### Post by vintem on 2005-06-14
This works. Thanks for your help. I really appreciate it!!!
The only thing I would like to add (for eventual other beginners) is that, when you compile, you should use -I -L and -lmysqlclient options. You also must 

#include<mysql.h>   



Then,  to compile:

g++ -c -I/usr/include/mysql testdb.c
g++ -o testdb testdb.o -L/usr/lib/mysql -lmysqlclient

This worked on my system. The paths may differ of course.

---

### Post by Rabbitbunny on 2009-02-25
This works perfectly under 8.04 Hardy and 8.10 Interpid although the proper package is libmysqlclient15-dev for both.

---

