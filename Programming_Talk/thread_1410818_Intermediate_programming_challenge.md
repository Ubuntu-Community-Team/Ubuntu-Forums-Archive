---
title: "Intermediate programming challenge"
date: 2010-02-19
forum: Programming Talk
---

### Post by howlingmadhowie on 2010-02-19
Okay, here's a slightly more difficult challenge than the ones in the beginner programming challenge series.

To prove or disprove is the following:

the 1000th prime number is 7919.
the 10000th prime number is 104729.
the 100000th prime number is 1299721.
the 1000000th prime number is 15485857.
the 10000000th prime number is 179424691.

How many of these can you prove or disprove in a reasonable time? You are not allowed to just look them up online! :D

---

### Post by Barrucadu on 2010-02-19
```
The 1000th     prime number is 7919
The 10000th    prime number is 104729
The 100000th   prime number is 1299709
The 1000000th  prime number is 15485863
The 10000000th prime number is 179424673
```

It took just under 10 minutes&#8212;the vast majority of which was spent on the 10,000,000th prime.

```
#include <stdio.h>

int isprime(int p)
{
    int i;

    for(i = 2; i * i <= p; i ++)
    {
	if(p % i == 0) return 0;
    }

    return 1;
}

int main()
{
    int n = 0;
    int p = 2;

    while(n <= 10000000)
    {
	if(isprime(p))
	{
	    ++n;

	    if(n == 1000)     printf("The 1000th     prime number is %i\n", p);
	    if(n == 10000)    printf("The 10000th    prime number is %i\n", p);
	    if(n == 100000)   printf("The 100000th   prime number is %i\n", p);
	    if(n == 1000000)  printf("The 1000000th  prime number is %i\n", p);
	    if(n == 10000000) printf("The 10000000th prime number is %i\n", p);
	}

	++p;
    }
}

```

---

### Post by howlingmadhowie on 2010-02-19
> **Barrucadu said:**
> ```
The 1000th     prime number is 7919
The 10000th    prime number is 104729
The 100000th   prime number is 1299709
The 1000000th  prime number is 15485863
The 10000000th prime number is 179424673
```

It took just under 10 minutes—the vast majority of which was spent on the 10,000,000th prime.


That seems to be a pretty fast computer. On my old laptop it took about 4 minutes to check the primes :) can you improve your algorithm? :D

---

### Post by Marlonsm on 2010-02-19
Here is mine, in Python. It's not very fast, but works...
[php]from math import sqrt
number = 17.00
count = 7
target = input("Which prime would you like to find? ")
lowprimes = {1:2,2:3,3:5,4:7,5:11,6:13}
if target in lowprimes:
	number = lowprimes[target]
else:
	while count < target:
		number += 2 
		root = int(sqrt(number)+1)
		for divisor in range(1,root/2):
			prime = True
			if number/(2*divisor + 1) == int(number/(2*divisor + 1)):
				prime = False
				break
		if prime == True:
			count += 1
print "The", target,"th prime is", int(number)[/php]

It tries only odd numbers (after 2) and tries only divisors smaller than or equal to the square root of the number.

EDIT: Updated thanks to CptPicard's hint.

---

### Post by CptPicard on 2010-02-19
> **Marlonsm said:**
> 
It tries **only odd** numbers (after 2) and tries only divisors smaller than or equal to the square root of the number.

Hint: You're onto something bigger there. Push that idea a bit further...

---

### Post by sharpdust on 2010-02-19
The expert challenge should be next where it uses numbers that are outside the range of primitive types.

---

### Post by Richard1979 on 2010-02-19
> **Barrucadu said:**
> ```
The 1000th     prime number is 7919
The 10000th    prime number is 104729
The 100000th   prime number is 1299709
The 1000000th  prime number is 15485863
The 10000000th prime number is 179424673
```It took just under 10 minutes&#8212;the vast majority of which was spent on the 10,000,000th prime.

```
#include <stdio.h>

int isprime(int p)
{
    int i;

    for(i = 2; i * i <= p; i ++)
    {
    if(p % i == 0) return 0;
    }

    return 1;
}

int main()
{
    int n = 0;
    int p = 2;

    while(n <= 10000000)
    {
    if(isprime(p))
    {
        ++n;

        if(n == 1000)     printf("The 1000th     prime number is %i\n", p);
        if(n == 10000)    printf("The 10000th    prime number is %i\n", p);
        if(n == 100000)   printf("The 100000th   prime number is %i\n", p);
        if(n == 1000000)  printf("The 1000000th  prime number is %i\n", p);
        if(n == 10000000) printf("The 10000000th prime number is %i\n", p);
    }

    ++p;
    }
}

```

I've ported this version to PHP:

[PHP]
<?php

function isprime($p)
{
    $i = 0;

    for ($i = 2; $i * $i <= $p; $i ++)
    {
    if ($p % $i == 0) {
        return 0;
    }
    }

    return 1;
}

echo "Prime Number PHP Port\nTo quit, press CTRL + \\\n\n";
$start = time();

$n = 0;
$p = 2;

while ($n <= 10000000)
{
    if (isprime($p))
    {
        ++$n;

        if ($n == 1000) {
            printf("The 1000th     prime number is %d\n", $p);
        }
        if ($n == 10000) {
            printf("The 10000th    prime number is %d\n", $p);
        }
        if ($n == 100000) {
            printf("The 100000th   prime number is %d\n", $p);
        }
        if ($n == 1000000) {
            printf("The 1000000th  prime number is %d\n", $p);
        }
        if ($n == 10000000) {
            printf("The 10000000th prime number is %d\n", $p);
        }
    }

    ++$p;
}

echo "Took " . round(($start - time()) / 60, 2) . " minutes to complete.\n";
[/PHP]It's been running for over an hour already...:lolflag:

---

### Post by Richard1979 on 2010-02-19
> **sharpdust said:**
> The expert challenge should be next where it uses numbers that are outside the range of primitive types.

Urgh no more maths, please. :P

---

### Post by jim_24601 on 2010-02-19
Here's a rework using a simple sieve of Eratosthenes. Uses a lot of memory, but is quite a bit faster:

```
#include <cstdio>
#include <vector>

const unsigned long MAXPRIME = 200000000;

int main()
{
  std::vector<int> composite(MAXPRIME/2);

  int n = 1;
  int p = 3;

  while (n < 10000000)
  {
    if (!composite[(p-3)/2])
    {
      //      printf("%d\n", p);
      ++n;
      if(n == 1000)     printf("The 1000th     prime number is %i\n", p);
      if(n == 10000)    printf("The 10000th    prime number is %i\n", p);
      if(n == 100000)   printf("The 100000th   prime number is %i\n", p);
      if(n == 1000000)  printf("The 1000000th  prime number is %i\n", p);
      if(n == 10000000) printf("The 10000000th prime number is %i\n", p);
      for (int pp = 3*p; pp < MAXPRIME; pp += 2*p)
      {
	composite[(pp-3)/2] = true;
      }
    }
    p += 2;
  }
}

```

(My original version used a vector<bool>, and took more than 10 times as long. vector<bool> is optimised for space not speed.)

---

### Post by howlingmadhowie on 2010-02-19
> **Richard1979 said:**
> I've ported this version to PHP:


It's been running for over an hour already...:lolflag:

it'll get there :) it will probably take between 10 and 20 times as long as the C code posted, so i'd reckon with about 3 hours.

---

### Post by Marlonsm on 2010-02-19
> **CptPicard said:**
> Hint: You're onto something bigger there. Push that idea a bit further...

I don't know if it's what you're thinking about, but I'll also remove the even numbers from the divisors...

Removing multiples of 3, 5... would be too much work for a small result, I think.

I updated my first post with the new program, it's about 80% faster than the other, but still quite slow.

---

### Post by howlingmadhowie on 2010-02-19
> **Marlonsm said:**
> I don't know if it's what you're thinking about, but I'll also remove the even numbers from the divisors...

Removing multiples of 3, 5... would be too much work for a small result, I think.

given that i've found all primes up to a certain number (which i will call n), how can i find if n+1 is prime? do i have to check it by dividing by all numbers up to sqrt(n+1) and calculating the remainder? can i miss certain numbers out? if so, which ones?

---

### Post by azagaros on 2010-02-19
I guess I looked at this and wonder why so many if's for simple thoughts.

[PHP]
#include <stdio.h>
#include <stdlib.h>

int isPrime(int nPrime)
{
    int bPrime = 1;
    int max = nPrime;
    int nIndex = 3;
    if ((nPrime % 2 == 0 && nPrime != 2))
    {
        bPrime = 0;
    }
    else
    {
        while(nIndex*nIndex <= max)
        {
            if (nPrime % nIndex == 0)
            {
                bPrime = 0;
                break;
            }
            nIndex+=2;
        }
    }
    return bPrime;
}

int main()
{
    int nBase = 1000;
    int nPrime = 2;
    int nMainIndex = 1;

    while(nMainIndex <= 10000000)
    {
         if (isPrime(nPrime))
         {
            ++nMainIndex;
            if(nMainIndex == nBase)
            {
                printf("The %10i prime number is %i\n", nBase, nPrime);
                nBase = nBase*10;
            }
        }
        ++nPrime;
    }/*nMainIndex while */
    return 0;
}  
[/PHP]

Are you sure your math is right?  My first three after getting the code worked out to this, come out smaller, the forth one is spot on.  I got impatient to see the 5th.


Main notes about programming, boil to math, limit tests and make flow smooth.  These are main optimization techniques in most coding.

One thing I have learned is a drop down approach from one level to the next.  Whiles tend to be faster than for's from experience.

---

### Post by Marlonsm on 2010-02-19
> **howlingmadhowie said:**
> given that i've found all primes up to a certain number (which i will call n), how can i find if n+1 is prime? do i have to check it by dividing by all numbers up to sqrt(n+1) and calculating the remainder? can i miss certain numbers out? if so, which ones?
I know I could only use primes to test the number, but it would involve creating a (huge) list with all primes found so far.
Besides that, I couldn't think of anything else yet.

---

### Post by Richard1979 on 2010-02-19
> **howlingmadhowie said:**
> it'll get there :) it will probably take between 10 and 20 times as long as the C code posted, so i'd reckon with about 3 hours.

It's still running after 3 hours :lol:
It found the first lot but it's taking ages on the last one - running at a load of ~3 although I am doing other stuff like playing mp3s and browsing.
```

richard@lara:~/Programming/PHP/UbuntuComp$ php prime2.php 
Prime Number PHP Port
To quit, press CTRL + \

The 1000th     prime number is 7919
The 10000th    prime number is 104729
The 100000th   prime number is 1299709
The 1000000th  prime number is 15485863

```Made a typo in the timing code but no big deal, I'll just have to divide by 60 twice to find out the real time in minutes.
The difference between C and PHP is pretty shocking when it comes to tasks like this, I wouldn't think it would take that much longer seeing as most of PHP is written in C anyway.

---

### Post by falconindy on 2010-02-19
> **Richard1979 said:**
> Made a typo in the timing code but no big deal, I'll just have to divide by 60 twice to find out the real time in minutes.
Nonsense! Use the 'time' builtin in Bash -- e.g. time php prime2.php.

> **Richard1979 said:**
> The difference between C and PHP is pretty shocking when it comes to tasks like this, I wouldn't think it would take that much longer seeing as most of PHP is written in C anyway.
That's the difference between compiled and interpreted code. A few seconds of up front compile time saves you metric *** loads in execution because of the translation of human readable to machine code.

I was going to post a cleaned up version of Barracadu's algorithm which ran in about 3 minutes for me, but I'm not sure there's much point after jim_24601 posted his sieve solution.

---

### Post by Richard1979 on 2010-02-19
> **falconindy said:**
> Nonsense! Use the 'time' builtin in Bash -- e.g. time php prime2.php.

Wasn't aware of using it this way, nice one. :)

---

