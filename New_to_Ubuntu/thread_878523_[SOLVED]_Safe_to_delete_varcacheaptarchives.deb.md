---
title: "[SOLVED] Safe to delete /var/cache/apt/archives/*.deb?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by mingle on 2008-08-03
Hi,

I've noticed that there are a lot of .deb installation packages (for apps and updates I've already installed) in the /var/cache/apt/archives/ directory.

Can I safely remove these?

Is there any command (or any program) that I can use to clean these caches and any other temp files on my system?

Cheers,

Mike.

---

### Post by Tim Sharitt on 2008-08-03
They can be safely removed. In a terminal enter
```
sudo apt-get clean
```
That should clear them out.

---

### Post by spectatorion on 2008-10-06
> **Tim Sharitt said:**
> They can be safely removed. In a terminal enter
```
sudo apt-get clean
```
That should clear them out.
to remove all but the latest version:
```
sudo apt-get autoclean
```

---

