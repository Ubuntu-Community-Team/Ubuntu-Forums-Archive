---
title: "How to install drivers for ISDN Modem"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by derektim on 2008-06-09
Hi,

I have recently installed ubuntu server, however I have an ISDN modem slotted in a free PCI slot.

The manufacturer of the modem provides linux drivers and I have donwloaded the appropriate package.

The question is...

How do I actually install the drivers??

This might sound stupid, but all I would do on windows, is go into device manager and install from there..

I have installed gnome desktop, but cannot see any kind of device manager in there..

Earler today, whilst scouring for answers, I did find a command line entry which listed the devices and the device is listed with the manufacturer but 'unknown'.

Any help will be most appreciated.

---

### Post by Wandering on 2008-06-09
Well if it is a .deb file, or has one in it, then all you have to do is install gdebi from synaptic then you can double click the file, and it should install.

Good luck.

---

### Post by derektim on 2008-06-10
Regrettably it isn't..

It looks like I need to use make to build and install the package.

Unfortunately, make throws up numerous errors, so i will attempt to use mISDN as this appears to include drivers for a variety of cards.

---

