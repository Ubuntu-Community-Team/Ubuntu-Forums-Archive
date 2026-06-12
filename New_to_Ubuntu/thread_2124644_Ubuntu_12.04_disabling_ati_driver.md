---
title: "Ubuntu 12.04 disabling ati driver"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by bruce247 on 2013-03-11
I'm using an nvidia graphics card, I then tried an ati card which worked after I activated the propiatary driver. I need to go back to my previous nvidia card for now, but Ubuntu will not boot, gibberish with white lines appear on screen.

Is there a way to disable the ati driver within a root shell command line so that I can regain access to the system with the nvidia card?

---

### Post by Mark Phelps on 2013-03-11
The way I would do it is to reinsert the ATI card and use the details in link below to remove the proprietary drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Then, when the default Radeon drivers are working, you should be able to shutdown, replace the ATI card with the NVidia card, reboot, and be OK.

---

### Post by Bashing-om on 2013-03-11
bruce247; In addition to Mark's advise ->

If you have the PCI slots you might consider leaving both cards in (later, when you are up). MAFoElffen Has an extensive thread:
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86)
within this tome of information he describes how one may have 2 different Xorg.conf files set up and switch between the cards at boot. I do not know that this is even what you would want to do, just thought that I would throw that in your direction.[INDENT=3]just a thought

[/INDENT]

---

### Post by bruce247 on 2013-03-14
Thanks for your replys. I have put the ATI card back in and it works fine.

---

