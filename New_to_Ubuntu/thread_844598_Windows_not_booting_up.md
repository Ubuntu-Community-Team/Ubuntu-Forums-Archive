---
title: "Windows not booting up"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by appi2012 on 2008-06-29
I installed ubuntu a 5 months ago, and ever since installing it, I have not been able to boot windows. However, I haven't really needed windows for any specific task. But I looked at all the games I had that were sitting just collecting dust. I've decided it is time to do something about the windows problem. I searched the web, and from what I've gathered, I know it is something to do with grub. All my windows files are there so that is not the problem. I was hoping someone could tell me how to fix this without needing to reinstall either ubuntu or windows.

As of now my grub looks like this: (* next to things that work)
Ubuntu(linux .....)*
Ubuntu Recovery(linux ....)*
Ubuntu(linux .....-1)*
Ubuntu Recovery(linux ....-1)*
memtest [haven't tested]

Other OSes
MS Windows (Sys Recovery)*
Windows NT/xp/.. (WINDOWS XP)

Help would be really appreciated :?

---

### Post by schwascore on 2008-06-29
What happens when you select Windows from your GRUB menu? Please post any errors or messages that are displayed. The more information you post, the more we can help.

---

### Post by tzulberti on 2008-06-29
Could you tell the mesage that appears when you try to boot windows? Also, could you post you /boot/grub/menu.lst file?

---

### Post by ercferret18 on 2008-06-29
yeah, what happens when you try to boot windows?

---

### Post by appi2012 on 2008-06-29
It just says something like "chainloading windows" and hangs.
this is my menu.lst
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
color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,2)/boot/grub/splashimages/AquaDreams4bydeadpxl.xpm.gz

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
# kopt=root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro

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
# defoptions=quiet splash vga=792

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
# howmany=2

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
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
title		Microsoft Windows XP Home Edition
unhide		(hd0,0)
hide		(hd0,1)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
unhide		(hd0,1)
hide		(hd0,0)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by appi2012 on 2008-06-29
I double checked, and all it says when I boot xp is "Starting up..." and then hangs

---

### Post by ad_267 on 2008-06-29
Can you also post the output of "sudo fdisk -l"

---

### Post by logos34 on 2008-06-29
So sda1 is a system recovery partition?

Post output of:
[B]
sudo fdisk -l[/B]

Try another windows entry.  

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

gksudo gedit /boot/grub/menu.lst

Add this to bottom (basically just take out 'hide/unhide' lines):

>  title        Windows XP (on /dev/sda2)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


Or try just '(hd0,0)'

---

### Post by appi2012 on 2008-06-29
sudo f-disk -l: 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15656   125756788+   7  HPFS/NTFS
/dev/sda2           18463       19457     7990920   1c  Hidden W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           15657       18340    21559230   83  Linux
/dev/sda4           18341       18462      979965    5  Extended
/dev/sda5           18341       18462      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by appi2012 on 2008-06-29
Perhaps it is because of the "Partition 2 does not end on cylinder boundary"?

I'm pretty sure the windows entry was like that before I added the hide/unhide things (another post said to do that) but I will try again.
Thanks for the suggestion, though.

---

### Post by logos34 on 2008-06-29
> **appi2012 said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15656   125756788+   7  HPFS/NTFS


This is the bootable windows partition, so this entry should work:

>  			 				 title        Windows XP (on /dev/sda1)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

You could try using Super Grub Disk (>fixboot).  Or if you can get your hands on an xp install cd, boot into the recovery console and run fixboot AND error checking w/ repair option:

**chkdsk /r**

---

### Post by appi2012 on 2008-06-29
I think the reason it isn't working is because the windows boot manager was stored on sda1 (hd0,0), and it is set to by default boot (hd0,1), so that's why the entry in grub to start System recovery points to sda1, but fdisk shows the recovery FAT partition as sda2. Do you think that is a reasonable guess? I'm not very knowledgeable in this topic, but that's what I'm guessing the problem is.

---

