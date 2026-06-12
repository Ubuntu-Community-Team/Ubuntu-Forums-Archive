---
title: "Stuffed up my partition because iI'm a kno(0)b."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by clarkyscored on 2008-06-03
Well I installed Ubuntu three times because I kept stuffing up and making mistakes. So now when the computer starts, at the grub menu before you log on to either windows or ubuntu, I have 10 different ubuntus to choose from and one windows. 

Inside ubuntu on the desktop I have a useless 14.3g media HDD next to my current Ubuntu's 13.2g media hdd.

I want to fix the computer so that I only have the necessary Ubuntus in the startup menu and put the useless 14.3 back into windows. 


How do I do this?

---

### Post by Sam Lars on 2008-06-03
These are listed in the file /boot/grub/menu.lst

---

### Post by clarkyscored on 2008-06-03
> **Sam Lars said:**
> These are listed in the file /boot/grub/menu.lst

How do I get to that?

---

### Post by clarkyscored on 2008-06-03
> **Sam Lars said:**
> These are listed in the file /boot/grub/menu.lst

Ok I found that. What Do I delete and how do I get rid of that horrible 14.2 gig that's doing nothing?



This is what is there...


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
# kopt=root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2ea854b6-fda1-477c-b630-df169f780e45 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=2ea854b6-fda1-477c-b630-df169f780e45 ro single 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2ea854b6-fda1-477c-b630-df169f780e45 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2ea854b6-fda1-477c-b630-df169f780e45 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Sam Lars on 2008-06-03
I would recommend copying this file somewhere else before doing anything to it, so you can copy it back if something goes wrong.

After the line that reads
```
## ## End Default Options ##
```
Are all of the options for boot.
Each Ubuntu instance has three entries.  The regular kernel, recovery mode, and memtest.  Delete all three of those for the instance that you want to remove.

---

### Post by drs305 on 2008-06-03
First, backup your boot menu:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

For now, the easiest way to avoid seeing all the options is to go to:

System > Administration > StartUp Manager > Advanced > Tick ... Limit number of kernels in boot menu and enter # 2  

This will hide all but the last two kernels. You will see two kernels and 2 recovery modes, plus a memtest. It's best to be able to view at least two kernels in case the newest one causes problems. It does not remove the older kernels from the computer.



If you don't see the preceeding menu choice, in terminal run:
```
sudo aptitude install startupmanager
```

---

### Post by clarkyscored on 2008-06-03
> **Sam Lars said:**
> These are listed in the file /boot/grub/menu.lst

> **Sam Lars said:**
> I would recommend copying this file somewhere else before doing anything to it, so you can copy it back if something goes wrong.

After the line that reads
```
## ## End Default Options ##
```
Are all of the options for boot.
Each Ubuntu instance has three entries.  The regular kernel, recovery mode, and memtest.  Delete all three of those for the instance that you want to remove.


Because I reinstalled Ubuntu, I think I might have two versions on my HDD as well as windows. I want to get rid of one them because it's a waste of 14.3g and I want to fix the start up...


drs305 - I tried that and it didn't work. I still have all those options listed at the start up. I limited it to two Kernals and I still a bunch of stuff...

---

### Post by clarkyscored on 2008-06-03
> **drs305 said:**
> First, backup your boot menu:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

For now, the easiest way to avoid seeing all the options is to go to:

System > Administration > StartUp Manager > Advanced > Tick ... Limit number of kernels in boot menu and enter # 2  

This will hide all but the last two kernels. You will see two kernels and 2 recovery modes, plus a memtest. It's best to be able to view at least two kernels in case the newest one causes problems. It does not remove the older kernels from the computer.



If you don't see the preceeding menu choice, in terminal run:
```
sudo aptitude install startupmanager
```


So I have a feeling it's because there might be another Ubuntu installed... I don't want to go into it because I have no idea what it will do to my computer...

Is there anyway I can remove it?

---

### Post by clarkyscored on 2008-06-04
Bumpo

---

### Post by clarkyscored on 2008-06-04
So I went into my windows partition thing and it shows this...


