---
title: "[SOLVED] GRUB Question"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by melrom on 2008-06-17
Okay, so I changed my partitions a lot today, so I'm editting grub's menu.lst, but I have one question.

I checked that the uuid was the same by typing the following into a terminal:

```

ls -l /dev/disk/by-uuid

```

However, I know that the kernel part [as listed in menu.lst] is probably wrong. For instance, where it says:

```

kernel /boot/vmlinuz-2.6.24-19-generic root=UUID='my uuid'

```

Where 'my uuid' is actually a long string of stuff that I didn't feel like typing out. Basically, I don't think the kernel I want it loading is 2.6.24. Is there a terminal command where I can check this??

---

### Post by melrom on 2008-06-17
oh thanks. i used

```

uname -a

```

oh that was dumb. that's only for the system i'm working on lol. okay yeah but if i look under /boot/, it should be the latest one in there, right?? Which I have as 

```

vmlinuz-2.6.24.19-generic

```

Does that seem correct?

---

### Post by justleen on 2008-06-17
uname -a will list the details about youre current kernel (the one your using now)

---

### Post by bumanie on 2008-06-17
To get uuid for all devices > sudo blkid without further parameters.

---

### Post by melrom on 2008-06-17
> **justleen said:**
> uname -a will list the details about youre current kernel (the one your using now)

yeah, that'd be for the live CD though.


EDIT: I still get Grub Error 22 upon startup.

---

### Post by justleen on 2008-06-17
try supergrub on a usb stick for the easy way out ;)

