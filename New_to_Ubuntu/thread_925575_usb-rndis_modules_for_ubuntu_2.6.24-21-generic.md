---
title: "usb-rndis modules for ubuntu 2.6.24-21-generic"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by nutpants on 2008-09-20
i cant find the usb-rndis modules for ubuntu 2.6.24-21-generic 
so i am thinking no one has built them yet
i need them for synce and my wm6.1 device.

how do i build them

this will be my first time doing this.
so think newbie..

nutz
(i have the source for the 2.6.24.18 modules and know where they are)

---

### Post by pytheas22 on 2008-09-20
Is there a readme file in the source?  Usually that will tell you how to compile the modules.  If not, look for a script with a name like 'configure' or 'install' and run it.  If that fails, cd to wherever the Makefile is and just type 'make', then (provided 'make' runs without errors) 'sudo make install'.

If these modules are part of the kernel tree, it may not be possible to compile just them--in that case you would need to build either the entire kernel, or find source code with a a Makefile just for the modules you want to build.

---

