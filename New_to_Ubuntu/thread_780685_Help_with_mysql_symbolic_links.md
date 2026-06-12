---
title: "Help with mysql symbolic links"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by flamingsole on 2008-05-03
Hello,

I just upgraded to Hardy Heron, and am getting all of my data working the way it was on Gutsy.

In Gutsy, I stored my MySQL data files on the /home partition, and created a symbolic link to them inside /var/lib. So, there was a symbolic link called mysql that pointed to /home/username/mysql, which was owned by the MySQL server.

I can't get this to work on Hardy, though. I've created the symbolic link, verified that it is owned by MySQL, but when I try to start the MySQL server I get a fail message. I'm not sure where to find more information on the failure, or what I need to do differently.

Any thoughts?
Thanks,
Jon

---

### Post by Monicker on 2008-05-03
Check /var/log/mysql.log.  What kind of errors does that show?

---

### Post by flamingsole on 2008-05-03
/var/log/mysql.log and /var/log/mysql.err are both empty. That doesn't seem normal, maybe they are somewhere else?

---

### Post by Monicker on 2008-05-03
> **flamingsole said:**
> /var/log/mysql.log and /var/log/mysql.err are both empty. That doesn't seem normal, maybe they are somewhere else?

/var/log/mysql.log is the default location.  Even if it dies trying to start up, normally something is written to the log files.  You can verify the location of the logs by looking at /etc/mysql/my.cnf


Also check /var/log/daemon.log

---

### Post by flamingsole on 2008-05-03
The main log file says this, from a couple of attempts at starting mysql:
```

/usr/sbin/mysqld, Version: 5.0.51a-3ubuntu5-log ((Ubuntu)). started with:
Tcp port: 3306  Unix socket: /var/run/mysqld/mysqld.sock
Time                 Id Command    Argument
/usr/sbin/mysqld, Version: 5.0.51a-3ubuntu5-log ((Ubuntu)). started with:
Tcp port: 3306  Unix socket: /var/run/mysqld/mysqld.sock
Time                 Id Command    Argument
/usr/sbin/mysqld, Version: 5.0.51a-3ubuntu5-log ((Ubuntu)). started with:
Tcp port: 3306  Unix socket: /var/run/mysqld/mysqld.sock
Time                 Id Command    Argument

```

---

### Post by TwoWordz on 2009-04-07
Did you fix this? 

I have the same problem. 

TW

---

### Post by flamingsole on 2009-04-07
No, I never did fix it. I've just used and restored a backup of the MySQL data. The symlink never did work.

---

