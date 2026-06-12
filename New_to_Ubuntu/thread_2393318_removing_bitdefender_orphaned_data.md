---
title: "removing bitdefender orphaned data"
date: 2018-06-01
forum: New to Ubuntu
---

### Post by rburkartjo on 2018-06-01
get this 

ray@nightmare:~$ sudo apt-get purge bitdefender-scanner bitdefender-scanner-gui
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bitdefender-scanner:i386* bitdefender-scanner-gui:i386*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 478265 files and directories currently installed.)
Purging configuration files for bitdefender-scanner-gui:i386 (7.7.1-1809) ...
find: ‘/opt/BitDefender-scanner/share/locale’: No such file or directory
dpkg: error processing package bitdefender-scanner-gui:i386 (--purge):
 installed bitdefender-scanner-gui:i386 package post-removal script subprocess returned error exit status 1
Purging configuration files for bitdefender-scanner:i386 (7.7.1-1809) ...
find: ‘/opt/BitDefender-scanner/share/locale’: No such file or directory
dpkg: error processing package bitdefender-scanner:i386 (--purge):
 installed bitdefender-scanner:i386 package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 bitdefender-scanner-gui:i386
 bitdefender-scanner:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
ray@nightmare:~$ 
/tks

---

