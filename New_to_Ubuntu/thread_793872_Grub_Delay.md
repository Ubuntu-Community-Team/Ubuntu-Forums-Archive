---
title: "Grub Delay"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Mhurst1 on 2008-05-14
Is there a way to bypass the countdown to start Grub and just have it start right away?

---

### Post by hermes0710 on 2008-05-14
Yes, there is an option in /boot/grub/menu.lst that points to the countdown seconds. Turn it's value to 0

---

### Post by TeoBigusGeekus on 2008-05-14
```
gksudo gedit /boot/grub/menu.lst
```

There is something like timeout=... or timer=... (I am on xp right now). Change the setting to 1sec or something and save.

---

### Post by Joeb454 on 2008-05-14
The part you are looking for in the file mentioned above is "timeout 10" (I think the default is 10 anyway).

To be able to save it, open a terminal (Applications > Accessories > Terminal) and run ```
gksudo gedit /boot/grub/menu.lst
``` to edit the file :)

---

### Post by Mhurst1 on 2008-05-14
> **hermes0710 said:**
> Yes, there is an option in /boot/grub/menu.lst that points to the countdown seconds. Turn it's value to 0
Thanks I got it :)

---

### Post by drs305 on 2008-05-14
There is also a gui way to change the time:
System, Admin, Startup Manager, Boot Option, timeout in seconds window

---

### Post by hermes0710 on 2008-05-14
> **drs305 said:**
> There is also a gui way to change the time:
System, Admin, Startup Manager, Boot Option, timeout in seconds window

If you don't see it there install it :
```
sudo apt-get install startupmanager
```

---

