---
title: "ubuntu brightness automatically without any delay"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by tux-world on 2013-06-27
after change brightness to for example 30% without delay and between work on laptop , that automatically change to 60% after 10~15 second. i'm change

```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

and update grub but that does not any change and i have this problem now.

---

### Post by cmcanulty on 2013-06-27
try installing xbacklight and add it to startup apps

---

### Post by tux-world on 2013-06-27
> **cmcanulty said:**
> try installing xbacklight and add it to startup apps

this package have problem
```
tux-world@tux-world ~ $ xbacklight -set 100%
tux-world@tux-world ~ $ xbacklight
50.000000

```

---

### Post by cmcanulty on 2013-06-27
Oh it works for me but obviously isn't working for you

---

