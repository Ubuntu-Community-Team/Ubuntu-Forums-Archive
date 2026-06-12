---
title: "Why Doesnt This C Program Crash?"
date: 2009-03-08
forum: Programming Talk
---

### Post by Nullack on 2009-03-08
Gday :)

So Ive been working on my little proggy and I decided to deliberately put an array that was too small in size. I dont understand though why this program doesnt crash at runtime??? The array named matrix should be 128. Both splint and gcc do not complain about this.

Also if anyone has a cleaner way of formatting the output without using ncruses or similar please advise :)

Code below:

```
#include <stdio.h> /* needed for printf() */
#include <stdlib.h> /* needed for rand() */
#include <time.h> /* needed for time() */

int main(void)
{
	/* declare variables */
	int matrix[123]; /* shouldnt this be too small?? */
	int i;

	time_t t;

	srand((unsigned) time(&t)); /* seed a new series of psudeo random integers, call it only once */
	
	printf("\n"); /* tidy display */

	/* Use modulus of RAND_MAX to achieve a psuedo random 0 or 1 */
	for(i=0; i<128; i++)
	{
		matrix[(i)] = rand()%2;
		if ((i == 32) || (i == 64) || (i == 96))
			printf("\n"); /* new line after four sets of eight */
		if ((i == 0) || (i == 8) || (i == 16) || (i == 24) || (i == 32) || (i == 40) || (i == 48) || (i == 56)) /* tab following each sequence of 8 */
			printf("\t");
		if ((i == 64) || (i == 72) || (i == 80) || (i == 88) || (i == 96) || (i == 104) || (i == 112) || (i == 120)) /* tab following each sequence of 8 */
			printf("\t");
		printf("%d", matrix[(i)]);
	}

	printf("\n\n"); /* tidy display */

	return (0);
}

```

---

### Post by lloyd_b on 2009-03-08
Because there's no rule that says you *can't* address beyond the end of the matrix - it only segfaults when you try to access beyond the limits of your memory segment.

When the program is compiled, it's quite possible that memory is being "padded" so that variables are aligned on a 2, 4, 8, or 16 byte boundary - the particulars are very compiler (and in some cases, machine) dependent.  So it may actually have extra bytes at the end of that array, thus preventing a segfault when you get to matrix[123].

It's also possible that you're messing with the value of one or more other variables.  When I run your code on my machine, it loops forever, which is probably a result of the value of "i" being overwritten by an access to matrix[].

A suggestion on simplifying the printing - if you use the modulo divide operator ("%"), you can easily determine if "i" is an even multiple of either 32 or 8.  Though you'll need to guard against the case of "i" being 0, since this will also leave a remainder of 0:
```
if (((i % 32) == 0) && (i > 0)) // newline after 4 sets of 8
    printf("\n");
else if (((i % 8) == 0) && (i > 0))  // tab after each set of 8
    printf("\t);
```

Lloyd B.

---

### Post by Nullack on 2009-03-08
Thanks very much Lloyd :) The modulus test is very elegant :)

This time I've done a massive difference between the loop and the array size, and it still doesnt crash.

```
#include <stdio.h> /* needed for printf() */
#include <stdlib.h> /* needed for rand() */
#include <time.h> /* needed for time() */

int main(void)
{
	int matrix[124]; /* declare the array */
	int i; 	/* declare the loop variable */

	time_t t;

	srand((unsigned) time(&t)); /* seed a new series of psudeo random integers, call it only once */
	
	/* Use modulus of RAND_MAX to achieve a psuedo random 0 or 1 */
	for(i=0; i<10124; i++)
	{
		matrix[(i)] = rand()%2;
		if ((i % 32) == 0) /* newline after 4 sets of 8 */
			printf("\n");
		if ((i % 8) == 0) /* tab after each set of 8 */
			printf("\t");
		printf("%d", matrix[(i)]);
	}

	printf("\n\n"); /* tidy display */

	return (0);
}

```

---

### Post by dwhitney67 on 2009-03-08
This program crashes on my system:
```

int main()
{
  int matrix[124];
  int i;

  for (i = 0; i < 126; ++i)
  {
    //matrix[i] = i % 2;
    matrix[i] = i;
  }
}

```
The reason is (probably) because I am exceeding the boundaries of matrix.  It will not crash when I iterate to i<125, which one would think it would.  Anyhow, not knowing enough about Linux internals, I suspect the code crashes because it is trying to reach a value outside its program space.

