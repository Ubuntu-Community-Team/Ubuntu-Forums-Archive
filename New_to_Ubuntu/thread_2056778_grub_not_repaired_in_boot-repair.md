---
title: "grub not repaired in boot-repair"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by neflarity on 2012-09-12
Hi,

I am very new to ubuntu so please forgive my ignorance. I have installed ubuntu 12.04 onto my netbook via usb which all seemed fine until it did it's first restart and now just cannot find the system at all unless i have the usb plugged in. I need to get the grub from the usb over to the hd but nothing as of yet has worked for me. tried what feels like everything and now am admitting defeat and putting to anyone that can help me. 

i ran boot-repair and it gave me back this

[COLOR=Red] paste.ubuntu.com/1200145[/COLOR]

and then i ran the bootinfo button and got this

[COLOR=Red]paste.ubuntu.com/1200160[/COLOR]

please help!

neflarity

---

### Post by mips on 2012-09-12
Make sure your settings are exactly the same as [http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html](http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html) as your partitions match that.

---

### Post by YannBuntu on 2012-09-12
Hello

> **neflarity said:**
> i ran boot-repair and it gave me back this

[COLOR=Red] paste.ubuntu.com/1200145[/COLOR]

Your boot files are too far from the start of the disk.

Solution:
1) Boot on your Ubuntu disk, choose "Try Ubuntu", run Gparted, reduce the sda1 partition from 317GB to 100GB. (reduce it from the right-side, so that it still starts at the beginning of the disk). In the free space, you can create a data partition (EXT4).
2) Reboot.
3) If still not good, run the "Recommended repair" again and tell us the new URL that will appear.

---

