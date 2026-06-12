---
title: "usb flash drive does not mount automatically"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by rybnik on 2012-04-04
I'm running Lucid Lynx.  I have a 4GB Sandisk usb flash drive (not sure if this matters, but back when I was running Windows, I removed the "U3" software).  It does not automatically mount when I plug it into the usb port--I've already checked the "automatic mount" flag, and it's set to "true." 

When I run "lsusb", the device appears on that list, but the system doesn't mount it.

Thank you!

---

### Post by pootan on 2012-04-04
Did you format the drive when you removed the software it came with? Often companies will write a small part of data to the first part of the drive as well and sometimes that doesn't play nice with Unix systems.

---

### Post by rybnik on 2012-04-04
Yes, I reformatted it (to FAT32).  It was originally FAT32.

---

### Post by DNRDustin on 2012-04-04
can you manually mount the drive?

---

### Post by rybnik on 2012-04-05
[quote=DNRdustin]can you manually mount the drive?[/quote]
I don't know how to do that.  But I'd prefer my system to just auto-mount everything anyway.

---

### Post by rybnik on 2012-04-05
Well, for some reason the drive starting automounting.  I have no idea what caused this, but I'm sure happy!

Thanks for your help, everyone!

---

### Post by UnknownFearNG on 2012-04-05
If your problem has been solved, please mark this thread as [SOLVED] by clicking on Thread Tools and click Mark thread as [SOLVED]. It lets users know the solution problem you had has been solved.

---

### Post by rybnik on 2012-04-06
Oops, I spoke too soon!  It turns out that the mounting is only *sometimes* automatic.  I don't know why that is... but I discovered that when I insert the flash drive before booting my computer, it mounts automatically regardless.

Any ideas?

---

### Post by UnknownFearNG on 2012-04-06
Hmm, not sure. I've never had an issue with flash drives not mounting automatically.

---

### Post by rybnik on 2012-09-08
For anyone who has had this same problem, here's how to fix it:

gedit /etc/modules

then add "usb-storage" (without the quotes) to the file on its own line of text

then reboot

---

### Post by rybnik on 2012-09-20
> **rybnik said:**
> For anyone who has had this same problem, here's how to fix it:

gedit /etc/modules

then add "usb-storage" (without the quotes) to the file on its own line of text

then reboot

Also, note that you need to be in root to modify the modules file.

---

