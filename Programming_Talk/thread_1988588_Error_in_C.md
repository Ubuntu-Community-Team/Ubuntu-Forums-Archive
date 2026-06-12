---
title: "Error in C"
date: 2012-05-27
forum: Programming Talk
---

### Post by hailholyghost on 2012-05-27
Hello, I have the following code in C:

```
#include <stdio.h>
#include <math.h>

int main (int argc, char *argv[])
{
long i = atoi(argv[1]);
long high = i/2;
long factors[high];
long primes[high];
long exp[high];
long x;
long index = 0;
long primeindex = 0;
long y;
for (x = 2; x < high; x++) {
   if (i % x == 0) {
      factors[index] = x;
      index++;
   }
   short tmp;
   for (y = 2; y < x-1; y++) {
      if (x % y == 0) {
         tmp++;
         break;
      }
   }
   if (tmp == 0) {
      int exp = 1;
      int try = pow(x,exp);
      while (i % try == 0) {
         exp++;
         try = pow(x,exp);
      }
      if (exp > 1) {
         primes[primeindex] = x;
         long z = exp-1;
         exp[primeindex] = z;
         primeindex++;
      }
   }
}
return 0;
}
```

The compiler error is on line 37:
"subscripted value is neither array nor pointer".  The purpose of that line is to mimic Perl's "push" function and have two identically indexed arrays like Perl's associative array.  Obviously I was not successful.  How can I write to the arrays?

The purpose of this exercise is for me to learn C, so I'm translating a Perl code I wrote (which works perfectly, I would just like to make it faster so it could handle larger numbers):
```
#!/usr/bin/perl
use strict;
use warnings;

if ((@ARGV==0) || (int($ARGV[0]) != $ARGV[0])) {
   print "You did not enter an integer.  The proper syntax is \"perl factors.pl integer\"\n";
} else {
   my $upper = $ARGV[0]/2;
   my @factors;
   my %primefactors;
#find primes below $ARGV[0]
   foreach my $x (2..$upper) {
      if ($ARGV[0] % $x == 0) {
         push(@factors,$x);
      }
      my $tmp = 0;
      foreach my $y (2..$x-1) {
         if ($x % $y == 0) {
            $tmp++;
            last;
         }
      }
      if ($tmp == 0) {
         my $exponent = 1;
         while (($ARGV[0] % (($x)**$exponent)) == 0) {
            $exponent++;
         }
         if ($exponent > 1) {
            $primefactors{$x} = $exponent-1;
         }
      }
   }
#write prime factorization
   if (@factors == 0) {
      print "$ARGV[0] is prime.
The prime factorization of $ARGV[0] is $ARGV[0]^1.\n";
   } else {
   my $answer;
      foreach (sort{$a <=> $b} keys(%primefactors)) {
         $answer .= "($_^$primefactors{$_})";
      }
      print "The factors of $ARGV[0] are: @factors
The Prime Factorization of $ARGV[0] is $answer\n";
   }
}
```

---

### Post by Bachstelze on 2012-05-27
Well, duh, exp is an int. You can't subscript an int...

---

### Post by trent.josephsen on 2012-05-27
**(1)** **int exp = 1;** inside the if statement hides **long exp[high];** elsewhere; rename one of them.

**(2)** atoi(3) is found in <stdlib.h>, but you should actually use strtol(3) instead; atoi is deprecated. In any case you still need to #include <stdlib.h>.

**(3)** This:
```
	long high = i / 2;
	long factors[high];
```
is acceptable only in C99. I'm referring to defining an automatic array of a size that isn't known at compile-time. The C89 way to do this, which many people prefer for different reasons, is
```
long high = i / 2;
long *factors;
factors = malloc(high * sizeof *factors);
```
There's nothing wrong with the way you did it, though.

**(4)** Finally, I strongly suggest compiling with lots of warnings enabled, like this:
```
% gcc -std=c99 -Wextra -Wall -pedantic filename.c
```

-std=c99 tells gcc to use the C99 standard. -Wall and -Wextra turn on all the most useful warnings. -pedantic warns about some (not all) uses of nonstandard GNU extensions.

