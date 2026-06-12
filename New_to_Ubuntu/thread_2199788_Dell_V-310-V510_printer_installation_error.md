---
title: "Dell V-310-V510 printer installation error"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by flyfisherbryan on 2014-01-15
I have a Dell V-510 printer to install on my Optiplex 745 desktop  running Ubuntu 13.10 (32 bit)  Finally found a driver on the Dell site and  looked up how to use it.  I cannot run the installer from the desktop,  but found a way to start it in Terminal.  Once started an installer  window opens and I proceed from there, but then I encounter an error.

This is a copy of the Terminal screen:

bryan@XYZ:~$ cd ~/Desktop/; chmod +x ./dell-inkjet-09-driver-1.0-1.i386.deb.sh; gksudo ./dell-inkjet-09-driver-1.0-1.i386.deb.sh
Verifying archive integrity... All good.
Uncompressing nixstaller.........................................................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86
TRACKING IDENT = 140509
cpu speed = 1795 MHz
ram size = 3960.47265625 MB
hd avail = 23872 MB
dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'dell-inkjet-09-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 dell-inkjet-09-driver-1.0-1.i386.deb

And the installer window reads:

xecute: dpkg -i dell-inkjet-09-driver-1.0-1.i386.deb 2>&1 | tee /root/lua_G70AIf/installerror_msgs

dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'dell-inkjet-09-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 dell-inkjet-09-driver-1.0-1.i386.deb
=============================
dpkg: error processing dell-inkjet-09-driver-1.0-1.i386.deb (--install): parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'dell-inkjet-09-driver': blank line in value of field 'Description'Errors were encountered while processing: dell-inkjet-09-driver-1.0-1.i386.deb
=============================
Execute: rm -rf /root/lua_G70AIf

=============================

Anybody know what I should do next?

---

### Post by flyfisherbryan on 2014-01-17
I have now tried several versions of the install file and they all fail in exactly the same way.  I cannot use CUPS because the script fails before unpacking the .ppd files.  It has now dawned on me that in all my research I have never seen this printer installed on a 13.X version of Ubuntu.  Maybe now it is no longer possible?  This printer is a problem even in Windows, and when I can I will replace it, but in the meantime, I guess the Windows partition stays.  :mad:

---