### Post by jumponskis on 2008-06-29
I'm having that same problem starting about an hour and a half ago.  I also get the black screen that says starting up and it never does start up.  Please help thats 110GB of data I CANNOT lose.  Ubuntu is working though... why does it always have to be microsofts fualt.  Just once why can't they do something right....

---

### Post by logos34 on 2008-06-29
> **appi2012 said:**
> I think the reason it isn't working is because the windows boot manager was stored on sda1 (hd0,0), and it is set to by default boot (hd0,1), so that's why the entry in grub to start System recovery points to sda1, but fdisk shows the recovery FAT partition as sda2. 

Either '(hd0,0)' or '(hd0,1)' should work...if the boot files (i.e. ntldr, ntdetect.com, boot.ini, etc.) are located instead on sda2, the recovery partition, then 'root (hd0,1)' should work--but didn't you already try that?

Mount both partitions in linux and look inside--do you see those files in sda1 (c:\) or sda2? 

The fact that it just hangs after grub chainloads it, without any error message, is not particularly helpful.  But my hunch is that since you have never been able to boot into windows after installing ubuntu, and it appears you shrank windows to make room for linux install, there may be bad blocks or other errors (common after resizing), something that chkdsk /r would likely fix.   (Actually windows will usually detect something amiss and automatically trigger a disk scan the first time you reboot into windows after making changes to the partition.  This usually clears up any problems.)

That's my guess, based on the info provided, as it could be any number of things.

---

### Post by logos34 on 2008-06-29
> **jumponskis said:**
> I also get the black screen that says starting up and it never does start up.  Please help thats 110GB of data I CANNOT lose.  Ubuntu is working though... why does it always have to be microsofts fualt.  Just once why can't they do something right....

Have you tried to mount windows in linux and access your files?  If you can do that, your data at least is safe.

---

### Post by jumponskis on 2008-06-30
> **logos34 said:**
> Have you tried to mount windows in linux and access your files?  If you can do that, your data at least is safe.

