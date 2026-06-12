---
title: "Compiling wih no debug symbol (no -g)"
date: 2007-10-17
forum: Packaging and Compiling Programs
---

### Post by nfm on 2007-10-17
I decided to compile all of my additional programs without debug symbols, or without -g flag. What is the cleanest way to approach this? I tried the following:

1. Edit Makefile(s), this works the best, only when a source program has 1 makefile. But there are programs such as yasm, gcc or avidemux that have many makefiles and require a lot of editing and searching for -g.
2. After I finish "make install", I go into usr/local/bin and /usr/local/lib and do "strip -s *" to all files.

I tried setting CFLAGS to -O2 only, but many programs are clever and do CFLAGS += -g :(. Passing "disable-debug" to ./configure gets always ignored for me. Does something like "/etc/make.conf" exists? I think I've seen something like that in Gentoo. The reason for this is that I don't want debug symbols in any of the programs that I compile.

---

### Post by dwhitney67 on 2007-10-18
I'm not aware that CFLAGS=-g is enabled by default.  Generally one has to set that themselves.  If you are still unconvinced, try inserting an "unset CFLAGS" statement in your ~/.bashrc file so that it is unset everytime you log in.

---

### Post by nfm on 2007-10-18
Hi dwhitney67,
CFLAGS=-g is not enabled by default, unless you change it. All of the programs that I try to compile set the -g option after running ./configure. I will try "unset CFLAGS". Looks I'll have to continue using "strip -s" on ELF files and "strip --strip-debug" on the libraries.

---

### Post by dwhitney67 on 2007-10-18
You could very well be correct.  I do remember having to run strip on the libraries/binaries I built after completing 95% of CLFS (Cross-Compiled Linux From Scratch).

For CLFS, I run a statement similar to:

```
/tools/bin/find /{,usr/}{bin,lib,sbin} -type f -exec /tools/bin/strip --strip-debug '{}' ';'
```

---

