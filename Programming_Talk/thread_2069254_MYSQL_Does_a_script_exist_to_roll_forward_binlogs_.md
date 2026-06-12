---
title: "MYSQL: Does a script exist to roll forward binlogs after a backup restore"
date: 2012-10-10
forum: Programming Talk
---

### Post by shumifan50 on 2012-10-10
I have found many suggestions on the web to take mysqldump backups of a database, many of which will work with some caveats. However, I have found nothing that helps with rolling forward a database from the point at which one of these backups are restored with the most recent updates(rolled forward) using the log_bin files. The Mysql website has an overview of how to do it, but it is very convoluted and not something I would like to go through when my database is down.
Do any such scripts exist and if so where can I find one?

Please note that I am not just after applying the backup, that is easy, I am more interested in the roll forward.

I understand the following to be the process to enable roll forward. Any input from mysql experts will be greatly appreciated.

[COLOR="#FF0000"]ENSURE that mysql is started with log_bin enabled[/COLOR]

As much as I can work out the following steps are required to keep track of what is going on:
1. To make sure you have a consistent backup(using mysqldump), stop mysql.
2. Archive all the existing log_bin files(default mysql-bin.*) to an archive directory and also copy the most recent mysqldump files to that directory(in case you need to go back more than one mysqldump).
3. Take the mysqldump to current dump directory.
4. Restart mysql server.

If you need to restore mysql:
1. Stop mysql if not already stopped to guarantee consistency.
2. Restore the mysqldump backup in the current dump directory (assuming you dont need to go back further).
3. Using mysqlbinlog do: mysqlbinlog <log1> <log2> <log3> ..... | mysql -u<user> -p
Mysql recommend processing the logfiles in one instance of mysqlbinlog to ensure consistency. <log1>etc are the logs in the current log directory(or in the same as the mysqldump file restored). If a previous(older) mysqldump is restored, all logfiles in all subsequent archive directories have to be processed as well.
4. Restart mysql

Any comments welcome.

---

### Post by shumifan50 on 2012-10-14
If nobody has a script, any comments on how to go about taking/restoring backups and log_bin files will be appreciated. Also comments on the outlined procedure.
Surely nobody does just restore dump recovery - or do they?

This is a very important part of implementing a system that uses mysql, so I am very surprised/disappointed that there are no replies.

I have read the mysql documentation, but need to be sure that what I propose will work correctly.

---

### Post by mevun on 2012-10-14
Well, the likelihood of finding a mysql proficient expert in Ubuntu Forums isn't that great.  You should probably try asking your question on the official mysql forums?  You might need an Oracle userid/login, but those are free for sign-up.

Speaking naively, it would not surprise me if someone suggests a different backup strategy.  It may very well be that using mysqldump and then using bin logs to move forward may not be a recommended way because of the convoluted steps required.  That is just conjecture on my side.

As you may know, another way of "backing up" involve replication to another database.  There you need a "failover/failback" strategy.

---

### Post by shumifan50 on 2012-10-15
@mevun:
Thanks for the reply.
After digging around the mysql forum, I found a hot backup utility from Percona called xtrabackup. However, I am somewhat wary of it as it reads mysql files directly and it is possible to end up in a situation where it lags behind the general mysql releases. In the meantime I have written a bash script that handles backup/recovery and I am testing it at the moment. I need to reduce the mysql downtime some more by allowing the dumping of binary logs only for incremental backups. This should only require a glitch in mysql uptime, but recovery times will be longer; however an offline database can be brought forward with the binary logs to reduce final recovery time.
Replication seems no good for recovery as it can lag far behind the live server.

mysqldump seems the only guaranteed dump that can recover accross database corruption. Having seen the RBS disaster earlier this year, I am also thinking of going back to the antiquated idea of writing an input transaction log allowing applications to reprocess transactions.

Note: I posted here out of desperation as there is no response on the mysql forums. I also think it might be of general interest to Ubuntu users.

---

