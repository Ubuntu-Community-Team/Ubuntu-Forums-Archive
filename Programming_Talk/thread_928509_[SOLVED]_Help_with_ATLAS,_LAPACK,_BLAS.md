---
title: "[SOLVED] Help with ATLAS, LAPACK, BLAS"
date: 2008-09-24
forum: Programming Talk
---

### Post by ad_267 on 2008-09-24
I'm having a few problems with ATLAS in C and I'm sure I'm missing something obvious but all the documentation is a bit over my head. I've installed ATLAS partly following [this guide]("http://seehuhn.de/pages/linear"). I'm using the basic lapack test program from that page and it compiles and runs fine on my computer at home.

The problem is that I'm trying to install ATLAS in my home directory at my university. The computers there run Fedora Core 6. I have downloaded and compiled ATLAS and can link to the libraries and header files but there is no liblapack_atlas. Without this library I get this error:
```
testlapack.c:(.text+0xa5): undefined reference to `clapack_dgesv'
```

I have linked to libatlas, liblapack and libcblas but it seems that these libraries aren't enough. How do I get liblapack_atlas as it doesn't seem to be included with ATLAS? Or how else can I use lapack without needing liblapack_atlas?

---

### Post by ad_267 on 2008-09-25
Anyone have any experience with this? I've sort of got it working by copying my liblapack_atlas.a over but this isn't a very nice solution and I'd rather figure out what I'm doing wrong.

---

### Post by ad_267 on 2008-09-26
Well I sorted this out by extracting the rpm for atlas-devel which had all the static libraries and header files I needed but I'd still be interested in how to get these from compiling atlas if anyone knows.

---