### Post by MadCow108 on 2010-02-19
very quick hack for multi threaded primecheck.
heavily unoptimized, uses the simple brute force "algorithm" and it probably has some off by one errors and other bugs (but I don't care :P)
it gets the (hopefully) prime 4611686018127387931 in ~1.2 seconds on 8 hyper threading 32 bit cores  :)

```

#include <stdio.h>
#include <math.h>
#include <pthread.h>
#include <stdint.h>
#include <stdlib.h>

static int end = 0;

typedef struct data {
  uint64_t tocheck;
  uint64_t lower;
  uint64_t upper;
} data;

void *isprime(void *arg)
{
  data * d = (data*)arg;
  uint64_t i;
  for (i = d->lower; i <d->upper && !end; i += 2) {
//    printf("testing %llu %% %llu = %llu\n", d->tocheck, i, d->tocheck % i );
    if (d->tocheck % i == 0) //simplest of all tests there are lots more
       __sync_fetch_and_add(&end,  1);
  }
}

int main(int argc, const char *argv[])
{
  pthread_t threads[NUM_THREADS];
 
  int rc;
  long t;
  data d[NUM_THREADS];
  uint64_t target = atoll(argv[1]);
  printf("testing %llu\n", target);
  if (target % 2 == 0)
    return 1;
  for(t=0; t<NUM_THREADS; t++){
    d[t].tocheck = target;
    d[t].lower = 3 + (double)t/NUM_THREADS * sqrt(target);
    d[t].upper = (double)(t + 1)/NUM_THREADS * sqrt(target);
    printf("In main: creating thread %ld\n", t);
    rc = pthread_create(&threads[t], NULL, isprime, (void *)&d[t]);
    if (rc){
      printf("ERROR; return code from pthread_create() is %d\n", rc);
      return 1;
    }
  }
  int i;
  for (i = 0; i < NUM_THREADS; i++) {
    pthread_join(threads[i], NULL);
  }
  if (!end) {
    printf("prime\n");
    return 0;
  }
  return 1;
}

```

---

### Post by Barrucadu on 2010-02-19
Another Sieve of Eratosthenes, 18 seconds (quite an improvement over my first entry):

**edit:** changing *sieve to a char array instead of an int array speeds it up to about 12 seconds, and lessens the memory usage by a few hundred MiB :D

```
#include <stdio.h>
#include <stdlib.h>

#define MAXPRIME 200000000

int main()
{
    int n = 0;
    int p = 0;
    int i;
    char *sieve = (char*)malloc(sizeof(char) * MAXPRIME);
    sieve[0] = 1;
    sieve[1] = 1;

    while(n <= 10000000)
    {
	while(sieve[p] == 1) ++p;
	for(i = 0; i * p < MAXPRIME; ++i) sieve[i * p] = 1;
	++n;
	
	if(n == 1000)     printf("The 1000th     prime number is %i\n", p);
	if(n == 10000)    printf("The 10000th    prime number is %i\n", p);
	if(n == 100000)   printf("The 100000th   prime number is %i\n", p);
	if(n == 1000000)  printf("The 1000000th  prime number is %i\n", p);
	if(n == 10000000) printf("The 10000000th prime number is %i\n", p);
    }

    return 0;
}

```

---

### Post by cdiem on 2010-02-19
Not quite the whole challenge, but more like 4/5 of it. Trying to compute the last one gives me a memory error (I will have to profile it and change it a bit, if I find the time). A sample run:

[PHP]python -m cProfile test2.py
7919
104729
1299709
15485863
         64682310 function calls in 229.696 CPU seconds

   Ordered by: standard name

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        1    0.000    0.000  229.696  229.696 <string>:1(<module>)
        1    0.000    0.000  229.695  229.695 test2.py:1(<module>)
        1  122.057  122.057  229.695  229.695 test2.py:11(erathostenes)
 15999998   27.266    0.000   27.266    0.000 test2.py:5(is_in_not_primes)
        1    0.001    0.001  229.696  229.696 {execfile}
 47651176   78.147    0.000   78.147    0.000 {method 'add' of 'set' objects}
  1031130    1.481    0.000    1.481    0.000 {method 'append' of 'list' objects}
        1    0.000    0.000    0.000    0.000 {method 'disable' of '_lsprof.Profiler' objects}
        1    0.744    0.744    0.744    0.744 {range}
[/PHP]

And here's the code:

[PHP]
"""
A naive implementation of the sieve of Erathostenes
@author A. Nackov
"""
not_primes = set([])
primes = []

# using a set is O(1) for lookups in Python 
def is_in_not_primes(num):
	if num in not_primes:
		return True
	else:
		return False

def erathostenes(max):
	for num in range(2,max):
		if is_in_not_primes(num):
			pass
		else:
			primes.append(num)
			sum = num + num
			while sum < max:
				not_primes.add(sum)
				sum = sum + num
	return primes

primes = erathostenes(16000000)
print primes[1000 - 1] # zero indexed
print primes[10000 -1]
print primes[100000 -1]
print primes[1000000 -1]
#print primes[10000000 -1] -> gives a memory error
[/PHP]

Probably it would be better to use a lazy generation of the primes sequence here, but I'm still new in Python (with a few weeks of coding in it).

---

### Post by Some Penguin on 2010-02-19
If I might make an observation that might be relevant for different test data:  you don't have to compute the first N prime numbers to verify that X is the Nth prime number, if you first determine that X is not actually prime.

---

### Post by Bachstelze on 2010-02-19
Just for the lulz, a quick Haskell code to compute the nth prime:

```
isPrime         :: Int -> Bool
nthPrime        :: Int -> Int

isPrime 1       = False
isPrime 2       = True
isPrime n       = [p | p <- [2..n-1], mod n p == 0] == []

nthPrime n      = [p | p <- [2..], isPrime p] !! (n-1)

```

Terribly slow of course, I'll work on optimizing it.

---

### Post by howlingmadhowie on 2010-02-19
> **Some Penguin said:**
> If I might make an observation that might be relevant for different test data:  you don't have to compute the first N prime numbers to verify that X is the Nth prime number, if you first determine that X is not actually prime.

Unfortunately the numbers i suggested are all prime :) maybe i should have put a large compound number in the list, it would have been a good teaser :)

---

### Post by howlingmadhowie on 2010-02-19
> **Bachstelze said:**
> Just for the lulz, a quick Haskell code to compute the nth prime:

```
isPrime         :: Int -> Bool
nthPrime        :: Int -> Int

isPrime 1       = False
isPrime 2       = True
isPrime n       = [p | p <- [2..n-1], mod n p == 0] == []

nthPrime n      = [p | p <- [2..], isPrime p] !! (n-1)

```

Terribly slow of course, I'll work on optimizing it.

it may be slow, but it's a thing of beauty :)

---

### Post by Richard1979 on 2010-02-19
I've had to stop the PHP version because I need my CPU for encoding ATM - will run it overnight.
It's taken 6 hours until I stopped it, pathetic.

---

### Post by howlingmadhowie on 2010-02-19
> **Richard1979 said:**
> I've had to stop the PHP version because I need my CPU for encoding ATM - will run it overnight.
It's taken 6 hours until I stopped it, pathetic.

Don't worry about it. Have a look on Wikipedia at the sieve of Eratosthenes and try to implement that. I'd imagine it's possible to write a php program which will solve this in about 3 minutes, but it will take a lot of memory, so you'll need to include the line
```

ini_set("memory_limit", "100M");

```
or similar at the head of the file. 

However, for the interpreted languages i will be granting lots of bonus points for low memory usage :)

---

### Post by Richard1979 on 2010-02-19
Well memory is something I have lot's of, when I was watching it I was wondering if I could make it use more RAM.
I pushed the Nice down a fair bit and managed to get the load up to ~4 but it wasn't enough.
I'll revisit this in the morning. For now, whiskey and old CDs from the attic are too much fun.. :P

---

### Post by howlingmadhowie on 2010-02-19
Here are some results on my reference laptop up till now:

```

jim_24601  12,65s user 0,43s system 99% cpu 13,102 total

```
nice method. i'm not sure it's worth jumping by 2 each time. you do save a bit of work, but it also makes the solution less pure. 

```

howlingmadhowie% time python Marlonsm.py
Which prime would you like to find? 1000
The 1000 th prime is 7919
python Marlonsm.py  0,18s user 0,02s system 5% cpu 3,490 total
howlingmadhowie% time python Marlonsm.py
Which prime would you like to find? 10000
The 10000 th prime is 104729
python Marlonsm.py  2,73s user 0,09s system 47% cpu 5,913 total
howlingmadhowie% time python Marlonsm.py
Which prime would you like to find? 100000
The 100000 th prime is 1299709
python Marlonsm.py  92,63s user 1,16s system 95% cpu 1:37,98 total

```
the first time is how long the calculation took (for example 92,63s for the 100000th prime), the second time is this time plus waiting for me to enter the number :)

```

howlingmadhowie% time php -f Richard1979.php
Prime Number PHP Port
To quit, press CTRL + \

The 1000th     prime number is 7919
The 10000th    prime number is 104729
The 100000th   prime number is 1299709
Took -0.77 minutes to complete.
php -f Richard1979.php  43,26s user 2,50s system 99% cpu 45,936 total

```
I like the time estimate :) i see a bright future for you in construction work :)

```

howlingmadhowie% time ./azagaros
The       1000 prime number is 7907
The      10000 prime number is 104723
The     100000 prime number is 1299689
The    1000000 prime number is 15485857
^C
./azagaros  873,23s user 9,17s system 99% cpu 14:47,93 total

```
I stopped this one after it had been going for a while. It may have been quite close to an answer, however. The algorithm used is an O(n^(3/2)), so looking at this:
```

howlingmadhowie% time ./azagaros     ### changed so it stops at 100000
The       1000 prime number is 7907
The      10000 prime number is 104723
The     100000 prime number is 1299689
./azagaros  1,35s user 0,10s system 100% cpu 1,449 total
howlingmadhowie% gcc -O2 azagaros.c -o azagaros  ## changed to stop at 1000000
howlingmadhowie% time ./azagaros               
The       1000 prime number is 7907
The      10000 prime number is 104723
The     100000 prime number is 1299689
The    1000000 prime number is 15485857
./azagaros  42,10s user 2,25s system 99% cpu 44,444 total

```
I'd estimate it will need about 30*42,1s ~=1250s on my system.

```

howlingmadhowie% gcc -O2 -DNUM_THREADS=4 MadCow108.c -lm -pthread -o MadCow108
MadCow108.c: In function ‘main’:
MadCow108.c:34: warning: format ‘%llu’ expects type ‘long long unsigned int’, but argument 2 has type ‘uint64_t’
howlingmadhowie% time ./MadCow108
zsh: segmentation fault  ./MadCow108

```
Sorry MadCow108 :( It doesn't work on my system :( Did i try to compile it wrong? let me use the source ...

a-ha, it expects an argument :) okay. let's see what it does ...

```

howlingmadhowie% time ./MadCow108 179424673
testing 179424673
In main: creating thread 0
In main: creating thread 1
In main: creating thread 2
In main: creating thread 3
prime
./MadCow108 179424673  0,00s user 0,01s system 174% cpu 0,006 total
howlingmadhowie% time ./MadCow108 179424671 ### lucky guess :)
testing 179424671
In main: creating thread 0
In main: creating thread 1
In main: creating thread 2
In main: creating thread 3
prime
./MadCow108 179424671  0,00s user 0,01s system 158% cpu 0,006 total
howlingmadhowie% time ./MadCow108 `expr 179424673 \* 179424671`
testing 32193212922307583
In main: creating thread 0
In main: creating thread 1
In main: creating thread 2
In main: creating thread 3
./MadCow108 `expr 179424673 \* 179424671`  3,73s user 0,13s system 186% cpu 2,072 total

```
Yeah, it seems to work okay :)

