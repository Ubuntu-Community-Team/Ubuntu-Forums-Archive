---
title: "Nic not saving dns ip"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by GR-Man on 2008-06-13
HI
I installed Ubuntu on a benq notbook and it works great only problem is that the nic does not want to except the dns ip. I changed it from DHCP to manual. I also tried to edit the network file but it will not allow me to save changes.
Any help would be great.

Thank you
G

---

### Post by hyper_ch on 2008-06-13
you mean the nameserver ip?

you can add it manually:
```

sudo nano /etc/resolv.conf

```

and add:

```

nameserver www.xxx.yyy.zzz

```

---

### Post by GR-Man on 2008-06-13
Thanks for the reply it worked

---

### Post by hyper_ch on 2008-06-13
then marked the thread title as [solved] from the thread tools drop down :)

---

