---
title: "[SOLVED] mysql has turned into myheadache"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by infosys on 2008-05-20
During boot-up MySQL fails to start. It used to work just fine though, don't know what changed.

 I’ve gone through several different forums, and the two main problems I’ve seen posted were: 1. mysql-server was not installed, and I’ve verified mine is. 2. In the /etc/mysql/my.cnf file the bind-address was incorrect, normally due to the IP address of the server changing. I’ve verified mine is set to the loop-back, 127.0.0.1.

When I try to start MySQL manually, by using the command “sudo /etc/init.d/mysql start”, it fails. When I try to start MySQL manually, by using the command “sudo mysql start”, it fails giving “ERROR 2002 (HY000): Can’t connect to local MySQL server through socket ‘/var/run/mysqld/mysqld.sock’ (2)”.

I've also checked the /var/log/mysql.err and mysql.log files, but they are both empty.

Anybody know what I can do or where I should look?

I’ve had some permissions problems in the past, and my guess is this is somehow related to permissions even though I have no reason to belive so.

---

### Post by Monicker on 2008-05-20
What is the output of these commands?
```

ls -lh /var/lib|grep mysql
sudo ls -lh /var/lib/mysql
```

Also, do you have any mysqld-bin files in /var/lib/mysql?  Those are binary log files.  You can use mysqlbinlog to show their contents.

```
sudo mysqlbinlog /var/lib/mysql/mysqld-bin.000001 > log.txt
```

Just use the log file file with the highest number at the end, if you have several.  There might be some useful information there.

---

### Post by infosys on 2008-05-21
Here is the output of the two commands:

infosys@perldesk:~$ ls -lh /var/lib|grep mysql
drwxr-xr-x 4 mysql mysql 4.0K 2008-05-21 08:18 mysql
drwxr-xr-x 2 root  root  4.0K 2007-10-12 07:52 mysql-cluster

-and-

infosys@perldesk:~$ sudo ls -lh /var/lib/mysql
total 21M
-rw-r--r-- 1 mysql mysql    0 2008-04-07 09:12 debian-5.0.flag
-rw-rw---- 1 mysql mysql  10M 2008-05-14 10:20 ibdata1
-rw-rw---- 1 mysql mysql 5.0M 2008-05-14 10:21 ib_logfile0
-rw-rw---- 1 mysql mysql 5.0M 2008-03-12 09:54 ib_logfile1
drwxr-xr-x 2 mysql mysql 4.0K 2008-04-07 09:12 mysql
-rw------- 1 mysql mysql    6 2008-03-12 09:54 mysql_upgrade_info
drwxr-xr-x 2 mysql mysql  12K 2008-05-09 02:30 perldesk
infosys@perldesk:~$

I also don't seem to have any mysqld-bin files in the /var/lib/mysql folder. Here are the contents:

infosys@perldesk:/var/lib/mysql$ ls
debian-5.0.flag  ib_logfile0  mysql               perldesk
ibdata1          ib_logfile1  mysql_upgrade_info
infosys@perldesk:/var/lib/mysql$

-and-

infosys@perldesk:/var/lib/mysql/mysql$ ls
columns_priv.frm   help_relation.MYI  time_zone_leap_second.frm
columns_priv.MYD   help_topic.frm     time_zone_leap_second.MYD
columns_priv.MYI   help_topic.MYD     time_zone_leap_second.MYI
db.frm             help_topic.MYI     time_zone.MYD
db.MYD             host.frm           time_zone.MYI
db.MYI             host.MYD           time_zone_name.frm
func.frm           host.MYI           time_zone_name.MYD
func.MYD           proc.frm           time_zone_name.MYI
func.MYI           proc.MYD           time_zone_transition.frm
help_category.frm  proc.MYI           time_zone_transition.MYD
help_category.MYD  procs_priv.frm     time_zone_transition.MYI
help_category.MYI  procs_priv.MYD     time_zone_transition_type.frm
help_keyword.frm   procs_priv.MYI     time_zone_transition_type.MYD
help_keyword.MYD   tables_priv.frm    time_zone_transition_type.MYI
help_keyword.MYI   tables_priv.MYD    user.frm
help_relation.frm  tables_priv.MYI    user.MYD
help_relation.MYD  time_zone.frm      user.MYI
infosys@perldesk:/var/lib/mysql/mysql$

---

### Post by infosys on 2008-05-21
Okay, I found mysql-bin files, but not mysqld-bin files. They were located at /var/log/mysql. The strange thing is that the folder and all the files were owned by root. So, I changed the ownership to mysql, tried to start mysql up, and *bam* it worked just fine.:guitar:

Thanks for the help, giving me ideas, and pointing me in the right dirrection.:)

---

