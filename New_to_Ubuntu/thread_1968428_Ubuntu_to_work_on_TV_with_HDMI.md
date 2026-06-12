---
title: "Ubuntu to work on TV with HDMI"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2012-04-29
Hi Guys could anyone please help? How do I get my netbook to work on my Tv with the HDMI cable?  It works on Windows and did work in Ubuntu briefly then stopped after updates, now there is just a blank screen on my TV I've just upgraded to 12.04 and I'd really like to do everything in Ubuntu.

Any help is greatly appreciated?

---

### Post by cheekymonky2010 on 2012-04-29
It's OK managed to get it working through displays in settings and simply turned the tv screen on in the displays box! now need to work out how to get it to fit correctly to the screen if anyone knows how that would be great?

---

### Post by souravc83 on 2012-04-29
Try installing the "disper" package

type 
```
sudo apt-get disper
```
in the terminal to install it. (I think it is available through the software center too.

after you are done, 
go to the terminal and type:

```
disper -c

```

to clone the displays.
For me, it automatically takes care of the resolution, but you can also specify the resolution through disper.

---

### Post by cheekymonky2010 on 2012-04-29
Thank you, got the screen to fit perfect by going into the menu on the TV itself and selecting "full PC mode"

---

