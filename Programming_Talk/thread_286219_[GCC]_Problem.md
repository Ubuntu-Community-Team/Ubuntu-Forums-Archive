---
title: "[GCC] Problem"
date: 2006-10-27
forum: Programming Talk
---

### Post by Salvatore Di Fazio on 2006-10-27
Hi guys,
I did read some posts about this problem but I couldn't resolve my problem.
If I try to use gcc to make something the system alert me that gcc isn't installed.
but if I check:

```

sudo dpkg -l | grep gcc
ii gcc-3.3-base
ii gcc-4.0-base
ii libgcc1

```

Somebody told me to install the package build-essential
But I couldn't find it:

```

salvo@linux:~/Desktop$ sudo apt-cache search build | grep essential
salvo@linux:~/Desktop$

```

tnx

---

### Post by tpg on 2006-10-27
Try running
```
sudo apt-get update
sudo apt-get install build-essential
```

which should install everything needed to get GCC working :)

---

### Post by Salvatore Di Fazio on 2006-10-27
okkey I forgot to do and update of the system.
Tnx :)

---

