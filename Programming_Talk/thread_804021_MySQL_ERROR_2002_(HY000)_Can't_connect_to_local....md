---
title: "MySQL ERROR 2002 (HY000): Can't connect to local..."
date: 2008-05-22
forum: Programming Talk
---

### Post by sevenearths on 2008-05-22
I upgraded to 8.04 recently and during the upgrade process Ubuntu asked me if I wanted to change one of my mysql configuration files and I must have clicked yes which is why I am in a bit of a pickle now. I currently get the following when I try to log in:

```
arthur@localhost:/etc/mysql$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

And my /etc/mysql/my.cnf is as follows:

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
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

I see that the above has the following line:

```
socket		= /var/run/mysqld/mysqld.sock
```

I looked in the directory and its empty.

If I could find where the error file is I would post it here, but I don't have a clue where it would be inside the os

I found addition help at the mysql forums (something to do with linking ?!?! Never done linking before so I'm a bit lost)

[http://forums.mysql.com/read.php?11,9689,14974#msg-14974](http://forums.mysql.com/read.php?11,9689,14974#msg-14974)

I tryed as a last resort this but it didn't work:

[http://forums.mysql.com/read.php?11,9689,131127#msg-131127](http://forums.mysql.com/read.php?11,9689,131127#msg-131127)

this might be of interest:

```
arthur@localhost:/$ ls -l /var/run/ | grep mysqld
drwxr-xr-x 2 mysql      root         40 2008-05-22 23:08 mysqld
```

and this:

```
arthur@localhost:/etc$ ls -l | grep mysql
drwxr-xr-x  3 www-data www-data   4096 2008-05-20 01:55 mysql
```

I'm not to sure if the owernership of thoses folders should be 'www-data' or 'mysql'

I did this as well:

[http://forums.mysql.com/read.php?11,9689,16554#msg-16554](http://forums.mysql.com/read.php?11,9689,16554#msg-16554)

No joy :(

Then I did this

```
arthur@localhost:/var/lib/mysql$ sudo su
root@localhost:/var/lib/mysql# mysqld
InnoDB: The log sequence number in ibdata files does not match
InnoDB: the log sequence number in the ib_logfiles!
080523  0:32:57  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
InnoDB: Last MySQL binlog file position 0 3388, file name /var/log/mysql/mysql-bin.000031
080523  0:32:57  InnoDB: Started; log sequence number 0 63353
080523  0:32:57 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'user'
```

And thought WOW! what do I do now?

An help would be gratefully appreciated

---

### Post by sevenearths on 2008-05-24
Anybody?

---

### Post by Kadrus on 2008-05-24
try ```
sudo mysqladmin password newpassword
```
type a new pass..
and then ```
sudo mysql -u root -p
```
good luck

---

### Post by sevenearths on 2008-05-26
I got the following:

```
root@localhost:/home/arthur# mysqladmin password newpassword
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
root@localhost:/home/arthur# 
```

---

### Post by dwhitney67 on 2008-05-26
This may seem silly, but have you verified that the MySQL server is running?

Verify using 'ps -ef | grep mysql'.  You should see something like:
```
$ ps -ef |grep mysql
root      5325     1  0 13:09 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     5413  5325  0 13:09 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5415  5325  0 13:09 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
```

---

### Post by sevenearths on 2008-05-27
Not to sure what I'm looking for, but this is what I get:

```
arthur@localhost:~$ ps -ef | grep mysql
arthur    6946  6928  0 22:39 pts/0    00:00:00 grep mysql
arthur@localhost:~$ 
```

---

### Post by dwhitney67 on 2008-05-27
Your mysql server is not running!

I don't have my Ubuntu system available at this moment, but I believe if you navigate into the System->Administration pull-down, there is a menu option to control "services" or something to that effect.

From there, you can start the mysql server.  Then you should be able to connect (that is, log on).

---

### Post by sevenearths on 2008-05-27
Right, I know what you are getting at. I have got a screen shot of it. You will see that it is 'off' in the screen shot.

When I loaded up services and it was enabled,

I disabled it in the hope of re-enabling it (like in the services window, under admin tools in xp) and now I can re-enable it :(

---

### Post by sevenearths on 2008-05-27
In addition I found the [following]("http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-start-mysql-in-ubuntu-340993/") in regards to starting mysql service from the command line. I tried the following:

```
sudo apt-get install mysql-server
```

Thinking that I might not have the server installed (I've done worse), and got the following in reply:

```
arthur@localhost:~$ sudo apt-get install mysql-server
[sudo] password for arthur: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
The following packages were automatically installed and are no longer required:
  pwgen libglib1.2ldbl liblzo1 libgtk1.2 libqt3-mt-mysql libfame-0.9 libpvm3
  libfftw3-3 libmyth-0.21-0 transcode ntp libtunepimp5 libifp4
  libgtk1.2-common libmyth-perl xaw3dg libnet-upnp-perl libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles Warning: found /etc/apparmor.d/force-complain/usr.sbin.mysqld, forcing complain mode
