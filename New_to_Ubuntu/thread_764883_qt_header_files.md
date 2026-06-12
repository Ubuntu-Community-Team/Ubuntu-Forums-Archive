---
title: "qt header files"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by ahaider on 2008-04-24
I want to compile the package named kphone. While configuring it, it gives error

```
checking location of Qt header files...
not found. Giving up.
```

What package is missing ?

---

### Post by Monicker on 2008-04-24
> **ahaider said:**
> I want to compile the package named kphone. While configuring it, it gives error

```
checking location of Qt header files...
not found. Giving up.
```

What package is missing ?

Depends on what version of Qt it needs.

Perhaps libqt3-headers or libqt4-dev - check the application requirements.

---

### Post by ahaider on 2008-04-24
> **Monicker said:**
> Depends on what version of Qt it needs.

Perhaps libqt3-headers or libqt4-dev - check the application requirements.

What the hell this is...

I have hardly managed to install both, libqt3-headers as well as libqt4-dev. But still the same error.

---

### Post by Monicker on 2008-04-24
> **ahaider said:**
> What the hell this is...

I have hardly managed to install both, libqt3-headers as well as libqt4-dev. But still the same error.


Just curious...why are you manually compiling kphone?  Packages exist for it in the Ubuntu Universe repository.

There should be a README with the app showing what its prerequisites are.

---

### Post by Monicker on 2008-04-24
[QUOTE=ahaider;4780149]What the hell this is...

grrr..

---

