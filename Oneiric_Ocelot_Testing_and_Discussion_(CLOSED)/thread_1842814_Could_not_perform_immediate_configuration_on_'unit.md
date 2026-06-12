---
title: "Could not perform immediate configuration on 'unity-2d'"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Justin Trouble on 2011-09-12
I thought I'd have a play with Oneiric!

Trouble is the upgrade failed part way through the install with the error:

```
Could not perform immediate configuration on 'unity-2d'
```

I'm just trying to work out what's wrong.

Has anyone seen this before and can help?

Thanks!

---

### Post by cariboo on 2011-09-12
It could be several things. To complete the upgrade, start in recovery mode and select dpkg from the menu.

---

### Post by BiggieStylein on 2011-09-12
I had this same problem while running apt-get dist-upgrade. I've been running Oneiric for a while now, so it wasn't a recent upgrade. I solved it by running dpkg -i on the new unity-2d .deb file, then running apt-get dist-upgrade again and it worked fine. Not sure what the problem is though, or why apt stopped... but at least its easy enough to get around.

---