---

### Post by trent.josephsen on 2012-05-28
> **trent.josephsen said:**
> **(4)** Finally, I strongly suggest compiling with lots of warnings enabled, like this:
```
% gcc -std=c99 -Wextra -Wall -pedantic filename.c
```

-std=c99 tells gcc to use the C99 standard. -Wall and -Wextra turn on all the most useful warnings. -pedantic warns about some (not all) uses of nonstandard GNU extensions.
Quick addendum to this: -Wall -Wextra unfortunately wouldn't have warned you about accidentally hiding the long exp[] behind an int exp, but if you wanted to be warned about that, -Wshadow would do the trick.

Even with just -Wall, you would probably have gotten some idea of the problem anyway because gcc would have warned you that the 'exp' declared on line 11 was unused. Enabling more diagnostic messages is almost never a bad idea.

---

### Post by ofnuts on 2012-05-28
> **trent.josephsen said:**
> 
**(3)** This:
```
    long high = i / 2;
    long factors[high];
```is acceptable only in C99. I'm referring to defining an automatic array of a size that isn't known at compile-time. The C89 way to do this, which many people prefer for different reasons, is
```
long high = i / 2;
long *factors;
factors = malloc(high * sizeof *factors);
```There's nothing wrong with the way you did it, though.

But malloc() will require a free() somewhere, while the de-allocation of local variables is automatic. Of course, this doesn't make much difference here in the main().

---

### Post by trent.josephsen on 2012-05-28
> **ofnuts said:**
> But malloc() will require a free() somewhere, while the de-allocation of local variables is automatic. Of course, this doesn't make much difference here in the main().
You're correct, and I probably should have mentioned that.

I've personally spent some non-trivial time working on an embedded platform without working VLAs and it's something of a habit to avoid using them. Especially now that in C11 they're optional (and there's a macro you can test to see if the current implementation supports them, __STDC_NO_VLA__).

---

### Post by hailholyghost on 2012-06-03
Hello all,

I would've replied more quickly but I just finished a move and I have a big presentation to deal with.

The code has changed to:

```
#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main (int argc, char *argv[])
{
long i = strtol(argv[1], &argv[1], 10);
long high = i/2;
long factors[high];
/*long *factors;
factors = malloc(high * sizeof *factors);*/
long primes[high];
long exps[high];
long x;
long index = 0;
long primeindex = 0;
long y;
for (x = 2; x < high; x++) {
   if (i % x == 0) {
      factors[index] = x;
      index++;
   }
   int tmp;
   for (y = 2; y < x-1; y++) {
      if (x % y == 0) {
         tmp++;
         break;
      }
   }
   if (tmp == 0) {
      long exp = 1;
      long try = pow(x,exp);
      while (i % try == 0) {
         exp++;
         try = pow(x,exp);
      }
      if (exp > 1) {
         primes[primeindex] = x;
         exps[primeindex] = exp-1;
         primeindex++;
      }
   }
}
long px; //print index = px
for (px = 0; px <= primeindex; px++) {
   printf("%ld\n",factors[px]);
}
return 0;
}
``` 

I compile with:
```
gcc -o factors -std=c99 -Wextra -Wall -pedantic factors.c -lm
```

But unfortunately,
```
$ ./factors 36
2
3
4

```

The "malloc" code didn't make a difference with the c99 standard.

Maybe linked lists would work?

---

### Post by ofnuts on 2012-06-03
OK, now I see what you try to do... your code/algorithm is much too complicated... the one thing it should do, after discovering a factor, is to divide the output number by that factor and look for factors in the result. Otherwise it's very difficult to avoid not checking for 6 after checking for 2 and 3 (or 4 after 2, as you discovered). See this instead:
```

void factors(int x) {
    printf("%d:",x);
    for (int factor=2;factor<=x;) {
        if (x%factor !=0) {
            factor++; // not a divisor, try next
        }
        else {
            printf(" %d,",factor);
            x/=factor; // ... and try again with same factor
        }
    }
    printf("\n");
}

```With this code, the check for non-prime divisors is guaranteed to fail because any smaller divisors have already been removed.