[IMG]http://i8.photobucket.com/albums/a26/g-drive/Untitled-3.jpg[/IMG]

Does this mean I have three unnecessary Ubuntu partitions? It would make sense, because I've reinstalled three times... I don't want to delete anything, because last time I stuffed up the grub client, which is another reason I had to reinstall..

---

### Post by didac on 2008-06-04
Like drs305 says, do:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then edit your menu.lst by hand:

```
sudo gedit /boot/grub/menu.lst
```

Delete everything from ## ## End Default Options ## downwards, and paste the following code:

```

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04, memtest86+
root (hd0,7)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Once you are booting again with only one ubuntu option, post your /etc/fstab and the output of 

```
sudo fdisk -l
```

here to help you continue cleaning other installations and partitions. Or maybe you'll be happy like this.

---

### Post by clarkyscored on 2008-06-05
> **didac said:**
> Like drs305 says, do:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then edit your menu.lst by hand:

```
sudo gedit /boot/grub/menu.lst
```

Delete everything from ## ## End Default Options ## downwards, and paste the following code:

```

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=d3854dc4-da72-45e4-9b48-db881e31c58b ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04, memtest86+
root (hd0,7)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Once you are booting again with only one ubuntu option, post your /etc/fstab and the output of 

```
sudo fdisk -l
```

here to help you continue cleaning other installations and partitions. Or maybe you'll be happy like this.


Thanks so much for your help.


Here you go.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf4b025b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43582   350072383+   7  HPFS/NTFS
/dev/sda2           43583       48641    40636417+   5  Extended
/dev/sda5           45218       46826    12924229+  83  Linux
/dev/sda6           46827       46903      618471   82  Linux swap / Solaris
/dev/sda7           46904       48641    13960453+  83  Linux
/dev/sda8           43583       45142    12530637   83  Linux
/dev/sda9           45143       45217      602406   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2050 MB, 2050560000 bytes
64 heads, 32 sectors/track, 1955 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1956     2002160    6  FAT16
```

Quite the mess, I know.

---

### Post by drs305 on 2008-06-05
I'll take a look at the above. In the meantime, I wrote a fairly comprehenive post yesterday on grub menu displays. You may want to check it out:

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

It does appear you could have two installations of ubuntu since you have 2 swaps. First, we need to make sure which partition is your active ubuntu setup. From what you have indicated, it's probably sda8, but let's make sure. Please post the results of:
```
cat /etc/fstab
```

This will show us which partitions are being mounted and where. You might also want to check out partitions 6 & 7 to see if there is any data you want on those two. Once we determine they contain nothing you want but do contain an extra ubuntu setup we can go about reformatting them. But not yet!

---

### Post by clarkyscored on 2008-06-06
> **drs305 said:**
> I'll take a look at the above. In the meantime, I wrote a fairly comprehenive post yesterday on grub menu displays. You may want to check it out:

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

It does appear you could have two installations of ubuntu since you have 2 swaps. First, we need to make sure which partition is your active ubuntu setup. From what you have indicated, it's probably sda8, but let's make sure. Please post the results of:
```
cat /etc/fstab
```

This will show us which partitions are being mounted and where. You might also want to check out partitions 6 & 7 to see if there is any data you want on those two. Once we determine they contain nothing you want but do contain an extra ubuntu setup we can go about reformatting them. But not yet!


Thanks so much for helping me with this! 

```
michael@michael-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d3854dc4-da72-45e4-9b48-db881e31c58b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=e90972ac-f833-4f36-b8b5-53d70aa9501c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


There's nothing I want on the other partitions. The sooner they're gone the better...


Oh and maybe this will help too
[IMG]http://i8.photobucket.com/albums/a26/g-drive/yeah.jpg[/IMG]

---

### Post by didac on 2008-06-06
OK, now you can delete sda5 sda6 and sda7.

Are you sure you don't have anything inside? Maybe mount them and at least have a look at the home folder in each partition. sda6 won't contain any interesting thing, as it is only swap. But if you are sure . . . go ahead and delete. Make no mistake, only 5 6 and 7 are for deletion.

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> OK, now you can delete sda5 sda6 and sda7.

