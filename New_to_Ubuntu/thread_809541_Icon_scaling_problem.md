---
title: "Icon scaling problem?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-27
Applying custom icons to any folder/launcher gets distorted above zoom level >=150
I had folders having scalable PNG icons (of size 256x256) set at 400% zoom level. In Hardy, they seem to become pixelated when zoomed. I reported a bug, but I was told:
1. Bug has already been reported and is of **low priority** :mad:
2. Non svg's don't scale properly.. (they did very well in Gutsy)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/234438](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/234438)

Will this ever be solved?

---

### Post by Paqman on 2008-05-27
> **LinuxIsInnovation said:**
> 
2. Non svg's don't scale properly.. (they did very well in Gutsy)


Svg stands for Scalable Vector Graphics. They're designed to scale, so it's hardly surprising they do it better than other types.

---

### Post by sayakb on 2008-05-28
Yes I do know about the vector and raster graphics theory, but I don't understand, when a 256x256 PNG is showed at 400% zoom, it does not need to be scaled (since 400% keeps it around 256x256). If in Gutsy, it was sharp enough, what is the problem with Hardy? :(

---

### Post by netron on 2008-05-28
i've noticed this as well. there is something seriously wrong with the thumbnailing code in the Hardy version of nautilus.

thats my only conclusion.

also - custom folder icons are scaling to the same size as regular folder icons.

music cover art is affected , especially if you dont have all folders showing covert art.

i've put some screenshots in this thread:

[http://ubuntuforums.org/showthread.php?t=801493](http://ubuntuforums.org/showthread.php?t=801493)

this wasnt a problem in Gutsy.

---

### Post by sayakb on 2008-05-28
> **netron said:**
> this wasnt a problem in Gutsy.

+1
But I don't think they would fix this either.. I wish I could post the screenshots of the Gutsy folders at 400%. I did have only 4 categories of folders: Data, Music, Videos and Movies on my external HDD, and they looked splendid with the 400% zoom and Tango icons.. ;)

Can't I downgrade nautilus to the one I had in Gutsy?

---

### Post by netron on 2008-05-28
i'm afraid not. nautilus is so dependent on numerous gnome packages, that you might as well just reinstall gutsy.

---

### Post by sayakb on 2008-05-28
Well, not a very acute reason to go back to Gutsy... I'll wait till it's resolved (have to wait indefinitely, methinks.. ;))

---

