---
title: "Dual monitor lags"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by ruddi on 2013-03-15
Hello, this is my first thread so I am sorry if I am doing something wrong.

When i plug in my hdtv with hdmi cable and enable Dual-monitor via catalyst control center, ubuntu gets all laggy and uncomfortable, if the hdtv is unplugged everything runs smooth and nice.
my question is what can I do to make it as smooth as when I only have my primary display enabled, I have searched google for hours and hours and have not found a thing that can help me.

I have a fresh copy of Ubuntu 12.04LTS 
Specs
Radeon hd 7950 with drivers installed from the amd homepage.
athlon x4 620 @3.6ghz 
4gb of ram

---

### Post by ruddi on 2013-03-15
I saw this on youtube but I am not sure if I can post links here from youtube.. :) 

-Open a terminal
-Type: sudo gedit /etc/X11/xorg.conf
-Add the following lines to the file:
Option"TripleBuffer" "True"
Option"BackingStore" "True"
Option  "PixmapCacheSize" "300000"
Option  "OnDemandVBlankInterrupts" "True"
Option  "InitialPixmapPlacement" "2"
Option  "GlyphCache" "1"
-Save
-Restart

This increased performance for me allot but if anyone has other suggestions I am all ears because the performance is still not as good as i would have wanted it to be. Still a little sluggish when opening and closing windows and dragging them

---

### Post by ruddi on 2013-03-15
No one? :)

---

### Post by ruddi on 2013-03-16
Has no one really encountered this problem before?

---

### Post by ManamiVixen on 2013-03-16
I know what is wrong. Your graphics card is too weak. Ubuntu Unity by default creates four virtual desktops on a single monitor from which you can work, all of which are treated as actually existing. Meaning your main monitor's resolution is effectively double lengnth and width wise, creating 4x the volume (the four desktops). So if your monitor 1680x1050 as an example, Ubuntu will virtually stretch it to 3360x2100 and then put four virtual desktops on it but will tell the GPU to only focus on one quadrant of the resolution despite the GPU having the four desktops in memory. So by adding a second monitor, Ubuntu effectevly creates 8 virtual desktops with corrisponding quadrants on both monitors moving in sync when you switch dektops. In the end, your card dosent have the oomph to keep up with all the data. But you can fix this by disabling virtual desktops using a Unity Tweak tool. Like Ubuntu Tweak or something like that.

---

### Post by ruddi on 2013-03-17
Thank you so much! :)
I actually had only 2 virtual desktops enabled in Ubuntu tweak, but when I disabled the other desktop it runs better and again thank you so much :)

But shouldn't the ati radeon hd 7950 be able to run 2 virtual desktops (or 4 with the tv plugged in)

---

