---
title: "Rsync mysql data directory in Ubuntu"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by siddharth007 on 2014-04-01
Hi all.I am rsyncing the mysql data-directory (/var/lib/mysql) from one server(say A)  to another (say B) in realtime.The backup server comes up only if the server A goes down (say power outage,system failure,etc)

On server B,i change the directory permissions and then start the mysql server. The server is starting (on B) but my problem is am losing a substantial amount of data.I know that mysql-server on A holds the currently used 'binlog' file and so no complete rsync on 'B'. In other words i am trying to achieve HA without the mysql clustering technology.Is it possible?

---

### Post by Lars Noodén on 2014-04-01
MySQL has some built-in clustering.  You should look at that instead.

[http://dev.mysql.com/doc/refman/5.5/en/mysql-cluster.html](http://dev.mysql.com/doc/refman/5.5/en/mysql-cluster.html)

rsync can't work, unless you stop mysql for the duration of the transfer, because while you are reading a file mysql can be writing that file or a different on and they get all kinds of out of sync and or broken.  If you're going with pausing the server then mysqldump might be a better option.  But first I would look at the clustering.

---

### Post by SeijiSensei on 2014-04-01
If you don't want to go the clustering route, I second Lars's suggestion of using mysqldump. You would probably need to run two scripts, one on server A that runs mysqldump and a second script on server B that uses that file and the mysql command-line client to rebuild the database.  You could either copy the backup files over with scp or rsync, or create an NFS share on one machine and mount it on the other.

If you want to continue your current method, you would need to shutdown mysqld while the files are being copied.  If this is a server that runs 24/7, that can be difficult.  Mysqldump takes a snapshot of the database at the time of execution and can be run while the database is still online.

---

### Post by siddharth007 on 2014-04-02
I have a better option available which is of taking incremental backups every 1 hr.However,that would mean i also risk loosing data upto 1 hr (time between two incremental backups).I cannot afford to loose 1 hr of data.

---

### Post by SeijiSensei on 2014-04-02
If you really cannot afford to lose an hour's worth of data, you might want to look into more "industrial-strength" databases.  In the free-software world, [PostgreSQL]("http://www.postgresql.org/") now has a very well-developed replication tools include "[synchronous replication]("http://www.postgresql.org/docs/current/static/warm-standby.html#SYNCHRONOUS-REPLICATION")."

Of course, there's always [Oracle]("http://www,oracle.com/") ...

---

### Post by gopukrishnan on 2014-04-02
Hi,

Why you don't prefer master-master replication ?

---

### Post by SeijiSensei on 2014-04-02
By "master-master" you mean this: [http://www.howtoforge.com/mysql_master_master_replication?](http://www.howtoforge.com/mysql_master_master_replication?)

That might be a fine solution.  I don't use MySQL and don't keep up on its development.  I've been a PostgreSQL user for well over a decade.  Here's its developers take on replication strategies: [http://www.postgresql.org/docs/9.3/static/high-availability.html](http://www.postgresql.org/docs/9.3/static/high-availability.html)

I also don't manage databases where an hour of downtime is unacceptable.  For my purposes, daily backups with pg_dump and mysqldump are sufficient.  In practice PG is incredibly stable without any type of replication, so I've never bothered with that.

---

