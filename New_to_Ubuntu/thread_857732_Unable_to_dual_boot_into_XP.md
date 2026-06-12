---
title: "Unable to dual boot into XP"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by tuna_for_lunch on 2008-07-12
I tried to install a dual boot windows XP/ubuntu. I had XP previously installed on one partition of my hard drive and installed ubuntu on a second empty partition. I managed a working installation of ubuntu, but I am unable to boot into windows - I boot directly into ubuntu.

Looking back at the dual boot installation guide [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
I did not first open the installation CD in windows, and instead installed ubuntu directly from turning on my computer.

I have have not overwritten the XP partition (I hope).

Can anyone help me correct my mistake?

---

### Post by damis648 on 2008-07-12
> **tuna_for_lunch said:**
> I tried to install a dual boot windows XP/ubuntu. I had XP previously installed on one partition of my hard drive and installed ubuntu on a second empty partition. I managed a working installation of ubuntu, but I am unable to boot into windows - I boot directly into ubuntu.

Looking back at the dual boot installation guide [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
I did not first open the installation CD in windows, and instead installed ubuntu directly from turning on my computer.

I have have not overwritten the XP partition (I hope).

Can anyone help me correct my mistake?

What you did was fine, but when you came to the partition menu in the installer, what did you choose?

---

### Post by tuna_for_lunch on 2008-07-12
I partitioned manually as follows:

ext3  10GB partiton for root
ext3 20GB partition for \home
2GB swap
windows is on an ntfs partition (90GB)

---

### Post by rsambuca on 2008-07-12
First, try opening a terminal and entering the following command:

```
sudo fdisk -l
```After entering your password, copy the output into this thread and we will see what you have.

---

### Post by tuna_for_lunch on 2008-07-12
I ran that command; this is what came up: 


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc24dc24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       14592   117210208+   f  W95 Ext'd (LBA)
/dev/sda5            3825       14592    86493928+   7  HPFS/NTFS
/dev/sda6               1         243     1951803   82  Linux swap / Solaris
/dev/sda7            1460        3824    18996831   83  Linux
/dev/sda8             244        1459     9767488+  83  Linux

Partition table entries are not in disk order

---

### Post by rsambuca on 2008-07-12
Good news.  It definitely looks as though your XP partition is intact - the sda5 ntfs one.  That means you just have to add the XP boot entry to the menu.lst file so that grub can see it.

Open a terminal and post the output of:

```
cat /boot/grub/menu.lst
```

---

### Post by tuna_for_lunch on 2008-07-12
Phew! I really didn't want to have to install XP again! Here is the output:

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
timeout		3

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
# kopt=root=UUID=f0bbe214-b624-43e8-ad11-2c3075af70f3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f0bbe214-b624-43e8-ad11-2c3075af70f3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f0bbe214-b624-43e8-ad11-2c3075af70f3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by rsambuca on 2008-07-12
Well, hopefully you won't have to re-install, but to be honest, there are a couple of strange things here.  First, I don't recall XP ever being on logical partition before (sda1 to sda4 are for primary partitions, sda5 and up are for logical partitions within a primary partition).  The problem is that XP really likes to be in a primary partition.  The second strange thing is that Grub almost always sees XP during setup and adds XP as a boot option - definitely strange that it wasn't seen.

Anyways, we can still hope.  So the next thing is to figure out what to put for your XP entry.  The first thing I would try is adding this entry to the bottom of your menu.lst.  You can edit the menu.lst by using the text editor gedit:

```
gksudo gedit /boot/grub/menu.lst
```
Try adding this code to the bottom of the file after this line:  ### END DEBIAN AUTOMAGIC KERNELS LIST
```
title           Windows 
root            (hd0,4)
chainloader     +1

```
save the file, reboot, and try selecting Windows from the menu.  You will have to press "esc" during the three seconds that grub is loading to see the menu since you have the 'hiddenmenu' option.

---

### Post by tuna_for_lunch on 2008-07-12
Thanks. Unfortunately, not so much happened. I got to the boot menu, selected windows and ended up on a black screen with "Starting up ..." in the corner. Didn't get beyond this screen though.

---

### Post by SunnyRabbiera on 2008-07-12
sometimes dual booting can cause hiccups like this, be patient and hopefully your issue will be solved.

---

### Post by rsambuca on 2008-07-12
Hmmm...  Try making the Windows entry look like this

```
title           Windows 
rootnoverify            (hd0,4)
chainloader     +1
```

---

### Post by tuna_for_lunch on 2008-07-12
Exactly the same thing happens, I'm afraid.

---

### Post by tuna_for_lunch on 2008-07-13
Hi All, 
Does anyone else have any ideas of how I might fix this problem?

I can tell the dreaded "why can't you just leave things alone" is on my wife's lips. ;)

---

