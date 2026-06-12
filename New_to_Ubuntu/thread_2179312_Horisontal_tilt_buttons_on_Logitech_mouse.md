---
title: "Horisontal tilt buttons on Logitech mouse"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by Melhisedek on 2013-10-07
Is there a way for me to set horisontal left tilt as middle click? My middle click is kinda broken and in Windows I just binded left horisontal to middle mouse click. But I did it through Logitech Gaming software. Any chance of doing it in Ubuntu as well? Using G500s Logitech mouse.

Thank you for your time!

---

### Post by whitesmith on 2013-10-07
Here's how I'm changing the behavior of my Logitech Performance Mouse MX: [http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Guide-for-setup-Performance-MX-mouse-on-Linux-with-KDE/td-p/517167](http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Guide-for-setup-Performance-MX-mouse-on-Linux-with-KDE/td-p/517167)

---

### Post by Melhisedek on 2013-10-07
Well I have been trying to get this to work with no results sadly. "m:0x4 + c:37"

I tried installing xbindkeys_config and doing it through there but sadly no go. What is funny is that I can bind "xterm" or some other command to my b:6. But if I try Control+b:1 (which would simulate middleclick), or b:2, or "m:0x4 + c:37" which would be raw input. Nothing happens. I tried 
xbindkeys -n command to see what is going wrong but when I press b:6 nothing happens.

Any more help folks?

***EDIT***
I found out I didn't have xte installed... Now I want to kill myself :)

---

