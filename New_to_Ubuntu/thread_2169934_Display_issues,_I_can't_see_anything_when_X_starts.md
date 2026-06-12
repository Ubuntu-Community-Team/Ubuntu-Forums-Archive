---
title: "Display issues, I can't see anything when X starts but TTYL works"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by Alship on 2013-08-24
So as the title says, when my computer boots it gets fine past everything, when X starts it shows the mouse in the middle of the screen then shuts off to a black screen then re-appears in a loop, however I can drop to any TTYL that I want with no issue. I have tried some basic things from around the internet but nothing seems to be going my way at the moment, I am wondering if anyone else knows of anything I could do to see if the can try work it out, I am certain the computer is using a SiS VGA monitor.

Can anyone offer me anything to do? I have tried following 
[https://help.ubuntu.com/community/BinaryDriverHowto/Sis](https://help.ubuntu.com/community/BinaryDriverHowto/Sis)

But the Xorg file isn't generated on my system so that doesn't work, at the moment I am at a loss for ideas. One last note is I have no internet access for this computer as of yet, I am working on getting it sorted but I would like it up and GUI running before I work on that. 

Thanks for the help.

---

### Post by Alship on 2013-08-24
Still looking for help on this.

---

### Post by Alship on 2013-09-01
Anyone ._. i am really at a loss....

---

### Post by btedm on 2013-09-06
I am not an expert in Ubuntu but have struggled with display problems so will give a few suggestions.
On my system I get a log file in /var/log/Xorg.0.log   It is a long file to read but it may give some hints where the problem is.
I had resolution problems -- the driver could not find the resolution of my display and used a value out of range. 
I had success by changing file  /etc/X11/xorg.conf.  This file xorg.conf can be in one of a number of different folders as given in ```
man xorg.conf
```
My references are a bit old but could help: 
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") gives information on setting resolution.
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:__Incorrect_Resolution_when_no_EDID_available_such_as_from_old_monitor_or_a_KVM_device]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:__Incorrect_Resolution_when_no_EDID_available_such_as_from_old_monitor_or_a_KVM_device")  also gives information on setting resolutions.

You said the Xorg file is not generated on your computer.  Do you mean that xorg.conf is not generated when you run ```
Xorg -configure
```?

---

