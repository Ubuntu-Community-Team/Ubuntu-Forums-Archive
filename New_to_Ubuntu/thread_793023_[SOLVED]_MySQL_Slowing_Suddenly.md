---
title: "[SOLVED] MySQL Slowing Suddenly"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by mrhinman on 2008-05-13
System: Dapper Drake 6.06 Server w/GUI installed

Okay, suddenly this morning the MySQL DB is running terribly slow.  All other aspects of the server (apache, ftp, etc) are all running quite speedily.

I've scoured the web for answers but they go on about query optimization, which I've done extensively already in the past.  Ideas?

---

### Post by Monicker on 2008-05-13
Do you have any stalled queries?  If you have mysql administrator installed, you can check the number of connections, and see if perhaps there is a backlog.

---

### Post by mrhinman on 2008-05-13
> **Monicker said:**
> Do you have any stalled queries?  If you have mysql administrator installed, you can check the number of connections, and see if perhaps there is a backlog.

I am running WebMin.  Can I look for stalled queries there?

---

### Post by Monicker on 2008-05-13
No idea.  I do not use webmin.

You can check from the command line:

```
mysql -u root -p
```

Enter the root password and then the following

```

show processlist;
```

---

### Post by mrhinman on 2008-05-13
> **Monicker said:**
> No idea.  I do not use webmin.

You can check from the command line:

```
mysql -u root -p
```

Enter the root password and then the following

```

show processlist;
```

Here's what I have:

mysql> show processlist;
+----+------+-----------+------+---------+------+-------+----------------- -+
| Id | User | Host      | db   | Command | Time | State | Info  |
+----+------+-----------+------+---------+------+-------+----------------- -+
| 98 | root | localhost | NULL | Query   |    0 | NULL  | show processlist  |
+----+------+-----------+------+---------+------+-------+----------------- -+
1 row in set (0.00 sec)

No real trouble there...

Wonder what it could be?  I've run the Ubuntu system monitor and all look great, cpu, memory, etc.

---

### Post by Monicker on 2008-05-13
Hrmm.  This just started today?  Are there a lot of queries against the db?  Is there a lot of information in the db tables?

Another thing to look at is disk space where /var/lib/mysql is located.

What does the following show?

```
df -h
sudo du -ch /var/lib/mysql
```

---

### Post by mrhinman on 2008-05-13
> **Monicker said:**
> Hrmm.  This just started today?  Are there a lot of queries against the db?  Is there a lot of information in the db tables?

Another thing to look at is disk space where /var/lib/mysql is located.

What does the following show?

```
df -h
sudo du -ch /var/lib/mysql
```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             181G   13G  160G   8% /
varrun                474M  216K  474M   1% /var/run
varlock               474M  4.0K  474M   1% /var/lock
udev                  474M  108K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm


680K    /var/lib/mysql/mysql
60K     /var/lib/mysql/safety
15M     /var/lib/mysql/apps
492K    /var/lib/mysql/wiki
64K     /var/lib/mysql/clients
44M     /var/lib/mysql
44M     total

---

### Post by mrhinman on 2008-05-13
I wonder if my Postfix Mail Server could be the trouble.  I keep getting mail message in queue, but they are addressed to root@ from root@....

I do have some script automated mails... perhaps they are not working.

Could that slow the system down?  But why would MySQL only be affected?

---

### Post by mrhinman on 2008-05-13
Whoa, Nellie!

I have a test area with new code which seems to be zipping along just fine... Could be the old PHP code?

---

### Post by mrhinman on 2008-05-13
Okay, I had a moment of stupid there.  I realized I had the file which houses my connect information using a remote address from DynDNS instead of "localhost"...  wow was that dumb, and I can't figure out how it happened.

Anyway, problem solved.

---

