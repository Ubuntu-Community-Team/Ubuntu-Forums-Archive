---
title: "HOWTO: Captive-ntfs on ubuntu"
date: 2005-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by badriram on 2005-01-05
Captive ntfs is a great program that lets you read and write to ntfs(windows) partitons, but on ubuntu it kept freezing well until now...
[list=1]
[*] First download the rpm package from [http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)
[*] Install kernel-headers for your kernel revision
[list]To find out your kernel type in the terminal '*uname -a*'
[*]To install kernel-headers use synaptic or apt-get to find and install the correct version 
[*]in my case i did '*apt-get install linux-headers-2.6.8.1-4-k7*'
[*] if do not know use '*apt-cache search linux-headers*' for list of kernel headers available [/list]
[*] use alien to convert rpm to deb package

[list][*]run '*alien captive-static-1.1.5-0.i386.rpm*'
[*]This creates captive-static_1.1.5_1.i386.deb[/list]
[*] Install deb package using '*dpkg -i captive-static_1.1.5_1.i386.deb*'
[*] run '*captive-install-acquire*'

[list][*]Follow directions to find ntfs.sys and other files that captive needs.[/list]
[*] run '*/usr/share/lufs/prepmod*'
[*] create user and group named captive
[*] use '*mount -t captive-ntfs /dev/hd?? /mnt/winpart*' to mount. Change options to enable write etc....
[/list]
:-) You can also post any questions here or on [http://blog.badri.us/badriram/archive/2005/01/05/155.aspx](http://blog.badri.us/badriram/archive/2005/01/05/155.aspx)

---

### Post by billputer on 2005-01-09
I've heard a lot about how write ntfs support is a bit sketchy.  I'm not willing to lose my Windows partition.  How safe is this?

---

### Post by badriram on 2005-01-09
Been running it for a week now without a problem. I do switch back and forth and i did  run chkdsk just to be sure the first couple days, and no errors.

My only problem with it is that it is slow when using a large file, 200+ MB....

---

### Post by c0rrupt on 2005-03-13
Ok, I keep getting this error.

```
c0rrupt@davidspc:~ $ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.10-4-k7 (base version 2.6.10)
Destination module directory: /lib/modules/2.6.10-4-k7/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.10-4-k7/build
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.10-4-k7/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
make: Entering directory `/usr/src/linux-headers-2.6.10-4-k7'
  CC [M]  /usr/share/lufs/2.6/dir.o
  CC [M]  /usr/share/lufs/2.6/file.o
  CC [M]  /usr/share/lufs/2.6/inode.o
  CC [M]  /usr/share/lufs/2.6/proc.o
  CC [M]  /usr/share/lufs/2.6/symlink.o
  LD [M]  /usr/share/lufs/2.6/lufs.o
  Building modules, stage 2.
  MODPOST
*** Warning: "kill_proc_info" [/usr/share/lufs/2.6/lufs.ko] undefined!
  CC      /usr/share/lufs/2.6/lufs.mod.o
  LD [M]  /usr/share/lufs/2.6/lufs.ko
make: Leaving directory `/usr/src/linux-headers-2.6.10-4-k7'
+ /bin/rm -rf /lib/modules/2.6.10-4-k7/kernel/fs/lufs; /bin/mkdir -p /lib/modules/2.6.10-4-k7/kernel/fs/lufs; /bin/ln -s /var/lib/lufs/lufs.ko /lib/modules/2.6.10-4-k7/kernel/fs/lufs/lufs.ko
+ /sbin/rmmod lufs 2>/dev/null; /sbin/insmod /lib/modules/2.6.10-4-k7/kernel/fs/lufs/lufs.ko 2>/dev/null
Failed to prepare lufs.ko module for your Linux kernel 2.6.10-4-k7.
Detected Linux kernel sources "/lib/modules/2.6.10-4-k7/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-4-k7/build
                /usr/src/kernel-headers-2.6.10-4-k7
                /usr/src/linux-2.6.10-4-k7
                /usr/src/linux-2.6.10
                /usr/src/linux
                /usr/src/kernel-source-2.6.10-4-k7

```
I looked for kernel-source-2.6.10 in synaptic but couldn't find it.  The newest was 2.6.9

---

### Post by bored2k on 2005-03-13
> **c0rrupt]Ok, I keep getting this error.

