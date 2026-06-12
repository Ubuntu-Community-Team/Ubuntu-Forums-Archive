---
title: "Installing ATI Graphics Driver"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by lol_u died on 2008-08-29
Hey people! I have Ubuntu 8.04 Hardy version and it is a 64 bit version also (let me know if you need more info). Anyway I'm totally new to Linux and I successfully compiled a game called bzflag which requires 3D Acceleration. I have a ATI Radeon X1650 AGP. And I download the driver on this link [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html")
And it saved to my desktop so I opened it and it opens text editor for some odd reason. And I really need to get my 3d acceleration and all that good stuff going with my ATI card. PLEASE help me!:guitar:

---

### Post by wolfen69 on 2008-08-29
go to system>administration>hardware drivers to install.

---

### Post by Crafty Kisses on 2008-08-29
Try the restricted drivers manager, your driver should be there.

---

### Post by SunnyRabbiera on 2008-08-29
Actually this method might not be best, plus ATI cards really suck in linux (more of a ati issue there though)
did you try the restricted drivers app?
its in system> administration> hardware drivers.

---

### Post by crjackson on 2008-08-29
> **lol_u died said:**
> Hey people! I have Ubuntu 8.04 Hardy version and it is a 64 bit version also (let me know if you need more info). Anyway I'm totally new to Linux and I successfully compiled a game called bzflag which requires 3D Acceleration. I have a ATI Radeon X1650 AGP. And I download the driver on this link [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html")
And it saved to my desktop so I opened it and it opens text editor for some odd reason. And I really need to get my 3d acceleration and all that good stuff going with my ATI card. PLEASE help me!:guitar:

If the driver in the "Hardware Drivers" applet will work for you it's generally a better driver.  I have 5 systems right now using AIT cards and they work fine.

If that driver won't work for you, and you want to try the driver you just downloaded to your desktop, follow these installation [instructions]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install from ati.com (latest version of drivers)").

---

### Post by t0p on 2008-08-29
There's also an app called **Envyng** which installs proprietary (NVIDIA and ATI) drivers for you.  The app is actually called **envyng-gtk** or **envyng-qt**, depending on whether you're running ubuntu or kubuntu - envyng-gtk is the ubuntu app.

---

### Post by crjackson on 2008-08-29
> **t0p said:**
> There's also an app called **Envyng** which installs proprietary (NVIDIA and ATI) drivers for you.  The app is actually called **envyng-gtk** or **envyng-qt**, depending on whether you're running ubuntu or kubuntu - envyng-gtk is the ubuntu app.

Envy is great, but it's 2 driver versions behind right now for ATI.  I haven't tried the current ATI driver just released, but the 2 previous drivers have to many problems for me to even consider.  The problems ARE related to it's 3D abilities and that seems to be exactly what the OP is concerned about.

The currently included restricted driver that's activated by the "Hardware Drivers" applet is in MY OPINION the better choice.  It's far more stable and plays 3D games very will.  The same can't be said for the ATI driver versions 8.6 and 8.7 . I haven't yet tried the 8.8 so I can't vouch for that one.  It may be that the 8.8 is a fine replacement I'm not sure.  Since Envy only includes the 8.6 driver I can't point anyone in that direction.

---

