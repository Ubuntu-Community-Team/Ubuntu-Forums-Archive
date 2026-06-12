---
title: "a good front-end program for MySQL"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by balagosa on 2008-06-24
Hi All. I have been looking for a good front-end program for MySQL. During my Windows days, I depended highly upon [SQLYog]("http://www.webyog.com/en/"). I searched for a linux version for the program but never found one. So now I am asking some suggestions to what might be a good alternative to **SQLYog**.

The easier to use, the better.

---

### Post by hyper_ch on 2008-06-24
phpMyAdmin

---

### Post by balagosa on 2008-06-24
thanks for the quick reply. I will be searching into this. 

can you give me a quick background of phpMyAdmin? Like, will I access the program via web browser? Does it support only PHP connections; I use Java?

---

### Post by Firehalk on 2008-06-24
**Navicat Lite for MySQL**

Most simple program I ever saw to administrate MySql bases... The Lite version is free, and has everything that is really essential to admin database :)

I was changing server, host, and thanks to that program all was transfered fine. With phpmyadmin I did get some complications.

---

### Post by Circus-Killer on 2008-06-24
```
sudo apt-get install mysql-admin
```

set of gui tools which makes managing a database server real easy.

---

### Post by hyper_ch on 2008-06-24
yes, php and apache will be needed for phpmyadmin.... you just need to configure it correctly and then it runs great

---

### Post by the_doc on 2008-06-24
Apparently SQLYog has been made to work under wine.

---

### Post by balagosa on 2008-06-24
ok, next step is to set up connection. Anyone got a good "Setting up MySQL guide" on your bookmarks?

from what i know, the back-end and the front-end MySQLs have to be connected with the help of a connector (based from windows experience).

**the_doc:**
I uninstalled and no longer use Wine because it is a waste of my Hard Disk. Everything I needed is on Linux. I had Wine before to play games, but when I learned that it did not support the games I wanted, so I removed it.

---

### Post by hyper_ch on 2008-06-24
steph 14: mysql
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p4)

---

### Post by balagosa on 2008-06-24
thanks, found it. will be giving my feedback right after.

---

### Post by Dr Small on 2008-06-24
> **hyper_ch said:**
> phpMyAdmin
+1 for PhpMyAdmin.

---

### Post by balagosa on 2008-06-24
1) Tried MySQL Administrator. Far from what I want. It is a program to administer the database; it does not do any inter-actions. I can not Export, Import, Query from MySQL Administrator. I will give it a 5/10.

Note: Unless that there is a **Query Text Field** but I just did not find it.

2) Tried PHPMyAdmin. Closer to what I want, has a **Query Text Field**. But my problem is I can not connect to the network MySQL server which is not loaded with phpMyAdmin. I will give it an 8/10.

Note: I was using localhost connection when I tried PHPMyAdmin. Is it possible to ever access the Network Server with PHPMyAdmin?

**BDNiner:**
I will be trying MySQL Query browser. Give you my feedback later.

---

### Post by BDNiner on 2008-06-24
There is a MySQL Query Browser that is also in the repos. i don't know if you are looking for one app to handle both the administration and query browsing. I use MySQL admin and MySQL Query Browser. i have not tried PHPMyAdmin.

---

### Post by hyper_ch on 2008-06-24
> **balagosa said:**
> Note: I was using localhost connection when I tried PHPMyAdmin. Is it possible to ever access the Network Server with PHPMyAdmin?

of course it is... just alter the phpmyadmin config accordingly...

---

### Post by balagosa on 2008-06-24
Tried MySQL Query Browser. It is close to what I want, but I am still configuring out how to export Database. I am also puzzled by **Stored Routine**, is it equal to Store Procedure. I can not execute Multiple queries(which I usually do), unless I just did not discover how to do it.7/10 for MySQL Query Browser.

**hyper_ch:**
Do you mind pin-pointing where to find the config? I am liking phpMyAdmin right now.

---

### Post by hyper_ch on 2008-06-24
good question... I think phpmyadmin installs in /var/lib/phpmyadmin .... you'll have to find out yourself... in there you'll have a config file

if yuo can't find it:

```

sudo updatedb
locate phpmyadmin

```

---

### Post by balagosa on 2008-06-24
found it, well i think it is the one. It is located at: ** /usr/share/phpmyadmin/libraries/config.default.php**.

Note: This is the phpMyAdmin config but it says at the top of the file to edit config.inc.php

---

### Post by balagosa on 2008-06-24
Yes, it is confirmed. the config to add another host is **/etc/phpmyadmin/config.inc.ph**.

I wonder if there is a how-to for this?

Searching...

I found this [one]('http://ubuntuguide.org/wiki/Ubuntu:Hardy'). Adding a Virtual Host to your LAMP server. Anyone care to define LAMP for me(noob here):)

---

### Post by balagosa on 2008-06-24
never mind. Here it is: LAMP (Linux, Apache, MySQL and PHP)

---