```

howlingmadhowie% time ./Barrucadu 
The 1000th     prime number is 7919
The 10000th    prime number is 104729
The 100000th   prime number is 1299709
The 1000000th  prime number is 15485863
The 10000000th prime number is 179424673
./Barrucadu  18,15s user 0,64s system 99% cpu 18,890 total

```
This works fine.  It might be a good idea to implement a method to find the upper bound for the length of the sieve rather than just allocating 200MB :)

```

howlingmadhowie% time python cdiem.py
7919
104729
1299709
15485863
python cdiem.py  46,96s user 2,14s system 99% cpu 49,350 total

```
This works okay for an interpreted language.  Rather worrying is however the following:
```

Mem:   3091720k total,  2830780k used,   260940k free,     3584k buffers
Swap:  4883752k total,   126560k used,  4757192k free,   155756k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
28729 howie     20   0 1312m 1.3g 1680 R   98 43.0   0:12.88 python             

```

Here's my test solution btw:
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

typedef char _Element;

_Element* sieve;

int main(int argc, char**argv) {
  int i, length, step, found, tofind;
  double f;

  if(argc!=2) return EXIT_FAILURE;
  tofind=atoi(argv[1]);

  f=(double)tofind;
  if(tofind>=6) {
    length=(int)(f*log(f) + f*(log(log(f))));
  } else {
    length=50;
  }

  printf("length: %d\n", length);

  sieve=malloc(length*sizeof(_Element));

  for(i=0; i<length; i++) {
    sieve[i]=(_Element)1;
  }

  for(step=2; step*step<=length; step++) {
    if(sieve[step]) {
      i=step+step;
      while(i<length) {
        sieve[i]=0;
        i+=step;
      }
    }
  }

  i=1;
  found=0;
  while(found<tofind) {
    i++;
    if(sieve[i])
      found++;
  }
  printf("the %d prime is %d\n", tofind, i);

  return EXIT_SUCCESS;
}

```

```

howlingmadhowie% time ./howlingmadhowie 10000000
length: 188980382
the 10000000 prime is 179424673
./howlingmadhowie 10000000  10,14s user 0,78s system 99% cpu 10,929 total

```

I may try making it multi-threaded, because the sieve of Eratosthenes should be parallelizable without any real problems.

---

### Post by Bachstelze on 2010-02-19
Slightly improved version. :p

```
intSqrt         :: Int -> Int
isPrime         :: Int -> Bool
nthPrime        :: Int -> Int

intSqrt n       = truncate (sqrt m)
                  where m = fromInteger (toInteger n)

isPrime 1       = False
isPrime 2       = True
isPrime n       = [p | p <- [2..intSqrt n], mod n p == 0] == []

nthPrime n      = [p | p <- [2..], isPrime p] !! (n-1)

main = print (nthPrime 1000000)

```

Computes the millionth prime in just over a minute. I'll let it run for the ten-millionth and see what gives.

---

### Post by lavinog on 2010-02-19
This is a good challenge.

Here is my attempt at the Sieve of Eratosthenes in python while trying to conserve memory.
It does take a considerable amount of time
I still have some tinkering to do.
I will have to get back to this later.

[php]#! /usr/bin/env python

import sys
import math

def sieve_of_eratosthenes(end):
    possible_primes = set(range(3 , end + 1, 2) )
    primeset=set([2]) #already know 2 is prime
    return sieve_main(primeset,possible_primes,end)
    

def sieverange(primeset,end):
    #get last prime in set
    first_num = max(primeset) + 1
    if first_num %2 ==0:
        first_num+=1  #start with odd number

    possible_primes = set( range (first_num, end + 1, 2 ) )
    
    #remove multiples of predetermined primes
    for p in primeset:
        if p==2: continue # no need to check since all should be odd
        possible_primes -= set( range( p, end + 1 , p ) )
    
    return sieve_main( primeset, possible_primes, end )
    
    
    
def sieve_main( primeset, possible_primes, end ):    
    while possible_primes:
         # get first number...should be a prime
        p = min(possible_primes)
        
        #remove multiples and self from possible primes list
        possible_primes -= set( range( p , end + 1 , p ) ) # using p for start because I want to remove it.
        
        primeset.add(p)
        if p**2 > end + 1:  # the rest should be primes
            primeset |= set(possible_primes)
            return primeset
    


def sievetest():
    #OUTPUT_LIST = [1000,10000,100000,1000000,10000000]
    OUTPUT_LIST = [1000,10000,100000,1000000]

    step = 10000  # increasing this should speed things up, but use more memory

    last_count = 0
    primes = sieve_of_eratosthenes(1000000)
    
    
    while len(primes) <= max(OUTPUT_LIST):


        output_n = min(OUTPUT_LIST)
        if len(primes) > output_n:
            getprime(primes,output_n)
            OUTPUT_LIST.remove(output_n)

        primes = sieverange(primes, max(primes) + step )
        
        # Show some sort of progress indication
        if len(primes) - last_count > step:
            last_count = len(primes)
            sys.stdout.write('.')
            sys.stdout.flush()
        


def getprime(primes,output_n):
    primelist = list(primes)
    primelist.sort()
    print '\nThe %sth prime is %s'%( output_n, primelist[output_n-1])


def isprime(n):
    if n<2:return False
    for x in xrange(2, int( math.sqrt(n) ) + 1 ):
        if n % x == 0:return False
        
    return True
    
def checkprimes(primelist):
    actual_primes = [ n for n in xrange( max(primelist) + 1) if isprime(n) ]
    return set(primelist) ^ set(actual_primes)



def main():
    sievetest()


if __name__=='__main__':
    main()


[/php]

---

### Post by MadCow108 on 2010-02-19
> **howlingmadhowie said:**
> I may try making it multi-threaded, because the sieve of Eratosthenes should be parallelizable without any real problems.

this is actually a quite interesting problem. I though about trying after I wrote the other code posted here but ran out of time, maybe tomorrow.
It is not as easy as you think.
You'll need to synchronize your threads.

---

### Post by Bachstelze on 2010-02-19
```
firas@momiji ~ % cat primes.py
#!/usr/bin/env python

from math import *

def is_prime(n, l):
    # Where l is a list containing all primes up to n.
    for m in l:
        if n % m == 0:
            return False
        if m > sqrt(n):
            return True

primes = [2]
n = 3
l = 1

while l < 1000000:
    if is_prime(n, primes):
        primes.append(n)
        l += 1
        if l in [1000, 10000, 100000, 1000000, 10000000]:
            print("The %s th prime is %s." % (l, n))
    n += 1
firas@momiji ~ % time ./primes.py
The 1000 th prime is 7919.
The 10000 th prime is 104729.
The 100000 th prime is 1299709.
./primes.py  6.30s user 0.01s system 99% cpu 6.318 total

```

Not too bad. millionth is taking a while, though.

EDIT:

```
firas@momiji ~ % time ./primes.py
The 1000 th prime is 7919.
The 10000 th prime is 104729.
The 100000 th prime is 1299709.
The 1000000 th prime is 15485863.
./primes.py  151.39s user 0.03s system 99% cpu 2:31.45 total

```

---

### Post by Bachstelze on 2010-02-19
My C version, using the same method as the Python one above.

```
#include <math.h>             
#include <stdio.h>            
#include <stdlib.h>           

#define MAXPRIMENUMBER 10000000

int is_prime(int n, int l, int *primes)
{
    int i;
    for(i=0; i < l; i++) {
        if(n % *primes == 0)
            return 0;
        if(*primes > sqrt(n))
            return 1;
        primes++;
    }
    return 1;
}

int main(void)
{
    int n = 3;
    int l = 1;
    int *primes = malloc(MAXPRIMENUMBER*sizeof(int));

    *primes = 2;

    while(l < MAXPRIMENUMBER) {
        if(is_prime(n, l, primes)) {
            *(primes+l) = n;
            l++;
            if(l == 10000 || l == 100000 || l == 1000000 || l == 10000000) {
                printf("The %dth prime number is %d.\n", l, n);
            }
        }
        n++;
    }
    return 0;
}

```

```
firas@momiji ~ % time ./primes
The 10000th prime number is 104729.
The 100000th prime number is 1299709.
The 1000000th prime number is 15485863.
The 10000000th prime number is 179424673.
./primes  354.80s user 1.58s system 99% cpu 5:56.42 total

```

---

### Post by howlingmadhowie on 2010-02-20
> **MadCow108 said:**
> this is actually a quite interesting problem. I though about trying after I wrote the other code posted here but ran out of time, maybe tomorrow.
It is not as easy as you think.
You'll need to synchronize your threads.

I don't think any synchronization is necessary for the sieve of erasthingy. basically, all every thread will want to do is change a value in an array from an undetermined state to false.  who cares if 2 threads want to do that at the same time? the value at the end will still be false, and that's all we want.  you may end up doing some pointless work, but that's the only thing, and not all of it will be pointless.

---

### Post by nvteighen on 2010-02-20
PLT Scheme, using infinite streams (from the SRFI 41 library). Terribly slow and memory consuming, but the concept is what matters here... (I couldn't even get to the 10000th prime :(). Compiling to native doesn't help much either.

```

#lang scheme

(require srfi/41)

(define (make-integers-from n)
  (stream-cons n
               (make-integers-from (+ n 1))))

(define integers-from-2 (make-integers-from 2))

(define (make-primes stream)
  (stream-cons (stream-car stream)
               (make-primes (stream-filter
                             (lambda (x)
                               (not (= (modulo x
                                               (stream-car stream))
                                       0)))
                             stream))))

(define primes (make-primes integers-from-2))

(printf "1000th prime is ~a~%" (stream-ref primes 999))
(printf "10000th prime is ~a~%" (stream-ref primes 9999))
(printf "100000th prime is ~a~%" (stream-ref primes 99999))
(printf "1000000th prime is ~a~%" (stream-ref primes 999999))
(printf "10000000th prime is ~a~%" (stream-ref primes 9999999))

```

---

### Post by MadCow108 on 2010-02-20
> **howlingmadhowie said:**
> I don't think any synchronization is necessary for the sieve of erasthingy. basically, all every thread will want to do is change a value in an array from an undetermined state to false.  who cares if 2 threads want to do that at the same time? the value at the end will still be false, and that's all we want.  you may end up doing some pointless work, but that's the only thing, and not all of it will be pointless.

the simplest approach would be to remove the multiple in parallel and have a master thread determines which multiples.
But before you can do that, you have to make sure that all multiple eliminator threads are finished and distribute the value to eliminated to the threads.
I would consider this synchronization (and a performance factor when working on distributed nodes and not on shared memory)
But on shared memory system this is quite easy.

---

### Post by howlingmadhowie on 2010-02-20
> **MadCow108 said:**
> the simplest approach would be to remove the multiple in parallel and have a master thread determines which multiples.
But before you can do that, you have to make sure that all multiple eliminator threads are finished and distribute the value to eliminated to the threads.
I would consider this synchronization (and a performance factor when working on distributed nodes and not on shared memory)
But on shared memory system this is quite easy.

the way i see it is all you need is an atomic getNextNumber function, which starts at 2 and maxes out at sqrt(length)+1.

each thread when it's finished working through the list of numbers, or has determined that the number it's been given is already set to false, just calls getNextNumber again and continues.  

then at the end you have to wait for all threads to finish.  maybe getNextNumber can return 0 if called more often than it should and this trigger value can be used to end the threads.

---

### Post by MadCow108 on 2010-02-20
yes it can be optimized by only waiting for the thread which is working on the lowest set of non-sieved values containing a prime and threads which are finished faster just get stalled by getNextNumber()
Then your program does not get halted by slow threads which do not work on the critical set.
But determining this critical set is not trivial.

but this would also mean you need a threadsafe stack of numbers in getNextNumber() so the slow threads can catch up without losing information.

another way would be to produce all primes up to a certain bound in parallel and then removing all multiple of all these primes in parallel again, all packed in an recursive algorithm.
I think this would reduce the sequential part.

---

### Post by howlingmadhowie on 2010-02-20
> **MadCow108 said:**
> yes it can be optimized by only waiting for the thread which is working on the lowest set of non-sieved values containing a prime and threads which are finished faster just get stalled by getNextNumber()
Then your program does not get halted by slow threads which do not work on the critical set.
But determining this critical set is not trivial.

but this would also mean you need a threadsafe stack of numbers in getNextNumber() so the slow threads can catch up without losing information.


i don't see why you would need more than:
```

