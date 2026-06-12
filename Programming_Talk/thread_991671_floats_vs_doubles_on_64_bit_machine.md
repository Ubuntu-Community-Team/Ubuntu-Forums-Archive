---
title: "floats vs doubles on 64 bit machine"
date: 2008-11-24
forum: Programming Talk
---

### Post by u-slayer on 2008-11-24
I was doing some experimentation in c++ to see how much slower processing using doubles would be on my machine. 

I had assumed doubles should be an order of magnitude slower to use. However when I coded up a quick test, using doubles actually made my code run faster. 

Does this mean that I should always use doubles when compiling for 64-bit machines or am I overlooking  something 

```
	//Float vs. Double speed test
	const int SIZE = (int)1e3;
	float Q[SIZE];
	float temp;
	
	cout << "Filling Q" << endl;
	for ( int x = 0; x < SIZE; x++)
		Q[x]=rand.f();
		
	cout << "Testing Q" << endl;
	
	//okay();
	
	for ( int x = 0; x < SIZE; x++)
	{
		for ( int y = 0; y < SIZE; y++)
		{
			for ( int z = 0; z < SIZE; z++)
			{
				temp=Q[x] * Q[y] * Q[z];
			}
		}
		
		if ( ! ( x % 100 ) )
			cout << x << endl;
	}
```

Note: rand.f() just returns a float from the random number generator I built. You can replace it with something similar if you want to test this code.

---

### Post by samjh on 2008-11-24
The fact that double-precision floating point numbers are 64 bits might have something to do with performance.

---

### Post by Npl on 2008-11-24
for x86 Processors, **a single multiplication** takes the same time wether its float or double. It has nothing to do with 64bit Processors, as floating point operations are a seperate unit - 386 Processors already dealt with 32,64 and 80bit floats while beeing 32bit Processors.

using floats can improve performance if:
*) you arent running on x86 processors
*) you use multiple operations (not through a loop) - your processors can theoretically calculate twice as many floats, but only if your code and the compiler allow for it
*) if memory(-bandwidth) is a bottleneck as floats use half the memory

and regarding your code, you should check if your compiler doesnt just optimize away the y,z loops.

---

