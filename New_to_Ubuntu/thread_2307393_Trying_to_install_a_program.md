---
title: "Trying to install a program"
date: 2015-12-24
forum: New to Ubuntu
---

### Post by lightning_bolt6 on 2015-12-24
I'm trying to install a program that requires Mesa, which I think I've done successfully. However, it also says to do this: ```
You may also need to run /sbin/ldconfig as root
to update the system after installing Mesa.
(First, add '/usr/local/lib' to /etc/ld.so.conf if
you installed Mesa under /usr/local, the default.
```
What commands do I type to accomplish this?

---

### Post by The Cog on 2015-12-24
Without knowing anything about what those commands do, the command needed are:
```
sudo /sbin/ldconfig
sudo nano /etc/ld.so.conf
```

Nano is a simple text editor. Use Ctrl-X to exit, it asks if you want to save.

---

