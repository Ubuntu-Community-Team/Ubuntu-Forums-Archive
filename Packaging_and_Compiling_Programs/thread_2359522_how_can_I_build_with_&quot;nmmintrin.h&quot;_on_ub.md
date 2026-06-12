---
title: "how can I build with &quot;nmmintrin.h&quot; on ubuntu 14.04?"
date: 2017-04-25
forum: Packaging and Compiling Programs
---

### Post by harderthan on 2017-04-25
I builded the project. It had fatal error.

nmmintrin.h: No such file or directory.

When I checked the project on Windows 7, It worked.

Is "nmmintrin.h" library of Windows?

I attached the log of project.

---

### Post by howefield on 2017-04-25
Thread moved to the "*Packaging and Compiling Programs*" forum.

---

### Post by steeldriver on 2017-04-25
AFAIK they are header files for the Intel SIMD intrinsics

[http://stackoverflow.com/questions/11228855/header-files-for-x86-simd-intrinsics](http://stackoverflow.com/questions/11228855/header-files-for-x86-simd-intrinsics)

If you are using gcc, they should be provided by the corresponding lib-dev package e.g.

```

$ dpkg -S /usr/lib/gcc/x86_64-linux-gnu/4.9/include/nmmintrin.h
libgcc-4.9-dev:amd64: /usr/lib/gcc/x86_64-linux-gnu/4.9/include/nmmintrin.h

```

It's hard to be more specific without information from you about the project, and the platform / architecture on which you are trying to build it.

---

