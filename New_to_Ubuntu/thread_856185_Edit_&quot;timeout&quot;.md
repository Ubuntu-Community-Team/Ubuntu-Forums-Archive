---
title: "Edit &quot;timeout&quot;"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-07-11
Hey All:

Want to change the "timeout" in /menu.lst. Can't find the proper command in Kubuntu. Was "gksudo gedit /boot/grub/menu.lst," which doesn't work in Kubuntu.

Thank you,
Ed

---

### Post by dracayr on 2008-07-11
I don't know KDE, but you could use nano or vim:

sudo nano /boot/grub/menu.lst

dracayr

---

### Post by angry_johnnie on 2008-07-11
It's **kdesu** instead of gksu/gksudo for kde.

---

### Post by philinux on 2008-07-11
I think the editor is

kate

---

### Post by Whatrymes on 2008-07-11
Can you give me the whole command, it is still not working.

Thanks,
Ed

---

### Post by hyper_ch on 2008-07-11
what command is not working?

---

### Post by angry_johnnie on 2008-07-11
That's

```
kdesu kate /boot/grub/menu.lst
```

or (i'm not sure which is kubuntu's editor.)

```
kdesu kwrite /boot/grub/menu.lst
```

or (with a terminal editor)

```
sudo nano /boot/grub/menu.lst
```

---

### Post by Whatrymes on 2008-07-11
This was wht I needed Thanks!!

Ed

kdesu kwrite /boot/grub/menu.lst

---

