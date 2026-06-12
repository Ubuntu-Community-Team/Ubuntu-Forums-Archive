---
title: "Lost panels or taskbars"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by nnjond on 2008-06-18
Hi, Can anyone help me please?

I lost power, and when I re-booted, I had lost the panels. I can't do anything now!

---

### Post by KenBW2 on 2008-06-18
Try alt+F2 and type in gnome-panel - that should start the panels up again.
Let me know

---

### Post by yragrelluf on 2008-06-18
Same thing happened to me after making a liveCD/ install disk of my customized installation. I had to reinstall gnome-panel by typing in the terminal sudo apt-get gnome-panel. I dont remember exactly how i opened the terminal though, ill let you know if i figure it out.

---

### Post by yragrelluf on 2008-06-18
Yeah, Thats it, alt + f2

---

### Post by tamoneya on 2008-06-18
if that doesnt work go down to tty mode and type:```
sudo dpkg-reconfigure ubuntu-desktop
```Then go back into X and try the alt-f2 gnome-panel again.

---

