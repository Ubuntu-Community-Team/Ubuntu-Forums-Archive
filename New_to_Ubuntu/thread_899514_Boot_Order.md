---
title: "Boot Order"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by kf4tqj on 2008-08-24
How do I change the boot order where Windows will load first? I've got some stubborn family members that want it to just work like it did before. I know I've seen that here before but I can't find it now that I need it.
Thanks,
Woody / KF4TQJ

---

### Post by Elfy on 2008-08-24
Edit your menu list do you mean?

```
gksudo gedit /boot/grub/menu.lst
```

afaik you can move windows stanza above the 

> ### BEGIN AUTOMAGIC KERNELS LISTset default as 0 and it will boot win first and the win entry won't be moved on grub updates.

---

### Post by drs305 on 2008-08-24
A safe and easy way to tweak grub menu settings is with StartUp-Manager. You can set the default OS, how long the menu displays, how many kernels to show, and much more. I highly recommend this gui app.

Refer to the link in my signature line for a tutorial.

---

### Post by alzie on 2008-08-24
+1 for startup-manager

---

### Post by pikabuntu on 2008-08-24
yes, startup manager is probably the easiest way to go :)

---

### Post by nonpc on 2008-08-24
Maybe it is easier, but edit'ing files is more of an Linux way, lol. Not that scary as it might look.

---

