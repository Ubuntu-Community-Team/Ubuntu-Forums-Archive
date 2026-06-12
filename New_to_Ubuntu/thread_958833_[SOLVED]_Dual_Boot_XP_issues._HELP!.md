---
title: "[SOLVED] Dual Boot XP issues. HELP?!"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by endrswrd on 2008-10-25
I recently install kubuntu on my desktop. Its not my first time dealing with the ubuntu distro. But I dont consider myself well known with linux. Kubuntu has no problem booting up through grub. But when i go to boot xp Pro it just has the starting up.... and thats all it says. nothing happens at all. Any help would be greatly appreciated because i have no desire to reformat. thank you

---

### Post by Duck2006 on 2008-10-25
Do you get a error message?

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by endrswrd on 2008-10-25
I acutally dont get any message at all. It just moves through the three periods after starting up... and doesnt do anything just keeps doing that.

---

### Post by caljohnsmith on 2008-10-25
Sounds like a Windows problem rather than a Grub problem, but first we should make sure your Grub entry for Windows is OK. Open a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there. :)

---

### Post by drowner on 2008-10-25
> **endrswrd said:**
> I acutally dont get any message at all. It just moves through the three periods after starting up... and doesnt do anything just keeps doing that.

Does it start to boot windows at all, like do you get a splash screen or anything? Or does it just hang on a black screen?

---

### Post by endrswrd on 2008-10-25
Its a big post but here it is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b9de544

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   390636539   195318238+   7  HPFS/NTFS
/dev/sda2       398540520   488392064    44925772+  83  Linux
/dev/sda3       390636540   398540519     3951990    5  Extended
/dev/sda5       390636603   398540519     3951958+  82  Linux swap / Solaris

Partition table entries are not in disk order
ceir@ceir-desktop:~$ cat /boot/grub/menu.lst
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
timeout         10

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
# kopt=root=UUID=9a4aac02-89ad-4273-8b9b-d59cd5d0edb5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=9a4aac02-89ad-4273-8b9b-d59cd5d0edb5 ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=9a4aac02-89ad-4273-8b9b-d59cd5d0edb5 ro single
initrd          /boot/initrd.img-2.6.24-21-generic

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=9a4aac02-89ad-4273-8b9b-d59cd5d0edb5 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=9a4aac02-89ad-4273-8b9b-d59cd5d0edb5 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

thats all of it

---

### Post by endrswrd on 2008-10-25
it never really hangs. it just does the starting up... were the three periods move making me think its just loading but ive let it sit for 20 minutes and no change

---

### Post by caljohnsmith on 2008-10-25
OK, I think I know what the problem is, just do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens when you boot Windows. :)

---

### Post by endrswrd on 2008-10-25
thanks Booted right up to XP. Excited to be able to finally play with my linux again.

---

