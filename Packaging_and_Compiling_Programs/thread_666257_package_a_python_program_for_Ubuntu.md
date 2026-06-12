---
title: "package a python program for Ubuntu"
date: 2008-01-13
forum: Packaging and Compiling Programs
---

### Post by timmie on 2008-01-13
Hello,
I would like to package some python programs and modules for Ubuntu.

For simple programs I found the following tutorial very helpful:
LinuxJensMakingDeb: [http://wiki.showmedo.com/index.php/LinuxJensMakingDeb](http://wiki.showmedo.com/index.php/LinuxJensMakingDeb)

But how to I package a module which has already a setup.py file?

Can you point me to any tutorial?

---

### Post by dholbach on 2008-01-14
Check out [https://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages](https://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages)

CDBS python-distutils.mk might be what you are looking for. [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages) to get it included in Ubuntu.

---

