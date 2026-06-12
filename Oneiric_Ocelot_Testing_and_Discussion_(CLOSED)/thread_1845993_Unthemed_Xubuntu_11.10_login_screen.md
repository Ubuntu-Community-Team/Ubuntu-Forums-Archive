---
title: "Unthemed Xubuntu 11.10 login screen"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by teachop on 2011-09-18
The Ubuntu 11.10 beta login screen is themed out and looks nice.  The Xubuntu login screen is loud "EGA magenta" and decorated in a Windows 3.1-like style.  I assume this is what unthemed looks like.  I have been waiting this out for a long while, thinking it would sort itself out, but now am wondering enough to ask, is that what all Xubuntu testers are seeing?  I have installed on both AMD and Intel graphics with the same login screen look resulting.

By the way, the eye-pain is momentary.  Xubuntu looks real nice once it gets xfce loaded up, in my opinion the finest looking default of the "big 3" U/K/Xubunutu hands down.

---

### Post by Toz on 2011-09-23
Looks like the official xubuntu lightdm theme has been postponed until 12.04 LTS ([http://www.linux-archive.org/xubuntu-development/574716-xubuntu-community-meeting-minutes-2011-09-11-a.html]("http://www.linux-archive.org/xubuntu-development/574716-xubuntu-community-meeting-minutes-2011-09-11-a.html")). 

In the meantime, you can make some cosmetic changes by editing the **/etc/lightdm/lightdm-gtk-greeter.conf** file. Mine currently looks like:
```
[greeter]
background=/usr/share/backgrounds/beachwaves.jpg
theme-name=greybird
font-name=Ubuntu 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb

```

---

