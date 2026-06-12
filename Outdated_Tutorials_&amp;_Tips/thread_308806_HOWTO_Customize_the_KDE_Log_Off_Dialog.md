---
title: "HOWTO: Customize the KDE Log Off Dialog"
date: 2006-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by groggyboy on 2006-11-28
Have you ever told Kubuntu to shut down, and found yourself annoyed to see a picture of Konqi sleeping on the moon?  Have you ever wished that it was a lovely picture of the Kubuntu logo instead?  Or a picture of your own design?  Well fret no more, because here's how to do it, in three simple steps.

1. Download the attached picture at the bottom of this post or create a .png of your own in the GIMP named "shutdownkonq.png" (the logo I'm using is from the [KubuntuArtwork Wiki page]("https://wiki.ubuntu.com/KubuntuArtwork")).

2. Create a folder at this location: "/home/<username>/.kde/share/apps/ksmserver".  Make another folder inside that one, called "pics".

3. Move the .png to that folder.

Finished.

To set it up from a terminal, copy and paste the following code:```
wget http://i14.tinypic.com/2jeoj1h.png
mkdir ~/.kde/share/apps/ksmserver
mkdir ~/.kde/share/apps/ksmserver/pics
mv 2jeoj1h.png ~/.kde/share/apps/ksmserver/pics/shutdownkonq.png
```

---

### Post by groggyboy on 2006-12-11
I was just perusing my old posts, and saw this one.  Just bumping it so more people get the chance to see (and use) it.

I'm surprised the Kubuntu devs haven't done something like this already.  :D

---

### Post by Lord Illidan on 2006-12-11
10x it looks better now, but a bit small. Still an improvement.

---

### Post by Rashid584 on 2006-12-11
My one only has "end current session" so i like it small :D

btw your commands don't work...wget wgets the php bit not the actual image. I think you should host the image on a free image host or something?

-Rashid

---

### Post by groggyboy on 2006-12-12
k, found a place to host the pic (its at [tinypic.com]("http://www.tinypic.com")).  wget should work now.  thanks for the heads up, rashid!

---

### Post by BatteryCell on 2006-12-12
Just wondering, where did you find that pic?

---

### Post by groggyboy on 2006-12-13
> **BatteryCell said:**
> Just wondering, where did you find that pic?

[KubuntuArtwork Wiki page]("https://wiki.ubuntu.com/KubuntuArtwork").

I tailored the image in the GIMP.  I s'pose i should give credit where credit is due!

---

