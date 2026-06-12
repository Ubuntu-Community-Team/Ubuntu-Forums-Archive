---
title: "mysql can't log in"
date: 2012-08-22
forum: Programming Talk
---

### Post by Mr.Dee on 2012-08-22
```

$ mysql -p -u root
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```
 
Not sure what I'm doing wrong. My google-fu may be too week:
[http://dev.mysql.com/doc/refman/5.1/en/access-denied.html](http://dev.mysql.com/doc/refman/5.1/en/access-denied.html)

---

### Post by Mr.Dee on 2012-08-22
```
 
mysqld_safe --skip-grant-tables

```
That worked for me, but now it seems i don't need a password...

---

### Post by Bachstelze on 2012-08-22
What exactly do you want to do? Have you set an initial root password? If you re using Ubuntu, you have been prompted for one in the debconf screen after you installed mysql.

---

### Post by rukiaEnix on 2012-08-22
Or maybe the root user is not allow to start a session.

---

### Post by Mr.Dee on 2012-08-22
Running Linux Mint.  Can't remember if I created a password.  I installed by ...
 
```
 
sudo apt-get install mysql-server


```

---

### Post by Bachstelze on 2012-08-22
Try

```
sudo dpkg-reconfigure mysql-server-5.5
```

Or whatever your mysql version is. Don't do it on the mysql-server metapackage, it will not work.

---

### Post by Mr.Dee on 2012-08-22
> **Bachstelze said:**
> Try
 
```
sudo dpkg-reconfigure mysql-server-5.5
```
 
Or whatever your mysql version is. Don't do it on the mysql-server metapackage, it will not work.
 
WORKED!!! next round of beer is on me!  Thanks to all.

---

### Post by rukiaEnix on 2012-08-22
Well, let's wait for that beer, I'll join if it happens even though I didn't help xD but don't worry I'll pay my own beer xD

---

### Post by BadB77 on 2012-11-15
wow! it also worked for me - my very same problems started when I upgraded from Lucid to 12.04. I started receiving Access denied, spent a week trying to fix it... 3306 was open (terminal connection was accepted), iptables showed the port was also fine. mysqladmin was also returning access denied etc.

Reinstallation (autoremove/autoclean/using software center) did not work as well... I tried all "default" pwds I could think of...

mysqld_safe --skip-grant-tables did not work btw too, so I rm'ed the file manually....

and smth from the above worked... one weird thing though...after all remove/autoclean/rm's I still after re-installation (when I got access to my db's) I see my older db's...

not sure if it's feature or a bug....

---

