---
title: "Huge problem with audio/graphics drivers"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Indiefab on 2008-08-13
I installed VirtualBox with no problem at all. After it installed, it said I needed a restart. After I restarted, it ran in Safe Graphics mode. Now, it won't run in anything but Safe Graphics mode and it won't detect my video drivers or audio drivers. Any help would be amazing, I can't take this 800x600 resolution!


The audio/video is stock off of a Biostar NF61S Nvidia GeForce 6100.

I also tried re-installing the drivers for the graphics, but every time I install it says I'm running an X server and to exit it before continuing...but I've turned off everything, and it still won't install. I'll post the log in a minute.

Edit: It won't allow me to view the log.```
 jared@jared:~$ /var/log/nvidia-installer.log
bash: /var/log/nvidia-installer.log: Permission denied
```

---

### Post by Mister.Vash on 2008-08-13
Press Ctrl + Alt + F1 to get you to a terminal
from the terminal run
```
sudo /etc/init.d/gdm stop
```
 then try running your nvidia installer again, if it doesn't mention it in the instruction, you usually need to preface the installer commando with sudo

---

