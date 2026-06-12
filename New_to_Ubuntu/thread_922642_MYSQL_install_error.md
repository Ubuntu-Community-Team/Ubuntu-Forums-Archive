---
title: "MYSQL install error"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by disappearedng on 2008-09-17
Hi everyone
I installed MYSQL 5 on my ubuntu hardy doing exactly what I was told by the documentation website.

I am getting the following error:
```

disappearedng@disappearedng-ubuntu-client:~$ sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient15off mysql-client-5.0 mysql-common
  mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  libhtml-template-perl mailx
The following NEW packages will be installed:
  libapache2-mod-auth-mysql libdbd-mysql-perl libmysqlclient15off
  mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-mysql
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.4MB of archives.
After this operation, 110MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ca.archive.ubuntu.com hardy-updates/main mysql-common 5.0.51a-3ubuntu5.1 [59.7kB]
Get:2 http://ca.archive.ubuntu.com hardy-updates/main libmysqlclient15off 5.0.51a-3ubuntu5.1 [1836kB]
Get:3 http://ca.archive.ubuntu.com hardy/main libdbd-mysql-perl 4.005-1 [134kB]
Get:4 http://ca.archive.ubuntu.com hardy-updates/main mysql-client-5.0 5.0.51a-3ubuntu5.1 [7824kB]
Get:5 http://ca.archive.ubuntu.com hardy-updates/main mysql-server-5.0 5.0.51a-3ubuntu5.1 [27.4MB]
Get:6 http://ca.archive.ubuntu.com hardy/main libapache2-mod-auth-mysql 4.3.9-4 [22.6kB]
Get:7 http://ca.archive.ubuntu.com hardy-updates/main mysql-server 5.0.51a-3ubuntu5.1 [53.7kB]
Get:8 http://ca.archive.ubuntu.com hardy-updates/main php5-mysql 5.2.4-2ubuntu5.3 [65.2kB]
Fetched 37.4MB in 7min14s (86.1kB/s)                                           
Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 143483 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.51a-3ubuntu5.1_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Setting up mysql-common (5.0.51a-3ubuntu5.1) ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 143584 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_i386.deb) ...
Selecting previously deselected package libapache2-mod-auth-mysql.
Unpacking libapache2-mod-auth-mysql (from .../libapache2-mod-auth-mysql_4.3.9-4_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.1_all.deb) ...
Selecting previously deselected package php5-mysql.
Unpacking php5-mysql (from .../php5-mysql_5.2.4-2ubuntu5.3_i386.deb) ...
Setting up libmysqlclient15off (5.0.51a-3ubuntu5.1) ...

Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libapache2-mod-auth-mysql (4.3.9-4) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Setting up php5-mysql (5.2.4-2ubuntu5.3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```]

I can't start mysql.

What should I do? ( I have tried reinstalling already).

---

### Post by disappearedng on 2008-09-17
disappearedng@disappearedng-ubuntu-client:~$ sudo dpkg-reconfigure mysql-server
/usr/sbin/dpkg-reconfigure: mysql-server is broken or not fully installed
disappearedng@disappearedng-ubuntu-client:~$ 
disappearedng@disappearedng-ubuntu-client:~$ sudo dpkg-reconfigure mysql-server
/usr/sbin/dpkg-reconfigure: mysql-server is broken or not fully installed
disappearedng@disappearedng-ubuntu-client:~$ sudo dpkg-reconfigure mysql-server-5.0
/usr/sbin/dpkg-reconfigure: mysql-server-5.0 is broken or not fully installed
disappearedng@disappearedng-ubuntu-client:~$ 

?

---

### Post by acidsolution on 2008-09-17
```

sudo apt-get install -f


```

---

### Post by disappearedng on 2008-09-17
```

disappearedng@disappearedng-ubuntu-client:/var/lib/dpkg$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by disappearedng on 2008-09-17
```

disappearedng@disappearedng-ubuntu-client:/var/lib/dpkg$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

disappearedng@disappearedng-ubuntu-client:/var/lib/dpkg$ sudo /etc/init.d/mysql start
] * Starting MySQL database server mysqld                                [fail] 
disappearedng@disappearedng-ubuntu-client:/var/lib/dpkg$ ]


```

---

### Post by Venkat.yarl on 2009-12-12
I am quite new in ubuntu and to mysql i tried installing mysql using 
```

$ sudo apt-get install mysql-server

```and I keep on getting this error and I dont know where to go from there... I tried doing install -f as posted here but no use, I still keep on getting the error down below.

```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Any help regarding this would be helpful. A detailed instruction would be amazing.
Thank You

---

