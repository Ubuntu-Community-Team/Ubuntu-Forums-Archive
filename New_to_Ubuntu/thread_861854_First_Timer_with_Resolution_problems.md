---
title: "First Timer with Resolution problems"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Mister Cuddles on 2008-07-17
Hello, I'm a first time user of a Linux type OS, and as soon as I got the OS working I ran into a frustrating problem. 

My resolution is stuck at either 800x600 or 640x480 and with my [monitor]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00043882&lc=en&cc=us&product=365087&dlc=en") I usually run at 1024x768 resolution so the change looks huge to me.

I've looked online for a few fixits but I have to admit I'm not very apt at the workings of Ubuntu. I tried to follow the steps as much as possible and I can't seem to get things to work. Either what I'm doing is wrong, or I'm just not doing it right.

I'd appreciate any help I can possibly get.

Oh yea, if it makes a difference, I had a friend who's had SOME experience help me out a little, and he said I should post this snipit from the lspci command in the terminal.

> 00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

---

### Post by tuxxy on 2008-07-17
Nivigate to administration panel and find *restricted hardware drivers* see if you can enable the driver from here, from terminal it would be

```
sudo jockey-gtk
```

---

### Post by koji042 on 2008-07-17
I think that the problem is that Ubuntu can't properly auto-detect your screen. In that case, you can go to Places > Computer

Then go to Filesystem and navigate to /usr/share/applications and find an application called "Screens and Graphics"

From there, just find the proper model for your screen, or go to "Generic" and then click "LCD Panel 1024x768" or "Monitor 1024x768" depending on your screen type.

Hope that helps.

---

### Post by Mister Cuddles on 2008-07-17
Okay, so when I did what you said, my resolution got worse. It took away my 800x600 resolution and gave me two worse options.

EDIT: When I did what tuxxy told me to.

---

### Post by Mister Cuddles on 2008-07-17
> **koji042 said:**
> I think that the problem is that Ubuntu can't properly auto-detect your screen. In that case, you can go to Places > Computer

Then go to Filesystem and navigate to /usr/share/applications and find an application called "Screens and Graphics"

From there, just find the proper model for your screen, or go to "Generic" and then click "LCD Panel 1024x768" or "Monitor 1024x768" depending on your screen type.

Hope that helps.

That worked 100%. Thank you.

---

