---
title: "VLC Closing unexpectedly when playing mp3 files"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by rrsk on 2011-12-21
Am using ubuntu 11.04....VLC version: 1.1.9-1ubuntu1.3
VLC Closing unexpectedly when playing mp3 files
any solution?

Note: VLC works properly for when i didnot connect to internet(offline usage) (i.e) only when i connected to internet
it tries to connected to a music site(see logs) and then fails and so closes unexpectedly

> [0x1dc17c0] signals interface error: signal 17 overriden (0x7fdc4a37a450)
[0x1dc17c0] signals interface error: /usr/lib/libQtCore.so.4(?)[(nil)]
[0x243e4f0] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x243e4f0] access_http access error: error: HTTP/1.0 407 Proxy Authentication Required
[0x243e4f0] access_mms access error: cannot connect to [www.last.fm:80](www.last.fm:80)
[0x2409820] main art finder error: no suitable access module for `[http://www.last.fm/music/Why](http://www.last.fm/music/Why) This Kolaveri'di/3.mp3'
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0x1dc17c0] signals interface error: signal 17 overriden (0x7fdc4a37a450)
[0x1dc17c0] signals interface error: /usr/lib/libQtCore.so.4(?)[(nil)]
Segmentation fault

---

### Post by emmomalick on 2011-12-21
Did you have install Ubuntu Restricted Extras?

[http://packages.ubuntu.com/search?keywords=ubuntu-restricted-extras](http://packages.ubuntu.com/search?keywords=ubuntu-restricted-extras)

---

### Post by rrsk on 2011-12-21
> **emmomalick said:**
> Did you have install Ubuntu Restricted Extras?

[http://packages.ubuntu.com/search?keywords=ubuntu-restricted-extras](http://packages.ubuntu.com/search?keywords=ubuntu-restricted-extras)
ya i have installed it already

---

### Post by emmomalick on 2011-12-21
So if you're using two graphic cards at the same time, disable one of them using BIOS if possible as it may be that the system is being confused by the hardware choice in some way.

---

### Post by emmomalick on 2011-12-21
Have you tried changing the video output device to something other than default? Often sudden closure of programs like vlc or MPlayer is related to innapropriate video or sound settings. I attach a screenshot to illustrate the section in the preferences that I am referring to.[IMG]http://ubuntuforums.org/attachment.php?attachmentid=130356&d=1254385100[/IMG]

---

### Post by rrsk on 2011-12-21
> **emmomalick said:**
> Have you tried changing the video output device to something other than default? Often sudden closure of programs like vlc or MPlayer is related to innapropriate video or sound settings. I attach a screenshot to illustrate the section in the preferences that I am referring to.[IMG]http://ubuntuforums.org/attachment.php?attachmentid=130356&d=1254385100[/IMG]
i set that to default only......
whether i have to try it with other options?

---

### Post by emmomalick on 2011-12-21
Yes, you have to try it with X11 Video Input. As shown in the image. Try it and do inform me. Thanks

---

### Post by emmomalick on 2011-12-21
> **emmomalick said:**
> Yes, you have to try it with X11 Video Input. As shown in the image. Try it and do inform me. Thanks
A spell mistake its not (X11 Video Input) its X11 Video Output.

---

### Post by rrsk on 2011-12-21
i tried........but still having problem......pls refer error logs for more info

---

### Post by rrsk on 2011-12-21
this problem solved.....it is bcos of one mp3 file that tries to connect to a site when we load VLC...

---

