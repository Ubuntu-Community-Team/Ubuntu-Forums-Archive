---
title: "GRUB &amp; Wubi Don't work"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Ubangi on 2008-04-27
I have mentioned the GRUB problem before in the "Ubuntu AMD64 Fails to Install Thread", without any comments being raised. 

I have now managed to install off the CD by using F6 and some magical incantations boot options but I still have the GRUB problem and it has now got worse.

Since my hard disk Ubuntu desktop installation has finally succeeded, I have now uninstalled Wubi from Vista but I still have two ubuntu entries in the boot menu and neither of them now works. I need some help please with resetting the GRUB. Bear in mind that my Ubuntu no longer boots up. Vista remains the only operating system that still boots up after all this....

Anyway, there is a definite issue with wubi not using the Grub properly and leaving it in a sorry state. On wubi installation, it writes in wrong disk numbers so the installation fails to boot up and on uninstallation it kills the proper Ubuntu as well but still leaves the GRUB and both now defunct entries in it. What a balls up...

---

### Post by Tatty on 2008-04-27
Can you boot to a live cd then post the output of:

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

---

### Post by overdrank on 2008-04-27
> **Ubangi said:**
> I have mentioned the GRUB problem before in the "Ubuntu AMD64 Fails to Install Thread", without any comments being raised. 

I have now managed to install off the CD by using F6 and some magical incantations boot options but I still have the GRUB problem and it has now got worse.

Since my hard disk Ubuntu desktop installation has finally succeeded, I have now uninstalled Wubi from Vista but I still have two ubuntu entries in the boot menu and neither of them now works. I need some help please with resetting the GRUB. Bear in mind that my Ubuntu no longer boots up. Vista remains the only operating system that still boots up after all this....

Anyway, there is a definite issue with wubi not using the Grub properly and leaving it in a sorry state. On wubi installation, it writes in wrong disk numbers so the installation fails to boot up and on uninstallation it kills the proper Ubuntu as well but still leaves the GRUB and both now defunct entries in it. What a balls up...

Hi and have you tried to reinstall the grub via the live cd
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Oldsoldier2003 on 2008-04-27
I'm under the impression that grub and wubi are mutally exclusive since wubi uses the windows bootloader to launch ubuntu installations that are wubi installed.

---

### Post by Ubangi on 2008-04-27
Tatty, thanks for looking into this.

Here is my fdisk -l output:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000370df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18728   150432628+  83  Linux
/dev/sda2           18729       19457     5855692+   5  Extended
/dev/sda5           18729       19457     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x409a4099

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       20023    78911280    b  W95 FAT32


As to the grub menu list, being on live-cd session, it was not in /boot/... but I found it in /media/disk/boot/grub/menu.lst. I will assume that is the one you need, so here it is:

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
# kopt=root=UUID=8c28a165-0b2c-46d1-904c-f0d8aed7b897 ro

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
# defoptions=quiet splash all_generic_ide floppy=off irqpoll

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8c28a165-0b2c-46d1-904c-f0d8aed7b897 ro quiet splash all_generic_ide floppy=off irqpoll
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8c28a165-0b2c-46d1-904c-f0d8aed7b897 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Overdrunk, thanks, this might well do it but I don't trust it anymore. If something is wrong again and I loose Vista as well, I am truly screwed...

---

### Post by Ubangi on 2008-04-27
Overdrunk, thanks for the link, I finally plucked up the courage to mess around with the GRUB and followed the procedure in the link but to no effect.

However, putting one and one together with Oldsoldier's comment, I realise now that it is still the Windoze boot loader that is coming up, despite the wubi being uninstalled and Grub being installed. The windoze boot loader refuses to revert to its original simple form with Vista only, and it is making Grub invisible.

So, my real question now is this. Is there a way of restoring the windoze boot loader to its state prior to wubi installation(s), under VISTA amd64? I have tried before with all the known windoze methods fdisk /mbr etc. but failed miserably. Do I have to live with it in its corrupted state forever, and never even see the Ubuntu I had so laboriusly installed?

I have ubuntu (and presumably Grub) on hd0,0 and Vista and windoze boot loader on hd1,0

---

### Post by Ubangi on 2008-04-27
Having got this far, I tried F11 while booting and then I chose the other disk and found the hidden GRUB and booted up to Ubuntu at last.

However, my joy was short lived, as it is incredibly slow, to the point of the mouse being unusable. After a few moments the mouse disappeared alltogether and Ubuntu froze totally, to the extent that I had to pull out the power plug to get my machine back....

Also, I still have no idea if I will ever manage to restore my windoze boot loader. I think wubi ought not leave it like that, when there is no way of fixing it. Not at all nice.

What a disappointment.

---

### Post by Ubangi on 2008-04-27
I have reinstalled from the CD yet again, this time  with F6 and all_generic_ide floppy=off options but not the irqpoll option!

Then I rebooted and hit F11 to choose the right boot loader.

This time, I am actually typing this from 8.04 for the first time!
I might be OK now, provided I remember all these magic incantations and don't ever try to install Ubuntu again, or assume naively that it will work without knowing all these secrets....

---

### Post by overdrank on 2008-04-27
> **Ubangi said:**
> I have reinstalled from the CD yet again, this time  with F6 and all_generic_ide floppy=off options but not the irqpoll option!

Then I rebooted and hit F11 to choose the right boot loader.

This time, I am actually typing this from 8.04 for the first time!
I might be OK now, provided I remember all these magic incantations and don't ever try to install Ubuntu again, or assume naively that it will work without knowing all these secrets....

congrats and glad you got it running   I have no experience with Wubi so I could not help but glad you figured it out and GOOD luck! :KS

---

### Post by Ubangi on 2008-04-28
Thanks overdrunk. I hope for Ubuntu's sake (which I think is a great project) that this kind of fiddling becomes unnecessary in future releases. I was beginning to think that writing my own operating system may have been easier than figuring all this out!

---

