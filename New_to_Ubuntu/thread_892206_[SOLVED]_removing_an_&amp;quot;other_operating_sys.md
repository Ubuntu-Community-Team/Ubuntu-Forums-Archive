---
title: "[SOLVED] removing an &amp;quot;other operating system&amp;quot; from computer"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-16
it' listed in my GRUB menu as Debian.  This link explains everything about what is on what partition and how I got into this quagmire. [http://ubuntuforums.org/showthread.php?t=879702&page=5](http://ubuntuforums.org/showthread.php?t=879702&page=5)  I just want to free up the space that debian is taking up by removing it.  Anybody know how?  That is, without a grub error/boot failure?

---

### Post by tamoneya on 2008-08-16
can we see the output of this:```
sudo fdisk -l
```

---

### Post by adamogardner on 2008-08-16
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33f133f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19012   152705915+   7  HPFS/NTFS
/dev/sda2           19127       28432    74750445   83  Linux
/dev/sda3           28433       28905     3799372+   5  Extended
/dev/sda4           28906       30401    12016620   83  Linux
/dev/sda5           28433       28833     3221001   82  Linux swap / Solaris
/dev/sda6           28834       28905      578308+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 255 MB, 255066112 bytes
16 heads, 32 sectors/track, 973 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         973      249037+   6  FAT16

---

### Post by tamoneya on 2008-08-16
can we see menu.lst as well.
```
cat /boot/grub/menu.lst
```

---

### Post by adamogardner on 2008-08-16
cat /boot/grub/menu.lst
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
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

## ## End Default Options ##

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-19-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by tamoneya on 2008-08-16
first go into menu.lst and put a "#" before these lines:```
title Debian GNU/Linux, kernel 2.6.18-5-686
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro
initrd /boot/initrd.img-2.6.18-5-686
savedefault

title Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro single
initrd /boot/initrd.img-2.6.18-5-686
savedefault

```

Then run gparted by typing```
gksudo gparted
```
Then you are free to remove /dev/sda4.  You can make it into what ever you want for space and you can also try dynamically increasing the size of one of your current partitions.  Note that resizing is a little dangerous so make sure to back things up if you want to follow this route.

---

### Post by adamogardner on 2008-08-17
> **tamoneya said:**
> first go into menu.lst and put a "#" before these lines:```
title Debian GNU/Linux, kernel 2.6.18-5-686
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro
initrd /boot/initrd.img-2.6.18-5-686
savedefault

title Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro single
initrd /boot/initrd.img-2.6.18-5-686
savedefault

```

Then run gparted by typing```
gksudo gparted
```
Then you are free to remove /dev/sda4.  You can make it into what ever you want for space and you can also try dynamically increasing the size of one of your current partitions.  Note that resizing is a little dangerous so make sure to back things up if you want to follow this route.

when you say, "go into menu.lst, do you mean open up gedit? or? Please be more specific  
gparted is confusing too.  I can't learn this because if I tamper with it everything gets screwed up.   I need to touch something and see it work to learn it easily.

---

### Post by adamogardner on 2008-08-17
when you say, "go into menu.lst, do you mean open up gedit? or? Please be more specific
gparted is confusing too. I can't learn this because if I tamper with it everything gets screwed up. I need to touch something and see it work to learn it easily. Please forgive my timidity.

---

### Post by dreadmeat on 2008-08-17
the hash symbols # tell the system to 'ignore' the line.
it's called "commenting" or "commenting out" i believe.

find the folder called **/boot** inside that there is one called **/grub** in there is a file called **/menu.lst**

edit that file.

if you type [copy and paste rather] this
> 
sudo gedit /boot/grub/menu.lstinto your terminal
it will open that file in SUPER USER MODE, which means you can edit it.
it will tell you to be careful too.

---

### Post by adamogardner on 2008-08-17
> **dreadmeat said:**
> the hash symbols # tell the system to 'ignore' the line.
it's called "commenting" or "commenting out" i believe.


that just makes a lot of information invisible but still there?

