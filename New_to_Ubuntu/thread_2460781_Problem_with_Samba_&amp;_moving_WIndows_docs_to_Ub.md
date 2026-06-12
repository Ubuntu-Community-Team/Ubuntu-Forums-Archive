---
title: "Problem with Samba &amp; moving WIndows docs to Ubuntu 20.04"
date: 2021-04-18
forum: New to Ubuntu
---

### Post by markb60000 on 2021-04-18
I am trying to set up the transfer of my Windows 10 desktop files to Ubuntu 0.04, which I just installed.
 
 In doing so, I installed Samba, but did so incorrectly.  I tried to uninstall the program, but, as shown in the attached document, the delete was aborted.

Is there a way to delete Samba, or should I forget about the remnants of the installation, and use a program that does what Samba does?  Or should I use another method to move my Windows desktop documents to Ubuntu?

Thanks,
Mark
 
mark@mark-HP-Notebook:~$ sudo apt-get remove --purge samba
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages were automatically installed and are no longer required:
  attr ibverbs-providers libcephfs2 libibverbs1 librados2 librdmacm1
  samba-vfs-modules tdb-tools
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
After this operation, 16.6 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Abort.
mark@mark-HP-Notebook:~$ sudo apt-get autoremove --purge samba
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages will be REMOVED:
  attr* ibverbs-providers* libcephfs2* libibverbs1* librados2*
  librdmacm1* samba* samba-vfs-modules* tdb-tools*
0 upgraded, 0 newly installed, 9 to remove and 6 not upgraded.
After this operation, 35.8 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Abort.

---

### Post by DuckHook on 2021-04-18
Duplicate of: [https://ubuntuforums.org/showthread.php?t=2460752](https://ubuntuforums.org/showthread.php?t=2460752)

Please do not post duplicate threads. This confuses those trying to help and dilutes community effort.

***Thread Closed.***

---

