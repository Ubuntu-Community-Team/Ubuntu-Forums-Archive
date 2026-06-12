---
title: "error 21"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Kmob810 on 2008-05-10
Hi everyone. I am definitely [COLOR="Black"]_**a beginner**_[/COLOR] so non technical help would be appreciated. I have checked through the threads and could not find anything to help me.
I have vista home prem running on a laptop and I have added an external hdd with 360 gb drive. I have partitioned this drive hoping to install Ubuntu to it. I donwloaded 8.04 and installed it to the ext hdd but when I restarted I got this message .... Grub 1.5 error 21. Obviously I am hoping eventually to dual boot Vista & Ubuntu (Ubuntu from the external drive). I have no idea about Grub or how to change it. Can anyone help? please
:confused:

---

### Post by TeoBigusGeekus on 2008-05-10
Open a terminal and post the results of 
```
sudo fdisk -l
```
that's -L.

Also post us the content of your menu.lst file(.LST)
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by spydon on 2008-05-10
He forgot to tell you that you need to boot up the live cd first and then do as he said.

---

### Post by TeoBigusGeekus on 2008-05-10
Oh crap, yeah...
Thanks Spydon!!!
Sorry Kmob810!!!

---

### Post by Kmob810 on 2008-05-10
Thanks guys but as I said I am a complete novice and you were all a bit technical for me!!! also I am using my pc for this thread and my problem is on my laptop so I can;t give the info you are asking for.

---

### Post by TeoBigusGeekus on 2008-05-10
Boot with the live cd on your laptop and type the commands in a terminal.

You can save the outputs in a text file, transfer them with a flash in the pc and post them.

---

### Post by cosine352 on 2008-05-10
I am also new in Ubuntu. I did installed Ubuntu on an external hard drive successfully. Before installing I took the internal hard drive of the notebook out. This way it will write the GRUB in the external hard drive (not in the internal hard drive). 
I am not an expert. I just thought may be this is the cause of the error:confused: ????????

---

### Post by reefsrt4 on 2008-05-10
I just had this same problem as well!!  Got a new desktop with Vista, inserted another 80G HDD so I could instal hardy.  Booted with live CD, used Guided to install to entire 80G HDD.  Now when I boot, I get error 17.....and if I remove the 80G HDD from my dektop I get error 21!

WTF happened.  I successfully installed 7.10 on 3 other computers and never had this problem!!  what do I do now?  I can't even get back into Vista with the 80G HDD out....

---

### Post by Kmob810 on 2008-05-10
ok I have managed to get the sudo fdisk -l information but the contents of /boot/grub/menu.lst was ...... nothing! completely blank. Can you help with the following only?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cc21473

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         702         893     1536000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             893       14594   110050304    7  HPFS/NTFS

Disk /dev/sdb: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3a5adb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       43403   348634566   83  Linux
/dev/sdb2           43404       43777     3004155    5  Extended
/dev/sdb5           43404       43777     3004123+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by TeoBigusGeekus on 2008-05-10
Are you sure? Please recheck and post.

---

### Post by Kmob810 on 2008-05-10
can you give me a brief explanation how to get the /boot/grub/menu.lst? (remember I'm a novice)Thanks

---

### Post by TeoBigusGeekus on 2008-05-10
Ok then.
When you boot up with the live cd, you should navigate with Nautilus to your external hd, where Ubuntu is supposed to be installed. 
In there, there should be a place called filesystem (/). Try to find the folder boot, get inside, and then find the folder grub. In there you should find the file menu.lst. 
Now, copy the full path of the folder grub from Nautilus and paste it in the following command
```
gksudo gedit /full/path/to/menulst/menu.lst
```

---

### Post by annda on 2008-05-10
> **Kmob810 said:**
> 
I have vista home prem running on a laptop and I have added an external hdd with 360 gb drive. I have partitioned this drive hoping to install Ubuntu to it. I donwloaded 8.04 and installed it to the ext hdd but when I restarted I got this message .... Grub 1.5 error 21. Obviously I am hoping eventually to dual boot Vista & Ubuntu (Ubuntu from the external drive). I have no idea about Grub or how to change it. Can anyone help? please
:confused:

it seems to me that during ubuntu install you put GRUB on your internal drive instead of the external one. now every time you boot without the external disk plugged in, GRUB will complain. please plug the ubuntu drive and try booting. this should work.

if it doesn't or if you are not satisfied with this "mode of operation", let us know.

---

### Post by Kmob810 on 2008-05-10
I couldn't find Nautilis but a search brought up the menu.lst :



# sample /boot/grub/menu.lst entry for memtest86
#
# This example 	assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

---

### Post by TeoBigusGeekus on 2008-05-10
That's all?
Then you don't have grub!
Try this link
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
to recover grub.
And if that doesn't work, then you should resort to supergrub disk
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")
Before everything, try what annda posted... and remember to post back your progress.
Good luck!

---

### Post by Kmob810 on 2008-05-10
Annda, I have tried this. Also booting without the external drive connected. I keep getting the same response. error 21

---

### Post by annda on 2008-05-10
ok, this my last shot at the problem: it is very likely that your BIOS has a problem with such a large boot partition.

i know it's a little messy but use the **live cd**'s partition editor (in system > administration) to resize the ubuntu partition to something like 20GB. later, you can format the rest as media strage or something.

---

### Post by dizee on 2008-05-10
When you are booting from the live cd trying to fix the problem, you might first need to mount your Ubuntu partition. Boot from the cd, then open a terminal and type ```
sudo mkdir /ubuntu 
sudo mount /dev/sdb1 /ubuntu
```
Then navigate to the /ubuntu folder and look for menu.lst in /ubuntu/boot/grub/ - use the file browser to do this (click on places then on filesystem).

If you find that post the contents of that file here.

---

### Post by Kmob810 on 2008-05-11
here is the menu.list doc
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
# kopt=root=UUID=3267c507-c746-4dfe-b040-c096e9fe3612 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3267c507-c746-4dfe-b040-c096e9fe3612 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3267c507-c746-4dfe-b040-c096e9fe3612 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by Kmob810 on 2008-05-11
How do I take the internal drive out?

---

### Post by Kmob810 on 2008-05-11
I think maybe it would be a good idea for me to uninstall ubuntu and learne more about it before reinstalling. Is there an easy way to do this bearing in mind the problems I am having? will I be able to boot back into vista easily? thanks for all your help. Just this last query and I will leave you alone!!!!!!!!!

---

