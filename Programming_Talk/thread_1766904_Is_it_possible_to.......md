---
title: "Is it possible to......"
date: 2011-05-25
forum: Programming Talk
---

### Post by thunderkyss on 2011-05-25
Write a Web application that can read & write to a database located on a remote server? 

Can I require users to log on & use that user id to control what they can & cannot do in/to the database?

Can multiple users access the database with little to no cost in speed? 

How would I start?

---

### Post by slavik on 2011-05-25
every user would either need their own db, or to have restricted access to the same db, simplest solution is something like phpmyadmin for mysql.

---

### Post by r-senior on 2011-05-25
> **thunderkyss said:**
> Write a Web application that can read & write to a database located on a remote server?
Most significant web applications use this model. The database is usually on a separate physical machine(s) from the web application server(s).

> 
Can I require users to log on & use that user id to control what they can & cannot do in/to the database?
You can authenticate your users in the web application and control what they can and cannot do. Typically, web applications maintain a pool of anonymous connections to the database for performance reasons. As such, enforcing policies based on database constraints, e.g. the ability for a given userid to update a specific column, is problematic.

> Can multiple users access the database with little to no cost in speed?
Typical database engines for these applications, e.g. Oracle and MySQL, are designed with that in mind.

> How would I start?
Decide which language you want to use, based on the scale of your requirements. Prepare yourself for a lot of work.

---

### Post by simeon87 on 2011-05-25
> **slavik said:**
> every user would either need their own db, or to have restricted access to the same db, simplest solution is something like phpmyadmin for mysql.

Not really, database connections can be reused and you can determine in your web application what permissions a user has. This also determines what the user can modify in the database.

---

### Post by thunderkyss on 2011-05-25
Thanks for all the replies guys. 

The reason I am contemplating a web application is because I want hundreds of users to access the database without having to deploy/install an application on several machines. 

Are there any other benefits to a stand alone application that might outweigh that one benefit of the web app?

---

### Post by thunderkyss on 2011-05-25
> **r-senior said:**
> 

Decide which language you want to use, based on the scale of your requirements. Prepare yourself for a lot of work.

Is there anyway to test what kind of performance hit I would take with multiple users?

Other than testing with multiple users that is.

---

### Post by Petrolea on 2011-05-25
> **thunderkyss said:**
> Thanks for all the replies guys. 

The reason I am contemplating a web application is because I want hundreds of users to access the database without having to deploy/install an application on several machines. 

Are there any other benefits to a stand alone application that might outweigh that one benefit of the web app?

For your job I recommend PHP + MySQL + phpmyadmin. Few 100 users shouldn't be a problem for MySQL, and in combination with PHP it can do lots of things so there is really no need for a separate program.

With HTML + CSS you can create a great interface with buttons and textboxes and with using PHP you can retrieve data and save it in a database (which is usually in the same local network as webserver).

---

