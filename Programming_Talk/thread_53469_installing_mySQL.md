---
title: "installing mySQL"
date: 2005-08-01
forum: Programming Talk
---

### Post by ronnelson929 on 2005-08-01
I've got all the packages installed for mySQL, php works, perl works etc. and apache works.  I even believe that mySQL works i just can't get permissions to establish / change the password for the username or create a new user.  I need to create these things to install moveable type the way that I want to.  I can get into the mysql shell but once there i can't perform any operations because i'm not logged in with any privileges.  Any ideas? :confused:  :confused:

---

### Post by Burgundavia on 2005-08-01
This page may have some information you might want to look at:

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

Corey

---

### Post by Wide on 2005-08-01
Have you set a root password for mysql?

[http://ubuntuguide.org/#installmysqldatabaseserver](http://ubuntuguide.org/#installmysqldatabaseserver)


```
mysqladmin -u root password db_user_password
``` 


replace "db_user_password" with your password


Hope this helps :grin:

---

### Post by ronnelson929 on 2005-08-01
root@slacker:/usr/bin # mysqladmin -u root password blank
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

i don't believe that i've given it a password yet.  neither of those suggestions have gotten me anywhere.  I believe that I am yet again stuck on the mysql system ](*,)  ](*,)

---

