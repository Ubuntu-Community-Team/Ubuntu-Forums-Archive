---
title: "Fast algorithm to find prime numbers"
date: 2012-04-20
forum: Programming Talk
---

### Post by DaviesX on 2012-04-20
Is that any fast algorithm to find all prime numbers that are less than n ?

---

### Post by davetv on 2012-04-21
(1) Initialise result list with 2
(2) Loop through all values from 3 to n-1 stepping by 2
(3) Apply the Sieve of Atkin to determine if prime

[http://en.wikipedia.org/wiki/Sieve_of_Atkin](http://en.wikipedia.org/wiki/Sieve_of_Atkin)

[http://en.wikipedia.org/wiki/Square-free_integer](http://en.wikipedia.org/wiki/Square-free_integer)

Thats the fastest way I know.

---

### Post by DaviesX on 2012-04-21
Can you please implement it with c language ?

Thank you

---

### Post by davetv on 2012-04-21
I would (might take an hour to write and test) ... but this sounds suspiciously like an assignment.

I know you know maths, time to test out your own c skills. 

:)

---

### Post by r-senior on 2012-04-21
Atkin is fast, but I think it's worth starting off with [Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) to get a feel for what's going on and then bring in the optimisations of Atkin.

---

### Post by DaviesX on 2012-04-21
> **davetv said:**
> I would (might take an hour to write and test) ... but this sounds suspiciously like an assignment.

I know you know maths, time to test out your own c skills. 

:)

It's not an assignment, instead, it's a question in programming competition. I want to participate a competition year or two later, is that possible ? Because I want to get scholarship for college ! :)

---

### Post by DaviesX on 2012-04-21
> **r-senior said:**
> Atkin is fast, but I think it's worth starting off with [Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes) to get a feel for what's going on and then bring in the optimisations of Atkin.

Thank you, I'm trying to achieve this one. (looks clear ^_^)

---

### Post by DaviesX on 2012-04-21
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <time.h>

int GetPrime ( int *primeSet, int upperLimit );

int main ( void )
{
    // The lower limit is 2 by default, and variable bounder is the upper limit
    int bounder;
    printf ( "Please enter the bounder of the searching rang\n" );
    scanf ( "%d", &bounder );
    getchar ();
    int *prime = (int*)malloc ( sizeof ( int )*(bounder + 1) );

    double start = clock ()/CLOCKS_PER_SEC;
    int numberPrimes = GetPrime ( prime, bounder );
    double end = clock ()/CLOCKS_PER_SEC;

    double interval = end - start;
    printf ( "%f\n", interval );
    getchar ();

    // Print out all the prime number found
    for ( int i = 0; i < numberPrimes; i++ )
    {
        printf ( "%d ", prime[i] );

    }// End For ( Each found )

    free ( prime );
    return 0;

}// End Function

int GetPrime ( int *primeSet, int upperLimit )
{
    // A list use to determine whether the subscript is a prime number
    // And it holds odd numbers only, for example, isPrime[1] means whether 3 is a prime number,
    // isPrime[2] means whether 5 is a prime number
    int *&isPrime = primeSet;
    for ( int i = 0; i <= (upperLimit >> 1); i++ )		// Does not count 0, 1, 2
    {
        isPrime[i] = true;

    }// End For

    // Then we filter out all numbers that is not a prime number
    // When doing this, never takes even numbers into account
    // And there is no need analyze the numbers which are greater than sqrt ( upperLimit )
    // Because those are repeating work
    const int end = sqrt ( upperLimit );
    for ( int i = 3; i <= end; i += 2 )
    {
        if ( isPrime[i >> 1] )
        {
            // When a number is a combination of two or more prime number must
            // Be a composite number
            for ( int composite = 3; i*composite <= upperLimit; composite += 2 )
            {
                isPrime[(i*composite) >> 1] = false;

            }// End For ( Each predictable composite )

        }// End If ( Can be used for fitlering )

    }// End For

    // Store back the result in term of a set
    int i, j;
    for ( i = 1, j = 1; j <= (upperLimit >> 1) - 1; j++ )
    {
        if ( isPrime[j] )
        {
            primeSet[i] = (j << 1) + 1;
            i++;

        }// End If ( if it is a prime number )

    }// End For

    // Can not forget that 1 + 1 question ^_^
    primeSet[0] = 2;

    return i;

}// End Function

