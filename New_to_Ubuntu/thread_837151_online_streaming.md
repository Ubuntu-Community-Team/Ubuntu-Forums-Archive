---
title: "online streaming"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Abu Noor-Eddin on 2008-06-22
Hi all, 

I am new to linux. 

I installed Ubuntu 8.04 LTS yesterday, but I cannot play online audio or listen to online radio station. 

Any help?

---

### Post by MasterSander on 2008-06-22
mp3 and other file extensions that are somehow copyright protected in some way are not standardly in ubuntu, you have to install them yourself. If you try to play an mp3 file in totem mediaplayer it will automatically ask you if you want to install these packages.

---

### Post by spiderbatdad on 2008-06-22
Try ```
sudo apt-get install ubuntu-restricted-extras
```you will have to accept an eula for some of the meta package...like sun-java.

also try ```
sudo apt-get install streamtuner
``` for streaming radio stations, though gstreamer will work if you input the url.

for streamtuner you either need to install xmms or change the settings to totem.

---

### Post by PhilJ on 2008-06-22
have you got the plugins installed in firefox ?  I find that the Mplayer plugins are best for me . I use it to listen to the BBC audio streams. You should have Totem plugins installed by default. in the address bar of firefox type      

about: plugins

this will show you what plugins are installed.

you will find  mozilla-mplayer in the repositories. best way is to google for Medibuntu and follow the instructions there to install the media codecs needed 

I always remove totem gstreamer and its  plugins as I fnd they dont work very well for me, my own pesonal preference. YOu could change Totem gstreamer to Totem Xine and try that. 

Phil

---

### Post by Abu Noor-Eddin on 2008-06-22
> **MasterSander said:**
> mp3 and other file extensions that are somehow copyright protected in some way are not standardly in ubuntu, you have to install them yourself. If you try to play an mp3 file in totem mediaplayer it will automatically ask you if you want to install these packages.

Totem does not play mp3 however I am installing the mp3 codec for it !!

---

### Post by Abu Noor-Eddin on 2008-06-22
> **spiderbatdad said:**
> Try ```
sudo apt-get install ubuntu-restricted-extras
```you will have to accept an eula for some of the meta package...like sun-java.


I am installing them now .....

---

### Post by james_vanb on 2008-06-22
If you haven't already, follow this tutorial.  It should get you all sorted out:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Abu Noor-Eddin on 2008-06-22
> **PhilJ said:**
> have you got the plugins installed in firefox ?  I find that the Mplayer plugins are best for me . I use it to listen to the BBC audio streams. You should have Totem plugins installed by default. in the address bar of firefox type      

about: plugins

this will show you what plugins are installed.


Yes totem plugins are installed

---

### Post by Abu Noor-Eddin on 2008-06-22
> **james_vanb said:**
> If you haven't already, follow this tutorial.  It should get you all sorted out:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Thanks for the tutorial but the problem still exists.

---