: done.
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
arthur@localhost:~$ 
```

AND every time I install new software I get the following:

---

### Post by sevenearths on 2008-05-27
On another note

```
sudo gedit /var/log/mysql.log
```

and

```
sudo gedit /var/log/mysql.err
```

both return empty files. Maybe I could try to start mysql from the command and and use a flag to get it to write to the log files.

---

### Post by sevenearths on 2008-05-27
Could be interesting:

```
arthur@localhost:~$ sudo tail /var/log/syslog
May 28 01:13:24 localhost mysqld[13982]: 080528  1:13:24  InnoDB: Started; log sequence number 0 63353
May 28 01:13:24 localhost mysqld[13982]: 080528  1:13:24 [ERROR] Fatal error: Can't open and lock privilege tables: Incorrect file format 'user'
May 28 01:13:24 localhost mysqld_safe[13993]: ended
May 28 01:13:39 localhost /etc/init.d/mysql[14143]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May 28 01:13:39 localhost /etc/init.d/mysql[14143]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May 28 01:13:39 localhost /etc/init.d/mysql[14143]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
May 28 01:13:39 localhost /etc/init.d/mysql[14143]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
May 28 01:13:39 localhost /etc/init.d/mysql[14143]: 
May 28 01:17:01 localhost /USR/SBIN/CRON[14202]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 28 01:20:01 localhost /USR/SBIN/CRON[14256]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
arthur@localhost:~$ 
```

---

### Post by dwhitney67 on 2008-05-27
I just updated my 7.10 system to 8.04 just yesterday, and my MySQL server is running like a charm.  I recall being asked the same question as you concerning the configuration file.  I accepted the replacement, since I recall that the changes I made to the original config file had no effect on what I was attempting to do at the time.

Anyhow, I can't begin to imagine what happened to your system.  I would suggest that you try to remove MySQL from your system, and then reattempt to install it.

Once MySQL is reinstalled, it should automatically start and be setup to run each time you reboot.

---

### Post by auskento on 2008-05-28
I am having many of the same issues as described here.

I have removed, cleaned, and purged mysql-server, mysql-server-5.0 and mysql-common so many times in the last few days.

I cannot even isolate what happened to kill it in the first place.

If i try and reinstall mysql-server-5.0, the base database does not even get created.  MYSQL wont use the default pid and sock file locations.

If i edit my my.cnf file and change the pid and sock file locations to /tmp/mysqld.pid and /tmp/mysqld.sock and change my data file location to anywhere other than the /var/lib/mysql, then i can get mysql to start, but its still unusable.

I cannot get any databases to function from there.

This is getting really annoying.

---

### Post by sevenearths on 2008-06-02
> **auskento said:**
> I am having many of the same issues as described here.

I have removed, cleaned, and purged mysql-server, mysql-server-5.0 and mysql-common so many times in the last few days.

I cannot even isolate what happened to kill it in the first place.

If i try and reinstall mysql-server-5.0, the base database does not even get created.  MYSQL wont use the default pid and sock file locations.

If i edit my my.cnf file and change the pid and sock file locations to /tmp/mysqld.pid and /tmp/mysqld.sock and change my data file location to anywhere other than the /var/lib/mysql, then i can get mysql to start, but its still unusable.

I cannot get any databases to function from there.

This is getting really annoying.

I read you. I've just done a mysql reinstall and I can't get it to work on startup :(

---

### Post by sevenearths on 2008-06-09
Due to time constraints I decided to do a reinstall.

It wasn't that bigger of an issue since all the data I was messing around with was test data, I was just wondering what you would do in a commercial enviroment since starting from scratch is not an option

---

### Post by geirha on 2008-06-09
Removing and even purging mysql-server, will not remove the databases. I'm not sure if these symptoms were due to corrupt databases or otherwise, but for a really clean reinstall of mysql-server, one should also remove /var/lib/mysql/ where the database-files are stored. 

This will remove configuration files and databases, so don't use it if you don't mean it:
```

