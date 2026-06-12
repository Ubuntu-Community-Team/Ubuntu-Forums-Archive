---
title: "xorg.conf"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by TrakerJon on 2008-05-21
[SIZE="3"]How come in Hardy sudo dpkg-reconfigure -phigh xserver-xorg won't bring up the x configuration utility like Gutsy did?[/SIZE]

---

### Post by spiderbatdad on 2008-05-21
The -phigh flag only asks high priority questions, otherwise xorg is silently reconfigured. If you want the interactive interface run: sudo dpkg-reconfigure xserver-xorg

---

### Post by TrakerJon on 2008-05-21
[SIZE="3"]**That helped somewhat but it didn't allow me to set the display resolution as in Gutsy. Has something changed?**[/SIZE]

---

### Post by spiderbatdad on 2008-05-21
Sounds like hardware detection problem. Can you run:```
dmesg >> dmesg.txt
```Then right click the file in your home folder and select create an archive? Upload the archive here.

---

### Post by Motorhead Kaze on 2008-07-01
Hello? Your thread is a month an a half old BUT, I had that same question about -phigh... and my computer is not "Seeing" my second monitor, although both are plugged in. 

SPIDERBATDAD?
Can you tell me how to make Ubuntu (Hardy) see both monitors?

(Long story, short version: Yesterday I had dual monitors, extended desktop on Hardy i386, using an ATI graphics card and the fglrx driver. Upon a fresh install of Hardy today, now xrandr claims I only have "Screen 0", where yesterday I had VGA 0 and DVI 0)

Please help me find my hardware?  I appreciate any help!

Just in case you ask, I am posting my dmesg.txt archive here too.  Hope you are still tuned in!

---

### Post by Tatty on 2008-07-01
X has changed somewhat in hardy, and is much better at autodetection.  As a result the xorg.conf file is less important and most things such as resolution should be autodetected.

However, It is still possible to manually configure things in the xorg.conf file if you wish to.

[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)  This thread should explain it better.

[http://ubuntuforums.org/showthread.php?t=846098](http://ubuntuforums.org/showthread.php?t=846098)  Please see this thread for information on how to add a second monitor.

---

### Post by Motorhead Kaze on 2008-07-01
Thank you so much for your help!

You are right, Hardy WOULD HAVE detected my monitor, BUT as I just found in another thread, the cause turned out to be that I had the propriety driver for my graphics card turned on today...yesterday I did not.

But now that my mood is FAR better, I am going to enjoy reading your links all the more.

Peace.

---

