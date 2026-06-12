---
title: "how to compile statically?"
date: 2006-07-17
forum: Packaging and Compiling Programs
---

### Post by loell on 2006-07-17
hi, how do i statically compile applications?
can someone point me to the right direction

thanks :)

---

### Post by gborzi on 2006-07-17
> **loell said:**
> hi, how do i statically compile applications?
can someone point me to the right direction

thanks :)

I think you mean statically *link* applications. Use the -static linker option. From gcc man page
> **-static**
           On systems that support dynamic linking, this prevents linking with
           the shared libraries.  On other systems, this option has no effect.

you can be also interested in this other option
> **-static-libgcc**
           On systems that provide libgcc as a shared library, these options
           force the use of either the shared or static version respectively.
           If no shared version of libgcc was built when the compiler was con&#8208;
           figured, these options have no effect.

---

### Post by loell on 2006-07-17
my bad, i don't know the right term :)

so basically what does this command do?

./configure --enable-static


ie, if i have a downloaded source code, and i would like a static binary <-- (if its the right term) what should i do?

---

### Post by gborzi on 2006-07-17
> **loell said:**
> my bad, i don't know the right term :)

so basically what does this command do?

./configure --enable-static

I think this depends on how the configure was made. Try ./configure --help for a description. Generally the linker option are given by the LDFLAGS variable, so you can try
> LDFLAGS="-static" ./configure

> **loell said:**
> 
ie, if i have a downloaded source code, and i would like a static binary <-- (if its the right term) what should i do?
Perhaps statically linked executable is a better (but longer) term. However "static binary" is clear enough.

---

