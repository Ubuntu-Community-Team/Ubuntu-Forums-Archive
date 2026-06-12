---
title: "[SOLVED] Help, Grub :("
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Mikey_W on 2008-05-17
Hello
I recently created a second partition to put windows on, so installed windows and then couldn't boot back into ubuntu. So i searched forums etc and twiddled with grub (probably shouldn't of), managed to get grub working and now lets me boot into ubuntu but now i've lost windows. :confused:
To my knowledge the partition with windows is untouched and still there working fine but i just cant access it,
When i boot it gives me the options of:
Ubuntu
Ubuntu recovery
mem test

and thats it. Can someone please help me?

---

### Post by robalcorn on 2008-05-17
Try using this link and it will help out your problem

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by the8thstar on 2008-05-17
Hello there. Open up a terminal, and type:

**> sudo fdisk -l**

please copy and paste the results of that command in your next post and we'll go from there.

Also, still in the terminal, type:

**> sudo gedit /boot/grub/menu.lst**

and again, paste it in your answer.

---

### Post by shifty_powers on 2008-05-17
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

may help you ;)

---

### Post by Mikey_W on 2008-05-17
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d704c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20458   164328853+  83  Linux
/dev/sda2   *       20459       29649    73826707+   7  HPFS/NTFS
/dev/sda3           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 4111 MB, 4111466496 bytes
16 heads, 32 sectors/track, 15684 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x08812a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15684     4015088    c  W95 FAT32 (LBA)



there ya go :KS

---

### Post by shifty_powers on 2008-05-17
we'll need the contents of your menu.lst as the8thstar requested ;)

---

### Post by Mikey_W on 2008-05-17
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=8dfce2b2-ffa9-4c86-b773-d32ca53853bd ro

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8dfce2b2-ffa9-4c86-b773-d32ca53853bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8dfce2b2-ffa9-4c86-b773-d32ca53853bd ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by shifty_powers on 2008-05-17
i think if you add

```
title Windows xp
root (hd1,0)
makeactive
chainloader +1
```

to the end, before it saya end debain automagic kernel list, it you will have a valid entry to boot into windows...

---

### Post by the8thstar on 2008-05-17
I think it's mixed up. Try this instead: 

> title Windows xp
**root (hd0,1)**
makeactive
chainloader +1

Reasoning:

**hd0 **(identified as sda in fdisk -l) has:

hd0,0 UBUNTU = /dev/sda1 1 20458 164328853+ 83 Linux
**hd0,1 WINDOWS XP = /dev/sda2 * 20459 29649 73826707+ 7 HPFS/NTFS**
hd0,3 EXTENDED PARTITION = /dev/sda3 29650 30401 6040440 5 Extended
hd0,4 LINUX SWAP = /dev/sda5 29650 30401 6040408+ 82 Linux swap / Solaris

**hd1** (identified as sdb in fdisk -l) has only a FAT32 partition.

---

### Post by shifty_powers on 2008-05-17
heh, bit rusty on this one.

---

### Post by meierfra. on 2008-05-17
Also you need to put it AFTER   "end debian automagic kernel list". Otherwise your windows entry will disappear during the next kernel update

---

### Post by Mikey_W on 2008-05-17
Thanks very much, worked perfectly!!

---

### Post by shifty_powers on 2008-05-17
heh happy to help ;) (ok, so i'm a bit rusty on gurb but meh :P)

oh and click on the thread tools at the top and mark the thread solved ;)

---

