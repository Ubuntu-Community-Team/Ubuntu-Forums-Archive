---
title: "ubuntu fails to load"
date: 2015-12-09
forum: New to Ubuntu
---

### Post by Pedro_Qamata on 2015-12-09
boot-repair pastebin  - [http://paste.ubuntu.com/13860267/](http://paste.ubuntu.com/13860267/)

---

### Post by sandyd on 2015-12-09
For some reason, grub cannot find your files, boot repair indicates /etc/grub.d and /etc/fstab is missing.

Can you post the output of the following
```

sudo umount /dev/sda1
sudo mount /dev/sda1 /mnt
ls -l /mnt/etc

```

---

