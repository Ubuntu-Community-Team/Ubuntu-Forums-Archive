---
title: "will ATI stream (or another GPGPU library) improve linear algebra operations?"
date: 2009-12-26
forum: Programming Talk
---

### Post by dracule on 2009-12-26
Hello all, 

I have a program that I want to make faster. I have a ATI 4890 and so I thought that maybe ATI's stream package could help.

Basically, all of my program is a series of matrix multiplications and modifications and other linear algebra stuff.

I was wondering if anyone hear knew anything about GPGPU computing and if it would help in this situation. I looked on ATI's site and it gave no indication that it had any libraries or anything. Do any of you know of a library for GPGPU computing that would help out in this instance?

---

### Post by trparacyte on 2009-12-26
As long as you can highly parallelize your workload, ATI Stream and other GPGPU solutions should do wonders to the performance =] For example, video transcoding, one of the most parallel computing jobs, can be improved up to 18x through GPGPU.

---

