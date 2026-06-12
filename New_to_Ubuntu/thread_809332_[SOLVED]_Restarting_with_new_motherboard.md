---
title: "[SOLVED] Restarting with new motherboard"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-05-27
Just changed to a better motherboard and fired up, checked BIOS and all seems to be OK.  Ubuntu seems to start off OK but will not complete start up.  I get to log on/ password and then the terminal line comes up.  So, what do I type after '....desktop~$' to get 7.10 running again?  I have tried help/start/getonwithit etc to no avail!
Got to be something simple!   Thanks

---

### Post by TeoBigusGeekus on 2008-05-27
How about
```
startx
```

---

### Post by Dumpy Dumpster on 2008-05-27
Thanks TeoBigusGeekus, that got things a bit further along the line.  The problem now is that Ubuntu does not recognize the ATI Radeon 7000 card that worked perfectly well with the old motherboard.  I tried to get to xorg.conf file (not sure what really to do if I did get there!!) but that was denied.  So it seems the monitor screen is not 'seen'.  Any further suggestions would be appreciated.

---

### Post by TeoBigusGeekus on 2008-05-27
Try this page
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by Dumpy Dumpster on 2008-05-30
Thanks.  Actually I gave up and installed Hardy Heron instead.  It seemed to be the simplest way out!

---

