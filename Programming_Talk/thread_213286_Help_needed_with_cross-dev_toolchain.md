---
title: "Help needed with cross-dev toolchain"
date: 2006-07-11
forum: Programming Talk
---

### Post by datajon on 2006-07-11
I'm a complete newbie but I'm trying to make a cross-dev. toolchain. When I try to configure the binutils-package for my target (i386), I get this:  
```
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i386-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for i686-pc-linux-gnu-ar... no
checking for ar... ar
checking for i686-pc-linux-gnu-as... no
checking for as... as
checking for i686-pc-linux-gnu-dlltool... no
checking for dlltool... dlltool
checking for i686-pc-linux-gnu-ld... no
checking for ld... ld
checking for i686-pc-linux-gnu-nm... no
checking for nm... nm
checking for i686-pc-linux-gnu-ranlib... no
checking for ranlib... ranlib
checking for i686-pc-linux-gnu-windres... no
checking for windres... windres
checking for i686-pc-linux-gnu-objcopy... no
checking for objcopy... objcopy
checking for i686-pc-linux-gnu-objdump... no
checking for objdump... objdump
checking for i386-linux-ar... no
checking for i386-linux-as... no
checking for i386-linux-dlltool... no
checking for i386-linux-ld... no
checking for i386-linux-nm... no
checking for i386-linux-ranlib... no
checking for i386-linux-windres... no
checking whether to enable maintainer-specific portions of Makefiles... no
updating cache ./config.cache
creating ./config.status
creating Makefile

```
It seems like I'm missing something... :-k 

Can somebody please help me?

---

### Post by toojays on 2006-07-11
There's no error message there. What do you think should be different?

---

### Post by datajon on 2006-07-11
> **toojays said:**
> There's no error message there. What do you think should be different?
I just thought I was missing the i386-linux-version of ar, as, dlltool and etc.

---

### Post by toojays on 2006-07-11
Well configure didn't find them, but if it needed them it would have complained.

---

### Post by datajon on 2006-07-12
Ok thanks! Another question: How do I compile with another version of gcc? (instead of the default 4.0.3 version).

---

### Post by mlind on 2006-07-12
> **datajon said:**
> Ok thanks! Another question: How do I compile with another version of gcc? (instead of the default 4.0.3 version).

export CC

for 3.2 compilance, export CC=gcc32

---

