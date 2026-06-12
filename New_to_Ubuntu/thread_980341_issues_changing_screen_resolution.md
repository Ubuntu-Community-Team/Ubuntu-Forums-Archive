---
title: "issues changing screen resolution"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-12
i am trying to change my screen resolution in ubuntu 8.10, but when i change it from 1024 x 768 to 1280 x 1024 the desktop becomes cropped on the screen, and the rest of the screen area looks scrambled.  is there anything i can do to correct this issue before i resort to using restricted drivers?  i have had bad experience with using the restricted drivers in the past because they never worked for me.

thanks.

---

### Post by alienexplorers on 2008-11-12
have you tried using the auto center command on your monitor if you have that.  Have you also ever tried using envyng to load the restricted drivers.  I always use that and never had a problem (knock on wood).

---

### Post by Crafty Kisses on 2008-11-12
Try the following and see if you can get a higher resolution:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Matt26 on 2008-11-12
> **Codename said:**
> Try the following and see if you can get a higher resolution:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

thanks for the suggestion, i tried that but unfortunately i have the same issue... i have attached a screen shot of the issue...

---

