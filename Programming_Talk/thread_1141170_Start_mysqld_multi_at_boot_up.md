---
title: "Start mysqld_multi at boot up"
date: 2009-04-28
forum: Programming Talk
---

### Post by thetorst on 2009-04-28
Hi,
I'm trying to figure out how to start mutiple mysql instances at boot up. I've used the following configuration to start multiple instances with mysqld_multi.

```
[mysqld]
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket = /var/run/mysqld/mysqld.sock
port = 3306
basedir         = /usr
datadir = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
...
[mysqld_multi]
mysqld     = /usr/bin/mysqld_safe
mysqladmin = /usr/bin/mysqladmin
user       = multi_admin
password   = multipass

[mysqld3307]
port=3307
socket=/tmp/mysql3307.sock
datadir=/var/lib/mysql/mhzdata
pid-file=/var/lib/mysql/mhzdata/mysqld3307.pid
user=mysql

```

These settings allowes me to start my mysql instances by running > sudo -u mysql mysqld_multi start

Yet, I don't know how to run this command att boot up. Is there possibly a config setting in /etc/mysql/my.cnf that starts all mysql instances att boot up? Or, should I edit my /etc/rc.local to start my mysql instances?

I appreciate all help that I can get
Thanks

---

