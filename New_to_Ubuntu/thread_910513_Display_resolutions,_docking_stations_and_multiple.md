---
title: "Display resolutions, docking stations and multiple displays"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by moody_mark on 2008-09-04
Hi, Id like to get some good references for a relative newbie like me to be able to get to grips with setting up displays. 

Heres the scoop... Im gradually making the switch to ubuntu. I got two PCs at home running, kubuntu, xubuntu and this Dell Latitude 610 laptop for which i have an old 40GB drive running ubuntu, another old 15GB drive with kubuntu installed and the original HDD with windows XP.

I started off mucking about on the home PCs, once I got some confidence I took the old 15GB drive and installed Kubuntu, it ran great even booting from USB in a caddy and then I decided to put ubuntu on another spare 40Gb I snaffled from work (it would have only gotten binned).

So, to the point of my question. At work I have a nice Dell flat screen that runs 1680 x 1050. Now with the kubuntu HDD in I can pop my laptop into the docking station and change the resolution and it works like a charm. With the ubuntu HDD i had a lot of problems today, it seemed that the resolution manager although I was selecting the right size it just stretched out the display.

I looked around on this forum and theres a lot or talk about xorg.conf settings etc. However I dont really understand it all, im a newbie and the xorg.conf man entries are too long winded. My xorg.conf shows the following for my display regardless of what im plugged in to (just pasted the display bit);

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

What id like to know is regardless of wether im using this laptop as is with the single screen, or plugged into the docking station at work, the xorg.conf file remains the same but the gnome monitor resolution settings shows the screens i have plugged in. Also the gnome resolution settings although it shows two screens, i cant seem to make any changes stay applied it keeps reverting. Perhaps theres a better tool for the gnome desktop for adjusting these settings?

If anyone has some good comprehensive guides that would get me started then that would be great.

Thanks :)

---

### Post by Peter09 on 2008-09-04
What graphics card are you using?

---

### Post by moody_mark on 2008-09-04
Heres my graphics card

```
curtis@Barney:/etc$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

---

