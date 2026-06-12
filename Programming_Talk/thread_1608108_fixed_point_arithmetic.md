---
title: "fixed point arithmetic"
date: 2010-10-28
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-28
Working with graphics libraries I find at several layers that they use fixed point 16.16 format calculations to transform coordinates for display.

Basically that is 32 bit integer arithmetic except that only the top 16 bits represent whole numbers and the lower 16 bits are the fractional part. That's no problem for addition but everytime you multiply or divide you have to do the calculation as a long (64 bit) to avoid overflow and then shift the result back by 16 bits.

I was wondering why they don't simply use floating point numbers, especially because doing the same calculations with float seems to be faster :shock: After all, performance **IS** often a limiting factor in the quality of computer graphics :confused:

---

### Post by Npl on 2010-10-28
display hardware and libraries typically dont deal with floats at many stages. adding hardware for floats would waste space and aint needed (unlike CPUs where its importnat for other ranges of problems).

also you dont have issues about precision and rounding if you use fixed point, unlike floats which are most precise around 0 and less precise the more you move away from it. For a limited range like screen coordinates its nearly always better to use fixed point.

this is only for the last stage in rendering though (rasterization), vertexes should generally be handled with floats.

---

### Post by saulgoode on 2010-10-28
> **worksofcraft said:**
> I was wondering why they don't simply use floating point numbers, especially because doing the same calculations with float seems to be faster :shock: 

I'd be interested in learning how you perceived this (because I am skeptical of what "seems" to be).

---

### Post by worksofcraft on 2010-10-28
> **saulgoode said:**
> I'd be interested in learning how you perceived this (because I am skeptical of what "seems" to be).

n.p. I looked at the kind of calculations it was doing mostly. Basically multplying a 2D displacement by a 2x2 transformation matrix and then adding a final displacement.

So I used random numbers to avoid any kind of optimization and ran this program for long, float and double:

[php]
#include <stdio.h>
#include <time.h>
#include <cstdlib> // rand/srand

//typedef float testnum;
typedef long testnum;

int main() {
	printf("size of testnum=%ld, RAND_MAX=%lu\n", sizeof(testnum), (unsigned long) RAND_MAX);
	testnum iF = 1.0;
	clock_t iStart = clock();
	srand(iStart);
	for (long i = 0; i < 20000000; ++i) {
		iF *= testnum(rand())/testnum(rand())+testnum(rand())/testnum(rand());
	}
	return !printf("time=%f seconds\n", float(clock()-iStart)/CLOCKS_PER_SEC);
}
[/php]

for "long" I get:
```


$> ./a.out
size of testnum=8, RAND_MAX=2147483647
time=1.900000 seconds

```

for float (and also double) I get:
```

$> ./a.out
size of testnum=4, RAND_MAX=2147483647
time=1.440000 seconds

```

... and that is without requiring the long arithmetic to shift by 16 bits on each multiply/divide while it IS requiring the floating point version to convert the random number to float each time... so it's really quite biased to favor integer computations. I might actually write the proper affine transforms in both flavors to get more accurate measure, but it wasn't what I expected at all :shock:

**After thought:**Floating point is done by a separate and dedicated floating point core and so perhaps it can run it's calculations  concurrently and in parallel to the main code ?! Definitely worth using floating point then ;)

---

### Post by worksofcraft on 2010-10-28
... btw thanks for that input Npl, I definitely see why they don't want to get cumulative errors as you move a pattern around on the screen... just for fun I'm making a graphics library for X11 and will make the data type configurable so that by applying floating point transformations on top of each other, I'm expecting to see the image disintegrate as errors accumulate :D

update: I just finished my affine transform code and apply 360000 cumulative 1 degree rotations to produce a resulting transformation  matrix. There is no discernable error as the determinant of the matrix is still 1.0000, but the cumulative angle error has moved it just past perfect full circle.

```

// 360000 matrix multiplications later:

xx=1.0000, xy=0.0000
yx=-0.0000, yy=1.0000
det=1.0000

xx=0.9998, xy=-0.0174
yx=0.0174, yy=0.9998
det=1.0000

```
... and that is probably because I expressed the angle as an integer scaled so that 180 degrees = 2^31.

edit: oops my bad... I had one too many iterations in the loop... no discernable error at all :shock:

---

### Post by worksofcraft on 2010-10-29
> **Npl said:**
> 
this is only for the last stage in rendering though (rasterization), vertexes should generally be handled with floats.

Yes I wondered about this. Size of float and size of int are both 4 bytes on my machine so I assumed I would get much better precision using appropriately scaled integers than using floats.

Floats would be wasting some of their bits on an exponent. Anyway I've put together the basis for 2D coordinate transformation library. Might even be quite an acceptable graphics package once it's ready ;) Meanwhile, I made the typedef separately configurable for the affine transform coefficients as opposed to vertex coordinates.

Then I applied a one degree rotation 360 times to a accurately scaled coordinate. The cumulative error was much worse with the integer than with the floating point vertexes :shock: Again not what I expected and I'm not quite sure why, or how representative that would be of typical graphics operations.... whatever. I'll attach my source code just in case anyone else wants to play with 2D transformations :P

---

### Post by saulgoode on 2010-10-29
Thanks for your reply and for your benchmarks. I repeated them on my Pentium IV and the results are more close (though the integer type is still slower).

In the past, the problem with floating point processing (as implemented by hardware) was not that it took longer, but that it interfered with the instruction pipelining optimization; potentially stalling the pipeline until the operation had finished. This is probably still true on some processors, but apparently not for your typical x86 architectures.

---

