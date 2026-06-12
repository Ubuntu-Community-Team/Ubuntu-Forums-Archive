---
title: "Remove ATI display drivers and use 'standard' drivers"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by PartisanEntity on 2008-10-17
I upgraded my wife's laptop to Ubuntu 8.04 and it seems the ATI drivers are not working right. The system is sluggish and windows take quite long to build up.

I'd like to remove all current accelerated display drivers and use 'standard' non-accelerated drivers.

What's the best way to rid the system of any and all display drivers and then use 'standard' drivers without graphics acceleration?

So far I have only dealth with nvidia which usually always worked right away..

Thanks!

---

### Post by christianvaldes on 2008-10-17
What is the model of the labtop?
What is the Video Card on the laptop?

---

### Post by bobnutfield on 2008-10-17
You can go to System>Administration>Hardware Drivers and disable the fglrx driver.  Reboot and it should load the "radeon" driver automatically.  You can even downgrade from that by changing the driver in xorg.conf to "vesa".

---

### Post by PocketDog on 2008-10-17
With my ATI I'd just go to System - Administration - Hardware Drivers and remove the tick from 'Accelerated graphics driver', and close the window.

I'm one of the lucky ones though, my ATI Radeon works perfectly so forgive me if I don't test the removal of the proprietary drivers myself ;)

---

### Post by PartisanEntity on 2008-10-17
It's an Acer Aspire 5100. Graphics card is ATI Radeon Xpress 1100

I don't know what the issue is, but since upgrading to 8.04 it's very slow:

- windows build slowly
- when scrolling you get this 'skipping' effect
- openoffice functions very slowly and keeps rebuilding its menus

---

### Post by bobnutfield on 2008-10-17
I have the step up from that graphics card in my Toshiba A210 (X1200).  I did have difficulty with smooth graphics in Hardy, but since I have upgraded to Intrepid and using the just release fglrx for the new Xorg, I have had no trouble and performance is greatly improved.

---

### Post by PartisanEntity on 2008-10-18
Can I just use the 'vesa' drivers? Would that solve the issue?

Basically what I would like to do is remove all ati related drivers and just use very basic/standard display drivers.

Any tips would be appreciated.

---

### Post by bobnutfield on 2008-10-18
Vesa IS the most basic driver you can use.  It will usualy work with just about any graphics chipset.  But, be aware that you will be very limited in the screen resolutions available to you and any fancy desktop stuff will probably not work well.

---

### Post by Tom--d on 2008-10-18
> **PartisanEntity said:**
> Can I just use the 'vesa' drivers? Would that solve the issue?

Basically what I would like to do is remove all ati related drivers and just use very basic/standard display drivers.

Any tips would be appreciated.



I would use the driver 'ati'
Its open source and should not make the computer slow. It should have 2D support for scrolling (etc) and should be fast. And you get the correct resolutions.

---

### Post by PartisanEntity on 2008-10-19
> **Tom--d said:**
> I would use the driver 'ati'
Its open source and should not make the computer slow. It should have 2D support for scrolling (etc) and should be fast. And you get the correct resolutions.

I think I tried the 'ati' driver with no effect. Unless I need to add or remove relevant sections from the xorg.conf file?

---

