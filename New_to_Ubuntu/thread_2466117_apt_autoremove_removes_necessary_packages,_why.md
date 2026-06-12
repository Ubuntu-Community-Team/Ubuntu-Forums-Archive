---
title: "apt autoremove: removes necessary packages, why?"
date: 2021-08-20
forum: New to Ubuntu
---

### Post by Johannes33 on 2021-08-20
Hi,
I just installed ubuntu 20.04 a couple of days ago and had a problem.
When doing 'sudo apt autoremove' I ended up with a system that did not have any good graphics drivers and I did not know what more was wrong so I reinstalled and installed timeshift.
Now I tried 'sudo apt autoremove' again and ended up in the  same way. I did a timeshift back. But I really would like to be able to do 'apt autoremove' without being worried that it will take packages that is used by the system.
What can be wrong?

My second question:
I did:
apt-get --dry-run autoremove | grep -P '^Remv \K[^ ]+'

and it shows apt will remove the following:

Remv chromium-codecs-ffmpeg-extra [1:85.0.4183.83-0ubuntu0.20.04.2]
Remv gir1.2-gtkclutter-1.0 [1.8.4-4]
Remv gir1.2-clutter-gst-3.0 [3.0.27-1]
Remv gir1.2-clutter-1.0 [1.26.4+dfsg-1]
Remv gir1.2-coglpango-1.0 [1.22.6-1]
Remv gir1.2-cogl-1.0 [1.22.6-1]
Remv gstreamer1.0-vaapi [1.16.2-2]
Remv libgstreamer-plugins-bad1.0-0 [1.16.2-2.1ubuntu1]
Remv xserver-xorg-video-nvidia-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-cfg1-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-ifr1-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-gl-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-common-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-encode-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-decode-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-extra-470 [470.57.02-0ubuntu0.20.04.1]
Remv libnvidia-fbc1-470 [470.57.02-0ubuntu0.20.04.1]
Remv libva-wayland2 [2.7.0-2]
Remv libx11-xcb1:i386 [2:1.6.9-2ubuntu1.2]
Remv nvidia-settings [470.57.01-0ubuntu0.20.04.1]
Remv libxnvctrl0 [470.57.01-0ubuntu0.20.04.1]
Remv nvidia-compute-utils-470 [470.57.02-0ubuntu0.20.04.1]
Remv nvidia-prime [0.8.16~0.20.04.1]
Remv nvidia-utils-470 [470.57.02-0ubuntu0.20.04.1]
Remv screen-resolution-extra [0.18build1]

What is good to keep and what is not nessesary?

---

### Post by Dennis N on 2021-08-20
Yes, autoremove is not guaranteed as safe to use. Often you don't know what you should keep in that list. 

Autoremove removes packages that were installed as dependencies but now no other package depends on them. So these dependencies are freed to be autoremoved. The user must ultimately decide.

My general rule is if you can't tell if something in the autoremove list is important or not, don't use autoremove. Remove only individual packages that you are sure won't effect your system using 'remove' option.

You can also protect a package from autoremoval by changing its status to manual. 

sudo apt-mark manual <package name>

Comment: Removing a meta-package (like ubuntu-desktop) followed by autoremove can be especially risky in this regard.

---

### Post by grahammechanical on 2021-08-20
I only use the autoremove command when the combination of update & upgrade commands advise me that there are unnecessary packages that can be removed by autoremove. I never have the problems mentioned in this thread. 

Mind you, I do not use a proprietary video driver. Could it be that Ubuntu does not see proprietary video drivers, Chrome and the other stuff as necessary for using Ubuntu?

Regards

---

### Post by GhX6GZMB on 2021-08-20
I always use a sequence of:
sudo apt update
sudo apt upgrade
sudo apt autoremove
When updating my machine, and it has performed reliably always, with one big exception (which was my own fault):
I had moved/renamed/deleted some file in the system and this provoked an avalanche of broken dependencies. I didn't realize it until I saw autoremove deleting 80+ files (normally it's a handful) and then it was too late.
Complete reinstall, but fortunately with a Timeshift backup afterwards (the machine wouldn't even boot into Ubuntu).
Today I check what autoremove wants to delete before pressing OK.

---

