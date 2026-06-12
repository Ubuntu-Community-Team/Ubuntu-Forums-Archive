---
title: "JWM Problem"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by vishy1618 on 2008-08-05
I have a slow computer so I use Joe window manager instead of gnome.
But whenever I log on with JWM, the fonts are diferent than that on gnome. also nautilus is not started by default. I like to keep my fonts small because of my low resolution.
Another problem, JWM is not in the 'Select Session' menu, I have to start it manually by starting 'blackbox' first. Any Ideas? Thanks.

---

### Post by SunnyRabbiera on 2008-08-05
Yeh JWM's implimentation isnt that great in ubuntu.
Try one of the others like ice WM or something light like that?

---

### Post by tuxxy on 2008-08-05
In your system > prefs > sessions click on add, then insert your command blackbox and click close.  Now it will run at startup and you no longer need to run the command at every boot.

---

### Post by vishy1618 on 2008-08-05
Yes, thank you, I did that. But I would like to know how to decrease the font size in JWM?

---

### Post by tuxxy on 2008-08-05
You could try right click on desktop and select change background, now click on the fonts tab and see if this is any help

---

### Post by bpowell2005 on 2008-08-05
Not really an answer to the question, but more of an observation: I've had good luck with Xubuntu...it runs on a very old laptop of mine just fine...I've never played with JWM, but if you're looking for a good manager for low-end PC's, Xubuntu fits the bill!

---

### Post by go_beep_yourself on 2009-07-21
Xfce is garbage. It really isn't much faster than Gnome for a slow machine. Go with Puppy Linux.

---

### Post by kerry_s on 2009-07-21
> **vishy1618 said:**
> Yes, thank you, I did that. But I would like to know how to decrease the font size in JWM?

/etc/jwm/jwmrc has the jwm settings, the bottom part has the font settings, you can change it to a true type font instead of fixed.
example: sans-9

---

### Post by kerry_s on 2009-07-21
> **go_beep_yourself said:**
> Xfce is garbage. It really isn't much faster than Gnome for a slow machine. Go with Puppy Linux.

that's bull, the xfce4 setup in xubuntu is slow, if you do a base+xfce4 it's much faster, if you go with a faster distro such as debian testing it's even faster.
i use debian testing xfce4 on 450mhz 256mb ram & it's plenty fast, while still using low resource, my startup ram use is only around 43mb.

---

### Post by go_beep_yourself on 2009-09-03
My JWM crashes every time I open an application. It happens with most applications. I can get to all of them through the debian menu. I am using jwm from the repos. Any help?

---

