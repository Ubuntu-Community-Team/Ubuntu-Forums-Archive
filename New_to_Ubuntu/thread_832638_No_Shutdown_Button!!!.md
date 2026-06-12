---
title: "No Shutdown Button!!!"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by bob16 on 2008-06-17
hi
i was playin around with my power options and now, theres no more shtdown button when i want to shut my laptop down

theres only hibernate, suspend, log out and switch users

how can i get my shutdown button back?

---

### Post by geezerone on 2008-06-17
Do you remember some of what you changed and did you reboot to find you don't have these options?

To shutdown in a terminal type ```
sudo shutdown now -P
```

---

### Post by cariboo on 2008-06-17
Can you just log out and shutdown from the login screen?

JIm

---

### Post by wormser on 2008-06-18
It usually is a setting with GDM.  There is a check box under System> Administation> Login Window> Local tab and check Show Actions Menu. Another way is to run the command.

```
sudo dpkg-reconfigure gdm
```

---

### Post by bob16 on 2008-06-18
> **cariboo907 said:**
> Can you just log out and shutdown from the login screen?

JIm
no i cant

---

### Post by yubbs on 2008-06-18
try going to system> administration> login window

in the local tab check "show actions menu"

---

### Post by bob16 on 2008-06-18
> **yubbs said:**
> try going to system> administration> login window

in the local tab check "show actions menu"

THANK YOU!!!

its so fkin simple and i havent thought of that

---

