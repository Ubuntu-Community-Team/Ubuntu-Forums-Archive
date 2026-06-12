---
title: "Kubuntu second screen; also, speakers."
date: 2008-10-11
forum: New to Ubuntu
---

### Post by ItecKid on 2008-10-11
First off I have a laptop.

I am trying to hook it up to my T.V. via a VGA cable. however the Fn+F7 command does not seem to work for this.  If I reboot the computer, I can the initial start up screen to display on the system, and it shows that blue bar when Kubuntu loads, but it goes blank when it gets to the screen where I enter my password.  I think it because my computer's native resolution in 1680*1050, while the T.V. only displays at 1360*768.  However, in the system settings, it doesn't seem to allow me to set a resolution for my second screen.  Any thoughts?

Edit: Fixed my speaker issue.

---

### Post by jamesrl on 2008-10-11
Depending on your video card (e.g. not being NVidea or ATI, which should have control centers that are better for configuration this), I would try xrandr (or grandr for a graphical program).
For xrandr You need to type in commands like 
```
xrandr --output VGA --left-of LVDS --output LVDS --auto
```
to 'extend' your desktop to the second monitor.
To switch an external monitor on, though you can easily put htat sort of stuff in a script.  For more info after installing xrandr type man xrandr

---