atomic function getNextNumber() {
  static int i=2;
  if(i<maxWanted)
    return i++;
  return 0;
}

```
With the sieve of erasthingy threads don't need to catch up. the worst that can happen is that you end up duplicating work.

Let me put my code where my mouth is ...

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

#define NUM_THREADS 4

typedef char _Element;

_Element* sieve;
int max, length;

int global_int=2;

void *run(void* foo) {
  unsigned int i, step;
  while(1) {
    step=__sync_fetch_and_add(&global_int, 1);
    if(step>max) {
      pthread_exit(NULL);
    }
    if(sieve[step]==0) continue;
    i=step+step;
    while(i<=length) {
      sieve[i]=0;
      i+=step;
    }
  }
}


int main(int argc, char** argv) {
  int i, tofind, rc, found;
  double f;
  pthread_t threads[NUM_THREADS];
  void *status;

  if(argc!=2) return EXIT_FAILURE;
  tofind=atoi(argv[1]);
  f=(double)tofind;
  if(tofind>=6) {
    length=(int)(f*log(f) + f*(log(log(f))));
  } else {
    length=50;
  }

  printf("length: %d\n", length);
  sieve=malloc(length*sizeof(_Element));
  max=(int)sqrt(length) +1;

  for(i=0; i<length; i++) {
    sieve[i]=(_Element)1;
  }

  for(i=0; i<NUM_THREADS; i++) {
    rc = pthread_create(&threads[i], NULL, run, NULL);
    if(rc) {
      printf("ERROR: return code from pthread_create is %d\n", rc);
      return EXIT_FAILURE;
    }
  }

  for(i=0; i<NUM_THREADS; i++) {
    rc=pthread_join(threads[i], &status);
    if (rc) {
      printf("ERROR: return code from pthread_join() is %d\n", rc);
      return EXIT_FAILURE;
    }
  }
  
  i=1;
  found=0;
  while(found<tofind) {
    i++;
    if(sieve[i])
      found++;
  }
  printf("the %d prime is %d\n", tofind, i);
  
  return EXIT_SUCCESS;
}

```

Strangely it's about 30% slower than a single threaded version on a dual core system. i'll try it out on a quad core system later on today.

---

### Post by MadCow108 on 2010-02-20
this works but, as you also noticed, is very slow
your first thread eliminates the multiples of 2 sequentially, but this is the most expensive step in the algorithm
all other threads will finish long before the first one. So your performance is effectivly again single threaded.

The gain (if not compensated by overhead) is negible and does not scale with higher number of processes.

you should try to keep the load on all threads as equal as possible to archive high speedup
you can do this by e.g. parallelizing this loop instead of the whole thing (and introducing alredy mentioned subtleties):
```

i=step*step;
    while(i<=length) {
      sieve[i]=0;
      i+=step;
    }

```
note you only have to begin at step*step instead of step+step, you already have removed all compounds of step < step*step earlier

---

### Post by howlingmadhowie on 2010-02-20
Firstly, there only are a small number of threads. Maybe the first thread will take along time eliminating multiples of 2, so long in fact, that all other threads have started by the time it finishes. but why should that make everything run 30% slower on a dual core machine? maybe one thread will try to eliminate multiples of 4 and another multiples of 6, so they won't do any useful work, but one will eliminate multiples of 3 and another multiples of 5 and so do useful work while the first is still eliminating multiples of 2. 

one idea i had to improve the performance would be to pause thread generation after the first thread has been generated. this should weed out a lot of extraneous work. another possiblity would be to assign batches of 100 or so numbers to be sieved for, rather than handing them out individually.

---edit---

my bad! i was counting it wrong! it actually takes less time :) Here some examples:

```

### NUM_THREADS=1, works in batches of 10
./howlingmadhowie2 10000000  13,46s user 0,22s system 98% cpu 13,819 total
howlingmadhowie% gcc -pthread -lm howlingmadhowie2.c -o howlingmadhowie2 -O2
howlingmadhowie% time ./howlingmadhowie2 10000000
length: 188980382
the 10000000 prime is 52200235
### NUM_THREADS=2, works in batches of 10
./howlingmadhowie2 10000000  20,88s user 0,26s system 176% cpu 11,973 total
howlingmadhowie% gcc -pthread -lm howlingmadhowie2.c -o howlingmadhowie2 -O2
howlingmadhowie% time ./howlingmadhowie2 10000000                           
length: 188980382
the 10000000 prime is 179424673
### NUM_THREADS=2, works in batches of 10. completes the sieve for 2 to 11 before creating threads
./howlingmadhowie2 10000000  18,94s user 0,19s system 169% cpu 11,287 total

```

As you can see, it is faster than a single-threaded approach, if not by much.

--edit--

more data. here at work on a 4-core phenom:
```

work-desktop% gcc -o mt -O3 -lm -pthread multithreaded.c -DNUM_THREADS=1
work-desktop% time ./mt 10000000                                        
length: 188980382
the 10000000 prime is 179424673
./mt 10000000  4,67s user 0,13s system 99% cpu 4,808 total
work-desktop% gcc -o mt -O3 -lm -pthread multithreaded.c -DNUM_THREADS=2
work-desktop% time ./mt 10000000                                        
length: 188980382
the 10000000 prime is 179424673
./mt 10000000  5,67s user 0,12s system 172% cpu 3,354 total
work-desktop% gcc -o mt -O3 -lm -pthread multithreaded.c -DNUM_THREADS=4
work-desktop% time ./mt 10000000                                        
length: 188980382
the 10000000 prime is 179424673
./mt 10000000  8,70s user 0,04s system 304% cpu 2,873 total

```
Here you can clearly see it getting faster when the number of threads is increased.

--edit--

btw, thanks for the tip with the step*step, MadCow108. i missed that one :)
That shaves another 2-10% off the time depending on number of threads and other stuff.

---

### Post by Richard1979 on 2010-02-20
Well the results are in for the PHP version, it took an amazing 594m25.311s which is nearly 10 hours.
Don't think I'll be using PHP for anything where speed is needed.

---

### Post by lavinog on 2010-02-20
I ran my script in python2.6 and 3.1 (up to 1,000,000th prime)

2.6:
```

The 1000th prime is 7919
.
The 10000th prime is 104729
..
The 100000th prime is 1299709
.......................................................................................
real	291m16.601s
user	283m39.860s
sys	7m36.690s

```

3.1:
```

The 1000th prime is 7919
.
The 10000th prime is 104729
..
The 100000th prime is 1299709
.......................................................................................
real	133m42.691s
user	127m30.870s
sys	6m11.760s

```

I checked that the count was greater than and not also equal to, so that is why the last prime wasn't displayed.

The fact that python3.1 took less than half the time is interesting.
I used 2to3 to refactor the script.

---

### Post by MadCow108 on 2010-02-20
> Here you can clearly see it getting faster when the number of threads is increased.

yes it does get faster. but the speedup is far from linear.
Also I'm sure the speedup will decrease further when using more threads. (I'll test when im at the right pc to use the 8 core pc I have acess to)

I'll hopefully have time this evening to try out my approach and see if it does better or worse.

---

### Post by howlingmadhowie on 2010-02-20
> **MadCow108 said:**
> yes it does get faster. but the speedup is far from linear.
Also I'm sure the speedup will decrease further when using more threads. (I'll test when im at the right pc to use the 8 core pc I have acess to)

I'll hopefully have time this evening to try out my approach and see if it does better or worse.

I don't think you can have a linear speed up without knowing beforehand which numbers are going to be prime, and that's the huge advantage of the single threaded method---by waiting until n-1 before running through the sieve for n, you do know which numbers are prime up to that point.  You might be able to restrict the threads to only run through the sieve for n smaller than the square of the largest finished value, but you'll be slowing down the computer immensely at the start.  As you pointed out, the time taken to run through the sieve for n=2 with a sieve of size 2*10^8 (which is what we're dealing with here) is not small, and in fact in this case you could probably save time by splitting this work up for a number of threads :)

Happy hacking!

---

### Post by Lux Perpetua on 2010-02-20
I took a crack at this. The only innovation here (not that I invented it) is "wheel factorization": pick a small number h (say 3) and take the smallest h primes: 2, 3, 5. The table of boolean values then omits all multiples of 2, 3, and 5; i. e., it only contains entries for numbers that are relatively prime to 2*3*5 = 30. There are various ways to implement this idea, and the one I chose here hopefully achieves a good balance between memory use and speed. Note that with h = 3, this eliminates almost 75% of all composite numbers before even starting to sift, and with h = 5 (my default), it eliminates almost 80%. The drawback to choosing larger values of h is the space required for bookkeeping and the cost of setting it up, which unfortunately explodes pretty quickly. 

```
#include <stdio.h>
#include <stdlib.h>

/* table[k][j] represents W*j + k.
   0 means not crossed off; 1 means crossed off.
   valid is a list of those k coprime to W (so that
   table[k] might actually contain primes) */

char **table;
int R;
int *valid;

int W = 1; 
int V = 1;

/* primes less than N will be printed */
int N = 200000000;

/* multiples of the h smallest primes will be eliminated
   implicitly */
int h = 5;

/* This is overkill; my machine overflows with just 10 primes */
int small_primes[25] = {2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31,
                        37, 41, 43, 47, 53, 59, 61, 67, 71, 73,
                        79, 83, 89, 97};

int to_print[6] = {1000, 10000, 100000, 1000000, 10000000, -1};
int count = 0;
int idx = 0;

void record(int p) {
    ++count;
    if (count == to_print[idx]) {
        ++idx;
        printf("prime #%d is %d\n", count, p);
    }
}

/* cross out all multiples of p of the form p*(W*j + k1) */
void sift(int k1, int p) {
    int q = k1*p;
    div_t d = div(q, W);
    int k2 = d.rem;
    int j2 = d.quot;

    if (q%p) {
        /* If k1*p overflowed, then q cannot be a multiple of p
           now. */
        return;
    }

    if (k1 <= p) {
        /* All multiples of p smaller than p*p are crossed off
           already, so find the smallest j2 for which 
           W*j2 + k2 is at least p*p. */
        
        d = div(p - k1, W);
        j2 += p*d.quot;
        if (d.rem) j2 += p;
    }

    for ( ; j2 < R; j2 += p) table[k2][j2] = 1;
}

void oom(void) {
    fprintf(stderr, "Memory allocation failed; aborting\n");
    exit(EXIT_FAILURE);
}

int main(int argc, char **argv) {
    int a;
    int i = 0, j = 0, k, p;

    if (argc >= 2) N = atoi(argv[1]);
    if (argc >= 3) h = atoi(argv[2]);

    if (h > 25 || h < 1) h = 1;

    for (a = 0; a < h; ++a) {
        int p = small_primes[a];

        W *= p;
        V *= (p-1);

        if (W%p) {
            /* overflow */
            h = 1;
            W = 2;
            break;
        }
    }

    R = N/W + 1;

    table = calloc(W, sizeof(*table));
    valid = malloc(V*sizeof(*valid));

    if (!table || !valid) oom(); 

    for (a = 0; a < h; ++a) {
        p = small_primes[a];
        record(p);
        table[p] = (char *)(-1);
        for (k = p*p; k < W; k += p) {
            table[k] = (char *)(-1);
        }
    }

    table[0] = NULL;
    for (k = 1; k < W; ++k) {
        if (!table[k]) {
            valid[i++] = k;
            table[k] =  calloc(R, sizeof(*(table[k])));
            if (!(table[k])) oom();
        } else {
            table[k] = NULL;
        }
    }

    i = 0;

    while (1) {
        int i1;

        ++i;
        if (i == V) {
            i = 0;
            ++j;
        }
        k = valid[i];
        p = W*j + k;

        if (p*p >= N) break;
        if (table[k][j]) continue;

        record(p);

        for (i1 = 0; i1 < V; ++i1) {
            sift(valid[i1], p);
        }
    }

    while (p < N) {
        if (!table[k][j]) record(p);

        ++i;
        if (i == V) {
            i = 0;
            ++j;
        }
        k = valid[i];
        p = W*j + k;
    }

    for (k = 0; k < W; ++k)
        if (table[k]) free(table[k]);

    free(table);
    free(valid);

    return 0;
}

``` Typical results: ```
> gcc -ansi -Wall -pedantic -O3 -o sieve7 sieve-v7.c
> time sieve7
prime #1000 is 7919
prime #10000 is 104729
prime #100000 is 1299709
prime #1000000 is 15485863
prime #10000000 is 179424673

real    0m4.972s
user    0m4.733s
sys     0m0.060s

```This is on an Intel Pentium M throttled to 800 MHz with 2GB of RAM, so the results aren't terrible. 

