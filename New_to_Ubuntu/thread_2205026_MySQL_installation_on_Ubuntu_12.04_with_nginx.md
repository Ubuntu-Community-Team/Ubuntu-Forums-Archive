---
title: "MySQL installation on Ubuntu 12.04 with nginx"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by Youri_van_Dijk on 2014-02-11
Hey guys I'm trying to follow the digital ocean tutorial to install a WordPress on a vps, but every time I try I can't establish a database connection. There must be something I'm doing wrong... Could someone hint me to a more noob proof guide To install MySQL on nginx?

 thanks

---

### Post by ubudog on 2014-02-11
Are you sure mysqld is running?
```
ps ax | grep mysql
```

---

### Post by Youri_van_Dijk on 2014-02-12
Hey thanks for that command. My SQL was running.  I got a little frustrated and set out to try again with another Ubuntu install. Hopefully I'll manage this time.

---

### Post by Youri_van_Dijk on 2014-02-13
I've tried again and am now stuck while trying to create a database on MySQL with the following command:
```
mysql -u USERNAME -pPASSWORD -e 'create database DB_NAME'
```

and recieve the following error:
```
ERROR 1045 (28000): Access denied for user 'USERNAME'@'localhost' (using password: YES)
```

How to find out what the issue is?

---

### Post by steeldriver on 2014-02-13
Did you actually set up a mysql user called USERNAME? iirc the default mysql-server install scripts only prompt you to set up the 'root'@'localhost' account

---

### Post by Youri_van_Dijk on 2014-02-13
I've changed the values for USERNAME, PASSWORD and DB_NAME to my own values ;)

I have been following this tutorial: [https://rtcamp.com/wordpress-nginx/tutorials/single-site/minimal/](https://rtcamp.com/wordpress-nginx/tutorials/single-site/minimal/)

---

### Post by steeldriver on 2014-02-13
OK let me try to rephrase. Is there a mysql user account with the "own values" of USERNAME and PASSWORD that you used?

---

### Post by Youri_van_Dijk on 2014-02-13
hmm reading back the tutorial never mentions creating a user befor exept root and a password... I probably should do that :D

Edit: Btw somehow I made a mistake and I recieve a "[COLOR=#000000][FONT=Times New Roman]502 Bad Gateway" error. How to figure out what happened?[/FONT][/COLOR]

---

