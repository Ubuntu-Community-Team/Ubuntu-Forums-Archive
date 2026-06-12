---
title: "Screen resolution problem"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by beagle1 on 2012-05-21
I have installed Ubuntu LTS 12.04 64bit in my Laptop.
My current monitor setting shows 1024 x 768.  This resolution is slightly different from my laptop's specification.
Photos and images appear a bit skewed.  If I go to display setting, it shows only 2 options: 1024x768 and 800x600.
Is there anyway to fix the screen distortion?
Thanks in advace for your hep,

B1
 
Hardware:

Asus U46E Bal7 laptop
Intel i7; 64bit
Screen: 14.1 inch (1366 x 768 )

---

### Post by |{urse on 2012-05-21
you can try 

xrandr --fb 1366x768 --output LVDS --auto

in the Terminal.

---

### Post by |{urse on 2012-05-21
You can also use the command

xrandr -q

to list your current driver's modes.

---

### Post by beagle1 on 2012-05-22
Current driver has only two resolutions: 1024x768 and 800x600.
I think, I need a driver that can support Asus U46E

B1

---

