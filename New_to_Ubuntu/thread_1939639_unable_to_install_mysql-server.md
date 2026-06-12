---
title: "unable to install mysql-server"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by thomsebastin on 2012-03-12
why do i always get this error??
```
thomas@thomas:~$ sudo apt-get install mysql-server
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mysql-server-5.1 (5.1.54-1ubuntu4) ...
invoke-rc.d: unknown initscript, /etc/init.d/mysql not found.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 100
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```this error message shows up even when i try to install something else via terminal(won't affect the installation even though).how do i solve this??:confused:
even when i try to open .php files in browser,it asks me to save instead of opening.

---

### Post by thomsebastin on 2012-03-12
yes damn....i solved it :popcorn::popcorn:here is how i at least got rid of it ..
```

sudo rm /var/lib/dpkg/info/mysql-server-5.1*
sudo apt-get remove --purge mysql-server-5.1
sudo apt-get clean
sudo apt-get update

```

---

