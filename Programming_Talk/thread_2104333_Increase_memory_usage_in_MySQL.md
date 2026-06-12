---
title: "Increase memory usage in MySQL"
date: 2013-01-12
forum: Programming Talk
---

### Post by icaka92 on 2013-01-12
I have a Ubuntu Linux 12.04.1 server with 4GB and Intel(R) Pentium(R) CPU        G6950  @ 2.80GHz, 2 cores CPU. My server use about 1.5 GB RAM and 100 of CPU. In htop i see that mysql use the cpu. How can i set mysql to use more memory and less cpu, because my site load really slow when the cpu is 100% used. I read that i should increase key_buffer_size, sort_buffer, read_buffer and table_cache, but i don't know what value to set. What is optimal mysql settings for my server?

This is my mysql settings now:

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket        = /var/run/mysqld/mysqld.sock
nice        = 0

[mysqld]
#
# * Basic Settings
#
user        = mysql
pid-file    = /var/run/mysqld/mysqld.pid
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
lc-messages-dir    = /usr/share/mysql
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address        = 127.0.0.1
#
# * Fine Tuning
#
key_buffer        = 16M
max_allowed_packet    = 16M
thread_stack        = 192K
thread_cache_size       = 8
interactive_timeout=5
wait_timeout=5
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
max_connections        = 500
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit    = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1
#
# Error logging goes to syslog due to /etc/mysql/conf.d/mysqld_safe_syslog.cnf.
#
# Here you can see queries with especially long duration
#log_slow_queries    = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id        = 1
#log_bin            = /var/log/mysql/mysql-bin.log
expire_logs_days    = 10
max_binlog_size         = 100M
#binlog_do_db        = include_database_name
#binlog_ignore_db    = include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet    = 16M

[mysql]
#no-auto-rehash    # faster start of mysql but no tab completition

[isamchk]
key_buffer        = 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

```

---

### Post by icaka92 on 2013-01-17
No ideas ?

---

### Post by greenpeace on 2013-01-17
The RAM and CPU aren't interchangeable like that, the best thing for you to do would be to check which queries are making your MySQL server run so slowly.

Check the slow queries log [1] on your server to see if you can find the queries that are causing the problems.

Aside from that, restart the MySQL server.  You should have more than enough power on your server to run websites (depending on the complexity of the sites of course).

cheers

[1] [http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html](http://dev.mysql.com/doc/refman/5.1/en/slow-query-log.html)

---

### Post by icaka92 on 2013-01-20
Hello. Thanks for answer. I check slow queries log, but there are nothing strange. There is something interesting. On htop load average is about 3-4 and sometimes from something it goes up to 20-30 and the site load very very slow. From what can be this ? How can i check what process make my load average up ?

Thanks !

---

### Post by greenpeace on 2013-01-21
> **icaka92 said:**
> On htop load average is about 3-4 and sometimes from something it goes up to 20-30 and the site load very very slow. From what can be this ? How can i check what process make my load average up ?

That's a very high load average, and perhaps there's no issue with your MySQL installation! 

Anything over 1 means that you have processes waiting [1], and **htop** (or **top**) should show you the processes that are taking up your resources.

In htop press F6 to sort the processes, and select CPU% or MEM% to order the processes in terms of how much they are using the CPU or RAM (respectively).

That should indicate the processes that are being particularly demanding of your resources.  Check the column where the percentage of usage of CPU/MEM is shown.


If you don't find anything using CPU or RAM heavily, then use the command **iotop**[2] to see your file system queue, as it is possible that you have a bottleneck there.

Good luck!

[1] [http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages)
[2] [http://lifehacker.com/5291974/iotop-tells-you-what-process-is-grinding-your-hard-drive](http://lifehacker.com/5291974/iotop-tells-you-what-process-is-grinding-your-hard-drive)

---

### Post by slickymaster on 2013-01-21
If you have lots of RAM free one way is to get as much of your databases in memory as possible, this will free up I/O and in turn reduce CPU usage. You can achieve it by increasing **tmp_table_size** and **max_heap_table_size** values.

---

### Post by icaka92 on 2013-01-21
Hello. Thanks for answers. The strange is that the site work with 2-3-4 load average and suddenly the load average goes up to 25 and more. I check in htop and mysql use most cpu and memory. I check my **tmp_table_size** and **max_heap_table_size**.

Yes i have about 2GB free ram and. How much i should increase thaat value to correct the problem, but I am not sure that this will help, because load average is okay and suddenly goes up.

tmp_table_size: 268435456
max_heap_table_size: 268435456

---

### Post by slickymaster on 2013-01-21
Before going and changing those values, try something, use "mysqladmin processlist" so you can see specifically which databases/tables/queries are causing the load.
The majority of MySQL performance gains are through optimizing code rather than the server.

---

### Post by hydn79 on 2013-01-21
This is a much deeper topic than you may be aware. You can't just increase a few parameters as it was. Also, so many admins have the false belief that with MySQL larger is always better. Its not.

You should look at MySQL's run time stats after things have been running for at least 24 hours.

If you don't know how to do this using the command line you can use free tools such as: 

MySQL Tuner - [http://mysqltuner.pl](http://mysqltuner.pl)
Tuning Primer: [http://www.day32.com/MySQL/](http://www.day32.com/MySQL/)

Now a lot of people use those tools and still have no clue. Feel free to PM me if you need more detailed help.

---

