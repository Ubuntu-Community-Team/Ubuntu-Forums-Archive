---
title: "Gnome problems"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by TheManno1 on 2012-07-14
A picture says a thousand words.

---

### Post by Shadius on 2012-07-14
Need some details. What version of Ubuntu are you running? It appears that you're running GNOME Classic?

---

### Post by TheManno1 on 2012-07-14
Ubuntu 12.04 LTS it is supposed to be gnome I think

---

### Post by Shadius on 2012-07-14
> **TheManno1 said:**
> Ubuntu 12.04 LTS it is supposed to be gnome I think

It looks like it's GNOME Classic to me because of the top and bottom panels. Anyway, you can try reloading GNOME by doing *Alt+F2+R*.

---

### Post by TheManno1 on 2012-07-22
Alt f2 gets me the run command and when I typed restart in it something weird happened.Also the same problem that you can see in the picture happened in cinnamon.

---

### Post by ub07 on 2012-07-22
Did this problem just pop up? Or did it occur immediately after you installed 12.04?

Also, what is your graphics card?

When you log in, you have the ability to choose your desktop environment for the session. Could you confirm that this is Gnome by selecting "Gnome" again from the menu?

---

### Post by vasa1 on 2012-07-22
Do a clean, fresh installation and keep meticulous notes of even the most innocuous tweak. Then, if problems arise, people maybe able to help. This way, it's a lot of guesswork.

---

### Post by Favux on 2012-07-22
That looks like the background of Cairo/Glx Dock, the black rectangle above the bottom panel.

Is that what it is?  If it is it looks like your video chipset:
```
lspci | grep VGA
```
doesn't support Glx or it isn't enabled.

Either way you can tell Cairo Dock to use its non-Glx fallback.  You just lose some effects.

---