to prevent of rebooting, try editing the kernel parameters in the grub menu (press 'e' on a selection, then edit the line you want.

PS: you dont have to use the UUID, you can also use /dev/sdaX, easier "trial and error"  when editting the grub menu at boot time

---

### Post by hyper_ch on 2008-06-17
post your grub menu.lst here.

---

### Post by melrom on 2008-06-17
Here are the results of fdisk -l

```

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2               5        9313    74774542+   7  HPFS/NTFS
/dev/sda4            9314       11978    21406612+   5  Extended
/dev/sda5   *        9314       11800    19976796   83  Linux
/dev/sda6           11801       11978     1429753+  82  Linux swap / Solaris

```

And here is the menu.lst:

```


title		Ubuntu 8.04
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f ro single
initrd		/boot/initrd.img-2.6.24-19-generic


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
title		Dell Utility Partition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1




```

---

### Post by hyper_ch on 2008-06-17
half of the grub menu.lst is missing there.

---

### Post by melrom on 2008-06-17
> **hyper_ch said:**
> half of the grub menu.lst is missing there.

only what's commented out. if you want to see the whole thing anyway:

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
# kopt=root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f ro single
initrd		/boot/initrd.img-2.6.24-19-generic


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
title		Dell Utility Partition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1



```

---

### Post by ukripper on 2008-06-17
Can you also post output of the folowing commands
```
 df -h /boot
```
and```
 blkid
```

---

### Post by hyper_ch on 2008-06-17
there are a few things mixed up...

you don't ahve a seperate boot partition and the root partition is this:
```

/dev/sda5   *        9314       11800    19976796   83  Linux

```
right?

As grub start with "0" and not with "1" you need to alter the entry to:
```

title		Ubuntu 8.04
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

I'm not sure if non existing labelled partitions exist... maybe you'll have to alter it to:
```

title		Ubuntu 8.04
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

And if that is not working either, then try to replace
```

root=UUID=f2d79187-0bd4-4e4f-b8db-34f9f427685f

```
with
```

root=/dev/sda5

```

---

### Post by justleen on 2008-06-17
agree with Hyper_c herre.. try to get it working with root-/dev/sdaX.

if that works, you can change the device with the correct UUID.. 

that way it is slighty more comprehendible

and do a "ls vmlinuz* /boot/" to double check that kernel name, i'd say

---

### Post by melrom on 2008-06-17
Out of blkid:

```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-031F" TYPE="vfat"
/dev/sda2: UUID="AC58A06658A0314E" TYPE="ntfs"
/dev/sda5: UUID="f2d79187-0bd4-4e4f-b8db-34f9f427685f" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: UUID="0593218c-9f92-4f9f-9811-2add886b0e7c" TYPE="swap"
/dev/loop0: TYPE="squashfs"

```

So, where everything is 1, 2, 5, and 6 with swap. Grub would see this as 1=0, 2=1, 5=4, and 6=5??

---

### Post by ukripper on 2008-06-17
To be certain which uuid you are currently using, can you post output from my previous post.

and for ```
df -h /boot 
```

---

### Post by melrom on 2008-06-17
> **ukripper said:**
> To be certain which uuid you are currently using, can you post output from my previous post.

and for ```
df -h /boot 
```

Er, I can, but I'm not sure if this works correctly on the live CD.

This is the output from df -h /media/disk/boot:

```

Filesystem     Size     Used   Avail   Use%  Mounted on
/dev/sda5      19G      6.8G   12G     37%   /media/disk

```

---

### Post by ukripper on 2008-06-17
> **melrom said:**
> Er, I can, but I'm not sure if this works correctly on the live CD.

This is the output from df -h /media/disk/boot:

```

Filesystem     Size     Used   Avail   Use%  Mounted on
/dev/sda5      19G      6.8G   12G     37%   /media/disk

```

Now we are certain the UUID you need to use is > f2d79187-0bd4-4e4f-b8db-34f9f427685f as hyper_ch mentioned you can follow that.

---

### Post by melrom on 2008-06-17
Okay, changing from (hd0, 5) to (hd0, 4) did not help. Changing it to dev/sda5 did not help either.

---

### Post by ukripper on 2008-06-17
> **melrom said:**
> Okay, changing from (hd0, 5) to (hd0, 4) did not help. Changing it to dev/sda5 did not help either.

try changing it to hd(0, 3)

---

### Post by melrom on 2008-06-17
Alright, here's my plan of action:

-make a 5gig partition
-install ubuntu [again] on that partition
-this will give me a working grub. it will also tell me which things (hd0, n) goes to which
-uninstall the new partition and fix the old menu.lst

---

### Post by ukripper on 2008-06-17
> **melrom said:**
> Alright, here's my plan of action:

-make a 2gig partition
-install ubuntu [again] on that partition
-this will give me a working grub. it will also tell me which things (hd0, n) goes to which
-uninstall the new partition and fix the old menu.lst

have you tried hd(0,3) yet?

if you have and it still is not working I would suggest rather going through that procedure you mentioned use supergrubdisk which will fix much quicker.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by melrom on 2008-06-17
> **ukripper said:**
> have you tried hd(0,3) yet?

yep. =\

---

### Post by ukripper on 2008-06-17
> **melrom said:**
> yep. =\

then it is best you try supergrub disk which will fix this easily for you.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by justleen on 2008-06-17
i'd try supergrub first - much quicker.. 

or boot into a livecd again, go into the grub-prompt and try to find out where grub is installed...

grub>  find /boot/grub/stage1

---

### Post by melrom on 2008-06-17
i'm at work though. i don't have blank cds. so i can't burn a super grub disk. =\ basically, i should be patient. this thread is psuedo-solved at the same time that it's not at all, so i might leave it open for now...

---

### Post by bumanie on 2008-06-17
Preferably, the boot partition should be windows.

---

### Post by melrom on 2008-06-17
> **bumanie said:**
> Preferably, the boot partition should be windows.

What!? Since when? Wouldn't that bypass grub?

---

### Post by bumanie on 2008-06-17
I stand to be corrected but what I have come across most often is that on a dual boot, windows is the * boot partition and grub is installed in windows mbr and points to the partition where ubuntu is. I had grub problems early on in my time with ubuntu and that is what I was told, by someone whom I know is very well-versed in linux. He got me to change the * boot form ubuntu to windows. I'm no expert, but that is what I have been told by someone with much more knowledge than myself. I know my fdisk -l reflects (different computer than before) as do most fdisk -l posts to the forum. As said, I stand to be corrected.
By the way your /boot/grub/menu.lst should have the dell (?rescue) partition as (hd0,0), windows as (hd0,1) and ubuntu as (hd0,4) according to the output of fdisk -l.

---

### Post by MasterSander on 2008-06-17
Why would you change it to windows, what is different when you do that?

---

### Post by melrom on 2008-06-17
> **bumanie said:**
> I stand to be corrected but what I have come across most often is that on a dual boot, windows is the * boot partition and grub is installed in windows mbr and points to the partition where ubuntu is. I had grub problems early on in my time with ubuntu and that is what I was told, by someone whom I know is very well-versed in linux. He got me to change the * boot form ubuntu to windows. I'm no expert, but that is what I have been told by someone with much more knowledge than myself. I know my fdisk -l reflects (different computer than before) as do most fdisk -l posts to the forum. As said, I stand to be corrected.
By the way your /boot/grub/menu.lst should have the dell (?rescue) partition as (hd0,0), windows as (hd0,1) and ubuntu as (hd0,4) according to the output of fdisk -l.

Interesting. Yeah, that was the ultimate menu.lst I tried. It still wasn't working. I'm not sure what I did. lol. 

But that's interesting about using Windows as the boot. I've never done that before. I'll look into it. Thanks for the suggestion.

---

### Post by meierfra. on 2008-06-17
1) Repartitioning does not change UUID's. So no need to change "root=UUID=  ". Also a wrong UUID cannot cause a Grub Error, since Grub does not even look at  "root=UUID=..." (that is a parameter for the kernel)

2)  Grub does not use the "boot" flag so the position of the boot flag is irrelevant. 

3) Since you only have one hard drive and Ubuntu is on "/dev/sda5",  the "root (hd?,?)"  lines for Ubuntu, Ubuntu recovery and memtest need to be "root (hd0,4)".  ( the second number in (hd?,?)  is ALWAYS one lower than the number in /dev/sda?"
Grub starts counting at zero, so (hd0,4) means fifth partition on the first hard drive.)

[B] To avoid problems after the  next kernel update, you need change the "groot" line to

"# groot (hd0,4)"

4)  You need to reinstall grub. You can use Supergrub for that, or you can boot from Ubuntu LiveCD, open a terminal and type

```
sudo grub
```
and at the "grub>" prompt:

```
root (hd0,4)
setup (hd0)
quit
```
[/B]

5) bumanie is right, you need "root (hd0,0)"  for  dell  and "root (hd0,1)" for Windows.

---

