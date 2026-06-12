---
title: "Easy Linux C Random Number Implementation?"
date: 2009-02-28
forum: Programming Talk
---

### Post by Nullack on 2009-02-28
Im doing my head in :)

I have a need for a program to spit out to the terminal 5 random 0s or 1s in eight length blocks. I figured this would be a good first learning exercise for coming to terms with C. But the more I search around about random numbers in Linux the more I realise its not simple!

I have so far hard coded the variables just to get something coded, its below. As I am a total amateur at C and this is my first C program I welcome any criticism :) Splint and gcc seem happy with the code so far.

```
#include <stdio.h>

int main(void)
{
	int n1, n2, n3, n4, n5, n6, n7, n8, i;
	i = 0;
	while (i < 5)
		{
			i++;
			n1 = 0, n2 = 1, n3 = 0, n4 = 0, n5 = 1, n6 = 1, n7 = 0, n8 = 1;
			printf("\n\t%d%d%d%d%d%d%d%d\n",n1,n2,n3,n4,n5,n6,n7,n8);
		}
	printf("\n");
	return (0);
}
```

---

### Post by stroyan on 2009-02-28
You can use srand and rand or srandom and random to create a sequence of
pseudo-random numbers after setting a seed value.  Setting the seed to different
initial values will be required if you want different random numbers for every
run of your program.
You can use /dev/urandom on linux to get random numbers from the kernel.
To see details on using the library functions you should get and read the
development manpages.
```

sudo apt-get install manpages-dev
man -k random
man 3 rand
man 3 random
man urandom

```

---

### Post by jimi_hendrix on 2009-02-28
may i suggest googling random numbers in C?

you will need to include stdlib.h (for the rand function) and time.h (for seeding the rand function)

---

### Post by eldragon on 2009-02-28
having /dev/urandom or /dev/random available, i wouldnt bother with anything else.

learn how to open files and read them and you are set :D

---

### Post by jimi_hendrix on 2009-02-28
> **eldragon said:**
> having /dev/urandom or /dev/random available, i wouldnt bother with anything else.

learn how to open files and read them and you are set :D

it is the easiest way, but not cross platform (well if you want your code ported to windows at least)

---

### Post by hessiess on 2009-02-28
> **jimi_hendrix said:**
> it is the easiest way, but not cross platform (well if you want your code ported to windows at least)

That's what the preprocessor is for ;).

---

### Post by jimi_hendrix on 2009-02-28
right :)

well the cross-platform way isnt complex and i am +1 for it but whatever works for him

---

### Post by Can+~ on 2009-02-28
No need for /dev/random, just plain [FONT="Courier New"]random()[/FONT] will do.

---

### Post by Nullack on 2009-03-01
Thanks for the help folks :)

Im trying to make this as cross platform as possible.

I've got two problems so far with my latest code:

1. If I quickly rerun the binary it shows the same numbers. How can I see srand with more time precision or something?

2. Splint has a code warning I dont understand and cant fix:

```

Splint 3.1.2 --- 08 Nov 2008

hello.c: (in function main)
hello.c:14:8: Function srand expects arg 1 to be unsigned int gets time_t:
                 time(NULL)
  To allow arbitrary integral types to match any integral type, use
  +matchanyintegral.

Finished checking --- 1 code warning
```

My code:

