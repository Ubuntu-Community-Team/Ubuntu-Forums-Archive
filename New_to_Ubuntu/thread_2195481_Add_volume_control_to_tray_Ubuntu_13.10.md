---
title: "Add volume control to tray Ubuntu 13.10"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by anthony.mcnamara19 on 2013-12-24
Hey gang,

I had to do some tinkering today to get HDMI output working on Ubuntu 13.10. In the process of doing this I appear to have removed the volume control from the tray at the top of the screen. How do I restore this?

Cheers and Merry Xmas!

edit: Another problem I've noticed, although I'm not sure if this is related, is that the system settings won't quit once opened. I open them, click on something (which doesn't open) and then can't quit system settings until I log out.

---

### Post by Frogs Hair on 2013-12-24
Hello and Welcome

It is possible to re-install indicator sound log out and back in. ```
sudo apt-get install --reinstall indicator-sound  
``` If this doesn't work please describe what HDMI fix you applied in detail.

---

### Post by anthony.mcnamara19 on 2013-12-24
Fixed! Thanks so much!

---

