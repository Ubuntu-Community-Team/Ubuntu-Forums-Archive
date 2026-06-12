---
title: "NVIDIA: Setting Resolution, DVI Problems"
date: 2014-09-26
forum: New to Ubuntu
---

### Post by Henry_Flower on 2014-09-26
Thanks again for all your help so far. I apologize if I've been previously unresponsive but I now have internet access so this should go much smoother from now on.

I've now installed the recommended driver for my video card (GeForce 430) and would like to set the resolution to my monitor's native 1080p. However, now that the video drivers are installed, the aspect ratio is so far off, that I can't reach any part of the task bar that a window might appear on (the terminal, the nvidia configuration settings). I tried adjusting the settings with xrandr in the terminal with ALT+F1 but I got an error message that the display couldn't be opened.

Additionally, I would like to use DVI output but the screen is completely black when I attempt to boot the computer with DVI (VGA works fine, monitor doesn't support HDMI).

---

### Post by papibe on 2014-09-26
Hi Henry_Flower.

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -E 'nvidia|nouveau|i915'

xrandr -q

xrandr -q --q1

[ -f /etc/X11/xorg.confo ] && grep nvidia /etc/X11/xorg.conf
```
Regards.

---

### Post by Henry_Flower on 2014-09-26
Sorry, had to reformat and get myself back to where I was after some shenanigans. I'm not quite sure how to copy & paste this since I'm having trouble opening anything on that computer right now.

---

### Post by Vladlenin5000 on 2014-09-28
In terminal, select the part to be copied by clicking and holding. Then right-click and "copy".

---

