---
title: "2 monitors"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by JonWasHere42 on 2008-05-17
Hey
I was wondering..
I have 2 monitors, but on occasion unplug the external monitor. This causes a series of pain in the *** things to happen in Ubuntu. I think, because the resolutions are not of the same height, that i can not pan across the desktop. So instead im stuck looking only at the right half of it.
So what I have done, is I have two files /etc/X11/xorg.conf_Xmonitors
where X is either 1 or 2. now what i do now, is whenever i log on with a different number of monitors than i had last time, is
'sudo cp /etc/X11/xorg.conf_Xmonitors /etc/X11/xorg.conf'

This works well enough. But is there somewhere that checks to see how many monitors are available, and can load the correct file automatically?

Thanks
--Jon

---

### Post by EXCiD3 on 2008-05-17
If you have an nvidia card, you can use nvidia-settings to configure your xorg so that if a certain monitor config is detected it will load the settings for it. I have it load certain settings for when my laptop is by itself and other settings when i have my external monitor plugged in. The only thing that needs to happen is for the monitor to be plugged in before the xserver is started or to restart the xserver if i plug in the monitor after its already started.

---

### Post by Inxsible on 2008-05-17
> **EXCiD3 said:**
> If you have an nvidia card, you can use nvidia-settings to configure your xorg so that if a certain monitor config is detected it will load the settings for it. I have it load certain settings for when my laptop is by itself and other settings when i have my external monitor plugged in. The only thing that needs to happen is for the monitor to be plugged in before the xserver is started or to restart the xserver if i plug in the monitor after its already started.Yes but if you just plug the external monitor without changing the resolution again ..it doesnt help.

I mean I sometimes undock my laptop and have to go into nvidia-settings again and remove Twinview. It does not happen automatically :(

---

### Post by EXCiD3 on 2008-05-17
> **Inxsible said:**
> Yes but if you just plug the external monitor without changing the resolution again ..it doesnt help.

I mean I sometimes undock my laptop and have to go into nvidia-settings again and remove Twinview. It does not happen automatically :(

Ah good point, I actually have it setup so my laptop monitor is disabled so I dont use Twinview. Thanks for the tip ;)

---

