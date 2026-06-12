---
title: "build from source error"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by ahmed.cnbd on 2011-10-22
I'm trying to build a program from it's source
but after ./configure command
I got this
 
unknown gdk target

so anyone have a good idea?  ;)

---

### Post by gsmanners on 2011-10-22
I think I'd have a better idea if you told us what you're building.

---

### Post by ahmed.cnbd on 2011-10-22
as you want 
you know I can install it easily in other ways but I just want to try the experiment of building it 

it's gnome-terminal-3.2.1.tar

---

### Post by gsmanners on 2011-10-22
Okay, try this:

```
sudo apt-get build-dep gnome-terminal
```

I think that should get you past the configure step.

---

### Post by ahmed.cnbd on 2011-10-22
thanks

---