---

### Post by dreadmeat on 2008-08-17
exactly, it's saying don't read [or use] any/everything after the #

kind of handy, i have some comments in my fstab file.
the text after the # is just for me =)
czech it out:> # <file system> <mount point> <type> <options> <dump> <pass>

proc                                       /proc          proc         defaults                     0  0  
**# /dev/sda1 :**
UUID=aab70474-924a-43c7-9192-822e8bbb03af  /              ext3         relatime,errors=remount-ro   0  1  
**# /dev/sda5 :**
UUID=fc4f6fad-632e-48f8-a1bf-2088c06a6cfa  none           swap         sw                           0  0  
**# odd**
/dev/scd0                                  /media/cdrom0  udf,iso9660  users,noauto,exec,utf8,sync  0  0  
/dev/scd1                                  /media/cdrom1  udf,iso9660  users,noauto,exec,utf8,sync  0  0  
**# /dev/sda2**
UUID=6cd84707-bdd5-4aa5-9a5f-e51dbd31de2b  /media/sda2    ext3         rw,suid,dev,exec,auto,users,async  0  2  
**# /dev/sda3**
UUID=48A6-8A9C                             /media/sda3    vfat         rw,suid,dev,exec,auto,users,async  0  2  
**# /dev/sdb1**
UUID=8ebbb5de-b121-4be0-bebc-ce9dcd70bbc1  /media/disk    ext3         rw,suid,dev,exec,auto,users,async  0  2  


---

### Post by Elfy on 2008-08-17
Open the file with gedit and delete the debian lines -

```
gksudo gedit /boot/grub/menu.lst
```

You can delete the old debian partion or empty it - you also have 2 swaps is there any reason why?


Edit - of course - if you installed grub to the debian partition then it will be lost and you will have to reinstall it with your buntu livecd.

---

### Post by adamogardner on 2008-08-17
> **forestpixie said:**
> Open the file with gedit and delete the debian lines

You can delete the old debian partion or empty it - you also have 2 swaps is there any reason why?


Oh hi forest pixie (you were 'my first' here when I joined the forum),  
So does deleting make a difference to commenting out?
also I want to eventually use the space for Arch install.  So I don't know if I'm asking the right questions.  I had edited my last post  with this but forgot to save I guess.

---

### Post by Elfy on 2008-08-17
If you are going to use the partition for the next great thing to play with I would leave the partition alone and when you install arch do whatever you need to do then. 

If you do want to deal with it then boot your livecd or livecd partition editor (a better choice) like parted magic and just format the partition. If you use the buntu livecd you will need to turn off the swap before you can do anything as it will mount them both.

There isn't any need to have seperate swaps, one would be used by whichever system you booted. So you could for instance delete sda4 (I think that is the debian partition from menu.lst) and sda5 and have 1 bigger ready to play with.

Regardless of what you do partition wise - it's a bit pointless having debian on the menu if it is going to be arch, or not pointing at any install.

And hi to you to :)

---

### Post by tamoneya on 2008-08-17
> **dreadmeat said:**
> the hash symbols # tell the system to 'ignore' the line.
it's called "commenting" or "commenting out" i believe.

find the folder called **/boot** inside that there is one called **/grub** in there is a file called **/menu.lst**

edit that file.

if you type [copy and paste rather] this
into your terminal
it will open that file in SUPER USER MODE, which means you can edit it.
it will tell you to be careful too.

because gedit is a gui program you should not use sudo.  Use gksudo instead:```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by dreadmeat on 2008-08-17
> **tamoneya said:**
> because gedit is a gui program you should not use sudo.  Use gksudo instead:```
gksudo gedit /boot/grub/menu.lst
```that would be similar for **x**ubuntu too then?

> gksudo **mousepad** /location/file
i've just tried it and it looks no different :s

---

### Post by adamogardner on 2008-08-17
oops I have managed two threads similar.  I am sorry.

---

### Post by dreadmeat on 2008-08-17
well that's it then, into the pit with ya ha ha ha :p

---

