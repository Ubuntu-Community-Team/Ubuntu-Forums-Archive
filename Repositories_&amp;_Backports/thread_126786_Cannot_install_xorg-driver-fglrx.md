---
title: "Cannot install xorg-driver-fglrx"
date: 2006-02-07
forum: Repositories &amp; Backports
---

### Post by peholmst on 2006-02-07
Hello,

I'm terribly sorry if this has been asked before, but frankly I did not manage to find any information either here or on Google.

I'm trying to install the xorg-driver-fglrx -package, but when I run the command:

sudo apt-get install xorg-driver-fglrx

I get:

```

Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  fglrx-kernel
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8325kB of archives.
After unpacking 24.1MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 158523 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/fglrx/libGL.so.1.xlibmesa' with
  different file `/usr/X11R6/lib/libGL.so.1', not allowed
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas what's causing this and how to fix it?

Thanks in advance,

-Petter-

---

### Post by peholmst on 2006-02-07
Never mind, I figured it out; There were some files left from a non-dpkg installation attempt of fglrx. Once I removed them everything worked.

-Petter-

---

### Post by lrbradford on 2008-09-27
Peter,

I can't get that far:

lynn@lynn-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for lynn: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
lynn@lynn-laptop:~$ 

I'm trying to install ATI Catalyst, but it stops and says it need the xorg-drive-fglrx.  This is in Synapptic, leaving me wonder if I don't have a repository installed?

Any ideas?  If there are commands, please show the example.

Thanks!

---

### Post by UbuWu on 2008-09-27
lrbradford: This isn't a problem with xorg-drive-fglrx, it looks like you have two package managers open at the same time, which doesn't work. If that is not the case, it could be that the update-manager was active in the background.

---

### Post by joshtheitguy on 2008-09-30
try a sudo dpkg --configure -a, that is what I always do when I get that message

---

### Post by sysboy on 2009-01-17
The same error i encountered. How to solve this problem? Many thanks.

---

### Post by sysboy on 2009-01-17
> **peholmst said:**
> Hello,

I'm terribly sorry if this has been asked before, but frankly I did not manage to find any information either here or on Google.

I'm trying to install the xorg-driver-fglrx -package, but when I run the command:

sudo apt-get install xorg-driver-fglrx

I get:

```

Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  fglrx-kernel
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8325kB of archives.
After unpacking 24.1MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 158523 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/fglrx/libGL.so.1.xlibmesa' with
  different file `/usr/X11R6/lib/libGL.so.1', not allowed
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas what's causing this and how to fix it?

Thanks in advance,

-Petter-

The same error i encountered. How to solve this problem? Many thanks.



netwalker@netwalker:~/Desktop$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/9952kB of archives.
After this operation, 30.1MB of additional disk space will be used.
(Reading database ... 207516 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.16-23.56_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.16-23.56_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.16-23.56_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

