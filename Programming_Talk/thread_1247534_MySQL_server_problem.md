---
title: "MySQL server problem"
date: 2009-08-23
forum: Programming Talk
---

### Post by Vishnu V on 2009-08-23
i tried to install MySQl server by the command

sudo apt-get install mysql-server

but i got the error 

the o/p for the above command is

vishnu@vishnu-desktop:~$ sudo apt-get install mysql-server
[sudo] password for vishnu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 171 not upgraded.
1 not fully installed or removed.
Need to get 0B/57.2kB of archives.
After this operation, 98.3kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mysql-server
Install these packages without verification [y/N]? y
Selecting previously deselected package mysql-server.
(Reading database ... 139454 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Reloading AppArmor profiles ...                                       [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

please help me to install it

---

