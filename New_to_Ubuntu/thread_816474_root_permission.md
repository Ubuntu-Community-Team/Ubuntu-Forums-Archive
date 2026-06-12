---
title: "root permission"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-02
what command would i enter in the terminal that would allow me to edit xorg.conf? now when i try to edit it, when i go to save it, it says that i don't have the necessary permissions.

---

### Post by oldos2er on 2008-06-02
"gksudo gedit /etc/X11/xorg.conf"

---

### Post by BennyHill on 2008-06-02
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by SunnyRabbiera on 2008-06-02
sudo is what you need, it will enter you into root user privileges.

---

### Post by maybeway36 on 2008-06-02
```
gksu gedit /etc/X11/xorg.conf
```
or if X11 isn't working:
```
sudo nano /etc/X11/xorg.conf
```

---

