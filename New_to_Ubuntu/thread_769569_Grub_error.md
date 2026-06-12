---
title: "Grub error"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by jimjesus on 2008-04-26
So I was having some issues with my previous install of ubuntu(7.10) so I decided I would download 8.04 and install it. I downloaded the iso image using my windows xp(I was set up to dual boot ubuntu and xp) and then booted from it. I manually selected my previous linux partition to install 8.10 on and finished my installation. I rebooted and made it into grub, but when I selected an os, it gave an error of something along the lines of "error, selected partition could not be mounted". Does anyone know how I can get ubuntu and windows xp to work without any data loss?

---

### Post by TeoBigusGeekus on 2008-04-26
Can you boot into Ubuntu? If not, use the live cd.
Once in, post us the results of the command
```
sudo fdisk -l
```
that's -L.
Then posts us the contents of your menu.lst fils (.LST)
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by jimjesus on 2008-04-26
I am currently using my live cd, I can't get into ubuntu or xp.

The output from the first command was 
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x472c092d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      467302   235520176+   7  HPFS/NTFS
/dev/sda2          467303      969017   252864360    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2   *           6        7294    58548892+   7  HPFS/NTFS

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006f32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        8970    72051493+   7  HPFS/NTFS
/dev/sdc2   *        8971       10319    10835842+  83  Linux
/dev/sdc3           10320       10455     1092420   82  Linux swap / Solaris
/dev/sdc4           10456       18448    64203160+   7  HPFS/NTFS
```
And the other command brings up an empty file so I have nothing to paste here.

---

### Post by teryowen on 2008-04-26
As well as TeoBigusGeekus asked please post the contents of the /boot/grub/menu.lst file

do this in terminal
```
cat /boot/grub/menu.lst
```
or
```
gedit /boot/grub/menu.lst
```

---

### Post by TeoBigusGeekus on 2008-04-26
Are you sure you wrote menu.lst (that's LST) and not menu.1st (that's 1ST)?

---

### Post by jimjesus on 2008-04-26
I copy/pasted the command directly from your post teo. And when I try cat instead of gedit, it says no such file exists. It would seem grub isn't on this computer, but when I try and boot, I get the grub menu. I would like to add that I get error 17(something like selected partition could not be mounted) when I try and boot ubuntu and error 13(incompatible format or something like that) when I try and boot into windows.

---

### Post by jimjesus on 2008-04-26
Ok I just manually navigated to the menu.lst file from the file browser and found it. It reads 

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
# kopt=root=UUID=c8e35813-418e-4b87-8444-821d5a8be3f7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c8e35813-418e-4b87-8444-821d5a8be3f7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c8e35813-418e-4b87-8444-821d5a8be3f7 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Home Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by teryowen on 2008-04-26
Are you using a live cd?

if so instead do this
```

cat /media/sdc2/boot/grub/menu.lst

```

EDIT: never mind seems you got to it before i did.

one more thing
```

cat /media/sdc2/boot/grub/device.map
```

this will show us how the drives are mapped.

---

### Post by TeoBigusGeekus on 2008-04-26
Very strange problem...
Try to reinstall grub followind the directions from this page
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

EDIT: No need to do it since you actually have a menu.lst file.

---

### Post by jimjesus on 2008-04-26
The contents of device.map are as follows:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

I do have multiple partitions on each of those hardrives, I don't know if they are supposed to show up in that list, but as you can see, they aren't.

---

### Post by teryowen on 2008-04-26
Alright this does seem quite odd and reinstalling grub will hopefully work run these commands in terminal:

```

sudo grub
root (hd2,1)
setup (hd2)
quit

```

---

### Post by dsdreamer on 2008-04-26
I just wanted to mention that under the very similar circumstances, I got the exact same grub misconfiguration.  That includes the strange gratuitous swapping of hd0 and hd1 for the Windows Boot:
map		(hd0) (hd1)
map		(hd1) (hd0)

So to be clear: when upgrading from an old installation of 7.10 to 8.04 as a new installation from the Live CD, and reusing the old 7.10 partitions as the target for the new 8.04 install, grub seems to mix up all the disk mappings and use the wrong root devices for each operating system.  I could only boot from the Live CD, and go in and fix everything by hand.  I think this will be quite a common complaint from people who upgraded in the same manner. When I can get to my Ubuntu machine, I can post the configuration files before and after I fixed it.

--dsdreamer.

---

### Post by jimjesus on 2008-04-26
I did as terryowen said and it was unsuccessful. I was considering installing an older version of ubuntu that I have successfully installed from live cd before(6.10) and see if I can just upgrade all the way up to 8.04 instead of just using the 8.04 live cd and writing over my old linux partition. Would this work?
I will be on a separate computer while doing this so I will still be on the forums.

---

### Post by jimjesus on 2008-04-26
Well I successfully installed ubuntu 6.10 and am using it now. I think I will just upgrade all the way up without using a live cd. I do have one other question though. How would I remove all my previous ubuntu installs from the grub list after I'm fully upgraded. I don't want to have to scroll down that huge list to get to xp. I just want it to show 8.04 and win xp.

---

### Post by teryowen on 2008-04-26
It will do it automatically but if you would like you could edit your grub menu entries by editing the menu file, to edit it do this in terminal

```

gksudo gedit /boot/grub/menu.lst

```

in the file at the bottom you will see all the entries and you can edit them, as well if you want to make XP or something else the default boot option you can edit that somewhere earlier in the same file where it says

```
default 0
```
change the number to your choice
0 being 1
1 being 2 and so on.

---

### Post by dsdreamer on 2008-04-26
> **jimjesus said:**
> I did as terryowen said and it was unsuccessful. I was considering installing an older version of ubuntu that I have successfully installed from live cd before(6.10) and see if I can just upgrade all the way up to 8.04 instead of just using the 8.04 live cd and writing over my old linux partition. Would this work?
I will be on a separate computer while doing this so I will still be on the forums.

Before you get into that (or is it too late?) let me tell you what worked for me.  I booted from the live CD, and was able to ```
sudo gedit /media/sdc2/boot/grub/menu.lst
```  from a command window and make a few changes to the root statements to point the right places and then do sudo update-grub and thereby apply the fixes.  If the path to your menu.lst is different you can find it by browsing to it in the file browser, right clicking on it and selecting the properties to read the location in the dialog box.

In order to boot into Windows I had to change the end of the grub/menu.lst file to look like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Previously it had looked exactly like yours and wouldn't boot.

Similarly, I had to change the root statements for the Ubuntu boot line items.

My corrected version has:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=xxxxxxxx-something-something-something ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```
Unfortunately, I can't find what mis-configured version looks like, but I think it had hd0 (or was it hd1?) where it should have had hd2.

Anyway, I can say that after changing just the root lines of this file and applying sudo update-grub, I was able to boot to both installed operating systems, which was an improvement from none!

--dsdreamer

---

### Post by jimjesus on 2008-04-26
Thanks for the help everyone. I am in the process of upgrading but I think it should all work.

---

### Post by jimjesus on 2008-04-26
Quick noob question here. How do I mark thread as solved?

---

### Post by teryowen on 2008-04-26
up top in red font "Thread tools" click it and in the menu click mark as solved.

---

### Post by jimjesus on 2008-04-27
That doesn't show up in thread tools for some reason.

---

