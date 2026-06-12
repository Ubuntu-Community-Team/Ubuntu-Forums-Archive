---
title: "HOWTO: Add SATA support for bootup ntfs mounting"
date: 2005-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jackmacokc on 2005-04-27
I know I'm not the only one who has this type of config: ATA/133 drive hosting hoary, SATA drive hosting WinXP (On a Dell if you must know, so ATA/133 is considered master of this config.)

The problem:

When trying to mount /media/windowsC at bootup with the mountall script, an error message is received. This apparently happens because the SATA drive support is not loaded until *after* mountall is already ran.

In my situation, my regular ata drive is considered drive 0. my sata drive is considered drive 1. so ubuntu doesn't want to load support for drive 1 out of the box. this may not happen if the SATA drive is your primary drive. I think this only happens when your primary drive is PATA.

The fix:
Compile a custom kernel with support for SATA drives built in

OR

edit your /etc/mkinitrd/modules file and add these lines to the end:

```
ata_piix
libata
sd_mod
scsi_mod
``` 

now make a new init ramdisk

```
sudo mkinitrd -o /boot/initrd.img-<your version>.custom <your version>
``` 

Replace <your version> with your kernel version by using uname -r

After that is done, edit your grub menu list and add the custom ramdisk you just made:

sudo nano /boot/grub/menu.list

Change your first entry to have the ramdisk you just made. Viola!


For reference, here's my fstab, menu.lst, and modules file:

```
# /etc/mkinitrd/modules: Kernel modules to load for initrd.
#
# This file should contain the names of kernel modules and their arguments
# (if any) that are needed to mount the root file system, one per line.
# Comments begin with a `#', and everything on the line after them are ignored.
#
# You must run mkinitrd(8) to effect this change.
#
# Examples:
#
#  ext2
#  wd io=0x300
ata_piix
libata
sd_mod
scsi_mod

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-686-smp.custom
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-686-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686-smp.custom
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686-smp
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-686-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686-smp
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda1	/media/windowsC	ntfs	umask=0222	0	0
/dev/sda2	/media/windowsD	ntfs	umask=0222	0	0

```

Thanks to zerokarmaleft for all his help in figuring this out. Just wanted to post in case someone else runs into this situation.

---

### Post by bored2k on 2005-04-27
Moved this to Tips and Tricks ;).

---

### Post by Balki on 2005-05-13
This easier method worked for me:

Just add the required kernel modules (in my case sata_sil) to /etc/modules

---

### Post by dbloom on 2005-06-02
balki, can you expand on that a little?  

1) is 'sata_sil' a silicon graphics module? i think i have a 3112 chip and i'm curious whether i would need that one too.

2) when i open my /etc/modules file in gedit, it looks completely garbled.  where exactly do you put 'sata_sil'?

thanks.

--db

---

### Post by deBaas on 2005-06-09
[QUOTE=Balki]This easier method worked for me:
Just add the required kernel modules (in my case sata_sil) to /etc/modules[/QUOTE]

Seems like this is the best option, it works for me!

Motherboard: Asus A7N8X-E Deluxe (nForce2 with Silicon Image 3112 sata controler)
Ubuntu on PATA disk /dev/hda
/home mounted on SATA disk /dev/sda1

thanks Balki!

---

### Post by shakin on 2005-06-25
I just found a better resource and I'm sure many people are still wondering how to do this. Basically, you need to add the right module to /etc/modules, but which is the right one?

I think you almost always need to add 'libata' to get things started, but for most chipsets you also need to add an appropriate low-level driver from the list below. Please post if you have corrections as I made best guesses and used google searches to find out which chipsets each driver supports.

sata_via - VIA chipsets (KT600, KT800, etc)
sata_nv - Nforce 3 (and 2?) chipsets
ahci - Intel ? and other ahci conforming chipsets
ata_adma - Pacific Digital and other adma conforming chipsets
ata_piix - Dell Poweredge and others.
sata_promise - Most Promise chipsets
sata_sil - Silicone Image chipsets (Nforce 2?)
sata_sx4 - Promise FastTrak S150 SX4
sata_svw - PowerPC G5
sata_vsc - Vitesse VSC7174 ? (Some Dells)

So to summarize, to get your SATA drives mounted on boot you'll need two lines added to /etc/modules: libata and the driver from the list above that corresponds to your SATA controller.

Hopefully this list helps a few people as it took me a while to get my VIA chipset working.

---

### Post by Zillion on 2005-09-12
Sry I am new to linux...

I can automount my ide drive on boot but I can mount my sata drive in Hoary only manually

I have Nforce4 chipset so I guess I need to add sata_nv

if I add these 2 lines in my /etc/modules 
libata
sata_nv

it still cant automount on boot. what am I doing wrong / forgetting? tx

my modules file :

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
libata
sata_nv

---

### Post by jackmacokc on 2005-10-16
[QUOTE=Zillion]Sry I am new to linux...

I can automount my ide drive on boot but I can mount my sata drive in Hoary only manually

I have Nforce4 chipset so I guess I need to add sata_nv

if I add these 2 lines in my /etc/modules 
libata
sata_nv

it still cant automount on boot. what am I doing wrong / forgetting? tx

my modules file :

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
libata
sata_nv[/QUOTE]

According to the list above, it looks like you need a different module.

---

