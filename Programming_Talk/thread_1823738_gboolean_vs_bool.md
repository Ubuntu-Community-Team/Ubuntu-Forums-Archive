---
title: "gboolean vs bool?"
date: 2011-08-12
forum: Programming Talk
---

### Post by nickos on 2011-08-12
alright so ive seen in many functions of type gbolean that return true or false.Is there any difference if its of type bool?

---

### Post by Bachstelze on 2011-08-12
The difference is that gboolean is not standard, while bool is.

---

### Post by cgroza on 2011-08-12
Wasn't gboolean introduced for having a bool equivalent in glibc since C does not have a bool type?

---

### Post by Bachstelze on 2011-08-12
> **cgroza said:**
> Wasn't gboolean introduced for having a bool equivalent in glibc since C does not have a bool type?

gboolean is a GLib type, not glibc. GLib is the core library used by GNOME, while glibc is the GNU C library. Totally different things.

---

### Post by Bachstelze on 2011-08-12
Otherwise they are mostly the same, a gboolean is an int that should only hold two values, TRUE and FALSE (uppercase). FALSE is defined as 0 and TRUE is defined as !FALSE.

---

### Post by nickos on 2011-08-12
right,thanks for that :)

---

