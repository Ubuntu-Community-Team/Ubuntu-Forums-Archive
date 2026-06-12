---
title: "Brand new to Ubuntu.   Want to install local DB (no cloud) prefer ORACLE but.."
date: 2018-01-15
forum: New to Ubuntu
---

### Post by chris53 on 2018-01-15
Hi there.   I'm brand new to Unbuntu.   Finally took the plunge.    About me, I'm a Data Warehouse developer, mostly Informatica and SQL guy but wanted to improve my UNIX skills.

I would love to have a local install of ORACLE and/or DB2 and SQL Server for that matter.  I would prefer an older version, not cloud based.   I know ORACLE 9i / 10g is no longer available but I'm sure its out there somewhere for download.

If any of you could recommend a source for a local installation of a DB I would appreciate it.

Thanks!
Chris

---

### Post by TheFu on 2018-01-15
A few ideas:
```
$ sudo apt install mariadb-server postgresql  sqlite3
```

All of these are SQL DBs.  Postgres is the most like Oracle.  MariaDB is API compatible with MySQL which many people in the F/LOSS world would chose over anything made by Oracle.

SQLite is THE most popular DBMS in the world, by far, as you are probably aware.

I'm fairly certain if you contact Oracle, IBM and Microsoft, they would be very willing to provide quotes for their commercial DBMS on Linux.

---

### Post by chris53 on 2018-01-15
Thank you very much.   I'll take a look at it.   Much appreciated.  

Edit:   I'm not really a DBA sort of guy, but I would like to get there.   I need to educate myself.  :)

Chris

---

### Post by SeijiSensei on 2018-01-15
I've used [PostgreSQL]("http://www.postgresql.org/") for a couple of decades now and would not choose any other SQL server for Linux.  I have a MySQL instance running on my servers to support WordPress, but I'd never prefer MySQL over PostgreSQL in any other setting.  PostgreSQL has excellent command-line utilities to create users and databases, tasks that are unnecessarily complex in MySQL.  It has a solid ODBC driver so it can communicate with Windows software.  I have a couple of PG databases that I manage with Microsoft Access that way. 

I started using Postgres when the licenses for mSQL and MySQL prohibited commercial redistribution.  Since I was selling servers at the time, I was forced to use the entirely free PostgreSQL.  I've never looked back.

---

### Post by TheFu on 2018-01-15
I liked that pg supported perl-based triggers.

There's a guy that the *Ask Noah Show* highlights who self-taugh himself to be a DBA in a few months. A year later and he's doing consulting work ... 100% F/LOSS DBs. Nothing commercial.

Linux is a VERY different world from what MSFT/Apple push.  And since most internet sites use F/LOSS DBs for their data storage, that should be a consideration as you begin your learning.

---

### Post by SeijiSensei on 2018-01-16
By the way, at one point I had a project that required me to interact with Oracle running on Linux.  It was a pain in the neck.  That was some time ago so maybe things have improved.  I just remember having to do all sorts of little annoying things to get a client written in PHP to work with Oracle.

---

### Post by Habitual on 2018-01-18
I just wound up using Oracle Enterprise Manager for the complex, pain in the neck stuff.

---

### Post by chris53 on 2018-01-18
> **Habitual said:**
> I just wound up using Oracle Enterprise Manager for the complex, pain in the neck stuff.

Which version of Oracle Enterprise Manager do you have and when did you download/install it?   I would prefer to use Oracle since that is what I use at work most often. And this is all local DB's?   I don't want to pay for the cloud service.

Thanks,
Chris

---