Are you sure you don't have anything inside? Maybe mount them and at least have a look at the home folder in each partition. sda6 won't contain any interesting thing, as it is only swap. But if you are sure . . . go ahead and delete. Make no mistake, only 5 6 and 7 are for deletion.


I'm trying to delete them from the partition editor on Ubunutu and whenever I goto delete, it tells me to 'Cannot delete, Please unmount any logical partitions having a number higher than 7."

What does that mean? They're not mounted to begin with...

---

### Post by didac on 2008-06-06
I'm sorry. I'm more comfortable with fdisk. If you are willing:

```

mount

```

It will tell you whether 5, 6 and 7 are mounted, and where. I don't think they're mounted. Just in case. If they are:

```

sudo umount /dev/sda5
sudo fdisk /dev/sda

```

Press 'l' then 'd' and enter the partitions numbers, one at a time. Exit by typing 'w'

Hope it helps. You must be about to despair . . .

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> I'm sorry. I'm more comfortable with fdisk. If you are willing:

```

mount

```

It will tell you whether 5, 6 and 7 are mounted, and where. I don't think they're mounted. Just in case. If they are:

```

sudo umount /dev/sda5
sudo fdisk /dev/sda

```

Press 'l' then 'd' and enter the partitions numbers, one at a time. Exit by typing 'w'

Hope it helps. You must be about to despair . . .

Ah yeah,it got a bit scary here.

```

Command (m for help): l

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot   
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data    
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access     
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor      
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT        
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep        
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT            
1c  Hidden W95 FAT3 75  PC/IX          

Command (m for help): d
Partition number (1-9): 

```

---

### Post by didac on 2008-06-06
Sorry, my typo. It's 'p' not 'l' Will just show you your partitions. After 'd' enter '5' Answer all the horrible messages, then 'd' again for 6 and 'd' for '7' 'w' to write changes and exit

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> Sorry, my typo. It's 'p' not 'l' Will just show you your partitions. After 'd' enter '5' Answer all the horrible messages, then 'd' again for 6 and 'd' for '7' 'w' to write changes and exit

I get no horrible questions - just this.


```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43582   350072383+   7  HPFS/NTFS
/dev/sda2           43583       48641    40636417+   5  Extended
/dev/sda5           45218       46826    12924229+  83  Linux
/dev/sda6           46827       46903      618471   82  Linux swap / Solaris
/dev/sda7           46904       48641    13960453+  83  Linux
/dev/sda8           43583       45142    12530637   83  Linux
/dev/sda9           45143       45217      602406   82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help): d
Partition number (1-9): 5

Command (m for help): 
```

---

### Post by didac on 2008-06-06
Continue with 'd' 6 'd' 7 'w' and you are done. Go to gparted and do what you like to the empty space

---

### Post by clarkyscored on 2008-06-06
Haha I feel so useless!

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.


WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```

Oh wait...I had Parititon Editor open when I did that...Was that bad?

What now?

---

### Post by clarkyscored on 2008-06-06
[IMG]http://i8.photobucket.com/albums/a26/g-drive/ohno-1.jpg[/IMG]


I don't want to shut the computer down because I'm scared Grub will crash or something...

---

### Post by didac on 2008-06-06
You're through with your troubles --  well this one. Just reboot and ubuntu will read the new partition table. No problems with grub

---

### Post by clarkyscored on 2008-06-06
Ok, now im on my other computer because mine's stuck with Grub Error 22...

Any ideas?

---

### Post by didac on 2008-06-06
At this rate, you're going to kill me :)

Do you have a boot-liveCD with ubuntu on it? Keep it at hand.

Can you press a key when the computer starts? Just when you get a message for a few second saying: "GRUB loading". Select you normal booting line (Ubuntu blah, blah) and without pressing enter, press 'e'

Press 'e' again and make that entry look like root (hd0,4) Press ESC
Go to the second line, press 'e' and make it look like 

kernel /boot/vmlinuz-2.6.24-18-generic root=/dev/sda5 ro

press ESC and 'b'

Keep me posted. Now you'll have to make some more modifications in your /etc/fstab once you get done with this

---

### Post by clarkyscored on 2008-06-06
Haha...I've gone ahead and did what I did before to fix it....install another Ubunutu. It's got the smallest possible partition I can make. It seems to repair the grub...

Anywhere we can go from there?

---

### Post by didac on 2008-06-06
I thought you wanted to save that partition.

Do you have ANY data in your ubuntu partitions? If you don't, boot with the intsllation CD again, delete all partitions with the fdisk business. After 'p' delete with 'd' any that is not sda1, which is your windows partitions. Save with 'w' and reinstall again.

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> I thought you wanted to save that partition.

Do you have ANY data in your ubuntu partitions? If you don't, boot with the intsllation CD again, delete all partitions with the fdisk business. After 'p' delete with 'd' any that is not sda1, which is your windows partitions. Save with 'w' and reinstall again.

Nah I want to keep my partition. I'm back on my proper Ubuntu now. However, I now just have another Ubuntu I won't use and that unallocated space....


I must seem so ignorant. I'm really sorry. What do I do now?

---

### Post by didac on 2008-06-06
Well, we are back to square one. Really, if there is no data, just delete everything but sda1 with the live CD and reinstall. If for some mysterious reasons you want to keep the partition, post again your /boot/grub/menu.lst /etc/fstab and fdisk -l and we start  the show again.

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> Well, we are back to square one. Really, if there is no data, just delete everything but sda1 with the live CD and reinstall. If for some mysterious reasons you want to keep the partition, post again your /boot/grub/menu.lst /etc/fstab and fdisk -l and we start  the show again.


I want to keep my Ubuntu Partition because it has stuff on it that I wanted. Like the drivers, settings and stuff I downloaded...I don't want to lose it all.


What would be the reason for why the Grub messed up?

---

### Post by didac on 2008-06-06
Grub messed up because fdisk shifted your partition numbers. Now post /boot/grub/menu.lst /etc/fstab and fdisk -l as it is now.

---

### Post by clarkyscored on 2008-06-06
I'm getting permission denied on anything I type into the terminal....



This is so frustrating.

---

### Post by clarkyscored on 2008-06-06
```
michael@michael-desktop:~$ fdisk -l
michael@michael-desktop:~$ fdisk -l
michael@michael-desktop:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf4b025b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43582   350072080    7  HPFS/NTFS
/dev/sda2           43583       48641    40636417+   5  Extended
/dev/sda5           46827       46903      618471   82  Linux swap / Solaris
/dev/sda6           43583       45142    12530637   83  Linux
/dev/sda7           46904       48562    13325886   83  Linux
/dev/sda8           48563       48641      634536   82  Linux swap / Solaris

```

That's all I can get


aaannd
[/code
```
michael@michael-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d3854dc4-da72-45e4-9b48-db881e31c58b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=e90972ac-f833-4f36-b8b5-53d70aa9501c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
michael@michael-desktop:~$ sudo cp /boot/grub/menu.lst
cp: missing destination file operand after `/boot/grub/menu.lst'
Try `cp --help' for more information.
michael@michael-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d3854dc4-da72-45e4-9b48-db881e31c58b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=e90972ac-f833-4f36-b8b5-53d70aa9501c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
michael@michael-desktop:~$ 

