---
title: "EeePC Screen Resolution FIX!!!"
date: 2009-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Ocxic on 2009-10-12
Ever since i got my EeePC, I've been trying to figure out how to get a higher resolution then 1024x600. I never found it very good at getting the most out of the screen.

I found this at forum.eeeuser.com ([http://forum.eeeuser.com/viewtopic.php?pid=645514](http://forum.eeeuser.com/viewtopic.php?pid=645514)) that allows you to scale your screen.

> 
```


xrandr --output LVDS --mode 1024x600 --scale 1.25x1.25


```This will enable a 1280x750 scaled resolution. Very useful for browsing the web and working with images. Just increase the DPI of your fonts to at least 120 and all will be readable, but you will have more space for windows on your screen.

That will work for a 1024x600 screen. If your screen has less (or more) resolution, you will have to change it in the xrandr command:

```


xrandr --output LVDS --mode <your-native-resolution> --scale <scaling-factor>


``` You can get other resolutions by changing the scale factor (i.e: --scale 1.5x1.5 to obtain a 1536x900 resolution).

But I think that 1280x750 is a good compromise between readability and screen space.

You might need to play around with your font settings as well to get everything perfect.(I find comic sans to be a good one) and turning off hinting seems to provide better results.

You will have to manually do this at every boot, but I'm sure you could write a small script to be run at boot the will set this for you, maybe:

```


#!/bin/sh
xrandr --output LVDS1 --mode 1024x600 --scale 1.25x1.25
fi


```

---

### Post by bapoumba on 2009-11-05
Sorry it took so long for the tutorial to be approved. Thanks for you patience :)

---

### Post by josvanr on 2009-11-08
hello

in gnome and xfce this works fine, but when I try this in kde, the desktop and panel sizes don't scale up. What I wind up with is a 
black screen, with a scaled version of the the original desktop 
sitting in the left top corner. Is this a kde bug?

(btw: i'm using a PB bg46 laptop and using kubuntu 9.10)

josvanr

---