```
#include <stdio.h> /* needed for printf() */
#include <stdlib.h> /* needed for rand() */
#include <time.h> /* needed for time() */

int main(void)
{
	/* declare variables */
	int a1, a2, a3, a4, a5, a6, a7, a8; /* a column */
	int b1, b2, b3, b4, b5, b6, b7, b8; /* b column */
	int c1, c2, c3, c4, c5, c6, c7, c8; /* c column */
	int d1, d2, d3, d4, d5, d6, d7, d8; /* d column */
	int i; /* loop integer */

	srand(time(NULL)); /* seed a new series of psudeo random integers, call it only once */

	for(i=0; i<5; i++) /* loop five times */
	{
		/* Use modulus of RAND_MAX to achieve a psuedo random 0 or 1 */
		a1 = rand() % 2, a2 = rand() % 2, a3 = rand() % 2, a4 = rand() % 2,
		a5 = rand() % 2, a6 = rand() % 2, a7 = rand() % 2, a8 = rand() % 2;
		b1 = rand() % 2, b2 = rand() % 2, b3 = rand() % 2, b4 = rand() % 2,
		b5 = rand() % 2, b6 = rand() % 2, b7 = rand() % 2, b8 = rand() % 2;
		c1 = rand() % 2, c2 = rand() % 2, c3 = rand() % 2, c4 = rand() % 2,
		c5 = rand() % 2, c6 = rand() % 2, c7 = rand() % 2, c8 = rand() % 2;
		d1 = rand() % 2, d2 = rand() % 2, d3 = rand() % 2, d4 = rand() % 2,
		d5 = rand() % 2, d6 = rand() % 2, d7 = rand() % 2, d8 = rand() % 2;
		printf("\n\t%d%d%d%d%d%d%d%d",a1,a2,a3,a4,a5,a6,a7,a8); /* display a column */
		printf("\t%d%d%d%d%d%d%d%d",b1,b2,b3,b4,b5,b6,b7,b8); /* display b column */
		printf("\t%d%d%d%d%d%d%d%d",c1,c2,c3,c4,c5,c6,c7,c8); /* display c column */
		printf("\t%d%d%d%d%d%d%d%d\n",d1,d2,d3,d4,d5,d6,d7,d8); /* display d column */
	}

	printf("\n"); /* tidy display */

	return (0);
}

```

My makefile:

```
hello:	hello.c
	gcc -march=native -mtune=native -O3 -Wall -pedantic -pipe -o hello hello.c
```

I would appreciate any criticism of my coding too please :)

---

### Post by monkeyking on 2009-03-01
how random do you need it to be?

---

### Post by Nullack on 2009-03-01
Not strong if its a hassle, but reasonable :)

---

### Post by monkeyking on 2009-03-01
I've been quite happy with the mersenne twister [http://en.wikipedia.org/wiki/Mersenne_twister](http://en.wikipedia.org/wiki/Mersenne_twister)

I would recommend, defining wrapper function,
such that, it's possible to switch to a different implementation of a random number generator at a later point.
Or just make it possible to change at compile time with a #define.
Also remember to use fixed seed, in the dev phase of your project,
and at a later point to print the seed so that you have a reference.

---

### Post by Can+~ on 2009-03-01
Ok, I noticed the code having the classical ignorance of Arrays.

[PHP]#include <stdio.h> /* needed for printf() */
#include <stdlib.h> /* needed for rand() */
#include <time.h> /* needed for time() */

int main(void)
{
	/* declare variables */
	int matrix[64];
	int i, col, row; /* loop integer */

	srand(time(NULL)); /* seed a new series of psudeo random integers, call it only once */

	for(i=0; i<5; i++) /* loop five times */
	{
		for(col=0; col<8; col++)
		{
			for(row=0; row<8; row++)
			{
				matrix[(col*8)+row] = rand()%2;
				printf("%d ", matrix[(col*8)+row]);
			}
			printf("\n");
		}
		printf("---------------\n");
	}

	printf("\n"); /* tidy display */

	return (0);
}[/PHP]

In fact, if your objective is just to print the matrix, you don't even need to store it anywhere, just do [FONT="Courier New"]printf("%d ", rand()%2);[/FONT]

Notice that:
[list][*]matrix can be [8][8] and have the same result as doing matrix[64].
[*]Also, for iterating over the array, you could use one or two for loops and each 8 iterations print the "\n".
[*]In the end, all the methods are equivalent, so it's a matter of personal choice.
[/list]

---

### Post by Nullack on 2009-03-01
That is so much better, thanks allot Can+~ - Im going to brush up on Arrays.

---

