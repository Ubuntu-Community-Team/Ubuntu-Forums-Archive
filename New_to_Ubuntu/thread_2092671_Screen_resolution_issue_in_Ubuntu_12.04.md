---
title: "Screen resolution issue in Ubuntu 12.04"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by alseba on 2012-12-08
I'm trying to switch the screen to higher resolution to no avail (I'm running Ubuntu 12.04). The display is Samsung device originally capable of 1280x1024, but currently it only shows 1024x768. The graphics adapter is nVidia  GeForce 7300GT. 

I tried to create a new rendering mode for with data I got from *cvt* util :
```
cvt -r 1280 1024 60

#nano ~/.xprofile
--------------------------------------------------------------------------------
xrandr &#8211;newmode &#8220;1280×1024&#8243; 90.75  1280 1328 1360 1440  
                                       1024 1027 1034 1054 +hsync -vsync
xrandr &#8211;addmode DVI-0 &#8220;1280×1024&#8243;
xrandr &#8211;addmode VGA-0 &#8220;1280×1024&#8243;
xrandr &#8211;output DVI-0 &#8211;mode &#8220;1280×1024&#8243;
xrandr &#8211;output VGA-0 &#8211;mode &#8220;1280×1024&#8243;
```but I can't figure out how to bootstrap it (is that  how it's called?). Anyway, it doesn't show up in *xrandr* output.

And seeing how proprietary nVidia drivers are quite notorious,  I didn't  bother with those.

 Help would be much appreciated! Cheers! :D

---

### Post by ibuclaw on 2012-12-08
> **alseba said:**
> And seeing how proprietary nVidia drivers are quite notorious,  I didn't  bother with those.

Notorious as they are, using them (and configuring through nvidia's config manager) might just give you the resolution you desire.

---

### Post by alseba on 2012-12-09
[LEFT]I downloaded the 9X.XX drivers from nVidia website, and they won't install as long X is not stopped. However, when I try for *sudo service lightdm stop* , I can no longer execute any commands (the system accepts keyboard input, but doesn't parse anything and calling the terminal via Ctrl+Alt+T doesn't work either). 

I sometimes managed to get the terminal window in the same state, so I just used to abandon it and start a new one instead. 

 My first  *nix attempt started this Wednesday, so I'm like a ball of confusion and stupid questions right now, sorry.
[/LEFT]

---

### Post by ibuclaw on 2012-12-09
> **alseba said:**
> [LEFT]I downloaded the 9X.XX drivers from nVidia website, and they won't install as long X is not stopped. However, when I try for *sudo service lightdm stop* , I can no longer execute any commands (the system accepts keyboard input, but doesn't parse anything and calling the terminal via Ctrl+Alt+T doesn't work either). 

I sometimes managed to get the terminal window in the same state, so I just used to abandon it and start a new one instead. 

 My first  *nix attempt started this Wednesday, so I'm like a ball of confusion and stupid questions right now, sorry.
[/LEFT]

Are the drivers not available through hardware drivers tool? (System Settings > Additional Drivers)

---

### Post by alseba on 2012-12-09
Wow, I missed those. Derp.

One set actually added 1152x864 mode along with some noticeable glitches. Will test  more later.

---

