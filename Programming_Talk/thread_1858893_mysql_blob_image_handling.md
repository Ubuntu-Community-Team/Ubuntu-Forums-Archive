---
title: "mysql blob image handling"
date: 2011-10-13
forum: Programming Talk
---

### Post by moldaviax on 2011-10-13
Hello all,

We recently migrated an application from oracle/windows servers to mysql/ubuntu and have experienced issues with the loading of images from the database.

The images are stored in a blob datatype and loaded via hibernate/jdbc as required. The oracle database was converted to mysql using an enterprise db convert tool which worked fine on test environments on windows. However when we upload the mysql export files to the ubuntu server all the data seems fine except the jpg images which don't render. 

We tried directly loading images into mysql on ubuntu and haven't had any success extracting those either, leads us to wonder if something needs installed or if something we are doing is corrupting the data.

Our installation is based on Ubuntu 10.04 64 bit, mysql 5 and tomcat. 

many thanks

M.

---

### Post by karlson on 2011-10-13
> **moldaviax said:**
> Hello all,

We recently migrated an application from oracle/windows servers to mysql/ubuntu and have experienced issues with the loading of images from the database.

The images are stored in a blob datatype and loaded via hibernate/jdbc as required. The oracle database was converted to mysql using an enterprise db convert tool which worked fine on test environments on windows. However when we upload the mysql export files to the ubuntu server all the data seems fine except the jpg images which don't render. 

We tried directly loading images into mysql on ubuntu and haven't had any success extracting those either, leads us to wonder if something needs installed or if something we are doing is corrupting the data.

Our installation is based on Ubuntu 10.04 64 bit, mysql 5 and tomcat. 

many thanks

M.

Have you tried using non-JDBC connector?
[http://dev.mysql.com/doc/refman/5.0/en/blob.html](http://dev.mysql.com/doc/refman/5.0/en/blob.html) has a good example of doing the image store and display in QT.  If this works for you there may be issues using JDBC.

---

### Post by moldaviax on 2011-10-13
Hi Karlson

Thanks for the link, some things there to follow up.

As for non jdbc connectors, we rewrote some of the code in php as a test and had the same problem, it makes me think its a config issue, somewhere! :-)

cheers

M.

---

### Post by karlson on 2011-10-13
> **moldaviax said:**
> Hi Karlson

Thanks for the link, some things there to follow up.

As for non jdbc connectors, we rewrote some of the code in php as a test and had the same problem, it makes me think its a config issue, somewhere! :-)

cheers

M.

In that doc there is link to a tutorial for using PHP.  I take it that doesn't work?

---

