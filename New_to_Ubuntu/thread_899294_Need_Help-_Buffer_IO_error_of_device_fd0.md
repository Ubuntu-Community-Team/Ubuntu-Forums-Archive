---
title: "Need Help- Buffer I/O error of device fd0"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by skitzojeffy on 2008-08-24
Hi,

I'm new around here and am having a problem trying to install Ubuntu 8.04 on my new computer that i just built
When i get to the boot menu and boot it using 'Install Ubuntu' i get the error message 'Buffer I/O error of device fd0, logical block 0'

My computer has the following specs
Asus M3N-H HDMI motherboard
2gb A-Data Ram
160gb Samsung SATA HDD
GeForce 8200 intergrated chipset
Asus retail DVD-RW DL

I now many people have the same problem but the forums have been no help so far

if someone has a solution it would be greatly appreciated

Thanks Jeffrey

---

### Post by bab1 on 2008-08-24
I believe that is a reference to a floppy drive.  Do you have a floppy drive?  Does it stop you from going on?

---

### Post by jondiced on 2008-08-29
Thanks **bab1**! I don't have a floppy drive, but forgot to disable it in CMOS. Disabling the floppy drive, and hence also removing it from the boot list, did the trick.

---

