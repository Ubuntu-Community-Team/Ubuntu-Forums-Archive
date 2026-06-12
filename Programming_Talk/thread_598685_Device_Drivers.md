---
title: "Device Drivers"
date: 2007-10-31
forum: Programming Talk
---

### Post by hunnybunny on 2007-10-31
I was just wondering if someone would be able to tell me what hardware information is necessary in order to write a device driver. For example, if I wanted to write a driver for my graphics card, what information would I need to get from the manufacturer - or is there some other way I could find it out myself? So far all the tutorials I've found only cover the higher-level driver programming concepts such as communicating with the kernel. :(

---

### Post by meatpan on 2007-11-01
Consider starting with an easier driver interface, like USB.   Perhaps after that you can try writing drivers for an old device over a parallel port.   Starting with a complicated system, such as a graphics card, is going to be difficult and frustrating.   There are quite a few decent linux USB driver tutorials on-line.

---

### Post by gradedcheese on 2007-11-01
You usually need a data sheet :)  That is, at least a list of the registers (and their addresses) and what they do.  You also need some basic information about the device's interface (stuff like "set this clock up, then set this enable bit, then wait for this status bit").  Without that, there's not much that you can do.  This is why projects like the nvidia driver start by reverse engineering the proprietary driver (spying on its traffic, etc).  Painful.

If you want to see what a typical data sheet that one would use looks like, check out the good old CS8900 Ethernet controller: [http://www.cirrus.com/en/pubs/proDatasheet/CS8900A_F4.pdf](http://www.cirrus.com/en/pubs/proDatasheet/CS8900A_F4.pdf)

There you'll see the register map, some device operation info, etc.  Take a look in the kernel tree at drivers/net/cs8900.c to see what the driver looks like.  Compare that to the data sheet and it should give you a good idea of what it's like to write these things.

---

### Post by moma on 2007-11-01
Hello,

If you are generally interested in writing device drivers, register yourself at 
"Linux Driver Project".  There you can learn from and communicate with other (300) driver developers. 

See: [http://www.futuredesktop.org/kernel.html](http://www.futuredesktop.org/kernel.html)  (the ultimate kernel knowledge page)

Browse to "**Driver and module programming**" section. 
Follow the link to "**Linux Driver Project.org**" and study the   "**Project mailing list... **" 

ps. See also "Nouveau, the free Nvidia driver"

---

### Post by hunnybunny on 2007-11-05
Thanks a lot, this has all been very useful! Everything is starting to fall into place. :D

---

