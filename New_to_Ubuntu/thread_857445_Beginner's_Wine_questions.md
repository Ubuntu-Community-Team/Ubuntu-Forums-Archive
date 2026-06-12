---
title: "Beginner's Wine questions"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by le singe on 2008-07-12
So I have a dual boot winXP and ubuntu Hardy, and I want to install a game (HL 2) but onto my ubuntu partition directly (I no longer want to use windows much). I managed to open the installation exe fine through wine, and I'm only getting stuck not knowing where to install to.

The installer only recognizes the C: drive, and I'm wondering if wine works such that it recognizes dual boots and I would be installing the game onto my windows partion, and then accessing it on ubuntu through wine?

And then, is my entire drive considered the C drive, or having a partition are the two halves assigned different letters? In that case, is it a matter of checking what letter's assigned to the ubuntu partition then typing this in at the installation prompt?

I admit I don't know these basics at all, but I did look around a bit.
I'm just trying to figure out where to install the game to.

---

### Post by RiceMonster on 2008-07-12
To wine, your C: drive is ~/.wine/drive_c and your Z: drive is your entire hard drive. So if you're installing it to C:\Program Files, it's really in ~/.wine/drive_c/Program Files/.

(By the way, ~ means /home/your_user_name)

---

### Post by TSS on 2008-07-12
I actually just did my first installation of Counterstrike over Wine last night, so I might be able to give you a few pointers.

First, look up your game in the Wine Application Database ([http://appdb.winehq.org/](http://appdb.winehq.org/)).  Often, workarounds for common problems for a particular game are posted there.  

Also, am I correct in thinking that Half Life 2 runs through Steam?  If that's the case, just install the Steam application under Wine.  Then, make a Steam account and run the Steam client.  You can enter in your product key and the Steam client will download and install the game for you.  This is how I installed Counterstrike.  

For me, Counterstrike was divided into three CDs.  It went find through the first one, but when it asked me to insert the 2nd CD, Wine would not let me eject my CD drive.  The work around was to do what I described above, and let the Steam client handle everything.

Good luck!

TSS

EDIT: Doh, forgot your main question.   As RiceMonster has already pointed out, Wine actually creates a "C Drive" on your Ubuntu partition.  When you are clicking through the installer, the path will say something like "C:/Program Files/Steam/Half Life 2".  Don't worry though, it's on your Ubuntu parition.

---

### Post by RiceMonster on 2008-07-12
TSS, if wine will not let you eject your cd, you can also use this in a terminal:

```
wine eject
```

That's just for future reference if you run into that problem again with something else ;).

---

### Post by TSS on 2008-07-12
That's good to know, thanks for the tip :-).

I tried... 
```
umount -f /dev/cdrom
```
... and after that didn't work I just decided to figure out a different way to install CS :-p.

---

### Post by RayArdia on 2008-07-12
> **RiceMonster said:**
> To wine, your C: drive is ~/.wine/drive_c and your Z: drive is your entire hard drive. So if you're installing it to C:\Program Files, it's really in ~/.wine/drive_c/Program Files/.

(By the way, ~ means /home/your_user_name)

Thankyou - that is without doubt the most useful post I've read on Ubuntu forums. NOW perhaps I can get Wine to work!

---

### Post by le singe on 2008-07-12
hey cool thanks much for the help!

---

### Post by le singe on 2008-07-12
thank you TSS for the tip.

I'm trying that, as wine/ubuntu is not letting me change CDs (I tried through the terminal as well), but I cannot download the game from steam.  I was only able to enter my cd key in an attempt to activate a game, and steam stressed that I did not yet have anything to activate installed.

How are you able to download a game, steam does not make it easy...

---

### Post by TSS on 2008-07-12
Well I created my Steam account.  Then I logged into it, and you should have a few tabs at the top of the window.  I went to "My Games".   At the bottom of My Games, there is a button that says, "Active a Product on Steam...".  Give that a try, enter in your CD code that game with the game, and it should start downloading.

Let me know how it goes.

---

### Post by aktiwers on 2008-07-12
Both [Wine-doors ]("http://www.wine-doors.org/wordpress/")and [PlayOnLinux ]("http://www.playonlinux.com/en/download.html")installs steam and fonts and everything needed automatically.
It has worked great on all PCs I installed them on.

---

