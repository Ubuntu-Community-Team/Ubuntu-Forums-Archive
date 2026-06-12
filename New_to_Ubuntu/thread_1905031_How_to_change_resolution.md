---
title: "How to change resolution?"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by braveswin11 on 2012-01-05
Ok, so i have a **Acer Aspire 5515** running **ubuntu 10.10**. Something happened with the resolution that changed it to 1024 x 68, and now when i boot to ubuntu a black screen comes instead of the boot splash screen.When this happens I can still hear the boot sounds, but can't see the screen. I know the resolution for this is 1280x800. A thread i was looking at was this : [http://ubuntuforums.org/showthread.php?t=1713043]("http://ubuntuforums.org/showthread.php?t=1713043")

I tried the first step in that thread which was xrandr.
This was my output: xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  

I saw that they created a new xorg.conf, but I do know that xorg.conf is different for different graphic cards. 

**My graphic card: ATI Radeon X1200**

Sorry about me being kind of new to ubuntu.:confused:

---

### Post by heyandy889 on 2012-01-05
Heh. No worries, dude! We all started there, at one point. If you already knew everything, there probably wouldn't be much point in starting the thread, would there?

This blog post looks promising.
[http://www.liberiangeek.net/2010/12/change-screen-resolutions-ubuntu-10-10-maverick-meerkat-arandr/](http://www.liberiangeek.net/2010/12/change-screen-resolutions-ubuntu-10-10-maverick-meerkat-arandr/)

From the blog post, I would take these actions. I assume you can get into a terminal? Ctrl-Alt-T is the default keyboard shortcut, I believe.

```
sudo apt-get install ARandR
ARandR
```

Welcome to the forums!

edit: does running "gnome-control-center" work? It might be an 11.04 thing. Worth a shot.

---

### Post by braveswin11 on 2012-01-05
Well, I already had ArandR, but when i start it and look in the resolution tab the only 2 options are 1024x768 which is already selected and 800x600. The one I need is 1280x800.

Also, when I type in gnome-control-center, a control center does open up. What should I do then?

---

### Post by braveswin11 on 2012-01-07
So, are there any ideas?

---

### Post by sailor2001 on 2012-01-07
system/preferences/monitor   click on x-server display

---

