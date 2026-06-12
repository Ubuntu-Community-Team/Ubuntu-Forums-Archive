---
title: "Linking in an architecture independent way: libarchive"
date: 2015-08-01
forum: Packaging and Compiling Programs
---

### Post by jonathon-love on 2015-08-01
Hi,

I'm trying to link my project against libarchive.so

I have installed the libarchive and libarchive-dev packages

I can link against it by passing the following as build arguments:

-L/usr/lib/x86_64_gnu_linux -larchive

However, this won't work on a 32-bit machine. I thought that perhaps there would be a platform independent symlink that links to the appropriate platform file, but this doesn't appear to be the case.

What's the correct way to link against this library, so that it will build on both architectures?

with thanks

Jonathon

---

### Post by steeldriver on 2015-08-01
Hello and welcome to the forums

Did you mean to type /usr/lib/**x86_64-linux-gnu** (which seems to be the standard location for libarchive.so)? 

If so, have you tried omitting the search path altogether i.e just using [FONT=courier new]-larchive[/FONT]? the compiler's built-in search path should include /usr/lib/x86_64-linux-gnu (and /usr/lib/i386-linux-gnu/ when run with the -m32 flag)

---

### Post by jonathon-love on 2015-08-01
ah, yup! thanks. kinda obvious in hindsight :)

---