---

### Post by squenson on 2012-06-03
A few things to make your program faster for large numbers:

1. If x1 is the number you want to factorize, and x2, x3, ..., xn the resulting numbers after you have divided x1 by the first found factors, you don't need to go further SQRT(xn) to search for the remaining factors. If there would be one number higher which is a factor, then it means that there is one lower and you would have already discovered it.

2. After you have identified the factor(s) 2, you don't need to check any even number as a factor, so your loop could be twice as fast if you start it with 3 and add 2 at each step.

Example: x1 = 172
x2 = 86
x3 = 43
test for 3, 5 are negative, 7*7 > 43 so no need to test further, 43 is a prime number, and 174 = 2 * 2 * 43.

---

### Post by trent.josephsen on 2012-06-03
Don't neglect to free() everything you malloc().

```
free(factors);
```

Put it right before **return 0;**.

---

### Post by hailholyghost on 2012-06-04
Hello all,

thanks so much for your assistance!  The C program is now fully functional to about 6.65000e+09, and it takes about 40 seconds to put out the numbers if it doesn't reach its primes quickly.

trent.josephsen: I added the free(factors) in as you suggested, along with the dynamic memory allocation.

ofnuts: you inspiration allows the program to run in split seconds instead of hours.  Your help is greatly appreciated!

squenson: I don't think I put in exactly what you said, but what you said inspired the "check" variable and loop which makes this program ***substantially*** faster for numbers with many factors of low prime numbers, although slightly slower if it has low exponents from  high prime numbers.  This is where the "try" comes in as well, which jumps up the index.

The code in its current form is ```
#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main (int argc, char *argv[])
{
long i = strtol(argv[1], &argv[1], 10);
long high = i/2;
/*long *factors;
factors = (long *) malloc (high * sizeof(long));
long factorindex = 0;*/
long *primes;
primes = (long *) malloc (high * sizeof(long));
long primeindex = 0;
long *primefactors;
primefactors = (long *) malloc (high * sizeof(long));
long x;
long check = 1;
for (x = 2; x <= high; x++) {
   if ((x > 2) && (x % 2 == 0)) {
      x++;
   }
   if ((x > 5 ) && (x % 5 == 0)) {
      x++;
   }
   if (i % x == 0) {
     // factors[factorindex] = x;
     // factorindex++;
      long z = 0;
      long y;
      for (y = 2; y <= x/2; y++) {
         if (x % y == 0) {
            z++;
            break;
         }
      }
      if (z == 0) {
         long exp = 1;
         long try = pow(x,exp);
         while (i % try == 0) {
            exp++;
            try = pow(x,exp);
         }
         exp--;
         primes[primeindex] = x;
         primefactors[primeindex] = exp;
         primeindex++;
         try = pow(x,exp);
         check *= try;
         x = try;
      }
   }
   if (check == i) {
      break;
   }
}
long V;
double j = i;
if (primeindex == 0) {
   printf("%e = %ld is a prime number\n",j,i);
} else {
  /* printf("The factors of %e = %ld are:\n", j,i);
   for (V = 0; V < factorindex; V++) {
      printf("%ld ",factors[V]);
   }*/
   printf("The prime factors of %e = %ld and their exponents are:\n",j,i);
   for (V=0; V < primeindex; V++) {
      printf("(%ld^%ld)",primes[V],primefactors[V]);
   }
   printf("\n");
}
//free(factors);
free(primes);
free(primefactors);
return 0;
}
```

However I get a "Segmentation Fault" if the number is too large.  I googled this and found that it is a common problem but I wasn't sure about how to fix it.

What can I do to the program so it can accept larger integers?  I noticed when I commented out the factoring parts that the integer limit went up.

Thanks for your help!
-Dave

---

### Post by Bachstelze on 2012-06-04
To deal with segfaults, you need to learn to use gdb. Here's a nice [tutorial](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Debug.html).

---

