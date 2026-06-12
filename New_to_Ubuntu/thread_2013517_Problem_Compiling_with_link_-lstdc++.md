---
title: "Problem Compiling with link -lstdc++"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by juaneco2710 on 2012-07-01
Hello,

I'm new using Linux (Ubuntu 12.04 LTS, 64-bit). I am trying to learn how to create binary files for a program called Tecplot.

I've been trying to compile the example file simtest.f90, using this:

[FONT=Courier New]$ gfortran -fcray-pointer -lstdc++ simtest.f90 tecio64.a
[/FONT]
When I do this, I get a huge list of errors like this:

[FONT=Courier New]tecio.a(tecxxx.o):(.gnu.linkonce.d.DW.ref.__gxx_personality_v0[DW.ref.__gxx_personality_v0]+0x0): undefined reference to `__gxx_personality_v0'
tecio.a(TranslatedString.o):(.gnu.linkonce.d._ZTIN7tecplot7strutil16TranslatedStringE[typeinfo for tecplot::strutil::TranslatedString]+0x0): undefined reference to `vtable for __cxxabiv1::__class_type_info'[/FONT]

I've been reading several forums, and it looks like this is the kind of erro you get when you don't link the libstdc++ library (in fact, if I remove the link -lstdc++ I get the exact same error).

If anyone can help me, I would appreciate it.

---

