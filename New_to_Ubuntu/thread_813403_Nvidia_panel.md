---
title: "Nvidia panel"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by fedex1993 on 2008-05-30
Okay usually i can type nvidia-xconfig and it pops up with a control pannel for video card. 

I get an error message of 
Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

---

### Post by Lapino on 2008-05-30
The control panel you want is started with the nvidia-settings command, nvidia-xconfig is a tool that configures your xorg.conf and that needs to be run as sudo to write to that file.

---

