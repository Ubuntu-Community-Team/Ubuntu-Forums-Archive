---
title: "ubuntu 12.04 64bit WINE"
date: 2012-05-07
forum: Packaging and Compiling Programs
---

### Post by ahso4271 on 2012-05-07
Hi
trying to compile wine 1.5.3 32bit I get:

configure: error: FreeType 32-bit development files not found. Fonts will not be built.

whatever I install it's the same. 64bit compiled but seems rubbish.
Thanks

---

### Post by Bachstelze on 2012-05-08
Why do you want to compile WINE? There's a PPA for that...

---

### Post by linuxsyst on 2012-05-08
why compile? open terminal and write ```
sudo apt-get install wine
```

---

### Post by davidvandoren on 2012-05-08
you might need to install ia32-libs-multiarch:i386 in order for wine 32 to work. 

Anyhow the one I installed from the software center works great.

---

