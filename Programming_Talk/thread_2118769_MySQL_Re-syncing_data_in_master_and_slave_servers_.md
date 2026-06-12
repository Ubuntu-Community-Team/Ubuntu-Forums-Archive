---
title: "MySQL: Re-syncing data in master and slave servers after a broken replication"
date: 2013-02-22
forum: Programming Talk
---

### Post by siddharth007 on 2013-02-22
Hi everyone.We are managing an OLTP system.We are doing master-slave  replication on MySQL server 5.5.24.We are yet to go live.The replication  has been setup and is working.I would like to know in case the  replication breaks,how can i fix it and re-sync data between the master  and the slave server.We don't want to take data dumps and put it from  master to slave.Please suggest a proper way to do it.I believe there  might be better ways than taking dumps and importing it.Thanx.

---

### Post by dazman19 on 2013-02-22
you have statement based and row based replication.

Have a read on it. [http://dev.mysql.com/doc/refman/5.1/en/replication-sbr-rbr.html](http://dev.mysql.com/doc/refman/5.1/en/replication-sbr-rbr.html)

I suggest you use row based if possible. we have had problems with statement based once we moved to row based it barely ever broke.

a few things i suggest you do.

1) Make sure the max allowed packet size on your slave is bigger than on your master.
2) make sure you keep the log files for say 14 days, so if the replication breaks because of a machine restart etc then it will automatically catch up.
3) Dont load triggers on the slave when using row based.

if you pull a copy off the slave to use as a backup remember to load the triggers again.

unfortunately taking a mysqldump and recording the binary log positions is the only way to do it although using ssd -C/sed (for replacements) and some tricky mysqldump switches and some fancy bash scripting you could make a script to lock, take the log positions, take the dump, remove the lock. and load the data into the slave it will take a while to perfect but can be done.

I use mysql 5.1.something. Not 5.5

---

