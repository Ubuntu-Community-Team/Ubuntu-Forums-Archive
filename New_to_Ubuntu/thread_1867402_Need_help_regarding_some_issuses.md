---
title: "Need help regarding some issuses"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by rex_dante on 2011-10-22
hi ubuntuforums and all of its members...:)

this is ma 1st thread on this site.
i'm using ubuntu 11.04 from last 2-3 months and ma love is increasing day-by-day and so my knowledge... ;)

i got some issues in ubuntu, here's the list in point form-

1. After I log in to ubuntu any ubuntu session except "ubuntu 3D or unity", pressing ALT + F1-F6 switches me to VIRTUAL TERMINALS :-\
which i think the correct key combination is
CTRL + ALT+ Function key

So i got to log off and then log on to get rid of this problem TEMPORARILY :(


2. After doing this annoying task, when i press ENTER key while doing some bash scripting or ANY task PREFERABLY under a TERMINAL, "scoll lock" LED light gets ON and then WHEN i press ENTER key, my session gets logged off...
:(

means my afterwards, i need to login...


3. And my last problem is, i can't install my NVIDIA drivers to use UNITY feature or ANY other 3d feature EXCEPT "glxgears". But WHEN i run "glxgears", it show VERY low performance, like a "second hand" of a WALL CLOCK, like TICK-TICK...
:-(
This can be done by the "additional drivers" utility which came with the installation of ubuntu. I installed nvidia drivers using THIS utility. Because of THIS, i can use "ubuntu classic" mode. But WHEN i select "ubuntu" mode in logon screen, my DESKTOP flashes or flickers to THAT much speed that i can't even CLICK to a certain ICON...
:(


i've tried almost EVERY METHOD...searched THIS forum...GOOGLED it...etc etc..but no luck...
i've tried everything...so THIS IS my LAST hope as i don't know ANY other way or any other PERSON to whom i should ASK...

THIS SITE IS BEST...for asking i think... :)

i think if someone could help me over TEAMVIEWER or anything else...
But i need SERIOUS help...no joking...



thanks...

---

### Post by Falcon1002 on 2011-10-22
Hey! Welcome to the Forums and Ubuntu Linux! Sorry to hear your having problems.
 1. When you press CTRL + ALT + F1 - F6 it should switch you to a terminal login, if you press CTRL + ALT + F7 it should send you back to the GUI.
 
 2. Are you using a terminal you got to by using the CTRL + ALT + F1 - F6 combination or the terminal in the GUI?

 3. What Card do you have? Assuming your card is powerful enough to run Ubuntu 3D and Unity, you could try downloading and installing the Nvidia drivers for your card from the Nvidia site [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). This is more complicated then installing the driver with the built in program though and using these drivers causes some issues.

---

### Post by d4m1r on 2011-10-22
What graphics card do you have (make and model) and is it a laptop or a desktop?

---

### Post by rex_dante on 2011-10-22
hi Falcon..:)

thnx for replying fast...but i was away for a moment or more..

eh..as per your first point, i KNOW that i can switch to GUI with CTRL + ALT + F6. but i said that ONLY "ALT + F1-F6" switches me to the virtual terminals EXCLUDING "CTRL" key...:(

your second point, i NEVER use virtual terminal or WHAT it is said to be which is accessed by CTRL + ALT + function keys...
i only use GUI version of "gnome-terminal".

third, my GPU is "Nvidia FX 5500". And i tried installing the drivers from where u r redirecting me, MANY times...but the installation stops abruptly. btw,.u r talking about ".run" package driver na..?
i KNOW how to install or launch them...
i ALSO tried installing .run package of driver in VIRTUAL terminal...but it stops on 44% stating that i got to check ma log to figure out the problem which i was unable to understand after i read it. :confused:


plz DO reply back....:confused:

---

### Post by rex_dante on 2011-10-22
> **d4m1r said:**
> What graphics card do you have (make and model) and is it a laptop or a desktop?

GPU- Nvidia FX5500

I'm having a DSEKTOP
:-|

---

### Post by Falcon1002 on 2011-10-23
Sorry about the delay getting back to you.

Has the problem with the key board been there since you first installed Ubuntu, or has it started since then?
Could you please post the contents of the Log file from trying to install the Nvidia driver. Thanks.

---

### Post by rex_dante on 2011-10-26
> **Falcon1002 said:**
> Sorry about the delay getting back to you.

Has the problem with the key board been there since you first installed Ubuntu, or has it started since then?
Could you please post the contents of the Log file from trying to install the Nvidia driver. Thanks.

here's the "nvidia-installer-log-file"
> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Oct  9 07:44:19 2011
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.25.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.38-8-generic/build'
-> Kernel output path: '/lib/modules/2.6.38-8-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.38-8-generi
   c/build SYSOUT=/lib/modules/2.6.38-8-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.38-8-generic/build SUBDIRS=
   /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv modules
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/generated/autoconf.h or include/config/auto.conf are
   missing.";\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.2
   5-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/inc
   lude  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude  
   -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -
   Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -
   Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-p
   ointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mprefer
   red-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -
   Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCON
   FIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare
   -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wfra
   me-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg 
   -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconse
   rve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pk
   g1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare
   -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM 
   -DNV_VERSION_STRING=\"173.14.25\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KB
   UILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD
   _STR(nvidia)" -c -o /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/
   nv/.tmp_nv.o /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:22:0,
                    from include/linux/kernel.h:17,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/bitops.h: In fu
   nction ‘set_bit’:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/bitops.h:64:6: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/bitops.h: In fu
   nction ‘clear_bit’:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/bitops.h:102:6:
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/bitops.h: In fu
   nction ‘change_bit’:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/bitops.h:178:6:
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in condition
   al expression
   In file included from include/linux/list.h:7:0,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:57,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57:19: warning: pointer of type ‘void *’ used i
   n arithmetic
   In file included from include/linux/preempt.h:11:0,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:57,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/list.h: In function ‘list_del’:
   include/linux/list.h:107:16: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/list.h:108:16: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/list.h: In function ‘hlist_del’:
   include/linux/list.h:602:12: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/list.h:603:13: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/sched.h:82:0,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/rculist.h: In function ‘list_del_rcu’:
   include/linux/rculist.h:112:16: warning: pointer of type ‘void *’ used i
   n arithmetic
   include/linux/rculist.h: In function ‘list_replace_rcu’:
   include/linux/rculist.h:158:14: warning: pointer of type ‘void *’ used i
   n arithmetic
   include/linux/rculist.h: In function ‘hlist_del_rcu’:
   include/linux/rculist.h:312:13: warning: pointer of type ‘void *’ used i
   n arithmetic
   include/linux/rculist.h: In function ‘hlist_replace_rcu’:
   include/linux/rculist.h:332:15: warning: pointer of type ‘void *’ used i
   n arithmetic
   In file included from include/linux/utsname.h:35:0,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:25,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2324:41: warning: pointer of type ‘void *’ used in
   arithmetic
   In file included from include/linux/rculist_bl.h:7:0,
                    from include/linux/dcache.h:7,
                    from include/linux/fs.h:383,
                    from include/linux/poll.h:12,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:78,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/list_bl.h: In function ‘hlist_bl_del’:
   include/linux/list_bl.h:105:12: warning: pointer of type ‘void *’ used i
   n arithmetic
   include/linux/list_bl.h:106:13: warning: pointer of type ‘void *’ used i
   n arithmetic
   In file included from include/linux/dcache.h:7:0,
                    from include/linux/fs.h:383,
                    from include/linux/poll.h:12,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:78,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/rculist_bl.h: In function ‘hlist_bl_del_rcu’:
   include/linux/rculist_bl.h:76:13: warning: pointer of type ‘void *’ used
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:78,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h: I
   n function ‘copy_from_user’:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_32.h:20
   9:6: warning: comparison between signed and unsigned integer expressions
   In file included from include/linux/io.h:22:0,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:89,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/io.h: In functi
   on ‘writeq’:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/io.h:106:24: wa
   rning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7:0,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/pci.h:141,
                    from include/linux/pci.h:1243,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:89,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199:35: warning: pointer of type ‘void *’ us
   ed in arithmetic
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/dma-mapping.h:43:0,
                    from include/linux/dma-mapping.h:93,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/pci.h:141,
                    from include/linux/pci.h:1243,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:89,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77:48: warning: pointer of type ‘
   void *’ used in arithmetic
   In file included from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv-linux.h:120:0,
                    from /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:197:3: warning: pointer of type ‘void *’ used in
   arithmetic
   include/linux/highmem.h:200:3: warning: pointer of type ‘void *’ used in
   arithmetic
   /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.c: At top leve
   l:
   /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.c:373:5: error
   : unknown field ‘ioctl’ specified in initializer
   /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.c:373:5: warni
   ng: initialization from incompatible pointer type
   make[3]: *** [/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).




here's the "nvidia-bug-report"-
> ____________________________________________

Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see [www.nvnews.net](www.nvnews.net)) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 7129089

Date: Sun Oct  2 06:10:12 IST 2011
uname: Linux sparda 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

____________________________________________

*** /etc/issue
*** ls: -rw-r--r-- 1 root root 20 2011-04-21 22:20:43.000000000 +0530 /etc/issue
Ubuntu 11.04 \n \l


____________________________________________

*** /etc/debian_version
*** ls: -rw-r--r-- 1 root root 12 2010-10-21 18:17:40.000000000 +0530 /etc/debian_version
squeeze/sid

____________________________________________

*** /var/log/nvidia-installer.log does not exist

____________________________________________

*** /var/log/Xorg.0.log
*** ls: -rw-r--r-- 1 root root 17926 2011-10-02 05:42:55.000000000 +0530 /var/log/Xorg.0.log
[  1082.230] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  1082.230] X Protocol Version 11, Revision 0
[  1082.230] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  1082.230] Current Operating System: Linux sparda 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[  1082.230] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3a09b439-ffbf-4498-a4ab-4f6f3f93b01c ro quiet splash vt.handoff=7
[  1082.230] Build Date: 19 April 2011  03:33:17PM
[  1082.230] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1082.230] Current version of pixman: 0.20.2
[  1082.231] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  1082.231] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1082.231] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct  2 05:01:15 2011
[  1082.231] (==) Using config file: "/etc/X11/xorg.conf"
[  1082.231] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1082.257] (==) No Layout section.  Using the first Screen section.
[  1082.257] (==) No screen section available. Using defaults.
[  1082.257] (**) |-->Screen "Default Screen Section" (0)
[  1082.257] (**) |   |-->Monitor "<default monitor>"
[  1082.257] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[  1082.257] (**) |   |-->Device "Default Device"
[  1082.257] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1082.257] (==) Automatically adding devices
[  1082.257] (==) Automatically enabling devices
[  1082.257] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1082.257] 	Entry deleted from font path.
[  1082.257] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1082.257] 	Entry deleted from font path.
[  1082.257] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1082.257] 	Entry deleted from font path.
[  1082.257] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1082.258] 	Entry deleted from font path.
[  1082.258] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1082.258] 	Entry deleted from font path.
[  1082.258] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1082.258] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1082.258] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1082.258] (II) Loader magic: 0x81ffde0
[  1082.258] (II) Module ABI versions:
[  1082.258] 	X.Org ANSI C Emulation: 0.4
[  1082.258] 	X.Org Video Driver: 10.0
[  1082.258] 	X.Org XInput driver : 12.3
[  1082.258] 	X.Org Server Extension : 5.0
[  1082.259] (--) PCI:*(0:1:0:0) 10de:0326:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
[  1082.259] (II) Open ACPI successful (/var/run/acpid.socket)
[  1082.259] (II) LoadModule: "extmod"
[  1082.260] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1082.270] (II) Module extmod: vendor="X.Org Foundation"
[  1082.270] 	compiled for 1.10.1, module version = 1.0.0
[  1082.270] 	Module class: X.Org Server Extension
[  1082.270] 	ABI class: X.Org Server Extension, version 5.0
[  1082.270] (II) Loading extension MIT-SCREEN-SAVER
[  1082.270] (II) Loading extension XFree86-VidModeExtension
[  1082.270] (II) Loading extension XFree86-DGA
[  1082.270] (II) Loading extension DPMS
[  1082.270] (II) Loading extension XVideo
[  1082.270] (II) Loading extension XVideo-MotionCompensation
[  1082.270] (II) Loading extension X-Resource
[  1082.270] (II) LoadModule: "dbe"
[  1082.270] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1082.275] (II) Module dbe: vendor="X.Org Foundation"
[  1082.275] 	compiled for 1.10.1, module version = 1.0.0
[  1082.275] 	Module class: X.Org Server Extension
[  1082.276] 	ABI class: X.Org Server Extension, version 5.0
[  1082.276] (II) Loading extension DOUBLE-BUFFER
[  1082.276] (II) LoadModule: "glx"
[  1082.276] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  1082.546] (II) Module glx: vendor="NVIDIA Corporation"
[  1082.546] 	compiled for 4.0.2, module version = 1.0.0
[  1082.546] 	Module class: X.Org Server Extension
[  1082.546] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[  1082.546] (II) Loading extension GLX
[  1082.546] (II) LoadModule: "record"
[  1082.546] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1082.559] (II) Module record: vendor="X.Org Foundation"
[  1082.559] 	compiled for 1.10.1, module version = 1.13.0
[  1082.559] 	Module class: X.Org Server Extension
[  1082.559] 	ABI class: X.Org Server Extension, version 5.0
[  1082.559] (II) Loading extension RECORD
[  1082.559] (II) LoadModule: "dri"
[  1082.560] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1082.567] (II) Module dri: vendor="X.Org Foundation"
[  1082.567] 	compiled for 1.10.1, module version = 1.0.0
[  1082.568] 	ABI class: X.Org Server Extension, version 5.0
[  1082.568] (II) Loading extension XFree86-DRI
[  1082.568] (II) LoadModule: "dri2"
[  1082.568] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1082.568] (II) Module dri2: vendor="X.Org Foundation"
[  1082.568] 	compiled for 1.10.1, module version = 1.2.0
[  1082.568] 	ABI class: X.Org Server Extension, version 5.0
[  1082.568] (II) Loading extension DRI2
[  1082.568] (==) Matched nvidia as autoconfigured driver 0
[  1082.569] (==) Matched nouveau as autoconfigured driver 1
[  1082.569] (==) Matched nv as autoconfigured driver 2
[  1082.569] (==) Matched vesa as autoconfigured driver 3
[  1082.569] (==) Matched fbdev as autoconfigured driver 4
[  1082.569] (==) Assigned the driver to the xf86ConfigLayout
[  1082.569] (II) LoadModule: "nvidia"
[  1082.569] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1082.598] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1082.598] 	compiled for 4.0.2, module version = 1.0.0
[  1082.598] 	Module class: X.Org Video Driver
[  1082.598] (II) LoadModule: "nouveau"
[  1082.600] (WW) Warning, couldn't open module nouveau
[  1082.600] (II) UnloadModule: "nouveau"
[  1082.600] (II) Unloading nouveau
[  1082.600] (EE) Failed to load module "nouveau" (module does not exist, 0)
[  1082.600] (II) LoadModule: "nv"
[  1082.601] (WW) Warning, couldn't open module nv
[  1082.601] (II) UnloadModule: "nv"
[  1082.601] (II) Unloading nv
[  1082.601] (EE) Failed to load module "nv" (module does not exist, 0)
[  1082.601] (II) LoadModule: "vesa"
[  1082.601] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1082.615] (II) Module vesa: vendor="X.Org Foundation"
[  1082.615] 	compiled for 1.10.0, module version = 2.3.0
[  1082.615] 	Module class: X.Org Video Driver
[  1082.615] 	ABI class: X.Org Video Driver, version 10.0
[  1082.615] (II) LoadModule: "fbdev"
[  1082.615] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1082.624] (II) Module fbdev: vendor="X.Org Foundation"
[  1082.624] 	compiled for 1.10.0, module version = 0.4.2
[  1082.624] 	ABI class: X.Org Video Driver, version 10.0
[  1082.624] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[  1082.624] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1082.624] (II) VESA: driver for VESA chipsets: vesa
[  1082.624] (II) FBDEV: driver for framebuffer: fbdev
[  1082.624] (--) using VT number 8

