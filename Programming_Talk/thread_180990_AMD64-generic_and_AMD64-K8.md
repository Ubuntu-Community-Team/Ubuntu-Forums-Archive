---
title: "AMD64-generic and AMD64-K8"
date: 2006-05-23
forum: Programming Talk
---

### Post by evilgold on 2006-05-23
Hi,

I was just wondering because i know there is a K8 kernel and a generic one, what the major differance is between the two? Isnt k8 the orignial AMD64 processor, with EM64T being intels clone later on. 

I'd like to know what amd64 processor wont run the k8 kernel if thats the case, and also i'd like to know what kind of optimizations the k8 has the the generic doesnt, and if its worth recompiling some packages for k8, like it is from going to i386 to i686.

---

### Post by rplantz on 2006-05-23
I have not compiled the kernels, but man gcc provides some hints about the differences between "generic" and "k8."

The -m64 option "... sets int to 32 bits and long and pointer to 64 bits and generates code for AMD&#8217;s x86-64 architecture."

The -mtune=k8 option provides "AMD K8 core based CPUs with x86-6 instruction set support. (This supersets MMX, SSE, SSE2, 3dNOW!, enhanced 3dNOW! and 64-bit instruction set extensions.)"

Both work on my Athlon 64 3200+. I run the k8 kernel, but I haven't done any meaningful comparisons.

---

