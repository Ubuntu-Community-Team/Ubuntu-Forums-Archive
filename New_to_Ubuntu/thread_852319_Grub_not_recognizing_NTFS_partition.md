---
title: "Grub not recognizing NTFS partition"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by mitchbones on 2008-07-07
I decided to install the new version of Ubutnu. I decided to delete the old ubuntu partition and just create a new partition with the old space. I believe grub was installed on the one I deleted.

Made a new partition (logical, was that a bad idea?) at the beginning, and then said to install the bootloader on hd0 instead of a specific partition.

Now when I boot up grub doesn't recognize my windows partition.

Thanks.

Edit: Should I reinstall and install grub on one of the partitions instead of "hd0"

---

### Post by stoneybroke on 2008-07-07
You could try this sudo apt-get install startupmanager then use startupmanager from the shell for a complete guide to setting up a hard drive try downloading this PDF document [http://knowfree.net/2008/01/29/beginning-ubuntu-server-administration-from-novice-to-professional.kf](http://knowfree.net/2008/01/29/beginning-ubuntu-server-administration-from-novice-to-professional.kf) you can also get 1,000's of other ebooks free at the same place.

That should help you.

---

### Post by wolfen69 on 2008-07-07
do
```
gksudo gedit /boot/grub/menu.lst
```
post output here.

---

### Post by mitchbones on 2008-07-07
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
timeout		3

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
# kopt=root=UUID=d27dba00-955b-48b4-a620-34a82e0b2aad ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d27dba00-955b-48b4-a620-34a82e0b2aad ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d27dba00-955b-48b4-a620-34a82e0b2aad ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by bumanie on 2008-07-07
It would also be helpful to have the output of > sudo fdsik -l That's a lower case L

---

### Post by mitchbones on 2008-07-07
> **bumanie said:**
> It would also be helpful to have the output of  That's a lower case L

mitch@mitch-desktop:~$ sudo fdsik -l 
sudo: fdsik: command not found

---

### Post by bumanie on 2008-07-07
Sorry I did a typo > sudo fdisk -l

---

### Post by mitchbones on 2008-07-07
mitch@mitch-desktop:~$ sudo fdisk -l 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88438843

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23703   190394316    7  HPFS/NTFS
/dev/sda2           23704       30401    53801685    5  Extended
/dev/sda5           30293       30401      875542+  82  Linux swap / Solaris
/dev/sda6           30136       30291     1253038+  82  Linux swap / Solaris
/dev/sda7           23704       30134    51656944+  83  Linux

---

### Post by stchman on 2008-07-07
> **mitchbones said:**
> I decided to install the new version of Ubutnu. I decided to delete the old ubuntu partition and just create a new partition with the old space. I believe grub was installed on the one I deleted.

Made a new partition (logical, was that a bad idea?) at the beginning, and then said to install the bootloader on hd0 instead of a specific partition.

Now when I boot up grub doesn't recognize my windows partition.

Thanks.

Edit: Should I reinstall and install grub on one of the partitions instead of "hd0"

The best way to install Ubuntu in a dual boot configuration is to have XP or Vista installed first.

Next use the Ubuntu LiveCD to create unallocated free space.  Use gparted on the LiveCD to accomplish this.

When you install Ubuntu use the use largest continuous free space option.

Let Ubuntu install using the default options.  Ubuntu will install GRUB to the MBR of the boot drive.  GRUB uses a file called menu.lst whichis located in /boot/grub/ in your Ubuntu installation.

When the installation is finished you will have entries for Ubuntu and Windows in a menu.  DO NOT edit the menu.lst by had use StartUpManager in Ubuntu.

```
sudo apt-get install startupmanager
```

To mount the Windows partition you will need to edit your fstab file.

Hope this helps.

---

### Post by bumanie on 2008-07-07
In terminal > sudo grub > root (hd0,6) > setup (hd0) > quitReboot and grub should now recognize windows as being there. For whatever reason, windows was not added to /boot/grbu/menu.lst

---

### Post by mitchbones on 2008-07-07
It didn't work.

```
grub> root (hd0,6) 

grub> setup (hd0) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by bumanie on 2008-07-07
output > cat /boot/grub/menu.lst You could try [super grub disc]("http://geocities.com/supergrubdisk/"), it often fixes grub issues.

---

### Post by mitchbones on 2008-07-07
> **bumanie said:**
> output  You could try [super grub disc]("http://geocities.com/supergrubdisk/"), it often fixes grub issues.


This is the current menu.lst 

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d27dba00-955b-48b4-a620-34a82e0b2aad ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d27dba00-955b-48b4-a620-34a82e0b2aad ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

---

### Post by bumanie on 2008-07-07
Is there any mention of windows? It seems that for some reason grub is not installing to windows mbr, if windows has no entry. Could try manually placing one there. Such as
 
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP 
root        (hd0,0)
savedefault
makeactive
chainloader    +1 This must go under the last entry in the list and **not** inside the existing area where ubuntu is entered. To edit the list by cutting/pasting the above > gksudo gedit /boot/grub/menu.lst but first backup present list > sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup After editng make sure you save the changes. If there is a windows entry, post it so that someone can look at the partition/drive numbers grub has allocated.

Hope this works. I am at work and have to do things so can't assist further, but there are plenty of others on the forum who can help and you can try super grub disk.

---

### Post by kansasnoob on 2008-07-07
> This is the current menu.lst

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d27dba00-955b-48b4-a620-34a82e0b2aad ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d27dba00-955b-48b4-a620-34a82e0b2aad ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet
__________________
Converted to Ubuntu on 12/4/06 

That shows you have no Microsoft Windows left.

Can you go to System > Administration > Partition Editor and send a screenshot?

Like this:

[ATTACH]76788[/ATTACH]

In Hardy you may have to go to Synaptic and install 

> gparted

first. Make no changes! Just send a screenshot by going to Accessories > Take Screenshot.

---

### Post by mitchbones on 2008-07-07
[http://i28.tinypic.com/2wd7lsk.png](http://i28.tinypic.com/2wd7lsk.png)

I tried reinstalling Ubuntu to see if that fixed anything. I realized i didn't set the ntfs partition mount point as "/windows" I tried but it failed.

Edit: On the information about the ntfs partition it says "Unable to read the contents of this file system."

---

### Post by kansasnoob on 2008-07-07
OK, I know people are laughing at me in the background, but just try installing > startupmanager from synaptic.

Then go to System > Administration  > Startup Manager and see if Windows even shows up like this:

[ATTACH]76804[/ATTACH]

You'll have to click on the default OS tab.

If it doesn't then we somehow need to change (boot) or (mount) but I'd have to study more.

BTW, you would have been better off leaving the new partition "blank, aka unformatted" rather than selecting "logical". It's difficult to explain, but an OS lives better on a primary partition. But you can only have 4 prinmary partitions on any one hard drive ............... but that doesn't matter right now. Suffice it to say Ubuntu will do it's own formatting.

---

### Post by kansasnoob on 2008-07-07
Is your Win OS Vista?

If so did you shrink it with Gparted?

---

### Post by bumanie on 2008-07-07
mitchbones, that was going to be my next question as to whether A) Was windows still there or B) that the mbr must be corrupt. Unfortunately it is A). You can try and recover what you have lost with ntfsprogs and use ntfsundelete. That needs to be done from a live cd and the recovered partition needs to be saved to another partition/drive. Look up the documentation on ntfsprogs and to install it > sudo apt-get install ntfsprogs Of course if your windows data was not important reinstall windows to the now blank partition and then reinstall grub off the live cd as described earlier. Sorry you have lost windows.

---

### Post by kansasnoob on 2008-07-07
Look here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by kansasnoob on 2008-07-07
Bumanie,

I personally wouldn't give up just yet.

---

### Post by mitchbones on 2008-07-07
Thanks for all the help guys (Especially) bumanie. I'm just going to reformat my entire computer. I have been thinking about doing it for months and I am of the opinion that the ntfs may be corrupt.

Sorry for all the hassle.

---

### Post by bumanie on 2008-07-07
That's why I suggest ntfsundelete, there is no windows files left on sda1, just an empty partition. The only hope is to undelete/recover the lost partition. There are a number of tools that can do it. As mitchbones has a working ubuntu, ntfsprogs is probably the easiest to try.

---

### Post by kansasnoob on 2008-07-07
One option of many:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It requires a bit of study!

---

### Post by bumanie on 2008-07-07
> **mitchbones said:**
> Thanks for all the help guys (Especially) bumanie. I'm just going to reformat my entire computer. I have been thinking about doing it for months and I am of the opinion that the ntfs may be corrupt.

Sorry for all the hassle.

No hassle. Forum members try to help out when they can. If you do format and reinstall, it is easier to have windows on the first partition. It is up to you, but personally I try to stay away from extended partitions as they are limiting as to what you can do with the partitions (ie resize etc) - it's ok for swap to be in a extended partition. I always manually partition at the partitioning stage, because then one can set up a / a swap and a separate /home that way. That way if something goes wrong with the ubuntu binaries etc., one can reinstall to / without harming saved data in/home. Suggest / - 8-10g; swap 1-2g and /home as large as you like. Hope it all goes well. Post again if you need help.

---

### Post by kansasnoob on 2008-07-07
Better yet:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by kansasnoob on 2008-07-07
> **mitchbones said:**
> Thanks for all the help guys (Especially) bumanie. I'm just going to reformat my entire computer. I have been thinking about doing it for months and I am of the opinion that the ntfs may be corrupt.

Sorry for all the hassle.

I wish you'd read on! It's not necessary!

You could save hours!!!!!!!!!11

---

### Post by kansasnoob on 2008-07-07
And, my apologies, I was thinking XP!

I made an assumption and I was wrong!

I could have shortened this process by simply asking, "XP or Vista"?

](*,)

I messed up!

---

