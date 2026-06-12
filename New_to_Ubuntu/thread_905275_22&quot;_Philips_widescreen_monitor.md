---
title: "22&quot; Philips widescreen monitor"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by lordbyron on 2008-08-30
I have an IBM hard drive that I have been working on UBUNTU for the past year very successfully. 

I have just changed the monitor for a 22" Philips widescreen monitor,Ubuntu allows me to put the screen resolution up to 1680 x 1050 @ 60Hz.(which is the what it says is the best resolution for the screen) but when I start up, the screen is too large and the lover panel does not appear.(it's there, but I have to change the horizontal location of the screen to get it, and then the top one obviously disappears.) 

if I turn the screen off and on again, or if I let it go into sleep mode, when it comes back on again the lower panel is there. is there anything I can do to have the lower panel on start up.  thank you.

---

### Post by overdrank on 2008-08-30
> **lordbyron said:**
> I have an IBM hard drive that I have been working on UBUNTU for the past year very successfully. 

I have just changed the monitor for a 22" Philips widescreen monitor,Ubuntu allows me to put the screen resolution up to 1680 x 1050 @ 60Hz.(which is the what it says is the best resolution for the screen) but when I start up, the screen is too large and the lover panel does not appear.(it's there, but I have to change the horizontal location of the screen to get it, and then the top one obviously disappears.) 

if I turn the screen off and on again, or if I let it go into sleep mode, when it comes back on again the lower panel is there. is there anything I can do to have the lower panel on start up.  thank you.

Hi and what is the model of the graphics card? If nvidia you can try and use the nvidia-settings to correct the issue. If not then you can use this command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by lordbyron on 2008-08-30
Hi I have tried that, but I think the major problem is that my screen is too big. I have checked on the list of philips monitors and it only goes up to 21 inch, so maybe someone might get onto the larger screen later.

---

### Post by Lythos on 2008-09-06
I have the same problem with a philips widescreen monitor. The resolution is right but it's displayed to big. If I change it to another resolution an than again to 1680 x 1050 its all fine. But after reboot it's al wrong again.

---

### Post by cariboo on 2008-09-06
Check the virtual screen size in you /etc/X11/xorg.conf I had the same problem after using **displayconfig-gtk**. The virtual screen size was set to 1600X1024 on a screen that natively only does 1280X1024.

Jim

---

