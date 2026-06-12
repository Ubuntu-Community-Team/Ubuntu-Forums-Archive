---
title: "how to remove previous installation"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by nguyenabcd on 2013-01-31
Hi all!
I am trying to install ubuntu 12.10 by vitual drive(iso file). In the install process, I choose help me boot from cd. I got an error " A previous installtion was detect in G:\ubuntu. Please uninstall that before continuing". My trouble is that I deleted this partition. What should I do to solve this problem?

---

### Post by Sef on 2013-01-31
> I am trying to install ubuntu 12.10 by vitual drive(iso file). In the install process, I choose help me boot from cd. I got an error " A previous installtion was detect in G:\ubuntu. Please uninstall that before continuing". My trouble is that I deleted this partition. What should I do to solve this problem?

Did you reformat that partition that you deleted?

---

### Post by Impavidus on 2013-02-01
> **nguyenabcd said:**
>  A previous installtion was detect in **G:\ubuntu**. Please uninstall that before continuing
Sounds like a windows drive letter, so I assume this was a wubi install. They don't need a partition of their own, but you made one anyway. I don't know much about Windows (stopped using it five years ago) and never tried a wubi install myself, but somewhere in windows the presence of Ubuntu must still be registered. I think there must be an uninstaller somewhere.

If you want a full installation on a partition of its own, you'll have to burn the iso and boot from it.

---