### Post by stroyan on 2008-11-24
I am suspicious that your rand.f() function is producing values very
close to zero.  (That might happen because of a missing type declaration.)
Floating point operations on values very close to zero often require
software emulation.  The hardware can only perform math on normalized
numbers that have a fractional part between 1 and 2.  There is a
pretty good discussion of normalized and denormalized number representation
at [http://docs.hp.com/en/B3906-90005/ch02s02.html](http://docs.hp.com/en/B3906-90005/ch02s02.html) .

Here is a benchmark that shows the performance of math on numbers very
near zero.  Because doubles have a much larger range of exponent values
than floats they can represent smaller numbers in normalized format.
```

$ cat denorm_bench.c
#include <malloc.h>
#include <values.h>
#include <stdio.h>
#include <time.h>
#include <sys/types.h>
#include <sys/param.h>
#include <sys/time.h>
#include <errno.h>
#include <stdlib.h>
#include <unistd.h>

#define LOOPS 10

#define BENCH(function,message) \
{ \
	register int i; \
	struct timeval time1, time2; \
	struct timezone tz; \
	double elapsed_time; \
\
	gettimeofday(&time1, &tz); \
	for (i=0; i<LOOPS; i++) { \
		function; \
	} \
	gettimeofday(&time2, &tz); \
	elapsed_time = time2.tv_sec - time1.tv_sec \
		+ (time2.tv_usec - time1.tv_usec) / 1e6; \
	printf("%.1f %s\n", LOOPS / elapsed_time, message); \
}


int floats(float epsilon)
{
    int i;
    float *fp, sum = 1.0f;
    fp = (float *)malloc(1000000*sizeof(float));
    for (i=0; i<1000000; i++) fp[i] = epsilon;
    for (i=0; i<1000000; i++) sum = sum * fp[i] + epsilon;
    return (int) sum;
}

int doubles(double epsilon)
{
    int i;
    double *fp, sum = 1.0f;
    fp = (double *)malloc(1000000*sizeof(double));
    for (i=0; i<1000000; i++) fp[i] = epsilon;
    for (i=0; i<1000000; i++) sum = sum * fp[i] + epsilon;
    return (int) sum;
}

int main()
{
    int sum=0;
    BENCH(sum+=floats(2e-30), "million normal float ops per second")
    BENCH(sum+=floats(2e-40), "million denorm float ops per second")
    BENCH(sum+=doubles(2e-30), "million normal double ops per second")
    BENCH(sum+=doubles(2e-40), "million (not quite) denorm double ops per second")
    return sum;
}

$ cc -O2 -o denorm_bench denorm_bench.c
$ ./denorm_bench
131.4 million normal float ops per second
3.0 million denorm float ops per second
92.8 million normal double ops per second
92.7 million (not quite) denorm double ops per second
$ 

```

---

### Post by monkeyking on 2008-11-24
> **stroyan said:**
> I am suspicious that your rand.f() function is producing values very
close to zero.  (That might happen because of a missing type declaration.)
Floating point operations on values very close to zero often require
software emulation.  The hardware can only perform math on normalized
numbers that have a fractional part between 1 and 2.  There is a
pretty good discussion of normalized and denormalized number representation
at [http://docs.hp.com/en/B3906-90005/ch02s02.html](http://docs.hp.com/en/B3906-90005/ch02s02.html) .

Here is a benchmark that shows the performance of math on numbers very
near zero.  Because doubles have a much larger range of exponent values
than floats they can represent smaller numbers in normalized format.
```

$ cat denorm_bench.c
#include <malloc.h>
#include <values.h>
#include <stdio.h>
#include <time.h>
#include <sys/types.h>
#include <sys/param.h>
#include <sys/time.h>
#include <errno.h>
#include <stdlib.h>
#include <unistd.h>

#define LOOPS 10

#define BENCH(function,message) \
{ \
	register int i; \
	struct timeval time1, time2; \
	struct timezone tz; \
	double elapsed_time; \
\
	gettimeofday(&time1, &tz); \
	for (i=0; i<LOOPS; i++) { \
		function; \
	} \
	gettimeofday(&time2, &tz); \
	elapsed_time = time2.tv_sec - time1.tv_sec \
		+ (time2.tv_usec - time1.tv_usec) / 1e6; \
	printf("%.1f %s\n", LOOPS / elapsed_time, message); \
}


int floats(float epsilon)
{
    int i;
    float *fp, sum = 1.0f;
    fp = (float *)malloc(1000000*sizeof(float));
    for (i=0; i<1000000; i++) fp[i] = epsilon;
    for (i=0; i<1000000; i++) sum = sum * fp[i] + epsilon;
    return (int) sum;
}

int doubles(double epsilon)
{
    int i;
    double *fp, sum = 1.0f;
    fp = (double *)malloc(1000000*sizeof(double));
    for (i=0; i<1000000; i++) fp[i] = epsilon;
    for (i=0; i<1000000; i++) sum = sum * fp[i] + epsilon;
    return (int) sum;
}

int main()
{
    int sum=0;
    BENCH(sum+=floats(2e-30), "million normal float ops per second")
    BENCH(sum+=floats(2e-40), "million denorm float ops per second")
    BENCH(sum+=doubles(2e-30), "million normal double ops per second")
    BENCH(sum+=doubles(2e-40), "million (not quite) denorm double ops per second")
    return sum;
}

$ cc -O2 -o denorm_bench denorm_bench.c
$ ./denorm_bench
131.4 million normal float ops per second
3.0 million denorm float ops per second
92.8 million normal double ops per second
92.7 million (not quite) denorm double ops per second
$ 

```

Wauw, I didn't know this, I'm gonna look into this.

---

### Post by u-slayer on 2008-11-24
> **stroyan said:**
> I am suspicious that your rand.f() function is producing values very
close to zero.  (That might happen because of a missing type declaration.)
Floating point operations on values very close to zero often require
software emulation.  The hardware can only perform math on normalized
numbers that have a fractional part between 1 and 2.  There is a
pretty good discussion of normalized and denormalized number representation
at [http://docs.hp.com/en/B3906-90005/ch02s02.html](http://docs.hp.com/en/B3906-90005/ch02s02.html) .

I'm not sure I follow you. 

rand.f() produces a number between 0 and 1

Floats can represent numbers as small as 2 ^ -127 before rounding to zero. I don't understand why the hardware should have any trouble with this.

---

### Post by stroyan on 2008-11-24
Not seeing the implementation of rand.f or how it was declared
in the test program, I suspected that it actually produced some
or many denormalized float numbers.  That might happen from a
misguided function that produced an integer random value and only
interpreted it as a float value.  If a memory address contains
an integer value less than 8388607 it will actually result in a
denormalized number if interpreted as a float.  And operations
on denormalized float numbers are _much_ slower than operations
on the same numbers represented as normalized doubles.

---

### Post by rplantz on 2008-11-25
The problem is that C will convert the 32-bit float values to 64-bit, perform the computation, then convert it back. For example,
```

#include <stdio.h>
int main() 
{
  float a,b;
  double x,y;

  a = 1.2;
  b = a + 3.4;
  x = 5.6;
  y = x + 7.8;

  printf("b = %f and y = %lf\n", b, y);

  return 0;
}
```
compiled with
```

bob@bob-desktop:~/programming$ gcc -O0 -g -Wa,-adhls -fno-asynchronous-unwind-tables fp_inC.c > fp_inC.lst

```
shows that the assembly language code produced is (I've added some of my own comments to the assembly language listing.)
```

GAS LISTING /tmp/ccEsOixT.s 			page 1


   1              		.file	"fp_inC.c"
   9              	.Ltext0:
  10              		.section	.rodata
  11              	.LC3:
  12 0000 62203D20 		.string	"b = %f and y = %lf\n"
  12      25662061 
  12      6E642079 
  12      203D2025 
  12      6C660A00 
  13              		.text
  14              	.globl main
  16              	main:
  17              	.LFB2:
  18              		.file 1 "fp_inC.c"
   1:fp_inC.c      **** /* fp_inC.c */
   2:fp_inC.c      **** #include <stdio.h>
   3:fp_inC.c      **** int main() 
   4:fp_inC.c      **** {
  19              		.loc 1 4 0
  20 0000 55       		pushq	%rbp
  21              	.LCFI0:
  22 0001 4889E5   		movq	%rsp, %rbp
  23              	.LCFI1:
  24 0004 4883EC20 		subq	$32, %rsp
  25              	.LCFI2:
   5:fp_inC.c      ****   float a,b;
   6:fp_inC.c      ****   double x,y;
   7:fp_inC.c      **** 
   8:fp_inC.c      ****   a = 1.2;
  26              		.loc 1 8 0
  27 0008 B89A9999 		movl	$0x3f99999a, %eax
  27      3F
  28 000d 8945FC   		movl	%eax, -4(%rbp)
   9:fp_inC.c      ****   b = a + 1.2;
  29              		.loc 1 9 0
  30 0010 F30F104D 		movss	-4(%rbp), %xmm1       # load a
  30      FC
  31 0015 0F5AC9   		cvtps2pd	%xmm1, %xmm1  # convert float to double
  32 0018 F20F1005 		movsd	.LC1(%rip), %xmm0     # load 1.2
  32      00000000 
  33 0020 F20F58C1 		addsd	%xmm1, %xmm0          # do addition
  34 0024 660F14C0 		unpcklpd	%xmm0, %xmm0  # unpack
  35 0028 660F5AC0 		cvtpd2ps	%xmm0, %xmm0  # convert double to float
  36 002c F30F1145 		movss	%xmm0, -8(%rbp)       # store a
  36      F8
  10:fp_inC.c      ****   x = 3.4;
  37              		.loc 1 10 0
  38 0031 48B83333 		movabsq	$4614838538166547251, %rax
  38      33333333 
  38      0B40
  39 003b 488945F0 		movq	%rax, -16(%rbp)
  11:fp_inC.c      ****   y = x + 3.4;
  40              		.loc 1 11 0
  41 003f F20F104D 		movsd	-16(%rbp), %xmm1      # load x
  41      F0
  42 0044 F20F1005 		movsd	.LC2(%rip), %xmm0     # load 3.4
  42      00000000 
  43 004c F20F58C1 		addsd	%xmm1, %xmm0          # do addition
  44 0050 F20F1145 		movsd	%xmm0, -24(%rbp)      # store x
  44      E8
  12:fp_inC.c      **** 
  13:fp_inC.c      ****   printf("b = %f and y = %lf\n", b, y);
  45              		.loc 1 13 0
  46 0055 F30F1055 		movss	-8(%rbp), %xmm2
  46      F8
  47 005a 0F5AD2   		cvtps2pd	%xmm2, %xmm2
  48 005d F20F1045 		movsd	-24(%rbp), %xmm0
  48      E8
  49 0062 660F28C8 		movapd	%xmm0, %xmm1
  50 0066 660F28C2 		movapd	%xmm2, %xmm0
  51 006a BF000000 		movl	$.LC3, %edi
  51      00
  52 006f B8020000 		movl	$2, %eax
  52      00
  53 0074 E8000000 		call	printf
  53      00
  14:fp_inC.c      **** 
  15:fp_inC.c      ****   return 0;
  54              		.loc 1 15 0
  55 0079 B8000000 		movl	$0, %eax
  55      00
  16:fp_inC.c      **** }
  56              		.loc 1 16 0
  57 007e C9       		leave
  58 007f C3       		ret
  59              	.LFE2:
  61              		.section	.rodata
  62 0014 00000000 		.align 8
  63              	.LC1:
  64 0018 33333333 		.long	858993459
  65 001c 3333F33F 		.long	1072902963
  66              		.align 8
  67              	.LC2:
  68 0020 33333333 		.long	858993459
  69 0024 33330B40 		.long	1074475827
 106              	.Letext0:
DEFINED SYMBOLS
                            *ABS*:0000000000000000 fp_inC.c
     /tmp/ccEsOixT.s:16     .text:0000000000000000 main

UNDEFINED SYMBOLS
printf

```

The float addition requires seven instructions (lines 30 - 36) and the double only four (lines 41 - 44). Note that the float constant value of 1.2 has been stored as a double (lines 64 - 65). This would be worse if both values were floats because both floats would need to be converted to doubles.

---

### Post by Npl on 2008-11-25
> **rplantz said:**
> The problem is that C will convert the 32-bit float values to 64-bit, perform the computation, then convert it back. For example...
...This would be worse if both values were floats because both floats would need to be converted to doubles.
or better if you would actually add floats in your C-Code instead of doubles.
```

#include <stdio.h>
int main() 
{
  float a,b;
  double x,y;

  a = 1.2f;
  b = a + 3.4f;
  x = 5.6;
  y = x + 7.8;

  printf("b = %f and y = %lf\n", b, y);

  return 0;
}
```

---

