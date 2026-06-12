---
title: "Sql"
date: 2007-10-28
forum: Programming Talk
---

### Post by Kadrus on 2007-10-28
Can someone help me run SQL on Ubuntu?

---

### Post by LaRoza on 2007-10-28
SQL is a language for working with Databases. Do you want a MySQL server? 

```

sudo aptitude install mysql-server

```

Do you want a LAMPP?

```

sudo tasksel

```

Or you can try SQLite, for a database without a server.

---

### Post by Kadrus on 2007-10-29
> **LaRoza said:**
> SQL is a language for working with Databases. Do you want a MySQL server? 

```

sudo aptitude install mysql-server

```

Do you want a LAMPP?

```

sudo tasksel

```

Or you can try SQLite, for a database without a server.


LaRoza..it isn't working..each time I try to install something it gives me a dpkg error..could you please help?

---

### Post by LaRoza on 2007-10-29
> **Kadrus said:**
> LaRoza..it isn't working..each time I try to install something it gives me a dpkg error..could you please help?

Post the error message.

---

### Post by dataw0lf on 2007-10-29
Post the dpkg error, then.

---

### Post by Kadrus on 2007-10-29
> **LaRoza said:**
> Post the error message.

Writing extended state information... Done
Setting up phpbb2-conf-mysql (2.0.21-6) ...
You need to have mysql-server installed if you want the MySQL
        database to be hosted locally. Aborting.