sudo aptitude purge mysql-server
sudo mv /var/lib/mysql /var/lib/mysql.backup
sudo aptitude install mysql-server
# If you are confident that you don't need the old databases around:
# rm -rf /var/lib/mysql.backup/

```

---

### Post by mikeysweet on 2009-02-14
sorry to bring up an old topic but I am completely at a loss.
Not sure why, but mysql stopped working one day. i would check and see that the service is running but no response. I kept getting the error in title of this posting.

So I tried to uninstall and re-install mysql. I've pasted the results of both actions below and you can see the errors. I have no idea how to get rid of it all and start all over.

removing mysql-server:
```
root@mike:/home/mike# sudo aptitude purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  mysql-server-5.0 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 85.4MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing mysql-server-5.0 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done    
```

trying to re-install
```
root@mike:/home/mike# sudo aptitude install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  mysql-server-5.0 
The following NEW packages will be installed:
  mysql-server 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/27.4MB of archives. After unpacking 90.1kB will be used.
The following packages have unmet dependencies:
  mysql-server-5.0: Depends: libdbi-perl but it is not installable
                    Depends: mysql-client-5.0 (>= 5.0.51a-3ubuntu5.1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libdbd-mysql-perl [4.005-1 (hardy)]
libdbi-perl [1.601-1 (hardy)]
libnet-daemon-perl [0.38-1.1 (hardy)]
libplrpc-perl [0.2017-1.1 (hardy)]
libterm-readkey-perl [2.30-3ubuntu1 (hardy)]
mysql-client-5.0 [5.0.51a-3ubuntu5 (hardy)]

Downgrade the following packages:
mysql-server-5.0 [5.0.51a-3ubuntu5.1 (hardy-updates, now) -> 5.0.51a-3ubuntu5
(hardy)]

Score is -56

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be automatically installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl 
  libterm-readkey-perl mysql-client-5.0 
The following packages will be DOWNGRADED:
  mysql-server-5.0 
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl 
  libterm-readkey-perl mysql-client-5.0 mysql-server 
0 packages upgraded, 7 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 36.2MB/36.3MB of archives. After unpacking 21.0MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://dell-mini.archive.canonical.com hardy/main libnet-daemon-perl 0.38-1.1 [45.9kB]
Get:2 http://dell-mini.archive.canonical.com hardy/main libplrpc-perl 0.2017-1.1 [35.0kB]
Get:3 http://dell-mini.archive.canonical.com hardy/main libdbi-perl 1.601-1 [771kB]
Get:4 http://dell-mini.archive.canonical.com hardy/main libdbd-mysql-perl 4.005-1 [135kB]
Get:5 http://dell-mini.archive.canonical.com hardy/main mysql-server-5.0 5.0.51a-3ubuntu5 [27.4MB]
Get:6 http://dell-mini.archive.canonical.com hardy/main mysql-client-5.0 5.0.51a-3ubuntu5 [7835kB]                           
Get:7 http://dell-mini.archive.canonical.com hardy/main libterm-readkey-perl 2.30-3ubuntu1 [32.8kB]                          
Fetched 36.2MB in 10min39s (56.6kB/s)                                                                                        
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 99882 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.601-1_lpia.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_lpia.deb) ...
Selecting previously deselected package mysql-server-5.0.
Preparing to replace mysql-server-5.0 5.0.51a-3ubuntu5.1 (using .../mysql-server-5.0_5.0.51a-3ubuntu5_lpia.deb) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5_lpia.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
df: `/var/lib/mysql/.': No such file or directory
df: no file systems processed
 * /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5_lpia.deb) ...
Selecting previously deselected package libterm-readkey-perl.
Unpacking libterm-readkey-perl (from .../libterm-readkey-perl_2.30-3ubuntu1_lpia.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.1_all.deb) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5_lpia.deb
 /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libterm-readkey-perl (2.30-3ubuntu1) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
dpkg: dependency problems prevent configuration of mysql-server-5.0:
 mysql-server-5.0 depends on mysql-client-5.0 (>= 5.0.51a-3ubuntu5.1); however:
  Version of mysql-client-5.0 on system is 5.0.51a-3ubuntu5.
dpkg: error processing mysql-server-5.0 (--configure):
 dependency problems - leaving unconfigured
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5) ...
Errors were encountered while processing:
 mysql-server-5.0
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
```

