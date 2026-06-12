---
title: "error 23: error while parsing number"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Sec Expert on 2008-06-04
hello,
I have dual boot:Win XP and Ubuntu but now I have just faced a strange problem,when I click on XP I get this message:error 23: error while parsing number.I don't know what I have done.please help me.:lolflag:

---

### Post by ajmorris on 2008-06-04
hi there,
can you please post the contents of your /boot/grub/menu.lst file. And also the output of sudo fdisk -l


AJ

---

### Post by Sec Expert on 2008-06-05
**this is the content of menu.lst:**

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

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
# kopt=root=UUID=310c76ea-69fe-4ad8-97a3-decbe53d013d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310c76ea-69fe-4ad8-97a3-decbe53d013d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=310c76ea-69fe-4ad8-97a3-decbe53d013d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault=true
makeactive
chainloader	+1


**and this is the output of fdisk -l:**

khh@KHPOWER:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31dc31db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1569    12602961    7  HPFS/NTFS
/dev/sda2            1570        8077    52275510    f  W95 Ext'd (LBA)
/dev/sda3            8078        9729    13269690   83  Linux
/dev/sda5            1570        1963     3164773+   7  HPFS/NTFS
/dev/sda6            1964        2151     1510078+   7  HPFS/NTFS
/dev/sda7            2152        4758    20940696    7  HPFS/NTFS
/dev/sda8            4759        6160    11261533+   7  HPFS/NTFS
/dev/sda9            6161        7998    14763703+   7  HPFS/NTFS
/dev/sda10           7999        8077      634536   82  Linux swap / Solaris

**you know I'm a newbie,I don't get a thing from these things and I'm totally confused:confused:**

---

### Post by Xiong Chiamiov on 2008-06-05
If you boot with [SuperGrubDisk]("http://supergrubdisk.org"), are you able to boot into the Windows partition directly?  If so, then you just need to recreate GRUB with same said disk.

---

### Post by Sec Expert on 2008-06-05
Hi dear Xiong Chiamiov,
thank you for your answer,can you explain more ,you know I don't have a cd writer or something,but I saw a "download FLOPPY" link on the homepage of supergrub.should I download that?:-s:)
How can I use that supergrub?

---

### Post by Xiong Chiamiov on 2008-06-05
Well, I haven't done it with a floppy before, but go ahead and download the latest version in your language.  From there, try doing [this]("http://supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_Floppy.") to install it onto the floppy.  From there, if you can get it booted, just follow the directions.  Sometimes the navigation's a little confusing, but I generally find it easier than doing it all manually.

---

### Post by Sec Expert on 2008-06-06
> **ajmorris said:**
> hi there,
can you please post the contents of your /boot/grub/menu.lst file. And also the output of sudo fdisk -l


AJ

you didn't get what the problem was(is)?:(.I've put what you said.;-)

---

### Post by Sec Expert on 2008-06-06
> **Xiong Chiamiov said:**
> Well, I haven't done it with a floppy before, but go ahead and download the latest version in your language.  From there, try doing [this]("http://supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_Floppy.") to install it onto the floppy.  From there, if you can get it booted, just follow the directions.  Sometimes the navigation's a little confusing, but I generally find it easier than doing it all manually.

I have downloaded the floppy file for Ubuntu,It's a *.img file(is that a picture?!).Now what should I do with that?:confused:

I read the wiki(the link you told me).I do'nt understand this:dd if=/path/to/floppyimage of=/dev/fd0.my problem is that I don't know what to write instead of path.I'm not familiar with paths in Ubuntu.](*,)

---

### Post by Sec Expert on 2008-06-07
as it is clear nobody wants to help me!:confused:

---

### Post by Mr Pockets151 on 2008-06-07
Try reading over this. There is a link here also that tells you how to use your supergrub disc when you have it.[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html")

and this which explains how to use the .img file on a floppy...[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#How_Make_your_Super_Grub_Floppy_Disk]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#How_Make_your_Super_Grub_Floppy_Disk")

So basically to make the disc use the image you dl'd.

USING UBUNTU
1. put  super_grub_disk_floppy_english_0.9575.img into your /home/username directory
2. Put a blank floppy disk in your machine's floppy disk drive.
3. Open a terminal
4. then do this ```
dd if=super_grub_disk_floppy_english_0.9575.img of=/dev/fd0
```
and this is directly out of the reading.  Should be easy.

---

### Post by meierfra. on 2008-06-07
```
savedefault=true
```
causes "Error 23.  Error while parsing a number"

Just change it to

```
savedefault
```

and you should be all set.

---

### Post by Sec Expert on 2008-06-09
> **meierfra. said:**
> ```
savedefault=true
```
causes "Error 23.  Error while parsing a number"

Just change it to

```
savedefault
```

and you should be all set.

thank you man that worked,I can't believe it, nobody knew that,that was gr8.:lolflag:

---

