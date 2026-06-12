---
title: "ere.  I had the problem saying &quot;Input signal out of range&quot; when I tried to install th"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by tk99 on 2008-11-19
Hello there.

I had the problem saying "Input signal out of range" when I tried to install the Ubuntu. Then I downloaded the Ubuntu alternate and installed it. However, the same error still exists when I try to reboot, saying "Input Signal Out of Range, please change to 1680x1050@60Hz"

I found some post in this forum with the same problem. I tried use 'Ctrl+ALT+F1' to command version and used "Sudo dpkg-reconfigure xserver-xorg", but it never showed the screen to select screen resolution. I also tried to edit "/etc/usplash.conf" and set change it to "# Usplash configuration file
xres=1680
yres=1050" (or some other lower resolution). But none of this works

I tried Ubuntu 8.04 and 8.1. The problem with 'signal out of range" happened in 8.04 and the screen will keep flashing black within second. My computer's setting is as below:
"Dell OptiPlex 755 Minitower, 
Dell 22 inch UltraSharp™ 2208FPW Widescreen, Adjustable Stand, VGA/DVI
256MB ATI Radeon 2400 XT, Dual Monitor DVI or VGA (TV-out), full height"

I am very frustrated now and any suggestion are welcome. 
Thanks a lot,

tk

---

### Post by markjensen on 2008-11-19
Before you work too hard at the command line, let's try switching video modes.

Use CTRL+ALT+[num pad plus] or CTRL+ALT+[num pad plus] to start toggling through the video modes listed in the xorg.conf file.  You should be able to get a good resolution mode quickly, then can do a proper setup from a more comfortable GUI.

---

