---
title: "HOW-TO: fix nvidia-glx"
date: 2007-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Zyphrexi on 2007-05-16
_User Level: _

Intermediate - disables the linux-restricted-manager's loading of nvidia drivers.


_Symptoms: _

nvidia module won't load, X won't load using module package nvidia-glx and Nvidia GeForce MX 440 video card.
no other package or card combo tested. 


_Introduction:_

I experienced this problem since before feisty was stable, when nvidia split the packages.
Even though I had an nvidia GeForce 4 MX 440, i couldn't get glx to work. I even thought about leaving ubuntu as a linux distro because of the problems I encountered. Well I just discovered an easy fix.


_What it does:_

This disables the lrm program from loading nvidia drivers, effectively fixing the problem.


_What to do:_

at commandline type
```
sudo nano /etc/modprobe.d/lrm-video
```

make it look like this:
> # Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
#install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
#install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS


just place '#' in front of each line. 
This comments out the commands so that lrm doesn't interfere with the way the nvidia module is loaded. BTW make sure that your /etc/X11/xorg.conf DOES load nvidia or this HOW-TO is pointless, since lrm was supposed to be an easy way for new users to load drivers.

reboot and voila!  working 3d. 
run glxgears just to make sure. Post any problems you run into.

*Limited support: I'll work on what I can with what knowledge I posses, nothing guaranteed nothing promised.*

---

### Post by Zyphrexi on 2007-09-16
my old computer died, so I can no longer maintain or test if this issue still exists.
This how-to is no longer supported and or recommended.

---

### Post by peteguhl on 2007-10-17
Just happened to me on Gutsy after trying to run a custom kernel - solution fixed my problem.

---

