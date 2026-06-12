---
title: "[FIX] No Sound In VIdeos -Adobe Flash Player[FIX]- EASY!"
date: 2011-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Bazzi313 on 2011-01-15
If You installed adboe Flash player, and its playing no sound, then dont worry cause here is a fix that will work and is very simple:

Open terminal, and enter: 
     Code:
     sudo aptitude install alsa-oss 
After Installing the type the following code in terminal:
     Code:
     gksudo gedit /etc/firefox/firefoxrc 
A file will open, and in the file you will see: 
     

                                                 FIREFOX_DSP="none"           
Change this to:
     

                                                 FIREFOX_DSP=”aoss” 

Comment on results, thankyou!

---

### Post by dashingdon on 2011-02-04
I cant find firefoxrc . What am I missing ? :confused:

---

