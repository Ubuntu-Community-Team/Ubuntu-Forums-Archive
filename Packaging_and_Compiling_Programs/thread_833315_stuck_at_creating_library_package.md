---
title: "stuck at creating library package"
date: 2008-06-18
forum: Packaging and Compiling Programs
---

### Post by melopsittacus on 2008-06-18
Hello!

I am learning how to package a library based on this MOTU school session:
[https://wiki.ubuntu.com/MOTU/School/LibraryPackaging](https://wiki.ubuntu.com/MOTU/School/LibraryPackaging)

It is all fine, however when I issue the command:
```
fakeroot make -f debian/rules binary
```

I get an error from dpkg-gencontrol:
```
dpkg-gencontrol: error: source package name 'PACKAGE' contains illegal character 'P'
```

I checked through the configuration files, however I did not find the package name 'PACKAGE' anywhere.

Could anyone tell me what might be wrong?

---

