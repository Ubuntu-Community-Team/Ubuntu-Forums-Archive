---
title: "gcc -mfpmath=both performance"
date: 2010-05-08
forum: Programming Talk
---

### Post by jero3n on 2010-05-08
I compile some math-expensive code with gcc 4.4.3 using

```
gcc -std=c99 -lm -O3 -ffast-math -march=native **-mfpmath=sse** *.c
```
and
```
gcc -std=c99 -lm -O3 -ffast-math -march=native **-mfpmath=both** *.c
```

According to gcc docs for -mfpmath=both:
> Attempt to utilize both instruction sets at once. This effectively double the amount of available registers and on chips with separate execution units for 387 and SSE the execution resources too. Use this option with care, as it is still experimental, because the GCC register allocator does not model separate functional units well resulting in instable performance.

OK, so I did a test, compiling the same code in the following processors and running in single core with the following results (in seconds):
```
[SIZE="4"][FONT="Courier New"]mfpmath=                          sse   both  Improvement
1.Pentium 4 @3.4Ghz               100'' 23''    77%*
2.Pentium 4 @2.53Ghz              33''  28''     5%
3.Intel Core 2 6400 @2.13GHz      26''  19''    37%
4.Xeon E5520 @2.27                18''  17''     6%
5.Athlon 64 X2 4600+ @2.6GHz(OC)  33''  12''*   63%
6.Intel Core 2 T8300 @2.4GHz      41''  15''    66%
[/FONT][/SIZE]
```
Well, indeed it seems that -mfpmath=both results in unpredictable performance, but these results are a bit comfusing to my unexperienced eye: 1) The best performance is given by this old Athlon, beating even this i7 based Xeon and 2) mfpmath=both at 1 results in 77% faster performance!

Does this mean that in future versions of gcc, the register allocator will do better job at 2,3 & 4? Or 1,5 & 6 have separate fp units, so they can utilize so much better?

I want to buy a dozen of processors for a cluster for math code, and since I dont know much for CPUs, my decision of what CPUs to buy depends in such tests. Any suggestions?

---

### Post by TheStatsMan on 2010-05-08
If you are buying a cluster, I assume you would paralyse your code. So shouldn't you do a test that allows for more that one core? You might want to also look into buying a Telsla cluster depending on what type of math you are doing. I know people who have made massive gains on there work using them.

---

### Post by jero3n on 2010-05-08
> **TheStatsMan said:**
> If you are buying a cluster, I assume you would paralyse your code. So shouldn't you do a test that allows for more that one core? You might want to also look into buying a Telsla cluster depending on what type of math you are doing. I know people who have made massive gains on there work using them.

Yeap, you are right, but in this case I don't test parallelization. I assume that since I can parallelize the data (MIMD), the total runtime would be something about (time per core) X (total cores).

I've been thinking about NVidia Cuda, but I don't know if it worths the time to study CUDA C and rewrite my functions to vectorized form. I have no experience. Moreover I *think* that because I have a very large amount of data (some gigabytes), the time the data needs to travel between GPU's and CPU's memory would be a huge bottleneck. I dont know.. :confused:

---

### Post by TheStatsMan on 2010-05-08
> **jero3n said:**
> Yeap, you are right, but in this case I don't test parallelization. I assume that since I can parallelize the data (MIMD), the total runtime would be something about (time per core) X (total cores).

I've been thinking about NVidia Cuda, but I don't know if it worths the time to study CUDA C and rewrite my functions to vectorized form. I have no experience. Moreover I *think* that because I have a very large amount of data (some gigabytes), the time the data needs to travel between GPU's and CPU's memory would be a huge bottleneck. I dont know.. :confused:

 It is probably worth asking on the NVidia CUDA forums. If you give them some details on your problem they may be able to give some guidance. A guy I know was getting a 30 times speed up using CUDA. He did say that GPU programming was very difficult though.

---