```

---

### Post by didac on 2008-06-06
```
sudo fdisk /dev/sda
```

press 'p' Start with 'd' again. Don't delete 1, 2 nor your old swap and good partition. I don't know which numbers will they have by now. They are the one which in the listing will match these lines:

  Device Boot      Start         End      Blocks   Id  System

/dev/sdaXX          43583       45142    12530637   83  Linux
/dev/sdaYY          45143       45217      602406   82  Linux swap / Solaris

Of course XX and YY are the new numbers. DON'T delete them. Summary, delete all but 1, 2 XX and YY. exit with 'w'

Boot. Before getting error 22, press any key. Just when you get a message for a few second saying: "GRUB loading". Press 'c'

Enter

```
find /boot/grub/stage1
```

whatever it answers, enter it in the next line

```
root (hd0,4)
```

0,4 if it told you 0,4, or whatever. 

```
setup (hd0)
```

Or follow the instructions I gave before, but start first with the lines above.

"Can you press a key when the computer starts? Just when you get a message for a few second saying: "GRUB loading". Select you normal booting line (Ubuntu blah, blah) and without pressing enter, press 'e'

Press 'e' again and make that entry look like root (hd0,4) Press ESC
Go to the second line, press 'e' and make it look like

kernel /boot/vmlinuz-2.6.24-18-generic root=/dev/sda5 ro

press ESC and 'b'"

---

### Post by didac on 2008-06-06
Ok, I've seen your listings. The grub command will be

```
root (hd0,4)
setup (hd0)
```

Do it once you have deleted partitions 7 and 8. these are the ones you have to delete.

And you are done . . . hopefully

---

### Post by clarkyscored on 2008-06-06
Haha mate, you have the patience of a saint...


I'll give it a crack...

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> /dev/sdaXX 43583 45142 12530637 83 Linux
/dev/sdaYY 45143 45217 602406 82 Linux swap / Solaris

```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf4b025b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43582   350072080    7  HPFS/NTFS
/dev/sda2           43583       48641    40636417+   5  Extended
/dev/sda5           46827       46903      618471   82  Linux swap / Solaris
/dev/sda6           43583       45142    12530637   83  Linux
/dev/sda7           46904       48562    13325886   83  Linux
/dev/sda8           48563       48641      634536   82  Linux swap / Solaris

Partition table entries are not in disk order

```

As you can see, the swap isn't listed....

---

### Post by didac on 2008-06-06
cat /etc/fstab

something like

# /dev/sda5
UUID=e90972ac-f833-4f36-b8b5-53d70aa9501c none    swap    sw    0       0

will tell you your working swap sda5 or sda8. I bet is sda5. If it is, go ahead and delete 7 and 8 only.

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> cat /etc/fstab

something like

# /dev/sda5
UUID=e90972ac-f833-4f36-b8b5-53d70aa9501c none    swap    sw    0       0

will tell you your working swap sda5 or sda8. I bet is sda5. If it is, go ahead and delete 7 and 8 only.

```
michael@michael-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=d3854dc4-da72-45e4-9b48-db881e31c58b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=e90972ac-f833-4f36-b8b5-53d70aa9501c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
michael@michael-desktop:~$ 

```


When I select the Kernel i want to run, it's SDA6 I choose, if that's any help...

---

### Post by didac on 2008-06-06
Data are discordant. fstab says you are using sda8 as root and sda9 as swap. According to fdisk, sda8 is swap and sda9 doesn't exist

Press a key when the computer starts, just when you get a message for a few second saying: "GRUB loading". Select you good booting line (Ubuntu the sda6 thing) and without pressing enter, press 'e'

Press 'e' again and make that entry look like root (hd0,5) Press ESC
Go to the second line, press 'e' and make it look like

kernel /boot/vmlinuz-2.6.24-18-generic root=/dev/sda6 ro

press ESC and 'b

If it doesn't boot, do root (hd0,4) and kernel /boot/vmlinuz-2.6.24-18-generic root=/dev/sda5 ro


Once you boot correctly, edit

```
sudo /boot/grub/menu.lst
```

look for the right entry and substitute for the lines above, the one that gave you access.

---

### Post by clarkyscored on 2008-06-06
Just quickly, I'd be happy to completely format everything I've done so far on Ubuntu and start from scratch. It would seem to be a lot easier. There's not really a whole lot I want to salvage from my partition, and all this code scares the **** out of me and I don't want to lose windows. Is that an option?

---

### Post by didac on 2008-06-06
Yeah, it's a faster option. Just when you reinstall, make sure gparted deletes everything before repartitioning. Everything, but Windows, of course.

Good luck

---

### Post by clarkyscored on 2008-06-06
> **didac said:**
> Yeah, it's a faster option. Just when you reinstall, make sure gparted deletes everything before repartitioning. Everything, but Windows, of course.

Good luck

You wouldn't know where to start? :lolflag:

---

### Post by didac on 2008-06-06
:lolflag::lolflag:

---

