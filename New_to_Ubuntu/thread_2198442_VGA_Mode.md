---
title: "VGA Mode"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by zero_cool05 on 2014-01-08
Hallo folks,
I would like to install ubuntu on my old pentium iv with 1.2gb ram.
Now my question i am only using a standard tv as a monitor (used to watch movies only) the resulution is 640x480 so in windows xp i f8 on boot and select vga modo. is there an option to have ubuntu run with that low resulution???? thats why i thought i ask here first before format my old xp machine

---

### Post by sudodus on 2014-01-08
Ubuntu can manage it, but it also depends on the particular hardware, the monitor/TV, the graphics card/chip and the driver that is selected (normally automatically) to run it. You can check the available graphics resolutions with the terminal window command

```
xrandr
```

640x480 is available on the machine with Ubuntu 12.04 LTS, where I am writing this reply, but I have at least one laptop, where 800x600 is the lowest available resolution (unless you do some special tweaks).

---

### Post by DuckHook on 2014-01-09
Without more HW info, this is just a shot in the dark, but based on P4 w/ 1.2 GB RAM I would say that your equipment is just barely capable of Ubuntu. You may wish to use Xubuntu or Lubuntu which would give you much better response and stability. Most cards will run 640x480, especially older machines that were originally loaded with XP. Do as *sudodus* suggests and check with ```
xrandr
```Do this from a LiveDVD/USB of Xubuntu/Lubuntu so that you don't have to nuke XP just to test.

---

### Post by grahammechanical on 2014-01-09
This I think is the problem you are going to face: getting Ubuntu to run at the correct screen resolution. Modern monitors/TV screens have coded in their electronics Extended Display Identification Data (EDID). This data includes the optimum screen resolution and frequencies. Linux sets the screen resolution each time it loads by reading the EDID from the monitor. Linux does not now set the screen resolution from a configuration file. That TV most likely does not have an EDID.

I would suggest that you may need to edit the Grub boot parameters to include "nomodeset." Then Linux will load without setting a video mode. You may also need to edit the Xserver configuration file to set the screen resolution.

The correct test is with a live session DVD.

Regards.

---

