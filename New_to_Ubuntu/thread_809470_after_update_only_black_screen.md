---
title: "after update only black screen"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by cmcfarland21 on 2008-05-27
I have Hardy 8.04.  After installing updates yesterday, instead of restarting I just shut down my CPU.  This morning when I started the cpu, NO GRUB just a black command screen saying

GRUB>

I have two harddrives, main with XP and slave has Ubuntu 8.04

What do I do from here?

Can someone Help????
I tried 
GRUB> find /boot/grub/stage1
     = (hd0,1)
GRUB> root (hd0,1)
GRUB> setup (hd0)

It came up successful but nothing changed. Still can't get into XP or Ubuntu.

Can I backup my Ubuntu files somehow and re-install ubuntu, therefore re-installing the GRUB?

---

### Post by d.kusummmanth@gmail.com on 2008-05-27
> **cmcfarland21 said:**
> I have Hardy 8.04.  After installing updates yesterday, instead of restarting I just shut down my CPU.  This morning when I started the cpu, NO GRUB just a black command screen saying


GRUB>

What do I do from here?
please **post ur system log** here. Ur **system specifications** might also help. The more clearly we can understand ur problem, the easier it is for us to guide u towards the right solution.

In the mean time, u can Google "Ubuntu GRUB errors"

---

### Post by Majorix on 2008-05-27
Use a LiveCD and check your /boot/grub/menu.lst . It might have gotten corrupt in the upgrade process.

---

### Post by cmcfarland21 on 2008-05-27
I still have the 7.10 Gutsy LiveCD.  Will that work even though I have upgraded to 8.04.

I am at work right now but:
from that GRUB> command can I type find /boot/grub/stage1 to find the hd

---

### Post by cmcfarland21 on 2008-05-27
> **Majorix said:**
> Use a LiveCD and check your /boot/grub/menu.lst . It might have gotten corrupt in the upgrade process.

How do I know if its corrupt?

Of all the files in disk-2/boot/grub menu.lst was changed yesterday.

results of fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         549       30401   239794222+   7  HPFS/NTFS
/dev/hda2               1         548     4401778+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e700e70

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2327    18691596   83  Linux
/dev/hdb2            2328        2434      859477+   5  Extended
/dev/hdb5            2328        2434      859446   82  Linux swap / Solaris

---

### Post by cmcfarland21 on 2008-05-28
Can Anyone Help????

---

### Post by phr0ze on 2008-05-28
does it look like there is a backup of the menu file? sometimes with the same name in the same location with an extension of .BAK or .Backup?

---

### Post by cmcfarland21 on 2008-05-28
no,  thanks though

How can I install a new GRUB.

---

### Post by cmcfarland21 on 2008-05-29
From the live CD, Can I backup my Ubuntu files somehow and re-install ubuntu, therefore re-installing the GRUB?

---

### Post by philinux on 2008-05-29
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

grub from live cd

Does not affect you files just restores the mbr.

I've got a copy of supergrub burned just for this.

---

### Post by d.kusummmanth@gmail.com on 2008-05-29
> **cmcfarland21 said:**
> How do I know if its corrupt?

Of all the files in disk-2/boot/grub menu.lst was changed yesterday.

results of fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         549       30401   239794222+   7  HPFS/NTFS
/dev/hda2               1         548     4401778+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e700e70

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2327    18691596   83  Linux
/dev/hdb2            2328        2434      859477+   5  Extended
/dev/hdb5            2328        2434      859446   82  Linux swap / Solaris


**checkout my result:**

vinay@eeee-desktop:~$ man fdisk

[1]+  Stopped                 man fdisk
vinay@eeee-desktop:~$ fdisk -l
vinay@eeee-desktop:~$ sudo fdisk -l
[sudo] password for vinay:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf83df83d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    b  W95 FAT32
/dev/sda2            1276        9541    66396645   83  Linux
/dev/sda3            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris
vinay@eeee-desktop:~$ 




why don't u use the UBUNTU irc???

---

### Post by cmcfarland21 on 2008-05-29
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

grub from live cd

Does not affect you files just restores the mbr.

I've got a copy of supergrub burned just for this.

How do you get that to work?   I have downloaded 3 different versions of the sgd and my cpu will not boot using them.

---

### Post by joshedmonds on 2008-05-29
Hi Chris, you asked if I could help based on another Grub problem I helped with, but I haven't got any experience of ending up at a Grub command line.