Please help!! I don't care about the data, I just need mysql back.
Thanks

Forgot to mention, I'm running Ubuntu 8.04 on a Dell Mini

---

### Post by sevenearths on 2009-02-17
try the following:

```
sudo chmod 775 /var/lib/mysql
```

It works for a lot of people

---

### Post by mikeysweet on 2009-02-17
Sevenearths - I tried that and nothing still

I've searched for about a week online,trying any and every command and no success.
here are just a few of the commands I've run and all of them end in failure to complete their intention:

```
sudo apt-get --purge remove mysql-server
sudo apt-get --purge remove mysql-server
sudo apt-get install --reinstall mysql-server-5.0
sudo dpkg -P --force-all mysql-server-5.0

```

Here is what I get when I list all package with mysql
```
root@mike:/home/mike# dpkg -l | grep mysql
ii  libapache2-mod-auth-mysql                  4.3.9-4                                            Apache 2 module for MySQL authentication
ii  libdbd-mysql-perl                          4.005-1                                            A Perl5 database interface to the MySQL data
ii  libmysqlclient15off                        5.0.51a-3ubuntu5.1                                 MySQL database client library
ii  mysql-admin                                5.0~rc12-2ubuntu1                                  GUI tool for intuitive MySQL administration
ii  mysql-client-5.0                           5.0.51a-3ubuntu5.1                                 MySQL database client binaries
ii  mysql-common                               5.0.51a-3ubuntu5.1                                 MySQL database common files
ii  mysql-gui-tools-common                     5.0~rc12-2ubuntu1                                  Architecture independent files for MySQL GUI
pFR mysql-server-5.0                           5.0.51a-3ubuntu5.1                                 MySQL database server binaries
ii  php5-mysql                                 5.2.4-2ubuntu5.3                                   MySQL module for php5

```

What does pFR before mysql-server-5.0 mean? Can that be a clue??? I know i'm clueless :(

Any help is greatly appreciated!

---

### Post by sevenearths on 2009-02-17
What happens when you type the following:

```
ps -ef |grep mysql
```

---

### Post by bfyrth on 2009-03-20
Yes AJ you know you shouldnt be allowed anywhere near code to start with

Ben

---

### Post by mcwafflestix on 2009-03-20
I think I've figured this one out; I was trying to install mysql on my machine.  The machine is a Dell Mini 9 (yes, I know) with the original 4GB SSD (yes, I know, again).

I kept getting this message:
```

 subprocess pre-removal script returned error exit status 1
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable

```

