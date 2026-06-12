---
title: "ignore OpenMP in C++ program on machine without it"
date: 2009-08-20
forum: Programming Talk
---

### Post by flylehe on 2009-08-20
Hi, 

I have a C++ program using OpenMP, which will run on several machines. Some of them have OpenMP installed and others don't. GCC below version 4.2.x doesn't support OpenMP. 

How could I make the Makefile of my program know if a machine has no OpenMP and ask g++ to ignore in my code those "#include omp.h", OpenMP directives (like "#pragma omp parallel ...") and/or library functions (like "tid = omp_get_thread_num();") instead of failing compilation? So that I can run my program without multi-threading on those machines without OpenMP?

Thanks and regards!

---

