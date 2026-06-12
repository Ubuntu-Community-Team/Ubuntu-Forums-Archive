---
title: "Login fail"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by ihaq2 on 2011-10-03
System not accepting my password, Im sure I type it the way it is. Anyway, I tried to change it via live cd - it happened not to work as well. My grub menu doesnt appear. What should I do?

---

### Post by seawolf167 on 2011-10-03
Try holding [SHIFT] during boot to get the Grub2 menu. If that doesn't work, you can re-install Grub2 following [this guide]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2"). After you have it installed, run

```
sudo update-grub
```

to pick up any other operating systems (i.e. Windows) you may have installed.

---

