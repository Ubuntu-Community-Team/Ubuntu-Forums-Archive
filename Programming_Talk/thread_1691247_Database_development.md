---
title: "Database development"
date: 2011-02-19
forum: Programming Talk
---

### Post by foxy123 on 2011-02-19
I wonder if it is very difficult to develop a database in Linux. I actually need a quite simple database for a small recruitment agency, which could store the information on applicants/candidates and probably export it in a file that could be sent to a client.

If it is too complicated may anyone suggest any commercial solution, which can be run on Linux? Cheers in advance.

---

### Post by thornmastr on 2011-02-19
Hi,

Look at Sqllite. [http://www.sqlite.org/](http://www.sqlite.org/)

It is free. It is meant as a single user DB, is very easy to use. Does not require a server process.

Any questions, post more of your requirements.

HTH,

Thorny

---

### Post by drdos2006 on 2011-02-19
This may be of some help.

[http://dabodev.com/](http://dabodev.com/)

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html)
# Building a Database Application using the Dabo Class Designer (Part 1) (Ed, 2007-01-04, about 10 minutes)

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html)
# Building a Database Application using the Dabo Class Designer (Part 2) (Ed, 2007-01-05, about 9.5 minutes)

regards

---

### Post by sneakyimp on 2011-02-19
Using linux to develop with MySQL is a piece of cake on a LAMP stack (Linux/Apache/PHP/MySQL) if phpMyAdmin is installed.  phpMyAdmin is a DB admin system written in PHP for MySQL and lets you create databases, tables, user, etc. and administer them and run queries.

---

### Post by Some Penguin on 2011-02-19
sqlite, MySQL, PostgreSQL are all reasonable choices.  The latter two (haven't investigated the first, but almost certainly the same goes for it) have libraries available to facilitate access in a number of programming languages and environments.

Importing to/from CSV format is pretty common functionality, but you do want to standardize on character sets (UTF-8 being a fairly logical choice; beware of software tools defaulting to some platform-specific character set.  I'm looking at you, MacRoman.)

Creating tables is pretty simple for the most part, when records are flat.  Storing variable-length arrays may be slightly trickier, at least if you care about having the DB see them as such (and not simply some blob which you deserialize into an array).  Some frameworks may abstract a fair bit of this ([http://en.wikipedia.org/wiki/Java_Persistence_API]("http://en.wikipedia.org/wiki/Java_Persistence_API") for instance).

---

### Post by foxmuldr on 2011-02-20
> **foxy123 said:**
> I wonder if it is very difficult to develop a database in Linux. I actually need a quite simple database for a small recruitment agency, which could store the information on applicants/candidates and probably export it in a file that could be sent to a client.

If it is too complicated may anyone suggest any commercial solution, which can be run on Linux? Cheers in advance.

OpenOffice or LibreOffice comes with a database tool.  It allows you to create input forms, record data, do reports, etc.  It's all GUI and part of the native install.

---

### Post by foxy123 on 2011-02-20
Thanks a lot, guys, for your responses!

> **foxmuldr said:**
> OpenOffice or LibreOffice comes with a database tool.  It allows you to create input forms, record data, do reports, etc.  It's all GUI and part of the native install.

I had some experience with MS Access and it became quite slow as soon as the size of the database had grown to a certain level. I guess it is true for OpenOffice/LibreOffice one.

Regarding Sqllite is there any good tutorial available?

---

### Post by lykeion on 2011-02-20
> **foxy123 said:**
> Regarding Sqllite is there any good tutorial available?
[Command Line Shell For SQLite]("http://sqlite.org/sqlite.html")
[Using SQLite in Python]("http://www.devshed.com/c/a/Python/Using-SQLite-in-Python/")
[PHP Manual SQLite3]("http://www.php.net/manual/en/book.sqlite3.php")

---

### Post by foxmuldr on 2011-02-22
> **foxy123 said:**
> I had some experience with MS Access and it became quite slow as soon as the size of the database had grown to a certain level. I guess it is true for OpenOffice/LibreOffice one.

Very likely.  But it would get you up and running today while you work on a more elegant solution over the next several days.

- Rick C. Hodgin

---

