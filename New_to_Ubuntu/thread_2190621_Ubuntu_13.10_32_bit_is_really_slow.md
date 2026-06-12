---
title: "Ubuntu 13.10 32 bit is really slow?"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by drakathlalala on 2013-11-28
Guys.Since i upgraded from 12.04 to 13.10,12.04 can work faster but 13.10 is lagging..how can i fix this or its really lag?

---

### Post by Dreamer Fithp Apprentice on 2013-11-29
> **drakathlalala said:**
> 13.10 is lagging..how can i fix this . . . ?Install lxde and select it as DE on the dropdown menu at login. It's a lot faster. Alternately, same advice with lubuntu-core or lubuntu-desktop. Lubuntu-core will use a little more drive space and lubuntu-desktop a little more still but I think they are probably as fast or almost as fast. Personally I'd install thunar also and uninstall the pcmanfm that comes with those packages, but pcmanfm probably is faster and you might like it. Either should be faster than Nautilus. If you give one of those a try for a few days and don't like it you can always select the DE you're useing now at login and uninstall them. A more extreme solution is to use plain openbox or one of the other ultra light-weights but they might take some getting used to. However, the same "however" still applies. You can always switch back, or for that matter back and forth with the dropdown menu at login. You also might want to look at what is being autostarted and see if you really need all of it.

---

### Post by Impavidus on 2013-11-29
If 12.04 worked fine 13.10 shouldn't be very slow. The user interface hasn't become much heavier. The one thing I can think of is that 13.10 may not have the drivers for your graphics build-in. Maybe something better is available.

---

### Post by grahammechanical on 2013-11-29
Ubuntu 12.04 had a fall back mode for machines that had graphic adapters that could not run Unity 3D. It was called Unity 2D. It run on a window compositor called metacity instead of Compiz, the standard Ubuntu window compositor. Unity 2D is no longer used in Ubuntu. Instead we have something called llvmpipe. It is a subset of the Nouveau open source video driver. And if we are used to seeing accelerated video graphics it will seem slow, very slow. There is a noticable difference. We get llvmpipe in 13.10 when we use Recovery Mode>Resume.

Try activating another video driver (even full Nouveau) in System Settings>Software and Updates>Additional Drivers tab. You must be connected to the internet and you need to allow the utility time to find some drivers for you.

Upgrades to a newer a version of Ubuntu will also upgrade to newer Linux kernels, which in turn will need upgraded proprietary video drivers. Which seem to lead to problems. Some people do not even get to a desktop. I recommend deactivating proprietary video drivers in favour of Nouveau before running the upgrade.

Regards.

---

### Post by jdeca57 on 2013-11-29
> **grahammechanical said:**
> Unity 2D is no longer used in Ubuntu. Instead we have something called llvmpipe. It is a subset of the Nouveau open source video driver. And if we are used to seeing accelerated video graphics it will seem slow, very slow. 
That decision is made, that road is taken. Still, there still quite a few people who struggle with the decision to go that way. Linux also gets used on 'older' computers and computers with little graphical power. i'm one of them and coming years I'll have the choice of staying with 12.04 (most probably) or leaving Ubuntu in favor of Xubuntu or Lubuntu. The first gets my preference at this this time. Or my computer may break down and in that case I'll buy one that supports Ubuntu... ;-)

---

### Post by drakathlalala on 2013-11-30
Guys..I don't need 13.10 (actually i need it to run XFCE) because XFCE run more faster and lighter..

---

### Post by mastablasta on 2013-11-30
well then just install and run xfce

---

