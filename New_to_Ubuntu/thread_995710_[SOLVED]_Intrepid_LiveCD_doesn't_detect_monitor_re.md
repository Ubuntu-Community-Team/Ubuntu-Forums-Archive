---
title: "[SOLVED] Intrepid LiveCD doesn't detect monitor refresh rates properly"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by susanne260 on 2008-11-28
[http://i33.tinypic.com/2ajvtc5.png](http://i33.tinypic.com/2ajvtc5.png)

Why does it only offer a refresh rate as high as 85Hz, when my monitor supports 150Hz at 1024x768?

---

### Post by pedro_orange on 2008-11-28
The new version of Xserver auto detects your hardware and chooses the best configuration it knows. 
Perhaps it is only at 85Hz during liveCD is because you've not installed your graphics driver.

Eitherway, you can force Ubuntu to have whatever refresh rate you like by editing your /etc/X11/xorg.conf file

---

### Post by theozzlives on 2008-11-28
I'm running 1280x800 @ 60 Hz and it's fine, If you wanna change it edit your /etc/X11/xorg.conf. Intrepid is worthy to install.

---

### Post by susanne260 on 2008-11-28
Ah yes, my bad...
I completely forgot about the graphics drivers. #-o :lolflag:

Thanks guys!

---

