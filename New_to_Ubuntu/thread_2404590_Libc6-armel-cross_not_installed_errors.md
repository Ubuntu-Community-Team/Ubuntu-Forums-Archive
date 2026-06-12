---
title: "Libc6-armel-cross not installed errors"
date: 2018-10-25
forum: New to Ubuntu
---

### Post by moge233 on 2018-10-25
Hi all,

I recently upgraded my system to ubuntu 18.04 and after this I have been getting the following error message while trying to run really anything with apt:

The following packages have unmet dependencies:
 libasan4-armel-cross : Depends: libc6-armel-cross (>= 2.27) but it is not installed
 libatomic1-armel-cross : Depends: libc6-armel-cross (>= 2.27) but it is not installed
 libcilkrts5-armel-cross : Depends: libc6-armel-cross (>= 2.27) but it is not installed
 libgcc1-armel-cross : Depends: libc6-armel-cross (>= 2.27) but it is not installed
 libgomp1-armel-cross : Depends: libc6-armel-cross (>= 2.27) but it is not installed
 libstdc++-7-dev-armel-cross : Depends: libc6-dev-armel-cross (>= 2.13-0ubuntu6) but it is not installed
 libstdc++6-armel-cross : Depends: libc6-armel-cross (>= 2.27) but it is not installed
 libubsan0-armel-cross : Depends: libc6-armel-cross (>= 2.27) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


I have tried to run 'apt --fix-broken install' like it mentions.  I have not tried with a specific solution like it says at the end as I am not really sure what specific solution I would need to use.
I have tried to run 'apt install libc6-armel-cross' and get the following:

The following packages have unmet dependencies:
 libstdc++-7-dev-armel-cross : Depends: libc6-dev-armel-cross (>= 2.13-0ubuntu6) but it is not going to be installed


Ok, well trying to install libc6-dev-armel-cross, I get an error message exactly like the first error message I posted.  I am really at a loss here.  Everything seems to be functioning fine except for anything using apt, such as autoremove or clean.
Does anyone have any solutions or trouble shooting ideas?

Thanks

---

### Post by wildmanne39 on 2018-10-25
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by moge233 on 2018-10-25
Thanks for moving it.  I wasn't sure exactly where to put it.

---

### Post by moge233 on 2018-10-25
Also, just to be more thorough, here is the error I get when I try 'apt --fix-broken install':

(Reading database ... 453513 files and directories currently installed.)
Preparing to unpack .../libc6-armel-cross_2.27-3ubuntu1cross1.1_all.deb ...
Unpacking libc6-armel-cross (2.27-3ubuntu1cross1.1) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-armel-cross_2.27-3ubuntu1cross1.1_all.deb (--unpack):
 unable to open '/usr/arm-linux-gnueabi/lib/ld-2.27.so.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
         Preparing to unpack .../libc6-dev-armel-cross_2.27-3ubuntu1cross1.1_all.deb ...
Unpacking libc6-dev-armel-cross (2.27-3ubuntu1cross1.1) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-armel-cross_2.27-3ubuntu1cross1.1_all.deb (--unpack):
 unable to open '/usr/arm-linux-gnueabi/lib/Mcrt1.o.dpkg-new': No such file or directory
No apport report written because the error message indicates an issue on the local system
         Errors were encountered while processing:
 /var/cache/apt/archives/libc6-armel-cross_2.27-3ubuntu1cross1.1_all.deb
 /var/cache/apt/archives/libc6-dev-armel-cross_2.27-3ubuntu1cross1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

