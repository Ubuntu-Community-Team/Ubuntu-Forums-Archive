---
title: "[SOLVED] Gefource Video card"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by jamesrfla on 2008-06-07
I just did a update for my Ubuntu computer. I installed a video card update and now my resolution is messed up. I tried changing it but there is no option for a higher resolution. How do I uninstall a update? I am not sure on the model of the video card but if you need it I will need some help to find it.

---

### Post by wolfen69 on 2008-06-07
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` reboot.

---

### Post by jamesrfla on 2008-06-07
When I did that command I got this xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080607131930
I just did a reboot and it is back to normal. Thanks for the help.

---

