---
title: "Characters and formatting lost after syncing xp with ubuntu."
date: 2008-07-23
forum: New to Ubuntu
---

### Post by geokok1981 on 2008-07-23
I use synctoy to sync winxp with my ubuntu box but I have this issue. 
Lets say I create this file with gedit:

> LINE 1
lINE 2

After the sync on xp notepad show this:

> LINE 1 (SOME FUNNY CHARACTERS HERE) LINE 2

Also if I edit mp3 tags with rythmbox they dont show up on xp......

Any tips here?

---

### Post by markjensen on 2008-07-23
Windows and DOS use a CR to mean Carriage Return AND Linefeed.

Unix and other OSes use both CR and LF for Carriage Return and Linefeed.

I don't run into this very often, and there used to be a basic commandline instruction to make a file "to unix" or "to dos".   However, I am pretty sure you have an option in gedit to force a DOS-like CR mode.

---

### Post by geokok1981 on 2008-07-23
Sorry but I dont seem to be able to find that and it still wont resolve my mp3 tags problem..... :(

---

