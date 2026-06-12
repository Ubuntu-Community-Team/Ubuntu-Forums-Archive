---
title: "cannot move mysql data directory to another partition"
date: 2010-12-21
forum: Programming Talk
---

### Post by realitybites on 2010-12-21
I followed the [simple steps]("http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html") to change the mysql data directory on 10.10.

new directory is on another partition, since there is no empty space left on the original partition. the problem is, even though permissions make sense, I still get the following error message in the error log, during server startup:

```
101221 19:09:11 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Table 'plugin' is read only
101221 19:09:11 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101221 19:09:11  InnoDB: Started; log sequence number 0 44233
101221 19:09:11 [ERROR] /usr/sbin/mysqld: Can't create/write to file '/media/oldc/mysql/data/compname.pid' (Errcode: 13)
101221 19:09:11 [ERROR] Can't start server: can't create PID file: Permission denied
```

I feel the need to state the fact that directory owner is mysql user and the group is also set to mysql. Everywhere on the internet changing permissions had solved the problem, but not for me.


Edit: Now I realized apache also gives permission errors if I move the DocumentRoot to another partition. Thus, I realized this is not a folder permission issue, but a partition permission issue.
How can I fix this?

---

### Post by pukakk on 2011-01-16
I have same problem.

Please Help!

---

### Post by charlylh on 2011-03-19
Check /var/log/messages for apparmor denying access.
In that case edit and correct /etc/apparmor.d/usr.sbin.mysqld.

---

### Post by basarugur on 2011-09-20
I had the exact same problem. What solved my problem is, partitioning the RAID disks with **[gparted]("http://gparted.sourceforge.net/")**, not mounting them under /media/<name> etc. And if i say gparted, a "BIOS RAID support"ed version of gparted, I think it is 0.8.0 or higher.

After partitioning the BIOS RAID disks (near 2TB) as ext4, I mounted them using the method as told [here]("http://www.psychocats.net/ubuntu/mountlinux"). Then I re-did the things told in ubuntugeek.com about MySQL. This time it worked like a charm.

---

