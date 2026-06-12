---
title: "Old Challenges 1: Multiplication Table"
date: 2008-05-09
forum: Programming Talk
---

### Post by JupiterV2 on 2008-05-09
This first one is from Dec. 06 but I wanted to start doing these from the beginning, as it were. This submission is almost identical to another poster's response so obviously I've not created anything magical here.

Critiques welcome.

[php]
#include <stdio.h>

int main(int argc, char** argv)
{
	for(int x = 1; x <= 10; x++)
	{
		for(int y = 1; y <= 10; y++)
		{
			printf("%4d%s", (y * x), (y == 10 ? "\n" : ""));
		}
	}
	
	return 0;
}[/php]

Note: I could have gotten fancy and accepted arguments to make the table from in the command line args but I was feeling lazy.

---

### Post by samjh on 2008-05-09
> **JupiterV2 said:**
> Critiques welcome.

[php]...
	for(int x = 1; x <= 10; x++)
	{
		for(int y = 1; y <= 10; y++)
		{
			printf("%4d%s", (y * x), (y == 10 ? "\n" : ""));
		}
	}	
...[/php]

First, the int declarations inside for(...) is naughty. ;)

Secondly, I am repulsed by the unnecessary use of [FONT="Courier New"]**y == 10 ? "\n" : ""**[/FONT], when you could have simply put [FONT="Courier New"]printf("\n");[/FONT] after the inner for-loop. :o

Here's a version more to my liking:```
#include <stdio.h>

int main(int argc, char** argv)
{
    int x, y;

    for(x = 1; x <= 10; x++)
    {
        for(y = 1; y <= 10; y++)
        {
            printf("%4d", (y * x));
        }
        printf("\n");
    }
    
    return 0;
} 
```:)

---

### Post by dwhitney67 on 2008-05-09
> **samjh said:**
> First, the int declarations inside for(...) is naughty. ;)

Please explain your statement.

Why do you think it is better to declare a variable outside of the functional block it will be used in?

Why do you think it is better to declare a variable that hasn't been initialized?

Please enlighten me and the OP.

---

### Post by WW on 2008-05-09
By default, the declaration a variable in the for-loop initialization clause is not allowed in gcc.  You can enable it with the option **-std=c99**.

For example...

**fortest.c**
```

#include <stdio.h>

int main(int argc, char *argv[])
{
    for (int i = 0; i < 5; ++i)
        printf("%d ",i);
    printf("\n");
    return 0;
}

```

Compile:
```

$ [color=blue]gcc --version[/color]
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

$ [color=blue]gcc fortest.c -Wall  -o fortest[/color]
fortest.c: In function 'main':
fortest.c:5: error: 'for' loop initial declaration used outside C99 mode
$ [color=blue]gcc fortest.c -Wall -std=c99 -o fortest[/color]
$ 

```

---

### Post by bobbocanfly on 2008-05-09
Here it is in Python

```
for i in range(1, 10):
    print str(i) + "x table:"
    for j in range(1, 10):
        print i*j
    print ""
```

---

### Post by dwhitney67 on 2008-05-09
> **WW said:**
> By default, the declaration a variable in the for-loop initialization clause is not allowed in gcc.  You can enable it with the option **-std=c99**.

Informative statement, however I was hoping samjh would reply back.

I was really looking for an opinion as to which style is more efficient and whether it is wise (i.e. best practice) to declare variables outside of the functional block where they are used.

As far as efficiency is concerned, well that is hard to discern on a regular desktop/laptop which is undoubtedly running many applications.

Nevertheless, below is a simple program I compiled using:
```
$ gcc -Wall -std=gnu99 -O2 compare.c -o compare
```
[PHP]
#include <stdlib.h>      // for atoi
#include <stdio.h>       // for printf
#include <sys/time.h>    // for gettimeofday
#include <time.h>        // for gettimeofday
#include <unistd.h>      // for sleep


void style_one( const unsigned int iter );
void style_two( const unsigned int iter );
void printTimeDelta( const char *txt, const struct timeval before, const struct timeval after );


int main( int argc, char **argv )
{
  const unsigned int iter = (argc > 1 ? atoi(argv[1]) : 10000 );

  style_one( iter );
  style_two( iter );

  return 0;
}

void style_one( const unsigned int iter )
{
  struct timeval before;
  struct timeval after;

  gettimeofday( &before, NULL );

  unsigned int i, j;

  for ( i = 0; i < iter; ++i )
  {
    for ( j = 0; j < iter; ++j )
    {
      sleep( 0 );
    }
  }

  gettimeofday( &after, NULL );

  printTimeDelta( "Style 1 Time Delta = ", before, after );
}


void style_two( const unsigned int iter )
{
  struct timeval before;
  struct timeval after;

  gettimeofday( &before, NULL );

  for ( unsigned int i = 0; i < iter; ++i )
  {
    for ( unsigned int j = 0; j < iter; ++j )
    {
      sleep( 0 );
    }
  }

  gettimeofday( &after, NULL );

  printTimeDelta( "Style 2 Time Delta = ", before, after );
}


void printTimeDelta( const char *txt, const struct timeval before, const struct timeval after )
{
  time_t delaySecs = after.tv_sec - before.tv_sec;
  suseconds_t delayUsecs = after.tv_usec - before.tv_usec;

  if ( delayUsecs < 0 )
  {
    delaySecs  -= 1;
    delayUsecs += 1000000;
  }

  printf( "%s%d.%d\n", txt, (int)delaySecs, (int)delayUsecs );
}[/PHP]

Run the code many times and you will see that it is not always clear as to which style is more efficient.  Perhaps Linux has a better timer, such has gethrtime() on Sun Solaris?

---

### Post by Wybiral on 2008-05-09
It's likely that GCC will optimize simple cases that use variables declared in a loop, so I wouldn't worry about it.

---

### Post by LaRoza on 2008-05-09
> **bobbocanfly said:**
> Here it is in Python

```
for i in range(1, 10):
    print str(i) + "x table:"
    for j in range(1, 10):
        print i*j
    print ""
