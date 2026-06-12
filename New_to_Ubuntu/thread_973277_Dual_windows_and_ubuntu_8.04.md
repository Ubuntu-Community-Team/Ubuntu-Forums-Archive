---
title: "Dual windows and ubuntu 8.04"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by XxBlissXx on 2008-11-06
[SIZE="2"][FONT="Garamond"]Hey, well I was trying to have windows vista (for gaming) and ubuntu 8.04 on my computer and I've tried it a few times. Right now I have windows as my first partition and as my primary and I have ubuntu as my second and as a logical partition. I didn't resize either, from the beginning I used gparted on my live cd to split my hard drive in half. Then I just went ahead and reinstalled windows and then ubuntu. Now my problem is I can get to Windows anymore, there isn't an option too when I boot up. I've look at a few other posts and configured my device.map and menu.lst and that didn't help. When I did that the option came up for me to load windows but when I selected it it gave me an error message. .something about being invalid . .Anyway Windows was working fine when I first reinstalled it so I know it's not that. And making windows my primary and ubuntu my logical seemed to fix the hal.dll problem so I wanted to know if anyone could help me locate the root id # or path to windows so I can add it in my menu.lst and the correct device.map settings. . heres the info on my system and set-up

MENU.LST
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
# kopt=root=UUID=821a8ed2-3863-4ee2-afce-fbc63e4c0790 ro

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
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=821a8ed2-3863-4ee2-afce-fbc63e4c0790 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=821a8ed2-3863-4ee2-afce-fbc63e4c0790 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=821a8ed2-3863-4ee2-afce-fbc63e4c0790 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=821a8ed2-3863-4ee2-afce-fbc63e4c0790 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


DEVICE.MAP
(hd0) /dev/sde


MY PARTITIONS LOOK LIKE

8mb unallocated | /dev/sda5 116.24GB | /dev/sda6 166.15GB

unallocated   7.84mb
/dev/sda1      extended 232.88 GB      boot lba
        ##/dev/sda5    ntfs 116.24 GB
        ##/dev/sda6    ext3 / 116.15 GB
        ##/dev/sda7    linux-swap 494.16 mb


SYSTEM INFO
UBUNTU 8.04 HARDY
Kernal Linux 2.6.24-21-generic
GNOME 2.22.3

hardware
memory 1.9GB
cpu 0 amd atholon 64 dual 3800
cpu 1 amd atholon 64 dual 3800

disk space av.
102.9

and I have an Nvidia driver if that helps at all. .and yes, I am a complete newb and i don't really understand what all this involves, so if you need anymore info just ask and tell me how I can find it :). . but anyway PLEASE help me . .any input would be greatly appreciated .

[/FONT][/SIZE]

---

### Post by jimmy the saint on 2008-11-06
You may have installed ubuntu over windows.  I may be wrong, but it also looks like you made a large extended partition and populated it with logical partitions as opposed to using a primary partition for windows.  You should probably give windows its own primary partition.

---

### Post by gorgon on 2008-11-06
Hi there,

the issue might be in menu.lst, there didnt seem to be an entry for windows.

Edit it so that this comes under ## ## End Default Options ## :

```

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

```

---

### Post by caljohnsmith on 2008-11-06
So is sda5 your Windows partition? Windows normally can't boot from a logical partition unless it puts its boot files in some primary partition; it is possible to boot Windows directly from a logical partition, but it takes a little bit of work. How about first posting the full output of:
```
sudo fdisk -lu
```

---

### Post by gorgon on 2008-11-06
ah, and since your ntfs partition is at sda5, guessing that this is your windows one, you should change the above (hd0,0) to (hd0,4)

---

### Post by XxBlissXx on 2008-11-08
> **gorgon said:**
> Hi there,

the issue might be in menu.lst, there didnt seem to be an entry for windows.

Edit it so that this comes under ## ## End Default Options ## :

```

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

```

So I tried that and I tried it with the (hd0,4) setting but it gave me an invalid device request error

---

### Post by XxBlissXx on 2008-11-08
> **caljohnsmith said:**
> So is sda5 your Windows partition? Windows normally can't boot from a logical partition unless it puts its boot files in some primary partition; it is possible to boot Windows directly from a logical partition, but it takes a little bit of work. How about first posting the full output of:
```
sudo fdisk -lu
```

ok so here is what it gave me. . .
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   488392064   244188000    f  W95 Ext'd (LBA)
/dev/sda5           16128   243786374   121885123+   7  HPFS/NTFS
/dev/sda6       243786438   487379969   121796766   83  Linux
/dev/sda7       487380033   488392064      506016   82  Linux swap / Solaris



