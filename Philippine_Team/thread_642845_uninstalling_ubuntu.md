---
title: "uninstalling ubuntu"
date: 2007-12-17
forum: Philippine Team
---

### Post by traxid on 2007-12-17
my PC had  a 80 GB PATA where my windows xp is installed, and a 160 GB  SATA where the ubuntu 7.10 is installed( partitioned into 80 GB FAT 32 and the other 80 GB as ext3 for ubuntu,(my windows xp can not recognize this format) however ubuntu can not detect the number keypad and the arrow keys,that's why upon booting i have only 1 choice to boot from( ubuntu only coz i can't move the selection using the arrow keys)
how can i uninstall my ubuntu and the GRUB and recover the space partitioned for ubuntu, thanks

---

### Post by SteveHillier on 2007-12-17
The question to ask is "Why can't you move your cursor on boot up?"

---

### Post by traxid on 2007-12-17
i dont know why my cursor my cursor doesn't move( durnig booting up to select which OS to use) it's the same problem my brother encountered it in his PC

---

### Post by traxid on 2007-12-17
others said that ill run my recovery cd then use fixmbr, ive tried that thing but the problem is that my PC has no floppy disk drive

---

### Post by jmazaredo on 2007-12-17
if you want to remove the ubuntu bootup in the hard drive fastest way is boot a windows xp cd and format.

Another option slave the hard drive on a windows xp system, look for a free program to edit the mbr of the drive where ubuntu is installed and copy the mbr of windows xp system to the mbr where the ubuntu is installed.

:guitar:

---

### Post by SteveHillier on 2007-12-18
> **jmazaredo said:**
> if you want to remove the ubuntu bootup in the hard drive fastest way is boot a windows xp cd and format.


But don't do this until you have made sure you can reinstall all programs and recover all user data.

---

### Post by Tom Mann on 2007-12-18
Do you have a USB keyboard? Go into the BIOS and make sure 'Legacy USB emulation' (or something similar) is enabled otherwise your keyboard will not be detected by the BIOS at startup, and unavailable to the system until an operating system is booted (hence why you cannot select anything on the boot menu)

Tom

---

