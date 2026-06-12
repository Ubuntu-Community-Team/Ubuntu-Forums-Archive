---
title: "Building Oracle Client 11gR2 on 13.04 fails can't find sys/types.h"
date: 2013-06-27
forum: Packaging and Compiling Programs
---

### Post by dwschulze on 2013-06-27
I'm trying to install Oracle Client 11gR2 on Ubuntu 13.04 64-bit following [this HowTo]("http://forums.oracle.com/thread/1117155").  When I run the installer it fails with this error:

INFO: ntcontab.c:7:23: fatal error: sys/types.h: No such file or directory
compilation terminated.

I've installed the libc-dev-bin library and the ia32-libs.  Is there another package I need to get this to compile?

---

### Post by compiledkernel on 2013-06-27
> **dwschulze said:**
> I'm trying to install Oracle Client 11gR2 on Ubuntu 13.04 64-bit following [this HowTo]("http://forums.oracle.com/thread/1117155").  When I run the installer it fails with this error:

INFO: ntcontab.c:7:23: fatal error: sys/types.h: No such file or directory
compilation terminated.

I've installed the libc-dev-bin library and the ia32-libs.  Is there another package I need to get this to compile?

Memory serving me this is caused by not having glibc-headers installed. Im not sure if the metapackages for libc-dev and ia32-libs installs this, so I could be wrong. 

11gR2 runs ok on Debian machines, but its really to your advantage to run it on OEL. I however commend your drive to install it on Ubuntu.

---

### Post by dwschulze on 2013-06-28
> **compiledkernel said:**
> Memory serving me this is caused by not having glibc-headers installed. Im not sure if the metapackages for libc-dev and ia32-libs installs this, so I could be wrong. 

11gR2 runs ok on Debian machines, but its really to your advantage to run it on OEL. I however commend your drive to install it on Ubuntu.


There isn't a glibc-headers package available for Ubuntu.  I've got build-essentials and libc6-dev installed which have the headers.  Here are where sys/types.h exists on my file system:

/usr/include/x86_64-linux-gnu/sys/types.h
/usr/lib/syslinux/com32/include/sys/types.h

Is there another package that I need to install to make this work on 13.04?

Thanks.

---

### Post by steeldriver on 2013-06-28
**DISCLAIMER: this is on a crunchbang 11 box - I don't have a native 64-bit Ubuntu box to check**

I *think* that the link gets created when you install the i386 libc6-dev packages e.g.

```

$ **apt-cache policy libc6-dev-i386**
libc6-dev-i386:
  **Installed: (none)**
  Candidate: 2.13-38
  Version table:
     2.13-38 0
        500 http://ftp.debian.org/debian/ wheezy/main amd64 Packages
$ 
[B]$ find /usr/include/sys -name 'types.h'
$ [/B]

```

Then if I do
```

**$ sudo apt-get install libc6-dev-i386**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libc6-i386
Recommended packages:
  gcc-multilib
The following NEW packages will be installed:
  libc6-dev-i386 libc6-i386
0 upgraded, 2 newly installed, 0 to remove and 59 not upgraded.
Need to get 5,620 kB of archives.
After this operation, 14.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ftp.debian.org/debian/ wheezy/main libc6-i386 amd64 2.13-38 [4,033 kB]
Get:2 http://ftp.debian.org/debian/ wheezy/main libc6-dev-i386 amd64 2.13-38 [1,586 kB]
Fetched 5,620 kB in 4s (1,405 kB/s)         
Selecting previously unselected package libc6-i386.
(Reading database ... 145080 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.13-38_amd64.deb) ...
Selecting previously unselected package libc6-dev-i386.
Unpacking libc6-dev-i386 (from .../libc6-dev-i386_2.13-38_amd64.deb) ...
Setting up libc6-i386 (2.13-38) ...
Setting up libc6-dev-i386 (2.13-38) ...
$ 
[B]$ find /usr/include/sys -name 'types.h' -ls
1452115    0 lrwxrwxrwx   1 root     root           31 Dec 30 10:37 /usr/include/sys/types.h -> ../x86_64-linux-gnu/sys/types.h
$ [/B]

```

Obviously that brings in a whole multilib infrastructure - I don't *think* that's a problem, but ymmv

---

