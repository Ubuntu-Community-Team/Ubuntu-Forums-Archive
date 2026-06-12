---
title: "Nvidia 'not in use'???"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-10-22
Excuse my ignorance when describing my situation<------noob!!!

When I check my hardware drivers (system> admin> hardware drivers) I noticed that the second option is "not in use", which is the nvidia accelerated graphics driver (latest card).  I do have a nvidia Geforce 6 series card in my acer laptop btw.  Now when I check this option to put it into use, ubuntu goes through a series of updates and then ask to restart my computer.  But while restarting (before it gets to the splash screen),  it says that it is in "low graphics mode" and I need to 'reconfigure' it.  So I did this choosing the correct graphics card as well as the LCD 1440x900 widescreen monitor.  But still it boots up into what seems to be safe mode (everything is big: icons, wallpaper, etc.).  Compiz won't work and my nvidia settings manager no longer has the option to correct certain features, such as the screen resolution.

I resolved this problem through EnvyNG, which seemed to update the graphics card and removing my previous update (when I checked the option in "hardware drivers").  My laptop is back to normal, no problems.

Now my question is, why is it that when I look at the "hardware drivers" setting (system> admin> hardware drivers), it says that the nvidia graphics card (latest) is 'not in use'???  It appears to be in use as compiz is working fine (I now have a nvidia splash screen that appears before I get to the desktop).

Thank You

---

### Post by phidia on 2008-10-22
The hardware driver applet you are checking uses synaptic (apt) to enable/download and install the nvidia driver. envyng is not supported AFAIK in ubuntu so the applet you're looking at doesn't have anyway of recognizing what is a 3rd party install.

---

