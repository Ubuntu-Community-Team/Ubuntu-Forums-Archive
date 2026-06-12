---
title: "Enabled Restricted Nvidia Drivers, now ruined"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by VioletArrows on 2008-04-27
I installed 8.04 a few days ago and have just now gotten around to changing the settings. My second monitor was half off the edge of the screen, so I read on the forums that Ubuntu has Nvidia drivers. I enabled it in Hardware Devices, rebooted, and now the main screen is scrambled with a black stripe down the middle, and the second monitor isn't recognized at all. Can't see anything, so can't get in to change it back.

Dell Inspiron 1520
Nvidia 8600 GT

---

### Post by cmnorton on 2008-04-27
Reboot, and choose recovery mode.

Run dpkg-reconfigure xserver-xorg, and first chose the vesa driver, taking all other defaults. 

If the vesa drive does not work, try vga.

You won't like the resolution, but you can at least work from that point to get decent graphics running again. 

Dual monitors tend to be difficult to configure. I suggest that you search these archives for others who have had to do this.

---

