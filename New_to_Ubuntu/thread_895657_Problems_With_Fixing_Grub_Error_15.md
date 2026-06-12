---
title: "Problems With Fixing Grub Error 15"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by ThePerm on 2008-08-20
I've been having some problems switching around some operating systems around on my disks. I have Ubuntu Hardy on the drive that is set as the first drive to boot from in BIOS which is booting fine and brings up the bootloader menu fine also (so I figure it's sumpthin' in the menu.lst), And I also have Ubuntu Hardy with Ubuntu Studio packages on the second drive and Windows XP on the third. Each OS on each drive is the frontmost partition. Hardy on the initial drive is booting fine,

XP on the third is also booted from the menu fine also, but Ubuntu on the second drive comes up with a Grub Error 15 which I understand to be a kernel file not found or something like that? But as far as I can tell in examining my menu.lst I'm not sure I can see any problems with the file it's pointing to, they seem to exist just fine so I figure it's sumpthin' else that's the matter but I can't figure it out.

Here's my device map:
[INDENT][I]
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc[/I][/INDENT]

And here's my menu.lst:

[INDENT][I]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=1be2676b-3093-4d9b-8888-5754155800ed ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1be2676b-3093-4d9b-8888-5754155800ed ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1be2676b-3093-4d9b-8888-5754155800ed ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=a5926bc6-1eed-4149-9fcc-6e787c46c8d6 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=a5926bc6-1eed-4149-9fcc-6e787c46c8d6 ro single 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5926bc6-1eed-4149-9fcc-6e787c46c8d6 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a5926bc6-1eed-4149-9fcc-6e787c46c8d6 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a5926bc6-1eed-4149-9fcc-6e787c46c8d6 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a5926bc6-1eed-4149-9fcc-6e787c46c8d6 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1[/I][/INDENT]

And here's what typing ls in to terminal produces in the /boot directory of the second drive, the one with the Ubuntu kernels that aren't working right:

[INDENT][I]abi-2.6.22-14-generic             initrd.img-2.6.24-19-rt
abi-2.6.24-19-generic             initrd.img-2.6.24-19-rt.bak
config-2.6.22-14-generic          memtest86+.bin
config-2.6.24-19-generic          System.map-2.6.22-14-generic
config-2.6.24-19-rt               System.map-2.6.24-19-generic
grub                              System.map-2.6.24-19-rt
initrd.img-2.6.22-14-generic      vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-19-rt
initrd.img-2.6.24-19-generic.bak[/I][/INDENT]

The menu comes up with three different kernels to boot from the second drive and none of them seem to work but I think the rt one is the one I specifically want to work out of all of them 'cause that's the one I used to use before I managed to mess it up.

Any help? Hope my mucked up explanation of my drive structure makes sense.

---

### Post by pauper on 2008-08-20
> 15: File not found
This error is returned if the specified file name cannot be found, but
everything else (like the disk/partition info) is OK.
[Source.](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)

Compare UUID numbers in /boot/grub/menu.lst and /etc/fstab.

Check if GRUB matches all /boot entries against menu.lst.
Reboot. Press Esc at GRUB menu, then "c". To exit back to menu press Esc.

An example:
```
grub> find /boot/vmlinuz-2.6.22-14-generic   
 (hd1,0)

grub> find /boot/initrd.img-2.6.22-14-generic
 (hd1,0)

grub> null (hd1,0)/boot/vmlinuz # Press <Tab>
...
grub> null (hd1,0)/boot/initrd.img # Press <Tab>
...
grub> cat (hd1,0)/boot/grub/menu.lst
...
```

Finally try booting manually.

