---
title: "Database programming - what alternatives? (2012 version)"
date: 2012-02-14
forum: Programming Talk
---

### Post by JaM0N on 2012-02-14
Hello everybody, i'm looking for some way to organice my lab data (works and profiles) that's not the oocalc way (have this now, got to copy 'n paste all the time, get messed with filters, etc.).

So looking for some database managing tool i've found oobase and Glom, but both similary complicated as oocalc ¬¬. Now i know there is nothing pre-built to do what i need, so i must do it myself, seen [_this thread_]("http://ubuntuforums.org/showthread.php?t=1081302"), now it's clear.

What language do you recomend? Phyton or Gambas? I can handle the programing since I know some phyton, c, and other basics, but don't have any idea on how to do an interface (GUI?)...

PD: sorry for my dusted english...

---

### Post by lykwydchykyn on 2012-02-14
There are plenty of choices for making GUIs.  I personally choose QT most of the time, which even has its own database abstraction layer and some other advanced tools to make going from GUI->DB as slick as possible.

QT works best with C++ but I use it with python myself since I'm too lazy to manage pointers and whatnot.

Other people will suggest Tkinter, GTK, and wxWidgets.  They all have their advantages, you just have to try a few and see what commends itself to your thinking.

I know zip about gambas, so I can't comment on it.

---

### Post by SeijiSensei on 2012-02-14
One of the few reasons I keep a copy of Windows around is to use Microsoft Access.  If you save your data tables in .xls, you can easily import them to Access.  Then you can use its GUI to design the queries you need.  I can write complex SQL queries from the command line when necessary, but I often find Access the easiest method to extract what I need from a database.

I actually use Access as a front-end to PostgreSQL.  You can install the PG ODBC driver in Windows and connect to the remote database over the network.  In my case the data need to be available to web applications written in PHP as well as via Access to a desktop machine.

---

### Post by CryptAck on 2012-02-15
> **SeijiSensei said:**
> One of the few reasons I keep a copy of Windows around is to use Microsoft Access.  If you save your data tables in .xls, you can easily import them to Access.  Then you can use its GUI to design the queries you need.  I can write complex SQL queries from the command line when necessary, but I often find Access the easiest method to extract what I need from a database.

How can you stand Access? One of the worst software applications from Microsoft, IMO. :(

To Microsoft's credit, I really do like Excel. 

@OP: My recommendation would depend on the complexity of your data needs. If your needs are for storing a reasonably small amount of data in a tabular structure, I would recommend either a script or a Python program (possibly with a GUI) that allows you to directly edit the fields on a flat file. If your data needs are greater, than a DBMS (postgreSQL, MySQL, SQLLite, etc) could be used to manage the data, and a admin interface could be used in lieu of creating something completely new (phpMyAdmin for example).

---

### Post by muteXe on 2012-02-16
I have a lot of time for Access.

---

### Post by qeemat on 2012-02-17
Yes you can you this database tool "Install Firebird Database on Ubuntu"
and you can start from python.

---

### Post by alexfish on 2012-02-22
Can have a look at PureBasic , although not free software it will allow freedom to design you own data base
layouts , it can use SQL and sqlite , one advatage is the easy for manipulating data , Take notice of what has been mentioned about Firefox extention RE sqlite, from Firefox it is easy to set up a database and test sql commands. then the data base can also be accessed by purebasic IE in a similar  achieved in Access, The main advantage of this route the program is standalone once it is compiled , there is also a demo version, free to download.


alexfish

---

