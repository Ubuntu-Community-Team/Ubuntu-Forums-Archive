---
title: "Ubuntu Login Screen Changed"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by Spence_Blood on 2013-08-15
Hello. I was using the the LightDm login screen when all of a sudden my login screen changed. It now looks a lot worse (like GDM) and it uses the default ubuntu background. How do i get back the old login? I am running 12.04.

---

### Post by deadflowr on 2013-08-16
```
sudo dpkg-reconfigure lightdm
```
Then follow then selections and choose lightdm.

If lightdm in command does nothing, then run it with gdm.

---

