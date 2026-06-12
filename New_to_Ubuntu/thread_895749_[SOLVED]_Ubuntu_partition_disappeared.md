---
title: "[SOLVED] Ubuntu partition disappeared"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by sprogmeister on 2008-08-20
Having been forced to use Windows for a course, I started to check out the XP partition I had on my dual boot machine. I started to try and remove sp3 from XP but gave up when the install disk told me I could only re-install. Since then the machine has booted straight into XP and gives no option for Hardy Heron, and it will not show up in my computer. I know the partition is there but cannot find, ideally I want to be able to boot into. At worst I want to be able to retrieve data. Please can someone help?

---

### Post by Elfy on 2008-08-20
I assume that you no longer have the menu list, in which case reinstall grub - use the livecd

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

---

### Post by sprogmeister on 2008-08-20
Thanks. Will try it

---

### Post by pi.boy.travis on 2008-08-20
Check this out:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by sprogmeister on 2008-08-20
Forestpixie, tried the method you suggested and got to the 'grub> setup (hd0)' and got the reply, "Error 17 cannot find selected partition". Any ideas about what I can do, please?

---

### Post by sprogmeister on 2008-08-20
Thanks for your help pi.boy.travis but I do not understand how I can follow that method without wiping the hard drive.  Any ideas?

---

### Post by Elfy on 2008-08-20
If you are in the livecd can you run this from a terminal

```
sudo fdisk -l
```

---

### Post by pi.boy.travis on 2008-08-20
OOPs, forgot to specify. . .  Look at the second post.

> Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

Hope this helps!

---

### Post by sprogmeister on 2008-08-20
> **forestpixie said:**
> If you are in the livecd can you run this from a terminal

```
sudo fdisk -l
```


What does this do?

---

### Post by sprogmeister on 2008-08-20
> **pi.boy.travis said:**
> OOPs, forgot to specify. . .  Look at the second post.



Hope this helps!

Thanks for that. I looked at and do not understand at all. I am getting:

sda1 ntfs
sda2 ntfs
sda3 swap
sda6 ext3

I tried all these numbers and got the error 17 over and over. Sorry for my naivety, but could you point me in the right direction?

---

### Post by pi.boy.travis on 2008-08-20
Is that a fdisk output?  fdisk identifies your partitions and gives you various data about them.  

Your problem is that the Windows boot loader has overwritten GRUB, the Linux boot loader.  All you have to do is put GRUB back into your MRB and you should be all set!

---

### Post by Elfy on 2008-08-20
I was just checking you actually had the partition. When you say

> Since then the machine has booted straight into XP and gives no option for Hardy Heron, does it mean you don't see the grub menu list at all?

Error 17 means that the partition it is trying doesn't exist.

I think that sda6 should be (hd0,6)

I think that pi.boy.travis is pointing at the end of the second post otherwise it's the same as I am.

---

### Post by sprogmeister on 2008-08-20
fdisk -l showed the partition on the live cd but didn't know what to do after. I am still having dramas with the grub, mainly because of my lack of understanding. Thank you both for your patience and help. Sorry for the time taken to reply, it is due to rebooting all the time. Please bear with me!

---

### Post by Elfy on 2008-08-20
Can you do this in a terminal, it should get us a copy of your menu list, please paste all of it. 

```
sudo mkdir /recovery
sudo mount -t ext3 /dev/sda6 /recovery
cat /recovery/boot/grub/menu.lst
```

Also paste 

```
sudo fdisk -l
``` from there as well

---

### Post by sprogmeister on 2008-08-20
Frostpixie, no I am unable to see any grub menu. The machine boots straight to XP. I tried the hd0,6 and it didn't work. There seems to be no output from fdisk -l, although I can see inside the 'missing' drive with the live CD  Help!

---

### Post by Elfy on 2008-08-20
Sorry mean to say boot the livecd and run those commands from there, if that doesn't help try supergrub, boot xp go [here]("http://www.supergrubdisk.org/index.php?pid=5") burn as an iso and you can boot with it.

---

### Post by sprogmeister on 2008-08-20
> **forestpixie said:**
> Can you do this in a terminal, it should get us a copy of your menu list, please paste all of it. 

```
sudo mkdir /recovery
sudo mount -t ext3 /dev/sda6 /recovery
cat /recovery/boot/grub/menu.lst
```

Also paste 

```
sudo fdisk -l
``` from there as well

Did as you said, gives a long list and shows the heron part of the hdd. fdisk -l seems to give no output though. Please can you guide me?

---

### Post by sprogmeister on 2008-08-20
the first bit is as:

ubuntu@ubuntu:~$ sudo mkdir /recovery
mkdir: cannot create directory `/recovery': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /recovery
mount: /dev/sda6 already mounted or /recovery busy
mount: according to mtab, /dev/sda6 is already mounted on /recovery
ubuntu@ubuntu:~$ cat /recovery/boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5deb64a4-7d5a-4f67-a791-9111b4f72986 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

ubuntu@ubuntu:~$

---

### Post by sprogmeister on 2008-08-20
then:

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$

---

### Post by Elfy on 2008-08-20
It's a lowercase L not a 1

```
sudo fdisk -l
```

---

### Post by Elfy on 2008-08-20
Use the command as given - you need sudo

---

### Post by sprogmeister on 2008-08-20
Ooops missed out the sudo:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f580c4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  12  Compaq diagnostics
/dev/sda2   *         913        5776    39070080    7  HPFS/NTFS
/dev/sda3            5777        9729    31752472+   5  Extended
/dev/sda5            5777        5898      979933+  82  Linux swap / Solaris
/dev/sda6            5899        9729    30772476   83  Linux

---

### Post by Elfy on 2008-08-20
Run the grub restore from the livecd again - I think it should be hd0,5 not hd0,6 as you tried previously

---

### Post by sprogmeister on 2008-08-20
Forestpixie (apologies for misreading your name earlier), it all works again. Thank you very much for your help and patience, very gratefully appreciated!

The sprog rides again!!

---

### Post by Elfy on 2008-08-20
Completely welcome - please mark thread solved - and if there's a solved finally button use that :lol:

---