[  1082.686] (II) Loading sub module "fb"
[  1082.686] (II) LoadModule: "fb"
[  1082.687] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1082.687] (II) Module fb: vendor="X.Org Foundation"
[  1082.687] 	compiled for 1.10.1, module version = 1.0.0
[  1082.687] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1082.687] (II) Loading sub module "wfb"
[  1082.687] (II) LoadModule: "wfb"
[  1082.688] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1082.710] (II) Module wfb: vendor="X.Org Foundation"
[  1082.710] 	compiled for 1.10.1, module version = 1.0.0
[  1082.710] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1082.710] (II) Loading sub module "ramdac"
[  1082.711] (II) LoadModule: "ramdac"
[  1082.711] (II) Module "ramdac" already built-in
[  1082.711] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1082.711] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1082.711] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1082.711] (WW) Falling back to old probe method for vesa
[  1082.711] (WW) Falling back to old probe method for fbdev
[  1082.711] (II) Loading sub module "fbdevhw"
[  1082.711] (II) LoadModule: "fbdevhw"
[  1082.711] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1082.712] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1082.713] 	compiled for 1.10.1, module version = 0.0.2
[  1082.713] 	ABI class: X.Org Video Driver, version 10.0
[  1082.713] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  1082.713] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  1082.713] (==) NVIDIA(0): RGB weight 888
[  1082.713] (==) NVIDIA(0): Default visual is TrueColor
[  1082.713] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1082.713] (**) NVIDIA(0): Option "NoLogo" "True"
[  1082.713] (**) NVIDIA(0): Enabling RENDER acceleration
[  1082.713] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  1082.713] (II) NVIDIA(0):     enabled.
[  1083.115] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 (NV34) at PCI:1:0:0 (GPU-0)
[  1083.115] (--) NVIDIA(0): Memory: 262144 kBytes
[  1083.115] (--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
[  1083.115] (II) NVIDIA(0): Detected AGP rate: 8X
[  1083.115] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1083.115] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
[  1083.115] (--) NVIDIA(0):     HCM510LSA (CRT-0)
[  1083.115] (--) NVIDIA(0): HCM510LSA (CRT-0): 350.0 MHz maximum pixel clock
[  1083.116] (II) NVIDIA(0): Assigned Display Device: CRT-0
[  1083.116] (==) NVIDIA(0): 
[  1083.116] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  1083.116] (==) NVIDIA(0):     will be used as the requested mode.
[  1083.116] (==) NVIDIA(0): 
[  1083.116] (II) NVIDIA(0): Validated modes:
[  1083.116] (II) NVIDIA(0):     "nvidia-auto-select"
[  1083.116] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[  1083.116] (--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
[  1083.116] (--) NVIDIA(0):     option
[  1083.117] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[  1083.117] (II) UnloadModule: "vesa"
[  1083.117] (II) Unloading vesa
[  1083.117] (II) UnloadModule: "fbdev"
[  1083.117] (II) Unloading fbdev
[  1083.117] (II) UnloadModule: "fbdevhw"
[  1083.117] (II) Unloading fbdevhw
[  1083.117] (--) Depth 24 pixmap format is 32 bpp
[  1083.119] (II) NVIDIA(0): Initialized AGP GART.
[  1083.122] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  1083.207] (II) Loading extension NV-GLX
[  1083.222] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[  1083.225] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[  1083.225] (==) NVIDIA(0): Backing store disabled
[  1083.225] (==) NVIDIA(0): Silken mouse enabled
[  1083.225] (==) NVIDIA(0): DPMS enabled
[  1083.226] (II) Loading extension NV-CONTROL
[  1083.226] (==) RandR enabled
[  1083.226] (II) Initializing built-in extension Generic Event Extension
[  1083.226] (II) Initializing built-in extension SHAPE
[  1083.226] (II) Initializing built-in extension MIT-SHM
[  1083.226] (II) Initializing built-in extension XInputExtension
[  1083.226] (II) Initializing built-in extension XTEST
[  1083.227] (II) Initializing built-in extension BIG-REQUESTS
[  1083.227] (II) Initializing built-in extension SYNC
[  1083.227] (II) Initializing built-in extension XKEYBOARD
[  1083.227] (II) Initializing built-in extension XC-MISC
[  1083.227] (II) Initializing built-in extension SECURITY
[  1083.227] (II) Initializing built-in extension XINERAMA
[  1083.227] (II) Initializing built-in extension XFIXES
[  1083.227] (II) Initializing built-in extension RENDER
[  1083.227] (II) Initializing built-in extension RANDR
[  1083.227] (II) Initializing built-in extension COMPOSITE
[  1083.227] (II) Initializing built-in extension DAMAGE
[  1083.227] (II) Initializing built-in extension GESTURE
[  1083.231] (II) Initializing extension GLX
[  1083.304] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1083.331] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1083.331] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1083.331] (II) LoadModule: "evdev"
[  1083.332] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1083.363] (II) Module evdev: vendor="X.Org Foundation"
[  1083.363] 	compiled for 1.10.0.902, module version = 2.6.0
[  1083.363] 	Module class: X.Org XInput Driver
[  1083.363] 	ABI class: X.Org XInput driver, version 12.3
[  1083.363] (II) Using input driver 'evdev' for 'Power Button'
[  1083.363] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1083.363] (**) Power Button: always reports core events
[  1083.363] (**) Power Button: Device: "/dev/input/event1"
[  1083.364] (--) Power Button: Found keys
[  1083.364] (II) Power Button: Configuring as keyboard
[  1083.364] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1083.364] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1083.364] (**) Option "xkb_rules" "evdev"
[  1083.364] (**) Option "xkb_model" "pc105"
[  1083.364] (**) Option "xkb_layout" "us"
[  1083.368] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1083.368] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1083.368] (II) Using input driver 'evdev' for 'Power Button'
[  1083.368] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1083.368] (**) Power Button: always reports core events
[  1083.368] (**) Power Button: Device: "/dev/input/event0"
[  1083.368] (--) Power Button: Found keys
[  1083.368] (II) Power Button: Configuring as keyboard
[  1083.368] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1083.368] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1083.368] (**) Option "xkb_rules" "evdev"
[  1083.368] (**) Option "xkb_model" "pc105"
[  1083.368] (**) Option "xkb_layout" "us"
[  1083.382] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1083.382] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1083.382] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1083.382] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1083.382] (**) AT Translated Set 2 keyboard: always reports core events
[  1083.382] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1083.383] (--) AT Translated Set 2 keyboard: Found keys
[  1083.383] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  1083.383] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  1083.383] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  1083.383] (**) Option "xkb_rules" "evdev"
[  1083.383] (**) Option "xkb_model" "pc105"
[  1083.383] (**) Option "xkb_layout" "us"
[  1083.384] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[  1083.384] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[  1083.384] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[  1083.384] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1083.384] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[  1083.384] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[  1083.384] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[  1083.384] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[  1083.384] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[  1083.384] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[  1083.384] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[  1083.384] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[  1083.384] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[  1083.384] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1083.384] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[  1083.384] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[  1083.385] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[  1083.385] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[  1083.385] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[  1083.385] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[  1083.385] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[  1083.385] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[  1083.385] (II) No input driver/identifier specified (ignoring)
[  1094.888] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[  3582.062] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm

____________________________________________

*** /etc/X11/xorg.conf
*** ls: -rw-r--r-- 1 root root 83 2011-08-27 04:47:41.000000000 +0530 /etc/X11/xorg.conf

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


____________________________________________

*** /var/log/Xorg.0.log.old
*** ls: -rw-r--r-- 1 root root 19071 2011-10-02 05:01:15.000000000 +0530 /var/log/Xorg.0.log.old
[    98.965] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    98.965] X Protocol Version 11, Revision 0
[    98.965] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    98.965] Current Operating System: Linux sparda 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    98.965] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3a09b439-ffbf-4498-a4ab-4f6f3f93b01c ro quiet splash vt.handoff=7
[    98.965] Build Date: 19 April 2011  03:33:17PM
[    98.965] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    98.965] Current version of pixman: 0.20.2
[    98.965] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    98.965] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    98.966] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct  2 04:44:52 2011
[    98.966] (==) Using config file: "/etc/X11/xorg.conf"
[    98.966] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    98.966] (==) No Layout section.  Using the first Screen section.
[    98.966] (==) No screen section available. Using defaults.
[    98.967] (**) |-->Screen "Default Screen Section" (0)
[    98.967] (**) |   |-->Monitor "<default monitor>"
[    98.967] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    98.967] (**) |   |-->Device "Default Device"
[    98.967] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    98.967] (==) Automatically adding devices
[    98.967] (==) Automatically enabling devices
[    98.967] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    98.967] 	Entry deleted from font path.
[    98.967] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    98.967] 	Entry deleted from font path.
[    98.967] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    98.967] 	Entry deleted from font path.
[    98.967] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    98.967] 	Entry deleted from font path.
[    98.967] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    98.967] 	Entry deleted from font path.
[    98.967] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    98.967] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    98.968] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    98.968] (II) Loader magic: 0x81ffde0
[    98.968] (II) Module ABI versions:
[    98.968] 	X.Org ANSI C Emulation: 0.4
[    98.968] 	X.Org Video Driver: 10.0
[    98.968] 	X.Org XInput driver : 12.3
[    98.968] 	X.Org Server Extension : 5.0
[    98.969] (--) PCI:*(0:1:0:0) 10de:0326:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
[    98.969] (II) Open ACPI successful (/var/run/acpid.socket)
[    98.969] (II) LoadModule: "extmod"
[    98.970] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    98.970] (II) Module extmod: vendor="X.Org Foundation"
[    98.970] 	compiled for 1.10.1, module version = 1.0.0
[    98.970] 	Module class: X.Org Server Extension
[    98.970] 	ABI class: X.Org Server Extension, version 5.0
[    98.970] (II) Loading extension MIT-SCREEN-SAVER
[    98.970] (II) Loading extension XFree86-VidModeExtension
[    98.970] (II) Loading extension XFree86-DGA
[    98.970] (II) Loading extension DPMS
[    98.970] (II) Loading extension XVideo
[    98.970] (II) Loading extension XVideo-MotionCompensation
[    98.970] (II) Loading extension X-Resource
[    98.970] (II) LoadModule: "dbe"
[    98.971] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    98.971] (II) Module dbe: vendor="X.Org Foundation"
[    98.971] 	compiled for 1.10.1, module version = 1.0.0
[    98.971] 	Module class: X.Org Server Extension
[    98.971] 	ABI class: X.Org Server Extension, version 5.0
[    98.971] (II) Loading extension DOUBLE-BUFFER
[    98.971] (II) LoadModule: "glx"
[    98.971] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    99.036] (II) Module glx: vendor="NVIDIA Corporation"
[    99.036] 	compiled for 4.0.2, module version = 1.0.0
[    99.037] 	Module class: X.Org Server Extension
[    99.037] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[    99.037] (II) Loading extension GLX
[    99.037] (II) LoadModule: "record"
[    99.037] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    99.037] (II) Module record: vendor="X.Org Foundation"
[    99.037] 	compiled for 1.10.1, module version = 1.13.0
[    99.037] 	Module class: X.Org Server Extension
[    99.037] 	ABI class: X.Org Server Extension, version 5.0
[    99.037] (II) Loading extension RECORD
[    99.037] (II) LoadModule: "dri"
[    99.037] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    99.052] (II) Module dri: vendor="X.Org Foundation"
[    99.052] 	compiled for 1.10.1, module version = 1.0.0
[    99.052] 	ABI class: X.Org Server Extension, version 5.0
[    99.052] (II) Loading extension XFree86-DRI
[    99.052] (II) LoadModule: "dri2"
[    99.052] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    99.052] (II) Module dri2: vendor="X.Org Foundation"
[    99.052] 	compiled for 1.10.1, module version = 1.2.0
[    99.052] 	ABI class: X.Org Server Extension, version 5.0
[    99.052] (II) Loading extension DRI2
[    99.052] (==) Matched nvidia as autoconfigured driver 0
[    99.052] (==) Matched nouveau as autoconfigured driver 1
[    99.052] (==) Matched nv as autoconfigured driver 2
[    99.052] (==) Matched vesa as autoconfigured driver 3
[    99.052] (==) Matched fbdev as autoconfigured driver 4
[    99.052] (==) Assigned the driver to the xf86ConfigLayout
[    99.052] (II) LoadModule: "nvidia"
[    99.052] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    99.053] (II) Module nvidia: vendor="NVIDIA Corporation"
[    99.053] 	compiled for 4.0.2, module version = 1.0.0
[    99.053] 	Module class: X.Org Video Driver
[    99.053] (II) LoadModule: "nouveau"
[    99.055] (WW) Warning, couldn't open module nouveau
[    99.055] (II) UnloadModule: "nouveau"
[    99.055] (II) Unloading nouveau
[    99.055] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    99.055] (II) LoadModule: "nv"
[    99.056] (WW) Warning, couldn't open module nv
[    99.056] (II) UnloadModule: "nv"
[    99.056] (II) Unloading nv
[    99.056] (EE) Failed to load module "nv" (module does not exist, 0)
[    99.056] (II) LoadModule: "vesa"
[    99.056] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    99.057] (II) Module vesa: vendor="X.Org Foundation"
[    99.057] 	compiled for 1.10.0, module version = 2.3.0
[    99.057] 	Module class: X.Org Video Driver
[    99.057] 	ABI class: X.Org Video Driver, version 10.0
[    99.057] (II) LoadModule: "fbdev"
[    99.057] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    99.057] (II) Module fbdev: vendor="X.Org Foundation"
[    99.057] 	compiled for 1.10.0, module version = 0.4.2
[    99.057] 	ABI class: X.Org Video Driver, version 10.0
[    99.057] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[    99.057] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    99.057] (II) VESA: driver for VESA chipsets: vesa
[    99.057] (II) FBDEV: driver for framebuffer: fbdev
[    99.057] (--) using VT number 1

