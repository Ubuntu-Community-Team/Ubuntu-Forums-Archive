---
title: "Well, tried to get my screen res above 640x400 but no luck.."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Linuxwho? on 2008-05-31
Hi All, I did the search first and tried the splash file but my screen still refuses to see anything above 640x400 resolution.  I went to the HP site to see the drivers for the 15" HP 1530 flat screen and all they have is for XP.  Am I outta luck?

---

### Post by spiderbatdad on 2008-05-31
what video card?

---

### Post by Linuxwho? on 2008-05-31
I honestly dont know...its an inboard on an old 550mhz compaq proliant 1850R.

I did find "xvidtune" but afraid to touch it cuz it says WARNING WARNING WARNING

---

### Post by spiderbatdad on 2008-05-31
how about the output of this:
```
sudo lshw -C video
```

---

### Post by Linuxwho? on 2008-06-01
> **spiderbatdad said:**
> how about the output of this:
```
sudo lshw -C video
```

It says B.02.12.01

.. Ok, I outputed it as html and got 3d rage IIc 21511C [mach64 GT IIC]/...hmmm I doubt that is correct, lol.  Sounds too current for this machine!

---

