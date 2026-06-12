---
title: "Howto: Use OSD with Rhythmbox, X-Chat and others"
date: 2005-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2005-11-29
[XOSD]("http://www.ignavus.net/software.html") (On-Screen Display) displays text on your screen, usually with information for other programs. XOSD works with Gnome, but does not have support for more modern apps.

Gnome-OSD give you support for more modern apps (Rhythmbox, Evolution, X-Chat), plus nice configuration options.

1. Get Gnome-OSD
```
wget -c http://mikesplanet.net/deb/gnome-osd_0.9.1-1~breezy_all.deb 
```
or
```
wget -c http://telecom.inescporto.pt/~gjc/gnome-osd/0.9.1/gnome-osd_0.9.1-1_all.deb
```
2. Install python-gnome2
```
sudo apt-get install python-gnome2
```
3. Install Gnome-OSD
```
sudo dpkg -i  gnome-osd_0.9.1-1~breezy_all.deb 
```
4. Press **Alt-F2** and run
```
/usr/bin/rbosd.py
```
5. To have it run automatically at Gnome launch. add the following to **System --> Preferences --> Sessions --> Start-up Programs**
```
/usr/bin/rbosd.py
```
I gave mine a startup order of 81, but anything above 50 should be fine.

Source: [http://mikesplanet.net/src/gnome-osd_0.9.1-1~breezy.tar.gz](http://mikesplanet.net/src/gnome-osd_0.9.1-1~breezy.tar.gz)

Let me know if you have any problems,
Mike

---

### Post by matthew on 2005-11-29
Hey, Mike,

Cool deal you have here. Couple of comments on the how-to.

I don't know if everyone will have python-gnome2 installed--I didn't on my Dapper test box where I installed this first. Since it's a dependency you might make a mention of it, to look and see if it's installed. Since it was installed on my Breezy box, and that is the release this was written for, this probably isn't an issue.

Also, someone will miss this step at 1.5:
```
sudo dpkg -i gnome-osd_0.9.1-1~breezy_all.deb 
``` 
I like this...thanks!

---

### Post by Technoviking on 2005-11-29
ACK!!!:-\" I got a call while typing this. Thanks for catching it. The instructions should be fixed now.

Mike

---

### Post by matthew on 2005-11-29
[quote=Mike Basinger]ACK!!!:-\" I got a call while typing this. Thanks for catching it. The instructions should be fixed now.

Mike[/quote]
That's cool. Those sorts of things are easy to miss...that's why we have another set of eyes look at our work. :) I can't tell you how many times someone else has saved me.

Oh, sorry. I found one more. In step 5 it reads:
[B]System --> Sessions --> Start-up Programs
[/B]and should read
**System --> Preferences -->Sessions --> Start-up Programs**

---

### Post by Athropos on 2005-12-21
Hi,

I just installed it, it works great with rhythmbox, just what I wanted :)
Thanks for this!

---

