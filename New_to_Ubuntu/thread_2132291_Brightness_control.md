---
title: "Brightness control"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-04-04
Hi, I am having trouble controling my brightness in my netbook (Asus X201E-KX006H). I can use this code:
```
xrandr --output LVDS1 --brightness 2
```
But it is not the same experience like in Windows (using fn keys..). Everything on screen just get whiter (using this code) and not brighter.
Thanks for every help.
Xubuntu 12.10 by the way..

EDIT1: When I am booting my Xubuntu, the screen is really at its (I would say maximum) brightness, but then it gets darker..

---

### Post by slickymaster on 2013-04-04
As you are on Xubuntu, I'm assuming you have Xfce4 as your desktop environment. If that's the case there's a plugin that manages the power sources on the computer and the devices that can be controlled to reduce their power consumption (**such as LCD brightness level**, monitor sleep, CPU frequency scaling).

At a terminal just run the following:
```
sudo apt-get install xfce4-power-manager-plugins
```

After that just right-click on the top panel, navigate to **panel > add new items** e search for  **“Brightness Plugin”**&#8203;.

---

### Post by ViliX64 on 2013-04-04
Thank you wery much slickymaster:) Now I can see on the sun again!

---

### Post by ViliX64 on 2013-04-04
By the way, what was the command:
```
xrandr --output LVDS1 --brightness (number)
```
for? For me, brightness is the same like the panel..

---

### Post by slickymaster on 2013-04-04
No need to thank. Glad you solved your problem.
Don't forget to mark this thread as solved, so other people searching the forums know that this thread provides a working solution for it. See my signature on how to do it.

---

### Post by ViliX64 on 2013-04-04
I think I know the way :)

---

### Post by slickymaster on 2013-04-04
> **ViliX64 said:**
> By the way, what was the command:
```
xrandr --output LVDS1 --brightness (number)
```
for? For me, brightness is the same like the panel..

**xrandr **is a command line utility available in your Linux system for reseting and resizing your screen resolution and/or the outputs of a screen.
**--output** is the option used to tell the xrandr command what is the output to be reconfigured.
**--brightness **speaks for itself.

See
```
man xrandr
```
for the full explanation.

---

### Post by ViliX64 on 2013-04-04
Yes, but it says its brightness.. And I imagine brightness like amount of power that is routing into my display..

---

### Post by slickymaster on 2013-04-04
Well, according to man page, the --brightness is a Per-output option to multiply the gamma values on the crtc currently attached to the output to specified floating value. Useful for overly bright or overly dim outputs. However, this is a software only modification, if your hardware has support to actually change the brightness, you will probably prefer to use xbacklight.

---

### Post by ViliX64 on 2013-04-04
Thank you, I am trying that right now:)

---

