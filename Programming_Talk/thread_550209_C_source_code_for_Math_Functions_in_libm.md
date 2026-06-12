---
title: "C source code for Math Functions in libm"
date: 2007-09-13
forum: Programming Talk
---

### Post by marzshadow on 2007-09-13
Help.
I need to do instruction cycle counting for a kalman filter  algorithm in double precision floating point.
I can't find the actual source codes for the math functions.

As we will be targeting other machines as well, I need to do software emulations as well.

Where do I find the source codes for GCC math functions,
Sin, Cos, Pow, Atan, and such?

Also, what GCC command option produces listing files?

Thanks!
Mark L. Martin

---

### Post by CptPicard on 2007-09-13
> **marzshadow said:**
> 
Where do I find the source codes for GCC math functions,
Sin, Cos, Pow, Atan, and such?


In the standard library source. 

```

apt-get source libc6

```

As for listing files... care to elaborate a bit more what you're after, I didn't quite understand?

---

### Post by marzshadow on 2007-09-13
listing files..
a program I worked in 2002 we would compile with a make file and we would get compiler output (.lst) files showing all the errors and line numbers where the errors were.

Also, we would get interleaved assembly and C source (with the C lines commented out).

I'm not finding these options in the current gcc command line list.

Thanks for helping.
--mark

---

### Post by marzshadow on 2007-09-13
thanks for the apt-get suggestion.
That worked.
I found the source files you pointed me to.
Those are all either stubs, or wrappers to the ieee_754 libraries.

Where do I get those source codes?

Example:
#ifdef _IEEE_LIBM
	return  __ieee754_pow(x,y);
#else
	double z;
	z=__ieee754_pow(x,y);
	if(_LIB_VERSION == _IEEE_|| __isnan(y)) return z;
	if(__isnan(x)) {
	    if(y==0.0)
	        return __kernel_standard(x,y,42); /* pow(NaN,0.0) */
	    else
		return z;

It seems all of the functions are calling a deeper function.

--mark

---

### Post by Awalton on 2007-09-13
Hrmp. Sounds like an interesting class.

Anyways, the command line you're looking for is 
gcc -Wa,-ahls source_file.c > source_file.lst

You might also want to play with just calling the assembler by itself (**as** is the assembler command).
edit:
-ahls is just what I've always used, you can call whatever you want to it, here's the man file for the assembler commands so you can make it however you need to for your class:
[http://ccrma.stanford.edu/planetccrma/man/man1/as.1.html](http://ccrma.stanford.edu/planetccrma/man/man1/as.1.html)

---

