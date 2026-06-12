---
title: "what are sieving techniques"
date: 2010-10-22
forum: Programming Talk
---

### Post by c2tarun on 2010-10-22
hi friends.
i was trying to make program for prime numbers for pretty large numbers.
i was also trying to reduce its execution time. while reading on net i found this topic that use seiving techniques that can be used to reduce the execution time of the program to great extent.
but i am not able to understand what are these techniques.
can anyone please explain, a good manual of reference material will help too.


thanx

---

### Post by simeon87 on 2010-10-22
[Generating primes]("http://en.wikipedia.org/wiki/Generating_primes")

---

### Post by spurs21 on 2010-10-23
The Sieve of Eratosthenes basically works like this:

1) You draw all the integers 2,3,4, ..., N on a piece of paper.
2) You start off at 2 which is a known prime. Then you cross 4,6,8, and all other multiplies of 2 (other than 2 itself) off the sheet.
3) Once you're finished with that, move to the next number that's still not crossed off (which is the prime 3).
4) Now cross off 6,9,12,15,etc. (e.g., all multiples of 3 other than 3 itself).
5) Now move on to the next number not crossed off. Since 4 has been crossed off already, it is 5.
6) Cross off 10,15,20,etc. and move on to the next non-crossed off number. Since 6 has been crossed off, it is the prime 7.
7) Cross off 14,21,28, etc. and advance to the next number not crossed off. It will be the prime 11, since 8 was crossed off (as a multiple of 2), 9 was crossed off (as a multiple of 3), and 10 was crossed off (as a multiple of 2)

... and so on. When you're done, all the numbers you haven't crossed off the sheet of paper are primes.

---

### Post by c2tarun on 2010-10-23
can these seiving techniques be used only for finding prime numbers or they are for other problems too.???
by other problems i mean some different problem with different seiving algorithm

---

### Post by phrostbyte on 2010-10-23
Sieving is really the act of filtering. So yes any algorithm which starts with a some well defined input of objects and outputs a subset of those objects could be considered a sieving algorithm.

---

### Post by worksofcraft on 2010-10-23
> **spurs21 said:**
> The Sieve of Eratosthenes basically works like this:

1) You draw all the integers 2,3,4, ..., N on a piece of paper.
2) You start off at 2 which is a known prime. Then you cross 4,6,8, and all other multiplies of 2 (other than 2 itself) off the sheet.
3) Once you're finished with that, move to the next number that's still not crossed off (which is the prime 3).
4) Now cross off 6,9,12,15,etc. (e.g., all multiples of 3 other than 3 itself).
5) Now move on to the next number not crossed off. Since 4 has been crossed off already, it is 5.
6) Cross off 10,15,20,etc. and move on to the next non-crossed off number. Since 6 has been crossed off, it is the prime 7.
7) Cross off 14,21,28, etc. and advance to the next number not crossed off. It will be the prime 11, since 8 was crossed off (as a multiple of 2), 9 was crossed off (as a multiple of 3), and 10 was crossed off (as a multiple of 2)

... and so on. When you're done, all the numbers you haven't crossed off the sheet of paper are primes.

The question is whether it takes longer to "cross off" the ones you don't want than to process them unnecessarily.

When it comes to checking if a number is prime it is easy enough to skip the even numbers and not too hard to make it jump over the ones that are divisible by 3 but from then on I suspect you are into deminishing returns on trying to remove them as opposed to simply doing the division.

---

### Post by ladasky on 2010-10-23
> **worksofcraft said:**
> The question is whether it takes longer to "cross off" the ones you don't want than to process them unnecessarily.

When it comes to checking if a number is prime it is easy enough to skip the even numbers and not too hard to make it jump over the ones that are divisible by 3 but from then on I suspect you are into deminishing returns on trying to remove them as opposed to simply doing the division.

I had this same conversation with a mathematician friend about seven years ago.  He said that the Sieve of Eratosthenes could be made to run blindingly fast.  The alternate method, trial division, could not compete.

You need more memory to run the Sieve.

---

### Post by worksofcraft on 2010-10-23
> **ladasky said:**
> I had this same conversation with a mathematician friend about seven years ago.  He said that the Sieve of Eratosthenes could be made to run blindingly fast.  The alternate method, trial division, could not compete.

You need more memory to run the Sieve.

Yes I heard that too, but IDK... if anyone is writing a sieve algorithm for primes... we could race it against the following dumb version... but obviously would have to run both on the same computer... well here is the dumb version:
[php]
#include <stdio.h>
#include <time.h>
#include <math.h>

unsigned long Prime;

inline void test_prime(unsigned long Num) {
	// won't be divisible by anything greater than it's square root
	unsigned Max = ceil(sqrt((double) Num));
	unsigned register Test = 5;
	while (Test <= Max) {
		if (!(Num % Test)) return;
		Test += 2;
		if (!(Num % Test)) return;
		Test += 4;
	}
	Prime = Num;
//	printf("prime=%lu\n", Num);
}
		

int main() {
	unsigned long Num = 5;

	const unsigned Seconds = 60; // time to run for
	clock_t Finish = clock () + Seconds * CLOCKS_PER_SEC ;

 	while (clock() < Finish) {
		test_prime(Num);
		Num += 2; // both even and multiple of 3 skipped
		test_prime(Num);
		Num += 4; // skip even and a multiple of 3 and another even
	}
	printf("Largest prime found in %u seconds: %lu\n", Seconds, Prime);
}
[/php]
and here is the output on my computer:
```

$> ./a.out
Largest prime found in 60 seconds: 31571063
# and if you compile with optimization and replace the
# unsigned long with an ordinary unsigned int you get:
$> g++ -O3 primes.cc
$> ./a.out
Largest prime found in 60 seconds: 33028453

```

so not a huge difference

---

### Post by worksofcraft on 2010-10-23
Just for those interested in how effective it is to actually put some thought into designing efficient algorithms I found an [implementation of the Sieve of Atkin]("http://cr.yp.to/primegen.html") in C and that claims:

"It generates the 50847534 primes up to 1000000000 in just 8 seconds on a Pentium II-350"

So it would be **an awful LOT faster** than the dumb version... however it wouldn't build on my computer :(
```

$> make setup check
...
./makelib str.a str_len.o byte_copy.o byte_cr.o
./load auto-str substdio.a error.a str.a 
collect2: ld terminated with signal 11 [Segmentation fault]
/usr/bin/ld: make: *** [auto-str] Error 1

```

update: ok fixed that and on my computer it produces:
```

50847534 primes up to 1000000000.
Timings are in ticks. Nanoseconds per tick: approximately 0.452484.
Overall seconds: approximately 1.064862.

```

OTOH the dumb version has been running for an hour and not finished yet. SO why is that you may wonder?

The Seive algorithm gets faster as the numbers get bigger O(N/log log N) whereas the dumb version gets slower O(N*sqrt(N))

---