I made a multithreaded version of this, but I could only get a speedup of 22% on a (different) quad-core CPU, which to me doesn't justify the additional complexity.

---

### Post by Marlonsm on 2010-02-20
> **Lux Perpetua said:**
> I took a crack at this. The only innovation here (not that I invented it) is "wheel factorization": pick a small number h (say 3) and take the smallest h primes: 2, 3, 5. The table of boolean values then omits all multiples of 2, 3, and 5; i. e., it only contains entries for numbers that are relatively prime to 2*3*5 = 30. There are various ways to implement this idea, and the one I chose here hopefully achieves a good balance between memory use and speed. Note that with h = 3, this eliminates almost 75% of all composite numbers before even starting to sift, and with h = 5 (my default), it eliminates almost 80%. The drawback to choosing larger values of h is the space required for bookkeeping and the cost of setting it up, which unfortunately explodes pretty quickly. 

In mine I used only odd numbers (after 2) which is basically the same as using h=1. But yours seem quite fast.

---

### Post by Lux Perpetua on 2010-02-20
> **Marlonsm said:**
> In mine I used only odd numbers (after 2) which is basically the same as using h=1. But yours seem quite fast.It would be the same if you had implemented the sieve of Eratosthenes. :-) What you implemented is trial division, a much slower algorithm. (Its only redeeming quality is its excellent memory performance (O(1))).

---

### Post by howlingmadhowie on 2010-02-22
> **Lux Perpetua said:**
> I took a crack at this. The only innovation here (not that I invented it) is "wheel factorization": pick a small number h (say 3) and take the smallest h primes: 2, 3, 5. The table of boolean values then omits all multiples of 2, 3, and 5; i. e., it only contains entries for numbers that are relatively prime to 2*3*5 = 30. There are various ways to implement this idea, and the one I chose here hopefully achieves a good balance between memory use and speed. Note that with h = 3, this eliminates almost 75% of all composite numbers before even starting to sift, and with h = 5 (my default), it eliminates almost 80%. The drawback to choosing larger values of h is the space required for bookkeeping and the cost of setting it up, which unfortunately explodes pretty quickly. 

```
#include <stdio.h>
#include <stdlib.h>

/* table[k][j] represents W*j + k.
   0 means not crossed off; 1 means crossed off.
   valid is a list of those k coprime to W (so that
   table[k] might actually contain primes) */

char **table;
int R;
int *valid;

int W = 1; 
int V = 1;

/* primes less than N will be printed */
int N = 200000000;

/* multiples of the h smallest primes will be eliminated
   implicitly */
int h = 5;

/* This is overkill; my machine overflows with just 10 primes */
int small_primes[25] = {2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31,
                        37, 41, 43, 47, 53, 59, 61, 67, 71, 73,
                        79, 83, 89, 97};

int to_print[6] = {1000, 10000, 100000, 1000000, 10000000, -1};
int count = 0;
int idx = 0;

void record(int p) {
    ++count;
    if (count == to_print[idx]) {
        ++idx;
        printf("prime #%d is %d\n", count, p);
    }
}

/* cross out all multiples of p of the form p*(W*j + k1) */
void sift(int k1, int p) {
    int q = k1*p;
    div_t d = div(q, W);
    int k2 = d.rem;
    int j2 = d.quot;

    if (q%p) {
        /* If k1*p overflowed, then q cannot be a multiple of p
           now. */
        return;
    }

    if (k1 <= p) {
        /* All multiples of p smaller than p*p are crossed off
           already, so find the smallest j2 for which 
           W*j2 + k2 is at least p*p. */
        
        d = div(p - k1, W);
        j2 += p*d.quot;
        if (d.rem) j2 += p;
    }

    for ( ; j2 < R; j2 += p) table[k2][j2] = 1;
}

void oom(void) {
    fprintf(stderr, "Memory allocation failed; aborting\n");
    exit(EXIT_FAILURE);
}

int main(int argc, char **argv) {
    int a;
    int i = 0, j = 0, k, p;

    if (argc >= 2) N = atoi(argv[1]);
    if (argc >= 3) h = atoi(argv[2]);

    if (h > 25 || h < 1) h = 1;

    for (a = 0; a < h; ++a) {
        int p = small_primes[a];

        W *= p;
        V *= (p-1);

        if (W%p) {
            /* overflow */
            h = 1;
            W = 2;
            break;
        }
    }

    R = N/W + 1;

    table = calloc(W, sizeof(*table));
    valid = malloc(V*sizeof(*valid));

    if (!table || !valid) oom(); 

    for (a = 0; a < h; ++a) {
        p = small_primes[a];
        record(p);
        table[p] = (char *)(-1);
        for (k = p*p; k < W; k += p) {
            table[k] = (char *)(-1);
        }
    }

    table[0] = NULL;
    for (k = 1; k < W; ++k) {
        if (!table[k]) {
            valid[i++] = k;
            table[k] =  calloc(R, sizeof(*(table[k])));
            if (!(table[k])) oom();
        } else {
            table[k] = NULL;
        }
    }

    i = 0;

    while (1) {
        int i1;

        ++i;
        if (i == V) {
            i = 0;
            ++j;
        }
        k = valid[i];
        p = W*j + k;

        if (p*p >= N) break;
        if (table[k][j]) continue;

        record(p);

        for (i1 = 0; i1 < V; ++i1) {
            sift(valid[i1], p);
        }
    }

    while (p < N) {
        if (!table[k][j]) record(p);

        ++i;
        if (i == V) {
            i = 0;
            ++j;
        }
        k = valid[i];
        p = W*j + k;
    }

    for (k = 0; k < W; ++k)
        if (table[k]) free(table[k]);

    free(table);
    free(valid);

    return 0;
}

``` Typical results: ```
> gcc -ansi -Wall -pedantic -O3 -o sieve7 sieve-v7.c
> time sieve7
prime #1000 is 7919
prime #10000 is 104729
prime #100000 is 1299709
prime #1000000 is 15485863
prime #10000000 is 179424673

real    0m4.972s
user    0m4.733s
sys     0m0.060s

```This is on an Intel Pentium M throttled to 800 MHz with 2GB of RAM, so the results aren't terrible. 

I made a multithreaded version of this, but I could only get a speedup of 22% on a (different) quad-core CPU, which to me doesn't justify the additional complexity.

wow, cool beans :) that's fast :) 

now i just have to learn to read C code, so i can understand it :D

---

### Post by Marlonsm on 2010-02-22
> **howlingmadhowie said:**
> wow, cool beans :) that's fast :) 

now i just have to learn to read C code, so i can understand it :D

Agreed, it's very fast. I tried it, and here it seems that using h=4 is even faster.

---

### Post by Lux Perpetua on 2010-02-22
> **Marlonsm said:**
> Agreed, it's very fast. I tried it, and here it seems that using h=4 is even faster.I reworked it a little so that it tries to determine at run-time which value of "h" will work best. Unfortunately, it requires tuning based on specific information about the compiler and hardware (to know which parts will take how much time to execute), which I have no inclination to do. (The C1 and C2 constants in my code were found by trial and error. One could be more scientific about it and do some kind of linear regression, but it would still be machine-specific.) ```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

/* table[k][j] represents W*j + k.
   0 means not crossed off; 1 means crossed off.
   valid is a list of those k coprime to W (so that
   table[k] might actually contain primes) */

char **table;
int R;
int *valid;

int W = 1; 
int V = 1;

/* primes less than N will be printed */
int N = 200000000;

/* multiples of the h smallest primes will be eliminated
   implicitly */
int h = 5;

int to_print[6] = {1000, 10000, 100000, 1000000, 10000000, -1};
int count = 0;
int idx = 0;

void record(int p) {
    ++count;
    if (count == to_print[idx]) {
        ++idx;
        printf("prime #%d is %d\n", count, p);
    }
}

/* cross out all multiples of p of the form p*(W*j + k1) */
void sift(int k1, int p) {
    int q = k1*p;
    div_t d = div(q, W);
    int k2 = d.rem;
    int j2 = d.quot;

    if (q%p) {
        /* If k1*p overflowed, then q cannot be a multiple of p
           now. */
        return;
    }

    if (k1 <= p) {
        /* All multiples of p smaller than p*p are crossed off
           already, so find the smallest j2 for which 
           W*j2 + k2 is at least p*p. */
        
        d = div(p - k1, W);
        j2 += p*d.quot;
        if (d.rem) j2 += p;
    }

    for ( ; j2 < R; j2 += p) table[k2][j2] = 1;
}

void oom(void) {
    fprintf(stderr, "Memory allocation failed; aborting\n");
    exit(EXIT_FAILURE);
}

int main(int argc, char **argv) {
    int a;
    int i = 0, j = 0, k, p;
    double cost_est = HUGE_VAL, last_cost_est;

    if (argc >= 2) N = atoi(argv[1]);

    valid = malloc(1*sizeof(*valid));

    valid[0] = 1;
    for (a = 0; ; ++a) {
        int b = 0;
        int c = 0;
        int V1, W1;
        int *tmp;

        if (a == 0) p = 2;
        else if (a == 1) p = 3;
        else p = valid[1];

        V1 = V*(p-1);
        W1 = W*p;
        
        /* Estimate whether eliminating one more prime would
           help or hurt us, and act accordingly. */
        {
            /* This needs some tuning... */

            static const double C1 = 1.0;
            static const double C2 = 1000.0;

            last_cost_est = cost_est;
            cost_est = C1*N*log(log(N))*V1/W1 + C2*W1;
        }

        if (last_cost_est <= cost_est ||
            V1 < V || W1 < W) 
        {
            printf("eliminating %d small primes...\n", a);
            break;
        }

        record(p);

        tmp = malloc(V1*sizeof(*tmp));
        if (!tmp) oom();

        for (b = 0; b < p; ++b) {
            int d;
            for (d = 0; d < V; ++d) {
                tmp[c] = valid[d] + b*W;
                if (tmp[c]%p) ++c;
            }
        }

        free(valid);
        valid = tmp;

        V = V1;
        W = W1;
    }

    R = N/W + 1;

    table = calloc(W, sizeof(*table));
    if (!table) oom();

    for (i = 0; i < V; ++i) {
        table[valid[i]] = calloc(R, sizeof(**table));
    }
    
    i = 0;

    printf("beginning sieve...\n");

    while (1) {
        int i1;

        ++i;
        if (i == V) {
            i = 0;
            ++j;
        }
        k = valid[i];
        p = W*j + k;

        if (p*p >= N) break;
        if (table[k][j]) continue;

        record(p);

        for (i1 = 0; i1 < V; ++i1) {
            sift(valid[i1], p);
        }
    }

    while (p < N) {
        if (!table[k][j]) record(p);

        ++i;
        if (i == V) {
            i = 0;
            ++j;
        }
        k = valid[i];
        p = W*j + k;
    }

    for (k = 0; k < W; ++k)
        if (table[k]) free(table[k]);

    free(table);
    free(valid);

    return 0;
}
```

---

### Post by patrickaupperle on 2010-02-27
Although it is slow and almost embarrassing after all the multithreading and super quick ones, but here it is. I am an absolute beginner at all programming. 
```
/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package primenumbers;

