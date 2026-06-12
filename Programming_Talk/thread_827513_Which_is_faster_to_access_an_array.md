---
title: "Which is faster to access an array?"
date: 2008-06-12
forum: Programming Talk
---

### Post by JupiterV2 on 2008-06-12
I tried doing a little test but at 10,000 iterations there seems to be absolutely no difference:

**version 1 (standard array access):**
[PHP]#include <stdio.h>
#include <time.h>

int main()
{
	time_t t_start = 0, t_end = 0;
	
	int i, x[10000];
	
	t_start = time( NULL );
	for(i = 0; i < 10000; i++) x[i] = i;
	t_end = time( NULL );
	
	printf("It took %d seconds to use x[]\n", (t_end - t_start));
}[/PHP]
```
It took 0 seconds to use x[]

real	0m0.001s
user	0m0.000s
sys	0m0.000s

```

**version 2 (pointer arithmetic)**
[PHP]#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
	time_t t_start = 0, t_end = 0;
	
	int i, *y = NULL;
	
	y = calloc(10000, sizeof(int));
	
	t_start = time( NULL );
	for(i = 0; i < 10000; i++) { *(y++) = i; }
	t_end = time( NULL );
	
	printf("It took %d seconds to use pointer arithmetic\n", (t_end - t_start));
}[/PHP]
```
It took 0 seconds to use pointer arithmetic

real	0m0.001s
user	0m0.000s
sys	0m0.000s

```

Is there any advantage to using pointer arithmetic for this particular use?

---

### Post by loell on 2008-06-12
ever tried a very very large array?

---

### Post by Jessehk on 2008-06-12
Array notation is syntactic sugar for pointer arithmetic. I'm reasonably sure they compile to the same thing.

---

### Post by Yuki_Nagato on 2008-06-12
> **loell said:**
> ever tried a very very large array?

Yes, you are using a relatively simple algorithm with simple linear notation.  You will need something up in the billions to notice any difference.

Now if you were testing something with more calculations, such as sorting methods, this would be different, and your sample size would be fine.

---

### Post by CptPicard on 2008-06-12
The only difference between what they compile into would be that the latter one gets to use increments of y while the other one does additions of y + i.

I fail to see how the difference would really be meaningful in any way... this seems like a case of speed-kiddyism :)

---

### Post by slavik on 2008-06-12
> **CptPicard said:**
> The only difference between what they compile into would be that the latter one gets to use increments of y while the other one does additions of y + i.

I fail to see how the difference would really be meaningful in any way... this seems like a case of speed-kiddyism :)
actually, from what I've seen, gcc puts in x++ as x=x+1 ...

also, think about multidimentional arrays. if you can precalculate all the sizes to jump rows, you do a single addition, whereas array notation might make the compiler encode multiplications ...

in any case, wherever you have something where you can tell the size ahead of time, the compiler can hard code it. (ie: unroll loops)

---

