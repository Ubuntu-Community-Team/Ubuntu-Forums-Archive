---
title: "Grub Slip Up"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Pudworthy on 2008-06-23
I feel foolish. And scared...

I was installing a nice pretty GUI to paper over the GRUB cracks, to make it all look nicer. Eventually when I got it to work I found for some reason I can no longer access my second hard drive, which is what my Vista runs from. In addition, i can't load Windows from it either.

Fdisk says this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ecb6b0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ce02cdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14026   112663813+  83  Linux
/dev/sdb2           14027       14593     4554427+   5  Extended
/dev/sdb5           14027       14593     4554396   82  Linux swap / Solaris


Don't know if that's any help, but whatever you can suggest would be most helpful!

P

---

### Post by Duck2006 on 2008-06-23
Post the output of your menu.lst.
In the terminal,

cat /boot/grub/menu.lst

---

### Post by Pudworthy on 2008-06-23
gfxmenu (hd1,0)/home/lloyd/Other/Ubugrey/message.ubugrey
default 0
timeout 30

title Linux Ubuntu 8.04
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=f3e5c4ce-f0e0-483c-9ce5-bdee6dd07f7f ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic

title Linux Ubuntu 8.04 (Recovery Mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=f3e5c4ce-f0e0-483c-9ce5-bdee6dd07f7f ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin

title Other operating systems:

title Windows Vista
root (hd0,0)
chainloader +1
savedefault
makeactive


That what'cha lookin' for?

P

---

### Post by Duck2006 on 2008-06-23
> I can no longer access my second hard drive, which is what my Vista runs from. In addition, i can't load Windows from it either.

With your fdisk -l and your menu.lst win is your first drive.
Change this,

title Windows Vista
root (hd0,0)
chainloader +1
savedefault
makeactive

To this.

title Windows Vista
root (hd0,0)
makeactive
chainloader +1

---

### Post by Pudworthy on 2008-06-23
Ok, I changed it, but it's made no difference. I can't load up Vista from the GRUB, if I try the screen goes blank for a few seconds and then goes back to GRUB again, and the actual drive itself has disappeared from Ubuntu as well, I can't access the files from that drive.

Where's it all gone?

Thanks, P

---

### Post by Duck2006 on 2008-06-23
Witch drive in your BOIS do you have set to boot from?

If it is the second drive then add these lines to your win in your menu.lst

map (hd0) (hd1)
map (hd1) (hd0)

so it looks like this

title Windows Vista
root (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by Pudworthy on 2008-06-23
Ok, I now get an error message when attempting to load Windows:

root (hd0,0)
  filesystem type unknown, partition type 0x7

...followed by the mapping & bootloader details etc.

I still can't get Windows, and I still have no access to that drive from Ubuntu. It's like it's entirely disappeared as a drive from my pc...

Any further suggestions will be implemented tomorrow.

Thanks for the help so far.

P

---

### Post by Duck2006 on 2008-06-23
Some reading on grub that may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You can try super grub disk to fix the problem.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by logos34 on 2008-06-23
If you have the vista installation disc you could try Startup Repair option:
[http://windowshelp.microsoft.com/Windows/en-US/help/5c59f8c1-b0d1-4f1a-af55-74f3922f3f351033.mspx](http://windowshelp.microsoft.com/Windows/en-US/help/5c59f8c1-b0d1-4f1a-af55-74f3922f3f351033.mspx)

---

### Post by Duck2006 on 2008-06-23
If you go that way and recover the mbr for vista. Then try EasyBCD to use as your loader.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Pudworthy on 2008-06-24
Thanks for the help. I used my Windows disk and went to repair... scared the turd out of me 'cos it couldn't see any windows OS there! And there I looked at my C: drive and it said it was blank...

However, I ran repair anyway, and it fixed it perfectly. Didn't even overwrite my GRUB, so now it boots into GRUB and then to whichever system I want, just as I wanted it to before I got into this mess. 

One thing I will say for Microsoft, they may make poor software, but they can fix their own crap really easily and efficiently...

Anyway, back to full strength. Thanks fellas.

P

---

