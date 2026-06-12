---
title: "Ubuntu 10.10 Package update operation failed"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by bubastiss on 2011-12-05
Hello! Since I got new kernel 2.6.35-31, after every package update I have an operation failure. Could anyone please suggest any solution :confused:
Here is the log: 
> Loading new emgd-1.6.0.1922 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-31-generic
Building for architecture x86_64
Building initial module for 2.6.35-31-generic

Error! Bad return status for module build on kernel: 2.6.35-31-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/emgd/1.6.0.1922/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/emgd-dkms.0.crash'
dpkg: error processing emgd-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
 
Screenshot: 
[ATTACH]208552[/ATTACH]

---

### Post by jerrrys on 2011-12-06
are you running virtual systems?  If not, you may not even need dkms.

Open a terminal and try:

sudo dpkg --configure -a

---

### Post by bubastiss on 2012-02-21
> **jerrrys said:**
> are you running virtual systems?  If not, you may not even need dkms.

Open a terminal and try:

sudo dpkg --configure -a
Thank you for reply! I'm also running win7 if that's what you asking by virtual system. Could you explain for a newbie does the error affect for applying update packages??
Here is the terminal log after trying your suggested command:
> massalim@massalim-Inspiron-N5010:~$ sudo dpkg --configure -a
Setting up emgd-dkms (1.6.0.1922-0ubuntu1~ppa12) ...
Removing old emgd-1.6.0.1922 DKMS files...

------------------------------
Deleting module version: 1.6.0.1922
completely from the DKMS tree.
------------------------------
Done.
Loading new emgd-1.6.0.1922 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-32-generic
Building for architecture x86_64
Building initial module for 2.6.35-32-generic

Error! Bad return status for module build on kernel: 2.6.35-32-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/emgd/1.6.0.1922/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/emgd-dkms.0.crash'
dpkg: error processing emgd-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 emgd-dkms
massalim@massalim-Inspiron-N5010:~$ ^C
massalim@massalim-Inspiron-N5010:~$  

---