/**
 *
 * @author patrick
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        int primeCount = 1; //For 2
        int prime = 1;
        int printable = 1; //Lowest prime to print, then this number multiplied by the multiples of 10 will be printed
        if (printable == 1) {
            System.out.println("The 1st prime number is 2");
            printable*=10;
        }
        while (primeCount <= 10000000) {
            if (checkPrime(prime)) {
                primeCount++;
                if (primeCount == printable) {
                    System.out.println("The "+printable+"th prime number is "+prime);
                    printable *= 10;
                }
            }
            prime += 2;
        }
    }

    public static boolean checkPrime(int num) {
        double sqrt = Math.sqrt(num);
        if (num == 2)
                return true;
        if (num%2 == 0 && num != 2 || num == 1 )
            return false;
        for (int i = 3; i <= sqrt; i+=2) {
            if (num%i == 0) {
                return false;
            }
        }
        return true;
    }


}


```

Edit: I went too long without checking this thread, so these changes are later than they should be. I have incorporated the suggestions below.

---

### Post by lavinog on 2010-02-27
> **patrickaupperle said:**
> Although it is slow and almost embarrassing after all the multithreading and super quick ones, but here it is. I am an absolute beginner at all programming. 


You could speed it up by first checking if the number is even (num%2==0) and (num>2)
then iterate through (int i = 3; i <= Math.sqrt(num); i+=2)

That should almost half the iterations needed to determine if prime.

---

### Post by howlingmadhowie on 2010-02-27
another thing. although the jvm probably caches the result it may be worth calculating Math.sqrt(n) only once and assigning this value to a variable in checkPrime().

---

### Post by cprofitt on 2010-02-27
Here is the code I came up with prior to reading the thread:

[PHP]
#! /usr/bin/env python
# verify the place of a prime
# written by cprofitt 2/26/2010
# version .0.1
# The 1000th     prime number is 7919
# The 10000th    prime number is 104729
# The 100000th   prime number is 1299709
# The 1000000th  prime number is 15485863
# The 10000000th prime number is 179424673

import time

def erat_sieve(target_prime):
   if target_prime < 2:
      return []
   max = (target_prime - 1) / 2
   sieve = [True] * (max + 1)
   #loop up to square root
   for numx in range(int(target_prime ** 0.5) / 2):
      # check for prime
      if sieve[numx]:
         # unmark all odd multiples of the prime
         num = numx * 2 + 3
         sieve[numx+num:max:num] = [False] * ((max-numx-num-1)//num + 1)
   # create a list of primes up to target_prime
   return [2] + [numx * 2 + 3 for numx in range(max) if sieve[numx]]

def find_nth(number, nth):
    starttime = time.time()
    prime_set = erat_sieve(number)
    if len(prime_set) == nth:
        # test if number is prime
        if number in prime_set:
            print "true " + str(number) + " is the " + str(nth) + " prime."
        else:
            print "number is not a prime"
    else:
        print "false"
        
    stoptime = time.time()
    print 'Time to complete: %s secs' % (stoptime - starttime)
   

find_nth(7919, 1000)
find_nth(104729, 10000)
find_nth(1299709, 100000)
find_nth(15485863, 1000000)
find_nth(179424673, 10000000)
[/PHP]Here were my results (As you can see I timed each test individually to illustrate that the time becomes an issue with the last test)
-----

$ python nthprime.py
true 7919 is the 1000 prime.
[COLOR=RoyalBlue]Time to complete: 0.00105094909668 secs[/COLOR]
true 104729 is the 10000 prime.
[COLOR=RoyalBlue]Time to complete: 0.0118269920349 secs[/COLOR]
true 1299709 is the 100000 prime.
[COLOR=RoyalBlue]Time to complete: 0.13739490509 secs[/COLOR]
true 15485863 is the 1000000 prime.
[COLOR=RoyalBlue]Time to complete: 1.72376608849 secs[/COLOR]
true 179424673 is the 10000000 prime.
[COLOR=Red]Time to complete: 91.3069701195 secs[/COLOR]


-----
I would really like to cut the last one down... so I need to find a better piece of code I think... or approach this from a different angle.

---

### Post by cprofitt on 2010-02-27
I found a good example piece of code from this page - [http://zerovolt.com/?p=8](http://zerovolt.com/?p=8)

[PHP]
import time

# wheel code copyright zerovolt.com
'''
Copyright 2009 by zerovolt.com
This code is free for non-commercial purposes, in which case you can just leave this comment as a credit for my work.
If you need this code for commercial purposes, please contact me by sending an email to: info [at] zerovolt [dot] com.
'''

from math import ceil, sqrt

# small primes array
__smallp = ( 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97, 101, 103, 107, 109, 113, 127, 131, 137, 139, 149, 151, 157, 163, 167, 173, 179, 181, 191, 193, 197, 199, 211, 223, 227, 229, 233, 239, 241, 251, 257, 263, 269, 271, 277, 281, 283, 293, 307, 311, 313, 317, 331, 337, 347, 349, 353, 359, 367, 373, 379, 383, 389, 397, 401, 409, 419, 421, 431, 433, 439, 443, 449, 457, 461, 463, 467, 479, 487, 491, 499, 503, 509, 521, 523, 541, 547, 557, 563, 569, 571, 577, 587, 593, 599, 601, 607, 613, 617, 619, 631, 641, 643, 647, 653, 659, 661, 673, 677, 683, 691, 701, 709, 719, 727, 733, 739, 743, 751, 757, 761, 769, 773, 787, 797, 809, 811, 821, 823, 827, 829, 839, 853, 857, 859, 863, 877, 881, 883, 887, 907, 911, 919, 929, 937, 941, 947, 953, 967, 971, 977, 983, 991, 997)

def sieve_wheel_30(N):
    ''' Returns a list of primes <= N using wheel criterion 2*3*5 = 30 '''

    wheel = (2, 3, 5)
    const = 30
    if N < 2:
        return []
    if N <= const:
        pos = 0
        while __smallp[pos] <= N:
            pos += 1
        return list(__smallp[:pos])
    # make the offsets list
    offsets = (7, 11, 13, 17, 19, 23, 29, 1)
    # prepare the list
    p = [2, 3, 5]
    dim = 2 + N // const
    tk1  = [True] * dim
    tk7  = [True] * dim
    tk11 = [True] * dim
    tk13 = [True] * dim
    tk17 = [True] * dim
    tk19 = [True] * dim
    tk23 = [True] * dim
    tk29 = [True] * dim
    tk1[0] = False
    # help dictionary d
    # d[a , b] = c  ==> if I want to find the smallest useful multiple of (30*pos)+a
    # on tkc, then I need the index given by the product of [(30*pos)+a][(30*pos)+b]
    # in general. If b < a, I need [(30*pos)+a][(30*(pos+1))+b]
    d = {}
    for x in offsets:
        for y in offsets:
            res = (x*y) % const
            if res in offsets:
                d[(x, res)] = y
    # another help dictionary: gives tkx calling tmptk[x]
    tmptk = {1:tk1, 7:tk7, 11:tk11, 13:tk13, 17:tk17, 19:tk19, 23:tk23, 29:tk29}
    pos, prime, lastadded, stop = 0, 0, 0, int(ceil(sqrt(N)))
    # inner functions definition
    def del_mult(tk, start, step):
        for k in xrange(start, len(tk), step):
            tk[k] = False
    # end of inner functions definition
    cpos = const * pos
    while prime < stop:
        # 30k + 7
        if tk7[pos]:
            prime = cpos + 7
            p.append(prime)
            lastadded = 7
            for off in offsets:
                tmp = d[(7, off)]
                start = (pos + prime) if off == 7 else (prime * (const * (pos + 1 if tmp < 7 else 0) + tmp) )//const
                del_mult(tmptk[off], start, prime)
        # 30k + 11
        if tk11[pos]:
            prime = cpos + 11
            p.append(prime)
            lastadded = 11
            for off in offsets:
                tmp = d[(11, off)]
                start = (pos + prime) if off == 11 else (prime * (const * (pos + 1 if tmp < 11 else 0) + tmp) )//const
                del_mult(tmptk[off], start, prime)
        # 30k + 13
        if tk13[pos]:
            prime = cpos + 13
            p.append(prime)
            lastadded = 13
            for off in offsets:
                tmp = d[(13, off)]
                start = (pos + prime) if off == 13 else (prime * (const * (pos + 1 if tmp < 13 else 0) + tmp) )//const
                del_mult(tmptk[off], start, prime)
        # 30k + 17
        if tk17[pos]:
            prime = cpos + 17
            p.append(prime)
            lastadded = 17
            for off in offsets:
                tmp = d[(17, off)]
                start = (pos + prime) if off == 17 else (prime * (const * (pos + 1 if tmp < 17 else 0) + tmp) )//const
                del_mult(tmptk[off], start, prime)
        # 30k + 19
        if tk19[pos]:
            prime = cpos + 19
            p.append(prime)
            lastadded = 19
            for off in offsets:
                tmp = d[(19, off)]
                start = (pos + prime) if off == 19 else (prime * (const * (pos + 1 if tmp < 19 else 0) + tmp) )//const
                del_mult(tmptk[off], start, prime)
        # 30k + 23
        if tk23[pos]:
            prime = cpos + 23
            p.append(prime)
            lastadded = 23
            for off in offsets:
                tmp = d[(23, off)]
                start = (pos + prime) if off == 23 else (prime * (const * (pos + 1 if tmp < 23 else 0) + tmp) )//const
                del_mult(tmptk[off], start, prime)
        # 30k + 29
        if tk29[pos]:
            prime = cpos + 29
            p.append(prime)
            lastadded = 29
            for off in offsets:
                tmp = d[(29, off)]
                start = (pos + prime) if off == 29 else (prime * (const * (pos + 1 if tmp < 29 else 0) + tmp) )//const
                del_mult(tmptk[off], start, prime)
        # now we go back to top tk1, so we need to increase pos by 1
        pos += 1
        cpos = const * pos
        # 30k + 1
        if tk1[pos]:
            prime = cpos + 1
            p.append(prime)
            lastadded = 1
            for off in offsets:
                tmp = d[(1, off)]
                start = (pos + prime) if off == 1 else (prime * (const * pos + tmp) )//const
                del_mult(tmptk[off], start, prime)
    # time to add remaining primes
    # if lastadded == 1, remove last element and start adding them from tk1
    # this way we don't need an "if" within the last while
    if lastadded == 1:
        p.pop()
    # now complete for every other possible prime
    while pos < len(tk1):
        cpos = const * pos
        if tk1[pos]: p.append(cpos + 1)
        if tk7[pos]: p.append(cpos + 7)
        if tk11[pos]: p.append(cpos + 11)
        if tk13[pos]: p.append(cpos + 13)
        if tk17[pos]: p.append(cpos + 17)
        if tk19[pos]: p.append(cpos + 19)
        if tk23[pos]: p.append(cpos + 23)
        if tk29[pos]: p.append(cpos + 29)
        pos += 1
    # remove exceeding if present
    pos = len(p) - 1
    while p[pos] > N:
        pos -= 1
    if pos < len(p) - 1:
        del p[pos+1:]
    # return p list
    return p

# end wheel code from zerovolt.com

# code written by cprofitt - 2/27/2010

def find_nth(number, nth):
    starttime = time.time()
    prime_set = sieve_wheel_30(number)
    if len(prime_set) == nth:
        # test if number is prime
        if number in prime_set:
            print "true " + str(number) + " is the " + str(nth) + " prime."
        else:
            print "number is not a prime"
    else:
        print "false"
        
    stoptime = time.time()
    print 'Time to complete: %s secs' % (stoptime - starttime)


find_nth(7919, 1000)
find_nth(104729, 10000)
find_nth(1299709, 100000)
find_nth(15485863, 1000000)
find_nth(179424673, 10000000)

# end code written by cprofitt - 2/27/2010
[/PHP]

the results...

-----
$ python primes.py
true 7919 is the 1000 prime.
Time to complete: 0.00124597549438 secs
true 104729 is the 10000 prime.
Time to complete: 0.00755596160889 secs
true 1299709 is the 100000 prime.
Time to complete: 0.105724096298 secs
true 15485863 is the 1000000 prime.
Time to complete: 1.40095901489 secs
true 179424673 is the 10000000 prime.
Time to complete: 17.0449299812 secs
-----

A very nice improvement for the last prime; memory usage was also much better... now to study how this 'wheel' works.

---

### Post by YourMomsASmurph on 2010-02-27
[PHP]/*
YourMomsASmurph
*/

