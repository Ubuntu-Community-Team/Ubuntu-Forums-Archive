---
title: "Code error in terminal"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Benbow on 2008-04-27
I have the following error -

./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

any idea what "libstdc++.so.5:" is?

Usung Hardy.

---

### Post by FredB on 2008-04-27
LibC - the main library of your system. RealPlayer wants a version that doesn't exist.

Try to find it using Synaptic.

---

### Post by Benbow on 2008-04-27
Thanks, I have found plenty of libstdc++ but none with .so.5: on the end. Found a libstdc++5 though.

---