[    99.118] (II) Loading sub module "fb"
[    99.118] (II) LoadModule: "fb"
[    99.119] (II) Loading /usr/lib/xorg/modules/libfb.so
[    99.119] (II) Module fb: vendor="X.Org Foundation"
[    99.119] 	compiled for 1.10.1, module version = 1.0.0
[    99.119] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    99.119] (II) Loading sub module "wfb"
[    99.119] (II) LoadModule: "wfb"
[    99.120] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    99.120] (II) Module wfb: vendor="X.Org Foundation"
[    99.120] 	compiled for 1.10.1, module version = 1.0.0
[    99.120] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    99.120] (II) Loading sub module "ramdac"
[    99.120] (II) LoadModule: "ramdac"
[    99.120] (II) Module "ramdac" already built-in
[    99.120] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    99.120] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    99.120] (II) Loading /usr/lib/xorg/modules/libfb.so
[    99.120] (WW) Falling back to old probe method for vesa
[    99.120] (WW) Falling back to old probe method for fbdev
[    99.121] (II) Loading sub module "fbdevhw"
[    99.121] (II) LoadModule: "fbdevhw"
[    99.121] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    99.121] (II) Module fbdevhw: vendor="X.Org Foundation"
[    99.121] 	compiled for 1.10.1, module version = 0.0.2
[    99.121] 	ABI class: X.Org Video Driver, version 10.0
[    99.121] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    99.121] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    99.121] (==) NVIDIA(0): RGB weight 888
[    99.121] (==) NVIDIA(0): Default visual is TrueColor
[    99.121] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    99.121] (**) NVIDIA(0): Option "NoLogo" "True"
[    99.121] (**) NVIDIA(0): Enabling RENDER acceleration
[    99.122] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    99.122] (II) NVIDIA(0):     enabled.
[    99.523] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 (NV34) at PCI:1:0:0 (GPU-0)
[    99.523] (--) NVIDIA(0): Memory: 262144 kBytes
[    99.523] (--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
[    99.523] (II) NVIDIA(0): Detected AGP rate: 8X
[    99.523] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    99.523] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
[    99.523] (--) NVIDIA(0):     HCM510LSA (CRT-0)
[    99.523] (--) NVIDIA(0): HCM510LSA (CRT-0): 350.0 MHz maximum pixel clock
[    99.524] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    99.524] (==) NVIDIA(0): 
[    99.524] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    99.524] (==) NVIDIA(0):     will be used as the requested mode.
[    99.524] (==) NVIDIA(0): 
[    99.524] (II) NVIDIA(0): Validated modes:
[    99.524] (II) NVIDIA(0):     "nvidia-auto-select"
[    99.524] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    99.524] (--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
[    99.524] (--) NVIDIA(0):     option
[    99.525] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    99.525] (II) UnloadModule: "vesa"
[    99.525] (II) Unloading vesa
[    99.525] (II) UnloadModule: "fbdev"
[    99.525] (II) Unloading fbdev
[    99.525] (II) UnloadModule: "fbdevhw"
[    99.525] (II) Unloading fbdevhw
[    99.525] (--) Depth 24 pixmap format is 32 bpp
[    99.527] (II) NVIDIA(0): Initialized AGP GART.
[    99.530] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    99.617] (II) Loading extension NV-GLX
[    99.631] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    99.635] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    99.635] (==) NVIDIA(0): Backing store disabled
[    99.635] (==) NVIDIA(0): Silken mouse enabled
[    99.635] (==) NVIDIA(0): DPMS enabled
[    99.635] (II) Loading extension NV-CONTROL
[    99.636] (==) RandR enabled
[    99.636] (II) Initializing built-in extension Generic Event Extension
[    99.636] (II) Initializing built-in extension SHAPE
[    99.636] (II) Initializing built-in extension MIT-SHM
[    99.636] (II) Initializing built-in extension XInputExtension
[    99.636] (II) Initializing built-in extension XTEST
[    99.636] (II) Initializing built-in extension BIG-REQUESTS
[    99.636] (II) Initializing built-in extension SYNC
[    99.636] (II) Initializing built-in extension XKEYBOARD
[    99.636] (II) Initializing built-in extension XC-MISC
[    99.636] (II) Initializing built-in extension SECURITY
[    99.636] (II) Initializing built-in extension XINERAMA
[    99.636] (II) Initializing built-in extension XFIXES
[    99.636] (II) Initializing built-in extension RENDER
[    99.636] (II) Initializing built-in extension RANDR
[    99.636] (II) Initializing built-in extension COMPOSITE
[    99.636] (II) Initializing built-in extension DAMAGE
[    99.636] (II) Initializing built-in extension GESTURE
[    99.640] (II) Initializing extension GLX
[    99.668] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    99.684] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    99.684] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    99.684] (II) LoadModule: "evdev"
[    99.685] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    99.686] (II) Module evdev: vendor="X.Org Foundation"
[    99.686] 	compiled for 1.10.0.902, module version = 2.6.0
[    99.686] 	Module class: X.Org XInput Driver
[    99.686] 	ABI class: X.Org XInput driver, version 12.3
[    99.686] (II) Using input driver 'evdev' for 'Power Button'
[    99.686] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    99.686] (**) Power Button: always reports core events
[    99.686] (**) Power Button: Device: "/dev/input/event1"
[    99.686] (--) Power Button: Found keys
[    99.686] (II) Power Button: Configuring as keyboard
[    99.686] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    99.686] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    99.686] (**) Option "xkb_rules" "evdev"
[    99.686] (**) Option "xkb_model" "pc105"
[    99.686] (**) Option "xkb_layout" "us"
[    99.690] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    99.690] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    99.690] (II) Using input driver 'evdev' for 'Power Button'
[    99.690] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    99.690] (**) Power Button: always reports core events
[    99.690] (**) Power Button: Device: "/dev/input/event0"
[    99.690] (--) Power Button: Found keys
[    99.690] (II) Power Button: Configuring as keyboard
[    99.690] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    99.690] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    99.691] (**) Option "xkb_rules" "evdev"
[    99.691] (**) Option "xkb_model" "pc105"
[    99.691] (**) Option "xkb_layout" "us"
[    99.704] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    99.704] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    99.704] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    99.704] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    99.704] (**) AT Translated Set 2 keyboard: always reports core events
[    99.704] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    99.704] (--) AT Translated Set 2 keyboard: Found keys
[    99.704] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    99.704] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    99.704] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    99.704] (**) Option "xkb_rules" "evdev"
[    99.705] (**) Option "xkb_model" "pc105"
[    99.705] (**) Option "xkb_layout" "us"
[    99.705] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    99.705] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    99.706] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    99.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    99.706] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    99.706] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    99.706] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    99.706] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    99.706] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    99.706] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    99.706] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    99.706] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    99.706] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    99.706] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    99.706] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    99.706] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    99.706] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    99.706] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    99.706] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    99.706] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    99.706] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    99.707] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    99.707] (II) No input driver/identifier specified (ignoring)
[   106.551] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[  1081.136] 
Backtrace:
[  1081.136] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
[  1081.136] 1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
[  1081.136] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb4140c]
[  1081.136] 3: /usr/bin/X (0x8048000+0x27f1e) [0x806ff1e]
[  1081.137] 4: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[  1081.137] 5: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x649e37]
[  1081.137] 6: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[  1081.137] 
Caught signal 3 (Quit). Server aborting
[  1081.137] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  1081.137] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1081.137] 
[  1081.152] (II) Power Button: Close
[  1081.152] (II) UnloadModule: "evdev"
[  1081.152] (II) Unloading evdev
[  1081.152] (II) Power Button: Close
[  1081.152] (II) UnloadModule: "evdev"
[  1081.152] (II) Unloading evdev
[  1081.153] (II) AT Translated Set 2 keyboard: Close
[  1081.153] (II) UnloadModule: "evdev"
[  1081.153] (II) Unloading evdev
[  1081.153] (II) ImPS/2 Generic Wheel Mouse: Close
[  1081.153] (II) UnloadModule: "evdev"
[  1081.153] (II) Unloading evdev
[  1081.680]  ddxSigGiveUp: Closing log

____________________________________________

*** /var/log/Xorg.1.log
*** ls: -rw-r--r-- 1 root root 18255 2011-09-24 14:54:31.000000000 +0530 /var/log/Xorg.1.log
[  5176.988] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  5176.988] X Protocol Version 11, Revision 0
[  5176.988] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  5176.988] Current Operating System: Linux sparda 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[  5176.988] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3a09b439-ffbf-4498-a4ab-4f6f3f93b01c ro quiet splash vt.handoff=7
[  5176.988] Build Date: 19 April 2011  03:33:17PM
[  5176.988] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  5176.988] Current version of pixman: 0.20.2
[  5176.988] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  5176.988] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  5176.989] (==) Log file: "/var/log/Xorg.1.log", Time: Sat Sep 24 14:46:01 2011
[  5177.046] (==) Using config file: "/etc/X11/xorg.conf"
[  5177.046] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  5177.072] (==) No Layout section.  Using the first Screen section.
[  5177.072] (==) No screen section available. Using defaults.
[  5177.072] (**) |-->Screen "Default Screen Section" (0)
[  5177.072] (**) |   |-->Monitor "<default monitor>"
[  5177.073] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[  5177.073] (**) |   |-->Device "Default Device"
[  5177.073] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  5177.073] (==) Automatically adding devices
[  5177.073] (==) Automatically enabling devices
[  5177.117] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  5177.117] 	Entry deleted from font path.
[  5177.117] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  5177.117] 	Entry deleted from font path.
[  5177.117] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  5177.117] 	Entry deleted from font path.
[  5177.130] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  5177.131] 	Entry deleted from font path.
[  5177.131] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  5177.131] 	Entry deleted from font path.
[  5177.140] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  5177.140] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  5177.140] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  5177.140] (II) Loader magic: 0x81ffde0
[  5177.140] (II) Module ABI versions:
[  5177.140] 	X.Org ANSI C Emulation: 0.4
[  5177.140] 	X.Org Video Driver: 10.0
[  5177.140] 	X.Org XInput driver : 12.3
[  5177.140] 	X.Org Server Extension : 5.0
[  5177.141] (--) PCI:*(0:1:0:0) 10de:0326:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
[  5177.141] (II) Open ACPI successful (/var/run/acpid.socket)
[  5177.141] (II) LoadModule: "extmod"
[  5177.199] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  5177.199] (II) Module extmod: vendor="X.Org Foundation"
[  5177.199] 	compiled for 1.10.1, module version = 1.0.0
[  5177.199] 	Module class: X.Org Server Extension
[  5177.199] 	ABI class: X.Org Server Extension, version 5.0
[  5177.199] (II) Loading extension MIT-SCREEN-SAVER
[  5177.199] (II) Loading extension XFree86-VidModeExtension
[  5177.199] (II) Loading extension XFree86-DGA
[  5177.199] (II) Loading extension DPMS
[  5177.199] (II) Loading extension XVideo
[  5177.199] (II) Loading extension XVideo-MotionCompensation
[  5177.199] (II) Loading extension X-Resource
[  5177.199] (II) LoadModule: "dbe"
[  5177.199] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  5177.208] (II) Module dbe: vendor="X.Org Foundation"
[  5177.208] 	compiled for 1.10.1, module version = 1.0.0
[  5177.208] 	Module class: X.Org Server Extension
[  5177.208] 	ABI class: X.Org Server Extension, version 5.0
[  5177.208] (II) Loading extension DOUBLE-BUFFER
[  5177.208] (II) LoadModule: "glx"
[  5177.208] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  5177.512] (II) Module glx: vendor="NVIDIA Corporation"
[  5177.512] 	compiled for 4.0.2, module version = 1.0.0
[  5177.512] 	Module class: X.Org Server Extension
[  5177.512] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[  5177.512] (II) Loading extension GLX
[  5177.512] (II) LoadModule: "record"
[  5177.513] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  5177.525] (II) Module record: vendor="X.Org Foundation"
[  5177.525] 	compiled for 1.10.1, module version = 1.13.0
[  5177.525] 	Module class: X.Org Server Extension
[  5177.525] 	ABI class: X.Org Server Extension, version 5.0
[  5177.525] (II) Loading extension RECORD
[  5177.525] (II) LoadModule: "dri"
[  5177.525] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  5177.575] (II) Module dri: vendor="X.Org Foundation"
[  5177.575] 	compiled for 1.10.1, module version = 1.0.0
[  5177.575] 	ABI class: X.Org Server Extension, version 5.0
[  5177.575] (II) Loading extension XFree86-DRI
[  5177.575] (II) LoadModule: "dri2"
[  5177.600] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  5177.610] (II) Module dri2: vendor="X.Org Foundation"
[  5177.610] 	compiled for 1.10.1, module version = 1.2.0
[  5177.610] 	ABI class: X.Org Server Extension, version 5.0
[  5177.610] (II) Loading extension DRI2
[  5177.610] (==) Matched nvidia as autoconfigured driver 0
[  5177.610] (==) Matched nouveau as autoconfigured driver 1
[  5177.610] (==) Matched nv as autoconfigured driver 2
[  5177.610] (==) Matched vesa as autoconfigured driver 3
[  5177.610] (==) Matched fbdev as autoconfigured driver 4
[  5177.610] (==) Assigned the driver to the xf86ConfigLayout
[  5177.610] (II) LoadModule: "nvidia"
[  5177.610] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  5177.664] (II) Module nvidia: vendor="NVIDIA Corporation"
[  5177.664] 	compiled for 4.0.2, module version = 1.0.0
[  5177.664] 	Module class: X.Org Video Driver
[  5177.671] (II) LoadModule: "nouveau"
[  5177.704] (WW) Warning, couldn't open module nouveau
[  5177.704] (II) UnloadModule: "nouveau"
[  5177.704] (II) Unloading nouveau
[  5177.704] (EE) Failed to load module "nouveau" (module does not exist, 0)
[  5177.704] (II) LoadModule: "nv"
[  5177.705] (WW) Warning, couldn't open module nv
[  5177.705] (II) UnloadModule: "nv"
[  5177.705] (II) Unloading nv
[  5177.705] (EE) Failed to load module "nv" (module does not exist, 0)
[  5177.705] (II) LoadModule: "vesa"
[  5177.705] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  5177.713] (II) Module vesa: vendor="X.Org Foundation"
[  5177.713] 	compiled for 1.10.0, module version = 2.3.0
[  5177.713] 	Module class: X.Org Video Driver
[  5177.713] 	ABI class: X.Org Video Driver, version 10.0
[  5177.713] (II) LoadModule: "fbdev"
[  5177.714] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  5177.723] (II) Module fbdev: vendor="X.Org Foundation"
[  5177.723] 	compiled for 1.10.0, module version = 0.4.2
[  5177.723] 	ABI class: X.Org Video Driver, version 10.0
[  5177.723] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[  5177.730] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  5177.730] (II) VESA: driver for VESA chipsets: vesa
[  5177.730] (II) FBDEV: driver for framebuffer: fbdev
[  5177.730] (--) using VT number 8