Postinstallation of phpbb2-conf-mysql failed. Run
`dpkg --configure -a' to retry
dpkg: error processing phpbb2-conf-mysql (--configure):
 subprocess post-installation script returned error exit status 1
Setting up phpgroupware (0.9.16.011-3) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-addressbook:
 phpgroupware-addressbook depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-addressbook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-bookmarks:
 phpgroupware-bookmarks depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-bookmarks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-calendar:
 phpgroupware-calendar depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-calendar (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-chat:
 phpgroupware-chat depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-chat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-comic:
 phpgroupware-comic depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-comic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-developer-tools:
 phpgroupware-developer-tools depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-developer-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-dj:
 phpgroupware-dj depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-dj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-eldaptir:
 phpgroupware-eldaptir depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-eldaptir (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-email:
 phpgroupware-email depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-email (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-etemplate:
 phpgroupware-etemplate depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-etemplate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-felamimail:
 phpgroupware-felamimail depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-felamimail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-filemanager:
 phpgroupware-filemanager depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-filemanager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-folders:
 phpgroupware-folders depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-folders (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-ftp:
 phpgroupware-ftp depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-ftp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-fudforum:
 phpgroupware-fudforum depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-fudforum (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-headlines:
 phpgroupware-headlines depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-headlines (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-hr:
 phpgroupware-hr depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-hr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-notes:
 phpgroupware-notes depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-notes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-phonelog:
 phpgroupware-phonelog depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-phonelog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-infolog:
 phpgroupware-infolog depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
 phpgroupware-infolog depends on phpgroupware-addressbook; however:
  Package phpgroupware-addressbook is not configured yet.
 phpgroupware-infolog depends on phpgroupware-notes; however:
  Package phpgroupware-notes is not configured yet.
 phpgroupware-infolog depends on phpgroupware-phonelog; however:
  Package phpgroupware-phonelog is not configured yet.
dpkg: error processing phpgroupware-infolog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-manual:
 phpgroupware-manual depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-manual (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-messenger:
 phpgroupware-messenger depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-messenger (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phpbb2-conf-mysql
 phpgroupware
 phpgroupware-addressbook
 phpgroupware-bookmarks
 phpgroupware-calendar
 phpgroupware-chat
 phpgroupware-comic
 phpgroupware-developer-tools
 phpgroupware-dj
 phpgroupware-eldaptir
 phpgroupware-email
 phpgroupware-etemplate
 phpgroupware-felamimail
 phpgroupware-filemanager
 phpgroupware-folders
 phpgroupware-ftp
 phpgroupware-fudforum
 phpgroupware-headlines
 phpgroupware-hr
 phpgroupware-notes
 phpgroupware-phonelog
 phpgroupware-infolog
 phpgroupware-manual
 phpgroupware-messenger
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up phpgroupware (0.9.16.011-3) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
psql: could not connect to server: No such file or directory
        Is the server running locally and accepting
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-comic:
 phpgroupware-comic depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-comic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-dj:
 phpgroupware-dj depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-dj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-chat:
 phpgroupware-chat depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-chat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-bookmarks:
 phpgroupware-bookmarks depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-bookmarks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-eldaptir:
 phpgroupware-eldaptir depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-eldaptir (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-filemanager:
 phpgroupware-filemanager depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-filemanager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-manual:
 phpgroupware-manual depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-manual (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-etemplate:
 phpgroupware-etemplate depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-etemplate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-infolog:
 phpgroupware-infolog depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-infolog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-developer-tools:
 phpgroupware-developer-tools depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-developer-tools (--configure):
 dependency problems - leaving unconfigured
Setting up phpbb2-conf-mysql (2.0.21-6) ...
You need to have mysql-server installed if you want the MySQL
        database to be hosted locally. Aborting.
Postinstallation of phpbb2-conf-mysql failed. Run
`dpkg --configure -a' to retry
dpkg: error processing phpbb2-conf-mysql (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-fudforum:
 phpgroupware-fudforum depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-fudforum (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-phonelog:
 phpgroupware-phonelog depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-phonelog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-messenger:
 phpgroupware-messenger depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-messenger (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-felamimail:
 phpgroupware-felamimail depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-felamimail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-addressbook:
 phpgroupware-addressbook depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-addressbook (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-folders:
 phpgroupware-folders depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-folders (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-hr:
 phpgroupware-hr depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-hr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-headlines:
 phpgroupware-headlines depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-headlines (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-notes:
 phpgroupware-notes depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-notes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-email:
 phpgroupware-email depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-email (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-calendar:
 phpgroupware-calendar depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-calendar (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpgroupware-ftp:
 phpgroupware-ftp depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-ftp (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phpgroupware
 phpgroupware-comic
 phpgroupware-dj
 phpgroupware-chat
 phpgroupware-bookmarks
 phpgroupware-eldaptir
 phpgroupware-filemanager
 phpgroupware-manual
 phpgroupware-etemplate
 phpgroupware-infolog
 phpgroupware-developer-tools
 phpbb2-conf-mysql
 phpgroupware-fudforum
 phpgroupware-phonelog
 phpgroupware-messenger
 phpgroupware-felamimail
 phpgroupware-addressbook
 phpgroupware-folders
 phpgroupware-hr
 phpgroupware-headlines
 phpgroupware-notes
 phpgroupware-email
 phpgroupware-calendar
 phpgroupware-ftp

---

### Post by dataw0lf on 2007-10-29
apt-get install mysql-server

That's all you need for an SQL service.

---

### Post by LaRoza on 2007-10-29
Run:

```

dpkg --configure -a

```

and it looked like you were not installing mysql-server, run: ```
sudo aptitude install mysql-server
```

---

### Post by Kadrus on 2007-10-29
> **LaRoza said:**
> Run:

```

dpkg --configure -a

```

and it looked like you were not installing mysql-server, run: ```
sudo aptitude install mysql-server
```
Still isn't working!:mad:

---

### Post by Kadrus on 2007-10-29
> **LaRoza said:**
> Run:

```

dpkg --configure -a

```

and it looked like you were not installing mysql-server, run: ```
sudo aptitude install mysql-server
```
euuh..mm..so there is no solution..

---

### Post by pmasiar on 2007-10-29
Do you need real full-features SQL server, or just plain SQL-accessible data storage for a single user (like in a web application) is enought? Because SQLite is just a simple to use bunch of libraries, you don't incurr overhead of administering full-blown server.

---

### Post by Kadrus on 2007-10-29
> **pmasiar said:**
> Do you need real full-features SQL server, or just plain SQL-accessible data storage for a single user (like in a web application) is enought? Because SQLite is just a simple to use bunch of libraries, you don't incurr overhead of administering full-blown server.
I need SQL..can you help?

---

### Post by Kadrus on 2007-10-29
So...no one can help?:sad::-s

---

### Post by DuneSoldier on 2007-10-29
> **Kadrus said:**
> Still isn't working!:mad:

Which command isn't working? What do you need a SQL Database for?

---

### Post by Siph0n on 2007-10-29
You keep saying that you need SQL, but all SQL is, is a language...

---

### Post by Kadrus on 2007-10-29
> **Siph0n said:**
> You keep saying that you need SQL, but all SQL is, is a language...
I know that it is a language..but you need something to make it run!
DUUH!!

---

### Post by Kadrus on 2007-10-29
> **DuneSoldier said:**
> Which command isn't working? What do you need a SQL Database for?

this command 
sudo aptitude install mysql-server

---

### Post by DuneSoldier on 2007-10-29
what does it give you for output?

---

### Post by Kadrus on 2007-10-29
> **DuneSoldier said:**
> what does it give you for output?

Nothing...!!!

---

### Post by pmasiar on 2007-10-29
> **Kadrus said:**
> I know that it is a language..but you need something to make it run!
DUUH!!

As I said, looks like beginner and could use simple way to do it. So I recommend installing SQLite and not MySQL. Of course up to you what is best for you.

---

### Post by Kadrus on 2007-10-29
> **pmasiar said:**
> As I said, looks like beginner and could use simple way to do it. So I recommend installing SQLite and not MySQL. Of course up to you what is best for you.

Alright..how do I install SQLite?

---

### Post by DuneSoldier on 2007-10-29
> **Kadrus said:**
> Nothing...!!!

Does it return you to a command line? Does it hang? I need a little more to go on.

---

### Post by Kadrus on 2007-10-29
> **DuneSoldier said:**
> Does it return you to a command line? Does it hang? I need a little more to go on.

When I open it with Firefox it tells me "You have chose to open exam.sql...which is a :SQL code...and i press ok..it opens text editor.."
!!

---

### Post by DuneSoldier on 2007-10-29
> **Kadrus said:**
> When I open it with Firefox it tells me "You have chose to open exam.sql...which is a :SQL code...and i press ok..it opens text editor.."
!!

Firefox doesn't run SQL code. You're going to need something like mysql-query-browser to run it on the database.

---

### Post by Kadrus on 2007-10-29
> **DuneSoldier said:**
> Firefox doesn't run SQL code. You're going to need something like mysql-query-browser to run it on the database.

Does it work on Safari?

---

### Post by Siph0n on 2007-10-29
Safari the web browser? I doubt it :)

---

### Post by Kadrus on 2007-10-29
> **Siph0n said:**
> Safari the web browser? I doubt it :)

Anyway Safari doesn't work on Ubuntu

---

### Post by DuneSoldier on 2007-10-29
> **Kadrus said:**
> Does it work on Safari?

You are going to need an application that can run SQL Scripts against the mysql server. You can do that from the command line or with a gui like mysql-query-browser. SQL is a language for retrieving and storing information in databases.

---

### Post by pmasiar on 2007-10-29
... or just a language with SQLite bindings, like Python/pysqlite.

Then you can avoid the pain running MySQL server.

---

### Post by Kadrus on 2007-10-29
> **DuneSoldier said:**
> You are going to need an application that can run SQL Scripts against the mysql server. You can do that from the command line or with a gui like mysql-query-browser. SQL is a language for retrieving and storing information in databases.

I know what SQL is for..I know the language..I  need to run it on Ubuntu..i used to do it on Windows..and NO...don't tell me switch back!

---

### Post by DuneSoldier on 2007-10-29
> **Kadrus said:**
> I know what SQL is for..I know the language..I  need to run it on Ubuntu..i used to do it on Windows..and NO...don't tell me switch back!

Well I'd run:
```

sudo apt-get install mysql-query-browser

```
then
```

sudo apt-get install mysql-admin

```
if you want to work with MySQL.

After that use mysql-query-browser to connect to the database to run scripts or queries.

Good luck

---

### Post by LaRoza on 2007-10-29
> **Kadrus said:**
> I know what SQL is for..I know the language..I  need to run it on Ubuntu..i used to do it on Windows..and NO...don't tell me switch back!

You make it sound like you need an interpreter.

What do you need it for? and what does this command give you:

```

mysql -uroot -p

```

---

### Post by ahvargas on 2007-10-30
you can install postgresql too :
sudo apt-get install postgresql-8.2 pgadmin3
then run pgadmin3 to try some queries

---

### Post by Kadrus on 2007-10-30
> **LaRoza said:**
> You make it sound like you need an interpreter.

What do you need it for? and what does this command give you:

```

mysql -uroot -p

```
When I write it gives me 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by munishvit on 2009-07-28
Bump!!!

---

### Post by jespdj on 2009-07-28
munishvit, instead of bumping a thread which is almost two years old, start a new topic in which you explain what your problem is!

---

