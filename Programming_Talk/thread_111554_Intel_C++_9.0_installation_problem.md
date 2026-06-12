---
title: "Intel C++ 9.0 installation problem"
date: 2006-01-02
forum: Programming Talk
---

### Post by koegli on 2006-01-02
I installed the Intel C++ 9.0 Compiler on Ubuntu Breezy 5.10 (gcc 4.0 installed)

The problem I'm facing is that compilation fails because icc cannot find the g++ toolchain. I have no clue how to tell the compiler where and how to find the g++ toolchain, because in the terminal environment all the tools are available in the PATH.

Has anyone faced a similar problem?
Has anyone gotten to run ICC with gcc 4.0???

Thanks a lot,

NIC

---

### Post by coredump on 2006-01-02
If you type:

```
which gcc
```

it'll tell you where on your path the 'gcc' command is found.  You can do the same thing, of course, for any command, like 'ls' or 'mount'.

---