```
c0rrupt@davidspc:~ $ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.10-4-k7 (base version 2.6.10)
Destination module directory: /lib/modules/2.6.10-4-k7/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.10-4-k7/build
+ set -e said:**
>   /usr/share/lufs/2.6/dir.o
  CC [M]  /usr/share/lufs/2.6/file.o
  CC [M]  /usr/share/lufs/2.6/inode.o
  CC [M]  /usr/share/lufs/2.6/proc.o
  CC [M]  /usr/share/lufs/2.6/symlink.o
  LD [M]  /usr/share/lufs/2.6/lufs.o
  Building modules, stage 2.
  MODPOST
*** Warning: "kill_proc_info" [/usr/share/lufs/2.6/lufs.ko] undefined!
  CC      /usr/share/lufs/2.6/lufs.mod.o
  LD [M]  /usr/share/lufs/2.6/lufs.ko
make: Leaving directory `/usr/src/linux-headers-2.6.10-4-k7'
+ /bin/rm -rf /lib/modules/2.6.10-4-k7/kernel/fs/lufs; /bin/mkdir -p /lib/modules/2.6.10-4-k7/kernel/fs/lufs; /bin/ln -s /var/lib/lufs/lufs.ko /lib/modules/2.6.10-4-k7/kernel/fs/lufs/lufs.ko
+ /sbin/rmmod lufs 2>/dev/null; /sbin/insmod /lib/modules/2.6.10-4-k7/kernel/fs/lufs/lufs.ko 2>/dev/null
Failed to prepare lufs.ko module for your Linux kernel 2.6.10-4-k7.
Detected Linux kernel sources "/lib/modules/2.6.10-4-k7/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-4-k7/build
                /usr/src/kernel-headers-2.6.10-4-k7
                /usr/src/linux-2.6.10-4-k7
                /usr/src/linux-2.6.10
                /usr/src/linux
                /usr/src/kernel-source-2.6.10-4-k7

