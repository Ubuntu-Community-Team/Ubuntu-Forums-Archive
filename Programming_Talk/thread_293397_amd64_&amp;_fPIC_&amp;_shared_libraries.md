---
title: "amd64 &amp; fPIC &amp; shared libraries"
date: 2006-11-05
forum: Programming Talk
---

### Post by alion on 2006-11-05
It's a fact, that on certain architectures (AMD64 among them), shared libraries must be PIC enabled.

But when I'm trying to link a library I get the following message:

libc.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC libc.o: could not read symbols: Bad value

So I already recompiled a bunch of the libraries my app is dependent of.
But I did that using source checkout and ./configure && make.

Is there a good-looking way to compile the whole runtime (libc + libstdc++,etc) with fPIC flag on Ubuntu?

---

### Post by nfm on 2007-04-28
I have the same issue, I can't compile gpac or swfdec because of it. Does this mean that I have to recompile ffmpeg when for example gpac links to libavcodec.a?

---

### Post by necrit on 2007-11-17
I receive this error as well....im trying VERY hard to force shared library compiles....yet its like the system doesnt have a way to force my newly created shared library into my header files search path..
ARGGG

---

