---
title: "Problem with random() in g++"
date: 2007-10-10
forum: Programming Talk
---

### Post by din_de_valhalla on 2007-10-10
Hello, i'm new at the forums, and i wanted to register because i have a probem with g++. I made a simple program to generate random numbers:

```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	int i;
	randomize();
	for(i=0;i<10;i++)
		printf("%d\n",random(10));
	return 0;
}

```

and using:
g++ -o random random.cpp

i get the following errors:

random.cpp: In function ‘int main()’:
random.cpp:7: error: ‘randomize’ no se declaró en este ámbito
/usr/include/stdlib.h:445: error: demasiados argumentos para function ‘long int random()’
random.cpp:9: error: en este punto en el fichero

in spanish, it says something like " 'randomize' is not declared"
and "too much arguments for function long int random ()"

what's wrong here? :(

---

### Post by Wybiral on 2007-10-10
Looks a lot like C code, not C++.

Randomize isn't part of the C standard, use :
```

srand(time(NULL));

```
To seed the random number generator.

Then call "rand" which will generate an integer between 0 and RAND_MAX. You can use the modulus operator to squish the result to the range you need (in this case, "rand()%10").

[http://www.daniweb.com/forums/thread1769.html](http://www.daniweb.com/forums/thread1769.html)

---

### Post by ryno519 on 2007-10-10
First off, if this is C++ you should be using these headers,

#include <cstdlib>
#include <iostream>

Might as well use C++ IO mechanisms.

I don't recall a randomize or random function in standard C. What I do recall is 'srand' for seeding and 'rand' for generating random numbers. You seem to want to generate a number between 0 and 10 it would seem.

```

#include <iostream>
#include <cstdlib>

using namespace std;

int random(int max)
{
    return rand() / (RAND_MAX / max + 1);
}

int main()
{
    srand((unsigned int)time(0));
    for(int i = 0; i < 10; ++i)
    {
        cout << random(10) << endl;
    }
    
    return 0;
}

```

What this code does is seed the random number generator using the current time (using srand). It then loops 10 times, calling my random function which will generate the random number and perform a calculation on it to ensure it's between 0 and the number entered (in this case 10).

---

### Post by dwhitney67 on 2007-10-10
Ryno591,

For the random() function, this also would work (and is probably more efficient):

```
int random(int max)
{
    return rand() % max;
}
```

If you are looking to include 'max' in the range of numbers that can be returned, then that's going to be a problem if MAX_INT is passed in.  Thus it is normally expected that the result will always be [0, max)  --- which in English means any number from 0 to max, but not including max.

---

### Post by ryno519 on 2007-10-10
> **dwhitney67 said:**
> Ryno591,

For the random() function, this also would work (and is probably more efficient):

```
int random(int max)
{
    return rand() % max;
}
```

If you are looking to include 'max' in the range of numbers that can be returned, then that's going to be a problem if MAX_INT is passed in.  Thus it is normally expected that the result will always be [0, max)  --- which in English means any number from 0 to max, but not including max.

The problem with using a modulus operator is many environments do not generate random numbers exceedingly well. Specifically, the low order bits are not very random on many systems. This may not be an issue if you're compiling solely for a single environment (like Windows), but in the open source world it could present a bit of a problem, because your code can be compiled on multiple platforms with multiple configurations using multiple compilers.

In order to retrieve more random numbers you will want to use the high-order bits instead of the low-order bits, which is what 'rand() / (RAND_MAX / max + 1)' does.

---

### Post by dwhitney67 on 2007-10-10
Where did you lift that information from?  I'm curious because I have used rand() (and the seeder, srand()) before.

I have never written s/w for Windows.  All my of 18 years of programming experience has been with Unix/Linux.

---

### Post by ryno519 on 2007-10-10
> **dwhitney67 said:**
> Where did you lift that information from?  I'm curious because I have used rand() (and the seeder, srand()) before.

I have never written s/w for Windows.  All my of 18 years of programming experience has been with Unix/Linux.

Various professors when I was in college and professional relations. I'm sure you could find some information about it online.

---

### Post by hod139 on 2007-10-10
> **ryno519 said:**
> I'm sure you could find some information about it online.

You can read all the details in Numerical recipes for C.  A quick google search found this page about it:
[http://members.cox.net/srice1/random/crandom.html](http://members.cox.net/srice1/random/crandom.html)

---

### Post by Wybiral on 2007-10-10
As an added note, for simple stuff it's not going to matter. Only if you're using it for some kind of accurate probability simulation.

---

### Post by ryno519 on 2007-10-10
> **Wybiral said:**
> As an added note, for simple stuff it's not going to matter. Only if you're using it for some kind of accurate probability simulation.

It's simple enough to avoid the problem all together, so why bother? It's only an extra few characters.

---

### Post by Wybiral on 2007-10-10
Well, in a tight loop, it's two divisions (slower then 1 modulus). But you're right, knowing this it should probably be avoided.

---

### Post by dwhitney67 on 2007-10-10
> **Wybiral said:**
> As an added note, for simple stuff it's not going to matter. Only if you're using it for some kind of accurate probability simulation.

After reading the article, I second your opinion.  For most general uses, the modulo formula will suffice.  The "extra characters" describe by ryno591 actually represent extra calculations, not just extra characters to type in.

---

### Post by ryno519 on 2007-10-10
> **dwhitney67 said:**
> After reading the article, I second your opinion.  For most general uses, the modulo formula will suffice.  The "extra characters" describe by ryno591 actually represent extra calculations, not just extra characters to type in.

An extra division calculation is not going to to make a difference in your application. I can't think of many applications which would benefit more from using the low-order bits for random number calculations than using the high-order bits. There performance cost is very negligible.

---

### Post by gnusci on 2007-10-11
here one small code, it just generate random numbers between 1 and a given number:

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// return a random number between 1 and max
int my_random(int _max){
    return (rand() % _max) + 1;
}

int main(void)
{
    int i;
    //randomize();
    srand(time(NULL));
    for(i=0;i<10;i++)
        printf("%d\n",my_random(10));
    return 0;
}

[/PHP]

---

### Post by hod139 on 2007-10-11
> **gnusci said:**
> here one small code, it just generate random numbers between 1 and a given number:
<snip>
Did you read what ryno519 stated, or the link I posted, or all the discussion up to this point? 

From the article:
> 
Once more: Do NOT use 
      y = rand()  %  M;
as this focuses on the lower bits of rand(). For linear congruential random number generators, which rand() often is, the lower bytes are much less random than the higher bytes. In fact the lowest bit cycles between 0 and 1. Thus rand() may cycle between even and odd (try it out)The work-around for dealing with C's rand is provided in the article I linked (No one can make you use it, but why wouldn't you?)

Note, if you want a better random number generator in C++ consider using [Boost's random]("http://www.boost.org/libs/random/index.html").

---

### Post by din_de_valhalla on 2007-10-11
Thanks, the problem has been solved :D

just something... what does:
[LIST]using namespace std;
[/LIST]
and
[list]return rand() / (RAND_MAX / max + 1);[/list]
do?

EDIT: Ok, forget about the second, i just read it in one of the pages someone posted, guess i should have probably done that before
but i still don't understand the namespace std thing

---

### Post by eldragon on 2007-10-11
shouldnt reading from /dev/random give you a more randomy number?

considering the kernel uses more aleatory proceses to generate that pool...... (keystrokes, hdd acces, etcetera)...

i might be wrong..

if you need many numbers, and dont like to wait when the pool is empty, you could use /dev/urandom which starts seeding pseudorandom numbers when there's no entropy for random generation.

---

