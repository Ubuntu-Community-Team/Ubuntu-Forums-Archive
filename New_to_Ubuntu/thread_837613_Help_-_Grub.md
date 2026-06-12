---
title: "Help - Grub"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by txflatt on 2008-06-22
I installed Xubuntu on a removable drive and kept my Windows XP Pro on the laptop...

Now, I have to have the removable drive attatched to the laptop just to boot into Windows or I get a Grub error and I can't boot.  

How do I fix this?  Thanks!

---

### Post by Biggy on 2008-06-22
[Super Grub Disk]("http://supergrub.forjamari.linex.org/") to fix grub

---

### Post by Mikecore on 2008-06-22
please post the output of 

```


sudo less /boot/grub/menu.lst


```

---

### Post by Johnnie_Walker on 2008-06-22
> **Biggy said:**
> [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to fix grub
It will definitely help, unless the BIOS is somehow f**ked up, because a week ago it was just the same with me. Fixed the GRUB with the great Super GRUB Disk, but the Win partition was unaccessible and reinstalling Winbuzz was needed. Back up important data and prepare for the worst :)

---

### Post by txflatt on 2008-06-26
timeout             10
hiddenmenu
title                    Microsoft WIndows XP Professional
root                   (hd0,0)
savedefault
makeactive
chainloader     +1

title                    Ubuntu 8.04, kernel 2.6.24-18-generic
root                    (hd1,0)
kernel                /boot/vmlunuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro quiet splash
initrd                  /boot/initrd.img-2.6.24-18-generic
quiet

title                    Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root                    (hd1,0)
kernel                /boot/vmlunuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro single
initrd                  /boot/initrd.img-2.6.24-18-generic

title                    Ubuntu 8.04, memtest86+
root                    (hd1,0)
kernel                /boot/memtest86+.bin
quiet

---

### Post by Pudworthy on 2008-06-26
I think your problem is that your computer is trying to boot into Grub which, unfortunately, is stored on your removable drive. I haven't tried it, but I think [THIS]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4") is what you need to do.

P

---

### Post by bobnutfield on 2008-06-26
I have never used Super Grub and it may in fact help, but when I install to an external drive (USB) I always install Grub to that drive rather than the MBR.  Then, I just set the computer to boot from the external drive (pressing F12 on my laptop and many others.)  That way, whatever is on the internal hard drive is not involved.  Just a thought.

Bob

---

### Post by txflatt on 2008-06-26
That is what I intended to do... however (being new to this whole thing), that's not how it ended up.   I'd like to restore the MBR to the regular windows XP way of things and do the "F12" thing.   

So how do I fix it without screwing up the XP side?

---

### Post by drs305 on 2008-06-26
> **txflatt said:**
> That is what I intended to do... however (being new to this whole thing), that's not how it ended up.   I'd like to restore the MBR to the regular windows XP way of things and do the "F12" thing.   

So how do I fix it without screwing up the XP side?

[HowTo: Cannot boot windows without external hard drive plugged in]("http://ubuntuforums.org/showthread.php?p=3995006")

---

### Post by Pudworthy on 2008-06-26
If you do as I suggested above, ie, using easyBCD to rewrite the MBR to xp and then adding Neogrub into it, you can then set the default timer to 0 and then it won't bring up the bootloader but you can press F12 to go into it.

I *think*...

P

---

### Post by txflatt on 2008-06-26
OK... I tried to follow the instructions...Now I can't boot into windows! here's what menu.lst shows now and what fdisk -l shows:

map (hd1) (hd0)
savedefault
makeactive
chainloader +1

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet


************

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc3ecc3e

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9729 78148161 7 HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004638af

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 6998 56211403+ 83 Linux
/dev/sdb2 6999 7301 2433847+ 5 Extended
/dev/sdb5 6999 7301 2433816 82 Linux swap / Solaris

---

### Post by txflatt on 2008-06-26
Let me repost the menu.lst:

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
# kopt=root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro

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

title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7c71f747-3901-4ec2-80e2-6dbe79fee455 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by kansasnoob on 2008-06-26
First change the menu. lst back to what it originally was. That wasn't the problem.

Just FYI, here's a Quick Guide to GRUB's Numbering System:

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

Back to your original problem, what happened is GRUB "rewrote" your XP mbr. So you need to "restore" the XP mbr.

To do this you'll either need your Windows XP Recovery Disc or an alternative like this:

[http://www.download.com/MbrFix/3000-2094_4-10485990.html?tag=lst-0-1&cdlPid=10485991](http://www.download.com/MbrFix/3000-2094_4-10485990.html?tag=lst-0-1&cdlPid=10485991)

If using the Windows Recovery Disc:
(of course you'll have your external drive UNPLUGGED)
Boot with the XP installation CD.
When prompted, press R to repair the Windows XP installation.
Enter the administrator password if prompted.
To fix the MBR, use the following command:

```
fixmbr
```

Type y and ENTER to fix the MBR.
Type exit to leave the recovery console and reboot.

But, do yourself a big favor and wait! Run this by at least one other person on the forum before jumping into it, because I'm NOT feeling quite up to par. There is a possibility that you'll also need to "fixboot" at the same time you "fixmbr", but I'm thinking not on XP.

My actual "preferred" method of doing this on my own machines is to create a dedicated GRUB partition on the permanent hard drive, but that's purely preference because I'm continually fiddling with things, deleting one OS, and installing another adnauseum. 

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

