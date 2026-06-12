---
title: "problem with flashybrid"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by Dimitris77 on 2012-05-14
hi,

i'm trying to install the flashybrid but when i enter the **apt-get install flashybrid** command the machine returns me this :


root@user-desktop:/home/user# apt-get install flashybrid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashybrid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up flashybrid (0.15+nmu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashybrid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashybrid
E: Sub-process /usr/bin/dpkg returned an error code (1)

please help me....

---

### Post by searchfgold6789 on 2012-05-14
Use ```
sudo apt-get install flashybrid
``` in a normal command prompt or a terminal, rather than running the command from the root prompt.

---

### Post by Dimitris77 on 2012-05-14
did it and it gives me the same result...

i olso tried this one to find what is already using that file :

root@user-desktop:/home/user# lsof | grep /var/cache/debconf/config.dat
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
dpkg-prec  4672       root    4rW     REG        8,6    39658    1697827 /var/cache/debconf/config.dat


but i dont know how to carry on, how to deal accordingly with it........any idea???

thnx anyway!

---

