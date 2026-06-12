---
title: "install pci driver"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by firebird7 on 2012-01-19
Please help. I have installed a network adapter TG-3269 to my desktop amdx2 245 dual core. I need to load the driver but don't 
know how. I am running ubuntu 11.10
thanks

---

### Post by cortman on 2012-01-19
[http://www.linuxforums.org/forum/debian-linux/182591-cant-install-driver-tg-3269-tplink-network-adapter.html]("http://www.linuxforums.org/forum/debian-linux/182591-cant-install-driver-tg-3269-tplink-network-adapter.html")

This one looks tricky...

---

### Post by Mark Phelps on 2012-01-20
Unlike Windows, Linux drivers are generally NOT supplied with the hardware you buy.

Which means, you generally have only two choices:
1) Easy -- if hardware vendor provide downloadable Linux drivers
2) Very hard -- having to build and compile a Linux driver from the source code using supplied source and scripts.

The link provided shows how hard the second option can be.

Unfortunately, since drivers run in kernel space, there is no third option.

---

