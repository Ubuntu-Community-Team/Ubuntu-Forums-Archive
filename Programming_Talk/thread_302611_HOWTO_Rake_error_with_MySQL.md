---
title: "HOWTO: Rake error with MySQL"
date: 2006-11-18
forum: Programming Talk
---

### Post by beaudrm2 on 2006-11-18
Hi,

I doing some Ruby on Rails development with the latest Ubuntu. I've got MySQL installed (version 5.x) and recently ran into some issues with trying to do a  "rake db:migrate". MySQL was spitting out the the connectiong was dropping.

Here's the message I was getting:

rake aborted!
Mysql::Error: Lost connection to MySQL server during query: SELECT version FROM schema_info

Anyhow, I found a great solution at the link below:

[http://www.afeared.org/?comment,343](http://www.afeared.org/?comment,343)

And it fixed my problem (see below for the output of the above mentioned steps).

Hope this works out for you too.

Cheers,

Marc

$ sudo apt-get install mysql-client libmysqlclient14-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmysqlclient14
The following NEW packages will be installed:
  libmysqlclient14 libmysqlclient14-dev mysql-client
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6476kB of archives.
After unpacking 17.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe libmysqlclient14 4.1.15-1ubuntu5 [1207kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe libmysqlclient14-dev 4.1.15-1ubuntu5 [5229kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main mysql-client 5.0.24a-9 [39.5kB]   
Fetched 6476kB in 11s (566kB/s)                                                
Selecting previously deselected package libmysqlclient14.
(Reading database ... 97569 files and directories currently installed.)
Unpacking libmysqlclient14 (from .../libmysqlclient14_4.1.15-1ubuntu5_i386.deb) ...
Selecting previously deselected package libmysqlclient14-dev.
Unpacking libmysqlclient14-dev (from .../libmysqlclient14-dev_4.1.15-1ubuntu5_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.24a-9_all.deb) ...
Setting up libmysqlclient14 (4.1.15-1ubuntu5) ...

Setting up libmysqlclient14-dev (4.1.15-1ubuntu5) ...
Setting up mysql-client (5.0.24a-9) ...

$ gem install mysql
Need to update 46 gems from [http://gems.rubyforge.org](http://gems.rubyforge.org)
..............................................
complete
Select which gem to install for your platform (i686-linux)
 1. mysql 2.7.1 (mswin32)
 2. mysql 2.7 (ruby)
 3. mysql 2.6 (ruby)
 4. mysql 2.5.1 (ruby)
 5. Cancel installation
> 2
Building native extensions.  This could take a while...
ruby extconf.rb install mysql
checking for mysql_query() in -lmysqlclient... yes
checking for mysql_ssl_set()... yes
checking for mysql.h... no
checking for mysql/mysql.h... yes
creating Makefile

make
gcc -I. -I. -I/usr/local/lib/ruby/1.8/i686-linux -I. -DHAVE_MYSQL_SSL_SET -DHAVE_MYSQL_MYSQL_H -I/usr/local/include  -fPIC -g -O2  -c mysql.c
gcc -shared  -L'/usr/local/lib' -Wl,-R'/usr/local/lib' -L'/usr/local/lib' -Wl,-R'/usr/local/lib' -o mysql.so mysql.o  -lmysqlclient  -ldl -lcrypt -lm   -lc

make install
mkdir -p /usr/local/lib/ruby/gems/1.8/gems/mysql-2.7/lib
/usr/bin/install -c -m 0755 mysql.so /usr/local/lib/ruby/gems/1.8/gems/mysql-2.7/lib

make clean
Successfully installed mysql-2.7

$ !rake
rake db:migrate
(in /home/work/daphari)
== CreateMembers: migrating ===================================================
-- create_table(:members)
   -> 0.0065s
== CreateMembers: migrated (0.0069s) ==========================================

---

