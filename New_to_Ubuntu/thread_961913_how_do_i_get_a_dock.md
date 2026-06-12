---
title: "how do i get a dock?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by rspk12 on 2008-10-28
i just installed ubuntu 8.0.4 and i love it so much better than vista but where do you get the dock im still a noobie at installing things in ubuntu thanks.:)

---

### Post by kerry_s on 2008-10-28
what dock? you have to be specific.

---

### Post by mcallenSchmee on 2008-10-28
Enter this command at a terminal:
```
sudo apt-get install awn-manager
```

---

### Post by aktiwers on 2008-10-28
There are many docks.. one popular is Avant AWN..

Go to system => Administration => Synaptics package manager
and search for it..  then mark it for installation and hit apply.

Then find it under  Applications => Accessories => Avant window manager

Edit: McallenSchmee beat me..

---

### Post by joey-elijah on 2008-10-28
BEat. lol

---

### Post by lifestream on 2008-10-28
You mean like this:
[IMG]http://wiki.awn-project.org/images/thumb/7/7b/Awn-preview-small.png/600px-Awn-preview-small.png[/IMG]

1)  Turn on desktop effects in SYSTEM > PREFERENCES > APEARANCES

2) hit ALT + F2 and type  
gksudo gedit /etc/apt/sources.list

At the end of the file, add these lines:

#avant window manager awn
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main


3) Launch your terminal from ACCESORIES  > TERMINAL
type:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install  avant-window-navigator

4) Go to ACCESSORIES > AVANT WINDOW NAVIGATOR  to launch it, OR type in a terminal :
avant-window-navigator&
(don't forget the & at the end)

5) right click anywhere in the applet that there isn't a icon, and select DOCK PREFERENCES.
Adjust to your liking.

6) Grab some cute themes from here:
[http://wiki.awn-project.org/Themes](http://wiki.awn-project.org/Themes)
If you want.



Let us know if you need more help,

Lifestream

---

### Post by ChildOfMana on 2008-10-28
Just for info - you can find a good comparison of the various different docks available [here](http://linuxowns.wordpress.com/2008/05/08/the-best-and-worst-docks-for-ubuntu/).

---