### Post by ofnuts on 2012-06-05
I don't think you are optimizing anything with this (except code obfuscation):
```

 if ((x > 2) && (x % 2 == 0)) {       x++;    }    
if ((x > 5 ) && (x % 5 == 0)) {       x++;    }
if (i % x == 0) {
  ...
}

```The idea is to avoid computing remainders... with you code you compute at least a remainder every time (maybe the compiler optimizes the "remainder by 2"), two remainders for every odd number (I'm not convinced the compiler will optimize the "remainder by 5") and 3 the rest of the time. Without these tests you only compute one each time.

Optimizing the code is fine but either you have a very clear view of an efficient algorithm that you code directly, or you write inefficient but working code that you gradually improve, checking that each individual improvement leaves you with working code (though in most cases this will never get you near the efficient algorithm... but it may lead you to think it over, scrap your code and start afresh with an efficient algorithm, because it's doesn't help much to be instruction-wise and algorithm-foolish).

Currently your code is hard to follow (variable names...) and hard to debug... Start by putting a couple of printf() at strategic places to see the evolution of strategic values.

Ponder these words by Nicolas Boileau: "Whatever we well understand we express *clearly*, and words flow with ease. " (change "express" by "code" and words by "instructions". If you aren't a fluent programmer, start by expressing your whole algorithm in English (or your native language), and then translate to code. Keep the English as comments. Programming isn't a matter of code anyway, it is a matter of having very clear ideas).

Ps: about "high" and the size of the arrays: a long unsigned int (64 bits) is less that 2^64, so has at most 63 divisors, so you can hardcode the size of your arrays (63 is a small number...).

---

### Post by 11jmb on 2012-06-05
> **ofnuts said:**
>  it's doesn't help much to be instruction-wise and algorithm-foolish).


Your wording here rivals Knuth's "Premature optimization..." :) I agree entirely

> **ofnuts said:**
> 
Start by putting a couple of printf() at strategic places to see the evolution of strategic values.


Or even better, use this as an opportunity to get familiar with gdb

> **ofnuts said:**
> 
Ps: about "high" and the size of the arrays: a long unsigned int (64 bits) is less that 2^64, so has at most 63 divisors, so you can hardcode the size of your arrays (63 is a small number...).

Be careful here. long unsigned int will have different ranges on different architectures. In fact, I think it is more likely to be 32 bits in my experience, and sometimes neither (40 bits on TI DSP's for example)

---

### Post by ofnuts on 2012-06-05
> **11jmb said:**
> Your wording here rivals Knuth's "Premature optimization..."
Premature *ation: always leaves some people complaining about the performance...

> **11jmb said:**
> Or even better, use this as an opportunity to get familiar with gdbReal programmers don't use debuggers :) What did RMS use to debug GDB? And let's be nice and suggest the DDD front-end to GDB.

> **11jmb said:**
> Be careful here. long unsigned int will have different ranges on different architectures. In fact, I think it is more likely to be 32 bits in my experience, and sometimes neither (40 bits on TI DSP's for example)
ok, let's settle for "sizeof (unsigned long long))*8)-1" (assuming an 8 bit byte of course...)

---

### Post by 11jmb on 2012-06-05
> **ofnuts said:**
> 
Real programmers don't use debuggers :) What did RMS use to debug GDB? 


REAL programmers program in machine language (none of this instruction set B.S. not to mention allowing themselves to be coddled by these "compilers" and "high-level languages" like fortran). Why rely on somebody else's work? :) When I was your age, I had to throw a lever just to flip a single bit.

> **ofnuts said:**
> 
And let's be nice and suggest the DDD front-end to GDB.

Fair enough :)

---

### Post by hailholyghost on 2012-06-10
Hello all,

I've taken your comments into account and after a lot of work I've come up with the following (this should remove all comments about inefficiency):

```
#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main (int argc, char *argv[])
{
unsigned long i = strtol(argv[1], &argv[1], 10);
unsigned long hi = i/2;
unsigned long si = sqrt(i);
/*long *factors;
factors = (long *) malloc (high * sizeof(long));*/
unsigned long x;
unsigned long check = 1;
double j = i;
printf("The number is %e and the factors are:\n",j);
if (i % 2 == 0) {
   unsigned long exp = 1;
   unsigned long try = 2;
   while (i % try == 0) {
      exp++;
      try = pow(2,exp);
   }
   exp--;
   printf("(2^%ld)",exp);
   check *= pow(2,exp);
}
if (check < i) {
   hi = i/check;
   for (x = 3; x <= hi; x+=2) {
      if (i % x == 0) {
         unsigned char z = 0;
         unsigned long y;
         for (y = 3; y <= sqrt(x); y+=2) {
            if (x % y == 0) {
               z++;
               break;
            }
         }
         if (z == 0) {
            unsigned long exp = 1;
            unsigned long try = x;
            while (i % try == 0) {
               exp++;
               try = pow(x,exp);
            }
            exp--;
            printf("(%ld^%ld)",x,exp);
            check *= pow(x,exp);
            hi = i/check;
         }
      }
      if ((check == 1) && (x >= si)) {
         printf("%e = %ld is a prime number\n",j,i);
         break;
      }
   }
}
printf("\n");
/*free(factors);*/
return 0;
}
```

The only problem is that it cannot go higher than 9.223372*10^18, for example when I try 9*10^19 I get this:
```
david@david-laptop:~/perl$ ./factors 90000000000000000000
The number is 9.223372e+18 and the factors are:
(7^2)(73^1)(127^1)(337^1)(92737^1)(649657^1)
```

The Perl equivalent of this program can deal with higher integers, however.

How can I get this program to accept higher integers?  I've thought about putting "long" in the arguments to main() but unfortunately it looks like the "char" type is required there.

How can I get this program to accept numbers higher than 9.223372e+18?

Thanks!

---

### Post by ofnuts on 2012-06-10
> **hailholyghost said:**
> Hello all,

I've taken your comments into account and after a lot of work I've come up with the following (this should remove all comments about inefficiency):

Not yet :)


