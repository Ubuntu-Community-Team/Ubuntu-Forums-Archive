---
title: "Some question about SQL."
date: 2012-04-24
forum: Programming Talk
---

### Post by prismctg on 2012-04-24
Hi, recently I m just interested about learning SQL ... But as usual i have many silly question :o about this ... Is SQL is only for server side programming or It is desktop application friendly ?What is deference between SQL and SQLLITE ?What is prerequisites for leanring SQL ? I just know c and python . And lastly tell me some name of book for learning SQL.  :)

---

### Post by lykeion on 2012-04-24
Try this tutorial, basic but pretty good: [http://www.w3schools.com/sql/default.asp](http://www.w3schools.com/sql/default.asp)

---

### Post by Crossover on 2012-04-24
SQL is a language

SQLlite a database engine

Start with MySQL: [http://dev.mysql.com/doc/](http://dev.mysql.com/doc/)

---

### Post by marin123 on 2012-04-24
Probably you have googled this already, but here it is.

SQL is database server and there is no "programming" in SQL, at least not classic programming like C.

You can send queries to database server (SQL server) and the server returns the data you have asked for. Also you can store new data or update old values.

It is very useful in object-oriented languages like Java or C# where you can have all your data stored when the application is shut down and you can get them all back when you start app again.

---

### Post by imachavel on 2012-04-24
is writing in sql popular now? Seems like css as a back end is much more popular, as well as java. Not a programming expert, but I'd start by installing lamp all together, and getting to know local host in /var/www if I'm not mistaken. Gotten some very very good advice from senior member MG&TL, learn about d.n.s., or more often common used in small lans dynamic host configuration protocol which translates i.p. addresses to url, and I also believe hands out i.p. addresses, but I'm not sure. This will lead you into the world of dedicated ethernet, and into the world of servers and what not what is a server, how does a server give i.p.'s over a network, what is a subnet, what type of OS can be a server, difference between server and file server, etc.

Anyhow if you already are very familiar with all that I won't waste your time, on to business:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

here is what your syntax should look like. Actually for me it's already install so it won't be the same at all, but just an example:

sudo apt-get install tasksel
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tasksel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
danel@danel-Dimension-4700:~$ sudo tasksel install lamp-server
danel@danel-Dimension-4700:~$ apache2 service
Usage: apache2 [-D name] [-d directory] [-f file]
               [-C "directive"] [-c "directive"]
               [-k start|restart|graceful|graceful-stop|stop]
               [-v] [-V] [-h] [-l] [-L] [-t] [-T] [-S] [-X]
Options:
  -D name            : define a name for use in <IfDefine name> directives
  -d directory       : specify an alternate initial ServerRoot
  -f file            : specify an alternate ServerConfigFile
  -C "directive"     : process directive before reading config files
  -c "directive"     : process directive after reading config files
  -e level           : show startup errors of level (see LogLevel)
  -E file            : log startup errors to file
  -v                 : show version number
  -V                 : show compile settings
  -h                 : list available command line options (this page)
  -l                 : list compiled in modules
  -L                 : list available configuration directives
  -t -D DUMP_VHOSTS  : show parsed settings (currently only vhost settings)
  -S                 : a synonym for -t -D DUMP_VHOSTS
  -t -D DUMP_MODULES : show all loaded modules 
  -M                 : a synonym for -t -D DUMP_MODULES
  -t                 : run syntax check for config files
  -T                 : start without DocumentRoot(s) check
  -X                 : debug mode (only one worker, do not detach)


As for the language itself I don't actually know much about it. Good luck.

---

### Post by imachavel on 2012-04-24
> **marin123 said:**
> Probably you have googled this already, but here it is.

SQL is database server and there is no "programming" in SQL, at least not classic programming like C.

You can send queries to database server (SQL server) and the server returns the data you have asked for. Also you can store new data or update old values.

It is very useful in object-oriented languages like Java or C# where you can have all your data stored when the application is shut down and you can get them all back when you start app again.

will never understand why if c c++ and c# and Java is object oriented, why Java needs a virtual machine to run the environment, and yet is supposed to compiled once, and able to use cross platform. So if I wrote a program in Java it could be downloaded from a server I have running to access it, and run on windows or Linux or Mac without having to be recompiled to each kernel? But these days c I don't think is used much to write back end server support programs, most OS have in the i.p. protocol libraries somewhere all the necessary compiled files to support network services. As far as I know, c (and c with classes) will always be the main language for an OS kernel, the gui, everything that accesses any type of base binary. For whatever you would like to support network apps, for codecs, plug ins, and java run time libraries, I believe all the supported running services and interprepeters will be in the form of things such as php, .net library, adobe flash, codecs, and drivers are much lower lower level code.

So here I go again, mashing it all together and generalizing too much. You asked a specific question, sorry to waste your time.

Linux: back end file system, OS kernel
Apache: back end web server
my sql: server data base library? I don't even know exactly
php: interpreter

Sorry if I made a few mistakes, most of my experience is mem testing bsod, and formatting winblows, most file system knowledge I've gotten aside from installing drivers and decoders and plug ins has been from member MG&TL, but hey even god can't assist someone all the time :guitar:

---

### Post by codemaniac on 2012-04-24
> **marin123 said:**
> Probably you have googled this already, but here it is.

SQL is database server and there is no "programming" in SQL, at least not classic programming like C.


SQL is not a database server my dear mate , it is only a language used to query a database server .
On the other hand Sql Server is a database server product .

---

### Post by imachavel on 2012-04-24
so sql would query apache, which is a data base server correct?

---

### Post by wojox on 2012-04-24
Great intro from [SQLzoo]("http://sqlzoo.net/")

---

### Post by codemaniac on 2012-04-24
apache is a web server which host your web applications , every web application needs a backend database server(Oracle/Mysql/DB2) to store information which can be retrieved or used by the web applications .

---

### Post by prismctg on 2012-04-24
Can i use SQL with desktop applications ?

---

### Post by imachavel on 2012-04-24
be specific, which ones? I'd say no, it runs with apache, here is a good abstract, with highest level stuff being on top, lowest level on the bottom:

php
mysql
apache
linux kernel file system OS

so really, what desk top applications would you want to run it with? It's made to work with web server stuff. Get to know ping and the NIC and how all your network protocol is transferred over the OSI, web data base is specifically web data base. Anything not web data base would just be file system data base accessed by host user. Make sense? A web app is a server app, and can be accessed within a LAN, over an internet WAN, and along related concepts

---

### Post by wojox on 2012-04-24
> **prismctg said:**
> Can i use SQL with desktop applications ?

Sure, if you run Firefox you using embedded sqlite.

---

### Post by SeijiSensei on 2012-04-24
KDE uses MySQL as a database backend for its Akonadi service that manages things like calendars.

SQL is simply a standard language that is used to construct database queries.  A simple SQL statement might be something like:

```
select * from users where username='SeijiSensei';
```

That command would look in a table called "users" and find the row(s) where the username column matches 'SeijiSensei'; "select *" tells the database program to return the entire matching record(s).

SQL is useless without a database server like PostgreSQL, MySQL, or Microsoft SQL Server.  Learning SQL in the abstract would be pretty useless. Since you know Python, maybe [this](http://openbookproject.net/py4fun/sql/sql.html) is a good place to start.

---

### Post by oldfred on 2012-04-24
While you can install a full apache server in you desktop to connect to a SQL server, if just starting out and learning, using sqlite is easy. It is not quite as complete, but has most standard SQL features. The connection statements are a bit easier.

[http://docs.python.org/library/sqlite3.html](http://docs.python.org/library/sqlite3.html)

[http://zetcode.com/db/sqlitepythontutorial/](http://zetcode.com/db/sqlitepythontutorial/)

[http://www.halfcooked.com/presentations/osdc2006/python_databases.html](http://www.halfcooked.com/presentations/osdc2006/python_databases.html)

---

### Post by prismctg on 2012-04-24
thnx everybody for loosing ur valueable time wid my post

---

### Post by greenberry on 2012-04-25
SQL is the language to access data in relational database systems.  A good tutorial can be found at [http://www.1keydata.com/sql/sql.html]("http://www.1keydata.com/sql/sql.html").

---