yes I tried that first :( I used to be able to see the volume HP_*sumthing* but i dont even see that anymore

---

### Post by jumponskis on 2008-06-30
> **logos34 said:**
> my hunch is that since you have never been able to boot into windows after installing ubuntu, and it appears you shrank windows to make room for linux install, there may be bad blocks or other errors (common after resizing), something that chkdsk /r would likely fix.
That's my guess, based on the info provided, as it could be any number of things.

it is chkdsk /f actually. /r will not auto fix if it detects the errors. but before i *was* able to boot to windows


EDIT: That's it?! your just going to tell me my data is not safe then leave me hangin'?!!  I'm in a serious predicament here!

---

### Post by logos34 on 2008-06-30
> **jumponskis said:**
> it is chkdsk /f actually. /r will not auto fix if it detects the errors. but before i *was* able to boot to windows

EDIT: That's it?! your just going to tell me my data is not safe then leave me hangin'?!!  I'm in a serious predicament here!


sorry for late response.

I thought '/r' meant 'repair/recover'.  

> **CHKDSK**

**chkdsk drive /p /r**
  The **chkdsk** command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.

 You can use the following options:   /p : Does an exhaustive check of the drive and corrects any errors.
   /r : Locates bad sectors and recovers readable information. 

**Note** If you specify the **/r** option, the **/p** option is implied. When you specify  the **chkdsk** command without arguments, the command checks the current drive with no options in effect. 


> 
yes I tried that first :sad: I used to be able to see the volume HP_*sumthing* but i dont even see that anymoretry manually mounting windows.  Post your fdisk

sudo fdisk -l

---

### Post by jumponskis on 2008-06-30
I cannot manually mount because I cannot see the windows partition in ubuntu anymore!

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         967     7310488+   c  W95 FAT32 (LBA)
/dev/sda2   *         968       18428   132005160    7  HPFS/NTFS
/dev/sda3           18429       20673    16972200    5  Extended
/dev/sda5           18429       20573    16216168+  83  Linux
/dev/sda6           20574       20673      755968+  82  Linux swap / Solaris

```

this
```
/dev/sda1               1         967     7310488+   c  W95 FAT32 (LBA)
```
is just the recovery partition which I was told not to touch or bad s**t would happen
and /f is the same as /p + /r

---

### Post by logos34 on 2008-06-30
to manually mount, try this:

sudo mkdir /media/windows

sudo mount -t ntfs /dev/sda2 /media/windows

---

### Post by jumponskis on 2008-06-30
```
thomas@thomas-desktop:~$ sudo mkdir /media/windows
[sudo] password for thomas: 
thomas@thomas-desktop:~$ sudo mount -t ntfs /dev/sda2 /media/windows
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
thomas@thomas-desktop:~$ 

```

this is what it says.

EDIT: come-on don't give up yet man I need you

---

### Post by logos34 on 2008-06-30
> NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.It might simply be an error in the partition table.  

I would suggest [TestDisk.  ]("http://www.cgsecurity.org/wiki/TestDisk")

sudo apt-get install testdisk

(it's in the universe repository, so make sure that's enabled in synaptic)

sudo testdisk

Read the documentation and [this page]("http://www.users.bigpond.net.au/hermanzone/p21.html"). be sure you know what you're doing before writing any changes to disk.

That's about your only option if you can't boot windows or mount it in linux (other than running chkdsk from the windows CD recovery console, that is).

---

### Post by jumponskis on 2008-06-30
and how do i run check disk from recovery console if I cant even get onto windows..

---

### Post by logos34 on 2008-06-30
"...from the windows **CD** recovery console..."

But then maybe you don't have the install cd

---

### Post by jumponskis on 2008-06-30
oh duh. well it is 11:30 here give me a break.  will that not mess up my ubuntu install?
and I do have the install CD thank you very much...:-s

---

### Post by jumponskis on 2008-06-30
i've been given his error message after running the anlalyze function in testdisk ```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63

Warning: the current number of heads per cylinder is 255
but the correct value may be 240.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.





```

---

### Post by logos34 on 2008-06-30
I get that message too.  But you can leave it, 255 is probably right (mine is at least).  Be sure to read Herman's page at the very least.

Oh, so you do have an install cd (usually the recovery partition is meant as a substitute so the cheapsake manufacturers can save 50 cents supplying you with the disc).  So did you try to run chkdsk from the recovery console? (sorry, it's late here too, getting ready to nod off)

---

### Post by Methuselah on 2008-06-30
Do you have windows installation/boot disks?
I think there is an option to run chkdsk from there.

---

### Post by jumponskis on 2008-06-30
i have an hp and you have to make your own back up disk for recovery.  problem is they only restore to factory defualts.  I will try the xp cd I hope it works.  Im really affraid that if I turn my computer off I will lose all hope of recovering windows.  I'm definitely hitting the thanks button on this one, if for nothing else but the patience and effort you have :lolflag: thank you.

---

### Post by smo0th on 2008-06-30
> **jumponskis said:**
> ```
thomas@thomas-desktop:~$ sudo mkdir /media/windows
[sudo] password for thomas: 
thomas@thomas-desktop:~$ sudo mount -t ntfs /dev/sda2 /media/windows
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
thomas@thomas-desktop:~$ 

```

this is what it says.

EDIT: come-on don't give up yet man I need you

HOLD ON!!!

```
sudo mount -t ntfs /dev/sda2 /media/windows
```

is evil code, try ```
sudo mount -t ntfs-3g /dev/sda2 /media/windows -o force
``` instead and let me know the results. Whenever you are mounting NTFS partitions, use the ntfs-3g directive, if you want to mount FAT partitions use the vfat directive.

---

### Post by smo0th on 2008-06-30
> **appi2012 said:**
> It just says something like "chainloading windows" and hangs.
this is my menu.lst
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
color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,2)/boot/grub/splashimages/AquaDreams4bydeadpxl.xpm.gz

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
# kopt=root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro

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
# defoptions=quiet splash vga=792

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
# howmany=2

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
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
title		Microsoft Windows XP Home Edition
unhide		(hd0,0)
hide		(hd0,1)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
unhide		(hd0,1)
hide		(hd0,0)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

try editing your menu.lst file in the last lines, replace your code for:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

delete the "Windows NT/2000/XP" partition info, since you only have one bootable partition and GRUB may be getting confused.

if the above does not work pls post back ;)

---

### Post by appi2012 on 2008-06-30
the boot.ini and ntldr are in my C:/ directory. Do you think making a backup of that file, and then deleting the entry for the recovery should work (in boot.ini) I would then also delete the grub entry for recovery too. Do you think that would work, or would it mess up my windows? Anyway, here's my boot.ini stored on sda1:
```
[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```

---

### Post by jumponskis on 2008-06-30
OK.  Yesterday night testdisk couldn't even see the NTFS partition so I ran the geometry option and then did some other stuff and was given the option to rebuild the boot sector and now it sees it but this is what it says now 
```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (FAT) != 255 (HD)
 1 P FAT32 LBA                0   1  1   910  29 63   14620977 [HP_RECOVERY]

Bad sector count.
 2 * HPFS - NTFS            910  30  1 17343 254 63  264010320

Bad relative sector.
 3 E extended             17344   0  1 19456 239 63   33944400
 5 L Linux                17344   1  1 19362 209 63   32432337
   X extended             19362 210  1 19456 239 63    1512000
 6 L Linux Swap           19362 211  1 19456 239 63    1511937



*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[COLOR="Lime"][[/COLOR]Proceed [COLOR="Lime"]][/COLOR]  [ Backup ]
                            Try to locate partition


```

what should I do now?

---

### Post by logos34 on 2008-06-30
> **jumponskis said:**
> OK.  Yesterday night testdisk couldn't even see the NTFS partition so I ran the geometry option and then did some other stuff and was given the option to rebuild the boot sector and now it sees it but this is what it says now 
```


```what should I do now?

maybe it is 240

> 
[http://www.cgsecurity.org/wiki/Menu_Geometry](http://www.cgsecurity.org/wiki/Menu_Geometry)
** Some hints about the geometry **

 **  How to find the correct number of heads? **

 If the HD geometry mismatches the geometry used when creating the partition table, warning messages such as: Bad sector count, Bad relative sector or Bad ending head are displayed when [Analyse]("http://www.cgsecurity.org/wiki/Menu_Analyse")  is selected from the main menu.  If you see such errors, you may need to use the Geometry menu to change the logical number of heads. Try 255, 16, 32, 64, 128 and 240 heads until TestDisk finds all your partitions. 255 and 240 are the most common head values. If you installed Linux as the only OS on your hard drive, it tends to default to only 16 heads. 
 **  How to find the correct number of sectors? **

 Usually the number of sectors per head is always 63, but on some USB devices, the value 32 can be found. 
Back to [Running the TestDisk Program]("http://www.cgsecurity.org/wiki/Running_TestDisk")
Read the documentation.

> I will try the xp cd I hope it works.  

yep, do that as soon as you can, because running chkdsk might solve your problem

---

### Post by logos34 on 2008-06-30
> **smo0th said:**
> try editing your menu.lst file in the last lines, replace your code for...

if the above does not work pls post back ;)

been there.  done that.  You need to read the whole thread.

> HOLD ON!!!

 	Code:
 	sudo mount -t ntfs /dev/sda2 /media/windows 
is evil code, try  	Code:
 	sudo mount -t ntfs-3g /dev/sda2 /media/windows -o force 
 instead and let me know the results. Whenever you are mounting NTFS partitions, use the ntfs-3g directive, if you want to mount FAT partitions use the vfat directive.


Huh?  evil?  don't understand.  ntfs should work fine...ntfs-3g is just the third-party driver that adds write support

---

### Post by logos34 on 2008-06-30
> **appi2012 said:**
> the boot.ini and ntldr are in my C:/ directory. Do you think making a backup of that file, and then deleting the entry for the recovery should work (in boot.ini) I would then also delete the grub entry for recovery too. Do you think that would work, or would it mess up my windows? Anyway, here's my boot.ini stored on sda1:
```
[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

```


looks ok to me.  "partition(1)" is correct.  I doubt it's corrupted (although it can happen if, say, you edited it with a linux text editor that messed with the formatting).  

Not sure what to suggest next

---

### Post by appi2012 on 2008-06-30
If it looks fine, then how come when ntldr is initiated, It launches the recovery one? maybe the way grub gives the command? Do you think that If the windows entry were second on the list it would work? I'm confused.:confused:

---

### Post by logos34 on 2008-06-30
no sure why it does that because the default is clearly marked:

> default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

---

### Post by kansasnoob on 2008-06-30
I've rather lost track but once you've done about so much, to me it's time to try a Super Grub Disk. And if the partition is not bootable from SGD then that OS is just broken.

Then one must focus on restoring or replacing the "broken" OS!

---

### Post by appi2012 on 2008-07-01
That's not entirely true. If the OS was broken, how come when grub tried to load the partition, it loaded the other one? Something is working in the OS.

---

### Post by jumponskis on 2008-07-01
My problem is kind of like this. It's a long story. First: I couldn't boot to windows so logos told me to use testdisk. I did that but it did not help at all. So I tried it again and played around with it a bit and finally ubuntu can see the HP_PAVILION partion in the places menu but it cannot mount it. He gave me two strings of code to try but they didnt work. they made it worse. he recommended trying the xp install cd. I ran chkdsk with it in recovery mode. That made it FAR worse. now when I boot up it goes to the BIOS POST screen where it checks the memory and whatnot, and the next screen is all black with a flashing underscore mark in the top left corner. The only way to use my computer now is to turn on the computer and open the cd drive to put the 8.04 live cd in and close the drive, turn the computer off with the switch (ouch), turn it back on and boot into ubuntu with the option that says try ubuntu without making any changes. PLEASE HELP

EDIT: it may sound like I'm blaming logos but I'm not; I've just been up too long trying to fix this to keep in mind the different ways someone could interpret my posts therefore hurting their feelings.

---

### Post by logos34 on 2008-07-01
Can you see and mount sda5, your linux root partition?  Did you try again to manually mount sda2 (windows)?

The flashing cursor...it's not even getting to the bootloader...check the Bios hard disk setting (should be set for 'auto' or 'LBA'.  I think something you did in testdisk has screwed it up even further.  

post your sudo fdisk -l again--just to make sure it's still seeing the partitions correctly

---

### Post by jumponskis on 2008-07-01
here it is looks ok to me
 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         967     7310488+   c  W95 FAT32 (LBA)
/dev/sda2   *         968       18428   132005160    7  HPFS/NTFS
/dev/sda3           18429       20673    16972200    5  Extended
/dev/sda5           18429       20573    16216168+  83  Linux
/dev/sda6           20574       20673      755968+  82  Linux swap / Solaris
```


[ATTACH]75974[/ATTACH]

16.6 GB is my linux partition and yes I can mount it: 
[ATTACH]75976[/ATTACH]
[ATTACH]75975[/ATTACH]

It doesn't boot far enough to give me the page that gives me the option of pressing F2 to access setup (BIOS)

---

### Post by logos34 on 2008-07-01
ok.

can you still mount linux root (the 16 gb volume)?

the fact the disk still shows up in fdisk means the bios disk settings haven't changed.

>  ...chkdsk said it was inconsistent so I ran testdisk and hdprogs... 

apparently there are still errors on the partition...you've got to find a way to fix those.  And something happened so now you can't even boot as far as grub.

---

### Post by jumponskis on 2008-07-01
> **logos34 said:**
> ok.

can you still mount linux root (the 16 gb volume)?

the fact the disk still shows up in fdisk means the bios disk settings haven't changed.



apparently there are still errors on the partition...you've got to find a way to fix those.  And something happened so now you can't even boot as far as grub.

Exactly. Yes I have already mounted the 16.6 GB volume (see screen shots) but I don't see how that will help me because all the files I need are on the windows partition.  I only just started experimenting with linux based OS's a mere 6 days ago.  Ubuntu is my first go at it.  I figured if I could achieve the cube with the transparent windows and skydome etc.. in 2 days how hard could it be.  then this happened and i have been taken a stp back to re-evaluate...

---

### Post by logos34 on 2008-07-01
that mount error message is just telling us what we already know--there's filesystem/inode/i/o  errors on sda2...If chkdsk can't fix it from the xp cd recovery console, not sure what to suggest...you can flag it for filesystem check in linux using ntfsfix (in the ntfsprogs pkg), but that just triggers a check the next time you try to boot into windows--the problem is you can't even get to grub anymore to choose the windows selection.  

I'd try booting back into the xp cd recovery console and running **fixboot c:** and **fixmbr**...see if that  shakes things up.

---

### Post by logos34 on 2008-07-01
> **jumponskis said:**
> Exactly. Yes I have already mounted the 16.6 GB volume (see screen shots) but I don't see how that will help me because all the files I need are on the windows partition.  Ive only had ubuntu installed for a mere 6 days.

just checking that it was still ok 

Super Grub Disk might be able to help you boot into windows, but 1) you'll have to find a way to dl and burn it (obviosuly can't do it in live cd session), and 2) I'm not sure even that will work because you've got some major filesystem errors on sda2 that chkdsk can't seem to fix

