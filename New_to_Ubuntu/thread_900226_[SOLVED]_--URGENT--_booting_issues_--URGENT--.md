---
title: "[SOLVED] --URGENT-- booting issues --URGENT--"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by GrimmReaperVI on 2008-08-25
hi guys! nice to be in the ubuntu community! but i have a MAJOR  problem!!
some days ago i installed ubuntu. i loved it, but since most of my family uses xp i dual booted it..i think...

whatever, when my computer started up i got 5 options on which OS to boot.
i didn't like that ^ ^ so i fixed some options in boot/grub/menu.lst so that windows would boot automaticaly. And it worked...once. The next day i find a grub error 17 during phase 1.5 or something. :lolflag:

now to the point. HEEEEELP!!!!!!!!!! :lolflag:

i can't boot ubuntu OR windows and right now i'm using the livecd to write this post.how do i get my system back to normal??

---

### Post by Crafty Kisses on 2008-08-25
You may want to try SuperGRUB. 

Here's the link > [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Elfy on 2008-08-25
Open a terminal and run this command - paste it here please

```
sudo fdisk -l
```

---

### Post by wannadumpwindows on 2008-08-25
This thread should fix you right up:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by GrimmReaperVI on 2008-08-25
codename i already tried that with my usb and it failed :(
(still showed the same error)

pixie what will that command do?

---

### Post by Elfy on 2008-08-25
Give a list of partitions - so we can mount the linux one and then we can see what your menu list looks like.

---

### Post by GrimmReaperVI on 2008-08-25
OH JOY! SWEET SWEET JOY!! I can acces my drives again.

right, now can someone help me do this right:
automaticaly boot windows unless i press the boot menu button and select otherwise

and can someone tell me why you have coffee cups under your names?


MANY MANY thanks to wannadumpwindows

---

### Post by Crafty Kisses on 2008-08-25
For the coffee cup answer, that would be because some people post a lot and some are moderators.

---

### Post by Dougie187 on 2008-08-25
What does your menu.lst look like?

And the coffee cups are because they have a lot of posts.

---

### Post by GrimmReaperVI on 2008-08-25
ok...why not coke?

---

### Post by Elfy on 2008-08-25
geeks drink coffee :D

> What's the deal with coffee cups/beans and the funny titles? 

Beans are posts. The post/bean count can be turned off by the user if so desired. 

There tends to be a close connection between geeks and coffee, so that's where the theme came from. Yes, we know not everyone likes coffee, but it's just a silly thing.from here [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)


For us to see the menu list - open aterminal in buntu and run this

```
cat /boot/grub/menu.lst
```

You can edit it so that the position of the windows doesn't move and will always be at the top.

---

### Post by GrimmReaperVI on 2008-08-25
hmmm more trouble

my ubuntu partition doesn't seem to work

i can only access windows :lolflag:

not even recovery mode!!

---

### Post by Elfy on 2008-08-25
Go back to the beginning then, boot the livecd post the result of the fdisk -l and we can check it out easily enough. If menu list is wrong for the normal boot it will be wrong for recovery as well, it's pointing at the wrong partition - that is what error 17 is.

---

### Post by mc4100 on 2008-08-25
> **GrimmReaperVI said:**
> ok...why not coke?
Because Coke isn't, as far as I know, made of coffee beans. ;)

---

### Post by GrimmReaperVI on 2008-08-25
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       38913   178361662+   f  W95 Ext'd (LBA)
/dev/sda5           16709       23083    51207156    7  HPFS/NTFS
/dev/sda6           35267       35874     4883728+  82  Linux swap / Solaris
/dev/sda7           35875       38913    24410736   83  Linux

Disk /dev/sdb: 2041 MB, 2041577472 bytes
61 heads, 60 sectors/track, 1089 cylinders
Units = cylinders of 3660 * 512 = 1873920 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1090     1993608    6  FAT16

```

enlighten me!

---

### Post by Elfy on 2008-08-25
Ok I'll try - open a terminal in the livecd and do these

```
sudo mkdir /mnt/recovery
sudo mount -t ext3 /dev/sda[COLOR="Red"]7[/COLOR] /mnt/recovery
```

That should mount the partition temporarily, now run

```
ls /mnt/recovery/boot/grub/menu*
cat /mnt/recovery/boot/grub/menu.lst
```

should give us the menu list - paste it here please, if there are any errors please post that and the command that failed.

So you know what we're doing - as I can see you like to know
we are making a folder in which to mount the linux partition, then the mount command does so. Then I've asked for a list of the menu files in the boot/grub folder, finally it will print the current menu list in the terminal.

---

### Post by GrimmReaperVI on 2008-08-25
the first 2 codes aren't working

```
ubuntu@ubuntu:~$ sudo mkdir/mnt/recovery
sudo: mkdir/mnt/recovery: command not found
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda /mnt/recovery
mount: mount point /mnt/recovery does not exist
ubuntu@ubuntu:~$ 


```

but if you tell me what file you're looking for i can fetch it for you.
I HAVE access to my partitioned drives


--edit-- nvm i don't have the recovery folder

--further edit-- i guess that's why the commands aren't working

---

### Post by Elfy on 2008-08-25
Sorry I hadn't got the command right - there should be a gap between mkdir and /mnt/recovery - changed it now

```
sudo mkdir /mnt/recovery
sudo mount -t ext3 /dev/sda7 /mnt/recovery
```

---

### Post by GrimmReaperVI on 2008-08-25
nothing happens when i type the 2nd one :(

```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda7/mnt/recovery

```

where are the spaces XD:lolflag:


```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda7 /mnt/recovery
mount: /dev/sda7 already mounted or /mnt/recovery busy
mount: according to mtab, /dev/sda7 is mounted on /media/disk

```

does thi smean i got it right?
cause i typed it once and nothing happened

---

### Post by Elfy on 2008-08-25
sudo mkdir /mnt/recovery
sudo mount -t ext3 /dev/sda7 /mnt/recovery

between mkdir and /mnt in first
and between /dev/sda7 and /mnt/recovery in second

---

### Post by Elfy on 2008-08-25
Oh ok it's already mounted on /media/disk we can go from there then 

```
ls /media/disk/boot/grub/menu*
cat /media/disk/boot/grub/menu.lst
```

---

### Post by GrimmReaperVI on 2008-08-25
```
ubuntu@ubuntu:~$ ls /media/disk/boot/grub/menu*
/media/disk/boot/grub/menu.lst   /media/disk/boot/grub/menu.lst~~
/media/disk/boot/grub/menu.lst~
ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=75ae15c6-0291-417e-aa9c-91ef99e1fb1b ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=75ae15c6-0291-417e-aa9c-91ef99e1fb1b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=75ae15c6-0291-417e-aa9c-91ef99e1fb1b ro single
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

err...right...what are we looking for again?

---

### Post by Elfy on 2008-08-25
Ok - we can edit that - we'll deal with getting ubuntu to boot first, run this command to open the file for editing

```
gksudo gedit /media/disk/boot/grub/menu.lst
```

You need to find the lines which look like
> root		([COLOR="Red"]hd0,5)[/COLOR]

change to (hd0,6)

There is also a line
> # groot=(hd0,5)change that to (hd0,6) as well

Save and close, reboot and remove the cd. Check that it boots ok and then we can deal with getting windows at the top and default for you.

---

### Post by GrimmReaperVI on 2008-08-25
Ubuntu boots AOK!
What's next,boss?

---

### Post by Elfy on 2008-08-25
Cool - that's good. Now from you're first post I see you want, or at least need, windows to be first and default if that is so, we can do that now.

---

### Post by GrimmReaperVI on 2008-08-25
lead the way, oh mighty saviour of my computer

---

### Post by totalnub on 2008-08-25
To make windows boot by default, change the default option in menu.lst from
```
default 0
```
to
```
default 4
```

This will make your windows boot selection be auto-highlighted.
You can also adjust the timeout for grub (default is 10 sec).

---

### Post by GrimmReaperVI on 2008-08-25
can i set 10 to 0?

---

### Post by Elfy on 2008-08-25
> can i set 10 to 0? you can and would need to press esc at the right time to access the menu, I've set it to 1 in the past.

If you do that then when grub updates with new kernels then it will need to be changed each time, you can move the windows stanza so it is above the automagic line and will always be first.

To do that, open the file for editing as before, cut all of this from the end of the file

> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

You need to paste it between the lines which read
> # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

Once you've done that change the default to

> default		1

save and close, if you want to make sure  paste the changed file here and we can give it a once over.

Then when you reboot - windows should be at the top and selected by default, so anyone wanting to run win has to do nothing.

---

### Post by totalnub on 2008-08-25
You can change it to 0, but choosing that will cause it to be almost impossible to select an OS. Try 3 or 4 sec :)

---

### Post by GrimmReaperVI on 2008-08-25
?you mean change it now?

adn can't i change the OS before my comp actually boots up?

(giant hp figure)
 and press F9 for boot menu?

---

### Post by totalnub on 2008-08-25
That F9 for boot menu is what lets you select which media to use to boot (i.e. HDD, CD, network, USB, floppy, etc.)

---

### Post by GrimmReaperVI on 2008-08-25
weird. mine just brings up all the OSs


```

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST
```

will this work?

---