I would suggest you boot in with a liveCD (the 7.10 cd is fine) and try following the instructions on the other post ([http://ubuntuforums.org/showthread.php?t=809297](http://ubuntuforums.org/showthread.php?t=809297)). 

This is the current configuration of your hard drives:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

Device Boot Start End Blocks Id System
/dev/hda1 * 549 30401 239794222+ 7 HPFS/NTFS
/dev/hda2 1 548 4401778+ b W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e700e70

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 2327 18691596 83 Linux
/dev/hdb2 2328 2434 859477+ 5 Extended
/dev/hdb5 2328 2434 859446 82 Linux swap / Solaris
```

It looks like you have Windows installed on the primary hard-drive (hd0) and Linux on the secondary drive (hd1).

Windows (hd0,0) hda1
Linux (hd1,0) hdb1

Presuming you installed Ubuntu correctly, you will find the Grub menu.lst under (hd1,0)boot/grub/menu.lst

You need to mount the partition that Ubuntu is installed on.

Find your mounted partition (probably under /mnt/disk or media/disk) and open the file /boot/grub/menu.lst

Copy and paste the complete text of the file here on the forums (remember to use the code tags when pasting code/text).

Then we can have a look at what might be wrong. As I said I don't have any experience with your particular problem, so hopefully the problem is in your menu.lst

---

### Post by cmcfarland21 on 2008-05-31
Here it is.  I really need help.  

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
## e.g. kopt=root=/dev/hda1 ro UUID=3e0ef06b-14eb-4578-87cd-17fe6c1034f4 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3e0ef06b-14eb-4578-87cd-17fe6c1034f4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3e0ef06b-14eb-4578-87cd-17fe6c1034f4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3e0ef06b-14eb-4578-87cd-17fe6c1034f4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3e0ef06b-14eb-4578-87cd-17fe6c1034f4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by philinux on 2008-05-31
When it boots after the bios post do you see 

grub loading stage 1.5

---

### Post by cmcfarland21 on 2008-05-31
All I see when I start my cpu is a black screen that says, 

[Minimal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]


grub>_

---

### Post by philinux on 2008-05-31
Odd one that.

Does the bios give it's normal 1 short beep to say everything is ok?

I would still follow this and reinstall grub from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by cmcfarland21 on 2008-05-31
I did the grub> find /boot/grub/stage1  several times and nothing

Is setup (hd0) correct.  I have two hd's 

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

Device Boot Start End Blocks Id System
/dev/hda1 * 549 30401 239794222+ 7 HPFS/NTFS
/dev/hda2 1 548 4401778+ b W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e700e70

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 2327 18691596 83 Linux
/dev/hdb2 2328 2434 859477+ 5 Extended
/dev/hdb5 2328 2434 859446 82 Linux swap / Solaris



```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1 
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

grub> 
```

---

### Post by philinux on 2008-05-31
From what was returned it looks like it should be.

setup (hd1)

I'm no grub expert that's why I use supergrub. 
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

On the top right are downloads for cdrom floppy and usb stick.

---

### Post by tom56 on 2008-05-31
> **philinux said:**
> From what was returned it looks like it should be.

setup (hd1)

I'm no grub expert that's why I use supergrub. 
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

On the top right are downloads for cdrom floppy and usb stick.

No, setup (hd0) was definitely right. You want setup to install GRUB to whatever disk the BIOS boots first (which should be hd0).

---

### Post by cmcfarland21 on 2008-05-31
> **philinux said:**
> From what was returned it looks like it should be.

setup (hd1)

I'm no grub expert that's why I use supergrub. 
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

On the top right are downloads for cdrom floppy and usb stick.


Supergrub did not fix mine.  I downloaded and it could not fix whatever issue I have.

---

### Post by joshedmonds on 2008-06-02
Your menu.lst appears fine, you followed the instructions you were given properly - I agree it should be setup (hd0).

I can suggest a couple of things.

```

GRUB> boot

```

if that doesn't work

```

GRUB> root (hd1,0)
GRUB> setup (hd0)
GRUB> boot

```

if that doesn't work

```

GRUB> root (hd1,0)
GRUB> kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/hdb1
GRUB> boot

```

if that doesn't work

```

GRUB> exit

```

After that I'm out of ideas. Try the Grub manual at [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html) for more info.

---

