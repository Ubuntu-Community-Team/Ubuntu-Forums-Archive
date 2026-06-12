---
title: "boot windows using grub"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by kastad on 2008-07-11
Hi!

Recently I had both windows and ubuntu on my computer, and booted by using grub. By accident I destroyed my windows partition, and now I am not able to reinstall it. I have tried to alter the menu.lst file in my grub directory with help from google, but this doesn't work. Here is the lst-file:


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a2fbdc97-007e-4c20-95b7-d4f862fd3812 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a2fbdc97-007e-4c20-95b7-d4f862fd3812 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
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

title 		CDROM

root		(hd0,0)
kernel 		/boot/grub/memdisk.bin
initrd 		/boot/grub/sbootmgr.dsk

# This finds and loads SETUPLDR.BIN in /I386
# searching it in all available drives in the order (fd) - (hd) - (cd)
title Boot SETUPLDR.BIN
find --set-root /I386/SETUPLDR.BIN
chainloader /I386/SETUPLDR.BIN

# This loads SETUPLDR.BIN in (cd)/I386
title Boot SETUPLDR.BIN from (cd)
root (cd)
chainloader /I386/SETUPLDR.BIN

# This loads SETUPLDR.BIN in (cd0)/I386
#Only try this if device (cd) is not already available
title Boot SETUPLDR.BIN from (cd0)
cdrom --init
map --hook
root (cd0)
chainloader /I386/SETUPLDR.BIN

The last five alternatives doesn't work. Can anyone help me?

---

### Post by fatality_uk on 2008-07-11
When you say "destroyed" your Windows partition, do you mean you formatted/erased it?

---

### Post by hyper_ch on 2008-07-11
post the output of
```

sudo fdisk -l

```

and when posting some output or something use those

[noparse]```

```[/noparse]

brackets around the output

---

### Post by kastad on 2008-07-11
I "destroyed" the windows partition by trying to install a new os there. I thought it was a usb disk... 

Fdisk gives this:

```


Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01880187

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1711    13743576    7  HPFS/NTFS
/dev/sda2            1712        8893    57689415    f  W95 Ext'd (LBA)
/dev/sda3            8894        9733     6747300   83  Linux
/dev/sda5            1712        8893    57689383+   7  HPFS/NTFS


```

---

### Post by sargetech on 2008-07-11
Sorry Dude I think That partition is Toast!!!!
I think you confused drive letters!!!! and erased the wrong drive!!
It can happen!!!!:( A fresh install is needed!!!

---

### Post by hyper_ch on 2008-07-11
you have a windows install cd?

---

### Post by kastad on 2008-07-11
yes, I have a windows cd, but the grub thing won't allow me to boot from this cd

---

### Post by hyper_ch on 2008-07-11
you need to set your bios to boot from cd first and harddisk second... that way you should be able to boot from the cd.

---

### Post by kastad on 2008-07-11
I already have, but it doesn't work

---

### Post by hyper_ch on 2008-07-11
then you don't have a windows install cd

---

### Post by kastad on 2008-07-11
But it is, it works fine on my mothers windows computer. :confused:

---

### Post by hyper_ch on 2008-07-11
then there is something wrong with your bios settings

---

### Post by upchucky on 2008-07-11
are you able to get into your bios?

some have a key to press that interrupts the post and lets you into the bios, some of mine are esc, f12, f1,f2, and f8. on some systems the key to press flashes on the screen very fast in the upper right corner, and some motherboards are set to not show the key on boot, googling the board will get you the info you need. 

if you cant get into the bios that way, disconnect the hard drive, then boot it may default you into the bios.

if the bios is password protected and is unknown, then removing the cmos battery will reset the bios to default settings, on most modern systems this is not a problem, but on some systems, the "post" when you try to reboot will not have the hard drive specs and you will need to find and manually enter the drive specs. as well a few other bios settings may need resetting. google the system motherboard and drive before going down this path to make sure you have everything you need first.

I take no responsibility for mistakes you may make, and have only posted this here because it is a solution that with proper understanding by reading all information about the system, it is repairable.

In short, make sure you read and understand what you are doing before attempting the above, when done right it will work.

---

### Post by kastad on 2008-07-12
Actually, I made a mistake while checking the windows cd. It isn't able to boot with it. I tried on another computer. Then it seems I have to find a new CD.

---

