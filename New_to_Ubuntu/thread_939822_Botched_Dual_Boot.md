---
title: "Botched Dual Boot"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by shade34321 on 2008-10-06
Last night I installed a fresh install of Windows XP Pro on a new 500 GB hard drive. I divided the hard drive into 4 partitions. 2 100 GB partitions(one for XP and Ubuntu), a swap partition, and the rest for my files. After installing XP I checked to make sure it worked, and it did. After that I installed ubuntu on the second 100 GB partition used the manual install to put it on the right partition and set that as /. After I installed and rebooted my computer it seemed to work. Grub came up and had Ubuntu 8.04 and Windows XP as an option. I checked Ubuntu to makes sure it worked and it did, then I checked XP to see if it worked. It gave me the blue screen of death. Any ideas of how I messed this up and how it can be fixed would be greatly appreciated. Thanks!

---

### Post by shifty_powers on 2008-10-06
did you get to see the blue screen message?

---

### Post by shade34321 on 2008-10-07
Yes, it says UNMOUNTABLE_BOOT_VOLUME.

---

### Post by kansasnoob on 2008-10-07
Well, lets start by seeing the output of:

```
sudo fdisk -l
```

---

### Post by shade34321 on 2008-10-07
Nothing outputs. It just starts a new command line.

---

### Post by HellNoire on 2008-10-07
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

This guide has helped me when I was dual booting, now I'm just Linux only. But take a look, it should help.

---

### Post by caljohnsmith on 2008-10-07
OK, try this: boot your Live CD, open a terminal (applications > accessories > terminal), and please post the output of what kansasnoob asked for:
```
sudo fdisk -l
```
Note the "-l" is a lowercase L, not a one.

---

### Post by shade34321 on 2008-10-07
So I thought maybe if I tried doing it again it would fix the problem. It didn't and the same thing happened. So with the same set up as last time this is what I get after sudo fdisk -l.

shade@OH-YEAH:~$ sudo fdisk -l
[sudo] password for shade: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aed41b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       28908    97996500   83  Linux
/dev/sda3           28909       60801   256180522+   5  Extended
/dev/sda5           28909       29157     2000061   82  Linux swap / Solaris
/dev/sda6           29158       60801   254180398+   b  W95 FAT32

---

### Post by caljohnsmith on 2008-10-07
OK, I have a hunch your problem is with Windows and not Grub, but let's check your menu.lst first:
```
cat /boot/grub/menu.lst
```
Do you still have your Windows Install CD handy? It is highly likely you will need it to do a few repairs on your Windows, but first post your menu.lst above and we can work from there.

---

### Post by WWSmith36 on 2008-10-07
> dev/sda6 29158 60801 254180398+ b W95 FAT32

Since linux can easily read and write to NTFS partitions, there is really no need to use the FAT32 format anymore.

---

### Post by shade34321 on 2008-10-07
I know but when I was using the manual install for ubuntu it wouldn't let me format it NTFS so I went with FAT32 to change it to NTFS later.

---

### Post by shade34321 on 2008-10-07
Here's what it said.

shade@OH-YEAH:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=89725809-8a98-43da-bf5c-0150d6df8a2e ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=89725809-8a98-43da-bf5c-0150d6df8a2e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=89725809-8a98-43da-bf5c-0150d6df8a2e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
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

---

### Post by caljohnsmith on 2008-10-08
Your Windows entry in menu.lst should work just fine to boot Windows, so I think you have a Windows problem and not a Grub problem at this point. If you have your Windows Install CD, boot that up, go to the "recovery console", and run the following commands:
```
fixboot
chkdsk /r
```
Then reboot, and let us know exactly what happens when you choose Windows from the Grub menu again. It is likely we will have to use testdisk to repair the boot sector of your Windows partition, but do the above first and report the results.

---

### Post by shade34321 on 2008-10-11
Sorry it took so long for me to reply, school work and work keep have been keeping me away from completing this. The fixboot command gave me FIXBOOT cannot find the system drive, or the drive specified is not valid. And chkdisk /r gave me the volume appears to contain or or more unrecoverable problems.

---

### Post by caljohnsmith on 2008-10-11
> **shade34321 said:**
> Sorry it took so long for me to reply, school work and work keep have been keeping me away from completing this. The fixboot command gave me FIXBOOT cannot find the system drive, or the drive specified is not valid. And chkdisk /r gave me the volume appears to contain or or more unrecoverable problems.
"Unrecoverable problems"? That's not a good sign. Since XP is a fresh install, how about just reinstalling at this point? It will overwrite Grub in the MBR, but first confirm after installing Windows that you can directly boot into it. Once you are sure of that, you can reinstall Grub with these simple steps:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
Let me know how it goes.

---

### Post by shade34321 on 2008-10-12
Well I went to do a fresh install and it kept looping back into an install, it would wouldn't finalze the install. So I'm not quite sure what's up with this. It did this before as well. So I think I might just leave it with Ubuntu only and then have XP on my laptop. I don't know....we'll see.

---

