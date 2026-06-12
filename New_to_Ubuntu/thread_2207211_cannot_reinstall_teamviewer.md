---
title: "cannot reinstall teamviewer"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by jj4 on 2014-02-22
$ sudo apt-get remove teamviewer --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  teamviewer*
0 upgraded, 0 newly installed, 1 to remove and 25 not upgraded.
After this operation, 81.9 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: files list file for package 'libapt-pkg4.12:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgconf-2-4:i386' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libgconf2-4:i386' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)



any ideas how to force this?

---

### Post by Vladlenin5000 on 2014-02-22
Use the 32-Bit / Multiarch version.

---

### Post by jj4 on 2014-02-23
> **Vladlenin5000 said:**
> Use the 32-Bit / Multiarch version.

I am - I'm installing it from the website and I get errors on install as well.

---

