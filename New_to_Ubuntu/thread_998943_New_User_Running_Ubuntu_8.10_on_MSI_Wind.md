---
title: "New User Running Ubuntu 8.10 on MSI Wind"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2008-12-01
I'm pretty new to the world of Ubuntu, only been using it for less than 5 days now. I decided to put it on my week old 6 cell MSI Wind (dual booting with XP Home).All I can say is Im loving this OS, haven't used Windows XP since I installed it.

One problem though is my battery life has gone from 4hrs and 30mins with XP to under 3hrs and 30mins with Ubuntu. This is with wireless on and bluetooth off and moderate to heavy use. I searched and installed/setup power saving programs and used methods mentioned in various threads. But I was wondering if there are any Wind specific power saving programs and methods (as all the others were for other laptops, so I couldnt implicate all methods). 

Also what are some temperature monitoring programs I can use to monitor HDD temp and etc. I tried installing one but it said it could pick up sensors. Im guessing it wasn't use to the Winds sensors, as speedstep in XP worked perfectly.

Any way thanks in advance for any help and sorry for such a long first post.

---

### Post by zzHanks on 2008-12-01
I don't know about the battery, but something about the temperature.

Check this out: [http://ubuntuforums.org/showthread.php?t=66238](http://ubuntuforums.org/showthread.php?t=66238) (lm-sensors and that, post #7) 

You may want to install the sensor-applet package too. 
After that you have to restart the panels
```
killall gnome-panel
```Then you should be able to add Hardware sensors monitor.

I almost forgot: You're probably want Hard drive temp too (hddtemp package).

---

### Post by jepong on 2008-12-03
try powertop

[http://www.lesswatts.org/projects/powertop/]("http://www.lesswatts.org/projects/powertop/")

---