I eventually managed to get this result:
```

 * /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!

```
So I'm going to try to free up some space and complete the removal.  For what it's worth, I am getting a 32GB SSD to install in this machine, which should give me plenty of space; and yeah, I know this isn't at ALL a normal use for a machine this tiny, but I just want to do some light development on the go, and it's the perfect form factor for it.  And for what it's worth, Eclipse runs beautifully on it!

---

### Post by sevenearths on 2009-03-23
> **bfyrth said:**
> Yes AJ you know you shouldnt be allowed anywhere near code to start with

Ben

AHHHHH!!! 'First cup of Ubuntu' isn't that sweet!

---

### Post by ardnet on 2009-04-25
Hi All, 

I'm new Ubuntu user, and also having the same problem like this.
And I've been read through all this post, and just wanna inform you guys that the conclusion is because..... the disk is full.

Try to restart mysql and it will tell you the problem,
by using this command: sudo /etc/init.d/mysql restart
And after that, I got this message:
  * /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!

Then I removed any file that I think is useless to save up some space, then restart mysql again... Voila!!! Works for me :-)

Thanks

---

### Post by susenj on 2009-09-14
Thank you so much:popcorn:. When i opened Services from the administration , i got that Mysql server is checked by deafult. i unchecked it amd then checked it once again. Wow..it was running. Everything is peachy. :) Thanks:):P
> **dwhitney67 said:**
> Your mysql server is not running!

I don't have my Ubuntu system available at this moment, but I believe if you navigate into the System->Administration pull-down, there is a menu option to control "services" or something to that effect.

