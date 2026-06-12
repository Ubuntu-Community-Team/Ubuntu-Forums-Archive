---
title: "program for ubuntu transfer files cable win95 DCC"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by thombark2 on 2014-08-13
Here is my setup.

 Source computer: old LAPTOP Win95 with Apache PCMCIA modem but no USB no Ethernet no CD no Floppy.

Cable:  An old Laplink (LL3) cable.

Target Computer: Desktop running 10.04 with a parallel port and USB.             

 I need to transfer files from the old Win95 to the Desktop. The Windows Direct Cable connection seems a good choice but what do I run on the 10.04 desktop to receive the files over the parallel cable?

Another possibility is to use the PCMCIA modem to connect to another more recent ubuntu or XP computer.

Any advice is appreciated. Thanks.

---

### Post by kurt18947 on 2014-08-14
IMO that's gonna be tough.  Would it be practical to remove the hard drive from the Win95 machine and install it into an external USB enclosure? Or use a laptop drive PATA - desktop PATA adapter?  I haven't tried but I'd be surprised if a laplink cable would work with Ubuntu.

---

### Post by sotiris2 on 2014-08-14
I also believe putting the drive on the  ubuntu machine to copy files would be the most reliable. The win98 has IDE drives right (the big 'tape' like cords? If your new machine has sata only (quite likely) you can get an ide pci card for 10-15 euros here.

---

### Post by sp40140 on 2014-08-14
One more suggestion: Get pcmcia ethernet or wi-fi card. will solve all your problems. they are not that exp.

---

### Post by coffeecat on 2014-08-14
> **sp40140 said:**
> One more suggestion: Get pcmcia ethernet or wi-fi card. will solve all your problems. they are not that exp.

Really? And what about the Windows 95 drivers for the pcmcia ethernet or wi-fi card? I suspect they might be a little more difficult to find.

@thombark2, I agree with sotiris2 and kurt18947 that removing the 2½" drive from the old laptop and connecting it directly to your Ubuntu machine is probably the best option. Instead of an ide pci card or USB enclosure you can also get all-purpose docking connectors with SATA, 2½" and 3½" ide connections, but they may not be cheap.

---

### Post by sudodus on 2014-08-14
I have a "USB2.0 to IDE & SATA cable". It came with a set of adapters for 2½" and 3½" ide and sata connections. It is fairly cheap and useful for many purposes, not only for your current task.

---

### Post by Sanctimonious_Ape on 2014-08-14
If moving the HD around isn't an option, [this ancient document](http://www.linux.com/learn/docs/ldp/Serial-Laplink-HOWTO) may be of some assistance.

---

