---
title: "Don't see 8.10 in boot menu"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by dgbearcat on 2008-11-07
Hey guys,

I've been running Ubuntu for about a year now, and after all of my initial problems, it's been smooth sailing until now.

I just upgraded to 8.10, but I'm having some problems. I've got an nvidia issue that I think I can fix with the fix found here:[http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu](http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu)

However, one other thing I've noticed is that when I get to the boot menu (Grub, I think it is?), all I see is 8.04. Where do I go so that I can be sure I'm booting into the correct thing?

---

### Post by tdrusk on 2008-11-07
> **dgbearcat said:**
> Hey guys,

I've been running Ubuntu for about a year now, and after all of my initial problems, it's been smooth sailing until now.

I just upgraded to 8.10, but I'm having some problems. I've got an nvidia issue that I think I can fix with the fix found here:[http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu](http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu)

However, one other thing I've noticed is that when I get to the boot menu (Grub, I think it is?), all I see is 8.04. Where do I go so that I can be sure I'm booting into the correct thing?
I think you press escape when it shows that. It should bring up a list.

---

### Post by caljohnsmith on 2008-11-08
It might be that during your upgrade process, you told the upgrader not to update your Grub's menu.lst with the new kernel used in Intrepid. How about opening a terminal (applications > accessories > terminal), and posting:
```
ls -l /boot
cat /boot/grub/menu.lst
```
Note that "-l" is a lowercase L, not a one.

---

### Post by dgbearcat on 2008-11-08
> **caljohnsmith said:**
> It might be that during your upgrade process, you told the upgrader not to update your Grub's menu.lst with the new kernel used in Intrepid. How about opening a terminal (applications > accessories > terminal), and posting:
```
ls -l /boot
cat /boot/grub/menu.lst
```
Note that "-l" is a lowercase L, not a one.

Unfortunately, I don't see 8.10 anywhere in the list. It's like it didn't install it, although I know that it did due to the fact that NVidia doesn't seem to work anymore. Every time I try to enable the restricted drivers, it just reboots crashed. 

The error I'm getting is: (EE)Nvidia(0): Failed to load the NVidia kernal module! ***Abort*** Screen(s) found, but none have a usable configuration.

I tried to use the fix I found on the page I put in the OP, but it hasn't seemed to work. 

Anyone have any ideas on this, please?

---

### Post by kansasnoob on 2008-11-08
Be assured that you have the best help possible in Caljohnsmith!

Be patient he'll get you sorted out!

---

### Post by kansasnoob on 2008-11-08
> **kansasnoob said:**
> Be assured that you have the best help possible in Caljohnsmith!

Be patient he'll get you sorted out!

Oops. I meant to add, please post the output of the commands that Caljohnsmith asked you to run. Sorry.

---

### Post by dgbearcat on 2008-11-08
> **kansasnoob said:**
> Oops. I meant to add, please post the output of the commands that Caljohnsmith asked you to run. Sorry.

Oops! I misread it and thought the commands were going to clean up the list :) I'll try to flip back over and post that.

---

### Post by dgbearcat on 2008-11-08
> **caljohnsmith said:**
> It might be that during your upgrade process, you told the upgrader not to update your Grub's menu.lst with the new kernel used in Intrepid. How about opening a terminal (applications > accessories > terminal), and posting:
```
ls -l /boot
cat /boot/grub/menu.lst
```
Note that "-l" is a lowercase L, not a one.

```
-rw-r--r-- 1 root root  424317 2007-10-14 20:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  422607 2008-04-10 11:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  507665 2008-11-04 15:00 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   75311 2007-10-14 20:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   79964 2008-04-10 11:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   91364 2008-11-04 15:00 config-2.6.27-7-generic
drwxr-xr-x 2 root root    4096 2008-11-08 13:26 grub
-rw-r--r-- 1 root root 7211061 2008-04-13 22:08 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7211408 2008-04-13 20:57 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 7436927 2008-04-22 07:47 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7437051 2008-04-22 07:45 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 8101284 2008-11-08 13:28 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r-- 1 root root  823535 2007-10-14 20:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  899892 2008-04-10 11:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1029585 2008-11-04 15:00 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root    1073 2008-11-04 15:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root 1764280 2007-10-14 20:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 11:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 2244464 2008-11-04 15:00 vmlinuz-2.6.27-7-generic

```



```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0ca51cbe-0f42-47be-839e-873a7de866ac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ca51cbe-0f42-47be-839e-873a7de866ac ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ca51cbe-0f42-47be-839e-873a7de866ac ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by caljohnsmith on 2008-11-08
OK, looks like you just need to add the new Intrepid kernel to your menu.lst, so first do:
```
gksudo gedit /boot/grub/menu.lst
```
And before your Ubuntu entries, add:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ca51cbe-0f42-47be-839e-873a7de866ac ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```
Save, reboot, try the new 8.10 entry, and let me know how it goes. :)

---

### Post by dgbearcat on 2008-11-08
> **caljohnsmith said:**
> OK, looks like you just need to add the new Intrepid kernel to your menu.lst, so first do:
```
gksudo gedit /boot/grub/menu.lst
```
And before your Ubuntu entries, add:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0ca51cbe-0f42-47be-839e-873a7de866ac ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```
Save, reboot, try the new 8.10 entry, and let me know how it goes. :)

Thanks, that fixed the boot menu, and I assume that since it loaded, it worked correctly.

Any idea on the nvidia issue? It loads OK with default graphics settings, but I've always been fine using "extra" as my graphics settings and having compiz-fusion running with all kinds of fun stuff.

The error it gives me is after it gives the loading bar at startup, and then it goes to very bad resolution and says 

```

(EE)Nvidia(0):Failed to load the nvidia kernal module!
(EE)Nvidia(0):***aborting***
(EE)Screen(s) found, but none have a usable configuration

```

---

### Post by dgbearcat on 2008-11-08
Anyone? Bump?

---

### Post by Pudworthy on 2008-11-10
I think that you've actually already solved that problem. I had the same issue and I realised it was because I was using the old Ubuntu kernel. When I found the new one and started using that, the problem disappeared.

P

---

