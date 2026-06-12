---
title: "Can I auto create database from JPA?"
date: 2008-12-27
forum: Programming Talk
---

### Post by cl333r on 2008-12-27
Hi folks,
When I create (using JPA - java persistence api) a persistence unit and then persistence entities they auto create the corresponding tables and fields in the database.
Can I also make it to auto create the database (if it doesn't exist)?

If it matters I'm using Ubuntu 8.10 x86, EclipseLink, MySQL and GlassFish.

---

### Post by slavik on 2008-12-27
I am missing your question. If the JPA creates a database of everything you use/create, then what do you mean by auto creating the database? What database do you want to automatically be created?

---

### Post by cl333r on 2008-12-27
I mean it creates inside the database the tables and fields, but not the database, and if the database hasn't been created before (by hand) - everything fails. So before running the project (which will auto generate the tables and fields if needed) I first must create (by hand) a database. Example:
I was getting an error that there's no database which I specified in glassfish as "otherdb", after I logged into mysql and created by hand the database "otherdb" - glassfish started working and created in turn (inside "otherdb") the tables and fields as needed. Thus I wanna know whether I can also create the database from JPA like it happens to tables and fields.

---

### Post by slavik on 2008-12-27
I see. no idea :(

EDIT, you could use JDBC to check if the database is there and if not create it, but this would have to be part of the code and you would need create database privelege, which is a security risk.

---

### Post by tinny on 2008-12-28
I'm pretty sure you cant (but I have been wrong before).

Personally im not quite sure why this is an issue for you. When you say that you are creating your database "by hand" you make it sound like quite a labor intensive process, perhaps you are using the wrong tools?

Ive used J2EE + JPA + MySQL a lot and never found it to be a problem, you tend to just create your database once so for me this isnt a big deal.

For this type of database admin I use the MySQL GUI tools that are available in the Ubuntu repositories. Perhaps these tools will make life easier for you.

[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

---

### Post by cl333r on 2008-12-28
The reason is simple, my goal is to create programs/installers as automated as possible. Because (I hope) they won't only be used by myself (the installers) and I wanna avoid as many installation steps as possible. I'm one of those guys who wanna create software where you just point and click once and the software is smart enough to do everything by itself. I've also been wrong, but the option to create the database if it's not there yet should/must be possible from JPA since the JPA has been created to deal with databases, not with astronomy, physics nor geometry.

---

### Post by Quikee on 2008-12-28
Just use by default hsql or h2 (file or in-memory) database, which doesn't require that a user account on a database must be present before you can run you program. It even doesn't require that you have a database installed.

If the user wants something more - like mysql, postgres, oracle whatever - just write a shell script which does this for various databases or provide instructions what he should do.

Also it makes more sense to first create the program to a certain usable stage and worry about things like that later.

---

### Post by Ruhe on 2008-12-28
Yeah, it's really common task to generate DB schema from some persistent framework. Hibernate provides such mechanism through hbm2ddl.

**cl333r**
Everything depends on which JPA provider you use.
If you use Toplink, then add property toplink.ddl-generation to persistense.xml file.
If you use hibernate then set hbm2ddl = true.

Checkout ref docs.

---

### Post by cl333r on 2008-12-28
As I noted in 1st post, I use EclipseLink which is afaik the open-sourced version of TopLink.
I searched for the dll-generation property before creating this thread, but couldn't find the value which specifies that the database must be created if needed. Thus, do you know what value the "ddl-generation" must be assigned? The "create-tables" only cares about tables.

---

### Post by tinny on 2008-12-28
> **quikee said:**
> just use by default hsql or h2 (file or in-memory) database, which doesn't require that a user account on a database must be present before you can run you program. It even doesn't require that you have a database installed.

If the user wants something more - like mysql, postgres, oracle whatever - just write a shell script which does this for various databases or provide instructions what he should do.

Also it makes more sense to first create the program to a certain usable stage and worry about things like that later.

+1

---

