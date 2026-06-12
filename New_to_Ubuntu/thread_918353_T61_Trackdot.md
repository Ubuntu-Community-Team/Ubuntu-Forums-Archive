---
title: "T61 Trackdot"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by dsurge on 2008-09-12
Hi, I'm new to the ubuntu community, recently switched from XP. I hope Ubuntu can be my new home and I'm ready and willing to learn. I'm trying to learn the terminal code so I can get my way around with less GUI, but I need some help on my first issue.

I've looked around but I'm not sure how to do this. I'm on a Lenovo T61 7664-16U and most of the things are working great, just one thing: is there a way to speed up my trackdot (the red dot in the middle of the laptop)? In windows I went to the Ultranav driver and set the speed to full, but when I change the mouse sensitivity in Ubuntu it doesn't change anything. It does accelerate faster when I fix that, but I want faster speed and sensitivity not acceleration. Anyway to do this? Or any way to import the ultranav driver from windows?

Thanks a lot everyone :D

-Surge

---

### Post by Whiffle on 2008-09-12
Easy!  

you'll need sysfs utils:

```

sudo apt-get install sysfsutils

```

and then, using this tutorial:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Sensitivity_.26_Speed](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Sensitivity_.26_Speed)

you can play with your sensitivity and speed till you get them how you want them.  Once you've got the numbers you like, edit /etc/sysfs.conf
```

sudo nano -w /etc/sysfs.conf

```
to look like this (but with your numbers)
```
devices/platform/i8042/serio1/serio2/speed=120
devices/platform/i8042/serio1/serio2/sensitivity=250

```

Thats what I have it at on my T43, there might be some slight variation in the file path for your T61, I'm not certain.

---

