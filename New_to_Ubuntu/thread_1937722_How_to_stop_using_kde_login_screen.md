---
title: "How to stop using kde login screen?"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by rollcast on 2012-03-08
I don't like the unity ui so I installed kde but didn't like it. I've managed to uninstall kde but ubuntu still automatically uses the kde login screen when I switch on the computer?

Is there any way to get back to the original login screen?

Thanks
AL

---

### Post by forrestcupp on 2012-03-08
Try to open a terminal and type
```
sudo dpkg-reconfigure lightdm
```and choose LightDM instead of KDM.

---

