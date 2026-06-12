---
title: "Distributed build for kernel? is it possible at all"
date: 2011-04-17
forum: Packaging and Compiling Programs
---

### Post by ggankhuy on 2011-04-17
Ya all know that the linux kernel takes hours to complete. I wonder if there is a distributed build available to fasten up the process? That is divide the build task within several computers connected together by network. Anyone has information on this? Thanks!

---

### Post by marshmallow1304 on 2011-04-25
[distcc]("https://code.google.com/p/distcc/") is what you want:

I'd also suggest you have a look at this Gentoo Wiki Archives [article]("http://www.gentoo-wiki.info/HOWTO_Compile_Kernel_With_Distcc_and_CCache").  It's old and Gentoo specific, but it's a good starting point along with the distcc documentation.

---

