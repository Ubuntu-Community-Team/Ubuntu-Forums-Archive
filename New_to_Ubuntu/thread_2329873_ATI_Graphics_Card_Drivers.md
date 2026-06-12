---
title: "ATI Graphics Card Drivers"
date: 2016-07-05
forum: New to Ubuntu
---

### Post by Diogo_Gomes on 2016-07-05
I received an old laptop, an ASUS A6Q00VA, with intel pentium M 750, 1Gb of RAM, and an ATI X700 Mobility Radeon Graphics Card, and installed ubuntu mate on it. It runs really well, but when i try to play youtube videos, the sound is fine, but the image is really bad, stuttering frequently even at low resolutions. I don't think these problems existed when it run XP. Maybe it's a drivers problem?

Some more info:
When i run dmesg, it shows no boot errors for the card
The output of lspci | grep VGA shows
```
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV410/M26 [Mobility Radeon X700]
```

---

### Post by QIII on 2016-07-05
AMD dropped Linux support for that card about eight years ago.  What it does or does not do in Windows is not material.

When you install Ubuntu, you get an open source driver known as Radeon.  Although it is very much improved over years past, with that old, graphics card you are just not going to get much.

---

### Post by Diogo_Gomes on 2016-07-05
So, basically, there's nothing i can do?

---

### Post by X-RED_Tech on 2016-07-05
You're most likely using the best solution available already.


> [COLOR=#000000]I don't think these problems existed when it run XP[/COLOR]
I believe you. Youtube worked pretty well with even weaker hardware back in 2006 but how is that relevant now?

Have you tried with another browser (Chromium, just an example...)?
Also your best bet is to make sure Youtube is playing with html5 instead of Flash, although html5 taxes CPU/GPU heavily and 1GB RAM is barely enough for Firefox with some tabs open nowadays so you have to be realist in your expectations about that machine.

---

### Post by poorguy on 2016-07-05
[COLOR=#000000]*Well this is what solved all all of my problems with videos on youtube using Ubuntu Mate 16.04.*[/COLOR]

[COLOR=#000000]*After it is installed go into settings under Misc look for "*[/COLOR][B]Force the use of flash player on all youtube.com" and [B]uncheck it IMO.

[http://www.slimjet.com/](http://www.slimjet.com/)


[/B][/B][COLOR=#000000][I]My graphics card:
[/I][/COLOR]Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV370 [Radeon X600] 

Nothing to lose by trying.

---

