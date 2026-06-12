---
title: "Needed Pakcakges to Compile"
date: 2007-06-24
forum: Packaging and Compiling Programs
---

### Post by EaStErDoM on 2007-06-24
Hi!

I switched to Ubuntu from Mandriva and try to compile a CLFS on a Feisty System now.

GCC is installed but it seems something is missing:

```
lfs@anexia-dev:/mnt/lfs/sources/binutils-build$ echo 'int main() {}' | gcc -x c -
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
```

Do i need additional packages? Or what is causing that problem?

---

### Post by EaStErDoM on 2007-06-24
The Package i needed was build-essential.

---

