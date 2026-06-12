---
title: "binutils build-depends on gcc, could be c-compiler?"
date: 2005-12-28
forum: Packaging and Compiling Programs
---

### Post by Antonio Martinez on 2005-12-28
I downloaded the binutils source package using apt-get source binutils, and was surprised to see that apt installed gcc-4.0 /even though/ I had gcc-3.4 installed.  The existing build dependency forces gcc, which forces gcc-4.0.

Could c-compiler be used instead of gcc as the build dependency?  Libtool, say, depends on either gcc or c-compiler.  Should I submit a bug report for this issue?

Thanks in advance,

--Antonio

---

