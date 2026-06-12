---
title: "black screen at log in?!"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by andyho on 2008-08-09
Yesterday I had a power outage.. Upon rebooting, after I log in I have a lovely black screen. I see the splash screen, it goes black and then can hear the boot up sound. I already pulled my xorg file and it looks like my nvidia settings got dumped but every time I sudo dpkg-reconfigure -phigh xorg-server all it does is create another file it doesn't go thru the settings selection like it used to?! Any ideas what I should do? Thanks!!

**quick edit**
I also plugged my monitor to my onboard and it's not recognizing it at all, so at least that isn't causing me issues like before..

---

### Post by ajgreeny on 2008-08-09
If you are running Hardy, you could try booting to recovery mode and choosing xfix when you get to the menu.  As I understand it that will go through the detection routine as if it was installing again and should give you a GUI from which you can reinstall the nvidia driver again if needed.

---

### Post by andyho on 2008-08-09
Well I was able to get my screen back. I think my xorg file keeps dumping the nvidia settings. If I lspci | grep VGA, I get..
[COLOR="SeaGreen"]02:03.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)[/COLOR]

but glxinfo gives me..
[COLOR="SeaGreen"]name of display: :0.0
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
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None[/COLOR]

I also have Nvidia X Server Settings now in my app launcher now.. but when I click on it I get.. [COLOR="SeaGreen"]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. [/COLOR] But I've done that.. 

So is there any way to make the settings stick?! And also is there a way to do like a system scan to see if anything is out of place? Just settings or files? Thanks for all the help!!

---

