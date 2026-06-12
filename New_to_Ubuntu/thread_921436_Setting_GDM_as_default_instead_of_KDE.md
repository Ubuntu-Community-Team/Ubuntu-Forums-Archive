---
title: "Setting GDM as default instead of KDE"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by littletinman on 2008-09-16
I'm having trouble getting GDM set as the default login screen. It says i need to set it as default. How do i do that?

---

### Post by iaculallad on 2008-09-16
If you have installed the (k)ubuntu desktop environment on top of Ubuntu or the other way around:.

```
sudo dpkg-reconfigure gdm
```

EDIT:

Or you could try:

```
kdesu kate /etc/X11/default-display-manager
```

and set it to: 

(For GDM)
> /usr/sbin/gdm

(For KDM)
> /usr/sbin/kdm

---

### Post by rraj.be on 2008-09-16
> **littletinman said:**
> I'm having trouble getting GDM set as the default login screen. It says i need to set it as default. How do i do that?

Run this command in terminal.


```
sudo dpkg-reconfigure gdm
```

---

### Post by luketjm on 2008-09-24
> **iaculallad said:**
> If you have installed the (k)ubuntu desktop environment on top of Ubuntu or the other way around:.

can i savely delete the kde packages because i dont need them? i tested kde 4.1 but i dont like it.

thx

---

