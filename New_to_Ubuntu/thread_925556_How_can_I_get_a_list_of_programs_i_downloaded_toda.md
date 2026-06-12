---
title: "How can I get a list of programs i downloaded today?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ahuman on 2008-09-20
Hi: Is there any way I can get a list of programs I downloaded today? I want to get rid of one, but can't remember its name offhand.

---

### Post by mc4100 on 2008-09-20
System -> Administration -> Synaptic
And then File menu -> History will show you all the packages you have installed (ever).

---

### Post by willca on 2008-09-23
sudo dpkg -l > list

---

### Post by jemate18 on 2008-09-23
> **willca said:**
> sudo dpkg -l > list

dpkg -l  => It gives all your installed package but not sorted by date.

The OP needs to know the installed package in a specific date

---

### Post by Greyed on 2008-09-23
Or if one is using aptitude

less /var/log/aptitude

---

