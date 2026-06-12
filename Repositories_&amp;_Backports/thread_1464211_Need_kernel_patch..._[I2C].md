---
title: "Need kernel patch... [I2C]"
date: 2010-04-27
forum: Repositories &amp; Backports
---

### Post by Moozillaaa on 2010-04-27
...so I can get VLC troubleSHOT !!!

First troubleshoot step is confirm 2.6.x.x.x kernel patch. I cannot find it. I found development page, but it was just updated 1 HOUR AGO!!!
Upgrading I2C Drivers to the new 2.6 Driver Model
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/i2c/upgrading-clients](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/i2c/upgrading-clients)

Help?

---

### Post by DLHDragon on 2010-04-30
look in synaptic for  **i2C** 
-----

**libi2c-dev**
userspace I2C programming library development files

I2C devices are usually controlled by a kernel driver. Using this
library it is also possible to access all devices on an adapter
from userspace and without the knowledge of Linux kernel internals.

-------------------------

**i2c-tools**
heterogeneous set of I2C tools for Linux

This package contains a heterogeneous set of I2C tools for Linux: a bus
probing tool, a chip dumper, register-level access helpers, EEPROM
decoding scripts, and more.

---

### Post by DLHDragon on 2010-04-30
try a google search about **i2c driver linux**

-------------------------------------------------

[https://i2c.wiki.kernel.org/index.php/Main_Page](https://i2c.wiki.kernel.org/index.php/Main_Page)

---

### Post by Moozillaaa on 2010-04-30
Thanks...

It was in local repo; I didn't recognize it by name...

---

