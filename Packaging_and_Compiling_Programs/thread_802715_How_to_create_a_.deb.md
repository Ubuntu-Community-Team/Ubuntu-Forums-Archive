---
title: "How to create a .deb"
date: 2008-05-21
forum: Packaging and Compiling Programs
---

### Post by Tux.Ice on 2008-05-21
i need to know how to create a deb of this.

---

### Post by SunnyRabbiera on 2008-05-21
dpkg will probably do it for you.
Or alien, if its not in source code.

---

### Post by bufsabre666 on 2008-05-21
```
sudo apt-get checkinstall
```

and when compiling

```
./configure
make
sudo checkinstall
```

it will ask you a few questions and when its done there will be a deb in the folder you were working in

---

### Post by qazwsx on 2008-05-21
Definately not an expert.

But is this really the right way? I mean your data.tar.gz includes $HOME folders. Never seen in real debs  $HOME folders.
Will it affect your permissons then?

---

### Post by Tux.Ice on 2008-05-21
it needs to create a .installer folder in ~/ how would you do this

---

### Post by bufsabre666 on 2008-05-21
> **Tux.Ice said:**
> it needs to create a .installer folder in ~/ how would you do this

```

sudo mkdir ~/.installer 
```

---

### Post by K.Mandla on 2008-05-21
Moved to Packaging and Compiling Programs.

---

### Post by ubuntu-freak on 2008-05-21
Is "sudo checkinstall -D" not necessary?
 
Nathan

---

### Post by panayk on 2008-05-22
For proper debian packages start here:

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

Since your package is a collection of scripts I imagine you'll want to install them under /usr/bin.

---

