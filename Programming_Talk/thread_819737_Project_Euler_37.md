---
title: "Project Euler: 37"
date: 2008-06-05
forum: Programming Talk
---

### Post by robheus on 2008-06-05
[Project Euler]("http://projecteuler.net") has some very challenging mathematical problems which can be solved using your programming skills.
Thus far I managed to solve 23 (out of a total of 196 problems) of them.

But on some problems I get stuck. Like this one, I'm currently trying to solve, Euler problem 37.
This is about prime numbers with the property that any number of digits to the left OR to the right of the digit representation (base 10) can be left out, and still yield a prime.
There are supposed to be exactly 11 such primes.
I could find 10 of them most easily, and also I can find many other primes that are EITHER left truncatable OR right truncatable, but I am missing out on the 11-th prime that is BOTH left and right truncatable.

```

truncatable: 13		left      
truncatable: 17		left      
truncatable: 31		     right
truncatable: 37		left right
truncatable: 53		left right
truncatable: 59		     right
truncatable: 71		     right
truncatable: 73		left right
truncatable: 79		     right
truncatable: 97		left      
truncatable: 113		left      
truncatable: 137		left      
truncatable: 173		left      
truncatable: 197		left      
truncatable: 311		     right
truncatable: 313		left right
truncatable: 317		left right
truncatable: 337		left      
truncatable: 353		left      
truncatable: 373		left right
truncatable: 379		     right
truncatable: 397		left      
truncatable: 593		     right
truncatable: 599		     right
truncatable: 719		     right
truncatable: 733		     right
truncatable: 739		     right
truncatable: 773		left      
truncatable: 797		left right
truncatable: 937		left      
truncatable: 953		left      
truncatable: 997		left      
truncatable: 1373		left      
truncatable: 1997		left      
truncatable: 3119		     right
truncatable: 3137		left right
truncatable: 3313		left      
truncatable: 3373		left      
truncatable: 3733		     right
truncatable: 3739		     right
truncatable: 3793		     right
truncatable: 3797		left right
truncatable: 5113		left      
truncatable: 5197		left      
truncatable: 5939		     right
truncatable: 5953		left      
truncatable: 7193		     right
truncatable: 7331		     right
truncatable: 7333		     right
truncatable: 7393		     right
truncatable: 7937		left      
truncatable: 9137		left      
truncatable: 9173		left      
truncatable: 9337		left      
truncatable: 9397		left      
truncatable: 13313		left      
truncatable: 31193		     right
truncatable: 31379		     right
truncatable: 33797		left      
truncatable: 37337		     right
truncatable: 37339		     right
truncatable: 37397		     right
truncatable: 39397		left      
truncatable: 59393		     right
truncatable: 59399		     right
truncatable: 71933		     right
truncatable: 73331		     right
truncatable: 73939		     right
truncatable: 79337		left      
truncatable: 79397		left      
truncatable: 91373		left      
truncatable: 91997		left      
truncatable: 99137		left      
truncatable: 99173		left      
truncatable: 99397		left      
truncatable: 139397		left      
truncatable: 373379		     right
truncatable: 373393		     right
truncatable: 379397		left      
truncatable: 391373		left      
truncatable: 399137		left      
truncatable: 399173		left      
truncatable: 513313		left      
truncatable: 593933		     right
truncatable: 593993		     right
truncatable: 719333		     right
truncatable: 739391		     right
truncatable: 739393		     right
truncatable: 739397		left right
truncatable: 739399		     right
truncatable: 933797		left      
truncatable: 979337		left      
truncatable: 3399173		left      
truncatable: 3513313		left      
truncatable: 3733799		     right
truncatable: 3739397		left      
truncatable: 5379397		left      
truncatable: 5939333		     right
truncatable: 7393913		     right
truncatable: 7393931		     right
truncatable: 7393933		     right
truncatable: 9139397		left      
truncatable: 9391373		left      
truncatable: 9979337		left      
truncatable: 33739397		left      
truncatable: 37337999		     right
truncatable: 39979337		left      
truncatable: 59393339		     right
truncatable: 73939133		     right
truncatable: 99979337		left      
truncatable: 933739397		left 

```

The approach I took was brute force (looping through all integers), although I set up a table for referring to prime values for performance reasons.

