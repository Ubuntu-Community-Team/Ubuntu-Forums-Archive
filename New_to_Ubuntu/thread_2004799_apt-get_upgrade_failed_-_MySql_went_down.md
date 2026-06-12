---
title: "apt-get upgrade failed - MySql went down"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-16
Hi,

I never thought an ```
sudo apt-get upgrade
``` could actually fail.

I just brought down my server, the MySQL database connection can not longer be established. Please advice what went wrong:


```

ubuntu@ip-xx-xx-xxx-xxx:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-image-virtual linux-virtual
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.5 (5.5.24-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Shall do a ```
sudo apt-get -f install
``` to force install?  Could I loose my data?

Many Thanks,

---

### Post by Houmie on 2012-06-16
Never mind its a confirmed bug without a workaround that is understandable by mortals. :D

[https://bugs.launchpad.net/ubuntu/+source/mysql-5.5/+bug/1012058](https://bugs.launchpad.net/ubuntu/+source/mysql-5.5/+bug/1012058)

It was faster reinstalling the Server and run my bash script to install the apps.  Scripts have saved my skin so many times.

Now I am thinking twice before running an apt-get update on production server.  Its best to test it on a local machine first. Before this incident I thought I could trust blindly all canonical updates.

:lolflag:

---

