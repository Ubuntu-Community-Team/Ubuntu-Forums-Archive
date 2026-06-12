---
title: "nvidia drivers"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by jtmedin on 2008-06-21
Don't know what i am missing but got the nvidia drivers from the nvidia.com linux. So they also have a nice edit the /etc/X11/xorg.conf pgm. Did that & looked @ the file it seemed ok. Then ran the NVIDIA-Linux-x86* file & it says i am running X server & must edit the file first. Suppose the file is the xorg.conf file which has been changed. Also it says must restart the X server. So why does it think the xorg.conf has not been edited OR how do u restart the X server? Ok what am i doing wrong? BTW tried to first use envyng but could not get the resolution above 800x600 ... . So here i am trying to get the proper dirvers for my nvidia geforce4 ... card. Bottom line is color me frustrated. TIA

---

### Post by PmDematagoda on 2008-06-21
You must first stop the X-Server before installing the Nvidia driver, but since you are a beginner you may want to try installing the driver using [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by aktiwers on 2008-06-21
I have also made small guide how to install them here:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

Just remember in the 3. and 2. last steps to change the file name to the one you got.

:)

---

### Post by sdennie on 2008-06-21
If you do decide to install them manually and not with envy, you may also want to look at this guide to prevent the drivers from breaking every time a big kernel update is released: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by jtmedin on 2008-06-21
already tried envyng

---

### Post by jtmedin on 2008-06-22
Ok found out by doing:gksudo displayconfig-gtk that i can get the resolution i need. However, when i reboot i have to do it all over again. How do i solve this? TIA

---

### Post by jtmedin on 2008-06-28
Still wondering how i can make the new screen resolution kept thru a boot. TIA

---

### Post by aktiwers on 2008-06-28
Did you ever try installing them manually like in the link I posted above?

---

### Post by sdennie on 2008-06-28
One of these two threads might work for you if it's simply not sticking through a reboot:

[http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2)

[http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

---

