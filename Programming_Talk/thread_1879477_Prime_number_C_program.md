---
title: "Prime number C program"
date: 2011-11-11
forum: Programming Talk
---

### Post by gameguy on 2011-11-11
I was just working on a basic C program (first C program - had a lot of experience with python though), but I can't understand some of the errors I am getting.
```

#include <stdio.h>
#include <math.h>

int is_prime (int num) {
    if (num % 2 == 0) {return 0;}
    int i;
    float root = sqrt(num);
    for (i=3; i < root + 1 ; i+=2) {
        if (num % i == 0) {
            return 0;
        }
    }
    return 1;

int main () {
    FILE *fin  = fopen ("primes.in", "r");
    FILE *fout = fopen ("primes.out", "w");

    int in;
    fscanf (fin, "%d", &in);  /*input*/

    int res = is_prime(in);

    fprintf (fout, "%d\n", res);
    return 0;
}

```Here's what I get:
```

When I try compiling it, I get this:
$ gcc -Wall -W main.c -o compiled
main.c: In function &#8216;is_prime&#8217;:
main.c:15:5: warning: &#8216;main&#8217; is normally a non-static function [-Wmain]
main.c:26:1: error: expected declaration or statement at end of input
$ ./compiled
../test.sh: 2: ./compiled: not found

```

---

### Post by karlson on 2011-11-11
> **gameguy said:**
> 
```

int is_prime (int num) {
    if (num % 2 == 0) {return 0;}
    int i;
    float root = sqrt(num);
    for (i=3; i < root + 1 ; i+=2) {
        if (num % i == 0) {
            return 0;
        }
    }
    return 1;


```

Anything missing at the end of this function?

---

### Post by Bachstelze on 2011-11-11
Indented correctly, your code is

```
#include <stdio.h>
#include <math.h>

int is_prime (int num) {
    if (num % 2 == 0) {return 0;}
    int i;
    float root = sqrt(num);
    for (i=3; i < root + 1 ; i+=2) {
        if (num % i == 0) {
            return 0;
        }
    }
    return 1;

    int main () {
        FILE *fin  = fopen ("primes.in", "r");
        FILE *fout = fopen ("primes.out", "w");

        int in;
        fscanf (fin, "%d", &in);  /*input*/

        int res = is_prime(in);

        fprintf (fout, "%d\n", res);
        return 0;
    }

```

See the problem now?

*EDIT for the lolz*:

```
BUGS
     indent has even more switches than ls(1).
```

---

### Post by gameguy on 2011-11-11
Yeah, I see it now. Now I have the error I had before though...
```

/tmp/ccVg8krD.o: In function `is_prime':
main.c:(.text+0x36): undefined reference to `sqrt'
collect2: ld returned 1 exit status

```

---

### Post by ziekfiguur on 2011-11-11
try to compile with -lm that will include the math library

---

### Post by gameguy on 2011-11-11
How exactly do I do that?
I tried this:
gcc -Wall -W main.c -o -lm compiled

but it seems to think that compiled is the input, not the output

---

### Post by JDShu on 2011-11-11
the flag -o means output, so it always has to be followed by the name of the executable.

---

### Post by gameguy on 2011-11-11
Thanks - it works great - but will I need to do that for every library?

---

### Post by ziekfiguur on 2011-11-11
For every other external library yes. But not for most things in the C standard library.
Actually I'm not really sure why the math functions are in a separate library in C, with C++ you wouldn't have to provide the -lm parameter.

---

### Post by Bachstelze on 2011-11-11
> **ziekfiguur said:**
> 
Actually I'm not really sure why the math functions are in a separate library in C, with C++ you wouldn't have to provide the -lm parameter.

They are not in a separate library "in C". They are in a separate library in the GNU C Library.

(10,000th message.)

---

### Post by gameguy on 2011-11-11
That makes sense. I had assumed the math module was in the standard library - I guess I'm too used to python.

Thanks for all your help guys.

---

### Post by nvteighen on 2011-11-12
Apparently, the reason why the math parts of the C Standard Library have been placed under a separate libm.so is historical... predating GNU/Linux...

[http://stackoverflow.com/questions/5419366/why-do-i-have-to-explicitly-link-with-libm](http://stackoverflow.com/questions/5419366/why-do-i-have-to-explicitly-link-with-libm)

[http://stackoverflow.com/questions/1033898/why-do-you-have-to-link-the-math-library-in-c](http://stackoverflow.com/questions/1033898/why-do-you-have-to-link-the-math-library-in-c)

---

### Post by 3Miro on 2011-11-12
The function may compile and run, but I don't think it does what it is supposed to do. There is some ambiguity on whether or not people take 1 to be prime or composite, however, every definition that I have seen takes 2 to be a prime number. If 2 is given to the code, then the is_prime function with return 0 (i.e. composite). You need one more if statement at the top.

---

### Post by gameguy on 2011-11-12
This program won't have to handle 2 as a prime number, so it's all good :)

---

### Post by trent.josephsen on 2011-11-12
I have never heard 1 called prime or composite.  It's neither.

---

### Post by 3Miro on 2011-11-12
> **trent.josephsen said:**
> I have never heard 1 called prime or composite.  It's neither.

It depends on the definition. One definition is that a prime number has exactly two distinct factors, composite numbers have more than two and 1 is the exception being neither prime nor composite.

The other way to look at it is to define prime numbers only those can be divided to 1 and themselves. This makes 1 a prime number and all numbers are either prime or composite.

In USA people seem to use the first definition more often then not. Either way, it makes no real difference since all math results are true one way or another. The only difference is that sometimes people have to make mention of 1 as a special case.

---

### Post by 3Miro on 2011-11-12
> **gameguy said:**
> This program won't have to handle 2 as a prime number, so it's all good :)

