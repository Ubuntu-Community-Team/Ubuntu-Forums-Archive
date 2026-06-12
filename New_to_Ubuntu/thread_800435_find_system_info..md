---
title: "find system info."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-05-19
Hi all, i have a server with ubuntu server on it and i don't have gnome, kde or any form of gui installed. and i wanted to check what hardware was install on that machine, more specifically the cpu and ram. how could i do this?

---

### Post by vitorgatti on 2008-05-19
sudo lshw |more

or

lspci

---

### Post by Dissident85 on 2008-05-19
> **vitorgatti said:**
> sudo lshw |more

or

lspci

cheers, that worked :)

---

### Post by tamoneya on 2008-05-19
another useful command is ```
cat /proc/cpuinfo
cat /proc/meminfo
```

---

### Post by sdennie on 2008-05-19
Also, lshw has a nice feature that will generate html for you instead of having to page through it in a terminal:

```

sudo lshw -html > hardware.html

```

---

