---
title: "not detecting a projector screen"
date: 2022-09-12
forum: New to Ubuntu
---

### Post by raulromero73 on 2022-09-12
Hi. I have a HpVictus laptop, AMD rysen5 and graphic Nvidia GTX 1650, with UbuntuStudio 22.04 LTS. I'm lost trying to use a second screen from a projector 'cause a work in a secondary school. i install already the Nvidia drivers. The laptop has a HDMI port but does not detect any extra screen connected. I cannot even add a new screen on the system arrange menu for the "screen and monitor". I'm not a new Ubuntu user but I feel like a beginner now 'cause I don't find answers as well as I did in the past. Thanks

---

### Post by TheFu on 2022-09-12
So, there are 2 issues.

Which display server is being used?  Wayland or X/Windows?  nvidia on 22.04, should use X/Windows, which is good.
The other issue would be to ensure the HDMI output is pushing the correct, standard resolution and refresh rate supported by the projector.

With Xorg, there's a program called **lxrandr** which makes this easy.  Install that, run it, and chose the resolution, refresh rate "60Hz" and choose the mirror or extend checkbox you want, then Apply.  There are other tools which can do this too, but none are as clear and easy, IMHO.

If using Wayland, I don't know how. Sorry.  There's probably an entry in the Ubuntu Desktop Guide for it. Just be certain to use the Desktop Guide for the correct DE AND the correct release.

---

### Post by MAFoElffen on 2022-09-17
Root of the problem is that NVidia drivers/ GPU polls the ports for devices, if they don't see anything, it turns off the ports. a number of projectors do no have an EDID map to report to a video card what it's possible resolutions are (to create modelines to add those resolutions)...

To confirm that, at the Grub Menu, Press <C>, then at the Grub CLI, type 
```
videoinfo
```
That would return what the computer sees as video resolutions from connected displays (your projector)...

What you need to look up, if that returns nothing (or if it does)... You need to know the resolutions of that projector...

I know of one way in Wayland to get around that when that happens:
- Set the resolution as a boot parameter in the boot line of Grub.

In Xorg XServer there are a quite a few ways. The easiest would be what 'TheFu" suggested, installing and using 'lxrandr'. There are three other ways that I know off the top of my head.

- Install 'x11-xserver-utils' and use 'xvidtune' (GUI). Any changes with this tool is non-persistent (for the session). Any boot or logout will lose the changes). Or just press the <R> key to reset.

- Same as above, setting a video boot parameter in Grub to use KMS. This is persistent.

- Use 'xrandr' (CLI). You would have to add a modeline by using 'cvt'. Then set that mode to a port. Any changes with this tool is non-persistent (for the session). Any boot  or logout will lose the changes). Restart the XSession to reset.

- Generate an xorg.conf file. Define a display section for the projector. Define a modeline for resolutions. Set the resolution in the appropriate section. (persistent) If you add multiple modelines/modes, those modes are persistent and can be chosen...

Feel free to ask for help with what you decide.

---