This is good, although I would make sure to put a comment line in the function specifying that it works only for large numbers (or numbers bigger than 2).

---

### Post by Bachstelze on 2011-11-12
> **3Miro said:**
> It depends on the definition. One definition is that a prime number has exactly two distinct factors, composite numbers have more than two and 1 is the exception being neither prime nor composite.

The other way to look at it is to define prime numbers only those can be divided to 1 and themselves. This makes 1 a prime number and all numbers are either prime or composite.

In USA people seem to use the first definition more often then not. Either way, it makes no real difference since all math results are true one way or another. The only difference is that sometimes people have to make mention of 1 as a special case.

No one says 1 is prime nowadays, mostly because if it were, the decomposition of an integer in prime factors would not be unique (so no, not all math results are true one way or another). Now whether you say it is composite or neither does not really matter, but it is definitely not prime.

---

### Post by 3Miro on 2011-11-12
> **Bachstelze said:**
> No one says 1 is prime nowadays, mostly because if it were, the decomposition of an integer in prime factors would not be unique (so no, not all math results are true one way or another). Now whether you say it is composite or neither does not really matter, but it is definitely not prime.

And if you define 1 to be composite, then you don't have prime number decomposition for all numbers.

On the other hand, if you define 1 as prime and redefine the prime number decomposition to exclude 1, then it is still unique. Regardless of how you define 1, sooner or later you have to deal with it as a special case. Sometimes it is easier to just take it as prime sometimes it is not and if you have to modify the theorems to account for the special case it doesn't make Math results false. It is not wrong to define 1 as a prime number, it is just uncommon in the USA.

---

### Post by Bachstelze on 2011-11-12
> **3Miro said:**
>  It is not wrong to define 1 as a prime number, it is just uncommon in the USA.

I didn't say it's wrong, I said no one does it nowadays. In no part of the world.

[http://en.wikipedia.org/wiki/Prime_number#Primality_of_one](http://en.wikipedia.org/wiki/Prime_number#Primality_of_one)

> Henri Lebesgue is said to be the last professional mathematician to call 1 prime.

Lebesgue died in 1941.

---

### Post by 3Miro on 2011-11-12
> **Bachstelze said:**
> 
Lebesgue died in 1941.

I have met a few living ones that still call it a prime.

Either way, the problem with the code isn't 1 but 2. Supposedly this wouldn't come into play, but I would still like to see the code fixed in that way.

---

### Post by Lux Perpetua on 2011-11-13
> **3Miro said:**
> And if you define 1 to be composite, then you don't have prime number decomposition for all numbers.1 isn't usually considered composite, either. 1 and -1 are **units** in the ring of integers, meaning they have multiplicative inverses. I'm not sure what you mean about not all numbers having decompositions, but if you mean that 1 doesn't have a prime factorization, then that's false: the prime factorization of 1 is the empty product. 
> **3Miro said:**
> Regardless of how you define 1, sooner or later you have to deal with it as a special case. Sometimes it is easier to just take it as prime sometimes it is not and if you have to modify the theorems to account for the special case it doesn't make Math results false. It is not wrong to define 1 as a prime number, it is just uncommon in the USA.It causes far fewer problems if 1 is not considered prime. In modern mathematics, 1 is therefore **not** considered prime. As far as I know, none of this is at all specific to the USA.

---

### Post by gameguy on 2011-11-14
```
#include <stdio.h>
 #include <math.h>
int is_prime (int num) {
    if (num % 2 == 0) {return 0;}
    int i;
    float root = sqrt(num);
    for (i=3; i < root + 1 ; i+=2) {
        if (num % i == 0) {
             return 0; 
        }
   }
   return 1;
 }

int main () {
     FILE *fin  = fopen ("primes.in", "r");
     FILE *fout = fopen ("primes.out", "w");
      int in;     fscanf (fin, "%d", &in);  /*input*/
      int res = is_prime(in);
      fprintf (fout, "%d\n", res);
      return 0;
}

```Happy now?

---

### Post by xytron on 2011-11-14
When you do consider 1 to be "just a prime" as it were it will possess some special properties that it shares with no other prime.
 
I read a book by a very educated modern author with advanced degrees that considered 1 to be prime but his results weren't exclusively connected to number theory.
 
I like the way a professor at UT put it "The number one is far more special than a prime!"

---

