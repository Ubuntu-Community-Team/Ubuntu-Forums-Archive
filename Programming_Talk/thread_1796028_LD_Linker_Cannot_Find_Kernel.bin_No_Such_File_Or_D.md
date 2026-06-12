---
title: "LD Linker: Cannot Find Kernel.bin: No Such File Or Directory"
date: 2011-07-03
forum: Programming Talk
---

### Post by smilinggoomba on 2011-07-03
I am trying to link 2 files together, from a tutorial that I got off the internet.  I use the command "ld -T link.ld kernel.bin ks.o kernel.o, to link ks.o to kernel.o as kernel.bin.  Yet I always get the following error: ld: cannot find kernel.bin: no such file or directory.  How do I get rid of this error?

---

### Post by slavik on 2011-07-03
doesn't sound legit ...

1. link to tutorial
2. what kind of code are you writing?

---

### Post by cgroza on 2011-07-03
Also, in what language are you writing? Assembly, C, C++?

---

### Post by smilinggoomba on 2011-07-03
Here is the tutorial:[http://www.osdever.net/tutorials/view/writing-a-simple-c-kernel]("http://www.osdever.net/tutorials/view/writing-a-simple-c-kernel")
I am programming in C.
The code is in the tutorial.

---

### Post by slavik on 2011-07-03
there's your problem:
> Updated September 13, 2002 by K.J.

find a more up to date guide. :)

---

