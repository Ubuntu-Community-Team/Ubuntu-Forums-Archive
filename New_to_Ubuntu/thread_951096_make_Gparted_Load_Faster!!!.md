---
title: "make Gparted Load Faster!!!"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by zamadatix on 2008-10-17
is there any way to get gparted to scan JUST my usb not my 2 hard drives (takes 5 minutes EVERY time). i recently have been playing around with partitioning my usb flash drive and my external and its annoying when i want to edit one thing so i can put another portable os it takes 5 minutes to load then i reboot and find out i have to wait another 5 minutes just to load the dang thing so i change the name of a partition... 

any help is GREATLY appreciated

---

### Post by Dr Small on 2008-10-17
> **zamadatix said:**
> is there any way to get gparted to scan JUST my usb not my 2 hard drives 

Sure. Just unplug the other two hard drives. Just kidding.
Actually, No, don't try that. It may be faster if you were loading it off the gParted LiveCD, but other than that, I have no ideas.

---

### Post by zamadatix on 2008-10-17
lol ill get right on unplugging them ;) obviously if i boot the gparted cd to ram it loads faster but that involves rebooting sticking in the cd waiting for it to copy from disk loading gparted for 3 minutes instead then restarting and reloading the disk... not much faster :/

isn't there anyway to just have t scan /dev/sdb1?

---

### Post by drs305 on 2008-10-17
You can start the command with only the drive you are interested in, for instance:
```
gksudo gparted /dev/sda
```

It will speed things up quite a bit, depending on your system, as it only read the drive you specify and none of the others on your system.

Added:
Actually, you can run it with one *or more* drives, such as:
```
gksudo /dev/sda /dev/sdb
```

---

### Post by zamadatix on 2008-10-19
thank you! just the thing i was looking for :P

i found after upgrading to the 8.10 beta gparted no longer takes so long to rescan so i would recomend doing it if i you want to get faster sooner :)

---

