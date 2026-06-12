---
title: "deleting Windows 7 with out reinstalling"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by Muirdoch on 2012-01-23
Ok I tried Lubuntu and love it.....even though I am still learning basics. Now windows 7 is taking up space I want for Lubuntu 11.10 oneiric. I removed all files I want from windows 7 and Gpart doesn't seem to help.

I started with windows 7 then added lubuntu. Use to duel boot fine then windows 7 compressed files and now Gpart won't even let me change sizes. Not sure if they are related, however I don't care as I want to get rid of windows completely and make this computer single Lubuntu.

Any help would be thank-full:D

---

### Post by bodhi.zazen on 2012-01-23
Try running gparted from a live CD. Then unmount swap, either with gparted or with the command line

```
sudo swapoff -a
```

Then make your changes in steps.

Delete windows partition -> apply changes
Add free space to lubuntu -> apply changes

---

### Post by GregA on 2012-01-23
If you're sure you want to nuke windows, then just do an install from the Live Lubuntu CD, and you'll get a screen that asks if you want to install using the whole disk.   

On that screen, or on the next, you'll get another warning that the disk contents will be erased (all data files, music, bookmarks, etc.)  At that point, when you click OK (or next), that will start the "write-over, erase process" and after a few minutes, your windows partition will be history.

Be sure you have all your key data saved . . . . . before using this process.

---

### Post by Muirdoch on 2012-01-24
TY, GregA don't want to loose lubuntu section as I have stuff there I don't want to have to reset-up

---

### Post by Muirdoch on 2012-01-24
I will try this ty bodhi.zazen

---