#include <cstdlib>
#include <iostream>
#include <cmath> // for sqrt

using namespace std;

//prototyope
bool prmChck(int n);
int prmCnt (int m);
void outpt (int prm, int chck);

int main()
{

    int prm(7919),chck(1000);

    outpt (prm, chck); // see function outpt.

    prm = 104729;
    chck *= 10;
    outpt (prm, chck);

    prm = 1299721;
    chck *= 10;
    outpt (prm, chck);

    prm = 15485857;
    chck *= 10;
    outpt (prm, chck);

    prm = 179424691;
    chck *= 10;
    outpt (prm, chck);




    cout << endl << endl;
    system("PAUSE");
    return 0;
}

int prmCnt (int m)
{
    int prmcntr;



    while (m > 1) {

        if (m%5 == 0)
                m -= 2;

        if (m%2 == 0)
            m--;

        if (prmChck(m))
            prmcntr++;

        m -= 2;
    }

    prmcntr +=2 ; //while loop does not count m=2 as a prime number. (it also skips 5)

    return prmcntr;
}

bool prmChck (int n)
{
    int div, chck(0);
    div=sqrt(n);

    if (div%2 == 0)
        div --;

    while (div > 1) {
        if ( n%div == 0) {
            chck = 1;
            div = 0;
        }

        div -= 2;
    }

//    if (n == 1) //function prmCnt doesnt allow n to be 1.
//        chck = 1;

    if (chck == 1)
        return false;
    else
        return true;




}

void outpt (int prm, int chck) {

    int count;

    cout <<"Checking ["<< prm << "= " << chck <<"th Prime number.] \n";

    count = prmCnt(prm); // counts the terms until prm number is reached. sets value to count.

    if ( count == chck) //checks if the number of terms counted is equal to the number of terms stated.
        cout << "True. \n\n";
    else{
        cout <<"False. \n";
        cout << prm << " is the " << count <<"th Prime number. \n \n";}

}

}



[/PHP]Fastest I can get it thus far

```
Process terminated with status 0 (20 minutes, 52 seconds)
```
Still working on it. (Considering it can be done in seconds.)

///How do you devote more sytem memory to the calculations? (C++)

---

### Post by snova on 2010-02-27
Ooh, this looks like fun.

Nothing special about the code; it's just an average Sieve of Eratosthenes implementation.

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define nr_targets 5

const int numbers[nr_targets][2] = {
    {1000, 7919},
    {10000, 104729},
    {100000, 1299721},
    {1000000, 15485857},
    {10000000, 179424691},
    };

int main() {
    printf("Initializing...\n");
    int target_idx = 0;
    int target_number = numbers[target_idx][0];
    int target_prime = numbers[target_idx][1];

    const int top_prime = numbers[nr_targets - 1][1];
    const int sieve_length = top_prime + 1;

    printf("Allocating sieve...\n");
    char* sieve = malloc(sieve_length);
    printf("Initializing sieve...\n");
    memset(sieve, 1, sieve_length);

    sieve[0] = 0;
    sieve[1] = 0;

    int have = 1;
    int prime = 2;

    printf("Starting.\n");
    while(prime * 2 < sieve_length) {
        int factor = 2;
        while(prime * factor < sieve_length) {
            sieve[prime * factor] = 0;
            factor += 1;
        }
        prime += 1;
        while(!sieve[prime]) {
            prime += 1;
        }

        have += 1;
        if(have == target_number) {
            if(prime == target_prime) {
                printf("Prime %i is correctly %i\n", have, prime);
            } else {
                printf("Prime %i is incorrectly %i\n", have, prime);
            }
            target_idx += 1;
            if(target_idx < nr_targets) {
                target_number = numbers[target_idx][0];
                target_prime = numbers[target_idx][1];
            } else {
                /* I think the loop is going to exit at this point anyway.
                 * Oh well.
                 */
                break;
            }
        }
    }

    return 0;
}
[/PHP]

Compiling and running on a relatively fast machine:

```

$ gcc sieve.c -o sieve -Wall -Wextra -Werror -O2 -mtune=native
$ time ./sieve
Initializing...
Allocating sieve...
Initializing sieve...
Starting.
Prime 1000 is correctly 7919
Prime 10000 is correctly 104729
Prime 100000 is incorrectly 1299709
Prime 1000000 is incorrectly 15485863
./sieve  7.13s user 0.06s system 99% cpu 7.194 total

```

---