[  5178.372] (II) Loading sub module "fb"
[  5178.372] (II) LoadModule: "fb"
[  5178.373] (II) Loading /usr/lib/xorg/modules/libfb.so
[  5178.374] (II) Module fb: vendor="X.Org Foundation"
[  5178.374] 	compiled for 1.10.1, module version = 1.0.0
[  5178.374] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  5178.374] (II) Loading sub module "wfb"
[  5178.374] (II) LoadModule: "wfb"
[  5178.375] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  5178.390] (II) Module wfb: vendor="X.Org Foundation"
[  5178.390] 	compiled for 1.10.1, module version = 1.0.0
[  5178.390] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  5178.390] (II) Loading sub module "ramdac"
[  5178.390] (II) LoadModule: "ramdac"
[  5178.390] (II) Module "ramdac" already built-in
[  5178.390] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  5178.390] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  5178.390] (II) Loading /usr/lib/xorg/modules/libfb.so
[  5178.390] (WW) Falling back to old probe method for vesa
[  5178.390] (WW) Falling back to old probe method for fbdev
[  5178.390] (II) Loading sub module "fbdevhw"
[  5178.390] (II) LoadModule: "fbdevhw"
[  5178.391] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  5178.394] (II) Module fbdevhw: vendor="X.Org Foundation"
[  5178.394] 	compiled for 1.10.1, module version = 0.0.2
[  5178.394] 	ABI class: X.Org Video Driver, version 10.0
[  5178.394] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  5178.394] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  5178.394] (==) NVIDIA(0): RGB weight 888
[  5178.394] (==) NVIDIA(0): Default visual is TrueColor
[  5178.394] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  5178.394] (**) NVIDIA(0): Option "NoLogo" "True"
[  5178.395] (**) NVIDIA(0): Enabling RENDER acceleration
[  5178.395] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  5178.395] (II) NVIDIA(0):     enabled.
[  5178.561] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 (NV34) at PCI:1:0:0 (GPU-0)
[  5178.561] (--) NVIDIA(0): Memory: 262144 kBytes
[  5178.561] (--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
[  5178.561] (II) NVIDIA(0): Detected AGP rate: 8X
[  5178.561] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  5178.561] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
[  5178.561] (--) NVIDIA(0):     HCM510LSA (CRT-0)
[  5178.561] (--) NVIDIA(0): HCM510LSA (CRT-0): 350.0 MHz maximum pixel clock
[  5178.562] (II) NVIDIA(0): Assigned Display Device: CRT-0
[  5178.562] (==) NVIDIA(0): 
[  5178.562] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  5178.562] (==) NVIDIA(0):     will be used as the requested mode.
[  5178.562] (==) NVIDIA(0): 
[  5178.562] (II) NVIDIA(0): Validated modes:
[  5178.562] (II) NVIDIA(0):     "nvidia-auto-select"
[  5178.562] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[  5178.563] (--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
[  5178.563] (--) NVIDIA(0):     option
[  5178.563] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[  5178.609] (II) UnloadModule: "vesa"
[  5178.609] (II) Unloading vesa
[  5178.609] (II) UnloadModule: "fbdev"
[  5178.609] (II) Unloading fbdev
[  5178.609] (II) UnloadModule: "fbdevhw"
[  5178.609] (II) Unloading fbdevhw
[  5178.609] (--) Depth 24 pixmap format is 32 bpp
[  5178.612] (II) NVIDIA(0): Initialized AGP GART.
[  5178.616] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  5178.702] (II) Loading extension NV-GLX
[  5178.748] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[  5178.751] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[  5178.751] (==) NVIDIA(0): Backing store disabled
[  5178.751] (==) NVIDIA(0): Silken mouse enabled
[  5178.751] (==) NVIDIA(0): DPMS enabled
[  5178.751] (II) Loading extension NV-CONTROL
[  5178.752] (==) RandR enabled
[  5178.752] (II) Initializing built-in extension Generic Event Extension
[  5178.752] (II) Initializing built-in extension SHAPE
[  5178.752] (II) Initializing built-in extension MIT-SHM
[  5178.752] (II) Initializing built-in extension XInputExtension
[  5178.752] (II) Initializing built-in extension XTEST
[  5178.752] (II) Initializing built-in extension BIG-REQUESTS
[  5178.752] (II) Initializing built-in extension SYNC
[  5178.752] (II) Initializing built-in extension XKEYBOARD
[  5178.752] (II) Initializing built-in extension XC-MISC
[  5178.752] (II) Initializing built-in extension SECURITY
[  5178.752] (II) Initializing built-in extension XINERAMA
[  5178.752] (II) Initializing built-in extension XFIXES
[  5178.752] (II) Initializing built-in extension RENDER
[  5178.752] (II) Initializing built-in extension RANDR
[  5178.752] (II) Initializing built-in extension COMPOSITE
[  5178.752] (II) Initializing built-in extension DAMAGE
[  5178.752] (II) Initializing built-in extension GESTURE
[  5178.756] (II) Initializing extension GLX
[  5178.879] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  5178.903] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  5178.904] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  5178.904] (II) LoadModule: "evdev"
[  5178.904] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5178.952] (II) Module evdev: vendor="X.Org Foundation"
[  5178.952] 	compiled for 1.10.0.902, module version = 2.6.0
[  5178.952] 	Module class: X.Org XInput Driver
[  5178.952] 	ABI class: X.Org XInput driver, version 12.3
[  5178.952] (II) Using input driver 'evdev' for 'Power Button'
[  5178.952] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5178.953] (**) Power Button: always reports core events
[  5178.953] (**) Power Button: Device: "/dev/input/event1"
[  5178.956] (--) Power Button: Found keys
[  5178.956] (II) Power Button: Configuring as keyboard
[  5178.956] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  5178.956] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  5178.956] (**) Option "xkb_rules" "evdev"
[  5178.956] (**) Option "xkb_model" "pc105"
[  5178.956] (**) Option "xkb_layout" "us"
[  5178.959] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  5178.960] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  5178.960] (II) Using input driver 'evdev' for 'Power Button'
[  5178.960] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5178.960] (**) Power Button: always reports core events
[  5178.960] (**) Power Button: Device: "/dev/input/event0"
[  5178.960] (--) Power Button: Found keys
[  5178.960] (II) Power Button: Configuring as keyboard
[  5178.960] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  5178.960] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  5178.960] (**) Option "xkb_rules" "evdev"
[  5178.960] (**) Option "xkb_model" "pc105"
[  5178.960] (**) Option "xkb_layout" "us"
[  5178.985] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  5178.985] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  5178.985] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  5178.985] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5178.985] (**) AT Translated Set 2 keyboard: always reports core events
[  5178.985] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  5178.985] (--) AT Translated Set 2 keyboard: Found keys
[  5178.985] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  5178.985] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  5178.985] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  5178.985] (**) Option "xkb_rules" "evdev"
[  5178.985] (**) Option "xkb_model" "pc105"
[  5178.985] (**) Option "xkb_layout" "us"
[  5178.986] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[  5178.986] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[  5178.986] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[  5178.986] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5178.986] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[  5178.986] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[  5179.004] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[  5179.004] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[  5179.004] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[  5179.004] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[  5179.004] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[  5179.004] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[  5179.004] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[  5179.004] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  5179.004] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[  5179.004] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[  5179.004] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[  5179.004] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[  5179.004] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[  5179.004] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[  5179.005] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[  5179.005] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[  5179.005] (II) No input driver/identifier specified (ignoring)
[  5687.049] (II) ImPS/2 Generic Wheel Mouse: Close
[  5687.050] (II) UnloadModule: "evdev"
[  5687.050] (II) Unloading evdev
[  5687.050] (II) AT Translated Set 2 keyboard: Close
[  5687.050] (II) UnloadModule: "evdev"
[  5687.050] (II) Unloading evdev
[  5687.050] (II) Power Button: Close
[  5687.050] (II) UnloadModule: "evdev"
[  5687.050] (II) Unloading evdev
[  5687.050] (II) Power Button: Close
[  5687.050] (II) UnloadModule: "evdev"
[  5687.050] (II) Unloading evdev
[  5687.099]  ddxSigGiveUp: Closing log

____________________________________________

*** /var/log/Xorg.1.log.old
*** ls: -rw-r--r-- 1 root root 18255 2011-09-05 19:48:36.000000000 +0530 /var/log/Xorg.1.log.old
[  1631.412] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  1631.413] X Protocol Version 11, Revision 0
[  1631.413] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  1631.413] Current Operating System: Linux sparda 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[  1631.413] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3a09b439-ffbf-4498-a4ab-4f6f3f93b01c ro quiet splash vt.handoff=7
[  1631.413] Build Date: 19 April 2011  03:33:17PM
[  1631.413] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1631.413] Current version of pixman: 0.20.2
[  1631.413] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[  1631.413] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1631.413] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Sep  5 19:47:58 2011
[  1631.413] (==) Using config file: "/etc/X11/xorg.conf"
[  1631.413] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1631.414] (==) No Layout section.  Using the first Screen section.
[  1631.414] (==) No screen section available. Using defaults.
[  1631.414] (**) |-->Screen "Default Screen Section" (0)
[  1631.414] (**) |   |-->Monitor "<default monitor>"
[  1631.414] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[  1631.414] (**) |   |-->Device "Default Device"
[  1631.414] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1631.414] (==) Automatically adding devices
[  1631.414] (==) Automatically enabling devices
[  1631.414] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1631.414] 	Entry deleted from font path.
[  1631.414] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1631.415] 	Entry deleted from font path.
[  1631.415] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1631.415] 	Entry deleted from font path.
[  1631.415] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1631.415] 	Entry deleted from font path.
[  1631.415] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1631.415] 	Entry deleted from font path.
[  1631.415] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1631.415] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1631.415] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1631.415] (II) Loader magic: 0x81ffde0
[  1631.415] (II) Module ABI versions:
[  1631.415] 	X.Org ANSI C Emulation: 0.4
[  1631.415] 	X.Org Video Driver: 10.0
[  1631.415] 	X.Org XInput driver : 12.3
[  1631.415] 	X.Org Server Extension : 5.0
[  1631.416] (--) PCI:*(0:1:0:0) 10de:0326:0000:0000 rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
[  1631.417] (II) Open ACPI successful (/var/run/acpid.socket)
[  1631.417] (II) LoadModule: "extmod"
[  1631.418] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1631.419] (II) Module extmod: vendor="X.Org Foundation"
[  1631.419] 	compiled for 1.10.1, module version = 1.0.0
[  1631.419] 	Module class: X.Org Server Extension
[  1631.419] 	ABI class: X.Org Server Extension, version 5.0
[  1631.419] (II) Loading extension MIT-SCREEN-SAVER
[  1631.419] (II) Loading extension XFree86-VidModeExtension
[  1631.419] (II) Loading extension XFree86-DGA
[  1631.419] (II) Loading extension DPMS
[  1631.419] (II) Loading extension XVideo
[  1631.419] (II) Loading extension XVideo-MotionCompensation
[  1631.419] (II) Loading extension X-Resource
[  1631.419] (II) LoadModule: "dbe"
[  1631.420] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1631.420] (II) Module dbe: vendor="X.Org Foundation"
[  1631.420] 	compiled for 1.10.1, module version = 1.0.0
[  1631.420] 	Module class: X.Org Server Extension
[  1631.420] 	ABI class: X.Org Server Extension, version 5.0
[  1631.420] (II) Loading extension DOUBLE-BUFFER
[  1631.420] (II) LoadModule: "glx"
[  1631.421] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[  1631.462] (II) Module glx: vendor="NVIDIA Corporation"
[  1631.462] 	compiled for 4.0.2, module version = 1.0.0
[  1631.462] 	Module class: X.Org Server Extension
[  1631.462] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[  1631.462] (II) Loading extension GLX
[  1631.462] (II) LoadModule: "record"
[  1631.463] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1631.463] (II) Module record: vendor="X.Org Foundation"
[  1631.463] 	compiled for 1.10.1, module version = 1.13.0
[  1631.463] 	Module class: X.Org Server Extension
[  1631.463] 	ABI class: X.Org Server Extension, version 5.0
[  1631.463] (II) Loading extension RECORD
[  1631.463] (II) LoadModule: "dri"
[  1631.464] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1631.464] (II) Module dri: vendor="X.Org Foundation"
[  1631.464] 	compiled for 1.10.1, module version = 1.0.0
[  1631.464] 	ABI class: X.Org Server Extension, version 5.0
[  1631.464] (II) Loading extension XFree86-DRI
[  1631.464] (II) LoadModule: "dri2"
[  1631.465] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1631.465] (II) Module dri2: vendor="X.Org Foundation"
[  1631.465] 	compiled for 1.10.1, module version = 1.2.0
[  1631.465] 	ABI class: X.Org Server Extension, version 5.0
[  1631.465] (II) Loading extension DRI2
[  1631.465] (==) Matched nvidia as autoconfigured driver 0
[  1631.465] (==) Matched nouveau as autoconfigured driver 1
[  1631.465] (==) Matched nv as autoconfigured driver 2
[  1631.465] (==) Matched vesa as autoconfigured driver 3
[  1631.465] (==) Matched fbdev as autoconfigured driver 4
[  1631.465] (==) Assigned the driver to the xf86ConfigLayout
[  1631.465] (II) LoadModule: "nvidia"
[  1631.465] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1631.467] (II) Module nvidia: vendor="NVIDIA Corporation"
[  1631.467] 	compiled for 4.0.2, module version = 1.0.0
[  1631.467] 	Module class: X.Org Video Driver
[  1631.467] (II) LoadModule: "nouveau"
[  1631.469] (WW) Warning, couldn't open module nouveau
[  1631.469] (II) UnloadModule: "nouveau"
[  1631.469] (II) Unloading nouveau
[  1631.469] (EE) Failed to load module "nouveau" (module does not exist, 0)
[  1631.469] (II) LoadModule: "nv"
[  1631.470] (WW) Warning, couldn't open module nv
[  1631.470] (II) UnloadModule: "nv"
[  1631.470] (II) Unloading nv
[  1631.470] (EE) Failed to load module "nv" (module does not exist, 0)
[  1631.470] (II) LoadModule: "vesa"
[  1631.470] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1631.471] (II) Module vesa: vendor="X.Org Foundation"
[  1631.471] 	compiled for 1.10.0, module version = 2.3.0
[  1631.471] 	Module class: X.Org Video Driver
[  1631.471] 	ABI class: X.Org Video Driver, version 10.0
[  1631.471] (II) LoadModule: "fbdev"
[  1631.471] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1631.472] (II) Module fbdev: vendor="X.Org Foundation"
[  1631.472] 	compiled for 1.10.0, module version = 0.4.2
[  1631.472] 	ABI class: X.Org Video Driver, version 10.0
[  1631.472] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[  1631.472] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  1631.472] (II) VESA: driver for VESA chipsets: vesa
[  1631.472] (II) FBDEV: driver for framebuffer: fbdev
[  1631.472] (--) using VT number 8

