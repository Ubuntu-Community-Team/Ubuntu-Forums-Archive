---
title: "Beginning learning MySQL- need help creating local file"
date: 2010-08-23
forum: Programming Talk
---

### Post by rdbowers on 2010-08-23
I am trying to learn mySQL, using mySQL Administrator.  I have multiple hard drives on my computer and would like to create a mySQL database in one of the folders (SQL) which is in the root of one of the drives.

I have some experience with Access, and have programmed with C, Basic, and Fortran (years ago).  If I can find out how to create a database and then start working with it, I will learn a lot faster than following the database design of someone (which I would have no use for).  Also, none mentioned how to create a database file in a specific location, which is what I need to do (so I can move it/copy it to other locations).

I've spent the last few hours Googling and reading, and found nothing that makes sense.  I'm fairly new to Linux, although I've been around computers (and programming and software) since 1974.  Is there anyone who is familiar with mySQL Administrator that could help me start working with it... so I can learn it on my own?  Also, is there a SIMPLE online book/manual that would help me get started- one that I could download?

Again, I just need to figure out how to create a database file in a specific directory on a specific drive.  Once I can do that, I can start "playing" with creating and building databases, and learn what I need to know.

I don't have the money to buy a book (unemployed and no unemployment), and I've already spent hours following links and reading without learning anything useful - so PLEASE, some direct answers and not just links to hours upon hours worth of useless blog entries????  (That's what I got with the last question I asked on another blog.)

---

### Post by Bachstelze on 2010-08-23
Creating a mysql database in another location than the default is far from trivial, and generally not recommended.  If you need to transfer your databases to another system, just make a dump and restore them on your other system with that.

---

### Post by rdbowers on 2010-08-23
"Dump and restore"???  

Where would the default location be anyway?   Can I copy it from there to the other drive and then access it?

---

### Post by Bachstelze on 2010-08-23
> **rdbowers said:**
> "Dump and restore"???

Any decent database management frontend will let you make a backup of your databases.  How exactly you would do is dependent on which one you use

> Where would the default location be anyway?

/var/lib/mysql

> Can I copy it from there to the other drive and then access it?

You can try.  It may or may not work, I don't think it's a supported way of making a backup of your databases.

---

### Post by Hellkeepa on 2010-08-27
HELLo!

I'd recommend that you read through the following guide, as using Access is a *far* cry from using a real database engine. (Even if some people would not call MySQL a real DB engine, ignore these [for now].)

[http://forge.mysql.com/wiki/MySQL_User_Guide](http://forge.mysql.com/wiki/MySQL_User_Guide)

Database files for such a system is *not* meant to be moved around, copied or anything. Ideally, they wouldn't even be stored on a file system. So, hands off, and just use the built-in methods for doing this.
On MySQL it's "CREATE DATABASE <name>" inside the MySQL client to create, and "mysqldump -u <user> -p <database> > dump.sql" to back up. To restore a backup, simply use "SOURCE <file>" from inside the MySQL client.

Happy codin'!

---

### Post by rdbowers on 2010-08-27
OK, some questions, and I need some advice.

I need to build databases away from the site- some go onto workstations, and some may- MAY go onto a server.  Access won't work because it locks people into Microsoft and there are problems there, I've worked with Approach (same problem- only worse), and I've been warned that OpenOffice Base becomes quite slow when things get big (some of the databases will have several tens of thousands of objects in them- including pictures, data, you name it).  These databases will have possibly multiple pictures, descriptive information (three or four columns), and technical data which will probably be in some form of array- possibly using a subform.  I'd say that there will be around 30 columns per row, and anywhere from a couple of thousand rows to several tens of thousands.

If I can't build SQL databases and put them into different environments (including ones with Windows, others with Linux, and maybe even Mac), what would be the solution?  (I also cannot go to the site to build these databases... and much of it needs to be done at home because of health issues.)

Some of those databases would also have to be able to be accessed by multiple users at the same time, others would have copies on different workstations and used as references.

Note that I am unemployed (and no income of any sort) and this project will provide employment... and I'm not at liberty to give specifics on it because of the organization it will be done through (and which I'm a part of)... so I don't have funds for expensive software.  That's why I looked as SQL, because it seemed to meet all of my needs, except now it looks like it's not as flexible as I thought it was.

---

### Post by Hellkeepa on 2010-09-01
HELLo!

You can do it that way, but then you'd have to implement the MySQL server code into your project. The easier way would be to have a server somewhere, and have your application connect to it over the network/internet.
Trying to use a RMDBs as you'd use a MS Access database file is not going to work, as they are meant for two completely different use-scenarios.

Happy codin'!

---

### Post by rdbowers on 2010-09-02
SIGH.  It sounds like SQL is not the answer to our problem... and I don't know what is.

---

### Post by Krupski on 2010-09-02
> **rdbowers said:**
> Again, I just need to figure out how to create a database file in a specific directory on a specific drive.

I see nobody has given you a decent answer yet.

OK, if you're using Ubuntu (or I suspect any other Linux) the DEFAULT location for the mysql database directory is "/var/lib/mysql".

If you want the directory to be different, FIRST, stop the mysql server:

```
service mysql stop
```

Then, edit the "/etc/mysql/my.cnf" file. In that file find the section called "Basic Settings". Then, edit the line "datadir     = /var/lib/mysql" to whatever path you wish. It's located at *approximately* line 46.

Next, you ALSO have to update APPARMOR with the new directory location. Edit the file "/etc/apparmor.d/usr.sbin.mysqld".

Look for these two lines:

```

/var/lib/mysql/ r,
/var/lib/mysql/** rwk,

```

...and edit them accordingly.

Then, reload APPARMOR to update the info:

```
service apparmor restart
```

Now, let's **assume** you relocated your database to "/home/rdbowers/mysql". Also assume that "/home/rdbowers" is the directory and you want the database TO BE in that directory but it's not there yet, obviously.

Copy the old database to it's new location:

```

sudo cp -pr /var/lib/mysql /home/rdbowers

```

Now, turn mysql back on:

```
service mysql start
```

It should start up and give you a message like this:

```
mysql start/running, process 6728
```

(note the process number will be different).

Lastly, if you want to create a new database in the relocated mysql directory, use the "mysql" command like this:

```

sudo mysql -uroot -pyour_password mysql

```

You should see:

```

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7
Server version: 5.1.41-3ubuntu12.6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

```

At the mysql prompt, type the following command:

```

CREATE database database_name;

```

Where "database_name" is the name you want for the database.

It should complete successfully and give you a message about rows created (I don't recall exactly what it says).

Lastly, to be sure it worked, type:

```

SHOW databases;

```

You should see two databases... "mysql" and "database_name" (whatever name you used).

Lastly, exit the mysql terminal by typing "quit".

Hope this helps.....

-- Roger

---

### Post by Krupski on 2010-09-02
> **rdbowers said:**
> "Dump and restore"???  

Where would the default location be anyway?   Can I copy it from there to the other drive and then access it?

You can "dump" the contents of the mysql database into one huge file and you can restore the database FROM that huge file as well. To dump the database:

```

sudo mysqldump -uroot -pyour_password database_name > dumpfile

```

To restore a database FROM a dump file:

```

sudo mysql -uroot -pyour_password database_name < dumpfile

```

BTW, a "dumpfile" is an ascii text file that can be viewed and edited... but manual editing is not a good idea unless you REALLY know what you're doing... as a bad edit can corrupt the database if you reload an incorrectly edited dump.

A dumpfile looks like this (obviously this is not the whole file!):

```

-- MySQL dump 10.13  Distrib 5.1.41, for debian-linux-gnu (x86_64)
--
-- Host: localhost    Database: mysql
-- ------------------------------------------------------
-- Server version   5.1.41-3ubuntu12.6

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `columns_priv`
--

DROP TABLE IF EXISTS `columns_priv`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `columns_priv` (
  `Host` char(60) COLLATE utf8_bin NOT NULL DEFAULT '',
  `Db` char(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `User` char(16) COLLATE utf8_bin NOT NULL DEFAULT '',
  `Table_name` char(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `Column_name` char(64) COLLATE utf8_bin NOT NULL DEFAULT '',
  `Timestamp` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  `Column_priv` set('Select','Insert','Update','References') CHARACTER SET utf8 NOT NULL DEFAULT '',

```

Good luck!

-- Roger

---

### Post by rdbowers on 2010-09-02
Roger-

THANK YOU! THANK YOU!! THANK YOU!!!  You've been a huge help!

That's the sort of thing I needed to find out right away (even though I've barely started to learn SQL), so now the projects can be started (I learn best by doing- but my own projects).

---

### Post by Krupski on 2010-09-02
> **rdbowers said:**
> Roger-

THANK YOU! THANK YOU!! THANK YOU!!!  You've been a huge help!

That's the sort of thing I needed to find out right away (even though I've barely started to learn SQL), so now the projects can be started (I learn best by doing- but my own projects).

