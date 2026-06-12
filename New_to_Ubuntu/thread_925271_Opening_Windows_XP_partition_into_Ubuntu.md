---
title: "Opening Windows XP partition into Ubuntu"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by thomsany on 2008-09-20
Hi! Just a question.
If I installed Ubuntu and Windows XP to dual boot in my computer, is there a way from Ubuntu to use a software like VMWare or something like that to boot my windows partition in a windows inside my ubuntu config?

Thanks much,
Teo

---

### Post by dhtseany on 2008-09-20
A) I don't think that's possible
B) If it did you'd essentially have 2 OS's running at once so your system performance would be terrible

Sorry,
Sean

---

### Post by Monotoko on 2008-09-20
I think there is a way to do that, but there is a far easier way.

use "sudo apt-get install wine"
that will give you the power to open .exe files like in windows, you can install and run games, programmes ect just like you can in windows without having to actually start windows, they will open with wine, for more info see: [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by Harisz750 on 2008-09-20
you can see the contents of the hard drive containing windows from places in the menu bar. Vmachines can virtualize windows but no.. you can not boot into this.

---

### Post by dhtseany on 2008-09-20
> 
use "sudo apt-get install wine"


Wine is ok but don't have super high expectations for it. Yes, some native M$ apps will run but not all of them and many of those that will won't work as good (aka some features might not work) as if they were on XP or Vista.

Peace
Sean

---

### Post by jvin248 on 2008-10-04
I've been switching back and forth on the dual boot thing lately (watching abc, nbc, fox tv shows on Windows as I haven't gotten them to work under Xubuntu).

Google for a method to copy or ghost an actual partition into a virtual machine (like virtual box). That's the closest I found to doing this.  It would be helpful if VB could set up a "new machine" that just pointed to the existing Windows partition.

---

