---
title: "[SOLVED] Another Linpus Lite Query"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by s.fox on 2008-10-04
Hi everyone,

As mentioned in my previous post I have recently purchased an Acer Aspire One running Linpus Lite.  I have been able to install the desktop switcher and XFCE menu without any problems and now the icons sit nicely on the menu bar at the bottom of the screen.  This was done purely to get rid of the childlike quadrant menu.

One of the first things i did with the acer is enable the right click menu on the desktop.  Now that i have the XFCE menu icon this is no longer needed.  I tried going into Desktop Preferences and unticking "Show desktop menu on right click".  This didn't work and its utterly baffling.  

I am new to this distro,  but I am pretty sure I am doing it correctly.  If someone could help me disable the right click menu it would be very appreciated.

-Ash R

---

### Post by s.fox on 2008-10-04
**Update: ** I have finally got it to work!  

I have noticed something very odd though,  the desktop background image will not show until I go change any setting in the Desktop Settings.   I get it to show and then when I restart its gone!  Has anybody got any clue whats happening and how to fix it?

Thank you for any help.

-Ash R

---

### Post by s.fox on 2008-10-06
**More information:**  The background solid colour i have set will load up ok,  its just the image itself.  If somebody could tell me how to set the desktop background image from terminal i think i may be able to force the system to load it.  I know this is probably the wrong way of doing it,  but i am totally out of ideas.

Many thanks,

-Ash R

---

### Post by s.fox on 2008-10-09
Is it just not possible to change the desktop wallpaper from terminal?  

Google has been hopeless, as all it finds is ways of setting the terminal as the desktop wallpaper :(

I am totally stuck and don't know how to proceed.  Any help would be great.

---

### Post by s.fox on 2008-10-09
Good news everyone!

I managed to get the desktop wallpaper to load when i boot up:)
I was able to do by running this automatically when I boot up: ```
xfdesktop -reload
```

I think I have now finished fine tuning my Acer.  I know I could install a different distro but I don't think I will bother as Linpus seems to be running very well for me.  

-Ash R

---

