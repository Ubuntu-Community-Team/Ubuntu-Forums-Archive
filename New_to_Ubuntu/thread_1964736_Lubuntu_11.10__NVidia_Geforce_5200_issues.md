---
title: "Lubuntu 11.10 / NVidia Geforce 5200 issues"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by cole2kb on 2012-04-24
Spent HOURS searching with no solutions.

Running Lubuntu 11.10, and it's nice, but the GUI and Flash video are laggy, presumably because I am not running the NVidia drivers for my card. When I install them, I am stuck in a 640x480 resolution.

The nvidia-settings panel says some error about scanout, which is fixed by downgrading the nvidia-settings package, but it doesn't show an available resolution over 640x480.

When trying to add a mode by hand using xrandr, I get an error about not being able to find gamma settings with every command I issue (""xrandr: Failed to get size of gamma for output default") and when I go to set the new mode I added, it says something about failing to set mode for cvrt 0. This problem is pretty wide-spread it seems, and I haven't found anything that works. When using whatever the default drivers are (removing the NVidia ones I installed) all I have to do is add the custom resolution (1360x768) with xrandr and it works perfectly, minus it just overall running very slow.

Thanks!

---

### Post by Locus Kiesselbachi on 2013-02-11
Hello!
I would recommend installing latest Nvidia graphics driver. 
Go to Preferences-->Monitor_Settings/Display_Settings! 
Does it now give you chance to change resolution?

my rig:
*AMD AthlonXP1800+ 1,5GHz
*ASRock K7S41GX
*Nvidia GforceFX 5200FX resolution 1600x1200
NVIDIA X Server, driver version: 96.43.20
(L)ubuntu11.10

---

