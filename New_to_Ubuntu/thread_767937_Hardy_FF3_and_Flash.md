---
title: "Hardy FF3 and Flash"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by bprof on 2008-04-26
I was trying to watch this video on youtube 

[http://www.youtube.com/watch?v=oDLscVzTlzc](http://www.youtube.com/watch?v=oDLscVzTlzc)

FF ask for installing a missing plugin to run flash, I choose Gnash. I can see the black screen now, I can see the movie controls and that the whole movie was downloaded, but I can't see it I can't play it, nothing.

Did anyone have the same experience? How did you make it to work? I've tried to uninstall the plugin to install another one, but I cant disable or enable any plugin :confused:

---

### Post by dangerpl on 2008-04-26
How did you install your plugin? Did you install all the gstreamer codecs?

---

### Post by Dr.Gringo on 2008-04-26
Uninstall the plugin and then go [Here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") Install by running in terminal (double click and choose run in terminal)

---

### Post by bprof on 2008-04-26
When I open youtube for the fist time, FF3 poped up asking for installing a missing plugin and it gave me three options one is gnash, the other two are flash encoder and swfdec. I've chosen gnash. The codecs are installed, but if I tried to test another video I will be asked one more time to install gsreamer codecs, so I did, and the video window shows up on youtube page with control and everything, the second counter increases but the window is black and there is no voice.

---

### Post by ad_267 on 2008-04-26
Uninstall the Gnash plugin and use synaptic to install flashplugin-nonfree or use
```
sudo apt-get install flashplugin-nonfree
```
You might want to install the ubuntu-restricted-extras package instead. This gives you flash, mp3, java and other useful things.

---

### Post by bprof on 2008-04-26
I uninstall gnash, installed swfdec the video plays but no sound. I've uninstalled that and installed Adobe flash, the video plays but no sound.

I can play a dvd without any problem.

---

### Post by bprof on 2008-04-26
Is there something I need to do to have sound in videos played in FireFox 3?

---

### Post by gandaran on 2008-04-26
> **bprof said:**
> Is there something I need to do to have sound in videos played in FireFox 3?

try runnig firefox as root,« sudo firefox » sometimes this way works.

---

