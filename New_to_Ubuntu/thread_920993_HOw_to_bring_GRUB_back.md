---
title: "HOw to bring GRUB back?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-09-15
I have linux as well as windows xp installed on my system.

due to a virus I had to format my c: drive and reinstall windows. Now the problem is that during startup i dont see the grub boot loader. so i cant startup my linux installation.

How do i bring it back?

---

### Post by caljohnsmith on 2008-09-15
Try booting your Live CD, open a terminal, and do:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should work, but let me know if you run into more problems.

---

### Post by faraz_k86 on 2008-09-15
k thx , so ill assume that here x is the windows partition and y is the linux partition?

---

### Post by faraz_k86 on 2008-09-15
thx a lot it worked :)

---

