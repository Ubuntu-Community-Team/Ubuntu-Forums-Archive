---
title: "How to tell configure where to find a library, when all I know is an .so file?"
date: 2015-05-21
forum: Packaging and Compiling Programs
---

### Post by Allen McBride on 2015-05-21
**EDIT: nevermind, I get it now. You have to install the "-dev" version of all the libraries you want to use.**

Hi. I'm trying to compile Clayton Otey's sbsms-app (a.k.a. wxsbsms, wxsbsmsPlayer). It depends on libsbsms. Ubuntu (15.04) provides a package called libsbsms10, which I do have installed. But when I run ./configure in the source directory for sbsms-app, it says it "checking for SBSMS... no / Sorry, you need libsbsms."

When I run "ldconfig -p | grep sbsms", I get "libsbsms.so.10 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libsbsms.so.10". That's probably the info I need, but I'm not sure what to do with it.

I've tried "./configure --with-PACKAGE=libsbms10" and "./configure CPPFLAGS=-I/usr/lib/x86_64-linux-gnu/libsbsms.so.10 LDFLAGS=-L/usr/lib/x86_64-linux-gnu/libsbsms.so.10".

Neither works, but I'm not surprised because I'm just guessing. From what I've read, the argument to CPPFLAGS is supposed to be an "include" directory, and the argument to LDFLAGS is supposed to be a "lib" directory. But all I can find for libsbsms is this one .so file.

I'd welcome suggestions. Once I get this I expect I'll have a better understanding of how to link libraries.

---