From there, you can start the mysql server.  Then you should be able to connect (that is, log on).
[http://susenj.wordpress.com]("http://susenj.wordpress.com/")

---

### Post by acho on 2009-10-26
Yup :guitar:

I had the same problem before. but re-installing fix the problem....thx.

---

### Post by Fitch on 2009-11-06
Ubuntu 9.10 doesn't have "services"
It's got the following:
   Computer Janitor
   Disk Utility
   Hardware Drivers
   Language Support
   Logfile Viewer
   Login Screen
   Mount Manager
   Netwrk
   Network Tools
   Printing
   Samba
   Software Sources
   Synaptic Package Manager
   System Monitoring
   System Testing
   Time and Date
   Update Manager
   USB Startup Disk Creator
   User Groups

So now what?

I was trying to install ZoneMinder and after about a week, the aforementioned error is all I get.
And Yes mysql doesn't run on startup.

---

### Post by jameshogan on 2009-11-07
Hey Guys,

Yup, I've go the same problem, having just upgraded from 9.04 to to 9.10.  I've gotta say, with 9.10, I've had nothing but hassles with this upgrade!  Too soon?

I'm trying to figure out where its all going wrong too.  From here: [http://theos.in/desktop-linux/tip-that-matters/how-do-i-restart-mysql-server/](http://theos.in/desktop-linux/tip-that-matters/how-do-i-restart-mysql-server/)
I'm finding that starting mysql server isn't happening.  Same story as above:  I've installed, reinstalled, completely reinstalled, chmoded and everything.  No joy.  

I'll keep trying to nut it out and keep an eye here for answers, or (fingers crossed) to post some solutions.

---

### Post by grantbuntu on 2009-11-15
Just confirming that this is a problem.  Everything stopped working after the upgrade to karmic.  Uninstalling and reinstalling worked until I rebooted.  Anyone know the answers?

---

### Post by rugger0 on 2009-11-17
Deleted by author. Opening new thread since this one starts with SOLVED and talks about 8.04

---

### Post by cftaupitz on 2009-11-20
I have the same problem it won't even start manually help!!!!

---

### Post by soumyamandi on 2009-12-30
this error occurs because of incomplete installation..
follow the procedure described here.. 

[http://tolearnfree.blogspot.com/2009/11/how-to-install-apache2-php5-mysql-and.html](http://tolearnfree.blogspot.com/2009/11/how-to-install-apache2-php5-mysql-and.html)

enjoy :guitar::guitar::guitar::guitar:

---

### Post by gurukatre on 2010-02-03
hi 

i had also same problem. I just open synaptic package manager and removed the phpmyadmin and reinstalled it by synaptic package manager and also restart my pc 

and logged in by root user and switch to another one i found it working in both root and normal user 

thanks

---

### Post by zenecan on 2010-03-03
There's a lot of talk of reinstalling mysql & other packages - my experience in resolving this issue did not involve reinstalling / removing anything - of-course the cause of me getting this error message could be different to your cause of getting the same error message - anyway this was my experience - hope it helps some one:

  
Everything was OK for months, with the machine being restarted multiple times ... until I ran this line to shutdown the mysql server
438  mysqladmin -hlocalhost -uroot -p<password> shutdown;

  439  mysqladmin -hlocalhost -uroot -p<password>;

got this error : ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
& from then on keep getting this error plus the can't find /var/run/mysqld/mysqld.sock - which yes did not exist
-- below your see that I created an empty mysqld.sock file and gave it 775 permissions - may be this helped.
-- then essentially sudo /etc/init.d/mysql restart 
-- worked - these all my trial & error commands from my command history - I've hidden the p/w with <password> of-course
-- 

  440  status
  441  mysqladmin -hlocalhost -uroot -p<password> status;
  442  mysqladmin -hlocalhost -uroot -p<password> ping;
  443  mysqladmin -hlocalhost -uroot -p<password> start;
  444  mysql -hlocalhost -uroot -p<password>;
got this error : ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
  445  /etc/rc.d/init.d/mysqld start
  446  service mysql start
  447  mysql -hlocalhost -uroot -p<password>
  448  mysql -hlocalhost -uroot -p<password>;
  449  /etc/rc.d/init.d/mysqld start
  450  mysqladmin -hlocalhost -uroot -p<password> start;
  451  /etc/init.d/mysql start
  452  mysql -hlocalhost -uroot -p<password>
  453  cd var/run/mysqld
  454  cd /var/run/mysqld
  455  ls -l
  456  ls -alF

created mysqld.sock file:

  457  touch mysqld.sock
  458  sudo touch mysqld.sock
  459  ls -l
  460  mysql -hlocalhost -uroot -p<password>
  461  mysqladmin -hlocalhost -uroot -p<password> shutdown;
  462  ls -l
  463  /etc/init.d/mysql start
  464  mysql -hlocalhost -uroot -p<password>
  465  sudo chmod 775 /var/lib/mysql
  466  mysql -hlocalhost -uroot -p<password>
still getting this error all the time : ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)
  467  sudo chmod 775 /var/run/mysqld ****** may be this helped ? 
  468  mysql -hlocalhost -uroot -p<password>
  469  ls -alF
  470  sudo chmod 775 /var/run/mysqld/mysqld.sock
  471  mysql -hlocalhost -uroot -p<password>
still got this error : ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)
  472  sudo /etc/init.d/mysql restart  *******************  this line seemed to sort it all out - ie restarting the mysql service ***
  473  mysql -hlocalhost -uroot -p<password>
************ this last line worked fine - now everything is back to normal - I am no longer getting any errors just like I have not done for months before I today ran
mysqladmin -hlocalhost -uroot -p<password> shutdown; 


OK asking for punishment I am going to run 
mysqladmin -hlocalhost -uroot -p<password> shutdown; 
again (must be mad).

yes - I get the same problem again - so now to fix it...
yep fixed it ... - this is my command line history below:

