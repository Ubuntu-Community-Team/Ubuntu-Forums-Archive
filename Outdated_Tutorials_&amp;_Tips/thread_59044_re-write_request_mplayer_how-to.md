---
title: "re-write request: mplayer how-to"
date: 2005-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by floppy on 2005-08-22
Hey, I'm an idiot newbie. Can someone recap the mplayer thread into a new how-to?
[http://www.ubuntuforums.org/showthread.php?t=44560](http://www.ubuntuforums.org/showthread.php?t=44560)

Frankly, I get confused by all the old versions and corrections in the thread.

All I want is to get Firefox and Mplayer working happily together.

Thank you!

---

### Post by gammyhand on 2005-08-22
[QUOTE=floppy]Hey, I'm an idiot newbie. Can someone recap the mplayer thread into a new how-to?
[http://www.ubuntuforums.org/showthread.php?t=44560](http://www.ubuntuforums.org/showthread.php?t=44560)

Frankly, I get confused by all the old versions and corrections in the thread.

All I want is to get Firefox and Mplayer working happily together.

Thank you![/QUOTE]
 I also would like to know how to get videos to open in mplayer rather than in the browser (if possible). Also, why do only certain types of video stream? wmv streams on windows but requires downloading first in ubuntu etc.

---

### Post by Tralobyte on 2005-08-22
This post was moved to the main thread. See the forum rules.

---

### Post by arnieboy on 2005-08-22
[QUOTE=gammyhand]I also would like to know how to get videos to open in mplayer rather than in the browser (if possible). Also, why do only certain types of video stream? wmv streams on windows but requires downloading first in ubuntu etc.[/QUOTE]
Make your /etc/mplayerplug-in.conf look like this and all your posted issues will be resolved:
```
#debug=0
#logfile=$HOME/mpp.log
#vo=xv,x11
#ao=alsa,esd,oss
download=0
#dload-dir=$HOME/tmp
#keep-download=0
noembed=1
#cachesize=1024
#use-mimetypes=0
#enable-real=0
enable-wm=1
#enable-qt=1
enable-mpeg=1
#enable-ogg=1
#enable-smil=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer

```

Moderators please move this to the appropriate forum.

---

### Post by gammyhand on 2005-08-23
Thanks :)

---

