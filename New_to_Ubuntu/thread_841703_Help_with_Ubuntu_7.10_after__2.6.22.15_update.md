---
title: "Help with Ubuntu 7.10 after  2.6.22.15 update"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by davexnet on 2008-06-26
Hello, after applying the latest updates for Ubuntu 7.10,
my Nvidia restricted driver failed to load and I was left with
a much lower resolution.  The driver was originally installed
by Envy.  The only way to get the driver to load was to use Envy
to uninstall, reboot, and reinstall the restricted driver.

It was successful, I get the Nvidia splash screen at boot time,
problem is it's using a resolution bigger that the physical
screen; thing usually on the far left and right are off the screen
completely - including the "system" and "administration" items
normally in the top left.

How can I get to the applet and change the screen res?
TIA for any info...

---

### Post by phidia on 2008-06-26
You could temporarily create a new panel and add the system menu item to that newly created panel-so that you can access the applet.
You could also edit /ect/X11/xorg.conf and comment out the Modes that are too large for your particular screen-then restart x and hopefully you're in a usable screen rez.

---

### Post by doddi on 2008-06-26
maybe you could hit Alt+F2 which should bring up the run application, then type nvidia-settings (providing you have this installed)

---

### Post by davexnet on 2008-06-26
Thanks - using Alt-F2 I was able to reach the Nvidia-Settings.
I am new to Linux and use it infrequently enough that I either forgot or never
even knew about alt-F2 !

---

