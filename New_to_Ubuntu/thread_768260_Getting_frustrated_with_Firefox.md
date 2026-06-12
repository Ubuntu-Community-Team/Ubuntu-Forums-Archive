---
title: "Getting frustrated with Firefox"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Dan Sarf on 2008-04-26
Hi guys

I've only recently switched to Ubuntu and in common with many other people I have had freezing and greying out issues with Firefox.  I hoped that the new Beta on Ubuntu 8 would have solved these but it doesn't seem to have.

As web browsing is mainly what I use my computer for it's pretty irritating along with the fact that one of the sites I use regularly just doesn't work in FF.

I've tried installing IE via Wine but I am not proficient enough to do it.

What I'm asking is: is there a browser which is as feature-rich as FF but without the bugs?  Because if not I regret to say that I may have to ditch the bits of Ubuntu that I do like and switch back to Mr Gates...

---

### Post by Michael.Godawski on 2008-04-26
Well you can try other browsers like

[Opera]("http://de.opera.com/")
[Epiphany]("http://www.gnome.org/projects/epiphany/")
[Kazehakase]("http://kazehakase.sourceforge.jp/20031201.html")

---

### Post by SunnyRabbiera on 2008-04-26
well the firefox 3 is still beta so issues are expected.
However I have noticed that firefox 2 runs a LOT smoother under hardy then it did in gutsy, you can try to downgrade to firefox 2 for the time being.

---

### Post by Google Spider on 2008-04-26
```
sudo apt-get install opera
```

or 

```
 sudo apt-get install firefox-2
```

---

### Post by SunnyRabbiera on 2008-04-26
aye, my system actually works better with firefox 2 right now.
I guess he and I are among the unlucky ones with firefox 3.

---

### Post by philinux on 2008-04-26
Firefox 3 has a documented bug regarding its anti attack and forgery website detection. This bug causes 100% cpu and lots of disk activity.

The solution/workaround is to go into your mozilla profile folder in home and delete the following file.

/home/username/.mozilla/firefox/xxxxxx.default/urlclassifier3.sqlite

Close and restart firefox and this file will be recreated.

Initially this file was 30mg now it's 500kb.

---

### Post by FredB on 2008-04-26
I think this bug had been killed since beta5 was released. I'm using homemade pre-rc1 firefox 3, and no problem of this kind.

---

### Post by philinux on 2008-04-26
> **FredB said:**
> I think this bug had been killed since beta5 was released. I'm using homemade pre-rc1 firefox 3, and no problem of this kind.

I'm running beta 5 and it's alive and well. Well not now I deleted that file.

---

### Post by tubunu on 2008-04-26
When you double click on the very top bar of Firefox it disappears altogether with the bottom one. I've noticed sometimes they both disappear out of the blue (even if I don't double click). How do I get back the top and bottom bars? How to prevent FF from making them disappear automatically? Thanks. [FF3b5]

---

### Post by cogitordi on 2008-04-27
> **philinux said:**
> Firefox 3 has a documented bug regarding its anti attack and forgery website detection. This bug causes 100% cpu and lots of disk activity.

The solution/workaround is to go into your mozilla profile folder in home and delete the following file.

/home/username/.mozilla/firefox/xxxxxx.default/urlclassifier3.sqlite

Close and restart firefox and this file will be recreated.

Initially this file was 30mg now it's 500kb.

Thanks for this tip, Sir!

---

### Post by T-Virus on 2008-04-27
If you my any means are going to visit KDE - give Konqueror a try, it's not that bad :)

---

### Post by swimm3r137@gmail.com on 2008-04-27
> **SunnyRabbiera said:**
> well the firefox 3 is still beta so issues are expected.
However I have noticed that firefox 2 runs a LOT smoother under hardy then it did in gutsy, you can try to downgrade to firefox 2 for the time being.

a

---

### Post by swimm3r137@gmail.com on 2008-04-27
> **SunnyRabbiera said:**
> well the firefox 3 is still beta so issues are expected.
However I have noticed that firefox 2 runs a LOT smoother under hardy then it did in gutsy, you can try to downgrade to firefox 2 for the time being.

How do you downgrade from the 3.5beta to firefox 2?

---

### Post by SuperSon!c on 2008-04-27
> **philinux said:**
> Firefox 3 has a documented bug regarding its anti attack and forgery website detection. This bug causes 100% cpu and lots of disk activity.

The solution/workaround is to go into your mozilla profile folder in home and delete the following file.

/home/username/.mozilla/firefox/xxxxxx.default/urlclassifier3.sqlite

Close and restart firefox and this file will be recreated.

Initially this file was 30mg now it's 500kb.

ff3b5 has been working splendidly for an hour since i did what you recommended.  hopefully this workaround sticks until it's properly debugged.

---

### Post by veritas366 on 2008-04-28
I have a second issue...I followed the instructions for the first and will see if I have luck avoiding the greyed out screen.

But I also have an issue where I close firefox and when I try to reopen it says it's already running.  Looking in system monitor shows a firefox process listed as "zombie". I can't stop it...I hit "end process" and it continues.  It seems "kill" plus process id works in a terminal, but I'm not sure that did it because it stayed listed on the system monitor, though it did let me restart firefox.

---

