---
title: "Dual Monitors VGA DVI"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by jrudi5of6 on 2011-12-01
Hi. i recently became interested in computers and the ubuntu operating system specifically. This question is probably;y really simplistic, but any help would be appreciated. I am trying to use dual monitors, but only one is showing up. My video card had two dvi outputs. The first monitor is attached by a dvi cable while the second is attached by a vga cable plugged into a vga female to dvi male adapter then the adapter is plugged into my video card. Do i need to have both monitors attached using dvi cables or both monitors attached using vga cables, or can I use this current setup?

Thanks

---

### Post by LowSky on 2011-12-01
nvidia or ati video card?

you may need the proprietary driver to run two monitors.

---

### Post by bcschmerker on 2011-12-01
Certain combinations of GPU(s) and display(s) will force use of the Restricted drivers.  My hybrid Everex® (500W Athena® PSU, Gigabyte® GA-MA78GM-S2HP/Advance Micro Devices® Athlon X2 5600+/4 GB RAM/Creative Laboratories® SB0350) packs a planar ATi® Radeon HD 3200 with its AMD® 780G chipset.  Purpose-built computer displays using VGA, DVI-D, and/or HDMI usually get by with the X.org server (package: xserver-xorg-radeon) OK, but many flat-screen televisions taking the signal at the HDMI port will force use of the Advance Micro Devices® Catalyst Control Center (package: fglrx-amdcccle) due to an overscan issue often encountered in over-the-air and cable digital television broadcasts.

Restricted drivers are also needed for multiple GPU's; an eMachines®/Acer® EL1210-09 equipped with a Shuttle® PC6300002 upgrade power supply and Asus® EN210/DI/512MD3(LP) currently being cycled for projection duty needs the nVIDIA® Driver Suite (package: nvidia-current) to control a primary display from the GeForce® 210 in the expansion VDA and a projector from the planar GeForce® 9200.

Hope this gives some perspective; I do not know at this time whether the Intel® iGPX family of GPU's has a specialized driver for the X Window System in LinUX.

---

### Post by jrudi5of6 on 2011-12-01
It is a nvidia GeForce card. I installed the drivers in the recommended additional drivers menu that popped up.

---

### Post by jrudi5of6 on 2011-12-01
If it helps at all, both monitors show the bios and Ubuntu loading symbol at startup.

---

### Post by papibe on 2011-12-01
If you installed the proprietary Nvidia driver, you need to use the program called 'Nvidia X Server Settings' to set up your monitors.

I don't think the physical connection you choose (VGA or DVI) would matter as far as the configuring them.

Regards.

---

### Post by jrudi5of6 on 2011-12-01
Thank you so much. The Nvidia x server settings did the trick! I just had to enable the other monitor in the settings! It makes sense now! I tried to modify the xorg.conf,, but only one monitor showed up. Thanks for the easy solution.

---

### Post by papibe on 2011-12-01
:) Great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

