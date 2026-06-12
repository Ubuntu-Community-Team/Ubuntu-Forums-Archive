---
title: "Updating non booted flash from booted flash -???"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-21
I have a stable 11.10 on stick A and I love it.

Stick B is to be used on another PC, but it will only boot to Terminal.

Is it possible to install drivers, etc. on stick B when running on stick A?

---

### Post by MG&amp;TL on 2012-05-21
I don't think so.

What you could try is downloading the packages required, then copying them to the other USB and running:

```
dpkg -i <package.deb>
```

there, replacing <package.deb> with the name of your packages.

Why do you want to do this? There may be an easier route to take.

---

