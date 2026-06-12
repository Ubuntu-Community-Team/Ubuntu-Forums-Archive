---
title: "so I downloaded a tar.gz file, opened it..now what..?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Ducatiboy-stu on 2008-05-02
I downloaded vmware-server as a tar file, opened it, but now dont how to get it running
This is a copy from term

stuart@stuart-laptop:~$ ls
conffiles  Examples  Public     virtualbox_1.5.4-27034_Ubuntu_gutsy_i386.deb
control    logs      setup      vmware-install.pl
Desktop    md5sums   shlibs     
Documents  Pictures  Templates  vmware-server-distrib
downloads  postinst  usr
etc        postrm    Videos
stuart@stuart-laptop:~$ cd downloads
stuart@stuart-laptop:~/downloads$ ls
VMware-server-1.0.5-80187.tar.gz  vmware-server-distrib
stuart@stuart-laptop:~/downloads$ cd vmware-server-distrib
stuart@stuart-laptop:~/downloads/vmware-server-distrib$ ls
bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl  vmware-vix
stuart@stuart-laptop:~/downloads/vmware-server-distrib$ 
stuart@stuart-laptop:~/downloads/vmware-server-distrib$ vmware install.pl
bash: vmware: command not found
stuart@stuart-laptop:~/downloads/vmware-server-distrib$ vmware
bash: vmware: command not found
stuart@stuart-laptop:~/downloads/vmware-server-distrib$ 


It has extracted the files...but now I am stuck....:confused:

---

### Post by tamoneya on 2008-05-02
```
sudo ./vmware-install.pl
```

---

### Post by cartisdm on 2008-05-02
This doesn't quite answer your question but you could always take the easy route.  Go to Applications --> Add/Remove --> Seach VMWare and download/install.  Does it all for you:)

---

### Post by Xiong Chiamiov on 2008-05-02
Yes, you should definitely read "[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")".  The idea of a package manager I don't think is very well explained, but once you get used to it, you'll never want to go back.

---

### Post by tamoneya on 2008-05-02
It is still important to learn how to install from stratch. Not all programs are in the package manager though and sometimes the package manager has out of date programs and it is better to install from source in order to get the correct version.

---

### Post by Xiong Chiamiov on 2008-05-02
> **tamoneya said:**
> It is still important to learn how to install from stratch. Not all programs are in the package manager though and sometimes the package manager has out of date programs and it is better to install from source in order to get the correct version.
...which is also explained in that wonderful guide I linked to.  I tell you, I think I link to it more often than Pschyocats!

---

### Post by miesnerd on 2008-05-02
> **Xiong Chiamiov said:**
> Yes, you should definitely read "[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")".  The idea of a package manager I don't think is very well explained, but once you get used to it, you'll never want to go back.

i completely agree. 2 years into linux, and i laugh at windows when I see people installing files. Its really pretty humorous, once you get used to linux. Its true, also, that as you get used to linux, you'll soon realize that what makes or breaks a distro is based on its package management...

---

### Post by Xiong Chiamiov on 2008-05-02
> **miesnerd said:**
> i completely agree. 2 years into linux, and i laugh at windows when I see people installing files. Its really pretty humorous, once you get used to linux. Its true, also, that as you get used to linux, you'll soon realize that what makes or breaks a distro is based on its package management...
I recently installed PC-BSD (to play around with), and among other things, they say that they don't like any of the Linux package management system, so they've made installers operate like Windows!
I found it so tiresome having to visit a website to download software, then click through multiple "next"s just to install the darn thing.

---

### Post by Ducatiboy-stu on 2008-05-02
I cant get VMware-server thru package installer...dont worry I tried

Anyway  i did sudo./vmware-install.pl

Got to the end when I got the following


None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.



:confused:

---

### Post by Monicker on 2008-05-02
> **Ducatiboy-stu said:**
> I cant get VMware-server thru package installer...dont worry I tried

Anyway  i did sudo./vmware-install.pl

Got to the end when I got the following


None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.



:confused:

You need to install the kernel headers.

```
uname -a
apt-cache search linux-header
```

Pick the one which matches the output of uname, and install.

---

### Post by Ducatiboy-stu on 2008-05-02
I did th uname -a


got a long list...

How do i dwnld and inst

Sorry for the noobie questions...but I gota learn somehow

