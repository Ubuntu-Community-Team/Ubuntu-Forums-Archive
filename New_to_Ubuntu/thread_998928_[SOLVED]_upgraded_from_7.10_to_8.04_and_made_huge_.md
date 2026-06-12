---
title: "[SOLVED] upgraded from 7.10 to 8.04 and made huge mistake"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by lmbrice on 2008-12-01
While in process of running the upgrade from 7.10 to 8.04 I stupidly said yes to Keep current menu.lst. (something like that) not thinking that it wouldn't place the 8.04 in the menu. Now I can't boot into 7.10 or Windows XP (i partitioned the drive and have a dual boot system). It was one of those things I knew was wrong the moment I hit the key. 

Now I get Error 17: Cannot mount selected partition

please help

---

### Post by philinux on 2008-12-01
Either reinstall grub from the live cd.
[How to install Grub from a live Ubuntu cd. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=224351") 

Or use super grub
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by -Zeus- on 2008-12-01
you need to boot to a recovery disc, then mount the hard drive, and edit the menu.lst.  Can you do this, or do you need more help?  I don't see why windows wouldn't work.

---

### Post by lmbrice on 2008-12-01
I get the same error from the recovery disk selection. I also tried to go about it with my 7.10 cd, but it wouldn't boot. I burned and am running the supergrub, but now I'm at a total loss of what to do.

---

### Post by caljohnsmith on 2008-12-01
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
sudo blkid
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```
All the above should hopefully give us enough info to help you get Grub working again. :)

---

### Post by lmbrice on 2008-12-01
While running supergrub it said it fixed the 8.04, but then I go to reboot and it only shows choices for 7.10 and WinXP where none of them work. I burned 8.10 as an iso and my computer won't boot from that either.

---

### Post by caljohnsmith on 2008-12-01
OK, how about trying this: when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. If that doesn't work, try (hd1,Y), and if that doesn't work, try different values of Y with X=0. One of those combinations should be enough to boot Ubuntu if your Grub menu is not to far off. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See if you can boot Ubuntu using that method, and we can work from there.

---

### Post by philinux on 2008-12-01
If I remember gutsy it used to use say /dev/hda1 or /dev/sda1 then hardy came along but it uses uuid's e.g. 
## ## End Default Options ##

```
title        Ubuntu jaunty (development branch), kernel 2.6.27-7-generic
uuid        46f0a359-373a-4b54-b773-405b860ce6db
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=46f0a359-373a-4b54-b773-405b860ce6db ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

```

My guess is that as you didn't let it install anew menu.lst you got the old way which wont boot.

---

### Post by lmbrice on 2008-12-01
Philinux,
That is what happened. I just don't know how to fix it. SuperGrub will allow me to access XP, but nothing else. Can I install 8.10 without destroying XP? There isn't anything on my Ubuntu side as far as files/documents needed and I only would need to reinstall other apps.
Thanks,
I really appreciate all the help.

---

### Post by lmbrice on 2008-12-01
> **caljohnsmith said:**
> OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
sudo blkid
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```
All the above should hopefully give us enough info to help you get Grub working again. :)


With 8.10 I was able to get a terminal and enter the above. Now what do I do?

---

### Post by philinux on 2008-12-01
Need to see the info those commands gave.
For instance 
blkid
will give you the uuid's

---

### Post by lmbrice on 2008-12-01
when I entered sudo blkid I got the following.
/dev/sda1: UUID="a6539469-3768-4f1e-858e-469542a70f68" TYPE="ext3" 
/dev/sda2: UUID="0CFCDD5CFCDD411E" TYPE="ntfs" 
/dev/sda5: UUID="efd09ad2-67fd-4270-8119-cacb7059bc48" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

then I entered - 
ubuntu@ubuntu:~$ ls -l /mnt boot
ls: cannot access boot: No such file or directory
/mnt:
total 104
drwxr-xr-x   2 root root  4096 2008-12-01 03:27 bin
drwxr-xr-x   3 root root  4096 2008-12-01 03:33 boot
lrwxrwxrwx   1 root root    11 2007-11-01 10:45 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-12-01 03:33 dev
drwxr-xr-x 146 root root 12288 2008-12-01 03:35 etc
drwxr-xr-x   5 root root  4096 2007-11-19 04:30 home
drwxr-xr-x   2 root root  4096 2007-10-15 23:17 initrd
lrwxrwxrwx   1 root root    33 2008-12-01 03:32 initrd.img -> boot/initrd.img-2.6.24-22-generic
lrwxrwxrwx   1 root root    33 2008-11-30 17:45 initrd.img.old -> boot/initrd.img-2.6.22-16-generic
drwxr-xr-x  18 root root 12288 2008-12-01 03:21 lib
drwx------   2 root root 16384 2007-11-01 10:45 lost+found
drwxr-xr-x   3 root root  4096 2008-12-01 03:31 media
drwxr-xr-x   2 root root  4096 2007-10-08 10:47 mnt
drwxr-xr-x   3 root root  4096 2007-11-20 19:10 opt
drwxr-xr-x   2 root root  4096 2007-10-08 10:47 proc
drwxr-xr-x  25 root root  4096 2008-12-01 03:16 root
drwxr-xr-x   2 root root  4096 2008-12-01 03:21 sbin
drwxr-xr-x   2 root root  4096 2007-10-15 23:17 srv
drwxr-xr-x   2 root root  4096 2007-10-04 11:17 sys
drwxrwxrwt  18 root root  4096 2008-12-01 03:35 tmp
drwxr-xr-x  13 root root  4096 2008-12-01 03:13 usr
drwxr-xr-x  16 root root  4096 2007-11-02 13:56 var
lrwxrwxrwx   1 root root    30 2008-12-01 03:32 vmlinuz -> boot/vmlinuz-2.6.24-22-generic
lrwxrwxrwx   1 root root    30 2008-11-30 17:45 vmlinuz.old -> boot/vmlinuz-2.6.22-16-generic


