---
title: "What other ways can you alt-tab (seem to be doing it by accident...)"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by diablo75 on 2008-11-24
A friend of mine is learning Ubuntu, and he says he thinks he's accidentally bumping his laptops touchpad, somehow causing the equivalent of an Alt-Tab, switching apps.

Edit:  We think his touchpad is (for some reason) become extra, super sensitive to tap-clicking.  He said he can even breath on the pad and it's enough to minimize a window by accident.  Is there a way to disable tap-clicking on the touchpad of a laptop through an internal setting?  (Mods... if you read this, can you please change the title of the thread to, "Is there a way to decrease touchpad sensitivity?")

---

### Post by __Ryan__ on 2008-11-24
Strange...

go to System -> Preferences -> Mouse and select the touchpad tab.

Go ahead and play with the settings or temporarily disable it. This should give you a better idea about where the problem is coming from.

---

### Post by DieB on 2008-11-25
there is also a enhanced way for setting up your touchpad via synaptics (bad they use a similar name to the packet-manager), simply do:

> sudo apt-get install synaptics

inside of a terminal. afterwards you will get a new entry in system-settings.

hope it is a help

---

### Post by nothingspecial on 2008-11-25
> The best fix is to disable all scroll and tap commands for 1 second after each keystroke.

Go to Preferences and select "Sessions". Click the add button and add an entry:

Name: Syndaemon
Command: syndaemon -d -t -i 1
Comment: Disable trackpad while typing

The '1' can be changed to any decimal number, and defines the amount of time to lock the trackpad after each keystroke. See the Syndaemon man page for full details. 

From here

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

