---
title: "Software Centre disappears, fix?"
date: 2017-01-03
forum: New to Ubuntu
---

### Post by helmcken on 2017-01-03
Hello! Although running reasonably well, my Ubuntu's left-hand side Software Centre icon is essentially non-functional. Whenever I try to click on it, the window opens up for approx. 2 seconds, then disappears altogether! It goes without saying that this is extremely frustrating and does NOT allow me to install new apps/programs. Is there a (hopefully simple!) way to fix this? After enduring 2+1/2years of computer malfunctions = no computer!, I REALLY, really don't want to undergo yet another complete re-install! Any ideas? (I'm using a dual-boot Win7 and Ubuntu 12 (I think!) on a home computer only a couple years old. :confused:

---

### Post by deadflowr on 2017-01-03
Perhaps open a terminal and run:
```
sudo apt-get update
```
post the results.
I ask, because sometimes when the action seen happens, it is because a hiccup has occurred in the update utility.
apt-get is the updating utility, so what it outputs might show where things are amuck.

---

### Post by ajgreeny on 2017-01-03
If you really want a GUI application to run updates and install or remove applications get synaptic.

It used to be the default package manager for Ubuntu and still is for Debian, I think.  In my opinion in is the very best package manager in the Linux world.

---

### Post by Geoffrey_Arndt on 2017-01-03
Helmcken . . . your post is full of bad "vibes".  Unfortunately,     I sense stormy sailing ahead . . . . 

Meanwhile, I suggest you follow ajgreeny's post above about installing and using the "Synaptic" package manager.   The old-semi ancient "software centre" is nearly "todt" (dead) on Ubuntu.   Not well supported anymore.    Also, Ubuntu 12.04 is only supported till the middle of this year . . . and afterwards, the software repos will be archived and not available.   

So . . . a re-install is very likely just "over the horizon" . . . . (account, it is harder to update online from such an old version of Ubuntu to the current LTS (e.g.,   12.04 to 16.04 . . . . . )

---

### Post by mörgæs on 2017-01-04
Yes, Software Centre is history. A fresh install of 16.04.1 will bring *Gnome Software* in stead.

---

### Post by vasa1 on 2017-01-04
> **Geoffrey_Arndt said:**
> ... Also, Ubuntu 12.04 is only supported till the middle of this year . . . and afterwards, the software repos will be archived and not available.   

So . . . a re-install is very likely just "over the horizon" . . . . (account, it is harder to update online from such an old version of Ubuntu to the current LTS (e.g.,   12.04 to 16.04 . . . . . )
If [another thread]("https://ubuntuforums.org/showthread.php?t=2343822") is anything to go by, OP maybe on 16.04 despite the profile showing Lucid Lynx!

> and my beloved Ubuntu (newer version @ 16.04) OS

OP, please do yourself and people who wish to help a favor by updating your OS information. Thanks!

---

