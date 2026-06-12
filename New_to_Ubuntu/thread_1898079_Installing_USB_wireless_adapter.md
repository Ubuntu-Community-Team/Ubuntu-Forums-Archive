---
title: "Installing USB wireless adapter?"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by NewAtLinux on 2011-12-20
Newbie here. Running Ubuntu 11.1 via WUBI on an XP machine.
How can I use my USB wireless adapter? It is a Netgear
WG111T. It shows up using the command "lcusb". The entry
for the device shows (no firmware). Any suggestions?

---

### Post by cortman on 2011-12-20
> **NewAtLinux said:**
> Newbie here. Running Ubuntu 11.1 via WUBI on an XP machine.
How can I use my USB wireless adapter? It is a Netgear
WG111T. It shows up using the command "lcusb". The entry
for the device shows (no firmware). Any suggestions?

Are you typing "lsusb" or "lcusb"?

---

### Post by fractalman on 2011-12-20
You need to install the driver for your adapter

[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)


[http://linuxwireless.org/en/users/Devices/USB](http://linuxwireless.org/en/users/Devices/USB)

you should be able to find your driver from the 2nd link there's a few netgears on there but i'm not sure quite which you will need

---

### Post by anewguy on 2011-12-21
Be sure your USB device is plugged in then do the following in a terminal window:

lsusb <press enter>

You should see a line that contains a pattern of xxxx:yyyy - these are the USB manufacturer id and the USB product id.  This will tell us the manufacturer and name of the chipset used in your adapter.  If you post that entire line back here, including the description, the xxxx:yyyy, etc., we should be able to know what chipset your adapter is using and therefore help you install a driver.

Dave ;)

---

