---
title: "No sound"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by cmoran on 2008-08-26
Hi, I am new to linux and just loaded Ubuntu Hardy Heron onto my Gateway 3520GZ.  I seem to have gotten everything to work but the sound!  The sound card seems to be recognized (Intel 82801DB-ICH4), but no sound comes from either speakers or headphones.  

Any help is greatly appreciated!

---

### Post by cmittle on 2008-08-26
I had this problem on my most recent install of Ubuntu on my laptop.  Go to the terminal and type alsamixer, this is where you can control sound of various items for your computer.  Use the left and right arrows to go through the items, and up and down to turn the volume up or down.  If the volume bar is empty and there is an MM in the bottom box press the letter m on your keyboard to turn this item on then you can turn the volume up and down.  

**Edit** I should mention when you are done press Ctrl + c to close alsamixer.**

What happened to me was all of these were off, so I simply had to turn them on and now sound works.  

Let us know if this works.

Cory

---

### Post by silkstone on 2008-08-26
You can also install alsamixergui from Synaptic.

You may have to go into System > Preferences > Sound and select ALSA for everything.

---

### Post by cmoran on 2008-08-26
hey, thanks... I tried this, and everything was already turned up to max...???

any other ideas?

---

### Post by Nibaini on 2008-08-29
I am having the same problem on my Emachines M5405 laptop is tried the above comments and all mine were set to the max already also. 
Thanx everyone in advance

---

### Post by swoll1980 on 2008-08-29
double click your volume in your panel see if turning those up helps on mine I have to right click the volume icon, preferences then select headphones for my volume to work I have the same card as you

---

### Post by Crafty Kisses on 2008-08-29
Post the results of > lspci

---

### Post by kansasnoob on 2008-08-29
Also I've had much better luck with gnome-alsamixer which is in synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It then shows up in the menu under Sound & Video:

[ATTACH]83219[/ATTACH]

[ATTACH]83220[/ATTACH]

---

### Post by Kevbert on 2008-08-29
Please take a look at this [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?t=616845")[/COLOR].

---

