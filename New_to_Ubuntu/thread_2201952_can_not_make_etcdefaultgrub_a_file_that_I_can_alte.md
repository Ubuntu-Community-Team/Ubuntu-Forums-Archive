---
title: "can not make /etc/default/grub a file that I can alter it is read-only chmod"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by keith14 on 2014-01-26
Hi,
 I want alter file /etc/default/grub but it is read only file and chmod will not change this. What do I need to do?
Thanks,
Keith

---

### Post by DuckHook on 2014-01-26
Any file outside of the /home directory belongs to root including everything under /etc and must be manipulated using *sudo*. ***IMPORTANT*** Do *NOT* chmod it. Instead,```
sudo nano /etc/default/grub
```

---

### Post by oldfred on 2014-01-26
This should work.
 gksudo gedit /etc/default/grub


 Details on settings in /etc/default/grub, with terminal:
 info -f grub -n 'Simple configuration'

---

### Post by DuckHook on 2014-01-26
Perhaps if you tell us what you are trying to do, we can better guide you without risk of you borking your system.

Any changes to */etc/default/grub* won't take effect until you also do:```
sudo update-grub
```

---

### Post by QIII on 2014-01-26
Just a point here --

If you use nano in the terminal, sudo is good.

But note that oldfred's suggestion uses gksudo because gedit is a graphical interface.

Don't mix the two up.  Always use gksudo for graphical applications.

---

