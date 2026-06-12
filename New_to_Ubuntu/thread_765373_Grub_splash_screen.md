---
title: "Grub splash screen?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Bleak Outlook on 2008-04-24
ive got a grub splash screen to add into grubs splash folder but when i try to drag it into the folder im denied and told i dont have permission

now as this is my comp and im pretty sure i would give myself permission ( if i asked nicely) how do i go about letting my computer know?

is there a way of letting my comp know that i would give permission to edit any folder i might choose

:confused:

thanks for your time and answers

---

### Post by spiderbatdad on 2008-04-24
you can use ```
gksu nautilus
``` to open a file browser in superuser mode, but be very careful. Not sure about grub themes, but gdm or greeter themes are usually dropped as tar packages into the local area of System>>Administration>>login window.

---

### Post by grannyw on 2008-04-24
sudo chown **username:username** /desktop/**filename**

change the above for your username and file name

---

### Post by omns on 2008-04-24
or the startup manager does a nice job as well. An easy way to configure boot, grub and usplash options in one handy gui.

---

### Post by Ub1476 on 2008-04-24
```
sudo apt-get install startupmanager

```

---

