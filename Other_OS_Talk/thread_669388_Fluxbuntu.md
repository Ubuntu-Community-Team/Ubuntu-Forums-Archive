---
title: "Fluxbuntu"
date: 2008-01-16
forum: Other OS Talk
---

### Post by teejay17 on 2008-01-16
Does anyone have any idea when Fluxbuntu is going to be out of Release Candidate mode? 
I've been waiting patiently...and I can't wait to try it, but I don't want to install it until it is fully operational as a legit release.

---

### Post by p_quarles on 2008-01-16
Their web site isn't particularly helpful, so I can only guess that they're working on 8.04 at this point. 

Anyway, I've used Fluxbuntu, and it's perfectly stable. After all, it's more of a combination of a bunch of existing applications rather than anything brand new. I prefer a minimal Ubuntu install + Fluxbox, but if you want a working Flux environment out of the box, Fluxbuntu is a great option.

---

### Post by teejay17 on 2008-01-17
> **p_quarles said:**
> Their web site isn't particularly helpful, so I can only guess that they're working on 8.04 at this point. 

Anyway, I've used Fluxbuntu, and it's perfectly stable. After all, it's more of a combination of a bunch of existing applications rather than anything brand new. I prefer a minimal Ubuntu install + Fluxbox, but if you want a working Flux environment out of the box, Fluxbuntu is a great option.

Yeah. The problem is that minimal Ubuntu + Fluxbox is not as easy as it sounds for someone who hasn't done that yet. 
As an aside, I've put Fluxbox on Ubuntu, but that defeats the purpose when all the apps are from Ubuntu, and Gnome and everything is still there taking up valuable space. That's not what I want.

---

### Post by p_quarles on 2008-01-17
> **teejay17 said:**
> Yeah. The problem is that minimal Ubuntu + Fluxbox is not as easy as it sounds for someone who hasn't done that yet. 
As an aside, I've put Fluxbox on Ubuntu, but that defeats the purpose when all the apps are from Ubuntu, and Gnome and everything is still there taking up valuable space. That's not what I want.
You appear to have missed the point of my last post. 

What I said was this:
1) The Fluxbuntu RC is perfectly stable and usable
2) They probably aren't going to release an "officially" stable version until late April
3) As an aside I mentioned that *I* prefer a raw Fluxbox setup to a preconfigured distro. Maybe I shouldn't have.

In short: backup your important data and install Fluxbuntu. It's a fantastic OS, and you won't encounter any problems that you wouldn't in Ubuntu itself.

---

### Post by teejay17 on 2008-01-17
> **p_quarles said:**
> You appear to have missed the point of my last post. 

What I said was this:
1) The Fluxbuntu RC is perfectly stable and usable
2) They probably aren't going to release an "officially" stable version until late April
3) As an aside I mentioned that *I* prefer a raw Fluxbox setup to a preconfigured distro. Maybe I shouldn't have.

In short: backup your important data and install Fluxbuntu. It's a fantastic OS, and you won't encounter any problems that you wouldn't in Ubuntu itself.
I didn't miss any point; I got the gist just fine. Thanks for the feedback, btw. 
What I was hoping to get out of this thread are some resources/information on installing a raw Fluxbox setup on Ubuntu. I'm not going to bother with Fluxbuntu.
Got any ideas?

---

