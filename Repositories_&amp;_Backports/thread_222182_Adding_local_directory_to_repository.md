---
title: "Adding local directory to repository"
date: 2006-07-24
forum: Repositories &amp; Backports
---

### Post by simteq on 2006-07-24
I am new to Ubuntu and have downloaded several Oracle deb files however I do not know how to actually install them

---

### Post by jordilin on 2006-07-24
dpkg -i | --install package_file

---

### Post by jordilin on 2006-07-24
I'll explain it a little bit more. With dpkg you can install individual *.deb files, so writing
```
dpkg -i nameofthepackage.deb
```
will install the software

---