[  1632.130] (II) Loading sub module "fb"
[  1632.131] (II) LoadModule: "fb"
[  1632.132] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1632.132] (II) Module fb: vendor="X.Org Foundation"
[  1632.132] 	compiled for 1.10.1, module version = 1.0.0
[  1632.132] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1632.132] (II) Loading sub module "wfb"
[  1632.132] (II) LoadModule: "wfb"
[  1632.133] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1632.134] (II) Module wfb: vendor="X.Org Foundation"
[  1632.134] 	compiled for 1.10.1, module version = 1.0.0
[  1632.134] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1632.134] (II) Loading sub module "ramdac"
[  1632.134] (II) LoadModule: "ramdac"
[  1632.134] (II) Module "ramdac" already built-in
[  1632.134] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[  1632.134] (II) Loading /usr/lib/xorg/modules/libwfb.so
[  1632.134] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1632.134] (WW) Falling back to old probe method for vesa
[  1632.135] (WW) Falling back to old probe method for fbdev
[  1632.135] (II) Loading sub module "fbdevhw"
[  1632.135] (II) LoadModule: "fbdevhw"
[  1632.135] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1632.135] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1632.136] 	compiled for 1.10.1, module version = 0.0.2
[  1632.136] 	ABI class: X.Org Video Driver, version 10.0
[  1632.136] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  1632.136] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[  1632.136] (==) NVIDIA(0): RGB weight 888
[  1632.136] (==) NVIDIA(0): Default visual is TrueColor
[  1632.136] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1632.136] (**) NVIDIA(0): Option "NoLogo" "True"
[  1632.136] (**) NVIDIA(0): Enabling RENDER acceleration
[  1632.136] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[  1632.137] (II) NVIDIA(0):     enabled.
[  1632.261] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 (NV34) at PCI:1:0:0 (GPU-0)
[  1632.261] (--) NVIDIA(0): Memory: 262144 kBytes
[  1632.261] (--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
[  1632.261] (II) NVIDIA(0): Detected AGP rate: 8X
[  1632.261] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[  1632.261] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
[  1632.261] (--) NVIDIA(0):     HCM510LSA (CRT-0)
[  1632.261] (--) NVIDIA(0): HCM510LSA (CRT-0): 350.0 MHz maximum pixel clock
[  1632.262] (II) NVIDIA(0): Assigned Display Device: CRT-0
[  1632.262] (==) NVIDIA(0): 
[  1632.262] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  1632.262] (==) NVIDIA(0):     will be used as the requested mode.
[  1632.262] (==) NVIDIA(0): 
[  1632.263] (II) NVIDIA(0): Validated modes:
[  1632.263] (II) NVIDIA(0):     "nvidia-auto-select"
[  1632.263] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[  1632.263] (--) NVIDIA(0): DPI set to (86, 84); computed from "UseEdidDpi" X config
[  1632.264] (--) NVIDIA(0):     option
[  1632.264] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[  1632.264] (II) UnloadModule: "vesa"
[  1632.264] (II) Unloading vesa
[  1632.264] (II) UnloadModule: "fbdev"
[  1632.264] (II) Unloading fbdev
[  1632.264] (II) UnloadModule: "fbdevhw"
[  1632.264] (II) Unloading fbdevhw
[  1632.264] (--) Depth 24 pixmap format is 32 bpp
[  1632.277] (II) NVIDIA(0): Initialized AGP GART.
[  1632.292] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[  1632.399] (II) Loading extension NV-GLX
[  1632.428] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[  1632.433] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[  1632.433] (==) NVIDIA(0): Backing store disabled
[  1632.433] (==) NVIDIA(0): Silken mouse enabled
[  1632.434] (==) NVIDIA(0): DPMS enabled
[  1632.434] (II) Loading extension NV-CONTROL
[  1632.435] (==) RandR enabled
[  1632.435] (II) Initializing built-in extension Generic Event Extension
[  1632.435] (II) Initializing built-in extension SHAPE
[  1632.435] (II) Initializing built-in extension MIT-SHM
[  1632.435] (II) Initializing built-in extension XInputExtension
[  1632.435] (II) Initializing built-in extension XTEST
[  1632.435] (II) Initializing built-in extension BIG-REQUESTS
[  1632.435] (II) Initializing built-in extension SYNC
[  1632.435] (II) Initializing built-in extension XKEYBOARD
[  1632.435] (II) Initializing built-in extension XC-MISC
[  1632.435] (II) Initializing built-in extension SECURITY
[  1632.435] (II) Initializing built-in extension XINERAMA
[  1632.435] (II) Initializing built-in extension XFIXES
[  1632.435] (II) Initializing built-in extension RENDER
[  1632.435] (II) Initializing built-in extension RANDR
[  1632.435] (II) Initializing built-in extension COMPOSITE
[  1632.435] (II) Initializing built-in extension DAMAGE
[  1632.435] (II) Initializing built-in extension GESTURE
[  1632.442] (II) Initializing extension GLX
[  1632.489] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1632.512] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1632.512] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1632.512] (II) LoadModule: "evdev"
[  1632.513] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1632.514] (II) Module evdev: vendor="X.Org Foundation"
[  1632.514] 	compiled for 1.10.0.902, module version = 2.6.0
[  1632.514] 	Module class: X.Org XInput Driver
[  1632.514] 	ABI class: X.Org XInput driver, version 12.3
[  1632.514] (II) Using input driver 'evdev' for 'Power Button'
[  1632.514] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1632.514] (**) Power Button: always reports core events
[  1632.514] (**) Power Button: Device: "/dev/input/event1"
[  1632.525] (--) Power Button: Found keys
[  1632.525] (II) Power Button: Configuring as keyboard
[  1632.525] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[  1632.525] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1632.525] (**) Option "xkb_rules" "evdev"
[  1632.525] (**) Option "xkb_model" "pc105"
[  1632.525] (**) Option "xkb_layout" "us"
[  1632.530] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  1632.531] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1632.531] (II) Using input driver 'evdev' for 'Power Button'
[  1632.531] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1632.531] (**) Power Button: always reports core events
[  1632.531] (**) Power Button: Device: "/dev/input/event0"
[  1632.544] (--) Power Button: Found keys
[  1632.544] (II) Power Button: Configuring as keyboard
[  1632.544] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  1632.544] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1632.544] (**) Option "xkb_rules" "evdev"
[  1632.544] (**) Option "xkb_model" "pc105"
[  1632.544] (**) Option "xkb_layout" "us"
[  1632.563] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1632.566] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1632.566] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1632.566] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1632.566] (**) AT Translated Set 2 keyboard: always reports core events
[  1632.566] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1632.584] (--) AT Translated Set 2 keyboard: Found keys
[  1632.584] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  1632.584] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[  1632.584] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  1632.584] (**) Option "xkb_rules" "evdev"
[  1632.584] (**) Option "xkb_model" "pc105"
[  1632.584] (**) Option "xkb_layout" "us"
[  1632.585] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[  1632.586] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[  1632.586] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[  1632.586] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1632.586] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[  1632.586] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[  1632.600] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[  1632.600] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[  1632.600] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[  1632.600] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[  1632.600] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[  1632.600] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[  1632.600] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[  1632.600] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1632.600] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[  1632.600] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[  1632.600] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[  1632.600] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[  1632.601] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[  1632.601] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[  1632.601] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[  1632.601] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[  1632.601] (II) No input driver/identifier specified (ignoring)
[  1669.060] (II) Power Button: Close
[  1669.060] (II) UnloadModule: "evdev"
[  1669.060] (II) Unloading evdev
[  1669.100] (II) Power Button: Close
[  1669.100] (II) UnloadModule: "evdev"
[  1669.100] (II) Unloading evdev
[  1669.128] (II) AT Translated Set 2 keyboard: Close
[  1669.128] (II) UnloadModule: "evdev"
[  1669.128] (II) Unloading evdev
[  1669.164] (II) ImPS/2 Generic Wheel Mouse: Close
[  1669.164] (II) UnloadModule: "evdev"
[  1669.164] (II) Unloading evdev
[  1669.524]  ddxSigGiveUp: Closing log

____________________________________________

Skipping ldd output (glxinfo not found)

____________________________________________

/usr/bin/lspci -d "10de:*" -v -xxx

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at fbee0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 3.0
	Kernel driver in use: nvidia
	Kernel modules: nvidia-173, nouveau, nvidiafb
00: de 10 26 03 07 00 b0 02 a1 00 00 03 00 f8 00 00
10: 00 00 00 fa 08 00 00 e0 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 60 00 00 00 00 00 00 00 0a 01 05 01
40: 00 00 00 00 02 00 30 00 1b 0e 00 1f 02 43 00 1f
50: 01 00 00 00 01 00 00 00 ce d6 23 00 0f 00 00 00
60: 01 44 02 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


____________________________________________

/usr/bin/lspci -t

-[0000:00]-+-00.0
           +-01.0-[01]----00.0
           +-06.0
           +-1d.0
           +-1d.1
           +-1d.2
           +-1d.3
           +-1d.7
           +-1e.0-[02]----0d.0
           +-1f.0
           +-1f.1
           +-1f.2
           \-1f.5

____________________________________________

/usr/bin/lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
02:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
____________________________________________

/usr/sbin/dmidecode

# dmidecode 2.9
SMBIOS 2.3 present.
59 structures occupying 1907 bytes.
Table at 0x000F04B0.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 0203    
	Release Date: 09/07/2006
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer: HCL Infosystems Limited
	Product Name: System Product Name
	Version: System Version
	Serial Number: A064AZ176584
	UUID: 0C40BC7F-74FE-D511-BEF4-02D62605DDB6
	Wake-up Type: PCI PME#

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer Inc.
	Product Name: P5P800-VM-GB
	Version: Rev 1.xx
	Serial Number: MB-1234567890

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: 280119718606lncfiodtlssmytehs
	Type: Desktop
	Lock: Not Present
	Version: Chassis Version
	Serial Number: Chassis Serial Number
	Asset Tag: Asset-1234567890
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000001

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket 775
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel            
	ID: 49 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 4, Stepping 9
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) 4 CPU 3.06GHz                   
	Voltage: 1.4 V
	External Clock: 133 MHz
	Max Speed: 4000 MHz
	Current Speed: 3066 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 16 KB
	Maximum Size: 16 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Internal
	Installed Size: 0 KB
	Maximum Size: 0 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		70 ns
		60 ns
		50 ns
	Supported Memory Types:
		SIMM
		DIMM
		SDRAM
	Memory Module Voltage: 2.9 V
	Associated Memory Slots: 4
		0x0009
		0x000A
		0x000B
		0x000C
	Enabled Error Correcting Capabilities:
		None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM A1
	Bank Connections: 1 0
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM A2
	Bank Connections: 3 2
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM B1
	Bank Connections: 5 4
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM B2
	Bank Connections: 7 6
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 512 MB (Single-bank Connection)
	Enabled Size: 512 MB (Single-bank Connection)
	Error Status: OK

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: PS/2 Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: PS/2 Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB3
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB4
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB5
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB6
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB7
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB8
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: LPT 1
	External Connector Type: DB-25 male
	Port Type: Parallel Port ECP/EPP

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: COM 1
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: Audio Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: Audio Line Out
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: Audio Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: LAN
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CD
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRI_IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SEC_IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FLOPPY
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CHA_FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CPU_FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: EATXPWR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: CHASSIS
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0025, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FP_AUDIO
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0026, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA1
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0027, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA2
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0028, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x0029, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI2
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 2
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x002A, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI3
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 3
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x002B, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP
	Type: 32-bit AGP 8x
	Current Usage: Available
	Length: Short
	ID: 4
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x002C, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description:  Realtek 8100CS

Handle 0x002D, DMI type 11, 5 bytes
OEM Strings
	String 1: To Be Filled By O.E.M.
	String 2: To Be Filled By O.E.M.
	String 3: To Be Filled By O.E.M.
	String 4: To Be Filled By O.E.M.

Handle 0x002E, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x002F, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x0030, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x100000003FF
	Range Size: 1073741825 kB
	Physical Array Handle: 0x002F
	Partition Width: 0

Handle 0x0031, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002F
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x0032, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0031
	Memory Array Mapped Address Handle: 0x0030
	Partition Row Position: 1

Handle 0x0033, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002F
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: DDR
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x0034, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x0033
	Memory Array Mapped Address Handle: 0x0030
	Partition Row Position: 1

Handle 0x0035, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002F
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x0036, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0035
	Memory Array Mapped Address Handle: 0x0030
	Partition Row Position: 1

Handle 0x0037, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002F
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK3
	Type: DDR
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: PartNum3

Handle 0x0038, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x0037
	Memory Array Mapped Address Handle: 0x0030
	Partition Row Position: 1

Handle 0x0039, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x003A, DMI type 127, 4 bytes
End Of Table


____________________________________________

/sbin/modinfo nvidia | grep vermagic


____________________________________________

Scanning kernel log files for NVRM messages:

/var/log/messages is not readable
/var/log/kernel.log is not readable

