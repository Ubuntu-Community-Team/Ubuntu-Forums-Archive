---
title: "Uninstall programs"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by jspolen on 2008-06-22
I was wondering how to uninstall a program that was not installed by the *Add/Remove* utility.

That is, I used ./configure -> make -> make install or similar.

---

### Post by Xerp on 2008-06-22
Sometimes you can

```
make uninstall
```

The other thing you can use is checkinstall

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by the_doc on 2008-06-22
Depending on the size of the program you could always examine the make files install target to see what files were put where then remove accordingly.

---

