---
title: "Network manager"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by Cthulu2156 on 2013-01-09
Hello,
  
  Pretty basic question, wondering how to get network manager starting at start up again.  Stopped for some reason - I put the command in the 'startup applications' applet, but still won't start.  I found in another post how to get it started through the command line every time I log on but would like it to start automatically.  Am I doing something wrong with the startup applications app?  Is there a file I can change to get it starting?

---

### Post by El Tito on 2013-01-09
I suppose you are using Ubuntu, but what desktop enviroment are you using
(KDE,Gnome,Unity...)?

---

### Post by Cthulu2156 on 2013-01-09
I'm using unity 2d, in another thread it wasrecommended using wcid which I have but it is unreliable.  the main issue is the connection is not good with wcid, but with network manager it is not great.  either way i would prefer to have network manager.

---

### Post by steeldriver on 2013-01-09
There shouldn't be any need to put anything in startup applications afaik - it should start automatically via upstart / init

Probably installing wicd has overridden the default network-manager startup behavior - you could try

```
sudo dpkg-reconfigure network-manager
```If that doesn't work, maybe purge wicd and reinstall network-manager... ?

---

### Post by grahammechanical on 2013-01-09
I believe that wicd uses the /etc/network/interfaces file. Network Manger does not use the interfaces file. In fact if there is anything in the interfaces file except default information then Network Manager does not work. This is what causes the conflict between Network Manager and Wicd. We use one or the other. We cannot use both.

This is what I have in my 12.10 /etc/network/interfaces file

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

If you have anything more than that then that is the reason Network Manager is not working.

Use this code to edit the interfaces file

```
gksudo gedit /etc/network/interfaces
```

Regards.

---

### Post by Cthulu2156 on 2013-01-10
You're right, your solution worked perfectly (no more error messages on startup - network settings) although I have no idea how I saved/replaced the file once edited.  I noticed that interfaces is a read-only file.  How do I edit read-only?   I have no idea how I did it the first time.  I'm just wondering because when I pull it up in unity it shows only some code that I put in, not later edits, but when pulled up in gedit through the command line it shows the edits.

---

