---
title: "Screen resolution"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by kashiram on 2008-07-15
i am not able to change the screen resolution ..
it shows only 800x600 & 640x480 mode but my monitor can support much higher resolutions..

i was asked after the installation about my video driver and monitor details .. i think i made a mistake there ...
now how can i change it to 1024x960 resolution??

---

### Post by iaculallad on 2008-07-15
> **kashiram said:**
> i am not able to change the screen resolution ..
it shows only 800x600 & 640x480 mode but my monitor can support much higher resolutions..

i was asked after the installation about my video driver and monitor details .. i think i made a mistake there ...
now how can i change it to 1024x960 resolution??

Try to post whatever displays when you issue the command below using in your terminal:

```
lspci | grep VGA
```

and do post your xorg.conf file:

```
cat /etc/X11/xorg.conf
```

---

