---
title: "zenity is to gnome as ??? is to xfce"
date: 2008-08-08
forum: Programming Talk
---

### Post by cszikszoy on 2008-08-08
Just wondering if anyone knows of a program similar to Kdialog (kde) and Zenity (gnome) for XFCE?

Thanks.

---

### Post by mocoloco on 2008-08-08
Still zenity.  Zenity uses gtk, which is what gnome and xfce use (as opposed to QT in KDE).  One difference between the two DEs is gnome has additional libraries and such, and some apps use these gnome-bindings so aren't straight gtk, meaning on xfce it has to load additional stuff and takes more memory.  Zenity is not one of those.  I've used it with xfce quite a bit.

There is also xdialog, but it's fugly and as mentioned you're not losing anything using zenity.

---

### Post by cszikszoy on 2008-08-08
> **mocoloco said:**
> There is also xdialog, but it's fugly and as mentioned you're not losing anything using zenity.

haha, yes, it is fugly, that's why I was hoping there was something pretty like zenity for XFCE.

Thanks.

---