```

---

### Post by caljohnsmith on 2008-11-08
So your Windows is on a logical partition, sda5, which means that most likely when you installed it, Windows put its boot files in some primary partition that no longer exists. Or maybe when you installed Ubuntu you somehow moved Windows inside of your extended partition, so Windows ended up as a logical partition. Either way, to get your Windows booting, please post the output of the following so I can see if you have the necessary boot files:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt

```
Where "-l" is a lowercase L, not a one.

---

### Post by XxBlissXx on 2008-11-12
> **caljohnsmith said:**
> So your Windows is on a logical partition, sda5, which means that most likely when you installed it, Windows put its boot files in some primary partition that no longer exists. Or maybe when you installed Ubuntu you somehow moved Windows inside of your extended partition, so Windows ended up as a logical partition. Either way, to get your Windows booting, please post the output of the following so I can see if you have the necessary boot files:
```
sudo mount /dev/sda5 /mnt
ls -l /mnt

```
Where "-l" is a lowercase L, not a one.

ok

```

asia@asia-desktop:~$ ls -l /mnt
total 40
drwxrwxrwx 1 root root  4096 2008-11-04 18:39 Documents and Settings
drwxrwxrwx 1 root root  4096 2008-11-04 18:43 Program Files
drwxrwxrwx 1 root root     0 2008-11-04 18:56 RECYCLER
drwxrwxrwx 1 root root  4096 2008-11-04 18:39 System Volume Information
drwxrwxrwx 1 root root 28672 2008-11-04 18:50 WINDOWS




```

---

### Post by caljohnsmith on 2008-11-12
Unfortunately, you are definitely missing your Vista boot files. Considering that you just recently installed Ubuntu and Vista, I think your best bet may be just to wipe the HDD clean, repartition so that Vista gets the first primary partition on the drive (make sure it's not logical), create two more partitions for Ubuntu, reinstall Vista, and after that reinstall Ubuntu. If you really don't want to do that, here is a tutorial for how to boot Vista from a logical partition, and it's not exactly trivial:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

So it's up to you, but good luck with whatever you decide to do.

---

### Post by XxBlissXx on 2008-11-12
> **caljohnsmith said:**
> Unfortunately, you are definitely missing your Vista boot files. Considering that you just recently installed Ubuntu and Vista, I think your best bet may be just to wipe the HDD clean, repartition so that Vista gets the first primary partition on the drive (make sure it's not logical), create two more partitions for Ubuntu, reinstall Vista, and after that reinstall Ubuntu. If you really don't want to do that, here is a tutorial for how to boot Vista from a logical partition, and it's not exactly trivial:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

So it's up to you, but good luck with whatever you decide to do.


Thanks for your help anyway. .i'm going to go ahead try to boot it from my logical drive, hopefully i won't have to reinstall everything. .

11/15
Didn't work, I went to hermans post as suggested in the link. I changed my boot flag to my ntfs as suggested, added the window boot.ini, ntldr, NTDETECT.COM to my windows C: drive, used GRUB's hide and unhide commands and changed my menu.lst to what herman suggested without the makeactive+ part. . .

My drive became unreadable, so nothing would load, only the boot screen with the options which didn't work. . .

---

### Post by XxBlissXx on 2008-11-15
**[SOLVED]** Yah, ok first of all I did have to reinstall both windows and ubuntu but other than that it was a simple fix. My problem was that windows made itself the logical partition even if it was the first and only system installed, even when I selected for it to be primary. Anyway I'll make it quick, I cleared my drive, **reinstalled windows first** and as primary( which it still made itself logical) then I **reinstalled ubuntu** on the second half of my drive. Now when it was time for me to make my partitions **in ubuntu's install prog.** all I did was **clicked on my windows** partition **(ntfs)** then clicked **edit** then **selected ntfs** for the **first** option and then **/windows** for the **second** clicked ok then **made my ext3 partition as logical** and made my **swap **and thats it!! It finished the install and when it booted up there was my option to load windows. Now heres what my paritions look like as appose to before when windows was logical

[IMG]http://www.fileden.com/files/2006/11/8/361625/Screenshot--dev-sda%20-%20GParted.png[/IMG]

I guess that changed it over because even when I was installing ubuntu gparted was still showing windows as a logical partition. . .Anyway, yay :grin: now I can game AND have a system that works for everything else!!

---

