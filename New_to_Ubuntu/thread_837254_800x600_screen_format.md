---
title: "800x600 screen format"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by ruffen91 on 2008-06-22
The only formats I can use is 800x600 and 640x480, even though my screen in 17' widescreen. What can I do to fix this? I have nvidia

---

### Post by PmDematagoda on 2008-06-22
> **ruffen91 said:**
> The only formats I can use is 800x600 and 640x480, even though my screen in 17' widescreen. What can I do to fix this? I have nvidia

Did you install the Nvidia driver? If so, how did you install it?

---

### Post by ruffen91 on 2008-06-22
I haven't installed anything on ubuntu. It says that the nvidia driver is "not in use".

---

### Post by phidia on 2008-06-22
Did you install the nvidia driver through System>Administration>Hardware drivers or restricted drivers (depending on which version of ubuntu you're using)?
Take a look at your /etc/X11/xorg.conf to see which driver and modelines are listed there.

---

### Post by bred on 2008-06-22
> **ruffen91 said:**
> I haven't installed anything on ubuntu. It says that the nvidia driver is "not in use".

[COLOR="Blue"]u need nvidia driver[/COLOR]

---

### Post by sailor2001 on 2008-06-22
go to :  system/administration/hardware drivers

then: gksudo displayconfig -gtk

---

### Post by Masoris on 2008-06-22
Type Alt+F2, and type *gksu displayconfig-gtk*. And change monitor and screen resolution setting.

---

