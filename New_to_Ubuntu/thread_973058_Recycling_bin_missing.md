---
title: "Recycling bin missing?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by watsgoodg on 2008-11-06
Quick question...my recycling bin disappeared from the bottom task pane...did some searching can figure out where to find it or how to empty it???

---

### Post by thavid on 2008-11-06
> **watsgoodg said:**
> Quick question...my recycling bin disappeared from the bottom task pane...did some searching can figure out where to find it or how to empty it???

Open a nautilus window (places - desktop) and you'll see the trash on your left.

---

### Post by Simian Man on 2008-11-06
1. Right click on the bottom pane
2. Select add to panel...
3. Add the trash can back

After that, you can move it to the right corner.  (You may have to unlock the other panel widgets first).

BTW it's called a Trash Can.  That other system calls it "recycle bin".

---

### Post by brandon88tube on 2008-11-06
> **Simian Man said:**
> 1. Right click on the bottom pane
2. Select add to panel...
3. Add the trash can back

After that, you can move it to the right corner.  (You may have to unlock the other panel widgets first).

BTW it's called a Trash Can.  That other system calls it "recycle bin".

I would also like to add that he should right click the trash can icon once its on the panel and moved to the desired location, selecting Lock To Panel. This will keep it from moving

---

### Post by RGPerson on 2009-02-17
I had a rather more severe problem (in the end requiring me to reinstall Nautilus).  One of the symptoms was a missing Trash can.  I was able to get my major problems resolved, but I still have not Trash can icon.

I tried right-clicking the panel and adding it but it doesn't show up.  I added Volume Control just to see if it would show up and it did without a problem.  Trash just won't.

Any ideas?

Gabrielle

---

### Post by UbuntuNerd on 2009-02-17
you can always add it to your desktop, type this in a terminal:
```
gconf-editor
```
go to apps > nautilus > desktop and click the box besides trash icon visible.

you can also empty the trash by typing the following in a terminal:
```
sudo rm -rf ~/.local/share/Trash
```
you can also try:
```
gksu nautilus
```
and deleted /home/user/.local/share/Trash

---

### Post by alphabravo8 on 2012-11-08
> **Simian Man said:**
> 1. Right click on the bottom pane
2. Select add to panel...
3. Add the trash can back

After that, you can move it to the right corner.  (You may have to unlock the other panel widgets first).

BTW it's called a Trash Can.  That other system calls it "recycle bin".

thanks man that was the only way for me!

---

