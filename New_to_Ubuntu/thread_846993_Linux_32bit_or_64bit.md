---
title: "Linux 32bit or 64bit?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by x88a on 2008-07-02
hwo do i know if my linux is 32bit or 64bit?
tq

---

### Post by iaculallad on 2008-07-02
> **x88a said:**
> hwo do i know if my linux is 32bit or 64bit?
tq

Drop to your terminal:

```
uname -m
```

32 bit version will output i686
64 bit version will output x86_64

---

### Post by WRDN on 2008-07-02
In the terminal, type:

```
uname -a
```

This will show information about the current kernel.

For example, it may output:

```
Linux Desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 **i686** GNU/Linux

```

The important part here is "i686", referring to a 32bit OS. A 32bit OS can also be given the form, "x86".
For a 64bit OS, "x86_64" would appear.

---

### Post by goforlinux on 2008-07-02
ya what those guys said :)

---

