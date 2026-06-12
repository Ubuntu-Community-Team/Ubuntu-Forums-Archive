---
title: "can't login with root"
date: 2020-02-16
forum: New to Ubuntu
---

### Post by cnedas on 2020-02-16
Hello,

I installed Ubuntu a few months ago with a user ID that the system asked me to provide which is a three character id.

Now, I want/need to login as root, but the system won't let me.

I can switch to root after I login with my id, but I want to login using ssh root@192.168.x.x instead of ssh abc@192.168.x.x

but when I do ssh and I am asked for my password, and  I get an "Access Denied" message, but I know the password is right.

Any suggestions?

---

### Post by CatKiller on 2020-02-16
You can't log in as root. You especially can't log in remotely as root. Log in as a normal user and then use sudo if you need to elevate your privileges temporarily.

---

### Post by cnedas on 2020-02-16
> **CatKiller said:**
> You can't log in as root. You especially can't log in remotely as root. Log in as a normal user and then use sudo if you need to elevate your privileges temporarily.

Ok Thanks! I had no idea about that.

But I have an issue now, I am doing:

```
sudo mysql_secure_installation
```

and I get this warning:
> 
NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

I am trying to install the ISPConfig control panel on my localhost to test it, and one of
the steps is to set a root password in MariaDB, so for that I need to open mysql_secure_installation,
but when I type in the password I know, I get:

> 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2 "No such file or directory")
Enter current password for root (enter for none):


Any thoughts?

---

### Post by yancek on 2020-02-16
Did you create a root password in mysql?  It is not the same as the root password for the operating system.  The message tells you to hit enter if you haven't created a password specifically for mysql yet.  You will be prompted to create it later if you do not have one.

---