I'm out of ideas...

---

### Post by jumponskis on 2008-07-01
> **logos34 said:**
> that mount error message is just telling us what we already know--there's filesystem/inode/i/o  errors on sda2...If chkdsk can't fix it from the xp cd recovery console, not sure what to suggest...you can flag it for filesystem check in linux using ntfsfix (in the ntfsprogs pkg), but that just triggers a check the next time you try to boot into windows--the problem is you can't even get to grub anymore to choose the windows selection.  

I'd try booting back into the xp cd recovery console and running **fixboot c:** and **fixmbr**...see if that  shakes things up.

ya i ran fixmbr and fix*** (something else that was three letters long that had to do with the filetable) right after chkdsk.  Before doing this I could boot into grub and select windows but it would hang at the black screen that said "starting up..." in the top left.  So I came to you and you told me to do chkdsk so I did but i also did those other two things.  when I restarted I got the black screen with the flashing line...but something I left out I can't boot using the windows cd anymore.  I pick to boot to the dvd drive with the xp cd in, and themn the screen goes completely black (the line isn't even there).  There is no beeping or anything though and I can boot to the ubuntu disk so I know it isn't a hardware problem
> I'm out of ideas...
this is very unsettling... Id rather not have people such as those at bestbuy touch my computer, they are complete imbecils
(e.g. last time I took my computer in becuase it would not turn on, they found out it was my power supply which I already knew but I had extended warranty so I took it in anyway and they insisted on putting in the power supply themselves ((and even picking the power supply even though I had the one I wanted in my hands..)).  When I got home I found they had not even connected the power supply to the computer components...)

