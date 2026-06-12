---
title: "grub takes time in loading"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by nnamdi on 2008-05-30
hello friends since i got my cdrom issues at startup my boot loader grub takes time in loading can anyone help me on that.

---

### Post by philinux on 2008-05-30
Not sure if I've got you right but. Have you set the countdown timeout to say 2 or 3 seconds instead of the default 10.

gksudo gedit /boot/grub/menu.lst

```
look for the timeout line, this is mine.
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2
```

---

