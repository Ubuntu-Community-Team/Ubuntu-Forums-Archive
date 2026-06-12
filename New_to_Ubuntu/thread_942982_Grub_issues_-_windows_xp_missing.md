---
title: "Grub issues - windows xp missing"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by dreadh3ad on 2008-10-09
I have windows xp installed on a hard drive A in my machine and installed Ubuntu 7.10 on hard drive b. Upon rebooting grub did not give me an option to boot into windows xp.  

How can I fix this?

---

### Post by caljohnsmith on 2008-10-09
You'll have to add an entry to your Grub menu, found in /boot/grub/menu.lst. How about first posting:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by dreadh3ad on 2008-10-09
```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    74878964    37439451   83  Linux
/dev/sda2        74878965    78172289     1646662+   5  Extended
/dev/sda5        74879028    78172289     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x391173a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488375999   244187968+   7  HPFS/NTFS

```

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=1ffa8111-463c-48ee-a256-67c6d0b58f9f ro

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
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=1ffa8111-463c-48ee-a256-67c6d0b58f9f ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=1ffa8111-463c-48ee-a256-67c6d0b58f9f ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1ffa8111-463c-48ee-a256-67c6d0b58f9f ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1ffa8111-463c-48ee-a256-67c6d0b58f9f ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by caljohnsmith on 2008-10-09
OK, open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
and at the end, add:
```
title Windows XP
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
Reboot, select Windows, and let me know what happens. :)

---

### Post by dreadh3ad on 2008-10-09
NTLDR Missing

---

### Post by caljohnsmith on 2008-10-09
Looks like you have a Windows problem rather than a Grub problem at this point. Can you boot your sdb Windows drive directly on start up, and does that work? 

From Ubuntu, please do:
```
sudo umount /dev/sdb1
```
Don't worry about a not mounted error, that is only to make sure. Proceed with:
```
sudo mount /dev/sdb1 /mnt
ls -l /mnt
```

---

### Post by handydan918 on 2008-10-09
I believe the Windows problem you have may be the fact that Windows wants to be on the first partition of the first harddrive. If you reverse the cabling of your disks, and reinstall GRUB, I would bet that would correct it.
There is a way to "re-map" the drives in GRUB, but I haven't had to fool with that for a long time...
ever since I quit using Windows....

---

### Post by benz3k3 on 2009-02-15
i had d same problem of windowsxp missing from grub 

go rid of it by formating n reinstaling linux n windows 
but dis problem occured again wen i changed a ext3 partion to ntfs
n also ubuntu does not show contents of ntfs partition wen d xp thing goes missing from grub

so wht i did waz tried d usual thing, update menu.lst  

title Windows XP
root 	(hd0,0)
makeactive
savedefault
chainloader +1


but dis didnt solve d problem 
den i tried bootin with xp cd
selected repair 
used the fixboot command to fix the bootsector 

one shud try dis ,,, i dont knw how it worked,,but it sure did save a lot of my time playin with grub n instalin ubuntu n windows

---