### Post by lavinog on 2010-02-28
> **cprofitt said:**
> I found a good example piece of code from this page - [http://zerovolt.com/?p=8](http://zerovolt.com/?p=8)
...
A very nice improvement for the last prime; memory usage was also much better... now to study how this 'wheel' works.

I just looked at the wikipedia article...it makes sense.
It seems like the zerovolt code has a lot of redundant code that could have been replaced with a function.

I have a couple of ideas for implementing a wheel.

---

### Post by Hendrixski on 2010-03-02
> **cprofitt said:**
> Here is the code I came up with prior to reading the thread:


-----
I would really like to cut the last one down... so I need to find a better piece of code I think... or approach this from a different angle.


If you use Jython, you can make your sieve recursive:
```

import itertools as it
def sieve(num=it.count(2)):
    p=num.next()
    x=sieve(n for n in num if n%p)
    yield p
    while True: yield x.next()


```
You may run out of stackspace pretty quickly in regular python using recursion like this. You could use stackless python (if you don't mind incurring the wrath of python purist snobs, I personally think it's cool) and it'll recurse happily forever.

---

### Post by Lux Perpetua on 2010-03-02
> **snova said:**
> Ooh, this looks like fun.

Nothing special about the code; it's just an average Sieve of Eratosthenes implementation.

[PHP]
    ...
    while(prime * 2 < sieve_length) {
        int factor = 2;
        while(prime * factor < sieve_length) {
            sieve[prime * factor] = 0;
            factor += 1;
        }
        prime += 1;
        while(!sieve[prime]) {
            prime += 1;
        }
        ...
    }
[/PHP]There are some obvious, easy, and immediate improvements to be made here. First, you can stop iterating when prime*prime > sieve_length, or prime > sqrt(sieve_length). You can eliminate the multiplication *and* the square root by computing the square root once only and using the computed value from then on. (I actually didn't do that last thing in my program!)

Next, instead of starting to mark multiples of `prime' at 2*prime, you can start at prime*prime, since the smaller multiples have already been marked. This will save you time for large primes. 

Third, instead of using prime*factor to index your sieve and incrementing `factor' by one every time, you can use an auxiliary variable, say `m', starting at m=prime*prime and incrementing m by `prime' every iteration. This will eliminate a multiplication, which is great, since multiplication is slow. (The fact that one can implement the main loop of the sieve of Eratosthenes so easily with only comparisons and additions is one if its main selling points.)

---

### Post by snova on 2010-03-02
> **Lux Perpetua said:**
> First, you can stop iterating when prime*prime > sieve_length, or prime > sqrt(sieve_length).

I'm not sure why I did that. This was originally Python (while making sure it worked properly), and even that was originally based off of something else I'd done.

> You can eliminate the multiplication *and* the square root by computing the square root once only and using the computed value from then on. (I actually didn't do that last thing in my program!)

That's an interesting idea.

Replacing it with **prime < sieve_sqrt** saved several seconds, but I think it made very little difference compared to the first change.

> Next, instead of starting to mark multiples of `prime' at 2*prime, you can start at prime*prime, since the smaller multiples have already been marked. This will save you time for large primes.

Saved less than 0.3 seconds.

> Third, instead of using prime*factor to index your sieve and incrementing `factor' by one every time, you can use an auxiliary variable, say `m', starting at m=prime*prime and incrementing m by `prime' every iteration. This will eliminate a multiplication, which is great, since multiplication is slow. (The fact that one can implement the main loop of the sieve of Eratosthenes so easily with only comparisons and additions is one if its main selling points.)

That seems to have made very little noticeable difference- only two milliseconds (though consistently across a few repeated trials). Random jitter (this computer is otherwise idle) affects it just as much as this change.

By now the only multiplication left is in finding the first spot to mark (prime * prime), and I suppose you could eliminate that too if you wanted- but considering how slow multiplication doesn't seem to be, it's just little micro-optimizations.

[PHP]
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define nr_targets 5

const int numbers[nr_targets][2] = {
    {1000, 7919},
    {10000, 104729},
    {100000, 1299721},
    {1000000, 15485857},
    {10000000, 179424691},
    };

int main() {
    printf("Initializing...\n");
    int target_idx = 0;
    int target_number = numbers[target_idx][0];
    int target_prime = numbers[target_idx][1];

    const int top_prime = numbers[nr_targets - 1][1];
    const int sieve_length = top_prime + 1;
    const int sieve_sqrt = sqrt(sieve_length) + 1;

    printf("Allocating sieve...\n");
    char* sieve = malloc(sieve_length);
    printf("Initializing sieve...\n");
    memset(sieve, 1, sieve_length);

    sieve[0] = 0;
    sieve[1] = 0;

    int have = 1;
    int prime = 2;

    printf("Starting.\n");
    while(prime < sieve_sqrt) {
        int spot = prime * prime;
        while(spot < sieve_length) {
            sieve[spot] = 0;
            spot += prime;
        }
        prime += 1;
        while(!sieve[prime]) {
            prime += 1;
        }

        have += 1;
        if(have == target_number) {
            if(prime == target_prime) {
                printf("Prime %i is correctly %i\n", have, prime);
            } else {
                printf("Prime %i is incorrectly %i\n", have, prime);
            }
            target_idx += 1;
            if(target_idx < nr_targets) {
                target_number = numbers[target_idx][0];
                target_prime = numbers[target_idx][1];
            } else {
                /* I think the loop is going to exit at this point anyway.
                 * Oh well.
                 */
                break;
            }
        }
    }

    return 0;
}
[/PHP]

---

### Post by Lux Perpetua on 2010-03-03
> **snova said:**
> 
...

That seems to have made very little noticeable difference- only two milliseconds (though consistently across a few repeated trials). Random jitter (this computer is otherwise idle) affects it just as much as this change.Wow, you tried all of my suggestions! I admit that I didn't know exactly how much improvement you'd get out of each optimization. 

---------------------

Here's a rather different approach to the sieve of Eratosthenes which I implemented a while ago (about a year and a half). It answers the questions: (1) How do you implement the sieve of Eratosthenes without making a gigantic table of all integers up to a certain limit? (2) How do you compute the first N prime numbers without having to compute (or guess) an upper bound for the Nth prime number (e. g., as you would to make a table for the sieve of Eratosthenes)? 

The solution (which I did not invent) is pretty cool: you don't need a table at all. You have a counter M and a list of all the primes less than M, and you maintain that invariant as you increment M. To maintain the invariant when incrementing M, you have to determine if M itself is prime. To do this, you also maintain the invariant that each prime in the list knows its "next multiple," i. e., its lowest multiple that is at least M. Those multiples are used as keys in a priority queue, and we pop a prime/multiple pair (p, m) from the priority queue. If m=M, then M is obviously not prime, so we don't add M to our list of primes, and we update the "next multiples" of all primes whose "next multiples" were previously M, and we increment M. However, if m > M, then M must be prime. We thus add M to our list of primes, pair it with its first proper multiple (2*M) and add the pair to the priority queue, and we increment M. 

That sounds nothing like the sieve of Eratosthenes, but it is morally very similar: each prime is responsible for marking off its multiples. We just don't mark off all multiples of a given prime at the same time; we mark off composite numbers in order, but each one still gets marked once for each prime factor. Many of the tricks useful in the normal sieve can also be used here, such as wheel factorization (which I use). Unfortunately, maintaining the priority queue isn't free, and there's some additional overhead as well, so this program isn't really competitive with my previous one (it seems to be about 7 times as slow to compute prime #10,000,000). 

Here's the code. I just love how simple the main() function is, with a little help from operator overloading. :-) ```

#include <vector>
#include <iostream>
#include <cstdlib>
#include <cerrno>

class prime_sequence {
    struct sieve_val {
        unsigned int prime;
        unsigned int idx;
        unsigned int val;

        sieve_val(int p, int k, int n) :
            prime(p), idx(k), val(n)
        { }
    };
    
    std::vector<unsigned int> primes;
    std::vector<sieve_val> sieve;

    unsigned int W;
    unsigned int *wheel;

    unsigned int current;
    unsigned int idx;

    void sieve_swap(unsigned int j, unsigned int k) {
        sieve_val t = sieve[k];
        sieve[k] = sieve[j];
        sieve[j] = t;
    }

    void increment() {
        current += wheel[idx];
        ++idx;
        if (idx == W) idx = 0;
    }

    void update(sieve_val & v) {
        v.val += v.prime * wheel[v.idx];
        ++v.idx;
        if (v.idx == W) v.idx = 0;
    }

    unsigned int val(unsigned int k) {
        return sieve[k].val;
    }

    void fixdown() {
        unsigned int k = 0;
        unsigned int a = val(k);

        while (k + k + 2 < sieve.size()) {
            unsigned int b = val(k + k + 1);
            unsigned int c = val(k + k + 2);

            if (a < b && a < c) return;

            unsigned int j = k;

            if (b < c)
                k = k + k + 1;
            else
                k = k + k + 2;

            sieve_swap(j, k);
        }
     
        if (k + k + 1 < sieve.size() && a > val(k + k + 1))
            sieve_swap(k, k + k + 1);
    }

    void fixup() {
        unsigned int k = sieve.size() - 1;
        unsigned int a = val(k);

        while (k > 0) {
            unsigned int j = k;
            k = (k-1)>>1;

            if (a < val(k))
                sieve_swap(j, k);
            else
                break;
        }
    }

    void save() {
        primes.push_back(current);
        sieve.push_back(sieve_val(current, 0, current));
        update(sieve.back());
        fixup();
    }

    void next_prime() {
        do {
            increment();

            while (val(0) < current) {
                update(sieve[0]);
                fixdown();
            }
        } while (val(0) == current);

        save();
    }

public:
    prime_sequence(unsigned int h) : primes(h), W(1), current(1), idx(0) {
        if (h > 0) {
            prime_sequence seq(0);
            for (unsigned int k = 0; k < h; ++k) {
                primes[k] = seq[k];
            }
        }

        unsigned int P = 1;
        for (unsigned int k = 0; k < h; ++k) {
            P *= primes[k];
            W *= primes[k]-1;
        }

        char *table = new char[P];

        for (unsigned int k = 0; k < P; ++k) {
            table[k] = 0;
        }
        
        for (unsigned int k = 0; k < h; ++k) {
            unsigned int p = primes[k];
            for (unsigned int k = 0; k < P; k += p) {
                table[k] = -1;
            }
        }

        wheel = new unsigned int[W];

        unsigned int j = 0;
        for (unsigned int k = 0; k < P; ++k) {
            if (!table[k]) {
                wheel[j++] = k;
            }
        }

        delete [] table;

        unsigned int a = P + wheel[0];

        for (unsigned int k = 0; k < W-1; ++k) {
            wheel[k] = wheel[k+1] - wheel[k];
        }
        wheel[W-1] = a - wheel[W-1];

        increment();
        save();
    }

    ~prime_sequence() {
        delete [] wheel;
    }
    
    unsigned int operator [] (unsigned int k) {
        while (k >= primes.size()) next_prime();
        return primes[k];
    }
};

using namespace std;

int main(int argc, char **argv) {
    unsigned int h = 7;

    prime_sequence p(h);

    cout << "prime #1000 is " << p[999] << endl;
    cout << "prime #10000 is " << p[9999] << endl;
    cout << "prime #100000 is " << p[99999] << endl;
    cout << "prime #1000000 is " << p[999999] << endl;
    cout << "prime #10000000 is " << p[9999999] << endl;

    return 0;
}
```

---

### Post by cprofitt on 2010-03-05
When do these threads 'end'.

---

### Post by cprofitt on 2010-04-13
Is this thread going to have a 'winner'?

---

### Post by Bachstelze on 2010-05-01
Bumpity, my attempt at multithreading in Python:

[PHP]#!/usr/bin/env python3

import math
import sys
import threading

class SieveThread(threading.Thread):

    def __init__(self, n):
        threading.Thread.__init__(self, name=str(n))

        if type(n) is str:
            self.n = int(n[0])
        else:
            self.n = n

    def run(self):
        global SIEVE_SIZE
        global sieve
        global sem

        #print('Thread %s started.' % self.name)

        if self.n != 2:
            sieve[self.n] = True
            r = range(pow(self.n, 2), SIEVE_SIZE, self.n)
        else:
            if self.name == "2t":
                start = SIEVE_SIZE // 2
                if start % 2 == 1:
                    start += 1
                r = range(start, SIEVE_SIZE, 2)
            else:
                sieve[2] = True
                r = range(4, SIEVE_SIZE // 2, 2)

        for i in r:
            sieve[i] = False

        sem.release()
          

def next_prime():
    global SIEVE_SIZE
    global largest_prime_so_far
    global sieve
    
    n = largest_prime_so_far+1

    while n < SIEVE_SIZE and sieve[n] is not None:
        n += 1

    return n

def print_usage():
    print('Usage: sieve.py target [num threads]', file=sys.stderr)
    print('Default is 4 threads.')
    sys.exit(1)


##### MAIN PROGRAM #####

if len(sys.argv) not in [2, 3]:
    print_usage()
elif len(sys.argv) == 2:
    try:
        N = int(sys.argv[1])
        if N <= 0:
            raise ValueError
    except ValueError:
        print('Error: target must be a positive integer.')
        print_usage()
    NUMBER_OF_THREADS = 4
else:
    try:
        N = int(sys.argv[1])
        NUMBER_OF_THREADS = int(sys.argv[2])
        if N <= 0 or NUMBER_OF_THREADS <= 0:
            raise ValueError
    except ValueError:
        print('Error: targer and number of thread must be positive integers.')
        print_usage()

SIEVE_SIZE = math.ceil(N*math.log(N)+N*math.log(math.log(N)))

# Initialise the sieve
sieve = SIEVE_SIZE*[None]
sieve[0] = sieve[1] = False

# Used to control the number of threads
sem = threading.Semaphore(NUMBER_OF_THREADS)

# Create the two "two threads"
for i in ["2b", "2t"]:
    thread = SieveThread(i)
    thread.start()
    sem.acquire()

primes_so_far = 1
largest_prime_so_far = 2

# Main loop
while primes_so_far < N:
    largest_prime_so_far = next_prime()
    primes_so_far += 1
    if primes_so_far in [10, 100, 1000, 10000, 100000, 1000000, 10000000]:
        print('%sth prime is %s.' % (primes_so_far, largest_prime_so_far))
    if primes_so_far == N:
        break
    sem.acquire()
    thread = SieveThread(largest_prime_so_far)
    thread.start()
[/PHP]

```
firas@tsukino ~ % time ./sieve.py 1000000 4
10th prime is 29.
100th prime is 541.
1000th prime is 7919.
10000th prime is 104729.
100000th prime is 1299709.
1000000th prime is 15485863.
./sieve.py 1000000 4  166.60s user 110.07s system 132% cpu 3:28.55 total

```

Not so great, I must be doing something wrong...

*EDIT: I think the problem is that I'm spending too much time creating threads, since I'm creating one for every prime. I must find a way to just reuse the threads...*

---

### Post by Bachstelze on 2010-05-01
[PHP]#!/usr/bin/env python3

import math
import sys
import threading

class SieveThread(threading.Thread):

    def __init__(self):
        threading.Thread.__init__(self)

    def run(self):
        global N
        global SIEVE_SIZE
        global largest_prime_so_far
        global primes_so_far
        global sieve

        while primes_so_far[0] < N:
            primes_so_far[1].acquire()
            largest_prime_so_far[1].acquire()

            # Get the next unmarked number
            n = largest_prime_so_far[0]+1
            while n < SIEVE_SIZE and sieve[n] is not None:
                n += 1

            self.name = str(n)
            primes_so_far[0] += 1

            if primes_so_far[0] in [10, 100, 1000, 10000, 100000, 1000000, 10000000]:
                print('%sth prime is %s.' % (primes_so_far[0], n))

            largest_prime_so_far[0] = n
            primes_so_far[1].release()
            largest_prime_so_far[1].release()

            sieve[n] = True
            for i in range(pow(n, 2), SIEVE_SIZE, n):
                sieve[i] = False


def print_usage():
    print('Usage: sieve.py target [num threads]', file=sys.stderr)
    print('Default is 4 threads.')
    sys.exit(1)


##### MAIN PROGRAM #####

if len(sys.argv) not in [2, 3]:
    print_usage()
elif len(sys.argv) == 2:
    try:
        N = int(sys.argv[1])
        if N <= 0:
            raise ValueError
    except ValueError:
        print('Error: target must be a positive integer.')
        print_usage()
    NUMBER_OF_THREADS = 4
else:
    try:
        N = int(sys.argv[1])
        NUMBER_OF_THREADS = int(sys.argv[2])
        if N <= 0 or NUMBER_OF_THREADS <= 0:
            raise ValueError
    except ValueError:
        print('Error: targer and number of thread must be positive integers.')
        print_usage()

SIEVE_SIZE = math.ceil(N*math.log(N)+N*math.log(math.log(N)))+1

# Initialise the sieve
sieve = SIEVE_SIZE*[None]
sieve[0] = sieve[1] = False

# Those variables are in a list with their associated lock.
# When a thread wants to modify or access one of them, it must
# first aquire the lock, then do its business and release it.
primes_so_far = [0, threading.Lock()]
largest_prime_so_far = [1, threading.Lock()]

# Create the two "two threads"
#for i in ["2b", "2t"]:
#    thread = SieveThread(i)
#    thread.start()
#    if NUMBER_OF_THREADS == 1:
#        thread.join()

# Create the threads
for i in range(NUMBER_OF_THREADS):
    thread = SieveThread()
    thread.start()
[/PHP]

Much better:

```
firas@tsukino ~ % time ./sieve.py 1000000 4
10th prime is 29.
100th prime is 541.
1000th prime is 7919.
10000th prime is 104729.
100000th prime is 1299709.
1000000th prime is 15485863.
./sieve.py 1000000 4  28.65s user 14.67s system 127% cpu 34.087 total

```

---

