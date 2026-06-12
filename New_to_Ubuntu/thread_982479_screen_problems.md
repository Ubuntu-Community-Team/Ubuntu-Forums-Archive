---
title: "screen problems"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by slammed87d21 on 2008-11-14
I installed 8.04.1 on my Aspire One and everything worked fine. I was going through the Wiki setting it up, and after I rebooted it, theres a screen that comes up saying it cannot recognize my screen. It also asks if I want to run in low graphics mode. If I tell it to continue in low graphics mode, everything is stretched from sise to side. Any suggestions on what I've done wrong? Thanks in advance.

---

### Post by slammed87d21 on 2008-11-14
Anyone?

---

### Post by eternalnewbee on 2008-11-14
Hi there. Go to: **Main Menu > System > Administration > Hardware Drivers**, and check if your graphic card is enabled.

---

### Post by slammed87d21 on 2008-11-15
in that window, when everything was working ok, nothing was there. also, the only thing that was there when i did the install, was the generic wirekess drivers which i got rid of in favor if ndiswrapper. i started having problems after doing this:

VIDEO AND 3D PERFORMANCE: (Optional)

Out of the box, the graphic card Intel GMA 950, is well detected, however you can tweak /etc/X11/xorg.conf to achieve better graphic card performance:

Section "Device"
(...)
        Option "MonitorLayout" "LVDS,VGA"
        Option "Clone" "true"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        VideoRam       229376
        Option "CacheLines" "1980"
EndSection


im unsure if i may have typed in something wrong, but like i said. it started after i did tat and rebooted. i would go back to the way it was, but id like to figure out what i did wrong if i can. oh, and that was on [https://help.ubuntu.com/community/AspireOne#VIDEO%20AND%203D%20PERFORMANCE:%20(Optional)]("https://help.ubuntu.com/community/AspireOne#VIDEO%20AND%203D%20PERFORMANCE:%20(Optional)")

---

### Post by jimmy the saint on 2008-11-15
If you did not make a backup of the file before you edited (hold out hand for proper slapping!) then you can issue this command to reset xorg.conf.  It is always better to back up the file though so you don't lose any tweaks that the system made for input devices (also controlled by xorg)

```
dpkg-reconfigure xserver-xorg
```

if you did back up the file, just replace the one you tweaked with your backup.

---

### Post by slammed87d21 on 2008-11-15
I know....not backing things up first, wasn't the brightest thing I've done. Well, I ran the command you gave me, and it fixed my screen. The only problem now is that my wireless doesn't work now. I tried re-installing ndiswrapper and the Windows driver to no avail. Did running that command mess with my wireless, and how do I fix that now?

---

### Post by jimmy the saint on 2008-11-15
I did a quick google search and saw that a few reports of a similar issue have been made.  I honestly had no idea that xorg.conf settings could impact wirelless at all until you just brought it up!  I would recommend searching google a bit, then posting a new thread with that issue "xorg changes disabled my wireless" or something to that affect. 
Good luck

---

