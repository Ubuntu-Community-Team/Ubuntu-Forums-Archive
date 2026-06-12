---
title: "List Perfect Numbers(C++)"
date: 2007-07-11
forum: Programming Talk
---

### Post by navneeth on 2007-07-11
This is an utterly simple program, but for some reason unknown to me, this does not work properly.

```

//This program lists all the perfect numbers less than a given positive integer(user input)

#include<iostream>

using namespace std;

main()
{

 int n,m,i,sum=1;

 cout << "List all the perfect numbers less than: ";
 cin >> m;

 for(n=2;n<m;n++)
 {
   for(i=n-1;i>1;i--)
   { 
      if(n%i == 0)
      sum += i; 
   }

    if(sum == n)
    cout << n <<endl;   
 }   
 
}

```

I use the GNU g++ compiler v4.1.2. It compiles fine, but when I execute and give the input, I get the back shell prompt. I must add that the second for loop works(i.e., when I test if a given number is perfect or not, or in other words, a fixed n), but that's not what I want here. 

Thanks for any help.

---

### Post by GeneralZod on 2007-07-11
Is m being read in correctly? Should "sum" not be reset to 1 for each n?

---

### Post by rodo-&gt;dave on 2007-07-11
here is mine:

```

//This program lists all the perfect numbers less than a given positive integer(user input)

#include <stdio.h>
#include <math.h>

int main (int argc, char **argv)
{
	int n;
	int max;
	int output;

	if (argc < 2) {
		printf("usage: %s number\n", argv[0]);
		return(-1);
	}

	max = atoi(argv[1]);

	// using the formula 2^n-1 (2^n -1)
	for (n = 2; n < max; n++) {
		output = pow(2, n-1);
		output *= (pow(2, n) - 1);

		printf("%d\n", output);
	}
}

```

Not exactly what you want but output gives
$ perfect_num 10
6
28
120
496
2016
8128
32640
130816
$

I got the formula here:
[http://en.wikipedia.org/wiki/Perfect_number](http://en.wikipedia.org/wiki/Perfect_number)

---

### Post by navneeth on 2007-07-11
> **GeneralZod said:**
> Is m being read in correctly? Should "sum" not be reset to 1 for each n?

Exactly. Thank you. :)

---

### Post by vexorian on 2007-07-11
I just felt the urge to request you to use the O(sqrt(n)) solution... ... sorry.

```

//This program lists all the perfect numbers less than a given positive integer(user input)

#include<iostream>
#include<cmath>

using namespace std;

main()
{

 int n,m,i,sum=1;

 cout << "List all the perfect numbers less than: ";
 cin >> m;

 for(n=2;n<m;n++)
 {
   sum=1;
   int q=sqrt(p);
      
   for(i=2;i<=q;i++)
   { 
         if(n%i == 0)
        {
             sum += n/i +  i; 
             if(sum>n) break;
        }
   }

    if(sum == n)
    cout << n <<endl;   
 }   
 
}
```

---

### Post by hod139 on 2007-07-11
> **rodo->dave said:**
> here is mine:

<snip>
Not exactly what you want but output gives
$ perfect_num 10
6
28
120
496
2016
8128
32640
130816
$