____________________________________________

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: HCL Infosystems Limited System Product Name/P5P800-VM-GB, BIOS 0203     09/07/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36778000 - 373b4000
[    0.000000] ACPI: RSDP 000faf50 00021 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 3ffb0100 0003C (v01 A M I  OEMXSDT  09000607 MSFT 00000097)
[    0.000000] ACPI: FACP 3ffb0290 000F4 (v03 A M I  OEMFACP  09000607 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ffb0400 03552 (v01  A0631 A0631036 00000036 INTL 02002026)
[    0.000000] ACPI: FACS 3ffc0000 00040
[    0.000000] ACPI: APIC 3ffb0390 0006C (v01 A M I  OEMAPIC  09000607 MSFT 00000097)
[    0.000000] ACPI: OEMB 3ffc0040 0003F (v01 A M I  OEMBIOS  09000607 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 135MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ffb0
[    0.000000] On node 0 totalpages: 261951
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5f78200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 272 pages used for memmap
[    0.000000]   HighMem zone: 34466 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bfb80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s28800 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259903
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3a09b439-ffbf-4498-a4ab-4f6f3f93b01c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5240960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003ffb0)
[    0.000000] Memory: 1011564k/1048256k available (5188k kernel code, 36240k reserved, 2540k data, 700k init, 138952k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f4c08000 soft=f4c0a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3061.123 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6122.24 BogoMIPS (lpj=12244492)
[    0.004012] pid_max: default: 32768 minimum: 301
[    0.004047] Security Framework initialized
[    0.004075] AppArmor: AppArmor initialized
[    0.004078] Yama: becoming mindful.
[    0.004169] Mount-cache hash table entries: 512
[    0.004405] Initializing cgroup subsys ns
[    0.004412] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004417] Initializing cgroup subsys cpuacct
[    0.004423] Initializing cgroup subsys memory
[    0.004436] Initializing cgroup subsys devices
[    0.004440] Initializing cgroup subsys freezer
[    0.004443] Initializing cgroup subsys net_cls
[    0.004446] Initializing cgroup subsys blkio
[    0.004510] CPU: Physical Processor ID: 0
[    0.004513] CPU: Processor Core ID: 0
[    0.004517] mce: CPU supports 4 MCE banks
[    0.004526] [Hardware Error]: No human readable MCE decoding support on this CPU type.
[    0.004531] [Hardware Error]: Run the message through 'mcelog --ascii' to decode.
[    0.004535] Disabling lock debugging due to kernel taint
[    0.004547] CPU0: Thermal monitoring enabled (TM2)
[    0.004553] using mwait in idle threads.
[    0.009347] ACPI: Core revision 20110112
[    0.012489] ftrace: allocating 23640 entries in 47 pages
[    0.016096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016401] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057547] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 09
[    0.060003] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      18
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             0000007fffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000003ffff
[    0.060003] CPU 1 irqstacks, hard=f4cb2000 soft=f4cb4000
[    0.060003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.148036] Brought up 2 CPUs
[    0.148042] Total of 2 processors activated (12244.59 BogoMIPS).
[    0.148508] devtmpfs: initialized
[    0.149947] print_constraints: dummy: 
[    0.149976] Time: 23:13:13  Date: 10/01/11
[    0.150030] NET: Registered protocol family 16
[    0.150047] Trying to unpack rootfs image as initramfs...
[    0.150276] EISA bus registered
[    0.150293] ACPI: bus type pci registered
[    0.150745] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.150751] PCI: Using configuration type 1 for base access
[    0.154129] bio: create slab <bio-0> at 0
[    0.156059] ACPI: EC: Look up EC in DSDT
[    0.158245] ACPI: Executed 1 blocks of module-level executable AML code
[    0.162214] ACPI: Interpreter enabled
[    0.162230] ACPI: (supports S0 S3 S4 S5)
[    0.162272] ACPI: Using IOAPIC for interrupt routing
[    0.173981] ACPI: No dock devices found.
[    0.173988] HEST: Table not found.
[    0.173996] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.174156] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.174490] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.174497] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.174503] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.174510] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffefffff] (ignored)
[    0.174545] pci 0000:00:00.0: [8086:2570] type 0 class 0x000600
[    0.174561] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.174579] pci 0000:00:00.0: reg 10: [mem 0xdc000000-0xdfffffff pref]
[    0.174665] pci 0000:00:01.0: [8086:2571] type 1 class 0x000604
[    0.174725] pci 0000:00:06.0: [8086:2576] type 0 class 0x000880
[    0.174742] pci 0000:00:06.0: reg 10: [mem 0xfecf0000-0xfecf0fff]
[    0.174856] pci 0000:00:1d.0: [8086:24d2] type 0 class 0x000c03
[    0.174917] pci 0000:00:1d.0: reg 20: [io  0xb800-0xb81f]
[    0.174965] pci 0000:00:1d.1: [8086:24d4] type 0 class 0x000c03
[    0.175026] pci 0000:00:1d.1: reg 20: [io  0xc000-0xc01f]
[    0.175074] pci 0000:00:1d.2: [8086:24d7] type 0 class 0x000c03
[    0.175134] pci 0000:00:1d.2: reg 20: [io  0xc400-0xc41f]
[    0.175181] pci 0000:00:1d.3: [8086:24de] type 0 class 0x000c03
[    0.175264] pci 0000:00:1d.3: reg 20: [io  0xc800-0xc81f]
[    0.175326] pci 0000:00:1d.7: [8086:24dd] type 0 class 0x000c03
[    0.175357] pci 0000:00:1d.7: reg 10: [mem 0xf9fffc00-0xf9ffffff]
[    0.175461] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.175470] pci 0000:00:1d.7: PME# disabled
[    0.175495] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.175554] pci 0000:00:1f.0: [8086:24d0] type 0 class 0x000601
[    0.175641] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.175671] pci 0000:00:1f.1: [8086:24db] type 0 class 0x000101
[    0.175693] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.175708] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.175723] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.175738] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.175752] pci 0000:00:1f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.175768] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.175806] pci 0000:00:1f.2: [8086:24d1] type 0 class 0x000101
[    0.175838] pci 0000:00:1f.2: reg 10: [io  0xa800-0xa807]
[    0.175860] pci 0000:00:1f.2: reg 14: [io  0xa400-0xa403]
[    0.175878] pci 0000:00:1f.2: reg 18: [io  0xa000-0xa007]
[    0.175892] pci 0000:00:1f.2: reg 1c: [io  0x9800-0x9803]
[    0.175905] pci 0000:00:1f.2: reg 20: [io  0x9400-0x940f]
[    0.175958] pci 0000:00:1f.5: [8086:24d5] type 0 class 0x000401
[    0.175982] pci 0000:00:1f.5: reg 10: [io  0xb400-0xb4ff]
[    0.175996] pci 0000:00:1f.5: reg 14: [io  0xb000-0xb03f]
[    0.176029] pci 0000:00:1f.5: reg 18: [mem 0xf9fff800-0xf9fff9ff]
[    0.176044] pci 0000:00:1f.5: reg 1c: [mem 0xf9fff400-0xf9fff4ff]
[    0.176098] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.176105] pci 0000:00:1f.5: PME# disabled
[    0.176154] pci 0000:01:00.0: [10de:0326] type 0 class 0x000300
[    0.176179] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.176192] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff pref]
[    0.176237] pci 0000:01:00.0: reg 30: [mem 0xfbee0000-0xfbefffff pref]
[    0.176314] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.176323] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.176330] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfbefffff]
[    0.176338] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf8ffffff pref]
[    0.176396] pci 0000:02:0d.0: [10ec:8167] type 0 class 0x000200
[    0.176437] pci 0000:02:0d.0: reg 10: [io  0xe800-0xe8ff]
[    0.176452] pci 0000:02:0d.0: reg 14: [mem 0xfbfffc00-0xfbfffcff]
[    0.176504] pci 0000:02:0d.0: reg 30: [mem 0xfbfc0000-0xfbfdffff pref]
[    0.176530] pci 0000:02:0d.0: supports D1 D2
[    0.176535] pci 0000:02:0d.0: PME# supported from D1 D2 D3hot D3cold
[    0.176543] pci 0000:02:0d.0: PME# disabled
[    0.176582] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.176591] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.176599] pci 0000:00:1e.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.176607] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.176613] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.176618] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.176637] pci_bus 0000:00: on NUMA node 0
[    0.176645] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.176803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.186301] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.186416] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.186525] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.186633] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.186742] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.186866] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.186992] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.187105] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.187334] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.187341] vgaarb: loaded
[    0.187825] SCSI subsystem initialized
[    0.187964] libata version 3.00 loaded.
[    0.188117] usbcore: registered new interface driver usbfs
[    0.188144] usbcore: registered new interface driver hub
[    0.188207] usbcore: registered new device driver usb
[    0.188445] wmi: Mapper loaded
[    0.188450] PCI: Using ACPI for IRQ routing
[    0.188458] PCI: pci_cache_line_size set to 64 bytes
[    0.188565] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.188572] reserve RAM buffer: 000000003ffb0000 - 000000003fffffff 
[    0.188810] NetLabel: Initializing
[    0.188814] NetLabel:  domain hash size = 128
[    0.188817] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.188839] NetLabel:  unlabeled traffic allowed by default
[    0.189007] hpet clockevent registered
[    0.189013] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.189021] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.189031] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.192144] Switching to clocksource hpet
[    0.195248] Switched to NOHz mode on CPU #0
[    0.195381] Switched to NOHz mode on CPU #1
[    0.209352] AppArmor: AppArmor Filesystem Enabled
[    0.209425] pnp: PnP ACPI init
[    0.209467] ACPI: bus type pnp registered
[    0.209700] pnp 00:00: [bus 00-ff]
[    0.209706] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.209711] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.209716] pnp 00:00: [io  0x0d00-0xffff window]
[    0.209722] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.209727] pnp 00:00: [mem 0x00000000 window]
[    0.209732] pnp 00:00: [mem 0x40000000-0xffefffff window]
[    0.209846] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.209936] pnp 00:01: [dma 4]
[    0.209942] pnp 00:01: [io  0x0000-0x000f]
[    0.209951] pnp 00:01: [io  0x0081-0x0083]
[    0.209955] pnp 00:01: [io  0x0087]
[    0.209959] pnp 00:01: [io  0x0089-0x008b]
[    0.209963] pnp 00:01: [io  0x008f]
[    0.209968] pnp 00:01: [io  0x00c0-0x00df]
[    0.210036] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.210062] pnp 00:02: [io  0x0070-0x0071]
[    0.210083] pnp 00:02: [irq 8]
[    0.210164] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.210185] pnp 00:03: [io  0x0061]
[    0.210254] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.210275] pnp 00:04: [io  0x00f0-0x00ff]
[    0.210285] pnp 00:04: [irq 13]
[    0.210359] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.211321] pnp 00:05: [io  0x0378-0x037f]
[    0.211327] pnp 00:05: [io  0x0778-0x077b]
[    0.211338] pnp 00:05: [irq 7]
[    0.211343] pnp 00:05: [dma 3]
[    0.211704] pnp 00:05: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.211772] pnp 00:06: [io  0x0000-0xffffffff disabled]
[    0.211778] pnp 00:06: [io  0x0000-0xffffffff disabled]
[    0.211783] pnp 00:06: [io  0x0290-0x0297]
[    0.211898] system 00:06: [io  0x0290-0x0297] has been reserved
[    0.211906] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.212208] pnp 00:07: [io  0x0010-0x001f]
[    0.212214] pnp 00:07: [io  0x0022-0x003f]
[    0.212219] pnp 00:07: [io  0x0044-0x005f]
[    0.212223] pnp 00:07: [io  0x0062-0x0063]
[    0.212227] pnp 00:07: [io  0x0065-0x006f]
[    0.212232] pnp 00:07: [io  0x0072-0x007f]
[    0.212236] pnp 00:07: [io  0x0080]
[    0.212240] pnp 00:07: [io  0x0084-0x0086]
[    0.212244] pnp 00:07: [io  0x0088]
[    0.212249] pnp 00:07: [io  0x008c-0x008e]
[    0.212253] pnp 00:07: [io  0x0090-0x009f]
[    0.212257] pnp 00:07: [io  0x00a2-0x00bf]
[    0.212262] pnp 00:07: [io  0x00e0-0x00ef]
[    0.212266] pnp 00:07: [io  0x04d0-0x04d1]
[    0.212270] pnp 00:07: [io  0x0800-0x087f]
[    0.212275] pnp 00:07: [io  0x0400-0x041f]
[    0.212279] pnp 00:07: [io  0x0480-0x04bf]
[    0.212284] pnp 00:07: [mem 0xfed20000-0xfed8ffff]
[    0.212289] pnp 00:07: [mem 0xffb00000-0xffbfffff]
[    0.212421] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.212427] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.212433] system 00:07: [io  0x0400-0x041f] has been reserved
[    0.212438] system 00:07: [io  0x0480-0x04bf] has been reserved
[    0.212446] system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.212452] system 00:07: [mem 0xffb00000-0xffbfffff] could not be reserved
[    0.212459] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.212656] pnp 00:08: [mem 0xfec00000-0xfec00fff]
[    0.212662] pnp 00:08: [mem 0xfee00000-0xfee00fff]
[    0.212766] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.212773] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.212780] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.212842] pnp 00:09: [io  0x0060]
[    0.212848] pnp 00:09: [io  0x0064]
[    0.212858] pnp 00:09: [irq 1]
[    0.212938] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.213041] pnp 00:0a: [irq 12]
[    0.213126] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
[    0.213717] pnp 00:0b: [io  0x03f8-0x03ff]
[    0.213727] pnp 00:0b: [irq 4]
[    0.213883] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.214116] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.214121] pnp 00:0c: [mem 0x000c0000-0x000dffff]
[    0.214126] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.214131] pnp 00:0c: [mem 0x00100000-0x3ffeffff]
[    0.214136] pnp 00:0c: [mem 0xfff00000-0xffffffff]
[    0.214249] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.214256] system 00:0c: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.214262] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.214269] system 00:0c: [mem 0x00100000-0x3ffeffff] could not be reserved
[    0.214275] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.214282] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.214600] pnp: PnP ACPI: found 13 devices
[    0.214605] ACPI: ACPI bus type pnp unregistered
[    0.214612] PnPBIOS: Disabled by ACPI PNP
[    0.253713] pci 0000:00:1f.1: BAR 5: assigned [mem 0x40000000-0x400003ff]
[    0.253727] pci 0000:00:1f.1: BAR 5: set to [mem 0x40000000-0x400003ff] (PCI address [0x40000000-0x400003ff])
[    0.253735] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.253742] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.253751] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfbefffff]
[    0.253759] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf8ffffff pref]
[    0.253770] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.253776] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.253786] pci 0000:00:1e.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.253793] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.253823] pci 0000:00:1e.0: setting latency timer to 64
[    0.253831] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.253836] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.253841] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.253846] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfbefffff]
[    0.253851] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf8ffffff pref]
[    0.253857] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.253862] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.253867] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.253872] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.253953] NET: Registered protocol family 2
[    0.254122] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.254678] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.255723] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.256492] TCP: Hash tables configured (established 131072 bind 65536)
[    0.256498] TCP reno registered
[    0.256510] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.256547] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.256824] NET: Registered protocol family 1
[    0.257007] pci 0000:01:00.0: Boot video device
[    0.257017] PCI: CLS 16 bytes, default 64
[    0.257465] cpufreq-nforce2: No nForce2 chipset.
[    0.257763] audit: initializing netlink socket (disabled)
[    0.257783] type=2000 audit(1317510793.256:1): initialized
[    0.272093] highmem bounce pool size: 64 pages
[    0.272105] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.276439] VFS: Disk quotas dquot_6.5.2
[    0.276585] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.278305] fuse init (API version 7.16)
[    0.278537] msgmni has been set to 1704
[    0.279071] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.279118] io scheduler noop registered
[    0.279123] io scheduler deadline registered
[    0.279163] io scheduler cfq registered (default)
[    0.279483] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.279538] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.279894] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.279908] ACPI: Power Button [PWRB]
[    0.280066] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.280075] ACPI: Power Button [PWRF]
[    0.280343] ACPI: acpi_idle registered with cpuidle
[    0.284128] ERST: Table is not found!
[    0.284375] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.292290] isapnp: Scanning for PnP cards...
[    0.304799] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.634712] Freeing initrd memory: 12528k freed
[    0.646658] isapnp: No Plug & Play device found
[    0.687313] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.687694] Linux agpgart interface v0.103
[    0.687892] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    0.691884] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xdc000000
[    0.694027] brd: module loaded
[    0.695019] loop: module loaded
[    0.695177] i2c-core: driver [adp5520] using legacy suspend method
[    0.695180] i2c-core: driver [adp5520] using legacy resume method
[    0.695336] ata_piix 0000:00:1f.1: version 2.13
[    0.695353] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.695377] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.695439] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.696023] scsi0 : ata_piix
[    0.696174] scsi1 : ata_piix
[    0.698337] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.698341] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.698381] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.698390] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.698463] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.698916] scsi2 : ata_piix
[    0.699042] scsi3 : ata_piix
[    0.699125] ata3: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0x9400 irq 18
[    0.699129] ata4: SATA max UDMA/133 cmd 0xa000 ctl 0x9800 bmdma 0x9408 irq 18
[    0.699803] Fixed MDIO Bus: probed
[    0.699867] PPP generic driver version 2.4.2
[    0.699964] tun: Universal TUN/TAP device driver, 1.6
[    0.699967] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.700181] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.700220] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.700245] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.700250] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.700312] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.708089] ehci_hcd 0000:00:1d.7: debug port 1
[    0.711980] ehci_hcd 0000:00:1d.7: cache line size of 16 is not supported
[    0.712023] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fffc00
[    0.724029] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.724230] hub 1-0:1.0: USB hub found
[    0.724237] hub 1-0:1.0: 8 ports detected
[    0.724370] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.724393] uhci_hcd: USB Universal Host Controller Interface driver
[    0.724450] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.724460] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.724464] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.724531] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.724600] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000b800
[    0.724807] hub 2-0:1.0: USB hub found
[    0.724815] hub 2-0:1.0: 2 ports detected
[    0.724935] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.724944] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.724948] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.725018] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.725086] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c000
[    0.725285] hub 3-0:1.0: USB hub found
[    0.725293] hub 3-0:1.0: 2 ports detected
[    0.725397] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.725406] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.725410] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.725470] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.728067] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c400
[    0.728272] hub 4-0:1.0: USB hub found
[    0.728279] hub 4-0:1.0: 2 ports detected
[    0.728377] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.728387] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.728391] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.728450] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.728506] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c800
[    0.728714] hub 5-0:1.0: USB hub found
[    0.728722] hub 5-0:1.0: 2 ports detected
[    0.728951] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.731786] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.731795] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.732037] mousedev: PS/2 mouse device common for all mice
[    0.732253] rtc_cmos 00:02: RTC can wake from S4
[    0.736134] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.736165] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.736312] device-mapper: uevent: version 1.0.3
[    0.736443] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.736571] device-mapper: multipath: version 1.2.0 loaded
[    0.736577] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.736695] EISA: Probing bus 0 at eisa.0
[    0.736738] EISA: Detected 0 cards.
[    0.736836] cpuidle: using governor ladder
[    0.736842] cpuidle: using governor menu
[    0.737302] TCP cubic registered
[    0.737511] NET: Registered protocol family 10
[    0.738454] NET: Registered protocol family 17
[    0.738482] Registering the dns_resolver key type
[    0.738543] Using IPI No-Shortcut mode
[    0.738715] PM: Hibernation image not present or could not be loaded.
[    0.738733] registered taskstats version 1
[    0.738969]   Magic number: 15:706:250
[    0.739092] rtc_cmos 00:02: setting system clock to 2011-10-01 23:13:14 UTC (1317510794)
[    0.739096] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.739099] EDD information not available.
[    0.752083] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.860306] ata4.00: ATA-6: WDC WD800BD-00JMC0, 05.01C05, max UDMA/133
[    0.860311] ata4.00: 156301488 sectors, multi 16: LBA 
[    0.868281] ata4.00: configured for UDMA/133
[    0.884357] ata1.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.03, max UDMA/66
[    0.884364] ata1.01: ATAPI: TSSTcorp CDW/DVD SH-M522C, TS07, max UDMA/33
[    0.890218] ata3.00: ATA-8: ST3320418AS, CC34, max UDMA/133
[    0.890222] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.900237] ata1.00: configured for UDMA/66
[    0.932181] ata1.01: configured for UDMA/33
[    0.935059] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.03 PQ: 0 ANSI: 5
[    0.937159] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.937163] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.937348] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.937458] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.938729] scsi 0:0:1:0: CD-ROM            TSSTcorp CDW/DVD SH-M522C TS07 PQ: 0 ANSI: 5
[    0.940732] sr1: scsi3-mmc drive: 8x/52x writer cd/rw xa/form2 cdda tray
[    0.940883] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    0.940976] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.946215] ata3.00: configured for UDMA/133
[    0.946357] scsi 2:0:0:0: Direct-Access     ATA      ST3320418AS      CC34 PQ: 0 ANSI: 5
[    0.946568] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.946645] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    0.946695] sd 2:0:0:0: [sda] Write Protect is off
[    0.946702] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.946758] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.946884] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800BD-00JM 05.0 PQ: 0 ANSI: 5
[    0.947253] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    0.947405] sd 3:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.947544] sd 3:0:0:0: [sdb] Write Protect is off
[    0.947549] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.947605] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.968635]  sdb: sdb1 sdb2 < sdb5 > sdb3 sdb4
[    0.969282] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.016915]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    1.017574] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.017630] Freeing unused kernel memory: 700k freed
[    1.018390] Write protecting the kernel text: 5192k
[    1.018457] Write protecting the kernel read-only data: 2148k
[    1.057609] <30>udev[71]: starting version 167
[    1.256054] Refined TSC clocksource calibration: 3061.004 MHz.
[    1.256064] Switching to clocksource tsc
[    1.312254] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.312293] r8169 0000:02:0d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.312334] r8169 0000:02:0d.0: (unregistered net_device): no PCI Express capability
[    1.313555] r8169 0000:02:0d.0: eth0: RTL8169sc/8110sc at 0xf801ac00, 00:18:f3:22:36:ec, XID 18000000 IRQ 23
[    1.960901] EXT3-fs: barriers not enabled
[    1.968449] kjournald starting.  Commit interval 5 seconds
[    1.968477] EXT3-fs (sdb1): mounted filesystem with ordered data mode
[   26.067503] <30>udev[296]: starting version 167
[   26.106782] Adding 584700k swap on /dev/sdb5.  Priority:-1 extents:1 across:584700k 
[   26.120808] lp: driver loaded but no devices found
[   26.153197] nvidia: module license 'NVIDIA' taints kernel.
[   26.801520] intel_rng: FWH not detected
[   27.083935] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.083956] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   27.095838] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[   27.104596] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.132379] parport_pc 00:05: reported by Plug and Play ACPI
[   27.132493] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   27.201125] type=1400 audit(1317510820.960:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=427 comm="apparmor_parser"
[   27.202393] type=1400 audit(1317510820.960:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=427 comm="apparmor_parser"
[   27.203179] type=1400 audit(1317510820.960:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=427 comm="apparmor_parser"
[   27.221138] lp0: using parport0 (interrupt-driven).
[   27.330299] psmouse serio1: ID: 10 00 64
[   27.697848] ppdev: user-space parallel port driver
[   27.775846] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   27.775917] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   27.886987] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   28.096064] intel8x0_measure_ac97_clock: measured 54537 usecs (2628 samples)
[   28.096072] intel8x0: clocking to 48000
[   28.920476] vesafb: framebuffer at 0xe0000000, mapped to 0xf8180000, using 3072k, total 3072k
[   28.920484] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   28.920489] vesafb: scrolling: redraw
[   28.920495] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   28.920795] Console: switching to colour frame buffer device 128x48
[   28.920843] fb0: VESA VGA frame buffer device
[   77.603637] EXT3-fs (sdb1): using internal journal
[   78.616863] type=1400 audit(1317510872.376:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=685 comm="apparmor_parser"
[   78.618242] type=1400 audit(1317510872.376:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=685 comm="apparmor_parser"
[   78.673891] type=1400 audit(1317510872.432:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=692 comm="apparmor_parser"
[   78.693793] type=1400 audit(1317510872.452:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=693 comm="apparmor_parser"
[   78.694943] type=1400 audit(1317510872.452:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=693 comm="apparmor_parser"
[   78.695659] type=1400 audit(1317510872.452:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=693 comm="apparmor_parser"
[   78.739913] type=1400 audit(1317510872.496:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=705 comm="apparmor_parser"
[   78.748920] type=1400 audit(1317510872.508:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=701 comm="apparmor_parser"
[   78.749821] type=1400 audit(1317510872.508:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=705 comm="apparmor_parser"
[   78.763761] type=1400 audit(1317510872.520:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=711 comm="apparmor_parser"
[   78.890721] r8169 0000:02:0d.0: eth0: link down
[   78.906964] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   79.201355] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   79.201380] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   79.201430] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   80.421788] r8169 0000:02:0d.0: eth0: link up
[   80.422072] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   91.296029] eth0: no IPv6 routers present
[   99.134787] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   99.134814] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   99.134864] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[  168.006172] device eth0 entered promiscuous mode
[  178.457392] device eth0 left promiscuous mode
[  206.644135] device eth0 entered promiscuous mode
[  211.970270] device eth0 left promiscuous mode
[  254.252262] device eth0 entered promiscuous mode
[  299.988036] [Hardware Error]: Machine check events logged
[  332.899722] device eth0 left promiscuous mode
[  384.267234] r8169 0000:02:0d.0: eth0: link down
[  388.766805] r8169 0000:02:0d.0: eth0: link up
[ 1082.726517] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[ 1082.726543] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[ 1082.726594] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[ 1155.597598] device eth0 entered promiscuous mode
[ 1159.269398] device eth0 left promiscuous mode
[ 4303.652146] device eth0 entered promiscuous mode
[ 4347.973821] r8169 0000:02:0d.0: eth0: link down
[ 4352.489849] r8169 0000:02:0d.0: eth0: link up
[ 4392.521675] r8169 0000:02:0d.0: eth0: link down
[ 4397.084400] r8169 0000:02:0d.0: eth0: link up
[ 4466.926679] device eth0 left promiscuous mode
____________________________________________

Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
____________________________________________

Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
____________________________________________

xset -q:

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  6/1    threshold:  5
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
____________________________________________

nvidia-settings -q all:


Attributes queryable via sparda:0.0:

  Attribute 'OperatingSystem' (sparda:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (sparda:0.0): 173.14.30 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen.

  Attribute 'NvControlVersion' (sparda:0.0): 1.16 
    'NvControlVersion' is a string attribute.
    'NvControlVersion' is a read-only attribute.
    'NvControlVersion' can use the following target types: X Screen.

  Attribute 'GLXServerVersion' (sparda:0.0): 1.4 
    'GLXServerVersion' is a string attribute.
    'GLXServerVersion' is a read-only attribute.
    'GLXServerVersion' can use the following target types: X Screen.

  Attribute 'GLXClientVersion' (sparda:0.0): 1.4 
    'GLXClientVersion' is a string attribute.
    'GLXClientVersion' is a read-only attribute.
    'GLXClientVersion' can use the following target types: X Screen.

  Attribute 'OpenGLVersion' (sparda:0.0): 2.1.2 NVIDIA 173.14.30 
    'OpenGLVersion' is a string attribute.
    'OpenGLVersion' is a read-only attribute.
    'OpenGLVersion' can use the following target types: X Screen.

  Attribute 'XRandRVersion' (sparda:0.0): 1.3 
    'XRandRVersion' is a string attribute.
    'XRandRVersion' is a read-only attribute.
    'XRandRVersion' can use the following target types: X Screen.

  Attribute 'XF86VidModeVersion' (sparda:0.0): 2.2 
    'XF86VidModeVersion' is a string attribute.
    'XF86VidModeVersion' is a read-only attribute.
    'XF86VidModeVersion' can use the following target types: X Screen.

  Attribute 'XvVersion' (sparda:0.0): 2.2 
    'XvVersion' is a string attribute.
    'XvVersion' is a read-only attribute.
    'XvVersion' can use the following target types: X Screen.

  Attribute 'TwinView' (sparda:0.0): 0.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (sparda:0.0): 0x00000001.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (sparda:0.0): 0x00000001.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'CursorShadow' (sparda:0.0): 0.
    'CursorShadow' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'CursorShadow' can use the following target types: X Screen.

  Attribute 'CursorShadowAlpha' (sparda:0.0): 64.
    The valid values for 'CursorShadowAlpha' are in the range 0 - 254
    (inclusive).
    'CursorShadowAlpha' can use the following target types: X Screen.

  Attribute 'CursorShadowRed' (sparda:0.0): 0.
    The valid values for 'CursorShadowRed' are in the range 0 - 255
    (inclusive).
    'CursorShadowRed' can use the following target types: X Screen.

  Attribute 'CursorShadowGreen' (sparda:0.0): 0.
    The valid values for 'CursorShadowGreen' are in the range 0 - 255
    (inclusive).
    'CursorShadowGreen' can use the following target types: X Screen.

  Attribute 'CursorShadowBlue' (sparda:0.0): 0.
    The valid values for 'CursorShadowBlue' are in the range 0 - 255
    (inclusive).
    'CursorShadowBlue' can use the following target types: X Screen.

  Attribute 'CursorShadowXOffset' (sparda:0.0): 4.
    The valid values for 'CursorShadowXOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowXOffset' can use the following target types: X Screen.

  Attribute 'CursorShadowYOffset' (sparda:0.0): 2.
    The valid values for 'CursorShadowYOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowYOffset' can use the following target types: X Screen.

  Attribute 'AssociatedDisplays' (sparda:0.0): 0x00000001.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

  Attribute 'InitialPixmapPlacement' (sparda:0.0): 1.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4
    (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.

  Attribute 'DynamicTwinview' (sparda:0.0): 1.
    'DynamicTwinview' is an integer attribute.
    'DynamicTwinview' is a read-only attribute.
    'DynamicTwinview' can use the following target types: X Screen.

  Attribute 'MultiGpuDisplayOwner' (sparda:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.

  Attribute 'GlyphCache' (sparda:0.0): 0.
    The valid values for 'GlyphCache' are in the range 0 - 1 (inclusive).
    'GlyphCache' can use the following target types: X Screen.

  Attribute 'Depth30Allowed' (sparda:0.0): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'SyncToVBlank' (sparda:0.0): 0.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'SyncToVBlank' can use the following target types: X Screen.

  Attribute 'LogAniso' (sparda:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 3 (inclusive).
    'LogAniso' can use the following target types: X Screen.

  Attribute 'FSAA' (sparda:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 2, 5, 6, 7, 8 and 9.
    'FSAA' can use the following target types: X Screen.

  Attribute 'TextureSharpen' (sparda:0.0): 0.
    'TextureSharpen' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'TextureSharpen' can use the following target types: X Screen.

  Attribute 'ForceGenericCpu' (sparda:0.0): 0.
    'ForceGenericCpu' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ForceGenericCpu' can use the following target types: X Screen.

  Attribute 'GammaCorrectedAALines' (sparda:0.0): 0.
    'GammaCorrectedAALines' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'GammaCorrectedAALines' can use the following target types: X Screen.

  Attribute 'AllowFlipping' (sparda:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'AllowFlipping' can use the following target types: X Screen.

  Attribute 'FSAAAppControlled' (sparda:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.

  Attribute 'LogAnisoAppControlled' (sparda:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.

  Attribute 'OpenGLImageSettings' (sparda:0.0): 1.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3
    (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.

  Attribute 'BusType' (sparda:0.0): 0.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU.

  Attribute 'VideoRam' (sparda:0.0): 262144.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (sparda:0.0): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (sparda:0.0): 270,266.
    The valid values for 'GPU2DClockFreqs' are in the ranges 67 - 540, 66 -
    1000 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (sparda:0.0): 270,266.
    The valid values for 'GPU3DClockFreqs' are in the ranges 67 - 540, 66 -
    1000 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (sparda:0.0): 270,266.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (sparda:0.0): 270,266.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (sparda:0.0): 270,266.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'BusRate' (sparda:0.0): 8.
    The valid values for 'BusRate' are in the range 1 - 8 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU.

  Attribute 'GPUErrors' (sparda:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.

  Attribute 'GPUPowerSource' (sparda:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (sparda:0.0): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (sparda:0.0): 0.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (sparda:0.0): 1.
    'GPUAdaptiveClockState' is an integer attribute.
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (sparda:0.0): perf=0, nvclock=270, memclock=266
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen.

  Attribute 'GvoSupported' (sparda:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.

  Attribute 'DigitalVibrance' (sparda:0.0; display device: CRT-0): 0.
    The valid values for 'DigitalVibrance' are in the range 0 - 63
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'ImageSharpening' (sparda:0.0; display device: CRT-0): 0.
    The valid values for 'ImageSharpening' are in the range 0 - 31
    (inclusive).
    'ImageSharpening' is display device specific.
    'ImageSharpening' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (sparda:0.0; display device: CRT-0): 60.00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (sparda:0.0; display device: CRT-0): 60.004 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'XVideoTextureSyncToVBlank' (sparda:0.0): 1.
    The valThe program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 412 error_code 8 request_code 140 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
id values for 'XVideoTextureSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoTextureSyncToVBlank' can use the following target types: X
    Screen.

  Attribute 'XVideoBlitterSyncToVBlank' (sparda:0.0): 0.
    The valid values for 'XVideoBlitterSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoBlitterSyncToVBlank' can use the following target types: X
    Screen.

  Attribute 'XVideoSyncToDisplay' (sparda:0.0): 0x00000001.
    'XVideoSyncToDisplay' is a bitmask attribute.
    'XVideoSyncToDisplay' can use the following target types: X Screen.

Attributes queryable via sparda:0[gpu:0]:

  Attribute 'OperatingSystem' (sparda:0[gpu:0]): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (sparda:0[gpu:0]): 173.14.30 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (sparda:0[gpu:0]): 0x00000001.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (sparda:0[gpu:0]): 0x00000001.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'Depth30Allowed' (sparda:0[gpu:0]): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

____________________________________________

*** /proc/cmdline
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.376193696 +0530 /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3a09b439-ffbf-4498-a4ab-4f6f3f93b01c ro quiet splash vt.handoff=7

____________________________________________

*** /proc/cpuinfo
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.384193696 +0530 /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping	: 9
cpu MHz		: 3061.123
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips	: 6122.24
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.06GHz
stepping	: 9
cpu MHz		: 3061.123
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips	: 6122.34
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:


____________________________________________

*** /proc/interrupts
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.388193696 +0530 /proc/interrupts
           CPU0       CPU1       
  0:         59          0   IO-APIC-edge      timer
  1:       7218          0   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:     567246          0   IO-APIC-edge      i8042
 14:      41318          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:     475329          0   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb5, nvidia
 17:       2045          0   IO-APIC-fasteoi   Intel ICH5
 18:      80440          0   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb4
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 23:     163509          0   IO-APIC-fasteoi   ehci_hcd:usb1, eth0
NMI:          0          0   Non-maskable interrupts
LOC:    1275773    1261595   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:      24297      42974   Rescheduling interrupts
CAL:       1597       2171   Function call interrupts
TLB:      20289      32062   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         18         18   Machine check polls
ERR:          1
MIS:          0

____________________________________________

*** /proc/meminfo
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.400193696 +0530 /proc/meminfo
MemTotal:        1024792 kB
MemFree:           83472 kB
Buffers:           62892 kB
Cached:           340236 kB
SwapCached:          352 kB
Active:           396460 kB
Inactive:         477144 kB
Active(anon):     203332 kB
Inactive(anon):   276664 kB
Active(file):     193128 kB
Inactive(file):   200480 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        138952 kB
HighFree:            264 kB
LowTotal:         885840 kB
LowFree:           83208 kB
SwapTotal:        584700 kB
SwapFree:         582160 kB
Dirty:                48 kB
Writeback:             0 kB
AnonPages:        470264 kB
Mapped:           141164 kB
Shmem:              9476 kB
Slab:              34440 kB
SReclaimable:      22520 kB
SUnreclaim:        11920 kB
KernelStack:        2728 kB
PageTables:         7864 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1097096 kB
Committed_AS:    2182512 kB
VmallocTotal:     122880 kB
VmallocUsed:       33324 kB
VmallocChunk:      81916 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      192504 kB
DirectMap4M:      716800 kB

____________________________________________

*** /proc/modules
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.404193696 +0530 /proc/modules
binfmt_misc 13213 1 - Live 0xf8545000
vesafb 13449 1 - Live 0xf8155000
snd_intel8x0 33213 2 - Live 0xf8163000
snd_ac97_codec 105614 1 snd_intel8x0, Live 0xf8123000
ac97_bus 12642 1 snd_ac97_codec, Live 0xf8109000
snd_pcm 80244 2 snd_intel8x0,snd_ac97_codec, Live 0xf813f000
ppdev 12849 0 - Live 0xf80d7000
snd_seq_midi 13132 0 - Live 0xf80d1000
snd_rawmidi 25269 1 snd_seq_midi, Live 0xf8100000
snd_seq_midi_event 14475 1 snd_seq_midi, Live 0xf80c4000
snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event, Live 0xf8114000
snd_timer 28659 2 snd_pcm,snd_seq, Live 0xf80dc000
snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf80e4000
snd 55295 11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf80ab000
psmouse 73312 0 - Live 0xf80ec000
parport_pc 32111 1 - Live 0xf80ba000
soundcore 12600 1 snd, Live 0xf80cb000
serio_raw 12990 0 - Live 0xf8f85000
shpchp 32345 0 - Live 0xf8f66000
nvidia 7098106 34 - Live 0xf87ee000 (P)
snd_page_alloc 14073 2 snd_intel8x0,snd_pcm, Live 0xf8f7b000
lp 13349 0 - Live 0xf801d000
parport 36746 3 ppdev,parport_pc,lp, Live 0xf8037000
r8169 42534 0 - Live 0xf802a000

____________________________________________

*** /proc/version
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.412193696 +0530 /proc/version
Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011

____________________________________________

*** /proc/pci does not exist

____________________________________________

*** /proc/iomem
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.420193696 +0530 /proc/iomem
00000000-0000ffff : reserved
00010000-0009fbff : System RAM
0009fc00-0009ffff : reserved
000a0000-000bffff : Video RAM area
000c0000-000cf7ff : Video ROM
000cf800-000d07ff : Adapter ROM
000e6000-000fffff : reserved
  000f0000-000fffff : System ROM
00100000-3ffaffff : System RAM
  01000000-015112a0 : Kernel code
  015112a1-0178c47f : Kernel data
  01841000-0191afff : Kernel bss
3ffb0000-3ffbffff : ACPI Tables
3ffc0000-3ffeffff : ACPI Non-volatile Storage
3fff0000-3fffffff : reserved
40000000-400003ff : 0000:00:1f.1
dc000000-dfffffff : 0000:00:00.0
e0000000-f8ffffff : PCI Bus 0000:01
  e0000000-efffffff : 0000:01:00.0
    e0000000-e02fffff : vesafb
f9fff400-f9fff4ff : 0000:00:1f.5
  f9fff400-f9fff4ff : Intel ICH5
f9fff800-f9fff9ff : 0000:00:1f.5
  f9fff800-f9fff9ff : Intel ICH5
f9fffc00-f9ffffff : 0000:00:1d.7
  f9fffc00-f9ffffff : ehci_hcd
fa000000-fbefffff : PCI Bus 0000:01
  fa000000-faffffff : 0000:01:00.0
    fa000000-faffffff : nvidia
  fbee0000-fbefffff : 0000:01:00.0
fbf00000-fbffffff : PCI Bus 0000:02
  fbfc0000-fbfdffff : 0000:02:0d.0
  fbfffc00-fbfffcff : 0000:02:0d.0
    fbfffc00-fbfffcff : r8169
fec00000-fec003ff : IOAPIC 0
fecf0000-fecf0fff : 0000:00:06.0
fed20000-fed8ffff : pnp 00:07
fee00000-fee00fff : Local APIC
  fee00000-fee00fff : pnp 00:08
ffb80000-ffffffff : reserved
  fff00000-ffffffff : pnp 00:0c

____________________________________________

*** /proc/mtrr
*** ls: -rw-r--r-- 1 root root 0 2011-10-02 05:01:16.016194730 +0530 /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back

____________________________________________

*** /proc/driver/nvidia/version
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.436193696 +0530 /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 

____________________________________________

*** /proc/driver/nvidia/cards/0
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.448193696 +0530 /proc/driver/nvidia/cards/0
Model: 		 GeForce FX 5500
IRQ:   		 16
Video BIOS: 	 04.34.20.69.00
Card Type: 	 AGP
DMA Size: 	 32 bits
DMA Mask: 	 0xffffffff
Bus Location: 	 01.00.0

____________________________________________

*** /proc/driver/nvidia/agp/card
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.456193696 +0530 /proc/driver/nvidia/agp/card
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0x1f000e1b:0x1f004302

____________________________________________

*** /proc/driver/nvidia/agp/host-bridge
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.464193696 +0530 /proc/driver/nvidia/agp/host-bridge
Host Bridge: 	 PCI device 8086:2570
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0x1f004a1b:0x00000b02

____________________________________________

*** /proc/driver/nvidia/agp/status
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.468193696 +0530 /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled

____________________________________________

*** /proc/driver/nvidia/warnings/README
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.480193696 +0530 /proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.

____________________________________________

*** /proc/driver/nvidia/registry
*** ls: -r--r--r-- 1 root root 0 2011-10-02 06:10:15.488193696 +0530 /proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
MapRegistersEarly: 0
RegistryDwords: ""

____________________________________________

End of NVIDIA bug report log file.




sorry for THIS much late reply...but i was fixing ma net connectivity issues caused by DNS SPOOFING via ettercap... :P


dantehh

---

### Post by Falcon1002 on 2011-10-26
> /tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.c: At top leve
l:
/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.c:373:5: error
: unknown field ‘ioctl’ specified in initializer
/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.c:373:5: warni
ng: initialization from incompatible pointer type
make[3]: *** [/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/src/nv/nv.
o] Error 1
make[2]: *** [_module_/tmp/selfgz6913/NVIDIA-Linux-x86-173.14.25-pkg1/usr/sr
c/nv] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at [www.nvidia.com](www.nvidia.com). 

From the above text I can tell that a file failed to compile. Sadly though I am not familiar enough with logs to tell what caused it. :( Although from my experience it could be caused by some dependency not being satisfied. 
If you run this command in the folder with the Nvidia download it will extract the contents of the run file
```
./NVIDIA-Linux-x86*.run --extract-only
```

In NVIDIA-Linux-x86-173.14.31-pkg1/usr/share/doc there is a readme file that has the dependencies list. You can check the dependencies and see if you have them all, I imagine you probably do though.

[http://nvidia.custhelp.com/app/answers/detail/a_id/132/kw/Linux/session/L3RpbWUvMTMxOTY3MTcxMy9zaWQvKnlsRm96SGs%3D]("http://nvidia.custhelp.com/app/answers/detail/a_id/132/kw/Linux/session/L3RpbWUvMTMxOTY3MTcxMy9zaWQvKnlsRm96SGs%3D") I did find this but I doubt that it would yield any better results. (If you do try to run this you need to run make in NVIDIA-Linux-x86-173.14.31-pkg1/usr/src/nv)

I am very sorry I cannot be of more help. :( I would suggest asking your questions again but maybe include "Video card problem" in your title. Hopefully someone with knowledge will be able to help. Sorry I am unable to help any more. Hope you get your problems fixed.

---

### Post by rex_dante on 2011-11-29
> **Falcon1002 said:**
> From the above text I can tell that a file failed to compile. Sadly though I am not familiar enough with logs to tell what caused it. :( Although from my experience it could be caused by some dependency not being satisfied. 
If you run this command in the folder with the Nvidia download it will extract the contents of the run file
```
./NVIDIA-Linux-x86*.run --extract-only
```

In NVIDIA-Linux-x86-173.14.31-pkg1/usr/share/doc there is a readme file that has the dependencies list. You can check the dependencies and see if you have them all, I imagine you probably do though.

[http://nvidia.custhelp.com/app/answers/detail/a_id/132/kw/Linux/session/L3RpbWUvMTMxOTY3MTcxMy9zaWQvKnlsRm96SGs%3D]("http://nvidia.custhelp.com/app/answers/detail/a_id/132/kw/Linux/session/L3RpbWUvMTMxOTY3MTcxMy9zaWQvKnlsRm96SGs%3D") I did find this but I doubt that it would yield any better results. (If you do try to run this you need to run make in NVIDIA-Linux-x86-173.14.31-pkg1/usr/src/nv)

I am very sorry I cannot be of more help. :( I would suggest asking your questions again but maybe include "Video card problem" in your title. Hopefully someone with knowledge will be able to help. Sorry I am unable to help any more. Hope you get your problems fixed.

thnx Falcon

---

