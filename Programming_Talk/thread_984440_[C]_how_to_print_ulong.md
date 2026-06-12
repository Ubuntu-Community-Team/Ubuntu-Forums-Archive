---
title: "[C] how to print ulong?"
date: 2008-11-16
forum: Programming Talk
---

### Post by days_of_ruin on 2008-11-16
I am actually coding it in vala but I am assuming that its exactly
the same because vala just generates c code.
%d is for int but what do you use for a ulong?

---

### Post by Nemooo on 2008-11-16
It's %lu.

---

### Post by nvteighen on 2008-11-16
Isn't it %uld? (%ld is for long)

---

### Post by Nemooo on 2008-11-16
There's no need for the d, since u is of type unsigned int. Only if it's not of type int you have to prefix u.

---

### Post by days_of_ruin on 2008-11-16
> **Nemooo said:**
> It's %lu.

Thanks that works.

---

