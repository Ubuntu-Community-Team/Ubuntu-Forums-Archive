---
title: "focus/sis setup"
date: 2007-11-20
forum: Philippine Team
---

### Post by mitchi on 2007-11-20
Please help me on this one, I cant configure my pc to make Focus/SIS run. I've already installed PHP, PostgreSQL, Apache, Htmldocs, the php-pgsql support, I've even reinstalled my O.S. with the thought I messed up the system, but I still cant get it to work.

It returns the ff:

> 
Error: Focus/SIS cannot connect to the Postgres database. Either the database "focus" does not exist, Postgres is not running, it was not started with the -i option, or connections from this host are not allowed in the pg_hba.conf file.

If the database does not exist, create it using phpPGAdmin, PGAdmin III, or by opening a terminal window and following these directions:

   1. Login as the postgres user
      ex) server$ su - postgres
   2. Login to the postgres database server using the template1 database
      ex) server$ psql template1
   3. Create the focus database
      ex) template1=# CREATE DATABASE focus; 


I really don't know what to do with this one. Please help.

BTW, I'm using Focus 2.2.
[**http://www.focus-sis.org/**]("http://www.focus-sis.org/")

---

### Post by SLEducator on 2009-02-26
When Having trouble with installing Focus/SIS try instead openSIS at [http://www.opensis.com](http://www.opensis.com) we have an autoinstaller and our product is an improvement on the original code base for Focus.

---

### Post by Jstannard on 2009-03-12
Are you still having a problem? Or did you decide to migrate to the SIS suggested somewhere else. I might have some helpful hints, but don't want to expend the effort unless you're going to use them. 

Cheers, 
J

---

