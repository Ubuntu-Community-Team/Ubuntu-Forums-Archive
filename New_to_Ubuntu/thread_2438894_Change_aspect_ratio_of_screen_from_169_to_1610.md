---
title: "Change aspect ratio of screen from 16:9 to 16:10?"
date: 2020-03-19
forum: New to Ubuntu
---

### Post by pkr19792 on 2020-03-19
Hi,

In the display settings I can change the resolution (aspect ratio) to either 1920x1080i (16:9), 1920x1080 (16:9) and 1280x720 (16.9).

However, I have an Eizo screen thats 16:10... so now I have a black field at the top and one at the bottom. Is there a way to force that aspect ratio?

If I use a Display Port cable from my mac it will automatically be 16:10, but when I use an HDMI cable it doesnt (there is no display port on my Ubuntu computer).

Cheers
Peter

---

### Post by him610 on 2020-03-19
Isn't 16:10 equivalent to 8:5? 
I may be wrong, but I think display resolution 1680x1050 is pretty close to what you are looking for.

---

### Post by CatKiller on 2020-03-19
They're after 1920×1200.

It sounds like that monitor's doing its own funky thing: assuming that if you're using HDMI then you want it to be a TV. The resolutions that are made available in Ubuntu are the ones that your monitor says it can do through EDID; in this case your monitor is lying. There are a bunch of posts about how to overcome that; the gist is that you want to tell X to ignore your monitor's EDID and provide your own values for HorizSync and VertRefresh. The resolutions your monitor can do can be calculated from that. Otherwise you can grab the EDID from when it's connected over DisplayPort and tell X to use that EDID rather than the one from the monitor. Either approach should work.

---

### Post by vanadium on 2020-03-20
The 16:10 resolution indeed should normally be available. You may want to try adding your custom resolution according to [http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)

---

### Post by pkr19792 on 2020-03-20
Seems to be a limitation from Eizos side. I found a dvi cable Im using instead.

---

