---
title: "cqrlog"
date: 2016-05-12
forum: New to Ubuntu
---

### Post by jack178 on 2016-05-12
```
unable to remove or reinstall cqrlog                                                                                                                                                                           Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  cqrlog
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0 B/7,773 kB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package cqrlog.
(Reading database ... 219781 files and directories currently installed.)
Preparing to unpack .../cqrlog_2.0.1-1~wily_amd64.deb ...
Unpacking cqrlog (2.0.1-1~wily) over (2.0.0-1~wily) ...
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/cqrlog_2.0.1-1~wily_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for gnome-menus (3.13.3-6ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+15.10.20150627.1-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for man-db (2.7.4-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/cqrlog_2.0.1-1~wily_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```    please help

---

### Post by QDR06VV9 on 2016-05-12
After you get that error, try
```
sudo apt-get -f install
``` 
to force an install of the files that didn't get loaded because of the error. Then try 
```
sudo apt-get update
```
And
```
sudo apt-get upgrade
```
And Post back any errors

---

### Post by QDR06VV9 on 2016-05-12
@jack178 Requesting status on the advise given.

---

### Post by jack178 on 2016-05-12
sorry  i had to go to doc appmt.  yes that solved the problem thanks

---

### Post by jack178 on 2016-05-12
problem solved thanks

---

### Post by QDR06VV9 on 2016-05-12
Hope things are well.
Best Regards
I'll Mark this as solved then....but if it needs changed back just post back here.

---

