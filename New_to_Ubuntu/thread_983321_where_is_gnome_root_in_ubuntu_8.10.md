---
title: "where is gnome_root in ubuntu 8.10?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-15
Hi
Can someone please let me know where is gnome_root in ubuntu 8.10?
I want to install SyncVFS and it needs the gnome_root, installation link which talks about gnome_root is [http://www.synce.org/moin/SynceTools/SynceVfs](http://www.synce.org/moin/SynceTools/SynceVfs)

---

### Post by legolas_w on 2008-11-16
Bump up, I hope someone sees the question.

Thanks

---

### Post by legolas_w on 2008-11-16
Any comment?

thanks

---

### Post by mapes12 on 2008-11-16
Gnome is the desktop environment. The only way I know of accessing the GUI with root privileges is ```
gksu nautilus
```

---

### Post by Patrick793 on 2008-11-16
Where it talks about gnome_root it says this:
> In Ubuntu 7.10 I had to use this configure line:

./configure --prefix=/usr --sysconfdir=/etc
I guess using this:
```
./configure --prefix=/usr --sysconfdir=/etc
```
would also work in Intrepid.

---

