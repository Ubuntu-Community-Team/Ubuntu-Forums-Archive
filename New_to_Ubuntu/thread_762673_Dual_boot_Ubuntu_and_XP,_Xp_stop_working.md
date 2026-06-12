---
title: "Dual boot Ubuntu and XP, Xp stop working"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by sholasys on 2008-04-22
after installing ubuntu and some packages, like wine, advance desktop effect, i can no longer boot to Xp again. At the boot menu after selecting windows xp it will just restart the laptop. If any body can help me pls i need to get some files out of it.
thanks

---

### Post by Ub1476 on 2008-04-22
You should be able to access XP from Places>Computer. If it's not there, post the output of:

```
sudo fdisk -l

cat /boot/grub/menu.lst
```

---

### Post by Joeb454 on 2008-04-22
Strange, sounds like it could be something to do with GRUB.

Do you get any error messages or any output at all before it restarts? Failing that, the above post will let us know if you can recover your files :)

---

### Post by sholasys on 2008-04-22
erudite@sholly:~$ sudo fdisk -l
[sudo] password for erudite:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
2 heads, 16 sectors/track, 4884421 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x08cd6025

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1     2560000    40959992    7  HPFS/NTFS
/dev/sda2         2560001     2682070     1953120    5  Extended
/dev/sda3         2682071     3292422     9765632   83  Linux
/dev/sda4         3292423     4884402    25471680   83  Linux
/dev/sda5         2560001     2682070     1953112   82  Linux swap / Solaris
erudite@sholly:~$ 



that is the result of the above commands. There is no any error message. imediatley i select windows xp it will jst restart the lapto.
Before i install wine, advance destop effect and some codec, i am able to load windows xp and boot to it.
pls help

---

### Post by Periswell on 2008-04-22
consider it good that windows broke.;)

just get rid of windows and run a virtual box on ubuntu.

---

### Post by sholasys on 2008-04-22
I will get rid of it but not as immediately. i hv some stuff i need to pull out

---

### Post by quinnten83 on 2008-04-22
> **Periswell said:**
> consider it good that windows broke.;)

just get rid of windows and run a virtual box on ubuntu.
That still isn' t going to solve the problem at hand.

Sometimes Ubuntu will not immediately load the program to read/write to NTFS (which is basically your windows partition).
If you install ntsf-3g, it will recognize it after that, just check the options that appear after starting the program the first time.
```

sudo apt-get install ntfs-3g
```

Remember it is a good idea to always backup your data before you install ubuntu or any other operating system for that matter.

---

### Post by Joeb454 on 2008-04-22
ntfs-3g has been installed by default since Ubuntu 7.10 with read/write capabilities.

I often use ntfs-config to get it to auto-mount my Windows Partition however, perhaps that is what you were thinking of?

```
sudo aptitude install ntfs-config
```

---

### Post by Jammy4041 on 2008-04-22
When you get to the GRUB menu, try scrolling down to Windows XP and Press F8 for advanced windows boot Options. I'm not 100% sure about this, but I do know if you get into the Advanced Windows Boot Options, you can then boot to windows in its last know good configuration.

Hope this helps.

---

### Post by Joeb454 on 2008-04-22
Usually it involves pressing Enter on the Windows XP option, then hammering F8 almost immediately after ;)

---

### Post by Ub1476 on 2008-04-22
> **sholasys said:**
> erudite@sholly:~$ sudo fdisk -l
[sudo] password for erudite:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
2 heads, 16 sectors/track, 4884421 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x08cd6025

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1     2560000    40959992    7  HPFS/NTFS**
/dev/sda2         2560001     2682070     1953120    5  Extended
/dev/sda3         2682071     3292422     9765632   83  Linux
/dev/sda4         3292423     4884402    25471680   83  Linux
/dev/sda5         2560001     2682070     1953112   82  Linux swap / Solaris
erudite@sholly:~$ 


I would like to see the result of the grub configuration file as well:

```
cat /boot/grub/menu.lst
#eventually:
gksudo gedit /boot/grub/menu.lst
```

;)

---

### Post by sholasys on 2008-04-23
erudite@sholly:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=44a91dc1-28be-410c-b254-125cb21129df ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=44a91dc1-28be-410c-b254-125cb21129df ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=44a91dc1-28be-410c-b254-125cb21129df ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

erudite@sholly:~$ #eventually:
erudite@sholly:~$ gksudo gedit /boot/grub/menu.lst

---

### Post by nicedude on 2008-04-23
Sholasys, heres the end of my laptop grub which has XP on first partiiton like yours and I see no differences so it might not be a grub problem. It might be a problem with your XP NTFS partition. After looking I saw this package that you can install with synaptic for ubuntu "ntfsprogs" it has several tools that help you manage NTFS. One of the included tools is named ntfsfix 

ntfsfix - fix common errors and force Windows to check NTFS
Synopsis
ntfsfix [options] device
Description
ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.
You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other way and it cannot be mounted. 

Hope maybe that works to get it to boot up your XP. I also don't see how updating Ubuntu or installing compiz could do this to your disk but hey weird stuff happens. Anyway goodluck.
   




### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

nicedude@mybox:~$

---

### Post by SR_ELPIRATA on 2008-04-23
Im having this issue as well, though in my case selecting XP won't cause it to restart, it will just hang in there. Tried safe mode and normal and didnt work. 2 days ago it worked with the LAST KNOWN GOOD, but other than that its normally a dead drive.

I thought I was having mobo problems, Im glad (sort of) that somebody else had it.

I'm installing the ntfsprogs and see what it does.

ELP

---

### Post by kannehana on 2008-05-05
> **SR_ELPIRATA said:**
> 

I'm installing the ntfsprogs and see what it does.

ELP
I got the same problem last night. After the Ubuntu installation on /dev/sdb SATA disk XP booted alright from the first disk. I can still see WINDOWS on /dev/sda but when started from GRUB it just reboots immediately, even when I select Safe Mode from Windows boot menu that follows GRUB. I have activate boot log on BOOT.INI but there's nothing relevant in the XP boot log.

I have started Windows installation in Repair mode and executed chkdsk /p. It detected one error on C: NTFS and fixed it. The reboot problem remains.

I am interested to hear about the results of *ntfsprogs*. Another utility that proved helpful is *chntpwd* (change NT password): it helped me to zero the long forgotten Administrator password for the XP setup's Repair mode.

Update: Even XP's chkdsk /r did not help and boy that was long. Finished reinstalling XP. Then found the backups not containing a complete system state. My XP finished to be about unusable without a major configuration work! Good for you. Booted on Ubuntu live CD, activated GRUB on the first disk with **grub-install --root-directory /mnt --recheck /dev/sda**. Guess what, XP did not boot anymore. So it was GRUB, after all. What a dummy I was, I could have tested first the FIXMBR in XP's Recovery menu. Here's the part of my* menu.lst*:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1
#
```

---

