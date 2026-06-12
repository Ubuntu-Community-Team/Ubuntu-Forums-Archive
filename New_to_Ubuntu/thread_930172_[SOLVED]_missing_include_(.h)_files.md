---
title: "[SOLVED] missing include (*.h) files"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by dreesthomas on 2008-09-25
Running xubuntu 6.02 (small memory); downloaded gcc from repository; seem to have everything but /include.  Tried a couple of versions of gcc, no luck.  Didn't have that problem a while back with 6.10.  Any obvious answers?

Can't even compile hello.c without stdio.h!

---

### Post by sam1948 on 2008-09-25
hi dreesthomas
please upload the code files and write down the command line u use for compiling it and i'll try to help

---

### Post by cmay on 2008-09-25
you need to install the build essential packages.

[PHP] sudo apt-get install build-essential[/PHP]

good luck
ehhh reading the post again it could be someting broken if you already had the gcc compiler working before. in that case ignore this suggestion. reinstalling gcc could help

---

### Post by dreesthomas on 2008-10-06
[QUOTE=cmay;5856280]you need to install the build essential packages.

[PHP] sudo apt-get install build-essential[/PHP]

Thanks - that was the answer (did it with synaptic pkg mgr, but same result)

David

---

