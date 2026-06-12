---
title: "[SOLVED] how do i know what version i have"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Kcrim on 2008-11-28
how do i know if i have the feisty, edgy or dapper

---

### Post by sisco311 on 2008-11-28
open a terminal and type:
```
cat /etc/issue
```
or ```
lsb_release -a
```

---

### Post by jpeddicord on 2008-11-28
> **sisco311 said:**
> open a terminal and type:
```
cat /etc/issue
```

Another verbose command is:
```
lsb_release -a
```

In the GUI, you can find out by going to System > About Ubuntu. The version is reported under the Ubuntu logo in the help docs.

---

### Post by Kcrim on 2008-11-28
> **sisco311 said:**
> open a terminal and type:
```
cat /etc/issue
```
or ```
lsb_release -a
```

ok when I do the first one I get Ubuntu 8.10 \n \l

and when i do the second one i get
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

so which one do i have

---

### Post by adult swim on 2008-11-28
Ubuntu 8.10 Intrepid Ibex

---

### Post by sisco311 on 2008-11-28
> **Kcrim said:**
> ok when I do the first one I get Ubuntu 8.10 \n \l

and when i do the second one i get
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

so which one do i have

you have the latest stable version:** 8.10 (Intrepid Ibex).**

---

### Post by jpeddicord on 2008-11-28
You have Ubuntu 8.10, the Intrepid Ibex. (edit: d'oh, beaten to the punch!)

---

### Post by Kcrim on 2008-11-28
> **sisco311 said:**
> you have the latest stable version:** 8.10 (Intrepid Ibex).**

so Intrepid is different than edgy, dapper, feisty?

---

### Post by jpeddicord on 2008-11-28
> **Kcrim said:**
> so Intrepid is different than edgy, dapper, feisty?

Yep, it's quite a few versions newer.
Dapper - 6.06
Edgy - 6.10
Feisty - 7.04
Gutsy - 7.10
Hardy - 8.04
Intrepid - 8.10

---