### Post by Lster on 2008-06-13
I made a test that filled 10^8 elements with there offset (0, 1, 2, ... 10^8-1). Test one used pointer arithmetic; test two used array elements. Both tests were compiled with O3 optimization and the values used during this were longs (I'm on a 64bit processor).

I took five results and averaged them to give scores of:

Pointer arithmetic (test one): 0.101.
Array elements (test two): 0.1106.

Pointer arithmetic's around 9% faster, if it wasn't just a fluke! 9% definitely isn't to be sneered at in some situations so I think this question is more important than it at first appears.

PS: I forgot to mention, they also don't compile to the same binary.

---

### Post by slavik on 2008-06-13
> **Lster said:**
> I made a test that filled 10^8 elements with there offset (0, 1, 2, ... 10^8-1). Test one used pointer arithmetic; test two used array elements. Both tests were compiled with O3 optimization and the values used during this were longs (I'm on a 64bit processor).

I took five results and averaged them to give scores of:

Pointer arithmetic (test one): 0.101.
Array elements (test two): 0.1106.

Pointer arithmetic's around 9% faster, if it wasn't just a fluke! 9% definitely isn't to be sneered at in some situations so I think this question is more important than it at first appears.

PS: I forgot to mention, they also don't compile to the same binary.

I find it interesting that the binaries were different, could you compile them to asm (-S flag to gcc)?

Also, I think it would be better to run the iteration at least 10000 times, since in this particular example, the difference of 0.01 seconds can be attributed to other things.

---

### Post by Lster on 2008-06-13
[QUOTE=slavik]...[/QUOTE]

Good points! :)

I ran each loop 100 times to produce these times (each test program was run five times and the quickest time chosen):

Pointer arithmetic (test one): 4.641s, 8752B
Array elements (test two): 4.732s, 8752B

The code compiles to the same thing now (as checked with diff)! And not just that, the assembly is also the same (obviously!).*

*Apart from:
> 	.file	"test1.c"
> 	.file	"test2.c"

---

### Post by nvteighen on 2008-06-13
> **slavik said:**
> 
Also, I think it would be better to run the iteration at least 10000 times, since in this particular example, the difference of 0.01 seconds can be attributed to other things.

Could you, please, elaborate on what other kind of things, for example?

---

### Post by Lster on 2008-06-13
Yielding for background tasks would probably be a large one. For some reason, timing something twice often seems to yield two results.

[http://en.wikipedia.org/wiki/Coroutine](http://en.wikipedia.org/wiki/Coroutine)

---

### Post by Can+~ on 2008-06-13
The second example does not free the allocated space. Also, you're using calloc, which wipes the space, meanwhile using myarray[10000] grabs anything there was in the memory before. I'd suggest just using malloc.

And AFAIK, using [FONT="Courier New"]anArray[2][/FONT] is equal to [FONT="Courier New"]*(anArray+sizeof(type)*2)[/FONT], since the [FONT="Courier New"][][/FONT] is just a wrapper for pointer arithmetic, and the name of the array is the pointer to the first element on it, so you could, use [FONT="Courier New"]myarray[10000][/FONT] and go throught it with both pointer arithmetic and the [FONT="Courier New"][][/FONT]. For example, you can use [FONT="Courier New"][-1][/FONT] and it will read what's behind the array in the memory (probably causing a segmentation fault), which is pretty much doing [FONT="Courier New"]*(anArray+sizeof(type)*-1)[/FONT]. Also, mallocing a [FONT="Courier New"]sizeof(type)*length[/FONT] let's you use [FONT="Courier New"][][/FONT] on the allocated space.

Access time to the memory is around 10^-9[seconds] or 1 [nanosecond], so you can expect minuscule times.

---

### Post by Lster on 2008-06-13
I write the test code myself. It declares the array globally (I'm not sure how GCC allocates it, but it's the same for both tests).

---

### Post by bruce89 on 2008-06-13
For instance, there are two signatures for the main function:

[PHP]
int main (int argc, char **argv)
int main (int argc, char *argv[])
[/PHP]

I like the first as saying "pointer to a pointer" is quite fun.

---

### Post by Can+~ on 2008-06-13
> **Lster said:**
> I write the test code myself. It declares the array globally (I'm not sure how GCC allocates it, but it's the same for both tests).

So if it's the same, why do you do it different? Build a normal array and go with both methods on the same file. Once setting the number to 1..n and another to n..1. That ensures that if the compiler... (or the kernel in fact) is allocating in different ways, it won't mess your "results".

I mean, is a general rule of thumb to just have 1 variable on any experiment, let everything else be constant.

---

### Post by wootah on 2008-06-13
> **Can+~ said:**
> The second example does not free the allocated space. Also, you're using calloc, which wipes the space, meanwhile using myarray[10000] grabs anything there was in the memory before. I'd suggest just using malloc.

** And AFAIK, using [FONT=Courier New]anArray[2][/FONT] is equal to [FONT=Courier New]*(anArray+sizeof(type)*2)[/FONT], since the [FONT=Courier New][][/FONT] is just a wrapper for pointer arithmetic,** and the name of the array is the pointer to the first element on it, so you could, use [FONT=Courier New]myarray[10000][/FONT] and go throught it with both pointer arithmetic and the [FONT=Courier New][][/FONT]. For example, you can use [FONT=Courier New][-1][/FONT] and it will read what's behind the array in the memory (probably causing a segmentation fault), which is pretty much doing [FONT=Courier New]*(anArray+sizeof(type)*-1)[/FONT]. Also, mallocing a [FONT=Courier New]sizeof(type)*length[/FONT] let's you use [FONT=Courier New][][/FONT] on the allocated space.

Access time to the memory is around 10^-9[seconds] or 1 [nanosecond], so you can expect minuscule times.

You are correct sir :)

---

### Post by Lster on 2008-06-13
[QUOTE=Can+~]I mean, is a general rule of thumb to just have 1 variable on any experiment, let everything else be constant.[/QUOTE]

It is. Literally, both files are identical except for the method they access the array.

If I was to run both tests in the same pass, that would introduce a new difference: which code is run first. Paging, and other things, could bias the results slightly. The way it is seems about as fair as possible.

---

### Post by slavik on 2008-06-13
> **nvteighen said:**
> Could you, please, elaborate on what other kind of things, for example?
other things: cache miss, other process, etc. anything that might interrupt the process from having 100% of CPU's time or even the inaccuracy of the clock.

---

### Post by nvteighen on 2008-06-13
> **slavik said:**
> other things: cache miss, other process, etc. anything that might interrupt the process from having 100% of CPU's time or even the inaccuracy of the clock.
Thanks! And possibly the same "time" command might interfere? (Heisenberg uncertainty principle may be applied?)

---

### Post by Can+~ on 2008-06-13
> **Lster said:**
> It is. Literally, both files are identical except for the method they access the array.

So if both methods of creating the array are the same (except that test2 didn't free the memory, causing it to re-address a new space), and both methods or accessing them are equivalent... what we are testing again?

Also, I told you to use the same array twice, that would reduce the fact that sometimes it is allocated somewhere, and after in another place, not that this is something crucial, and it may happened that allocates in the same place, I was just saying that to avoid this little issue.

And what has to do [paging]("http://en.wikipedia.org/wiki/Paging") here? You are using around 40kb of space, unless you're working with 64 kb of memory...

```
printf("%f", sizeof(int)*10000/1024.0);
```

*edit* Now I HAZ WORKZ, so I'll talk here later.

---

