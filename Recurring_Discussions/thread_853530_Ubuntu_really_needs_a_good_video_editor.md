---
title: "Ubuntu really needs a good video editor"
date: 2008-07-08
forum: Recurring Discussions
---

### Post by KingNeil on 2008-07-08
The most user-friendly one I've found is called Open Movie Editor.

It's really good for editing, but when you compile the file size is ludicrous, I'm talking 1GB for 10 minutes. So yeah, any devs out there really need to think about getting together seriously, because as a Windows user, I was used to Windows Movie Maker and used it at least once a month, so really need an alternative.

---

### Post by undadecor on 2008-07-08
Have you tried [Kino]("http://www.kinodv.org/")?
My personal favorite is [Cinelerra]("http://cinelerra.org/"), a very powerful video editor; however, it does take some getting used to.  Also, try to keep up to date on the status of [Jahshaka]("http://jahshaka.org/"), as it should be a pretty great program after some more development.

---

### Post by KingNeil on 2008-07-08
Well, Kino isn't much good, since you can't use anything except DV files... I've heard of the other two, but couldn't figure out how to download them. Maybe I should try again.

Do you just type in the code on this page into the Terminal to install Cinelerra? [http://cinelerra.org/getting_cinelerra.php#hardy](http://cinelerra.org/getting_cinelerra.php#hardy)

---

### Post by atomkarinca on 2008-07-08
Yes, you need to add the repositories. Open up a terminal (applicaitons > accessories > terminal) and type these:

```
sudo wget http://akirad.cinelerra.org/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key  add - && sudo apt-get update
```

then you can install Cinelerra:

```
sudo apt-get install cinelerra
```

---

### Post by undadecor on 2008-07-08
EDIT:  atomkarinca beat me to it...  :)

---

### Post by KingNeil on 2008-07-08
Thank you so much atomkarinca. This looks A LOT better than the other editors I've tried. I'll try it and come back if I'm having any problems.

---

### Post by atomkarinca on 2008-07-08
Not a problem. Cinelerra is a very good editor, I'm sure you'll like it.

---

### Post by purplepaint on 2008-07-08
I've tried Cinerella, and I couldn't make it work properly.  Jahshaka looks interesting (never heard of it).  Thanks for the info there.

---

### Post by Sef on 2008-07-08
Moved to recurring discussions.

---

