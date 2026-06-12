---
title: "MySQL: which one needed?"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by Autodave on 2013-06-08
Installing a program for our church's library.  Program calls for MySQL to be installed.  This will all be on one machine and one machine only.  Question: do I need to Install MySQL server or client, or both?

---

### Post by Cheesemill on 2013-06-08
It will be MySQL server that's needed, but installing this installs the client as well.
```
sudo apt-get install mysql-server
```

---

### Post by Autodave on 2013-06-08
I installed server through the software center: I assumke that client was also installed then?

---

### Post by SeijiSensei on 2013-06-08
If you can type "mysql" at the command prompt and not get an error in response, then the client is installed.  Note that if you intend to talk the to MySQL database with PHP, you need make sure the **php5-mysql** package is installed as well.

---

### Post by rewyllys on 2013-06-08
> **Autodave said:**
> Installing a program for our church's library.  Program calls for MySQL to be installed.  This will all be on one machine and one machine only.  Question: do I need to Install MySQL server or client, or both?
I hope I'm not being too curious in asking, what is the program that you're installing for your church's library?

---

### Post by Autodave on 2013-06-09
> **rewyllys said:**
> I hope I'm not being too curious in asking, what is the program that you're installing for your church's library?

Right now, I am looking at KOHA.  This is a small library: maybe 300 books.  I have been looking around and that was one I thought might work.  If anyone has a better idea, let me hear it.

Also, I need to install Sorl.  Is there a command line for that or do I need to d-l that .tar file and do it that way?

---

### Post by Cheesemill on 2013-06-09
I think you mean Solr...
```
sudo apt-get install solr-common
```

You can search for packages available in the repositories using the Ubuntu package database....
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by rewyllys on 2013-06-09
> **Autodave said:**
> Right now, I am looking at KOHA.  This is a small library: maybe 300 books.  I have been looking around and that was one I thought might work.  If anyone has a better idea, let me hear it.

Also, I need to install Sorl.  Is there a command line for that or do I need to d-l that .tar file and do it that way?
Thanks for the information.  KOHA looks interesting.


BTW, have you looked for possible answers to your MySQL question on the [Koha Community Website]("http://koha-community.org/")?

---