Glad to be of help. Anything else I can do for you... let me know.

-- Roger

---

### Post by GenBattle on 2010-09-02
> **rdbowers said:**
> SIGH.  It sounds like SQL is not the answer to our problem... and I don't know what is.

SQL is the Language used to query the database, it doesn't refer to the actual DBMS itself.

For your needs it sounds like you actually need multiple types of database with programs to port data between them. I would go with a mySQL database for the relatively non-portable parts of the system, stuff that is sitting on servers, and a SQLlite database for the more portable programs (with some sort of program to sit on the server and export entries from the server to a SQLlite DB maybe?). As other people have said, you will loose speed, but it will give you the best shot at portability without the slowness of something like openoffice.org base.

Without knowing much about the actual project, it sounds like a definite challenge. With portability and ease of use comes great slowness. I would reccomend you pick up a higher level programming language if you haven't already and use that rather than C or something harder. That said, you probably don't have the time to learn a new programming language on top of all of the DB stuff.

---

### Post by Some Penguin on 2010-09-03
[http://nosql.mypopescu.com/post/1016320617/mongodb-is-web-scale]("http://nosql.mypopescu.com/post/1016320617/mongodb-is-web-scale")

More seriously, I do have a question -- you insist on not renting server space, but you also insist on having a database which can be simultaneously used by multiple users.  Where, then, is the database to be hosted -- on a machine provided by the client?

---

### Post by dwhitney67 on 2010-09-03
> **rdbowers said:**
> SIGH.  It sounds like SQL is not the answer to our problem... and I don't know what is.

Why did you feel that your project required a database?  Could the information be stored in a mere flat-file?  If you need to cross-reference data, then a database might be desirable.

If you are unwilling to provide *somewhat* specific project requirements, then the onus will be on you to determine what your needs may be.  Reading one two posts on this forum to derive a solution is pointless, and could lead to a project catastrophe.  If you do not have any system design experience, then perhaps you are already half-way there.

P.S.  MySQL allows for the administrator to configure where the database file(s) will reside.  The default is /var/lib/mysql.  Look at /etc/mysql/my.cnf for where to configure the MySQL settings.  The default storage area is referenced via the "datadir" option.

---

### Post by Colin@oxford on 2010-10-27
I need to do exactly this - i.e. put the MySQL data somewhere safe so that it is accessible between different boots or OS versions.

I followed Roger's advice and all was going OK until I tried to restart the MySQL server.  Using:
```

sudo service mysql start

```
the process just hung - no message about a new process and I was unable to access the server:
```

 Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

```
Any suggestions on what I might have done wrong?

---

### Post by SeijiSensei on 2010-10-27
Let's back up a bit.

There are two parts to MySQL, a server "daemon" and a set of client programs.  You need to start by installing the server:

sudo apt-get install mysql-server

It should start running once installed.

Then you need to create a database.  For that, you use the "mysql" client program which you probably already have installed.  For now, you can use the "root" account though once you get to know what you're doing you should create a separate account for production purposes.  Type "mysql -u root" at the dollar-sign prompt, and you'll be able to talk to the server portion and run commands.

Follow the steps in [this tutorial](http://dev.mysql.com/doc/refman/5.0/en/tutorial.html) to see how to create and manage databases, run queries, etc.

Now a bigger comment.  It sounds to me like you want to build a MySQL "back-end" to support a variety of desktop applications.  If you're comfortable building applications in Access, you should read up on ODBC.  If you install the [MySQL ODBC driver in Windows]("http://dev.mysql.com/downloads/connector/odbc/5.1.html"), an Access application can use a MySQL database over the network.  

As for backup and portability, the "mysqldump" command creates a plain-text backup of your entire database as a series of SQL commands.  You can recreate the database anew by reading it into the mysql client.  The binary version of the database stored in /var/lib/mysql isn't really portable, but files created with mysqldump definitely are.

---

### Post by memilanuk on 2010-10-27
Something that may be of interest/use fo the OP...

sqlzoo.net

Provides some decent beginning tutorial/training on SQL commands and syntax.

---

### Post by snakerdlk on 2010-10-27
A lot of information which apparently doesn't help so much since rdbowers is new to mysql and doesn't or didn't understand the concept of a mysql database.

There is no reason to create a database file in a different location since mysql runs a server-client relationship.

The server administrates the databases(wherever they might be) and when you use them, you connect to the server, normally on the same machine you're project is at, and request actions of the server.

This connection is normally made through a socket file, or port.

MysqlAdministrator is a very good tool in managing databases(each project should have its own database and mysql access) and is available to most of operating systems. My latest attempts at using it on OSX where a little frustrating because of the instabiliy so I'm using Mysql Workbench, which is a bit less intuitive but better.
It's important to remember that the default mysql configuration only allowes access locally, from the same host.

You can also connect directly to the server from commandline to interact with it using the mysql command(mysql-client).

It may be wise to choose a language that has integrated or at least good support to mysql database access(like PHP for example)

Hope this cleared some doubts...

---

