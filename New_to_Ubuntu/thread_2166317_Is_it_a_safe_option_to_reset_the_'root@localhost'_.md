---
title: "Is it a safe option to reset the 'root@localhost' password via phpmyadmin?"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by Chris of Arabia on 2013-08-08
For what now seem rather inexplicable reasons, I didn't set a password for MySQL when I installed my LAMP server (13.04). Since then, I've been struggling to reset the 'root' password for MySQL to something usable/memorable, and as a consequence have been unable to gain access to phpmyadmin to do any work with databases.

Having taken a fair amount of time to use what appear to be the standard methods of resetting the 'root' password e.g. [http://chetansingh.me/2012/07/01/reset-lostforgot-mysql-root-password-ubuntu/](http://chetansingh.me/2012/07/01/reset-lostforgot-mysql-root-password-ubuntu/), I've had no joy getting things reset. In the process though, I did come across a way of accessing the password for **debian-sys-maint** user, by following this post - [http://ubuntuforums.org/showthread.php?t=1836919&p=11210808#post11210808](http://ubuntuforums.org/showthread.php?t=1836919&p=11210808#post11210808)

Using those user credentials, I have succeeded in logging into phpmyadmin, and now have access to all of the databases present (information_schema, MySQL, performance_schema, phpmyadmin & test). Given that I've now got into phpmyadmin using the **debian-sys-maint** user, is it now a safe option for me to reset the 'root' password in the (mysql) database | (user) table using the built-in tools within phpmyadmin?

Assuming that it is, should I then proceed to reset all of the versions of root to the same password? i.e.[INDENT]root@localhost
root@127.0.0.1
root@<server_name>
root@::1
[/INDENT]

---

### Post by stmiller on 2013-08-08
Yep - it is fine to do that through phpmyadmin.

I would make all of those have the same password.

Cheers,

---

### Post by Chris of Arabia on 2013-08-09
Thanks. I'll give it a go.

---

### Post by Chris of Arabia on 2013-08-09
OK, all is good with this now. I changed the passwords as proposed above, and can now log into phpmyadmin using root and debian-sys-maint. I can also log into MySQL at a terminal using:

> > mysql -u root -p

or

> mysql -u debian-sys-maint -p

job's a good 'un...

---

