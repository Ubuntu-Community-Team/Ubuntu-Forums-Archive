---
title: "Advice Required"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by Vortex5 on 2012-07-30
I've got an HP 1000-1122TU with 2 GB of RAM. It has an Intel Pentinum B950 processor and an Atheros AR9485 wireless card. Will Ubuntu run properly if I install it?:confused:

---

### Post by BkkBonanza on 2012-07-30
I had to look up that processor but it seems to be fairly recent and probably usable. The Atheros wifi card should work fine and is actually pretty cool because it supports master mode (AP) with current drivers unlike most. Barring other weird hardware in there I'd say you'll be fine with Ubuntu.

---

### Post by Zill on 2012-07-30
Vortex5:  See [Try Ubuntu before you install it]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install")

---

### Post by NikTh on 2012-07-30
> **Vortex5 said:**
> I've got an HP 1000-1122TU with 2 GB of RAM. It has an Intel Pentinum B950 processor and an Atheros AR9485 wireless card. Will Ubuntu run properly if I install it?:confused:


Hi , 
the best approach is to burn an .iso image to CD or Usb  and "Try Ubuntu" to see if works properly with your system. 

You can check some things 
e.g 
1) wireless  
is wireless activated and scan networks ? 
can you connect ?

2) unity 3D support 
open a terminal (ctrl+alt+t) and paste this command 
```
/usr/lib/nux/unity_support_test -p
```what is the output ? 

3) Is your cam work ? 
open a terminal again and paste this command 
```
gstreamer-properties
```in the opened window click on Video > Default Input > Test. 

Also you must know that Ubuntu comes with most of drivers pre-installed 
But
in some cases might needed to install additional drivers to your system.
If you want to test , what additional drivers are available you can run jockey.
```
jockey-gtk
```You can download Ubuntu 12.04 LTS image from here --> [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) 
and you can burn it to Usb (at least 2GB) with Unetbootin program
Unetbootin program here --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

** This is the advantage of Ubuntu (and other Linux Distros) . You can test (taste) it before you install (eat) it. **

Thanks

---