Here's my code:
```

/* euler37.c
 *
 * 
 * The number 3797 has an interesting property. Being prime itself, it is possible to continuously remove digits from
 * left to right, and remain prime at each stage: 3797, 797, 97, and 7. Similarly we can work from right to left: 3797,
 * 379, 37, and 3.
 *
 * Find the sum of the only eleven primes that are both truncatable from left to right and right to left.
 *
 * NOTE: 2, 3, 5, and 7 are not considered to be truncatable primes.
 *
 * Answer:
 *
 * See:
 * http://projecteuler.net/index.php?section=problems&id=37
 */

#include <stdio.h>
#include <string.h>

#define true		1
#define	false		0

typedef unsigned long long int number;
#define FORMAT_SPECIFIER	"%lld"

#define USE_TABLE

#ifdef USE_TABLE

#define min(a,b)		((a)<(b)?(a):(b))
#define map(n)			((n-11)/2)

#define TABLE_SIZE		100000000

enum prime {
	UNKNOWN
,	PRIME
,	NOT_PRIME
};

char table[TABLE_SIZE];

#endif


int isprime(number test)
{
	register number i;
	register number n = test;

    if (n < 2) 				return false;
	else if (n < 4)			return true;
	else if (n % 2 == 0) 	return false;
	else if (n < 9)			return true;
	else if (n % 3 == 0)	return false;
#ifdef USE_TABLE
	else if (map(n) < TABLE_SIZE)
		switch (table[map(n)])
		{
			case PRIME: 	return true;
			case NOT_PRIME:	return false;
		}
#endif
	for (i = 5; i * i <= n; i += 6)
	{
		if (n % i == 0)
		{
#ifdef USE_TABLE
			if (map(n) < TABLE_SIZE)	table[map(n)] = NOT_PRIME;
#endif
			return false;
		}
		else if (n % (i + 2) == 0)
		{
#ifdef USE_TABLE
			if (map(n) < TABLE_SIZE)	table[map(n)] = NOT_PRIME;
#endif
			return false;
		}
	}
#ifdef USE_TABLE
	if (map(n) < TABLE_SIZE)	table[map(n)] = PRIME;
#endif
	return true;
}


char buf[128];

int count_digits(number test, int *valid)
{
	register int i;
	int len, v=true;
	sprintf(buf, FORMAT_SPECIFIER, test);
	len=strlen(buf);
	if (len>1)
		for (i=0;v&&i<len;i++)
			if (buf[i]=='0'||buf[i]=='2'||buf[i]=='4'||buf[i]=='6'||buf[i]=='8')
				v=false;
	*valid=v;
	return len;
}

number truncate_left(number num, int trunc)
{
	long int n;
	int len;

	if (trunc==0) return num;
	sprintf(buf, FORMAT_SPECIFIER, num);
	len = strlen(buf);
	if (trunc>=len) return (number)0;
	n= atoll(&buf[trunc]);
	return n;
}

number truncate_right(number num, int trunc)
{
	number n;
	int len;

	if (trunc==0) return num;
	sprintf(buf, FORMAT_SPECIFIER, num);
	len = strlen(buf);
	if (trunc>=len) return (number)0;
	buf[len-trunc]='\0';
	n= atoll(buf);
	return n;
}

int main(int argc, char *argv[])
{
	register number i;
	int digits, k, valid, left_truncatable, right_truncatable;

#ifdef USE_TABLE
	memset(table,UNKNOWN,TABLE_SIZE);
#endif

	for (i = 11; ; i += 2)
	{
		if (i % 3)
		{
			digits=count_digits(i,&valid);
	
			if (valid)
				if (isprime(i))
				{
					for (k=1,left_truncatable=true;left_truncatable&&k<digits;k++)
						left_truncatable=isprime(truncate_left(i,k));

					for (k=1,right_truncatable=true;right_truncatable&&k<digits;k++)
						right_truncatable=isprime(truncate_right(i,k));
		
					if (left_truncatable || right_truncatable)
						printf("truncatable: " FORMAT_SPECIFIER "\t\t%s %s\n", i, left_truncatable ? "left" : "    ", right_truncatable ? "right" : "     ");
				}
		}
	}

	return 0;
}

```

But I suppose the algorithm can be much approved when one notices that for finding a new truncatable prime in the range 10^n .. 10^n+1, this has to be a left/right truncatable prime already found in the range 10^n-1 .. 10^n by testing if new formed numbers by adding 1,3,5,7,9 on the left side or right side are prime.

---

### Post by robheus on 2008-06-05
Already found the solution: for some reason the first left/right truncatable prime was not generated by this algorithm, so all 11 numbers are there:
23
37
53
73
313
317
373
797
3137
3797
739397

---

### Post by Lau_of_DK on 2008-06-06
Hey,


It would be sweet if you marked the thread as solved.


/Lau

---

