---
title: "Which Database to Use"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by candra on 2011-11-04
Greetings< 

I am a Ubuntu 10.04 LTS - the Lucid Lynx - user and I am looking for an easy-to-use, dependable database program. 

To date I have been using Kexi, and I am looking for something a bit more flexible. For instance, a database where I can change the design view and configuration without losing all the inputed data. 

In essence, I am looking for the open software version of MS Access. 

Any tips? recommendations? 

Thanks, 
candra

---

### Post by dave0109 on 2011-11-04
Some will doubt that Microsoft Access counts as a real database.

If you want a proper SQL database, have a look in the Software Center for MySQL.  You can administer it with a number of clients, including a web interface (phpmyadmin) if you have Apache installed on your machine as well. There are also client APIs for nearly any programming language you care to use.

---

### Post by jmajeremy on 2011-11-04
I always use MySQL as the database with phpMyAdmin with the frontend GUI administration/management. But if you want some more similar to MS Access, i.e. where you mainly access it through a desktop application, I would try LibreOffice Base. It's normally included with Ubuntu, but if you don't have it, you can get it by running ```
sudo apt-get install libreoffice-base
```

---

### Post by candra on 2011-11-04
Indeed your point is well-taken about Access...

Thank you for pointing me towards MySQL - I will check it out...

---

### Post by candra on 2011-11-04
Thanks, jmajeremy, for the lead on LibreOffice Base...

---

