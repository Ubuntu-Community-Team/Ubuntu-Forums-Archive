---
title: "reformat as sol'n to ubuntu removal"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by sadclownsmiles on 2008-10-19
hello,

i don't know anything about operating systems, just managed to dual boot vista with ubuntu 8.04. but the problem is, ubuntu has taken up majority of the harddisk space and i would the vista parition to have more memory.

i've read about messing up with the GRUB and donwloading softwares or chaning some settings when trying to remove the ubuntu partition so i'm just thinking of reformatting the machine

since i'm ok with reformatting the machine, will all the issues regarding GRUB loading and looking for an inexistent OS still po pup even if i have reformatted the machine?

or maybe someone knows a way i could add additional memory to the windows partition without having to uninstall anything?

thank you. :)

---

### Post by ugm6hr on 2008-10-19
> **sadclownsmiles said:**
> i don't know anything about operating systems, just managed to dual boot vista with ubuntu 8.04.

This is a significant achievement for someone who knows nothing about OS... At least you know what an OS is!

If you have the Ubuntu LiveCD (which you presumably installed with), boot with the LiveCD, and you can use Partition Editor (GParted) to shrink the Ubuntu partition.

Then rebbot into Vista and expand its partition to fill the space using Vista's own partition sizer (forgotten what it's called).

Make sure you backup before doing this (which you would have to do anyway if reformatting).

---

### Post by garok89 on 2008-10-19
try booting up the live cd for ubuntu and type

sudo gparted
from the terminal and unmount the ubuntu partition via right click and then shrink it by dragging to the right. it may take some time to do this.
after this, restart and boot windows.
if you google about you will find how to extend this partition.

you can format the ubuntu partition if u like and restore the MBR using the windows disk.....google about for how to do this (its been so long i cant remember the commands)

---

### Post by bodhi.zazen on 2008-10-19
See this link : [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by sadclownsmiles on 2008-10-26
thanks for the solutions/answers. i think i'd just delete the ubuntu partition, fix the mbr, expand vista and then reinstall ubuntu..

the ubuntu partition seems to be crashing lately and i don't know what to do, but reinstall it. 

thanks again

---

