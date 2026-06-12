---
title: "[SOLVED] Where in Ubuntu would I check to see if there are any driver or hardware iss"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by GumpTron on 2008-10-13
I am going to install Ubuntu for the first time after playing with it using Live. I used live by booting from the cd and other than it being slow and the screen savers moving slowly things seemed fine. Still, is there a menu in Ubuntu similar to windows Device Manager? I assume this will tell me if everything on my computer is recognized. Thank you.

---

### Post by Forbees on 2008-10-13
system->administration->hardware drivers


that'll show if you have a graphics card driver installed

---

### Post by drs305 on 2008-10-13
gnome-device-manager is probably what you are looking for. It's in the 'universe' repository.

```
sudo apt-get install gnome-device-manager
```

System, Admin, Hardware Drivers as well.

---