Now what do I do?

---

### Post by caljohnsmith on 2008-12-01
How about following the steps from post #5, beginning with posting the output of the fdisk command. If you run into problems doing the next steps, please post whatever results you get in case something goes wrong.

---

### Post by lmbrice on 2008-12-01
Here's what I have:
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00082b63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *     1477980   114543449    56532735   83  Linux
/dev/sda2       114543450   300704669    93080610    7  HPFS/NTFS
/dev/sda3       300704670   312576704     5936017+   5  Extended
/dev/sda5       300704733   312576704     5935986   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="a6539469-3768-4f1e-858e-469542a70f68" TYPE="ext3" 
/dev/sda2: UUID="0CFCDD5CFCDD411E" TYPE="ntfs" 
/dev/sda5: UUID="efd09ad2-67fd-4270-8119-cacb7059bc48" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ ls -l /mnt/boot
total 52468
-rw-r--r-- 1 root root  424317 2008-02-12 10:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  424374 2008-11-24 21:46 abi-2.6.22-16-generic
-rw-r--r-- 1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r-- 1 root root   75311 2008-02-12 10:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   75300 2008-11-24 21:46 config-2.6.22-16-generic
-rw-r--r-- 1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
drwxr-xr-x 2 root root    4096 2008-12-01 03:33 grub
-rw-r--r-- 1 root root 7236800 2008-11-30 17:45 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7236764 2008-11-30 17:44 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 7235927 2008-11-30 17:47 initrd.img-2.6.22-16-generic
-rw-r--r-- 1 root root 7235492 2008-11-30 17:45 initrd.img-2.6.22-16-generic.bak
-rw-r--r-- 1 root root 7499096 2008-12-01 03:33 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 7499112 2008-12-01 03:32 initrd.img-2.6.24-22-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2008-02-12 10:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  823860 2008-11-24 21:46 System.map-2.6.22-16-generic
-rw-r--r-- 1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 10:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1765592 2008-11-24 21:46 vmlinuz-2.6.22-16-generic
-rw-r--r-- 1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
default		3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=a6539469-3768-4f1e-858e-469542a70f68 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=a6539469-3768-4f1e-858e-469542a70f68 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=a6539469-3768-4f1e-858e-469542a70f68 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a6539469-3768-4f1e-858e-469542a70f68 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a6539469-3768-4f1e-858e-469542a70f68 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP 
root 		(hd0,0) 
makeactive 
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-01
OK, while you still have sda1 mounted on /mnt (from the last instructions), do:
```
gksudo gedit /mnt/boot/grub/menu.lst &
```
And then change all the Ubuntu entries to use "root (hd0,0)" instead of (hd0,1), similar to:
```
title Ubuntu 7.10, kernel 2.6.22-16-generic
root [COLOR="Red"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.22-16-generic root=UUID=a6539469-3768-4f1e-858e-469542a70f68 ro quiet splash
initrd /boot/initrd.img-2.6.22-16-generic
quiet
```
Also, change your Windows entry at the very bottom of that file to:
```
title Windows XP
root [COLOR="Red"](hd0,1)[/COLOR]
makeactive
chainloader +1 
```
Save, reboot, and let me know if that works to boot Ubuntu.

---

### Post by lmbrice on 2008-12-01
You totally ROCK! Now how do I get it that it will default to XP when my kids need it for schoolwork<

---

### Post by TJCIB on 2008-12-01
I think you can just add something like

```
timeout 2
color black/cyan yellow/cyan
default 0
```

and make the default whichever boot option you want to be default.  Make the timeout however many seconds you want to have to select something else...

I think that's right...but I'm still learning too.

*edit* add at the top of your grub listing, just above the first Linux entry
*second edit* You have to start with ZERO as your first entry, as you've noticed, grub starts counting from ZERO not one.

I recommend 

timeout 10
color black/cyan yellow/cyan
default 5

---

### Post by lmbrice on 2008-12-01
Thanks so much. You understand way more than I do. 

THANKS EVERYONE!

---

### Post by caljohnsmith on 2008-12-01
That's great news it worked OK. Cheers and have fun with your OSes. :)

---

