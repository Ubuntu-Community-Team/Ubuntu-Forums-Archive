---
title: "gdebi-gtk error"
date: 2008-03-17
forum: Packaging and Compiling Programs
---

### Post by Martje_001 on 2008-03-17
Hi,
I'm trying to make an .deb file, but I obviously doing something wrong. When I install my package with gdebi-gtk I get an error message (the file may be corrupt..), but when I install it with 'dpkg -i' however, it installs fine.

Can someone take a look at the package in the attachment?

---

### Post by Martje_001 on 2008-03-18
OK, I've found a tool called **lintian** (which most of you properly know). It checks .deb-packages, and returns errors if they're not valid.

It have found some permission errors (which are fixed now) and these ones:
```
E: mypackage: no-copyright-file
E: mypackage: changelog-file-missing-in-native-package
W: mypackage: unknown-section internet

```
The first two are easy to fix, but the last one.. does anyone has got a list with sections?

---

### Post by Martje_001 on 2008-03-18
I'm stuck. 
Lintian says everything is fine, but I still can't get it install via the GUI. Dpkg installs fine. Anybody?

Edit: Package attached.

---