---

### Post by logos34 on 2008-07-01
> **jumponskis said:**
> ya i ran fixmbr and fix*** (something else that was three letters long that had to do with the filetable) **right after chkdsk**.  Before doing this I could boot into grub and select windows but it would hang at the black screen that said "starting up..." in the top left. 

Oh, I see, you already did that...then try reinstalling grub to the mbr from live cd (see above link I gave you):

> sudo grub

> root (hd0,4)
> setup (hd0)
> quit

At least that will get you back to booting ubuntu on the hard disk.  But the other troubles (booting xp cd, etc.) has really got me stumped.

---

### Post by jumponskis on 2008-07-01
ok I'll try it I guess It can't really get any more screwed-up than it is right now

---

### Post by logos34 on 2008-07-01
> **jumponskis said:**
> this is very unsettling... Id rather not have people such as those at bestbuy touch my computer, they are complete imbecils
(e.g. last time I took my computer in becuase it would not turn on, they found out it was my power supply which I already knew but I had extended warranty so I took it in anyway and they insisted on putting in the power supply themselves ((and even picking the power supply even though I had the one I wanted in my hands..)).  When I got home I found they had not even connected the power supply to the computer components...)

yeah, I don;t blame you.  The 'geeksquad' is anything but.

---

### Post by sea_monkey987 on 2008-07-01
I think you should now try focusing on recovering that data in the windows partition and then starting over with the hard drive.  I can't remember any names right now (sorry), but may be you should try some sort of data recovery utility.  Also, maybe something with the dd command could be done.  Be careful with that command since it manipulates the hard drive directly!  Sorry I can't be of more help but I thought I should throw some ideas out there.

