---
title: "C and d drive swapped"
date: 2008-05-19
forum: Other OS Talk
---

### Post by Jorell00 on 2008-05-19
hoping I might be able to get some help on this...
after clean install of Hardy ,I am unable to get into XP.
My c drive has become D drive and vice versa . So when click on XP in grub , I get NTLDR is missing. Presumably because it's looking on C drive (old D drive) for boot files . I've spent a week researching and trying to find a solution . If anyone was any ideas I would greatly appreciate them..

here's output of my sudo fdisk -l (sdc1 is the xp Partition)


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc16b10d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35da35d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3cfda7cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3824    30716248+   7  HPFS/NTFS
/dev/sdc2            3825        4073     2000092+  82  Linux swap / Solaris
/dev/sdc3            4074        6196    17052997+  83  Linux
/dev/sdc4   *        6197       19929   110310322+   7  HPFS/NTFS


and my boot ini (if that helps )

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptOut


Please help -

---

### Post by LeoSolaris on 2008-05-19
This was a fresh install correct? Did you use the built in (in the install process) partition editor to resize Windows, or did you use GParted? I know that in 7.10, the built in partition editor did a destructive partitioning rather than actually compressing everything properly.

Do you have access to the Windows partition from Ubuntu?

To translate what I am seeing, it looks like you have a 500G hard drive, a 200G hard drive, and a 160G hard drive. The 160G has all of the bootable partitions?

(By the way, C drive and D drive are just Windows naming system, Linux uses a different one.)

---

### Post by LaRoza on 2008-05-19
Post the output of this command:

```

cat /boot/grub/menu.lst

```

(C: and D: are just pre-DOS naming conventions that mean nothing to Linux)

---

### Post by Jorell00 on 2008-05-19
Yes fresh install , using partitions from previous ubuntu installation. 
I have access to windows partition. yes your correct about the drives with the 160 having bootable partitions.
 

output of menu.lst

#[PHP] menu.lst - See: grub(8), info grub, update-grub(8)
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

#A splash image for the menu
#splashimage=(hd0,2)/boot/grub/splashimages/mac1.xpm.gz

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
# kopt=root=UUID=262d7c32-096f-4fb5-adb1-5b5946181b54 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=262d7c32-096f-4fb5-adb1-5b5946181b54 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=262d7c32-096f-4fb5-adb1-5b5946181b54 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1[/PHP]



Any ideas ?

---

### Post by LaRoza on 2008-05-19
> **Jorell00 said:**
> Yes fresh install , using partitions from previous ubuntu installation. 
I have access to windows partition. yes your correct about the drives with the 160 having bootable partitions.
 

output of menu.lst

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

#A splash image for the menu
#splashimage=(hd0,2)/boot/grub/splashimages/mac1.xpm.gz

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
# kopt=root=UUID=262d7c32-096f-4fb5-adb1-5b5946181b54 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=262d7c32-096f-4fb5-adb1-5b5946181b54 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=262d7c32-096f-4fb5-adb1-5b5946181b54 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1



Any ideas ?

Please wrap output in code tags so it is easier to read. Looking at the menu.lst, I see "map" twice. I never never seen that before so I am not willing to give any advise on it.

Is there a reason why you are not having the first hard disk for the OS's? Perhaps Windows has an issue with that. I have had (using Sata) Vista as the second disk and it worked, but I don't know about XP. Did it work fine before?

---

### Post by Jorell00 on 2008-05-19
sorry - didn't know about the code tags.
no idea why the OS drive isn't the first one . Anyway to change that?? maybe that will help
yes all worked fine before

---

### Post by LaRoza on 2008-05-19
> **Jorell00 said:**
> sorry - didn't know about the code tags.
no idea why the OS drive isn't the first one . Anyway to change that?? maybe that will help
yes all worked fine before

What kind of drives are these?

By being the first one I meant it literally. Exactly what is the first drive depends on what kind of drives they are.

---

### Post by Kevbert on 2008-05-19
Please post the output of:
```
sudo fdisk -l
```
You may be able to change 
```
root (2,0)
```
to
```
root (1,0)
```
to get round this problem. 'map' may not be required ([http://www.gnu.org/software/grub/manual/grub.html.gz#map]("http://www.gnu.org/software/grub/manual/grub.html.gz#map"))
I don't have this with my version of grub and I'm booting WinXP, Fedora, Ubuntu, Kubuntu and openSuse via two SATA drives.

---

### Post by Jorell00 on 2008-05-19
ide drive - bootable 160g
and the other two are sata drives ( is that what you mean?)

---

### Post by LaRoza on 2008-05-19
> **Jorell00 said:**
> ide drive - bootable 160g
and the other two are sata drives ( is that what you mean?)

Yes. I am not familiar with mixing drives like that, and am unable to really diagnose the problem. Sorry.

---

### Post by Jorell00 on 2008-05-19
output of sudo fdisk -l
[PHP]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc16b10d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35da35d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3cfda7cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3824    30716248+   7  HPFS/NTFS
/dev/sdc2   *        3825        4073     2000092+  82  Linux swap / Solaris
/dev/sdc3            4074        6196    17052997+  83  Linux
/dev/sdc4            6197       19929   110310322+   7  HPFS/NTFS
[/PHP]

---

### Post by Jorell00 on 2008-05-19
Thanks to all . It's know sorted. I did as 
Kevbert suggested ,I changes the root to (1,0) and removed the map entries and it's now all working . Thanks again

---

### Post by mips on 2008-05-20
> **Jorell00 said:**
> ide drive - bootable 160g
and the other two are sata drives ( is that what you mean?)

Mixing drives like that can be a bit of a pain. From experience I would say the machine boots the PATA(IDE) drives before it boots the SATA drives. You should be able to select the HD boot order in BIOS so you can make the drives boot in the order you want.

---

