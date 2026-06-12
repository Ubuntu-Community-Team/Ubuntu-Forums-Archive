---
title: "Problem waking laptop from sleep"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by coversnail on 2012-01-06
Sorry if this is in the wrong place.

I have a Lenovo B570 laptop and have Ubuntu 11.10 installed. My problem is that when the screen is turned off through inactivity (set at 10 minutes in the settings), it is very difficult to reawaken the laptop because there the screen doesn't 'wake up' to full brightness so that I can re-enter my password.

At first I thought that the screen was completely black but in fact the laptop has simply turned the brightness down to the lowest level so if I squint very hard I can see the password entry dialog box. But my hardware brightness keys (fn + up/down) do not work (though they work fine in every other circumstance).

I can unlock by entering my password 'blind' which unlocks the screen but leaves the brightness levels at the lowest possible, now the hardware brightness keys do work. Seems strange behaviour though. If I do a normal lock screen (Ctrl + Alt + L) there are no brightness problems so it must be something to do with the "turn screen off after 10 minutes"

Anyone have any ideas, or have I missed a blindingly obvious setting! Thanks for any potential help:D

---

### Post by cap10Ibraim on 2012-01-06
try 
[http://ubuntu-tweak.com/source/linrunner-tlp/](http://ubuntu-tweak.com/source/linrunner-tlp/)

---

### Post by coversnail on 2012-01-06
> **cap10Ibraim said:**
> try 
[http://ubuntu-tweak.com/source/linrunner-tlp/](http://ubuntu-tweak.com/source/linrunner-tlp/)

Thanks for the reply, not all that sure what I'm meant to be doing here though! Not to worry I'll have a search around and see if I can work out what I'm doing.

---

### Post by cap10Ibraim on 2012-01-06
okay search for TLP it's an alternative power management tool especially for thinkpads , try it

---

### Post by coversnail on 2012-01-06
Thanks for the help, I installed etc following the instructions fro the TLP Github page: [https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management](https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management)

Sadly nothing has changed, still the same behaviour even after reboot.

---

### Post by coversnail on 2012-01-11
This issue turned out to be a problem with the kernel which will be fixed in the next release of the kernel. The bug report relating to it is here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/872652)

If anyone else wants to apply the changes without waiting for a new update then look at comment #55 on the bug report page for a patch to apply.

---