---

### Post by appi2012 on 2008-07-01
Does anyone know what to do about my problem concerning booting windows?

I'm pretty sure my boot.ini is the problem. What should I do to fix it?

---

### Post by jumponskis on 2008-07-01
> **sea_monkey987 said:**
> I think you should now try focusing on recovering that data in the windows partition and then starting over with the hard drive. you should try some sort of data recovery utility.

yes this is what I have been trying to do for.... well, it's approaching 24 straight hours now.

---

### Post by jumponskis on 2008-07-01
> **appi2012 said:**
> Does anyone know what to do about my problem concerning booting windows?

I'm pretty sure my boot.ini is the problem. What should I do to fix it?

Where are my manners.  I've completely taken over this thread. srry man you have the floor.

---

### Post by logos34 on 2008-07-01
> **appi2012 said:**
> I'm pretty sure my boot.ini is the problem.

You'd get a different error message if that was the case.  

But hopefully someone else has some answers.

The other guy is right--you've got to focus on clearing up the filesystem errors so you can access and backup your windows data.

---

### Post by jumponskis on 2008-07-01
> **logos34 said:**
> try reinstalling grub to the mbr from live cd (see above link I gave you)
  I don't see any link that you gave me only a command...

---

### Post by sea_monkey987 on 2008-07-01
Try photorec:
[http://lifehacker.com/software/data-recovery/download-of-the-day-photorec-161318.php](http://lifehacker.com/software/data-recovery/download-of-the-day-photorec-161318.php)

Unlike what its name implies, it recovers any document.
> Photorec ignores the filesystem, this way it works even if the filesystem is severely damaged.

From what I can see, it should be on the testdisk livecd.  I know for sure that it is in the ubuntu repositories.  Install the "testdisk" package and then do sudo photorec from the terminal (from the livecd obviously).

---

### Post by logos34 on 2008-07-01
> **jumponskis said:**
> I don't see any link that you gave me only a command...

maybe it was in the reply to your PM

here

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jumponskis on 2008-07-02
hey Ive started a new thread since my problem is a little different apparently...  I've learned some new information about what happened to my computer from my brother.  I don't think he did it on purpose but it explains why non of what we have been trying is working.  the thread is here [http://ubuntuforums.org/showthread.php?t=847566]("http://ubuntuforums.org/showthread.php?t=847566")

---

### Post by appi2012 on 2008-07-02
I've backed up my important data in windows, but I'm not sure what to do in order to get my windows booting again. Do you think that using an xp install disk and rewriting the mbr would work? Would I still be able to boot ubuntu? I'm less concerned about my original windows install, so can some one guide me through reinstalling windows while not messing up my ubuntu install?

Thanks for all the great suggestions though!

---

### Post by jumponskis on 2008-07-02
> **appi2012 said:**
> I've backed up my important data in windows, but I'm not sure what to do in order to get my windows booting again. Do you think that using an xp install disk and rewriting the mbr would work? Would I still be able to boot ubuntu? I'm less concerned about my original windows install, so can some one guide me through reinstalling windows while not messing up my ubuntu install?

Thanks for all the great suggestions though!

just use the xp cd, it will guide you through each step and it will not touch your ubuntu install.  You may have to reinstall grub afterward with a supergrubdisk live cd, but I made one of those last night and it took me 3 mins to download and burn to a cd, and it is reaaally simple to use (choose the first option from the supergrub disk menu that says (with help) at the end):)

---

### Post by appi2012 on 2008-07-02
My hp didn't come with a windows cd, but I have an old one that has SP1 on it. (my hp had SP2) Do you think that would make a difference?

---

### Post by jumponskis on 2008-07-02
no it doesn't matter my xp cd is SP1 also just be sure to upgrade to sp2 and sp3 versions of xp. (yes there is a sp3 XP out now also that came out the same time as sp1 for Vista.)  let me know if it works.

---

