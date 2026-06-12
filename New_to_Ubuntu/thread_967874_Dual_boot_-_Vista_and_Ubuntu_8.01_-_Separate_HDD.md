---
title: "Dual boot - Vista and Ubuntu 8.01 - Separate HDD"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by bfeero on 2008-11-02
Hi,

I have two separate HDD's on my computer.  On the first, (the one that boots by default) I have Vista installed.  On the other, I have Ubuntu 8.  If I unplug the Vista HDD, ubuntu starts fine.  If I unplug the Ubuntu HDD, Vista starts fine.  If both are plugged in, Vista boots up.

Is there an easy way to get a dual boot setup working?  My current plan is this:
1) Switch the HDD cables so that my computer will boot from Ubuntu by default.
2) ??? What to do next?  I want GRUB to automatically boot into Windows if I power on and do nothing.

Thanks, Brett

---

### Post by caljohnsmith on 2008-11-02
You should be able to just go into your BIOS and change the boot order so that the Ubuntu drive boots first on start up, then it is really easy to add an entry in your Grub menu to boot Vista. If you open a terminal (applicaitons > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
That should pull up your menu.lst. At the very end, add:
```
title	   Windows Vista
rootnoverify     (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And that should be all it takes to boot Vista; if you run into problems, let me know, otherwise let me know how it goes. :)

---

### Post by bfeero on 2008-11-02
Well, I tried that, and this is what I get when I choose Windows from the GRUB loader:

Starting Up...
_

And it hangs forever.
This is what I've added to my menu.lst


```
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Windows Vista x64
rootnoverify	(hd1)
map		(hd0)	(hd1)
map	 	(hd1)	(hd0)
chainloader	+1
```

What should I do?

P.S. I'm running Ubuntu 8.04, not 8.01.

---

### Post by caljohnsmith on 2008-11-02
OK, how about first posting:
```
sudo fdisk -lu

```
And we can work from there.

---

### Post by bfeero on 2008-11-02
fdisk -lu:

```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3f850b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   398267414   199133676    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   378635984   189317961   83  Linux
/dev/sdb2       378635985   390716864     6040440    5  Extended
/dev/sdb5       378636048   390716864     6040408+  82  Linux swap / Solaris
```

---

### Post by caljohnsmith on 2008-11-02
That sounds suspiciously like a BIOS problem, because that Grub entry I gave you for Vista should work; and Grub obviously does boot Vista since you get the "starting up..." message. If you keep the Ubuntu drive connected, and set your BIOS to boot the Vista drive first on start up, does Vista boot OK?

---

### Post by funchords on 2008-11-02
When you installed Ubuntu, did you have the Windows disk disabled in BIOS?

---

### Post by bfeero on 2008-11-02
All,
When I change the boot order, Vista boots up fine.  And when I installed Ubuntu, I simply unplugged the Vista drive.

-Brett

---

### Post by bfeero on 2008-11-02
I'm not quite sure if this helps, but here's something new:

I can access the Vista drive by going to places->VISTA.
When I click on this icon, it prompts me for a password.  I'm not sure if this is my linux password or an administrator password for Vista, because they're the same.

---

### Post by caljohnsmith on 2008-11-02
Since you can boot your Vista drive fine on start up if it is first in the boot order, I think the problem of booting Vista from Grub is most likely a BIOS issue; how about going into your BIOS settings, and try changing the settings related to your HDDs one-by-one, such as "auto-detect", LBA, CHS, RAID, AHCI vs. IDE, ACPI, DMA, etc. Reboot to your Ubuntu drive each time and see if that changes anything when you boot Vista from Grub. I would also recommend writing down the settings that you change so you can always revert back if necessary. Let me know how it goes.

---

### Post by meierfra. on 2008-11-02
Try

title	   Windows Vista
rootnoverify     (hd1,0)
chainloader +1


and

title	   Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

---

### Post by DragonVengeance on 2008-11-02
title Windows Vista
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

works perfectly...if anyone else has this problem, go with that!!!...thanks meierfra

---

