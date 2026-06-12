---
title: "Building i386 gcc from x86-64"
date: 2007-12-27
forum: Packaging and Compiling Programs
---

### Post by yang on 2007-12-27
When building gcc 4.2.0 on my Ubuntu 7.10 x86-64, I get:

```
configure: error: No support for this target/host combination.
```

I ran configure --target=i386-jos-elf (AFAIK, "jos" is meaningless - I can put any string in the middle). I can't really tell what was being built, but it seems like libstdc++. It would be nice to have C++ support (I imagine it must exist for i386+ELF), but if this turns out to be difficult, I'd also be interested in knowing how to disable building libstdc++. Thanks in advance for any guidance.

---