Note: "root=" argument past the "kernel" statement is the partition containing
/sbin/init
```
grub> root (hd1,0)
grub> kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sdb1
grub> initrd /boot/initrd.img-2.6.24-19-generic
grub> boot
```

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
[http://forums.gentoo.org/viewtopic-t-122656.html](http://forums.gentoo.org/viewtopic-t-122656.html)

---

### Post by markbuntu on 2008-08-20
That doesn't work for me, I get grub error 15 with the i386 -19rt -20rt and-21rt kernels on my machine and trying to boot in recovery also gives error 15 and booting manually just hangs. The generic kernel boots just fine. The only difference in the grub lines is the rt. I never got any errors during the update/installs. Just no boot. This is definitely not a grub problem.

There is something wrong with the i386 rt kernel that may be machine specific because I have an amd64 UbuntuStudio install on the same machine and the same rt kernels boot just fine.

I have a three year old HP media center with a ASUS mobo, AMD64 3800+ cpu, 2GB ram, ATI HD3650 graphics card, and a whole bunch of other crazy stuff, 4hard drives, a SATA card, A SIIg PCI 7.1 sound card, Realtec ethernet card, 24 and 19 inch monitors blah blah blah... The only problem I have had recently with Ubuntu is the i386rt kernel and is the reason I switched my amd64 install to UbuntuStudio.


My suggestion, If you really need the rt, use the amd64 distro if your processor is 64 bit. Also, you can try the generic kernel.

---

### Post by ThePerm on 2008-08-22
So hang on, I'm sposed to type those code segments in to Grub as command upon boot up? What do they do I'm not totally sure I understand your help?

But it might not even be a solvable problem?
My rt kernel was booting totally fine until I tried switching around the OS's on my drives. I did have 64bit Ubuntu on my first drive before and they all booted just fine from the menu.
And I really don't wanna change distros on my second drive (the one that's not booting right) 'cause I really don't wanna format it if I can help it. =/

Pardon my newbyness, I am rather confused.

---

### Post by caljohnsmith on 2008-08-22
Please clarify: you said your Ubuntu Studio was on your 2nd HDD, but your menu.lst shows your realtime (rt) kernels are on your first HDD (hd0,0). Aren't your rt kernels on your Ubuntu Studio HDD? Because if that is true, it appears you may actually be booting from your Ubuntu Studio HDD, since the rt kernel entries in your menu.lst use (hd0,0) and not (hd1,0). 

Just to clear things up, please post the output of the following:
```
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdc  bs=1 skip=1049 count=2 | hexdump
sudo fdisk -lu
sudo blkid
sudo grub
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
grub> find /boot/initrd.img-2.6.24-19-generic
grub> find /boot/vmlinuz-2.6.24-19-rt
grub> quit

```

---

### Post by ThePerm on 2008-08-22
Yeah that confused me a lil but sumpthin' told me it was normal, forget what gave me that sense though.
Seeing as the two sections of the menu.lst that point to Ubuntu kernels are pointing to different drives though shouldn't I be unable to boot the Ubuntu on the first drive? And wouldn't all my settings and documents be in my home folder upon this boot? My GOD I'm bad at articulating this stuff.

Regardless here's the results of the commands you requested:

```
theperm@ThePerms-Virtual-Chillax-Pad:~$ sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 8100                                   
0000002
2 bytes (2 B) copied, 0.000200425 s, 10.0 kB/s
theperm@ThePerms-Virtual-Chillax-Pad:~$ sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 ff00                                   
0000002
2 bytes (2 B) copied, 0.00675972 s, 0.3 kB/s
theperm@ThePerms-Virtual-Chillax-Pad:~$ sudo dd if=/dev/sdc  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 0000                                   
0000002
2 bytes (2 B) copied, 0.00020794 s, 9.6 kB/s
theperm@ThePerms-Virtual-Chillax-Pad:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00099993

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   468664244   234332091   83  Linux
/dev/sda2       468664245   488392064     9863910    5  Extended
/dev/sda5       468664308   488392064     9863878+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bc0a205

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   149838254    74919096   83  Linux
/dev/sdb2       149838255   156296384     3229065    5  Extended
/dev/sdb5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80498049

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   488375999   244187968+   7  HPFS/NTFS
theperm@ThePerms-Virtual-Chillax-Pad:~$ sudo blkid
/dev/sda1: UUID="a5926bc6-1eed-4149-9fcc-6e787c46c8d6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="2d01caf9-b51d-4e65-af3b-0e7677283bad" 
/dev/sdb1: UUID="1be2676b-3093-4d9b-8888-5754155800ed" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="71f40274-c678-4f63-b537-39c1bff13587" 
/dev/sdc1: UUID="44CC0B4ECC0B3A26" TYPE="ntfs" 


grub> geometry (hd0)
drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> geometry (hd1)
drive 0x81: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> geometry (hd2)
drive 0x82: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> find /boot/initrd.img-2.6.24-19-generic
 (hd0,0)
 (hd1,0)

grub> find /boot/vmlinuz-2.6.24-19-rt
 (hd0,0)

```


Hope that explains more than I do! xD

---

### Post by pauper on 2008-08-22
> **ThePerm said:**
> What do they do I'm not totally sure I understand your help?

It's a simple check to see if there are any mistakes in your menu.lst file:
some bogus partition, misspelled names, wrong paths. GRUB will print all it
can find, then you compare that with your menu.lst entries.

If the error implies that "File not found", then you're better off checking all
that.

---

