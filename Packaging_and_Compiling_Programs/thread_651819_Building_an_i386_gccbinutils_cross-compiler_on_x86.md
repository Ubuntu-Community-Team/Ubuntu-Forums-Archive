---
title: "Building an i386 gcc/binutils cross-compiler on x86_64"
date: 2007-12-28
forum: Packaging and Compiling Programs
---

### Post by AntiRush on 2007-12-28
I've been following these instructions:

[http://www.osdev.org/osfaq2/index.php/GCC%20Cross-Compiler](http://www.osdev.org/osfaq2/index.php/GCC%20Cross-Compiler)

I've gotten to the point of 
```
$  ./binutils-2.18/configure --target=$TARGET --prefix=$PREFIX --disable-nls
```and I get the error:
```
configure: error: cannot find sources (move-if-change) in ./binutils-2.18 or ..
```

Google hasn't been very helpful on this error - what am I doing wrong?

---

### Post by dmg on 2008-01-26
I had the same problem when trying to build the AVR toolchain.

For me the issue was due to binutils not downloading/extracting correctly so half of the files were missing.

After re-downloading everything worked.

---

