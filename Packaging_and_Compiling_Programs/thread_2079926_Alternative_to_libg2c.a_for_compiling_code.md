---
title: "Alternative to libg2c.a for compiling code"
date: 2012-11-02
forum: Packaging and Compiling Programs
---

### Post by joy_stat on 2012-11-02
I was given a source file to compile but it seems to call the libg2c.a file which is not available in Ubuntu 11.10 (64-bit which I am using. Here's the command:

gcc  -O2 -Wall -o emmax emmax.c /usr/lib/liblapack.a /usr/lib/atlas-base/atlas/libblas.a /usr/lib/atlas-base/libatlas.a /usr/lib/libg2c.a /usr/lib/atlas-base/libcblas.a /usr/lib/x86_64-linux-gnu/libm.a /usr/lib/x86_64-linux-gnu/libz.a

Is there a way to get around this?

 Thanks,

-Joey

---

