---
title: "Eclipse opening files in gedit?!"
date: 2009-11-12
forum: Programming Talk
---

### Post by luckyone on 2009-11-12
I just did a fresh install with 9.10 and for some reason, when I try to open a file in eclipse, it instead opens in gedit.  Anyone know why this is happening and how to stop it?

---

### Post by Somme on 2009-11-12
In Terminal:

```
eclipse somefile.cpp
```

What's the output / result ?

---

### Post by ravindra.rajaram on 2009-11-12
Same problem here with Eclipse.. I use the pydev extension
eclipse xyz.py 
opens the file in the Eclipse but all formatting is lost !

---

### Post by luckyone on 2009-11-13
Somme, there's no output to the terminal.  I did "eclipse Variability.java" and eclipse started up which then started gedit.

---

### Post by ravindra.rajaram on 2009-11-13
I checked in 'Synapctic' and the package 'eclipse' was shown 'unchecked'!
checking the box, downloading the packages..seems to have solved the problem for me

---

### Post by kroiz on 2009-11-28
Yes that fixed the problem for me too.
I guess there is a problem when installing from "Ubuntu software center".

---

