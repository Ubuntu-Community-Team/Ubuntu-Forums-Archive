---
title: "[SOLVED] Video drivers seriously broken."
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Vadi on 2008-09-21
I've broke my video to the point where I cannot get the real nvidia driver working *at all* anymore. I tried every possible solution - using xfix, deleting my xorg.conf, reconfiguting, reinstalling hardware drivers, dexconf, and envy. Nothing is working.

My video card is 8600gt, nvidia drivers were working just fine on it before I upgraded drivers with envy and then downgraded (they were buggy).

Here's my **Xorg.0.log** ([click]("http://pastebin.com/m73ccbd85")), and my **xorg.conf** ([click]("http://pastebin.com/m12673ece")). Can anyone please help me?

I'm always stuck on 800x600 unless I use xfix - that gets my resolution to normal (1440x900), however there is no direct rendering.

---

### Post by bawilson2 on 2008-09-22
I was having some strange behavior from my video drivers so I switched the the latest nvidia beta drivers.  Easiest way to install is to boot into the recovery mode drop into root shell at startup and run it from the command line.  See if it works for you.

[http://www.nvidia.com/object/linux_display_ia32_177.67.html](http://www.nvidia.com/object/linux_display_ia32_177.67.html)

---

### Post by phidia on 2008-09-22
I've been noticing frequent reports of problems with (particularly) 8 & 9 series nvidia cards so I'm interested in how this comes out, and perhaps a bug should be reported or subscribed too also.

---

### Post by Crafty Kisses on 2008-09-22
I'd like to see the results of this command:
```
glxinfo
```
I'd also like to know, did these issues just start occurring out of the blue, or did you change or attempt to do something and that's when the issues started?

---

### Post by Vadi on 2008-09-22
No this isn't out of the blue, if the said user would've stuck to the learnt lesson (which was, "Only let Ubuntu upgrade drivers"), everything would've still been fine. I upgraded drivers via Envy but because they were buggy I downgraded. Downgrade did not work...

Here's my glxinfo. I'll try nvidia drivers from their website, that's one last thing I've been holding off.

> vadi@ubuntu-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x48 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
vadi@ubuntu-laptop:~$ 


---

### Post by Vadi on 2008-09-22
Awesome. The driver requirements were tricky to satisfy, but I got it working now.

---

