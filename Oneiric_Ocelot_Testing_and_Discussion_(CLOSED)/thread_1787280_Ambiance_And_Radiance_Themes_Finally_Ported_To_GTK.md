---
title: "Ambiance And Radiance Themes Finally Ported To GTK3 [Ubuntu 11.10 Oneiric Ocelot Upda"
date: 2011-06-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CreativeReach on 2011-06-20
founds this today! havent got update yet but glad to here it!
[http://www.webupd8.org/2011/06/ambiance-finally-ported-to-gtk3-ubuntu.html](http://www.webupd8.org/2011/06/ambiance-finally-ported-to-gtk3-ubuntu.html)

---

### Post by fjgaude on 2011-06-20
Great, and thanks... we were wondering when this would happen.

---

### Post by Harry33 on 2011-06-21
New package light-themes (0.1.8.15) is still not ready.
It is not a pure GTK+3 build.
It depends on both these
- gtk2-engines-murrine (>= 0.90.3+git20100810)
- gtk3-engines-unico (>= 0.1.0+r69)

---

### Post by lucazade on 2011-06-21
> **Harry33 said:**
> New package light-themes (0.1.8.15) is still not ready.
It is not a pure GTK+3 build.
It depends on both these
- gtk2-engines-murrine (>= 0.90.3+git20100810)
- gtk3-engines-unico (>= 0.1.0+r69)

It is normal because it should includes both gtk2-murrine and gtk3-unico themes to cover all possible applications.
With a gtk3 engine you can't skin old gtk2 apps, so a legacy theme and engine are required.

---

