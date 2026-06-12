---
title: "My sound disapeared"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by green96 on 2015-01-30
Hi, 
I am a new user, I use Ubuntu 14.04. I have restarted my system and I found that my sound have disappeared, I have no idea why. 

When ubuntu starts and the log screen appear I hear normal song but after it it doesn't work. 

I found info to do this operations:

sudo apt-get remove --purge alsa-base pulseaudi
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

but after it it I lost icon of sound next to the clock and also I lost some of my settings: 
[http://snag.gy/vvky1.jpg](http://snag.gy/vvky1.jpg)
 
Please help me.

---

### Post by sandyd on 2015-01-30
> **green96 said:**
> Hi, 
I am a new user, I use Ubuntu 14.04. I have restarted my system and I found that my sound have disappeared, I have no idea why. 

When ubuntu starts and the log screen appear I hear normal song but after it it doesn't work. 

I found info to do this operations:

sudo apt-get remove --purge alsa-base pulseaudi
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload

but after it it I lost icon of sound next to the clock and also I lost some of my settings: 
[http://snag.gy/vvky1.jpg](http://snag.gy/vvky1.jpg)
 
Please help me.

Looks like some stuff was removed due to dependencies.

Try
```

sudo apt-get install ubuntu-desktop
```

---

