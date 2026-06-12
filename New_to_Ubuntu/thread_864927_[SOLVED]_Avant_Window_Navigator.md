---
title: "[SOLVED] Avant Window Navigator"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by s.fox on 2008-07-20
Hi everybody,

I was looking for something similar to the Mac OS X application dock.  After a little research i came across avant-window-navigator.  I installed it from synaptic package manager.   I have also got the avant window manager installed aswell. 

My question is how do I add applications to the dock?   I assume that this is the reason I can see nothing at the bottom of my screen.  If anybody can help me with this teething problem I would be very grateful.

Thank you for assistance in this rather Noobish question.

---

### Post by bhadotia on 2008-07-20
> **Ash R said:**
> Hi everybody,

I was looking for something similar to the Mac OS X application dock.  After a little research i came across avant-window-navigator.  I installed it from synaptic package manager.   I have also got the avant window manager installed aswell. 

My question is how do I add applications to the dock?   I assume that this is the reason I can see nothing at the bottom of my screen.  If anybody can help me with this teething problem I would be very grateful.

Thank you for assistance in this rather Noobish question.
Just drag and drop the application from the nautilus menu to the dock to add it or use the awn manager to do the same.
If you want some extra applets use the bzr version of AWN , its not in the repos , but here is a list of how tos:
1. [http://ubuntuforums.org/showthread.php?t=762363&highlight=AWN+reacocard](http://ubuntuforums.org/showthread.php?t=762363&highlight=AWN+reacocard)
2. [http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html](http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html)

---

### Post by billgoldberg on 2008-07-20
AWN in the ubuntu repo's is useless. (mostly because of the feature freeze).

Cairo-dock is way better in almost all ways.

One of the standard themes is "mac osx" wich will give you a replica of the osx dock, icons and all.

> Go to [this page]("http://developer.berlios.de/project/showfiles.php?group_id=8724"), and download the latest &#8220;dock&#8221; and &#8220;plugin&#8221; .deb files. Double click them to install. After installation, you can open Cairo Dock using &#8220;applications -> system tools&#8221;.
 from [http://linuxowns.wordpress.com/2008/05/08/the-best-and-worst-docks-for-ubuntu/](http://linuxowns.wordpress.com/2008/05/08/the-best-and-worst-docks-for-ubuntu/)

A screenshot of the dock:

[http://upload.worldofplayers.de/files/a7o1CBildschirmfoto.png](http://upload.worldofplayers.de/files/a7o1CBildschirmfoto.png)

--

To start the dock when you start ubuntu, go to "system -> preferences -> sessions" and in the command box add "cairo-dock" (without " "). 

You can make up what you put in the other boxes.

---

### Post by MattBD on 2008-07-20
Avant Window Navigator is good, but the only thing it supports out of the box is the Launcher applet. To get more out of it, you need to add more applets.
I actually wrote a blog post about using Ubuntu Tweak to do this yesterday, and it's at [http://easierbuntu.blogspot.com/2008/07/using-ubuntu-tweak-to-get-third-party.html](http://easierbuntu.blogspot.com/2008/07/using-ubuntu-tweak-to-get-third-party.html)
Hope this helps.
Also, make sure you install the awn-manager package as well.

---

### Post by s.fox on 2008-07-20
Big thanks to everyone.  

I have been able to download and install cairo dock.  Its exactly what I was looking for and is pleasing on the eye.  Thank you so much.

One problem that I am experiencing with it though.  To get it to run I have to type into terminal:

```
cairo-dock

```

Not a major problem except that the dock disappears when I close terminal.  Whats going on? 

Once again thank you.

---

### Post by MattBD on 2008-07-20
You can easily set it up to launch when you start your system by going to System>Preferences>Session, clicking Add, and putting cairo-dock under Command, and filling in the other parts as necessary. When you next start your system, Cairo should be working straight away.
EDIT: Just realised billgoldberg has already written this.

---

### Post by s.fox on 2008-07-20
Nice, it worked :)

I was just a little surprised when the dock disappeared when I closed terminal

Thank you everyone :)

---

### Post by kgr132 on 2008-07-20
If you want to run it from a terminal session, but not have the terminal window left behind and cluttering things up, use Alt-F2 to bring up a "Run Application" interface. This will let you start the app. as if you were in a terminal window, but only the app. is left behind after you click Run, no actual terminal window will be left active on your desktop.

---

