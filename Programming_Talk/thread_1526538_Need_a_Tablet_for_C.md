---
title: "Need a Tablet for C"
date: 2010-07-08
forum: Programming Talk
---

### Post by navaneethan on 2010-07-08
> #include<stdio.h>
#include<conio.h>
void main()
{
	int i=54;
	float a=54;
	char *ii,*aa;
	

	ii=&i;
	aa=&a;

	printf("Address contained in ii=%u\n",ii);
	printf("Address contained in aa=%u\n",aa);

	printf("value at the Address contained in ii=%u\n",*ii);
	printf("value at the Address contained in aa=%f\n",*aa);
	getch();
}

Here i couldn't able to get the actual vlaue of *aa I mean (*aa=54) please what is the problem here?I wanna make it clear

---

### Post by dwhitney67 on 2010-07-08
I can cite several issues with the code, the most obvious being that it will not compile under Linux with the blaring conio.h header file being included.

As for a float value, it typically (always?) occupies 4-bytes.  You are assigning aa to the address of a, and then attempting to deference the value at aa for printing purposes.  This will yield only 1-byte out of the 4-bytes pointed to by aa.

So your goal of printing a 54 is not possible.


P.S.  If you have a strong desire to develop C code that is portable, then refrain from using whatever tutorial you are referencing because 1) it is outdated, and 2) it is Windoze-centric.

---

### Post by Tony Flury on 2010-07-08
If you want *aa to yeild 54 - you need to declare as a pointer to float

```

float *aa ; 

```
That way the compiler will know to generate a float value when you derefence the pointer.

And similarly ii should be declared as a pointer to int 
```

int *ii ;

```
if ii seems to work is more down to how the memory is organised and a lucky hit rather than deliberate and safe coding.

---

### Post by trent.josephsen on 2010-07-08
I'm not doing anything else this morning, so I thought I'd help you out with the rest of the issues in your code.  For starters, consider finding a better C book or tutorial and use a compiler with warnings turned on, which will catch most of your mistakes.

There are only two legal prototypes for main:
```
int main(void);
int main(int argc, char *argv[]);
```
Use one of those.  main returns **int**, so it's best to stick a return 0; at the end of it (zero, by long convention, indicates success).  In C89 forgetting to return something was a mistake; in C99 a return is implicitly added for you if you leave it out.

Don't use the non-standard <conio.h>.  Even on systems where it exists it was outdated decades ago (no exaggeration).  If you *must* get a character at the end of the program, use getchar(), which is defined in <stdio.h>.  It's better not to do that at all and run your terminal programs within a terminal, so that you can see the output even after they exit, instead of resorting to ugly hacks.

The %u format specifier expects an **unsigned int**, but you pass it a pointer.  This is likely to cause major problems when **int**s and pointers have different sizes, not just printing the wrong value (as it does on my computer) but screwing up the entire call stack.  Use %p to print pointers, and cast them to **void *** before passing them to printf.

Others have explained why *ii and *aa are **char**, but I'd also like to note that they are promoted to **int** for passing to printf -- that's one of the "standard integral promotions", and it's always done for printf.  By the same token, **float** arguments are promoted to **double**.  If you turned on warnings, you should have been told something like "format ‘%f’ expects type ‘double’, but argument 2 has type ‘int’" on the fourth printf, but the previous line would not give such an error.  (It is nonetheless wrong, because you're passing a **signed int** to a %u specifier, which expects **unsigned int**.)

gcc warns about "assignment from incompatible pointer type" on the assignments; they are likely to work anyway, but that's not the point.  It seems that the resource you are using may refer to a very old (pre-standard) C, where **char *** was the universal pointer type; since C89 it has been replaced in that job by **void ***.  Declaring ii and aa as **void *** will get rid of those warnings, but you can't dereference a pointer to void, so you must cast them back to **int *** and **float *** before dereferencing them.  Preferably, just declare them as pointer-to-int and pointer-to-float, respectively, to begin with, as Tony suggests.

I wouldn't have noticed by myself, but gnu **indent** warns me that there is ambiguity in the statements
```
ii=&i;
aa=&a;
```
because they could be interpreted as the old (pre-standard) form of the assignments
```
ii &= i;
aa &= a;
```
Use spaces around = to avoid these issues.

Here's my revision of your program:
```
#include<stdio.h>

int main(void)
{
    int i = 54, *ii = &i;
    float a = 54, *aa = &a;

    printf("Address contained in ii=%p\n", (void *) ii);
    printf("Address contained in aa=%p\n", (void *) aa);

    printf("value at the Address contained in ii=%u\n", *ii);
    printf("value at the Address contained in aa=%f\n", *aa);
}
```

---

### Post by navaneethan on 2010-07-09
Thanks my dear friend ;-)

---