I got the formula here:
[http://en.wikipedia.org/wiki/Perfect_number](http://en.wikipedia.org/wiki/Perfect_number)

This code is wrong.  The first 4 perfect numbers are:
6
28
496
8128

You misunderstood the formula provided by wikipedia.  All perfect numbers have the form: 2^*(n*&#8722;1)(2^*n* &#8722; 1), however, not all 2^(*n*&#8722;1)(2^*n* &#8722; 1) are perfect numbers.  Only when 2*^n* &#8722; 1 is prime, is the number a perfect number.  Values of *n* for which 2^*n* &#8722; 1 is prime are known as [Mersenne primes.]("http://en.wikipedia.org/wiki/Mersenne_prime")

---

### Post by rodo-&gt;dave on 2007-07-11
> **hod139 said:**
> This code is wrong.  The first 4 perfect numbers are:
6
28
496
8128

You misunderstood the formula provided by wikipedia.  All perfect numbers have the form: 2^*(n*&#8722;1)(2^*n* &#8722; 1), however, not all 2^(*n*&#8722;1)(2^*n* &#8722; 1) are perfect numbers.  Only when 2*^n* &#8722; 1 is prime, is the number a perfect number.  Values of *n* for which 2^*n* &#8722; 1 is prime are known as [Mersenne primes.]("http://en.wikipedia.org/wiki/Mersenne_prime")

Yes, you are correct; in the time between posts I looked at the wiki article more closely and I changed my code only do the calc if the number was prime.. .which I believe is correct now:

$ perfect_num 12
6
28
496
8128
2096128
$

And Just in case anybody cares:
```

#include <stdio.h>
#include <math.h>

int is_prime(int d);


int main (int argc, char **argv)
{
	int n;
	int max;
	double output;

	if (argc < 2) {
		printf("usage: %s number\n", argv[0]);
		return(-1);
	}

	max = atoi(argv[1]);

	// using the formula 2^n-1 (2^n -1)
	for (n = 2; n < max; n++) {
		if (is_prime(n)) {
			output = pow(2, n-1);
			output *= (pow(2, n) - 1);

			printf("%.0f\n", output);
		}
	}

                     return(0);
}

int is_prime(int d)
{
	int is_prime = 1;
	int n;
	

	for (n = 2; n < d; n++) {
		if ((d % n) == 0) {
			is_prime = 0;
			break;
		}
	}

	return(is_prime);
}

```
Thanks! Enjoyed the topic (so far).. I had never done anything with 'perfect numbers' before so this is my first exposure.

---

### Post by rodo-&gt;dave on 2007-07-11
Well, it appears that my fifth 'perfect number' is not perfect afterall :(
should be 33550336

solution: check if "(pow(2, n) - 1)" is prime :)

output is now:
$ perfect_num 18
6
28
496
8128
33550336
8589869056
$

which agrees with the article

---

### Post by hod139 on 2007-07-11
I modified your isPrime test, which doesn't seem correct.  In fact, we are looking for Mersenne primes and there are only 44 known, so it is easiest to simply build a lookup table.  The modified code is below.

```

#include <cstdio>
#include <cmath>
#include <map>

// global map of known mersenne primes
std::map<int, bool> knownMersennePrimes;

// this is only first 10 of known 44
void initMap(){
  knownMersennePrimes[2] = true;
  knownMersennePrimes[3] = true;
  knownMersennePrimes[5] = true;
  knownMersennePrimes[7] = true;
  knownMersennePrimes[13] = true;
  knownMersennePrimes[17] = true;
  knownMersennePrimes[19] = true;
  knownMersennePrimes[31] = true;
  knownMersennePrimes[61] = true;
  knownMersennePrimes[89] = true;
}

bool isMersennePrime(int d)
{
    return knownMersennePrimes[d];
}

int main (int argc, char **argv)
{
    if (argc < 2) {
        printf("usage: %s number\n", argv[0]);
        return(-1);
    }

    int max = atoi(argv[1]);

    // create the map of known mersenne primes
    initMap();

    // using the formula 2^n-1 (2^n -1)
    double output;
    for (int n = 2; n < max; ++n) {
        if (isMersennePrime(n)) {
            output = pow(2, n-1);
            output *= (pow(2, n) - 1);

            printf("%.0f\n", output);
        }
    }

   return(0);
}

```Now, running 
```

perfect_num 90

```produces:
```

6
28
496
8128
33550336
8589869056
137438691328
2305843008139952128
2658455991569831745807614120560689152
191561942608236107294793378393788647952342390272950272

```The reported number of perfect numbers is correct at 10, however the last two are not correct since we overflowed the double value.  They are close though.  The last two should have been:
2658455991569831744654692615953842176, and 

191561942608236107294793378084303638130997321548169216
[B]
Edit:[/B] I turned your code into C++ so I could use the std::map

---

### Post by rodo-&gt;dave on 2007-07-11
cool. Good job!

---

