---
title: "[SOLVED] Cannot compile ANYTHING."
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Slime mold on 2008-11-20
Hello Ubuntu community. I recently installed Xubuntu on my computer, and while it works fantastically for most uses, it cannot compile any of the tarball-only software I have encountered. I have also attempted to compile a bare bones project in mono develop, but to no avail.

The error I get when attempting to compile from tarball is:

```
configure: error: zlib library not found or incompatible, please specify the correct path with --with-zlib=DIR... stopping
```

EDIT: My version of Ubuntu is Xubuntu 8.04.

---

### Post by taurus on 2008-11-20
Have you installed the build-essential package?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Slime mold on 2008-11-20
> **taurus said:**
> Have you installed the build-essential package?

```
sudo apt-get update
sudo apt-get install build-essential
```

Thank you, that probably prevented myriad other errors I would have encountered in the future. However, the zlib problem is still extant after installing the build-essential package.

---

### Post by djbushido on 2008-11-20
try installing zlib from apt:
```
sudo apt-get install zlib
```

---

### Post by Slime mold on 2008-11-20
> **djbushido said:**
> try installing zlib from apt:
```
sudo apt-get install zlib
```

Tried that already, apt says it cannot find the package. Thanks though.

---

### Post by LowSky on 2008-11-20
you can get zlib here

[http://www.zlib.net/zlib-1.2.3.tar.gz](http://www.zlib.net/zlib-1.2.3.tar.gz)

---

### Post by prshah on 2008-11-20
> **djbushido said:**
> try installing zlib from apt:
```
sudo apt-get install zlib
```

> **Slime mold said:**
> Tried that already, apt says it cannot find the package. Thanks though.

It's zlibc, or zlib1-dev if you want to do development on zlibc itself.

```
sudo apt-get install zlibc
```

---

### Post by Slime mold on 2008-11-20
> **LowSky said:**
> you can get zlib here

[http://www.zlib.net/zlib-1.2.3.tar.gz](http://www.zlib.net/zlib-1.2.3.tar.gz)

Thank you very much for this link. It all works now!

---

### Post by Carl Hamlin on 2008-11-20
> **Slime mold said:**
> Tried that already, apt says it cannot find the package. Thanks though.

Prior to installing anything with apt-get, it's usually a good idea to do an 'apt-get update' to ensure that your package availability lists are current. If you've already done that and it's still telling you it can't find the package then it's likely under another name.

If you're developing software in C, the name of the package you're looking for is 'zlibc'.

---

