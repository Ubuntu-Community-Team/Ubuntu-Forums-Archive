---
title: "Hardware Process"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by vishal_agarwal2 on 2013-09-29
Hi,

How does ubuntu recognise my pen drive as soon as I insert it. ? or any other H/W changes ?

---

### Post by 3rdalbum on 2013-09-29
Here's the "Absolute Beginners Section" explanation:

Inserting any USB device causes the USB controller to send a message to the driver running in the operating system, saying that there's a new device.
The driver tells the Linux kernel, which then queries the USB device to determine what it is, and then loads an appropriate driver (in this case, it's USB Mass Storage - it's a built-in driver). The kernel also updates its internal table of what devices are connected to the system.

A small program running as part of Gnome periodically looks to see what devices are connected. When it sees that there's a new device that wasn't there before, it notices that this is a storage device and makes this information available to Unity. Unity will add an icon to the Launcher. When you click that icon, Unity mounts the device and opens a new Nautilus window for that device.

In reality there's a lot more to it than that, with certain responsibilities split between the kernel, the USB controller, udev and udisks; but that's a ballpark explanation.

For other hardware changes a similar process takes place. If you're talking about "installing a new PCI card" or something like that, then it's helpful to know that Linux doesn't assume that you'll be using the same hardware all the time. It scans for connected hardware whenever you boot up, in case you've changed something.

---

### Post by vishal_agarwal2 on 2013-09-29
Thanks, I got it.
But somebody questioned me that what daemon is responsible for the same. I will be thankful to you if you can guide me some abt this.

---

