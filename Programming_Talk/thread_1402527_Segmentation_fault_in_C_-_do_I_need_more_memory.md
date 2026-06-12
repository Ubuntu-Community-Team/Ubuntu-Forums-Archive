---
title: "Segmentation fault in C - do I need more memory?"
date: 2010-02-09
forum: Programming Talk
---

### Post by crowhill on 2010-02-09
Hi there

I'm writing a little program on C (on my Ubuntu 9.10) to solve a set of partial differential equations. Among many other things, the program uses N arrays, each of length L. Now, when I compile the program I get a segmentation fault. However, when either I decrease N or L the segmentation fault disappears and the program runs perfectly fine.

My problem is that I need to make the arrays bigger and bigger in order to be able to study smaller and smaller distances between individual points of my computational grid.

How can I assign more memory to the compiler? 

I run the program both on a machine with 1 G of RAM and one with 4 G of RAM. Unfortunately, there's no difference.

Some help, hint or advice would be very, very much appreciated.

Thanks a lot,
cheers,

crowhill.

---

### Post by MadCow108 on 2010-02-09
My guess would be a stack overflow
Are your arrays declared like this?
```

double array[1000];

```

these things are allocated on stack and stack is very limited (~8mb)
you can see the stack size with ulimit -a and change it with ulimit -s

but generally use should heap memory for large structures, it has about the size of the available ram:
```

double * array = malloc(sizeof(double)*1000);
if (!array){
  // malloc failed! probably out of ram
}

```

note: the sizeof operator on this will give you the size of the pointer (4 or 8 ) and not size 1000 like on the stack array. So save the size seperate somehow.

If that does not help, use valgrind on the binary compiled with debugging information (-g) to locate the source of the problem. (It can also tell if it is a stack overflow or something else)

---

### Post by crowhill on 2010-02-09
Thanks a lot for your quick reply!

I'll give this a try ...

Cheers :)

---

### Post by Zugzwang on 2010-02-09
@OP: Do you really get a segmentation fault when **compiling** the program? If so, you probably found a bug in GCC. If you get it when **running** the program, ignore this post and continue with MadCow108's suggestions.

---

### Post by crowhill on 2010-02-09
> ```

double * array = malloc(sizeof(double)*1000);
if (!array){
  // malloc failed! probably out of ram
}

```

i changed all my definitions of arrays a1, a2, ... from

```
double a1[Npoints], a2[Npoints], ...;
```

to

```
double * a1=malloc(sizeof(double)*Npoints), * a2=malloc(sizeof(double)*Npoints), ...;
```

However, I now get an incredible amount of error messages.

Do I changed the array declaration in functions and function prototypes from

```
void function(double a1[Npoints], ...);
```

to

```
void function(double * a1=malloc(sizeof(double)*Npoints), ...);
```

When using the function, do I write

```
function(* a1, ...);
```

I'm very confused!

Thanks again,
cheers,

crowhill.

---

### Post by Zugzwang on 2010-02-09
> **crowhill said:**
> i changed all my definitions of arrays a1, a2, ... from

```
double a1[Npoints], a2[Npoints], ...;
```

to

```
double * a1=malloc(sizeof(double)*Npoints), * a2=malloc(sizeof(double)*Npoints), ...;
```

However, I now get an incredible amount of error messages.



That's because you made an assignment out of a declaration. In this case, you need to replace your "," by ";".


> **crowhill said:**
> 
Do I changed the array declaration in functions and function prototypes from

```
void function(double a1[Npoints], ...);
```

to

```
void function(double * a1=malloc(sizeof(double)*Npoints), ...);
```


No, rather change it to: "void function(double *a1)" - Omit the definition of "a1" and only declare it.

> **crowhill said:**
> 
When using the function, do I write

```
function(* a1, ...);
```

I'm very confused!


No, you write "function(a1)". An pointer to some data can be used in the same way as an array, but does not have some length information encoded.

BTW: Warning: If you change the content of your array in a function with prototype as modified as stated above, this change is global rather than local.

You might want to have a look at some book on C and/or C++. Watch out for a chapter on arrays and pointers. The type of your questions suggest that you are currently not very experienced with them, so you should have a look.

---

### Post by crowhill on 2010-02-09
Thanks a lot Zugzwang! I'll spend some time on this ...

Cheers,
crowhill.

---

### Post by crowhill on 2010-02-09
The following program is supposed give (POINTS-1)^2 as output. The program is much to complicated for such a simple operation. It's the way it is because I wanted to play around with pointers and the function malloc().

The program runs fine as long as POINTS is not too big.

When I change POINTS (the length of the arrays) by inserting an additional zero in 10001 (approximately equal to a multiplication by 10) I get a completely terrible answer even though when I run it through the Gnome Debugger gdb the program exits normally.

I tried to allocate more space to the stack by typing ulimit -s 10000 but that didn't make a difference.

Here is the program.

```
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
#define POINTS 10001

void function(int * declaration_in, int * declaration_out);

int main(void)
{
	int i;
	int * in = malloc(POINTS*sizeof(int)); 
	int * out = malloc(POINTS*sizeof(int));

	for(i=0; i<POINTS; i++)
	{
		in[i]=i;
	}

	function(in, out);

	printf("%d\n", out[POINTS-1]);

	return 0;
}

void function(int * definition_in, int * definition_out)
{
	int i;

	for(i=0; i<POINTS; i++)
	{
		definition_out[i]=definition_in[i]*i;
	}
}
```

Am I doing something wrong?

I also tried to use static variables but that didn't change anything either.

Thanks for taking a look,
cheers,
crowhill.

---

### Post by TheStatsMan on 2010-02-09
You need to use long rather than int in that case

---

### Post by crowhill on 2010-02-09
Thanks for the quick answer.

Even if I use long the generated number is still too big. However, if I change '*i' to '+1' the generated numbers are no problem. More importantly, this shows that I can use malloc() to create bigger arrays.

Thanks to all,
cheers,
crowhill.

---

### Post by MadCow108 on 2010-02-10
the problem is related to the type
int is normally only 31 bit (one sign bit) which is less than your big POINTS^2
it will fit into 64 bit integers which are long long (yes two longs) in C99
but you also have to change printf to the long long type:
printf("%lld\n", out[POINTS-1]);
compile with -Wall and it will warn you about wrong printf formats

you get twice as high values into your integers by using unsigned values.

for even bigger numbers you have to use an arbitrary precision library like gmp


also note that you have to explicitly free the memory allocated with malloc again with the free(void*) function.

you can see where leaked memory by using valgrind --leak-check=full on your binary.

---

