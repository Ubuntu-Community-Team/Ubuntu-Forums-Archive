---
title: "help compiz in 8.04"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by 1scorpio on 2008-04-28
I have installed 8.04 and want to use compiz desktop environment followed instructions from howtoforges installing on 7.10 but couldnt find in synaptic gnome-compiz-manager nor is there a customize button on  the visual effects menu

is there something I am doing wrong??

---

### Post by chewearn on 2008-04-28
You don't need to install compiz in gutsy 7.10, or in hardy 8.04.  It's already preinstalled by default.

If your graphics card support 3D acceleration, compiz will be automatically enabled.  If it is not enabled, go to:
System > Preferences > Appearance > Visual Effects to turn it on.

To check your graphics card, run this command in the terminal:
```
glxinfo | grep rendering
```If the answer came back as
```
direct rendering: yes
```then you are good to go.



To get additional compiz tweaking mayhem, install CCSM:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Raistlinbuntu on 2008-04-28
> **1scorpio said:**
> I have installed 8.04 and want to use compiz desktop environment followed instructions from howtoforges installing on 7.10 but couldnt find in synaptic gnome-compiz-manager nor is there a customize button on  the visual effects menu

is there something I am doing wrong??

I upgraded from 7.10 (3d acceleration and compiz working) to 8.04 and compiz isn't working anymore. At the first reboot a message appear like "compiz is incompatible with this kernel version". If I try to activate it manually it crash.

---

### Post by alienexplorers on 2008-04-28
To run the compizconfig-settings-manager go to System/Preferences/Advanced Desktop Effects Settings.  You can also create a desktop launcher using the command:
> gksudo ccsm
click on the desktop launcher and you will enter the compiz setup program.

---