```
I looked for kernel-source-2.6.10 in synaptic but couldn't find it.  The newest was 2.6.9
 Sounds interesting, I hope it doesnt damage my ntfs drive @ testing !.

---

### Post by trigg on 2005-03-13
[QUOTE=c0rrupt]
I looked for kernel-source-2.6.10 in synaptic but couldn't find it.  The newest was 2.6.9[/QUOTE]

Have you updated all your repositories for hoary?

trigg

---

### Post by jdong on 2005-03-13
Well, don't use it if you really cherish your data:

When I used captive with Kanotix, I found it slow (like you guys). 

However, it pushed ntldr onto the 2nd MFT, rendering my **NTFS partition UNBOOTABLE**. So, be careful!

---

### Post by Insanely on 2005-03-13
This is great. I will have to try this when I get home. I didn't know about alien! Handy tip.

Is there any draw backs on speed with captive-ntfs?

---

### Post by phantagom on 2005-03-15
Hi,

I have created deb packages for captive-ntfs, these are not converted with alien but build from the captive-static.tar.gz.

You can find them [here](http://www.kruyt.org/?sub_item=46) 

.

---

### Post by Pse on 2005-03-15
Nice, guys! I've been trying to get captive to run on a warty installation without luck =). I'll follow your steps =) (if I haven't messed my warty installation already)

---

### Post by kahping on 2005-03-16
[QUOTE=phantagom]Hi,

I have created deb packages for captive-ntfs, these are not converted with alien but build from the captive-static.tar.gz.

You can find them [here](http://www.kruyt.org/?sub_item=46) 

.[/QUOTE]

thanks, phantagom.

but there's something wrong with the install script? i can't get out of it; if i say no to all the questions because i want to obtain the needed drivers later, i can't. it just repeats over and over again in an infinite loop :-(

kahping

---

### Post by phantagom on 2005-03-16
[QUOTE=kahping]thanks, phantagom.

but there's something wrong with the install script? i can't get out of it; if i say no to all the questions because i want to obtain the needed drivers later, i can't. it just repeats over and over again in an infinite loop :-(

kahping[/QUOTE]


mm, it's not the install script but the setup prog from captive, i will change that. not running the setup from the install script, but a user action via cmdl.

---

### Post by subjectdenied on 2005-03-16
is it possible to use your deb-package with kernel 2.6.10 without patching the kernel? because the binary one can get from the captive-ntfs website doesn't work with kernel 2.6.10 (unless you patch it)?

---

### Post by Insanely on 2005-03-18
liam@lhiggo:~$ uname -a
Linux lhiggo 2.6.10-4-386 #1 Sat Mar 12 11:09:25 GMT 2005 i686 GNU/Linux
liam@lhiggo:~$ sudo apt-get install linux-headers-2.6.10-4-386
Reading Package Lists... Done
Building Dependency Tree... Done
linux-headers-2.6.10-4-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
liam@lhiggo:~$ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.10-4-386 (base version 2.6.10)
Destination module directory: /lib/modules/2.6.10-4-386/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.10-4-386/build
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.10-4-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.10-4-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-4-386/scripts/gcc-version.sh: line 12: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.10-4-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.10-4-386'
+ find /lib/modules/2.6.10-4-386/build -name .depend|xargs rm -f; rm -f /lib/modules/2.6.10-4-386/build/scripts/mkdep; rm -f /lib/modules/2.6.10-4-386/build/scripts/split-include; make -C /lib/modules/2.6.10-4-386/build dep
/usr/src/linux-headers-2.6.10-4-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-4-386/scripts/gcc-version.sh: line 12: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.10-4-386'
*** Warning: make dep is unnecessary now.
make: Leaving directory `/usr/src/linux-headers-2.6.10-4-386'
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.10-4-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.10-4-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-4-386/scripts/gcc-version.sh: line 12: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.10-4-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.10-4-386'
Failed to prepare lufs.ko module for your Linux kernel 2.6.10-4-386.
Detected Linux kernel sources "/lib/modules/2.6.10-4-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-4-386/build
                /usr/src/kernel-headers-2.6.10-4-386
                /usr/src/linux-2.6.10-4-386
                /usr/src/linux-2.6.10
                /usr/src/linux
                /usr/src/kernel-source-2.6.10-4-386
liam@lhiggo:~$

