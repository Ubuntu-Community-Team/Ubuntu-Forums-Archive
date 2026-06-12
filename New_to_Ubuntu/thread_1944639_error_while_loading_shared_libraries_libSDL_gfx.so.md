---
title: "error while loading shared libraries: libSDL_gfx.so.4"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by Kerkyros on 2012-03-21
As in the title, I try to run my own program using SDL, which I wrote on a 32 bit computer. However now, on a 64 bit system ./nameoftheprogram gives ```
error while loading shared libraries: libSDL_gfx.so.4: cannot open shared object file: No such file or directory
```
I have no idea how to repair this to be able to run the program compiled, because that file libSDL_gfx.so.4 exists in the /usr/lib folder and is pointing to libSDL_gfx.so.13.5.2
Any suggestions?

---

### Post by yeats on 2012-03-21
Try installing the 32-bit libraries:

```
sudo apt-get install ia32-libs
```

---