```
How about this?
```

>>> for x in xrange(10):
...     for y in xrange(10):
...         print "%4i" % (y * x),
...     print "\n"
... 
   0    0    0    0    0    0    0    0    0    0 

   0    1    2    3    4    5    6    7    8    9 

   0    2    4    6    8   10   12   14   16   18 

   0    3    6    9   12   15   18   21   24   27 

   0    4    8   12   16   20   24   28   32   36 

   0    5   10   15   20   25   30   35   40   45 

   0    6   12   18   24   30   36   42   48   54 

   0    7   14   21   28   35   42   49   56   63 

   0    8   16   24   32   40   48   56   64   72 

   0    9   18   27   36   45   54   63   72   81 

>>> 


```

---

### Post by samjh on 2008-05-09
> **dwhitney67 said:**
> Why do you think it is better to declare a variable outside of the functional block it will be used in?It is usually not better.  But see below.

> Why do you think it is better to declare a variable that hasn't been initialized?It isn't.  Variables should - ideally - be initialised as soon as meaningful initialisation data exist.  But again, see below.

I'm afraid you have missed my point.  My concern was not with the two issues you posed.  Rather it is that declaring variables (aka. "hiding" a variable) within trivial scopes like for-loops is just bad engineering.

Two reasons:

It is not friendly on multiple platforms.  While declaring variables within for(..) is legal, you may end up with unexpected results with some compilers.

Example:
```
int x;

... //some code involving x

for (int x=1; x<10; x++)
    ...//some code
```The above code will not compile on some, because the scope of x is ambiguous.  MS VC++ 6, for instance.  On others, the declaration inside the for-loop will be ignored!

Another problem is that in large projects, "hiding" variable declarations in trivial scopes is cumbersome.  Variables should be declared in the smallest feasible scope, but also broad enough scope to avoid duplicity and to ensure they are easily noticeable.  Variables should not be concealed inside the nooks and crannies of for-loops where they can be easily missed during audits or debugging.

Ideally, variable declarations should be at beginning of each function block, with sensible default initialisations, or be initialised as soon as meaning information can be put in it.  In the case of a general counting variable called "counter", initialisation can be in the for-loops themselves, or just prior to while/do, etc.  Where declarations need to be done elsewhere, readability/maintainability issues should be considered very strongly.

If you're targeting one platform and one compiler, I suppose it's OK.  But I'm of the belief that one should attempt to code in the safest and most future-proof manner reasonably possible.  That includes taking up some slack for non-standard-compliant compilers and ensuring that the code is scalable if it is later used on larger projects.

---

### Post by JupiterV2 on 2008-05-09
> **samjh said:**
> First, the int declarations inside for(...) is naughty. ;)


After reading the further post I agree and disagree. I fully understand your point but both the c99 standard and C++ accept said method as being valid. I prefer to limit the scope of a loop iterator in order to make a point that x is only viable within the loop.

Example 1:
```

int x;
...
for( x = 0; ...) { ... }
...
/* x is still viable for use in another way at this point */

```

Example 2:
```

...
for(int x = 0; ...) { ... }
...
/* there can be no confusion that x is local to the loop alone */

```

> 
Secondly, I am repulsed by the unnecessary use of [FONT="Courier New"]**y == 10 ? "\n" : ""**[/FONT], when you could have simply put [FONT="Courier New"]printf("\n");[/FONT] after the inner for-loop. :o

To be honest, my original code did exactly that, use printf() within the outer for loop but I was going for the less is more thing by trying to complete the task in as few lines as possible. That being said, I could have omitted the code-block brackets on the inner for loop to further reduce space.

I appreciate the feedback though. I will definitely take it to heart.

Thanks everyone else for their replies too.

---

### Post by dwhitney67 on 2008-05-10
> **JupiterV2 said:**
> 
To be honest, my original code did exactly that, use printf() within the outer for loop but I was going for the less is more thing by trying to complete the task in as few lines as possible. That being said, I could have omitted the code-block brackets on the inner for loop to further reduce space.

I presume the rationale for samjh's comment was to indicate that you are performing an unnecessary conditional statement within the inner loop, which ultimately wastes CPU cycles.

Efficient code, which is considered more important than any effort to reduce SLOC (source lines of code), the advice given (and hence your original instincts) should be heeded.

---

### Post by JupiterV2 on 2008-05-10
> **dwhitney67 said:**
> I presume the rationale for samjh's comment was to indicate that you are performing an unnecessary conditional statement within the inner loop, which ultimately wastes CPU cycles.

Efficient code, which is considered more important than any effort to reduce SLOC (source lines of code), the advice given (and hence your original instincts) should be heeded.

Point well taken.

---

### Post by samjh on 2008-05-10
> **JupiterV2 said:**
> I was going for the less is more thing by trying to complete the task in as few lines as possible. That being said, I could have omitted the code-block brackets on the inner for loop to further reduce space.

Don't worry about lines.  They're just letters on a piece of paper. :)

If you're concerned about efficiency, look at the number of logical steps needed to achieve a result.  Try to reduce the number of logical steps and calculations so that the computer has to think less to get something done.  But also keep in mind that functionality and accuracy are more important than efficiency.

---

