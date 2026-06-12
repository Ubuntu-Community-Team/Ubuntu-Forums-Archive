---
title: "Maintain fullscreen flash using two monitors"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by aryka on 2012-09-28
Hello, newbie here!

I am using Ubuntu 12.04 64bit. I have an NVIDIA GTX 260 card connected to an LCD monitor (1680x1050) and an HDTV (1920x1200). Twinview is enabled.

I can watch flash videos and they fullscreen correctly filling the screen, but as soon as I click something on the other screen the video drops out of fullscreen. 
In the hours I've spent googling for it, I found tons of people complaining about all sorts of flash problems, including old fullscreen problems and video not scaling or getting cut off. Some people even suggest installing wine and using a windows hack exe... 
So I thought I would check here before trying hacks that might break something else.

Tested with Chrome PPAPI enabled and disabled and with Firefox.
Tested sites Youtube, BBC iPlayer, other streams
 
Flash ver: 11,2,202,238 installed

Is there any way to make full screen stick? 

I don't need to interact with the video at all, and I don't care about flash games, etc. I need to keep an eye on the TV for my work and if I can't get the videos to stay put I won't be able to keep using linux.

---

### Post by SushiAddiction on 2013-02-15
Old post but I've had the same problem. I hope others find this answer.

This page gives you much info.
[http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html](http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html)

Easiest way to do what you want is
```
sudo sed -i 's/_NET_ACTIVE_WINDOW/_AET_ACTIVE_WINDOW/g' /usr/lib/flashplugin-installer/libflashplayer.so
```

Now you don't have to mess around with a hex editor. Use the command above and restart you browser. Use the command whenever you get a flash version update.

I wish dual monitor support was better for many things :/

---

