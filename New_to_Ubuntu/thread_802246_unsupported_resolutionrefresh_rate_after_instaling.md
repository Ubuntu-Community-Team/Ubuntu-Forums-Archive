---
title: "unsupported resolution/refresh rate after instaling ATI drivers"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by cowboob on 2008-05-21
After installing  ATI driver for my 2600XT and rebooting computer when it gets to login screen monitor switches blank with a message that it don't support mode H:74.9KHz  V:59.9Hz
I know that i have somehow to edit xorg.conf file but i'm first day ubuntu user and i don't know how to do that.
Btw, i can login, but i'm still blind becouse of unsupported refresh rate.

Ubuntu 8.04

---

### Post by EXCiD3 on 2008-05-22
Try booting into recovery mode to use your screen again. I use nvidia, but if there is an ATI monitor/graphics configuration tool you should use that to configure your monitor correctly. You can manually edit the xorg.conf however by using this command: 
```
sudo gedit /etc/X11/xorg.conf
```

You can also redo your xorg.conf in case you mess something up by running this in terminal: ```

sudo dpkg-reconfigure xserver-xorg
```

---

