---
title: "Boots on one pc but not the other?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by StaticIp on 2008-04-24
My Ubuntu 7.10 full install to my 250gig external hard drive works great on the computer I installed from ( removed internal hdd before installing, so I  wouldn't destroy the MBR) I chose to install the boot loader to my removable but when I try to boot from another pc I get Grub Error 21. Any idea how to make Ubuntu fully portable? Or just how to boot from another pc? My Partition setup is as fallows:
sda1 data (documents and such)
sda2 / (installed ubuntu here)
sda3 swap

---

### Post by schwascore on 2008-06-27
It could simply be a hardware issue.  Unless the two computers have the same hardware, it is quite possible that either parts of Ubuntu won't work on the other computer or that part of the configuration necessary for one computers hardware does not work with the other computers hardware configuration.

You can use the live cd on both computers to help diagnose the actual problem.

---

### Post by mcduck on 2008-06-28
Sounds like a problem with the hard drive configuration on other machine being different from the one where you installed Ubuntu.

For example, if the machine you used for installing has one HD, that drive is seen as sda (or hd0 for grub) and the external drive becomes sdb (hd1).

If the other computer has 2 HD's, they are sda (hd0) and sdb (hd1) and your removable drive becomes sdc (hd2) instead.

Now, the Grub is configured to look for the boot image in hd1, which works on the first computer but points to wrong drive on the other..

I think that to make a OS fully portable you need to make it detect & configure quite a lot of stuff at boot time, more like live-CD's do than what happens when booting a normal, installed system.

---

