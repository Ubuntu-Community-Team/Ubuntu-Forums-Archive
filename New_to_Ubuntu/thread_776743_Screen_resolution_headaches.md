---
title: "Screen resolution headaches"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by cign on 2008-04-30
Hi everyone.  I'm having some headaches with my screen resolution.  My PC has on board video and the screen resolution seems to default at 1280x1024.  Every time I change the resolution after a reboot it seems to always go back to 1280x1024.  I'm new to Ubuntu so please be understanding as I don't know my way around it quite well yet.  Any input or suggestions are greatly appreciated.

Thanks,

Chris

---

### Post by bluefrog on 2008-05-13
have a look at /etc/X11/xorg.conf (with a text editor for example) and see if there is the resolution in that file.

you could also make a little command which will be launched upon your desktop start up to change automatically the reolution if you do not have any other way.

for such a command:
system/preferences/session [startup programs tab]
click add
name: change my res
command: xrandr 1024x768     (or whatever resolution you want, find available resolution in a terminal by issuing the command  xrandr)
comment: change my res upon startup

---

### Post by ubuntu-freak on 2008-05-13
Have you tried using displayconfig-gtk to make your chosen resolution stick? If not, press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then select your resolution and reboot to see if it sticks.
 
Nathan

---

### Post by alienexplorers on 2008-05-13
What graphics card are you using?  Do you have the correct video drivers loaded?

---

### Post by linux phreak on 2008-05-13
If your monitor is a 17 inch one then 1280x1024 is the default resolution.

---

### Post by cign on 2008-05-17
Thanks bluefrog.  I did end up modifying xorg with the help of another forum member, but i will try your approach.  Althoug I modified xorg.conf once in a while the resolution jumps to a different setting, however if i reboot it goes back to 1024x768.  I'll keep an eye on it and see how it goes.

---

### Post by cign on 2008-05-17
Hi, I did that and it seems to work for the most part.  Every once in a while it changes by itself but if I reboot it seems to go back to normal.

---

### Post by cign on 2008-05-17
Hi alienexplorers.  It's an onboard video card on a Compaq PC. I wouldn't even know where to begin looking for drivers for this machine.  I got it pretty steady with suggestions from forum members and I'll keep an eye on it to see how it plays out.

Thanks.

---

### Post by cign on 2008-05-17
Hi linux phreak.  It's a 19" monitor.

---