I have noidea where I am going wrong :(

I was thinking sudo apt-get install gcc-4.0

---

### Post by kahping on 2005-03-19
i have the problem, insanely. no idea y just now  :-( 

i'll update my system and see if it helps, though i doubt it would  [-o< 

kahping

edit: 

just checked out badri's blog site; insanely, you might want to try out badri's idea on solving this problem we're both having. i'll try it later when i'm back on Ubuntu  :)

---

### Post by Talomon on 2005-03-20
Just wanted to say that this is a great HOWTO. Works really great for me.

---

### Post by beefsprocket on 2005-03-20
What about this thread: [http://ubuntuforums.org/showthread.php?t=5176&highlight=lufs](http://ubuntuforums.org/showthread.php?t=5176&highlight=lufs)

> In Ubuntu, the kernel headers are in linux-headers-* instead of
kernel-headers-*. So you should install the package with

sudo apt-get install linux-headers-2.6.8.1-3-386

You can specify the location of these headers with the command

sudo module-assistant -k /usr/src/linux-headers-2.6.8.1-3-386

Then the module should build.

---

### Post by billy420 on 2005-03-20
thanks for this. very helpful.

---

### Post by beefsprocket on 2005-03-20
Right... Here it is (at least for me anyways). 

Step 1: Install gcc and kernel source for whichever version you so choose (I went with 2.6.10-4)

Step 2: Patch your kernel source with the following (taken from mail archive on captive [site](http://www.jankratochvil.net/pipermail/captive-list/2004-December/000645.html) )

diff -Naur kernel/signal.c.orig kernel/signal.c
--- kernel/signal.c.orig        2004-12-28 13:23:06.000000000 +0100
+++ kernel/signal.c     2004-12-28 13:24:59.000000000 +0100
@@ -1939,6 +1939,7 @@
 EXPORT_SYMBOL(sigprocmask);
 EXPORT_SYMBOL(block_all_signals);
 EXPORT_SYMBOL(unblock_all_signals);
+EXPORT_SYMBOL(kill_proc_info);  /* hcz */


 /*

To patch you should copy and paste the above into a new file and save.
Execute the following from within your /usr/src/linux directory:

patch -p0 < /path-to-previously-created-patch-goes-here

Step 3: Download captive-ntfs .deb from [here](http://www.kruyt.org/?sub_item=46) and install it.

Step 4: Compile your kernel and modules and reboot.

Step 5: Run captive-install-acquire and then try mounting your drive with mount -t captive-ntfs

Step 6: Write a reply telling me that I'm an idiot if this doesn't work for you  ](*,)

---

### Post by WingC3 on 2005-04-01
Your error requires you to install gcc. Go to the synaptic package manager and select it for install. I'm one step further and getting a new error message now saying that: 

Failed to prepare lufs.ko module for your Linux kernel 2.6.10-4-386.
Detected Linux kernel sources "/lib/modules/2.6.10-4-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.



But I have installed the debian version of those headers....so what gives?

---

### Post by Moeru on 2005-04-06
Am I missing something? I could've sworn I installed my kernel headers

Failed to prepare lufs.ko module for your Linux kernel 2.6.10-5-686.
Detected Linux kernel sources "/lib/modules/2.6.10-5-686/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.

---

### Post by phrob on 2005-04-10
same here..

Failed to prepare lufs.ko module for your Linux kernel 2.6.10-5-386.
Detected Linux kernel sources "/lib/modules/2.6.10-5-386/build" do not appear to
 be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.


i installed the headers.... 
can anyone tell me what's wrong ?!

---

### Post by kyle5778 on 2005-04-11
hi ,... i installed captive-ntfs the way its discribed, but still get error messages :


--------------------------------------------------------------------------------------------------------------------------------
Failed to prepare lufs.ko module for your Linux kernel 2.6.10-5-386.
Detected Linux kernel sources [COLOR=DarkRed]"/lib/modules/2.6.10-5-386/build"[/COLOR] do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.10-5-386/build
                /usr/src/kernel-headers-2.6.10-5-386
                /usr/src/linux-2.6.10-5-386
                /usr/src/linux-2.6.10
                [COLOR=Navy]/usr/src/linux[/COLOR]
                /usr/src/kernel-source-2.6.10-5-386
----------------------------------------------------------------------------------------------------------------------------------

all kernel-headers and sources are installed for kernel 2.6.10-5-386

--------------------------------------------------------------------------------------------------------------------------------
in : [COLOR=DarkRed]/lib/modules/2.6.10-5-386/[/COLOR]
lrwxrwxrwx   1 root root     35 2005-04-11 09:38 [COLOR=DarkRed]build -> /usr/src/linux-headers-2.6.10-5-386[/COLOR]

in : [COLOR=DarkRed]/usr/src/[/COLOR]
drwxr-xr-x  18 root root      704 2005-03-11 01:03 [COLOR=Navy]kernel-source-2.6.10[/COLOR]
-rw-r--r--   1 root root 35779826 2005-03-11 01:04 kernel-source-2.6.10.tar.bz2
lrwxrwxrwx   1 root src        21 2005-04-11 09:40 [COLOR=Navy]linux -> kernel-source-2.6.10/[/COLOR]
drwxr-xr-x   3 root root      520 2005-04-11 09:38 [COLOR=DarkRed]linux-headers-2.6.10-5-386[/COLOR]
---------------------------------------------------------------------------------------------------------------------------------

but it doesnt work ,... no idea y ,.. but would be nice someone explains y 

thx kyle5778

---

### Post by Suparious on 2005-04-19
I am getting the same errors

here is what I have don on a fresh install of 5.04

   1.  First download the rpm package from [http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)
   2. Install kernel-headers for your kernel revision
          * To find out your kernel type in the terminal 'uname -a'
          * To install kernel-headers use synaptic or apt-get to find and install the correct version
          * in my case i did 'apt-get install linux-headers-2.6.8.1-4-k7'
          * if do not know use 'apt-cache search linux-headers' for list of kernel headers available
   3. use alien to convert rpm to deb package
          * run 'alien captive-static-1.1.5-0.i386.rpm'
          * This creates captive-static_1.1.5_1.i386.deb
   4. Install deb package using 'dpkg -i captive-static_1.1.5_1.i386.deb'
   5. run 'captive-install-acquire'
          * Follow directions to find ntfs.sys and other files that captive needs.
   6. run '/usr/share/lufs/prepmod'
--------------------------------------------------------------------------------------------------
this is where I have a similar failure message:

Failed to prepare lufs.ko module for your Linux kernel 2.6.10-5-386.
Detected Linux kernel sources "/lib/modules/2.6.10-5-386/build" do not appear to be valid.

---------------------------------------------------------------------------------------------------

so I tried this: 

'module-assistant -k /usr/src/linux-headers-2.6.10-5-386/'

and prepared the lufs module, built it, installed it, updated my symlinks..... nogo!!

---------------------------------------------------------------------------------------------------

Please help!  I am very familliar with linux, but no expert. I have successfully used read/write with captive on suse 9.1, redhat9, and other non-debian style distros. 

I have no clue whay this is not working form me. I will post a solution if I find one, otherwise I would be more than grateful if someone can shed some light here!

Thanks,
Shaun

--------------------------------------------------------------------------------------------------------

I found more info on this here: [http://blog.badri.us/badriram/archive/2005/01/05/155.aspx](http://http://blog.badri.us/badriram/archive/2005/01/05/155.aspx)

apparently for now, it seems like we will have to patch and recompile the kernel. Then you will have to install captive from this kernel source....  

Badri has a link to a patch here: [http://www.badri.us/export_kpi.diff](http://http://www.badri.us/export_kpi.diff)

With these instructions: 
Go to the kernel source directory. then run

patch -p1 < export_kpi.diff

Once you have that done, you should be able recompile your kernel. I recommed using make_kpkg, which compiles and generate a deb package. I think it is a part of kernel_package in apt

-------------------------------------------------------------------------------------------------------

Is there a cleaner way to do this? I was going yo recompile my 2.6.10 for my k7 athlon, but I was enjoying the defaut optimizations of ubuntu 5.04 (fastest out-of-the-box distro I have installed).

Thanks,
Shaun

---

### Post by Suparious on 2005-04-20
OK, I decided to just try it....  here is what I have done with my kernel:

01. sudo apt-get install linux-source-2.6.10 linux-headers-2.6.10-5 linux-kernel-headers kernel-package 
02. sudo apt-get install linux-image-2.6.10-5-k7
03. sudo pico /boot/grub/menu.1st and put a commented out "hiddenmenu"
04. rebooted into the k7 kernel, works!
05. cd /usr/src/linux-source-2.6.10/
06. sudo  make-kpkg clean
06. sudo cp /boot/config-2.6.10-5-k7 .config
07. sudo wget [http://www.badri.us/export_kpi.diff](http://www.badri.us/export_kpi.diff)
08. sudo patch -p1 < export_kpi.diff 
09. sudo make-kpkg --append-to-version=masterkush --revision=001 kernel_image
10. sudo dpkg -i kernel-image-2.6.10masterkush_001_i386.deb

---

### Post by Suparious on 2005-04-20
was it a good idea to compile this with the linux-source-2.6.10? I didn't want to compile inside my k7 kernel headers as root.

I will post my results after I finish compiling it, I have to go to work now...   :roll:

---

### Post by thecrimsonking on 2005-05-04
Ya, these methods just don't work. period.

Strange because it was just soooo simple on mandrake 9.2, 10.1, fedora, and pclos.

I'll stick with usb keys, zip drives, and the more convienient network when I absolutely HAVE to write to NTFS, which is pretty much never.

---

### Post by cowlip on 2005-09-20
[QUOTE=thecrimsonking]Ya, these methods just don't work. period.

Strange because it was just soooo simple on mandrake 9.2, 10.1, fedora, and pclos.

I'll stick with usb keys, zip drives, and the more convienient network when I absolutely HAVE to write to NTFS, which is pretty much never.[/QUOTE]
 Yep, same lufs problem.  Oh well.

---

### Post by cowlip on 2005-09-20
[QUOTE=cowlip]Yep, same lufs problem.  Oh well.[/QUOTE]
 OK I got it to work THANK YOU SO MUCH Hairy_Palms

[quote=Hairy_Palms]ive found a workaround for this, the problem is that from the 2.6.10 kernal onwards it doesnt declare kill_proc_info ive made it work on my machine by doing this
1. install captive
2. run /usr/share/lufs/prepmod
3. open /usr/share/lufs/prepmod/2.6/inode.c
4. look for a line that says "kill_proc_info(SIGUSR1, &info, GET_INFO(sb)->server_pid);" and change it to say
kill_proc(SIGUSR1, &info, GET_INFO(sb)->server_pid);
now if u run prepmod you can mount and read/write ntfs partitions[/quote]

You basically need gcc3.4, build-essential, liinux-source-2.6.12 (or whatver number your kernel is) and linux-headers-2.6.12-8-386 (whatever your kernel/computer is; find out by typing in uname -a)

My7 only change is that /usr/share/lufs/prepmod/2.6/inode.c should be /usr/share/lufs/2.6/inode.c

---

### Post by eXcentra on 2005-10-03
I'd like to bump this thread. I need help...
I installed Ubuntu (my very first Linux at that) just yesterday. And I've already been having problems because of GRUB (as you can see [here](http://ubuntuforums.org/showthread.php?t=71302)). So what I wanted to do is mount the Windows NTFS partition and copy some files (mostly my brother's because I already backed up mine...) to my empty FAT32 partition. 
I was able to successfully mount the partition using this Captive technique (for some reason, I can't mount the partition with "mount -t vfat /dev/hda2 /mnt/win").
Now, how do I view the files? There isn't any icon or anything on the desktop.
Sorry for being such a noob but I really need help with this...

---

### Post by Hikaru79 on 2005-10-03
[QUOTE=eXcentra]I'd like to bump this thread. I need help...
I installed Ubuntu (my very first Linux at that) just yesterday. And I've already been having problems because of GRUB (as you can see [here](http://ubuntuforums.org/showthread.php?t=71302)). So what I wanted to do is mount the Windows NTFS partition and copy some files (mostly my brother's because I already backed up mine...) to my empty FAT32 partition. 
I was able to successfully mount the partition using this Captive technique (for some reason, I can't mount the partition with "mount -t vfat /dev/hda2 /mnt/win").
Now, how do I view the files? There isn't any icon or anything on the desktop.
Sorry for being such a noob but I really need help with this...[/QUOTE]

First of all, the reason you couldn't mount it without captive is because the type is ntfs , not vfat. So you can mount it without captive like this: ```
sudo mount -t ntfs /dev/hda2 /mnt/win
```
Then simply navigate to the /mnt/win directory, and copy whatever files you need using standard linux tools. You can even go there with Nautilus.

---

### Post by eXcentra on 2005-10-04
[QUOTE=Hikaru79]First of all, the reason you couldn't mount it without captive is because the type is ntfs , not vfat. So you can mount it without captive like this: ```
sudo mount -t ntfs /dev/hda2 /mnt/win
```
Then simply navigate to the /mnt/win directory, and copy whatever files you need using standard linux tools. You can even go there with Nautilus.[/QUOTE]
I get the following message:
> 
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

:|

---

### Post by johnnyangel on 2005-10-12
I was getting the same LUFS error, and running the following commands did the trick:

```

sudo apt-get install gcc-3.4-base
sudo apt-get install gcc-3.4

```
that allowed prepmod to run.  Now, however, the mount command just hangs...  Working on it.

---

### Post by Sianis on 2005-10-15
Hi all!

I have installed headers, and gcc, but premod doesn't work. Why?

Pls someoe write here all packages names what I need under Breezy.

Thanks!

---

### Post by jdwannam on 2005-10-21
I can't get the /usr/share/lufs/prepmod to run here either.  (using breezy)

I have installed linux-source-2.6.12, linux-headers-2.6.12-9-386, gcc-3.4, gcc-3.4-base

here is the output of prepmod:

```
make: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
  CC [M]  /usr/share/lufs/2.6/file.o
  CC [M]  /usr/share/lufs/2.6/inode.o
  CC [M]  /usr/share/lufs/2.6/proc.o
  CC [M]  /usr/share/lufs/2.6/symlink.o
  LD [M]  /usr/share/lufs/2.6/lufs.o
  Building modules, stage 2.
  MODPOST
*** Warning: "kill_proc_info" [/usr/share/lufs/2.6/lufs.ko] undefined!
  CC      /usr/share/lufs/2.6/lufs.mod.o
  LD [M]  /usr/share/lufs/2.6/lufs.ko
make: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
+ /bin/rm -rf /lib/modules/2.6.12-9-386/kernel/fs/lufs; /bin/mkdir -p /lib/modules/2.6.12-9-386/kernel/fs/lufs; /bin/ln -s /var/lib/lufs/lufs.ko /lib/modules/2.6.12-9-386/kernel/fs/lufs/lufs.ko
+ /sbin/rmmod lufs 2>/dev/null; /sbin/insmod /lib/modules/2.6.12-9-386/kernel/fs/lufs/lufs.ko 2>/dev/null
Failed to prepare lufs.ko module for your Linux kernel 2.6.12-9-386.
Detected Linux kernel sources "/lib/modules/2.6.12-9-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.12-9-386/build
                /usr/src/kernel-headers-2.6.12-9-386
                /usr/src/linux-2.6.12-9-386
                /usr/src/linux-2.6.12
                /usr/src/linux
                /usr/src/kernel-source-2.6.12-9-386
 at ./prepmod line 181

```


Any ideas? :confused: 

Thanks,

Duncan

---

### Post by jdwannam on 2005-10-21
Oops nevermind... I didn't read the entire thread sorry!   I changed kill_proc_info in inode.c to kill_proc and it compiled and mounts just fine.   Thanks for the information guys. :cool:

---

### Post by FrankTM on 2006-02-05
this thing is not working for me
i was able to install captive-static_1.1.7-1_i386.deb at step four and perform captive-install-acquire at step five

but then at step six i don't appear to have prepmod
i simple do not have a folder /usr/share/lufs

I tried to get that in several ways:
I've installed  lufs-cryptofs, lufs-source, lufs-utils, gcc-3.4 & gcc-3.4-base
I've browsed and searched the ubuntu packages at packages.ubuntu.com and with apt-file with no luck

does anyone know how to obtain prepmod or make this module work in another way?

---

### Post by FrankTM on 2006-02-05
[QUOTE=FrankTM]this thing is not working for me
i was able to install captive-static_1.1.7-1_i386.deb at step four and perform captive-install-acquire at step five

but then at step six i don't appear to have prepmod
i simple do not have a folder /usr/share/lufs

I tried to get that in several ways:
I've installed  lufs-cryptofs, lufs-source, lufs-utils, gcc-3.4 & gcc-3.4-base
I've browsed and searched the ubuntu packages at packages.ubuntu.com and with apt-file with no luck

does anyone know how to obtain prepmod or make this module work in another way?[/QUOTE]

seems like I didn't need the prepmod after all
after a few tries it suddenly started working
i did a manual **modprobe fuse** though, but i don't think that is nessary

---

### Post by RaptorRaider on 2006-02-05
Perhaps someone should update this thread?
The last time the startpost was updated was almost 13 months ago.

Aside from that, good NTFS writing support would be awesome, even if a bit slow.

---

### Post by barnabe on 2006-05-17
Thanks I have just tried it , it works fine .
a bit slow but i can handle it ;) ....

---

