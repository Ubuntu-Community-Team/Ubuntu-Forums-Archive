---
title: "HOWTO: Add Kubuntu to Ubuntu"
date: 2007-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by bscharff on 2007-03-04
The Following Was Written By Myself. Please Do Not Re-Post Without My Permission

If you want to be able to choose between Ubuntu (GNOME) and Kubuntu (KDE) at the Log-In Screen, Here's How:

Install Ubuntu As Usual If It Isn't Already.
Open Terminal and Enter "sudo aptitude update"
Follow On-Screen Directions
Allow It To Read The Package Lists
When It's Done, Enter "sudo aptitude install kubuntu-desktop"
Follow On-Screen Directions
Let It Install
Enter "exit"
Log-Out
On The Log-In Screen, Click "Session"
Select The Version You Wish To Run (GNOME=Ubuntu/KDE=Kubuntu)
That's It!
-----
If you decide that you want to uninstall the Kubuntu Part:
Log-In With A GNOME Session
Open Terminal
Enter "sudo aptitude remove kubuntu-desktop"
Follow On-Screen Directions
That's It!

---

### Post by aysiu on 2007-03-04
I prefer to refer people to this, since it has screenshots:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by bscharff on 2007-03-07
That Works Too :)

---

### Post by Takmadeus on 2007-03-07
How can I install kubuntu if I have the CD but not a decent internet connection

---

### Post by aysiu on 2007-03-07
> **Takmadeus said:**
> How can I install kubuntu if I have the CD but not a decent internet connection
If you have the Alternate CD, type these commands in the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo mv /etc/apt/sources.list /etc/apt/sources.list.cd
sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list
``` You can't add Kubuntu with the Desktop CD, though. You need the Alternate CD.

---

### Post by rotary on 2007-03-09
For some reason it doesn't work on mine. I had it installed but it is not showing in the Options. I also didn't see the gde/kde choice for default in the installation progress. :(

---

### Post by rotary on 2007-03-09
I succeded! :) Problem was I wasn't patient enough to wait for the updates to finish but in halfway started to install KDE.. Stupid.

---

### Post by wxnker on 2007-03-09
I don't like installing kubuntu on ubuntu much. I would advice anyone to try kubuntu on a separate partition. 

_First time kubuntu users:_
As a first time user it can make kubuntu seem more complicated (and messy) because of all the gnome stuff in the menu. I prefer installing a clean kubuntu on a partition of it's own. As I see it, installing kubuntu on ubuntu does not serve kubuntu right. 

The first time I tried kubuntu I installed it on ubuntu and like many others I switched right back to gnome, because I found KDE to be messy, but when I did a clean kubuntu install this changed drastically. Mainly because the menu's were clean (pure kubuntu) and not full of gnome stuff.
Now I practically only use kubuntu. I rarely log in to ubuntu anymore. 

_Why kubuntu? The KDE/kubuntu programs:_
People tend to love KDE/kubuntu programs like: Amarok, Kaffeine, k3b etc. and I understand why. In my opinion these applications have a much more "finished" look and feel than their gnome counterparts. So I figured, I like the KDE applications, why not use KDE instead of gnome? 

I absolutely love kubuntu. Like the KDE applications, kubuntu feels more complete than ubuntu (gnome). A kubuntu installation "out of the box" has many of those features, that I would have to use scripts and  customisation for in gnome. Kubuntu has more graphical choices and much better right click menus "out of the box".

Critics of kubuntu often claim that there are to many choices in KDE. Doing a clean kubuntu install certainly minimized this a lot.

_How kubuntu and ubuntu look:_
No comments on how ubuntu and kubuntu look. Making kubuntu look like ubuntu is easy, if that's what you want. Here's an example:
[http://www.mutube.com/mu/kubuntu-like-you-ubuntu/](http://www.mutube.com/mu/kubuntu-like-you-ubuntu/)

_Keep the gnome programs separated in kubuntu menu:_
Users who want to try kubuntu on top of ubuntu may find this useful: 
[http://www.kde-look.org/content/show.php?content=31031](http://www.kde-look.org/content/show.php?content=31031)

*I'd say, if you really want to compare gnome and kde. Use clean installs on different partitions. *

Regards
wxnker :)

---

