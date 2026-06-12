---
title: "Nvidia (gudie)"
date: 2005-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Dotrig on 2005-11-02
i translating a swedish nvidia gudie as worked for me ..


_______________________
first off all you open the terminal and do this:
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings

and do a copy of xorg.conf:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

do now:
sudo nvidia-glx-config enable
And the last thing you will need to do a getway to nvidia-settings in menu in gnome:
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

and put in:
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;


___________
Dont forget to save ;)
do sudo reboot

Worked for me..

Sorry for my bad english..

---

### Post by M7S on 2005-11-03
It's usually a nice thing to give a link to the original...

Regards,
M7S

---

### Post by tseliot on 2005-11-03
This is the method described in the Unofficial Starter's guide. I've put it as method 1 in my guide.

[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

