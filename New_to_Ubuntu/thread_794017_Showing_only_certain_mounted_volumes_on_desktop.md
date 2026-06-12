---
title: "Showing only certain mounted volumes on desktop"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-14
Hi,

I know it's possible to show either all mounted volumes on the desktop, or to show none at all, but is it possible to choose which ones it shows?

Thanks

---

### Post by TeoBigusGeekus on 2008-05-14
The file /etc/fstab defines which volumes will be mounted on boot up and therefore show up on your desktop.
```
gksudo gedit /etc/fstab
```

---

### Post by dwally89 on 2008-05-14
I want all my volumes to be mounted, but only some to be shown on the desktop.

---

