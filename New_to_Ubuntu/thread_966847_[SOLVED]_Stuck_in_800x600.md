---
title: "[SOLVED] Stuck in 800x600?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Axis on 2008-11-01
I accidentally quit my upgrade in the terminal which has caused my ubuntu after reboot go straight into 800x600, most of my start up services wont work and I can't seem to find the problem by searching. Does anyone know what the solution may be to my problem?

I have updated all of the way (even to 8.10) and still no luck. But when I look ubuntu still sees my nvidia card.

Help!?

Thanks,
Axis

SOLVED By entering the following commands
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

---