### Post by meborc on 2008-01-17
i think you are looking for this - [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) (don't let the title fool you)

have fun :D

edit: and after the base install, you might want to read this - [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

btw - i am using fluxbuntu RC and it is rock solid... so if your ubuntuserver+fluxbox doesn't work out so well, you can always try it... there are 2-3 known bugs which have easy fixes

---

### Post by p_quarles on 2008-01-17
> **teejay17 said:**
> I didn't miss any point; I got the gist just fine. Thanks for the feedback, btw. 
What I was hoping to get out of this thread are some resources/information on installing a raw Fluxbox setup on Ubuntu. I'm not going to bother with Fluxbuntu.
Got any ideas?
Well, installing Fluxbox isn't going to remove anything you already have on the system -- that would have to be done manually. 

The key to Fluxbox is the configuration folder. Inside of ~/.fluxbox, you will find files called menu, keys, startup, init, and slitlist. Between the five, you can control pretty much any aspect of the environment. These files use a relatively straightforward syntax. There is a suite of GUI configuration tools called Fluxconf, but I advise staying away from this: as currently packaged, it's very buggy, and unfortunately only makes things more difficult. 

One extraordinarily useful tool is the "xev" package. This allows you to quickly find the codes associated with any keypress or mouse gesture (or X event). It's a huge help when you're configuring the keys file. 

Desktop icons can be used by installing and configuring idesk.

Finally, my favorite collection of FB themes:
[http://www.tenr.de/styles/styles01.php](http://www.tenr.de/styles/styles01.php)

---

### Post by teejay17 on 2008-01-17
> **p_quarles said:**
> Well, installing Fluxbox isn't going to remove anything you already have on the system -- that would have to be done manually. 

The key to Fluxbox is the configuration folder. Inside of ~/.fluxbox, you will find files called menu, keys, startup, init, and slitlist. Between the five, you can control pretty much any aspect of the environment. These files use a relatively straightforward syntax. There is a suite of GUI configuration tools called Fluxconf, but I advise staying away from this: as currently packaged, it's very buggy, and unfortunately only makes things more difficult. 

One extraordinarily useful tool is the "xev" package. This allows you to quickly find the codes associated with any keypress or mouse gesture (or X event). It's a huge help when you're configuring the keys file. 

Desktop icons can be used by installing and configuring idesk.

Finally, my favorite collection of FB themes:
[http://www.tenr.de/styles/styles01.php](http://www.tenr.de/styles/styles01.php)
Thanks. I appreciate your feedback. I'm going to try everything out.

---

### Post by p_quarles on 2008-01-17
Just thought of a couple other things that you might be able to use:
[LIST]
[*]The "minimal Ubuntu" I mentioned earlier (but didn't explain) can be got by getting the "Alternate Install CD" and choosing the "command line installation" option from the option. This will install the base system without installing a GUI. Once you've installed, you can run the following from the console: ```
sudo apt-get install gdm fluxbox xorg
``` Then: ```
sudo /etc/init.d/gdm start
``` to load the GUI.
[*]The official Fluxbox documentation isn't perfect, but I've found parts of it extremely useful: [http://fluxbox.sourceforge.net/docbook.php](http://fluxbox.sourceforge.net/docbook.php)[/LIST]

---

### Post by teejay17 on 2008-01-17
> **p_quarles said:**
> Just thought of a couple other things that you might be able to use:[LIST]
[*]The "minimal Ubuntu" I mentioned earlier (but didn't explain) can be got by getting the "Alternate Install CD" and choosing the "command line installation" option from the option. This will install the base system without installing a GUI. Once you've installed, you can run the following from the console: ```
sudo apt-get install gdm fluxbox xorg
``` Then: ```
sudo /etc/init.d/gdm start
``` to load the GUI.
[*]The official Fluxbox documentation isn't perfect, but I've found parts of it extremely useful: [http://fluxbox.sourceforge.net/docbook.php](http://fluxbox.sourceforge.net/docbook.php)[/LIST]
Wicked! I might not get into this tonight, but it sure looks like a weekend project to me. I have this really old laptop that I love to tinker with, but a full installation of Ubuntu, or even Xubuntu taps its 4 gig HD. Thus, my desire for a bare necessity machine.

---

### Post by p_quarles on 2008-01-18
OK, didn't realize this was a laptop. Be forewarned that most wireless connections need restricted modules, which you won't get automatically with the alternate install CD. This is usually pretty easy to fix after the fact, but something to be aware of. In any case, if the laptop has an ethernet port, be sure to plug that in during the installation: things will go much more smoothly.

---

### Post by teejay17 on 2008-01-18
> **p_quarles said:**
> OK, didn't realize this was a laptop. Be forewarned that most wireless connections need restricted modules, which you won't get automatically with the alternate install CD. This is usually pretty easy to fix after the fact, but something to be aware of. In any case, if the laptop has an ethernet port, be sure to plug that in during the installation: things will go much more smoothly.
Okay, thanks. Good thing you reminded me too; I dug out my old ethernet card.

---

### Post by ugm6hr on 2008-01-18
> **meborc said:**
> i think you are looking for this - [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) (don't let the title fool you)


This has similar instructions (and illustrations, and how to enable repos etc), but the commands are only for icewm:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

This has info about the Window Manager options: [http://xwinman.org/](http://xwinman.org/)

Things to include (if wanted):
xorg, any WM (e.g. fluxbox or icewm), any file manager (thunar, rox or xfe are lightweight), a desktop manager (if necessary - idesk is good), synaptic (package manager), a terminal program (e.g. xterm), and a GUI login screen (if wanted - xdm or gdm).

---

### Post by teejay17 on 2008-01-18
> **ugm6hr said:**
> This has similar instructions (and illustrations, and how to enable repos etc), but the commands are only for icewm:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

This has info about the Window Manager options: [http://xwinman.org/](http://xwinman.org/)

Things to include (if wanted):
xorg, any WM (e.g. fluxbox or icewm), any file manager (thunar, rox or xfe are lightweight), a desktop manager (if necessary - idesk is good), synaptic (package manager), a terminal program (e.g. xterm), and a GUI login screen (if wanted - xdm or gdm).
Thanks. I like IceWM a lot too. I've also used it before, but over top of regular Ubuntu, so my machine was still pretty weighed down.

---

### Post by ugm6hr on 2008-01-18
> **teejay17 said:**
> Thanks. I like IceWM a lot too. I've also used it before, but over top of regular Ubuntu, so my machine was still pretty weighed down.

When you know what you are doing, it can be pretty impressive:
[http://ubuntuforums.org/showthread.php?p=1954760#post1954760](http://ubuntuforums.org/showthread.php?p=1954760#post1954760)

---

