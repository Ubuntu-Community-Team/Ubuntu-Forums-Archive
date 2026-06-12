---
title: "How to install GCC 3.0 in Ubuntu 8.04"
date: 2008-10-22
forum: Packaging and Compiling Programs
---

### Post by codeAries on 2008-10-22
Am I a fool... Maybe :)

I really need to install GCC 3.0, someone help me out please.

Thank you in advance.

---

### Post by bruce89 on 2008-10-22
[gcc-3.4]("apt:gcc-3.4") or perhaps [gcc-2.95]("apt:gcc-2.95")

---

### Post by codeAries on 2008-10-22
Bruce89, thank you.

But do i need to uninstall the present (GCC 4.2.4) GCC?

If so, how will i remove?

---

### Post by bruce89 on 2008-10-25
I suspect the old releases can be called with something gcc-2.9 or gcc-3.0. See what dpkg -L gcc-2.95/gcc-3.4 says.

---

