---
title: "Updating error in qmail : fqdn"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by learner11 on 2012-06-12
shagun@shagun:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 358 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main apparmor amd64 2.7.102-0ubuntu3.1 [358 kB]
Fetched 358 kB in 23s (15.0 kB/s)                                              
Preconfiguring packages ...
(Reading database ... 220439 files and directories currently installed.)
Preparing to replace apparmor 2.7.102-0ubuntu3 (using .../apparmor_2.7.102-0ubuntu3.1_amd64.deb) ...
Unpacking replacement apparmor ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
Setting up apparmor (2.7.102-0ubuntu3.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Installing new version of config file /etc/apparmor.d/abstractions/ubuntu-email ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Errors were encountered while processing:
 qmail
 qmail-run
E: Sub-process /usr/bin/dpkg returned an error code (1)


I am using ubuntu 12.04(amd64) and having this error while updating. What should i do ?

---