vince@vince-laptop:~$ mysqladmin -hlocalhost -uroot -p<password> shutdown
vince@vince-laptop:~$ mysql -hlocalhost -uroot -p<password>
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
vince@vince-laptop:~$ sudo /etc/init.d/mysql restart
[sudo] password for vince: 
 * Stopping MySQL database server mysqld                                                                              [ OK ] 
 * Starting MySQL database server mysqld                                                                              [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
vince@vince-laptop:~$ mysql -hlocalhost -uroot -p<password>
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 52
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

so all OK & working fine again - it looks like

vince@vince-laptop:~$ mysqladmin -hlocalhost -uroot -p<password> shutdown

is not shutting down cleanly

and 

vince@vince-laptop:~$ sudo /etc/init.d/mysql restart

fixes this.

Hope this helps someone!

---

### Post by yiming Lu on 2010-06-03
maybe you can try replace the current my.cnf file with the previous version, I think your older one you used before upgrade should be still in the same directory with another name.

---

### Post by djst on 2010-08-11
> **sevenearths said:**
> In addition I found the [following]("http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-start-mysql-in-ubuntu-340993/") in regards to starting mysql service from the command line. I tried the following:

```
sudo apt-get install mysql-server
```

Thinking that I might not have the server installed (I've done worse

I know this is an old thread but I got this same error message after upgrading my Ubuntu server from 9.10 to 10.4 and running sudo apt-get install mysql-server solved the problem for me.

No idea why the Ubuntu upgrading tool would leave the server in a state of no mysql server, but I'm glad it was an easy fix.

---

### Post by i_ReEm on 2011-02-08
> **djst said:**
> I know this is an old thread but I got this same error message after upgrading my Ubuntu server from 9.10 to 10.4 and running sudo apt-get install mysql-server solved the problem for me.

No idea why the Ubuntu upgrading tool would leave the server in a state of no mysql server, but I'm glad it was an easy fix.

I got the same error when I installed phpmyadmin in my new Ubuntu 10.10 without installing mysql-server manually (usually it installs mysql-server by default when installing phpmyadmin)
so the cause of the error *for me* was not complete installation and by installing mysql-server everything got OK.

---

### Post by upallnight on 2011-02-16
I'm getting millions of these messages in dmesg log:

[60253.081098] type=1400 audit(1297875316.964:1952): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=28453 comm="apparmor_parser"

And I can't connect to mysql-server through localhost, 127.0.0.1, or the sockets. I checked for sockets at /temp/mysqld.sock and /var/run/mysqld/mysqld.sock while mysql-server was running but both don't exist.

I also have tried purging mysql-* packages and reinstalling, but when entering my root password while installing mysql-server-5.1 I get an error message saying the password was not able to be set (assuming its because the server isn't connectable).

---

### Post by DegreesCelsius on 2011-02-16
Is there a program equivalent to the windows program "WAMP Server"?
if there is, just remove the mysql installation and phpmyadmin and install that instead. It contains everything you need for a server.

---

### Post by theGiallo on 2011-03-03
I had that problem and I tried to reinstall: nothing.

to correctly reinstall all use these commands, then it should work.

```
sudo apt-get remove mysql-server libapache2-mod-auth-mysql php5-mysql
sudo apt-get autoremove
sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
```

---

### Post by Scifer on 2011-03-06
> **ardnet said:**
> Hi All, 

I'm new Ubuntu user, and also having the same problem like this.
And I've been read through all this post, and just wanna inform you guys that the conclusion is because..... the disk is full.

Try to restart mysql and it will tell you the problem,
by using this command: sudo /etc/init.d/mysql restart
And after that, I got this message:
  * /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!

Then I removed any file that I think is useless to save up some space, then restart mysql again... Voila!!! Works for me :-)

Thanks

Ha hahahah! For hours reading forums and this was the problem. How stupid I am!

---

### Post by ahmed.elbougha on 2011-04-17
Hello guys,

actually the problem could happened due to permissions also.

I checked the owners of the directory "/var/run/mysqld" using 

#ls -lah 

and I got the following results:

drwxr-xr-x  2 mysql root  40 2011-04-17 07:42

so I changed the owners to be mysql user and mysql group, using:
#chown mysql.mysql . -R

then I restarted mysql and it worked fine for me.

---

### Post by konjeng on 2011-05-12
same thing happened to me and i tried many things but it didn't work at last it worked after typing the following command:

apt-get install mysql-server
mysql_secure_installation
mysql -u root -p



you may chech the following link for details:
[http://library.linode.com/lamp-guides/ubuntu-10.04-lucid](http://library.linode.com/lamp-guides/ubuntu-10.04-lucid)

---

### Post by mikefreeman on 2011-07-31
Ok, I've gone through EVERY single suggestion and linked tutorial on this post, as well as numerous other posts I've Googled, and after all that, I still get:

```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
```Ack!!!!! I want to set up MythTV as a DVB tuner/recorder backend for XBMC, and it requires mysql-server. It gives me this error (as does anything else I try to do with mysql-server) and says "No UPnP". I am about to chuck my laptop out of my 2nd-story window!!!

---

### Post by CriticalBandwidth on 2011-10-27
Hey. I was having a similar error when trying to access mysql at the command line. I look in the error.log (/var/log/mysql/error.log) and saw that I was having the following issue:
```

111027  6:20:29 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
111027  6:20:29 [ERROR] Do you already have another mysqld server running on port: 3306 ?
111027  6:20:29 [ERROR] Aborting

```

I went into the my.cnf file (/etc/mysql/my.cnf) and found this line:
```

bind-address           = 192.168.1.121

``` 

I'm not sure why it was bound to this IP address but it might have something to do with the configuration of my VM. I commented this line out and restarted mysql (service mysql start) and it works again.

Hope that helps someone!

---

### Post by walli on 2011-11-18
Hi, i have the error
SQLSTATE[HY000] [2002] Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) linux
after upgrading ubuntu from 11.04 to 11.10

The problem was caused by the apparmor daemon.

I just changed the lines in /etc/apparmor.d/usr.sbin.mysqld

-  /var/run/mysqld/mysqld.pid w,
-  /var/run/mysqld/mysqld.sock w,

to

+  /{,var/}run/mysqld/mysqld.pid w,
+  /{,var/}run/mysqld/mysqld.sock w,

and restarted appamor daemnon with 
/etc/init.d/appamor restart

After restarting mysql daemon everthing works fine
/etc/init.d/mysql restart

Perhapps it help you

---

### Post by vitalux on 2011-11-23
[COLOR=#333333][FONT=arial]I [/FONT][/COLOR][COLOR=#333333][FONT=arial]had the same[/FONT][/COLOR][COLOR=#333333][FONT=arial] problem:

[I]Nov 23 17:54:45 server /etc/init.d/mysql[13117]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Nov 23 17:54:45 server /etc/init.d/mysql[13117]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

[/I][/FONT][/COLOR][COLOR=#333333][FONT=arial]Finally, I[/FONT][/COLOR][COLOR=#333333][FONT=arial] note that in [/FONT][/COLOR][COLOR=#333333][FONT=arial]the file /[/FONT][/COLOR][COLOR=#333333][FONT=arial]etc/[/FONT][/COLOR][COLOR=#333333][FONT=arial]mysql/[/FONT][/COLOR][COLOR=#333333][FONT=arial]my.cnf [/FONT][/COLOR][COLOR=#333333][FONT=arial]specified [/FONT][/COLOR][COLOR=#333333][FONT=arial]IP [/FONT][/COLOR][COLOR=#333333][FONT=arial]was wrong[/FONT][/COLOR][COLOR=#333333][FONT=arial] because[/FONT][/COLOR][COLOR=#333333][FONT=arial] I had [/FONT][/COLOR][COLOR=#333333][FONT=arial]changed[/FONT][/COLOR][COLOR=#333333][FONT=arial] the IP of the [/FONT][/COLOR][COLOR=#333333][FONT=arial]server host [/FONT][/COLOR][COLOR=#333333][FONT=arial]recently.[/FONT][/COLOR]

---

### Post by arjun.mehta on 2011-12-17
Thank you so much walli!! After upgrading to 11.10 I had the same issue... Thankfully I found your post or I could have spent hours trying to figure it out.

---

### Post by sidewinder01 on 2012-04-15
Hi to all! I also had such problem:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

The solution was to change the bind-adress to 127.0.0.1 in /etc/mysql/my.cnf

Thanks to CriticalBandwidth for idea (#45)!

---

### Post by slavik on 2012-04-16
too old to live.

---

