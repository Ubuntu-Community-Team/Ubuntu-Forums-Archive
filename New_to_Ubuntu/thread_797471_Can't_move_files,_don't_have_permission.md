---
title: "Can't move files, don't have permission"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Infini on 2008-05-17
How do I give myself the required permissions to move files where I want to? I can't seem to move files into my usr/share folder.

```
Error moving file: Permission denied
```

This probably applies to more than just that folder but that's the one place where I want to move stuff.

---

### Post by macaholic on 2008-05-17
With individual files use 'sudo' in front of mv, or any other command you want to run as root, excluding graphical ones in which case you would use gksu.

---

### Post by Infini on 2008-05-17
So there's no way to do it drag n' drop style?

---

### Post by bsharp on 2008-05-17
```
gksudo nautilus
```

---

### Post by macaholic on 2008-05-17
> **bsharp said:**
> ```
gksudo nautilus
```
Ya, that is the way to do it, but be weary, it will then load nautilus with all your root users settings, like backgrounds.

---

### Post by Infini on 2008-05-17
Oh.. that easy huh? Thanks a lot.

---

### Post by shifty_powers on 2008-05-17
yup, jyst be careful what you do with nautilus in root mode, you can a lot of damage ;)

---

### Post by alex_anthony on 2008-05-17
```
gksudo nautilus --no-desktop
```
might be better

---

### Post by Infini on 2008-05-17
Ah, well I won't be doing anything I'm uncertain of. What does the extension of --no-desktop do?

---

### Post by alex_anthony on 2008-05-17
nautilus runs your desktop. Any nautilus that is started without --no-desktop starts managing it aswell. You don't really want to have root doing that. It's generally good practice to have --no-desktop with nautilus
Not catastrophic without it though

---

