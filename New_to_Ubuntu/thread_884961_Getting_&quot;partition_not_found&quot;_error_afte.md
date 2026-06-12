---
title: "Getting &quot;partition not found&quot; error after Ubuntu install"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by think_tough on 2008-08-09
Hi All,

I have windows xp on one of my disks and today I was trying to install ubuntu 7.04 in a different partition of same disk. However, after installing, I am not able to boot into either windows or ubuntu and I get a "partition not found" error when I select either of these OS. Can someone plz help me? I tried to reinstall ubuntu also, but that doesnt seem to work. :( Can someone here please help?
I am attaching the contents of some of my files here -


1. The contents of /etc/fstab -

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb7
UUID=3f796c69-33d9-4bc1-9492-f80778bbd6fa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=98E7-2F4D  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=0433-AC4A  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=4CA88EF6A88EDE38 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=C884-5416  /media/sdb6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb8
UUID=a0476b72-c38d-4293-bf54-a538e3cd0ad2 /media/sdb8     ext3    defaults        0       2
# /dev/sdb10
UUID=84aa12e2-678c-4f8f-97fe-8e5c6e29039b none            swap    sw              0       0
# /dev/sdb9
UUID=894b3446-f42f-4eb8-8cfc-e0db8f9ea2d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



2. Output of fdisk -l command -

Disk /dev/sda: 20.4 GB, 20411080704 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2481    19928601    c  W95 FAT32 (LBA)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sdb2            2551        9721    57601057+   f  W95 Ext'd (LBA)
/dev/sdb5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sdb6            5101        7650    20482843+   b  W95 FAT32
/dev/sdb7            7651        8592     7566583+  83  Linux
/dev/sdb8   *        8593        9514     7405933+  83  Linux
/dev/sdb9            9515        9562      385528+  82  Linux swap / Solaris
/dev/sdb10           9563        9721     1277136   82  Linux swap / Solaris


3. Contents of /boot/grub/device.map -

(hd0)   /dev/sda
(hd1)   /dev/sdb

4. Contents of /boot/grub/menu.lst -

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=3f796c69-33d9-4bc1-9492-f80778bbd6fa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3f796c69-33d9-4bc1-9492-f80778bbd6fa ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3f796c69-33d9-4bc1-9492-f80778bbd6fa ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by louieb on 2008-08-09
After a quick look everything looks all right.

Is one drive IDE and the other sata?
If so may have some GRUB confusion.
Try this with the device.map
from 
```
(hd0)   /dev/sda
(hd1)   /dev/sdb 
```
to 
```
(hd0)   /dev/sdb
(hd1)   /dev/sda
```

One other thing you can do is let GRUB tell you where its at 
when the GRUB menu comes up press **c **to get the command prompt.

and type 
```
find  /boot/grub/stage1
```

I suspect that GRUB is looking at your hard drives opposite of what they should be. 
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by think_tough on 2008-08-10
Thanks for your reply, louieb. I tried what you suggested, but that didn't seem to work. So, next I reverted back to my old device.map which looked like this -

```

(hd0) /dev/sda
(hd1) /dev/sdb

```

And, I tried to modify my menu.lst file only to point to (hd0,6) instead of (hd1,6). This helped me to boot into linux from my hard disk without the help of my cd. However, I tried to change the windows section in my menu.lst file also to point to (hd0,0) instead of (hd1,0). This does not work :( Could you please suggest me a solution to fix this? This is how my current menu.lst looks -


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=3f796c69-33d9-4bc1-9492-f80778bbd6fa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3f796c69-33d9-4bc1-9492-f80778bbd6fa ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3f796c69-33d9-4bc1-9492-f80778bbd6fa ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by louieb on 2008-08-10
So windows is defiantly on the same drive as Ubuntu?
If that is so remove the map lines from  the windows entry. 
The map lines are used when windows is on the 2nd drive, to make it believe its on the 1st drive.  

Good Luck.

One more thing. find the line in menu.lst
```
# groot=(hd1,6)
```
and change it too
```
# groot=(hd0,6)
```

That line is used by update-grub to built the entry when a new kernel is installed during update.

---

### Post by think_tough on 2008-08-11
Thanks a ton, louieb. That worked.

---

### Post by louieb on 2008-08-11
Glad it working. Please mark the thread a solved by clicking on thread tools and clicking solved.

---

