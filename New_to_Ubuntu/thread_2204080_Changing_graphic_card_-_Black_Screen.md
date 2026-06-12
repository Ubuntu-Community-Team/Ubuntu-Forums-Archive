---
title: "Changing graphic card - Black Screen"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by saculll on 2014-02-06
After changing from nvidia geforce 9600gso  to radeon 5750 card I got black screen after ubuntu loading screen. I tested some solutions from the Internet but they didn't work. Any ideas how to fix it even with using LiveCD ? My Ubuntu version is 13.04 or 13.10 When I put back geforce card the screen is loading fine.

---

### Post by deadflowr on 2014-02-06
Did you install the additional drivers for the old card?
You probably need to purge the old drivers and remove the xorg.conf file if you made one.
If you install them through the Addionatal drivers GUI, then you can uninstall them that way too.
You would simply make the xorg selection the one to activate.
Then remove the xorg.conf
```
sudo rm /etc/X11/xorg.conf
```
usually does the trick.

---

### Post by saculll on 2014-02-07
I pasted those commands and they helped me thanks a lot :)
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.OLD
sudo apt-get purge fglrx fglrx-amdcccle fglrx-dev
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core xserver-xorg-video-radeon xserver-xorg-video-intel
sudo reboot

---