```

I have made this code, but I don't know if it is fast. It need 10 seconds to find out all the prime numbers less than 200,000,000 on my Atom netbook.

I made several comments in the code, if there is any problems, please tell me. Thank you

---

### Post by DaviesX on 2012-04-21
Then I change the code a little bit, hoping it would be faster. I does when N < 10,000,000, but it's even 1s slower when N < 100,000,000

And here is the code
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <time.h>

int GetPrime ( int *primeSet, int upperLimit );

int main ( void )
{
    // The lower limit is 2 by default, and variable bounder is the upper limit
    int bounder;
    printf ( "Please enter the bounder of the searching range\n" );
    scanf ( "%d", &bounder );
    getchar ();
    int *prime = (int*)malloc ( sizeof ( int )*(bounder + 1) );

    double start = clock ()/CLOCKS_PER_SEC;
    int numberPrimes = GetPrime ( prime, bounder );
    double end = clock ()/CLOCKS_PER_SEC;

    double interval = end - start;
    printf ( "%f\n", interval );
    getchar ();

    // Print out all the prime number found
    for ( int i = 0; i < numberPrimes; i++ )
    {
        printf ( "%d ", prime[i] );

    }// End For ( Each found )

    free ( prime );
    return 0;

}// End Function

int GetPrime ( int *primeSet, int upperLimit )
{
    // A list use to determine whether the subscript is a prime number
    // And it holds odd numbers only
    int *&isPrime = primeSet;
    for ( int i = 3; i <= upperLimit; i += 2 )		// Does not count 0, 1, 2
    {
        isPrime[i] = true;

    }// End For

    // Then we filter out all numbers that is not a prime number
    // When doing this, never takes even numbers into account
    // And there is no need analyze the numbers which are greater than sqrt ( upperLimit )
    // Because those are repeating work
    const int end = sqrt ( upperLimit );
    for ( int i = 3; i <= end; i += 2 )
    {
        if ( isPrime[i] )
        {
            // When a number is a combination of two or more prime number must
            // Be a composite number
            for ( int composite = 3; i*composite <= upperLimit; composite += 2 )
            {
                isPrime[i*composite] = false;

            }// End For ( Each predictable composite )

        }// End If ( Can be used for fitlering )

    }// End For

    // Store back the result in term of a set
    int i, j;
    for ( i = 1, j = 3; j <= upperLimit; j += 2 )
    {
        if ( isPrime[j] )
        {
            primeSet[i] = j;
            i++;

        }// End If ( if it is a prime number )

    }// End For

    // Can not forget that 1 + 1 question ^_^
    primeSet[0] = 2;

    return i;

}// End Function

```

---

### Post by DaviesX on 2012-04-21
Finally, I made this code. I think I have learnt a from implementing this algorithm. I have never thought about using a large bunch of memory would consume that much (almost) 50%. But I don't know why the access speed slows down a lot when using a big block of heap memory. I guess that may because heap memory is discontinuous, isn't it ?
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <time.h>

int GetPrime ( int **primeSet, int upperLimit );
bool *isPrime = 0;

int main ( void )
{
    // The lower limit is 2 by default, and variable bounder is the upper limit
    int *prime, bounder;
    printf ( "Please enter the bounder of the searching range\n" );
    scanf ( "%d", &bounder );
    getchar ();
    isPrime = (bool*)malloc ( (bounder + 1) >> 1 );

    double start = clock ()/(double)CLOCKS_PER_SEC;
    int numberPrimes = GetPrime ( &prime, bounder );
    double end = clock ()/(double)CLOCKS_PER_SEC;

    double interval = end - start;
    printf ( "%f\n", interval );

    int printOut = 0;
    printf ( "Have everything print out ?\n" );
    printf ( "<0> No\n" );
    printf ( "<1> To file\n" );
    printf ( "<2> Display\n" );
    scanf ( "%d", &printOut );

	if ( printOut == 1 )
	{
		FILE *file = fopen ( "Test", "w+" );

		// Print out all the prime number found
		for ( int i = 0; i < numberPrimes; i++ )
		{
			fprintf ( file, "%d ", prime[i] );

		}// End For ( Each found )

		fclose ( file );
	}
	else if ( printOut == 2 )
	{
		// Print out all the prime number found
		for ( int i = 0; i < numberPrimes; i++ )
		{
			printf ( "%d ", prime[i] );

		}// End For ( Each found )

	}// End If

	free ( isPrime );
    free ( prime );
    return 0;

}// End Function

int GetPrime ( int **primeSet, int upperLimit )
{
    // A list use to determine whether the subscript is a prime number
    // And it holds odd numbers only, for example, isPrime[1] means whether 3 is a prime number,
    // isPrime[2] means whether 5 is a prime number
    for ( int i = 0; i <= (upperLimit >> 1); i++ )		// Does not count 0, 1, 2
    {
        isPrime[i] = true;

    }// End For

    // Then we filter out all numbers that is not a prime number
    // When doing this, never takes even numbers into account
    // And there is no need analyze the numbers which are greater than sqrt ( upperLimit )
    // Because those are repeating work
    int end = (int)sqrtf ( upperLimit );
    for ( int i = 3; i <= end; i += 2 )
    {
        if ( isPrime[i >> 1] )
        {
            // When a number is a combination of two or more prime number must
            // Be a composite number
            for ( int composite = 3; i*composite <= upperLimit; composite += 2 )
            {
                isPrime[(i*composite) >> 1] = false;

            }// End For ( Each predictable composite )

        }// End If ( Can be used for fitlering )

    }// End For

	*primeSet = (int*)malloc ( sizeof ( int )*(upperLimit + 1) );
	int *_primeSet = *primeSet;

    // Store back the result in term of a set
    int i, j;
    for ( i = 1, j = 1; j < (upperLimit >> 1); j++ )
    {
        if ( isPrime[j] )
        {
            _primeSet[i] = (j << 1) + 1;
            i++;

        }// End If ( if it is a prime number )

    }// End For

    // Can not forget that 1 + 1 question ^_^
    _primeSet[0] = 2;

    return i;

}// End Function

```

Now it takes 7s when searching for 200,000,000 prime numbers :)
And thanks you for providing me information ^_^

---

