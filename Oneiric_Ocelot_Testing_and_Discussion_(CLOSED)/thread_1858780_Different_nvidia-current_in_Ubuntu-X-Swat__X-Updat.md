---
title: "Different nvidia-current in Ubuntu-X-Swat / X-Updates PPA"
date: 2011-10-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-10-13
There is the newest prerelease of the Nvidia proprietary driver (nvidia-current) in the Ubuntu-X-Swat / X-Updates PPA.
The changelog claims that the support for xserver ABI 11 (xorg-server 1.11) has been added.
However, this particular build of the driver is not installable on setups with xserver 1.11.
This driver depends on ABI 10 (xorg-server 1.10).

This means, if you have xserver 1.11 installed, do not use this driver from X-Updates PPA.
A correctly built working nvidia-current for xserver 1.11 can be downloaded from Xorg-Edgers PPA.

But, if you have xserver 1.10 installed, you may use this new prelease nvidia-current from X-Updates PPA.
And yes, if you have xserver 1.11 installed, you can only use the driver from Xorg-Edgers PPA.

---

