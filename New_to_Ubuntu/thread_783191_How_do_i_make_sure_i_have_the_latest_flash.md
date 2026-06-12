---
title: "How do i make sure i have the latest flash?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-05
Flashes automatic settings for my webcam are wrong and some other programs seem to understand that but flash doesn't so how do i make sure i have the latest flash and install the new one if i don't?

---

### Post by bone2006 on 2008-05-08
You should probably use the one from the repository in which when new versions come out and are tested it will make it into the repository and when your software updates, it will update along with it.

If you want the closed source priority flash, then copy and paste this in a terminal
sudo apt-get install flash-nonfree

if you already have it installed, it will tell you.   I don't have a system to test this out, but you probably can type in the terminal flash-nonefree -v for the version.  Or try a man flash-nonefree and it will probably tell you the command to use.

If ther's a beta release or newer release you can either go to getdeb and search there for the deb or you need to enable in your source.lst the new releases that are still being tested.

---

### Post by zvacet on 2008-05-08
@ **gottabeandrew**

Go to some site with flash content (YouTube for example) and start one clip.Right click on it and you will see option about flash (or something similar) which will take you to the Adobe site and you will see which version do you use.

---

