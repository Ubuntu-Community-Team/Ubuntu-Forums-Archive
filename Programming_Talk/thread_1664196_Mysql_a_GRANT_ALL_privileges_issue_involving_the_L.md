---
title: "Mysql a GRANT ALL privileges issue involving the LAN"
date: 2011-01-10
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-10
>  Con1.Execute "GRANT ALL PRIVILEGES ON *.* TO " & "New" & "@'%' IDENTIFIED BY '" & "New" & "' WITH GRANT OPTION"
       


>   frmLogon.cnConnection.Execute "GRANT ALL PRIVILEGES ON *.* TO " & frmLogon.rsusertable!MYUser & "@'%' IDENTIFIED BY '" & PassWordy & "' WITH GRANT OPTION"
        frmLogon.cnConnection.Execute "GRANT ALL PRIVILEGES ON *.* TO " & frmLogon.rsusertable!MYUser & "@localhost IDENTIFIED BY '" & PassWordy & "' WITH GRANT OPTION"
      

for some reason, when running mysql on XP, there is no problem granting priviliges to users on the LAN, using the code from above.
No ip addresses have to be used in the statement.
On ubuntu, I am having to manually grant users privileges.  The program is programmed to do this

for example I am having to do this by way of the query analyzer, etc...
> GRANT ALL ON *.* TO 'username'@'192.168.1.%' identified by 'userpassword';

Do you understand what I am trying to explain?
I was wondering if something to do with the my.cnf?
Any easy way out?

---

### Post by sdowney717 on 2011-01-10
here is a snapshot of the server


frmLogon.rsusertable!MYUser & "@'%'

'username'@'192.168.1.%'

the only difference I see is using 192.168.1.% versus %

could it be %.%.%.% ??

---

### Post by sdowney717 on 2011-01-10
for example this is sent to the server when adding a guy named george with password sdls. That works fine on the LAN using a windows based version of mysql, but not for a ubuntu based version of mysql

> GRANT ALL PRIVILEGES ON *.* TO george@'%' IDENTIFIED BY 'sdls' WITH GRANT OPTION
GRANT ALL PRIVILEGES ON *.* TO george@localhost IDENTIFIED BY 'sdls' WITH GRANT OPTION

---

### Post by sdowney717 on 2011-01-10
well, it could be that the user logged in off the lan does not have grant privileges!
at least the query browser shows grants are off  for various hosts
Help, just got to be too easy!
so when root is logged in remotely, grant privileges are off, how is this changed?

is it perhaps I am just going to have to run from localhost to create grants?
seems like it.

---

### Post by tatterdemalion on 2011-01-11
Did you try to change this line:

```
bind-address        = 127.0.0.1
```
to
```
bind-address        = servers_local_ip
```

in the /etc/mysql/my.cnf file?

with these settings i can GRANT ALL PRIVILEGES to anyone on the local network. 

By the way if you want to reach your databases over internet you have to specify your out ip address. But this is not so secure.  

Hope it helps.

---

### Post by sdowney717 on 2011-01-11
hi thanks, but when I put that bind line in, mysql does not start.
one shot shows how it is not started and other shows it runs

here is my.cnf when it runs, notice the bind field
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
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 192.168.1.101
#bind-address            = servers_local_ip
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

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
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

---

### Post by sdowney717 on 2011-01-11
imagine this situation.
you write a program runs in XP that uses a mysql server.
the server is hosted on a pc in the building far away.
your program needs to be able to execute grant privileges to new users remotely.

I seem to recall this was working when the distant server is running an XP OS. at least we did not have any issues creating new users to log in.

Now, I notice if I use an ubuntu mysql database remotely using this same XP program, I can not create new users because I cant execute a grant privileges statement remotely.

 I can walk to the far away server, 
log in using mysql-query-browser
execute the grant statement locally on the machine

then walk back to the XP client and login ok.

so any ideas or is it a bust?

the query-browser shows the the grant-privileges are not granted for remote users of the server, only local users even if they are the same.

---

### Post by sdowney717 on 2011-01-11
answer is you cant do it. and this is by design.
(unless you know of a way)
perhaps this is something that has changed over the years as I have steadily migrated databases from mysql 3 to now 5.5 and the users were already granted!

[http://forums.mysql.com/read.php?10,71718,72191#msg-72191](http://forums.mysql.com/read.php?10,71718,72191#msg-72191)
> A quick test on my 5.0 system shows that the 'grant' command "grant all on *.* to root@'B' identified by 'mypw'" not only adds the record to mysql.**user but grants it every single privilege except Grant privilege, and this omission is by design.**

bolded text, this is it right here

HOWEVER THIS IS NOT TRUE!!!

---

### Post by sdowney717 on 2011-01-11
GRANT ALL ON *.* TO 'terror'@'%' identified by 'terror'; 

GRANT ALL ON *.* TO george@'%' IDENTIFIED BY 'sdls' WITH GRANT OPTION;

well for some reason it is sort of working?
I can now login and also the grants are showing up with Grant-priv set to Y

---

### Post by sdowney717 on 2011-01-11
HAHA it is working!
I created a user name of fred and fred has all privilieges includint the Grant_priv
and did it remotely from the XP program to the ubuntu mysql server.

I dont know why some of these users in mysql database have 192.168.1.%, but if they do delete them since they dont get Grant_priv, BUT if they are identified with just '%' then they do get the Grant_priv set to Y

run 
delete from user where user.user = 'whatevernameyouwanttodelete';
then redo the grant with

GRANT ALL ON *.* TO username@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;

---

### Post by sdowney717 on 2011-01-11
the problem for me was and is this.

when you create an instance of the server, say you give user name 'root'

'root' will then be put into the user table of mysql database in 2 ways
one as localhost with Grant_priv set to Y 
the other as 192.168.1.% with Grant_priv set to N

My program logs into the databsee using 'root' and is seen as 192.168.1.% to the server.

HOW do you or can you, set that root to % from the get go?? maybe you cant.

So when my program remotely was connecting to the server with 'root' I did not have any grant privileges. So I had to create at least one user that did on the data server machine locally, then use that name to login remotely and setup up other new users I wished, since my program was connected to a user remotely with grant privileges it works.

so it requires some one to still goto the server and setup at least one user with remote grant privileges or it will not ever work. I suppose you can live with that, but I dont recall this being an issue with windows, but who knows anymore.

I quess I need to put an error message into the program explaining this issue or I and anyone else will ever remember how to make it work.

---

