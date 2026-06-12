---
title: "[SOLVED] Grub No longer shows original system"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Tom Atkins on 2008-08-27
I just installed 8.04 LTS from the DVD on sysb. I had Suse 10.0 on sysa with GRUB as the loader. Now GRUB only show Ubuntu as four entries (2 normal and 2 faail safe). How do I get my entries for Suse back? It was being booted from hda1 /boot.

TIA

---

### Post by northern lights on 2008-08-27
From within Ubuntu, can you please post the outputs of ```
cat /boot/grub/menu.lst
``` and ```
sudo fdisk -L
```

Thank you.

---

### Post by Tom Atkins on 2008-08-27
How do I copy from the terminal to this thread?

---

### Post by northern lights on 2008-08-27
Either via the context menu --> "Edit > Copy" or by hitting 'Ctrl+Shift+C'.

You can mark with the mouse.

---

### Post by Tom Atkins on 2008-08-27
Here they are. copy and past do not seem to work in quick reply window

fdisk: invalid option -- L


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
tommy1@tommy1-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          14      112423+  83  Linux
/dev/sda2              15         145     1052257+  82  Linux swap / Solaris
/dev/sda3             146        9728    76975447+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000abcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9355    75144006   83  Linux
/dev/sdb2            9356        9729     3004155    5  Extended
/dev/sdb5            9356        9729     3004123+  82  Linux swap / Solaris
tommy1@tommy1-desktop:~$ 

tommy1@tommy1-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=16fe3a84-6e50-441d-a800-314ae5ce59dc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
tommy1@tommy1-desktop:~$

---

### Post by sandysandy on 2008-08-27
u will need to manually make entries for open suse in the ubuntu's menu.lst

first backup menu.lst

regards

---

### Post by northern lights on 2008-08-27
Mkey.

So we indeed need to add SUSE entries to the menu.lst. Neither unexpected nor a problem. However, 'fdisk' options ought to be lower case (my typo).

So please also post the output of ```
sudo fdisk -l
```It's still an L, just lower case...

---

### Post by Tom Atkins on 2008-08-27
Here it is:confused:


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          14      112423+  83  Linux
/dev/sda2              15         145     1052257+  82  Linux swap / Solaris
/dev/sda3             146        9728    76975447+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000abcfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9355    75144006   83  Linux
/dev/sdb2            9356        9729     3004155    5  Extended
/dev/sdb5            9356        9729     3004123+  82  Linux swap / Solaris
tommy1@tommy1-desktop:~$

---

### Post by caljohnsmith on 2008-08-27
Tom, to add OpenSUSE to your Ubuntu menu, you could look in your OpenSUSE Grub's menu.lst/grub.conf and copy those entries into your /boot/grub/menu.lst in Ubuntu (or if OpenSUSE uses LILO, you'll have to look inside its boot menu file). Or you could simply link to OpenSUSE's menu.lst/grub.conf by putting an entry in your Ubuntu's menu.lst like:
```
title   OpenSUSE
root    [COLOR="Blue"](hdX,Y)[/COLOR]
configfile  [COLOR="Blue"]/boot/grub/menu.lst[/COLOR]
```
I assume your OpenSUSE is sda1 since that is the bootable partition, so you would use (hd0,0) above. Also you need to give the correct path above to OpenSUSE's boot loader menu (whether it be menu.lst, grub.conf, or a LILO file). 

If you need more help figuring out the particulars, let me know; I'm not sure what your experience level is. :)

---

### Post by Tom Atkins on 2008-08-27
That Worked!!!!!!!!!!!!!!!!

Thank you very much. I have spent several hours trying to correct this

Thanks again.

Tom Atkins

---

