---
title: "install winde to e to install windows after installing ubuntu, is it possible?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-17
hi
Thank you for reading my post
is it possible to install windows after we installed ubuntu and keep ubuntu in its way?
I mean without killing ubuntu.
I have a free space in my laptop and I have ubuntu installed on it, now I want to install widows vista without losing ubuntu.

Thanks

---

### Post by oilchangeguy on 2008-11-17
> **legolas_w said:**
> hi
Thank you for reading my post
is it possible to install windows after we installed ubuntu and keep ubuntu in its way?
I mean without killing ubuntu.
I have a free space in my laptop and I have ubuntu installed on it, now I want to install widows vista without losing ubuntu.

Thanks

yes, you'll simply have to reinstall grub. also please edit your title, so that it makes sense.

---

### Post by caljohnsmith on 2008-11-17
Sure, you can install Windows after Ubuntu; just reinstall Grub afterwards by booting your Live CD, opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should be it. Let me know if you have any problems. :)

---