Linux stuart-laptop 2.6.24-16-386 #1 Thu Apr 10 12:50:06 UTC 2008 i686 GNU/Linux
stuart@stuart-laptop:~$ apt-cache search linux-header
linux-headers-2.6.24-16 - Header files related to Linux kernel version 2.6.24
linux-headers-2.6.24-16-386 - Linux kernel headers for version 2.6.24 on i386
linux-headers-2.6.24-16-generic - Linux kernel headers for version 2.6.24 on x86/x86_64
linux-headers-2.6.24-16-openvz - Linux kernel headers for version 2.6.24 on OpenVZ Virtualization enabled kernel
linux-headers-2.6.24-16-rt - Linux kernel headers for version 2.6.24 on Ingo Molnar's full real time preemption patch (2.6.24.3-rt3)
linux-headers-2.6.24-16-server - Linux kernel headers for version 2.6.24 on x86/x86_64
linux-headers-2.6.24-16-virtual - Linux kernel headers for version 2.6.24 on x86
linux-headers-2.6.24-16-xen - Linux kernel headers for version 2.6.24 on This kernel can be used for Xen dom0 and domU
linux-headers-386 - Linux kernel headers on 386
linux-headers-686 - Upgrade dummy package. Can be removed
linux-headers-generic - Generic Linux kernel headers
linux-headers-k7 - Upgrade dummy package. Can be removed
linux-headers-lbm-2.6.24-16-386 - Header files related to linux-backports-modules version 2.6.24
linux-headers-lbm-2.6.24-16-generic - Header files related to linux-backports-modules version 2.6.24
linux-headers-lbm-2.6.24-16-server - Header files related to linux-backports-modules version 2.6.24
linux-headers-lbm-2.6.24-16-virtual - Header files related to linux-backports-modules version 2.6.24
linux-headers-lum-2.6.24-16-386 - Header files related to linux-ubuntu-modules version 2.6.24
linux-headers-lum-2.6.24-16-generic - Header files related to linux-ubuntu-modules version 2.6.24
linux-headers-lum-2.6.24-16-server - Header files related to linux-ubuntu-modules version 2.6.24
linux-headers-lum-2.6.24-16-virtual - Header files related to linux-ubuntu-modules version 2.6.24
linux-headers-openvz - rt Linux kernel headers
linux-headers-rt - rt Linux kernel headers
linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-virtual - Linux kernel headers for the virtual flavour
linux-source-2.6.24 - Linux kernel source for version 2.6.24 with Ubuntu patches
linux-headers-lbm-2.6.24-16-openvz - Header files related to linux-backports-modules version 2.6.24
linux-headers-lbm-2.6.24-16-rt - Header files related to linux-backports-modules version 2.6.24
linux-headers-lbm-2.6.24-16-xen - Header files related to linux-backports-modules version 2.6.24
linux-headers-lum-2.6.24-16-openvz - Header files related to linux-ubuntu-modules version 2.6.24
linux-headers-lum-2.6.24-16-rt - Header files related to linux-ubuntu-modules version 2.6.24
linux-headers-lum-2.6.24-16-xen - Header files related to linux-ubuntu-modules version 2.6.24
linux-headers-xen - Xen Linux kernel headers
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver
stuart@stuart-laptop:~$

---

### Post by Xiong Chiamiov on 2008-05-02
All you really need to do is take a look at
```

uname -r

```
and install the package that is named that.

So, for example, I get
```

2.6.22-14-generic

```
so I would install like this:
```

sudo apt-get install linux-headers-2.6.22-14-generic

```
More clear?

---

### Post by Ducatiboy-stu on 2008-05-02
Yes...much clearer...

---

### Post by Ducatiboy-stu on 2008-05-02
Ok...downloaded headers etc....

Still having issues

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-386/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialisation from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialisation from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

stuart@stuart-laptop:~/vmware-server-distrib$ ls
bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl  vmware-vix

---

### Post by Monicker on 2008-05-02
I think you still have other dependencies which need to be satified.  Take a look at these threads:

[http://ubuntuforums.org/showthread.php?t=283454]("http://ubuntuforums.org/showthread.php?t=283454")

[http://ubuntuforums.org/showthread.php?t=770873]("http://ubuntuforums.org/showthread.php?t=770873")

---

### Post by Ducatiboy-stu on 2008-05-02
The guide on this link worked staright up

[http://ubuntuforums.org/showthread.php?t=613976&page=4](http://ubuntuforums.org/showthread.php?t=613976&page=4)

step 1 ) sudo bash ( note sudo su always exits for some reason )
step 2 ) apt-get install build-essential
step 3 ) download vmware-server 1.0.5.tar.gz
step 4 ) extract it to the desktop
step 5 ) go to [http://groups.google.com/group/vmker...es/files?hl=en](http://groups.google.com/group/vmker...es/files?hl=en) and download patch 116 ( i did not get the wireless bridge one but it should work also )

step 6 ) extract the patch to desktop
step 7 ) cd Desktop/vmware-server-distrib
step 8 ) ./vmware-install.pl Keep all the defaults and do everything until it asks if you want to compile the kernel then say no ( if you say yes it is not that big of a deal it will just fail )

step 9 ) cd ../vmware-any-any-update116/
step 10 ) ./runme.pl make sure to say yes to compile kernel and follow defaults

*** This is the step i had trouble finding ***
step 11 )
cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/


Hope this helps someone else
Reference [http://federkiel.wordpress.com/2008/...4/#comment-103](http://federkiel.wordpress.com/2008/...4/#comment-103)





Thanks guys for all your help....much appreciated...)):P

---

