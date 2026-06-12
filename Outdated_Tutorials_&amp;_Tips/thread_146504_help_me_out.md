---
title: "help me out"
date: 2006-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by rakhil on 2006-03-18
i am having this problem with Intel 82845G graphics controller and my xorg.conf file shows it is using i810 driver.My motherboard is of mercury and monitor is of LG 500E.Now the problem is that i can't get resolution more than 640x480.also my gdm is not starting using the command 
/etc/init.d/gdm start
actually it says it failed to do so.
i tried various solutions of 855 resolutin but they didn't work out.........
and this might be due to the fact that i don't know my monitor's vert refresh and horz sync rate plus videoram.How can i know that??
Plz give any idea vat to do ???
will driver or biosupdate help solving the problem?
my bios version is american megatrends inc. version 07.00T

---

### Post by Steve1961 on 2006-03-18
[QUOTE=rakhil]i am having this problem with Intel 82845G graphics controller and my xorg.conf file shows it is using i810 driver.My motherboard is of mercury and monitor is of LG 500E.Now the problem is that i can't get resolution more than 640x480.also my gdm is not starting using the command 
/etc/init.d/gdm start
actually it says it failed to do so.
i tried various solutions of 855 resolutin but they didn't work out.........
and this might be due to the fact that i don't know my monitor's vert refresh and horz sync rate plus videoram.How can i know that??
Plz give any idea vat to do ???
will driver or biosupdate help solving the problem?
my bios version is american megatrends inc. version 07.00T[/QUOTE]

The details of your monitor are listed [here]("http://www.firingsquad.com/hw/2021/LG_500E/")

At the command line type sudo dpkg-reconfigure xserver-xorg and follow along.  As long as the i810 driver is the right one for your graphics chip this should work.

---

### Post by bluevoodoo1 on 2006-03-18
[QUOTE=Steve1961]The details of your monitor are listed [here]("http://www.firingsquad.com/hw/2021/LG_500E/")

At the command line type sudo dpkg-reconfigure xserver-xorg and follow along.  As long as the i810 driver is the right one for your graphics chip this should work.[/QUOTE]

And, if you can't get the i810 running, choose "vesa" as the driver. It won't look very great... but it will get you going.

---

### Post by rakhil on 2006-03-19
i tried to change driver to "vesa" but the result i got was blank screen.still i m not able to change my resolution.vat else needs to be done??

---