As for your code, the reason it does not crash, nor terminate, is because the iterator i is being reassigned a value, presumably either 0 or 1, after you exceed the array boundaries.  The variable i falls right the matrix array on the stack.

Anyhow, it is good programming practice to avoid using hard-coded numerals when declaring arrays or when using them as boundaries in a conditional.  Declare these fixed-numbers with a const unsigned int.  Alternatively, compute the number of elements in the array as the limiting value.

Examples:
```

static const unsigned int SIZE = 124;
int matrix[SIZE];
...
for (unsigned int i = 0; i < SIZE; ++i)
{
  ...
}

```

```

static const unsigned int SIZE = 124;
int matrix[SIZE];
...
for (unsigned int i = 0; i < sizeof(matrix)/sizeof(int); ++i)
{
  ...
}

```

---

### Post by Nullack on 2009-03-08
Thanks, when I put the variable for the array GCC spits back at me:

warning: ISO C90 forbids variable length array ‘matrix’

---

### Post by dwhitney67 on 2009-03-08
> **Nullack said:**
> Thanks, when I put the variable for the array GCC spits back at me:

warning: ISO C90 forbids variable length array ‘matrix’
We are in the year 2009, right?  Why are you using a compiler using standards that are almost 20 years old?

The most recent version of the compiler was release in 1999.  Specify that you want to use this version when you compile.

```

int main()
{
  static const unsigned int SIZE = 10;
  char array[ SIZE ];
  ...
  return 0;
}

```
To compile:
```

gcc -Wall -ansi -pedantic -std=gnu99 test.c

```
Alternatively, and apparently with different "features", you can specify -std=c99.

P.S.  It is my understanding that a newer compiler will be released later this year; maybe this is only applicable to C++.

---

### Post by nvteighen on 2009-03-08
Well, what is/was done with the C89 standard was to use preprocessor macros, such as this:

```

#define SIZE 56

int main(void)
{
    char array[SIZE];

    /* ... */

    return 0;
}

```

---

### Post by dwhitney67 on 2009-03-08
> **nvteighen said:**
> Well, what is/was done with the C89 standard was to use preprocessor macros, such as this:

```

#define SIZE 56

int main(void)
{
    char array[SIZE];

    /* ... */

    return 0;
}

```

That is correct.  But unless absolutely necessary, one should use a new compiler that allows the programmer to use features that hopefully lead to better programming.

With lots of people still referring to the K&R book, I'm surprised that we don't see code like the following more often:
```

void function(str, val)
  char* str;
  int   val;
{
  ...
}
...

```

---

### Post by wmcbrine on 2009-03-08
K & R 2nd Edition uses ANSI prototypes. And it's still a good C book.

C89 is still the target of choice if you want your code to be portable.

---

### Post by dwhitney67 on 2009-03-08
> **wmcbrine said:**
> ...
C89 is still the target of choice if you want your code to be portable.
Portable to where?  If someone is writing a K&R example application, I hardly think it is going to be used within an embedded device.  So therefore, as long as the application is going to be used on a desktop, use a modern compiler.

If one needs to write s/w for a specialized device where the only compiler available is one that pre-dates the advent of sliced-bread, then one might as well code for that target, but not base all of their other code on some obscure device.

---

### Post by wmcbrine on 2009-03-08
Portable to everywhere with a C compiler. Even gcc doesn't fully implement C99 yet. C89/C90 is its default mode, for good reason. (Of course it also supports all kinds of gcc-specific extensions in its default mode.)

Again, I'm suggesting C89 (ANSI C), not "K & R" C (which implies pre-ANSI).

---

### Post by Nullack on 2009-03-08
Thanks, ansi and gnu99 works well :)

---

### Post by Sockerdrickan on 2009-03-09
> **Nullack said:**
> Thanks, ansi and gnu99 works well :)
Another thing you can do with C99 is

[php]
//C99 has C++ comments and variable declarations in for loops
//(you don't have to separate declaration and usage)
for(int i=0; i<lol; ++i)

/*C89 hasn't*/
int i;
for(i=0; i<lol; ++i)[/php]

---

### Post by nvteighen on 2009-03-09
Well, the GNU89 implementation does allow the C++/BCPL-style comments...

---

