---
title: "No rule to make target /usr/lib/libX11.so"
date: 2011-06-12
forum: Packaging and Compiling Programs
---

### Post by Amablue on 2011-06-12
I'm writing a program using the library SFML, which requires libX11. I just recently upgraded to ubuntu 11.04, and ever since I did I can't compile my program. I get the following error:

```
make[3]: *** No rule to make target `/usr/lib/libX11.so', needed by `lib/libsfml-window.so.2.0.0'.  Stop.

```

I thought maybe that when I upgraded Ubuntu that package was uninstalled for some reason, but according to Synaptic, I have libX11-dev (I'm just assuming that's what I should be looking for, but I'm probably wrong).

---