> **hailholyghost said:**
> 
The only problem is that it cannot go higher than 9.223372*10^18, for example when I try 9*10^19 I get this:
```
david@david-laptop:~/perl$ ./factors 90000000000000000000
The number is 9.223372e+18 and the factors are:
(7^2)(73^1)(127^1)(337^1)(92737^1)(649657^1)
```The Perl equivalent of this program can deal with higher integers, however.

How can I get this program to accept higher integers?  I've thought about putting "long" in the arguments to main() but unfortunately it looks like the "char" type is required there.

How can I get this program to accept numbers higher than 9.223372e+18?

Thanks!
C's ints (even the unsigned long long kind) are limited to 64bits on most architecture. If you want to deal with arbitrarily high integers you have to use a library for arbitrary precision arithmetic or roll your own.

This limit is some kind of blessing here, because I wouldn't try to factor really big numbers with your algorithm....

---

### Post by hailholyghost on 2012-06-11
Hi Ofnuts,

I have done a lot to optimize this program:

1. First, test whether the integer is divisible by 2.  Divide by the largest power of two that has modulo 0.  The program stops when the check variable equals the entered integer i.  This allows the next loop (if (check <i)) to proceed in steps of 2, making the next loop twice as fast in theory.  This also allows the range of the next loop to be reduced.

2. If the integer has factors other than two, the program continues upwards testing integers in steps of 2 from 3.  If an integer is found to be a factor, the range is again reduced by the check variable.  The factor is tested if it is prime up to the square root of the prime number.

3. If there are no factors found below and including the square root of the number, the program stops.  This makes it **much** faster for prime numbers while slightly slower for composite ones.

4. The arrays were removed since there I could include printf statements in the loop which removed the memory problem.

What particular parts do you think are inefficient?  How would you make it faster?

The program is optimized to find high factors of low primes (e.g. 2^23, etc.).

For example,

