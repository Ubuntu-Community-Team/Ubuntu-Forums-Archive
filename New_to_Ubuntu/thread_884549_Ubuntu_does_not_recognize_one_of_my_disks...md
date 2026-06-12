---
title: "Ubuntu does not recognize one of my disks.."
date: 2008-08-09
forum: New to Ubuntu
---

### Post by garyl on 2008-08-09
Hello all - 

I've just installed Ubuntu for the first time, replacing Windows.  For some reason Ubuntu does not 'see' one of the two hard disks installed in my machine. I can't access it at all. The partition editor only recognizes one disk, but unfortunately most of my data and files are on the other one. 

Any help will be much appreciated.  I definitely don't want to go back to Windows but I need to be able to access both disks.

---

### Post by starcannon on 2008-08-09
What file system is on the other disk? NTFS? fat32? or other?

Strange that its not seeing it, likely that it is, but since your not used to linux file browsers you could be looking in the wrong place.

Either way I'm sure one of us can help you locate your files.

---

### Post by Elfy on 2008-08-09
It might help to open a terminal (in accessories) and run this command - it will ask for password - use your normal one, but be aware it won't show as you type it. Paste the output into a new post.

```
sudo fdisk -l
```

---

### Post by coffeecat on 2008-08-09
Also - check in the BIOS that the BIOS is seeing both discs.

If it is, then try what forestpixie suggests. By the way, when you highlight, copy and paste into the message board from the terminal, use the edit menu - keyboard shortcuts are different in the terminal.

---

### Post by starcannon on 2008-08-09
Ctrl-C to copy from regular programs, like Firefox

Shift-Ctrl-V to paste into the terminal (just add a shift key to the regular copy/cut/paste keys when working in terminal)

---

### Post by coffeecat on 2008-08-09
> **starcannon said:**
> Ctrl-C to copy from regular programs, like Firefox

Shift-Ctrl-V to paste into the terminal (just add a shift key to the regular copy/cut/paste keys when working in terminal)

Actually, the OP will want to do it the other way around. :) Output of fdisk > firefox. I should have been clearer and said 'use the edit menu **in the terminal**'. But thanks for clarifying what I posted.

---

### Post by starcannon on 2008-08-09
> **coffeecat said:**
> Actually, the OP will want to do it the other way around. :) Output of fdisk > firefox. I should have been clearer and said 'use the edit menu **in the terminal**'. But thanks for clarifying what I posted.

Lol sorry, I prolly just added confusion.

OP: Anyway the jist(or jest as the case may be) of it is, in normal everyday programs CTRL-X/C/V act normally, in a terminal add the SHIFT key.

Hope I didn't cause more harm than good.

---

### Post by Elfy on 2008-08-09
Although it might be useful for the op to know about pasting with the middle button, if his mouse has one. Highlight with mouse text to copy and then when you are in the post - click with middle button.


> Also - check in the BIOS that the BIOS is seeing both discs.I spent 2 hours fiddling about until I remembered to check in BIOS that the disc was recognised - I'd managed to install to it but grub wouldn't work :)

---

### Post by garyl on 2008-08-09
Thanks - ran fdisk -l and here is the result: 

gary@gary-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73da73da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  83  Linux
/dev/sda2             123        9729    77168227+   f  W95 Ext'd (LBA)
/dev/sda5            5100        6119     8193118+   b  W95 FAT32
/dev/sda6            6120        6145      208813+  83  Linux
/dev/sda7            6146        9729    28788448+   b  W95 FAT32
/dev/sda8             123         487     2931799+  82  Linux swap / Solaris
/dev/sda9             488        5099    37045858+  83  Linux

Partition table entries are not in disk order
 
The second disk of about 120 Gigabytes, still seems to be out to lunch.

---

### Post by Elfy on 2008-08-09
Is BIOS recognising it.

---

### Post by garyl on 2008-08-09
Yep. Bios recognizes it as a secondary master.  It's an ordinary Western Digital disk, nothing exotic.

---

### Post by Elfy on 2008-08-09
Well not sure then - I did have a problem where the disc was seen on the main BIOS page but the Access Mode needed to be changed to Auto, then it was seen without any problem.

But it appears to be a bit odd  that the disc worked ok with win and isn't seen at all by ubuntu or gparted, have you tried with bootable editor like partedmagic or gparted or the one on the buntu livecd.

---

