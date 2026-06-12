---
title: "how do i mount my cd-rom?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by hazman on 2008-05-13
how do i mount my cd-rom? i recently upgraded to 8.04 and left external pcmcia cd-rom in thinking it would find drivers and install it.does it need mounting all its doing at moment is power light on and light on front just flashing

---

### Post by TeoBigusGeekus on 2008-05-13
Doesn't it show up in your /media folder?

---

### Post by alienexplorers on 2008-05-13
Try setting it up like this in /etc/fstab:

> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by tech9 on 2008-05-13
```
sudo mount /media/cdrom0
```or right on the CDROM device under computer and select mount

---