```
$ time ./factors 74000124414
The number is 7.400012e+10 and the factors are:
(2^1)(3^2)(4111118023^1)

real	0m18.286s
user	0m18.278s
sys	0m0.002s

$ time ./factors 7400012441400
The number is 7.400012e+12 and the factors are:
(2^3)(3^2)(5^2)(4111118023^1)

real	0m18.666s
user	0m18.485s
sys	0m0.003s

$ time ./factors 6502071962016153600
The number is 6.502072e+18 and the factors are:
(2^50)(3^1)(5^2)(7^1)(11^1)

real	0m0.002s
user	0m0.000s
sys	0m0.002s

$ time ./factors 9202071962016153600
The number is 9.202072e+18 and the factors are:
(2^17)(3^1)(5^2)(41^1)(7577^1)(3013237^1)

real	0m0.015s
user	0m0.014s
sys	0m0.001s
```

---

### Post by trent.josephsen on 2012-06-11
Well, for starters, you're calling pow() a lot, which causes two major problems:

1_ pow() is a library function and incurs a lot of overhead compared to ordinary arithmetic;

2_ pow() deals with doubles, not integer types, so when you go beyond DBL_DIG digits you are likely to lose precision -- which, for your purposes, makes it completely useless.

Item 2 applies equally to sqrt(), in fact; even if you eliminated pow(), you could conceivably fail on large square numbers, because converting the result of sqrt(p*p) to an integer type might sometimes result in (p - 1) and you would never check p itself.

---

### Post by trent.josephsen on 2012-06-11
For a while I puzzled over where your program seemed to stop working, because it didn't make sense from a range point of view. Then I realized that although you store the number in an unsigned long, you still use strtol to convert it into a (signed) long. You can increase the usable range of your program by a factor of 2 just by changing that to strtoul instead.

Incidentally, this also explains why you're not seeing overflow (and crashing with a negative number) when the number exceeds LONG_MAX. From strtol(3):

```
RETURN VALUES
     The strtol(), strtoll(), strtoimax() and strtoq() functions return the
     result of the conversion, unless the value would underflow or overflow.
     If no conversion could be performed, 0 is returned and the global vari-
     able errno is set to EINVAL (the last feature is not portable across all
     platforms).  If an overflow or underflow occurs, errno is set to ERANGE
     and the function return value is clamped according to the following ta-
     ble.

           Function       underflow    overflow
           strtol()       LONG_MIN     LONG_MAX
           strtoll()      LLONG_MIN    LLONG_MAX
           strtoimax()    INTMAX_MIN   INTMAX_MAX
           strtoq()       LLONG_MIN    LLONG_MAX
```

In other news, I need a hobby.

---

### Post by ofnuts on 2012-06-12
> **hailholyghost said:**
> Hi Ofnuts,

I have done a lot to optimize this program
Not enough and/or not in the right places:
```

>> time ./factors 74000124414
74000124414: 2^1 * 3^2 * 4111118023^1

real    0m0.003s
user    0m0.008s
sys     0m0.000s

>> time ./factors 12345678901234567
12345678901234567: 7^1 * 1763668414462081^1

real    0m0.439s
user    0m0.436s
sys     0m0.008s

```

(Processor: Core I5 @ 2.4GHz)

You should keep your inner loop as streamlined as possible. In particular, the test for the powers should be taken out: first obtain a string of dividers (my code for this is one test, and three instructions inside a for loop (see above)), and when done,  display it as powers (displaying 2^3 instead of 2*2*2 is only a display matter and shouldn't interfere with your base code, ideally it would be in a separate function).

---

### Post by hailholyghost on 2012-06-14
Hi OfNuts,

I am curious how you managed this.  Would you mind posting your code that you managed to achieve these spectacular times?

I wish to learn from the master:guitar:

-Dave

---

### Post by ofnuts on 2012-06-15
> **hailholyghost said:**
> Hi OfNuts,

I am curious how you managed this.  Would you mind posting your code that you managed to achieve these spectacular times?
I won't post it here because that looks too much like homework for "C programming 101", and I don't want to make it too easy for the next ones. But you have sweated enough over it so see your PM for the pastebin URL... 

(other interested people can PM me for same)

---

### Post by hailholyghost on 2012-06-19
Hi OfNuts, et al.,

thanks so much for all of your help!  Since OfNuts requested, I won't post the program he sent but I will mark this threat as solved.

much appreciated to all!
-Dave

---

