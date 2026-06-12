---
title: "ttf fonts"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-09-11
in 10.10, i could download a .ttf font file, double click it, some gui would open & it would install.

not happening in 11.10 (gn-sh or unity)

is it ok just to put the file in ~/.fonts ?

it works but is it kosher ?

---

### Post by VinDSL on 2011-09-11
> **flipper T said:**
> is it ok just to put the file in ~/.fonts ?
Placing fonts in ~/.fonts should work just fine, then run:

```

fc-cache -fv

```

...to rebuild the font cache.  ;)

---

### Post by flipper T on 2011-09-11
thanks

did not know about [FONT=monospace]font-cache-thingy[/FONT]

---

