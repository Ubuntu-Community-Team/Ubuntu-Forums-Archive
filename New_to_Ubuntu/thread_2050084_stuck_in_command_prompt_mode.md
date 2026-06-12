---
title: "stuck in command prompt mode"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by Paco62 on 2012-08-30
using ubuntu 10.04.   I was trying to resolve a problem with nvidia card drivers and the last thing I did was to uninstall and reinstall x-server.  Now when I login, I don't get the graphical interface but instead I get a full screen command prompt mode.  I can't seem to get out of it.  How do I get the normal ubuntu mode back?

---

### Post by SlugSlug on 2012-08-30
what happens if you type 

```
startx
```


after you log in?

---

### Post by Paco62 on 2012-08-30
I get a bunch of error messages, and then the command prompt again

---

### Post by jakesaunders24 on 2012-08-30
what nvidia card do you have?

---

### Post by Paco62 on 2012-08-30
> **jakesaunders24 said:**
> what nvidia card do you have?

asus/nvidia gt520 silent Geforce 1GB DDR3 with cuda  physx

---

### Post by Paco62 on 2012-09-02
I solved this problem by installing xserver-xorg-video-nouveau  and  xserver-xorg-video-vesa  and  xserver-xorg-video-fbdev

---

