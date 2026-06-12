---
title: "restricted pointers in c++"
date: 2008-02-26
forum: Programming Talk
---

### Post by carl.alv on 2008-02-26
Hi all. I would like to know If any of you has user restricted pointers with gcc-4.2 or g++-4.2 and has been able to really improve the efficiency of the code by overcoming pointer aliasing at compilation. I am asking because I have tried to use __restrict__ with g++, but it seems that the instruction is just ignored.

Thanks in advance for any help!

---

### Post by stroyan on 2008-02-26
I don't see any effect from __restrict__ with gcc-4.2.
With this simple function I need gcc-4.3 and -O2 -funroll-loops to see an effect.
I can get a similar effect with gcc-4.2 and -fargument-noalias.
But that option is a very blunt instrument that promises restrict for all parameters in a file.
```
#ifdef USE_RESTRICT
#define RESTRICT __restrict__
#else
#define RESTRICT
#endif

void vecmult(int n, float * RESTRICT a, float * RESTRICT b, float * RESTRICT c)
{
	int i;
	for (i=0; i<n; i++) {
		a[i] = b[i] * c[i];
	}
}
```

---

### Post by carl.alv on 2008-02-27
Thanks stroyan, I used g++-4.2 with -O3 option and the time of execution of the vector multiplication was reduced in 40-50%!!!

---

### Post by carl.alv on 2008-02-27
Well, I have played a little more with the thing, and now it seems that the difference in time has nothing to do with restricted, if I run the process several times the time varies, but it seems to keep ignoring the __restrict__ order. :(

---

