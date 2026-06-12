---
title: "Compiler Error: undefined reference to `_install_allegro_version_check'"
date: 2009-08-31
forum: Packaging and Compiling Programs
---

### Post by pi.theta on 2009-08-31
When compiling using g++ and the allegro library i get the following errors. I understand that some file has to be linked but can't identity which on and how to. Please guide me.

```
theta@boolean:~/c/simchamp$ g++ test.cpp -o test.o
/tmp/ccOO7riS.o: In function `main':
test.cpp:(.text+0x8e): undefined reference to `_install_allegro_version_check'
test.cpp:(.text+0xcf): undefined reference to `set_gfx_mode'
test.cpp:(.text+0x104): undefined reference to `set_gfx_mode'
test.cpp:(.text+0x139): undefined reference to `set_gfx_mode'
test.cpp:(.text+0x141): undefined reference to `allegro_error'
test.cpp:(.text+0x14d): undefined reference to `allegro_message'
test.cpp:(.text+0x172): undefined reference to `makecol'
test.cpp:(.text+0x178): undefined reference to `font'
test.cpp:(.text+0x17e): undefined reference to `screen'
test.cpp:(.text+0x1ae): undefined reference to `textprintf_ex'
collect2: ld returned 1 exit status
```

Thanks in advance for any help!

---

### Post by Bachstelze on 2009-09-03
Try:

```
g++ test.cpp -lalleg -o test.o
```

---

### Post by dnight on 2010-09-17
Using just "-lalleg" was not enough for me because it asked for more libs later, so I used this and it was fine:

g++ test.cpp `allegro-config --libs` -o test

---

