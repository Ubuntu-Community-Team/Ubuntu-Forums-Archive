---
title: "Sieve of Eratosthenes"
date: 2008-08-20
forum: Programming Talk
---

### Post by nebu on 2008-08-20
I have written this program to find all primes between two given nos.... using the [sieve of eratosthenes.]("http://en.wikipedia.org/wiki/Sieve_of_eratosthenes")

could you give me tips on how to optimize performance for the code in terms of processing time and memory usage...

```
#include <stdio.h>

main()
{
        int lo,hi;
        printf("\nLow,High: ");
        scanf("%d %d",&lo,&hi);
        const int max = hi;
        int z[max];
        int *p = z,*t,*q = &z[max];
        register int i;
        for(i=0;i<max;i++)
        {
                *p = i;
                p++;
        }
        p = &z[2];
        for(;p<q;p++)
        {
                if(*p!=0)
                {
                        t = p+*p;
                        for(;t<q;t+=*p)
                        {
                                *t=0;
                        }
                }
        }
        p = &z[lo];
        for(;p<q;p++)
        {
                if(*p!=0)
                        printf("%d\t",*p);
        }
        printf("\n");
}



```

---

### Post by dribeas on 2008-08-20
> **nebu said:**
> I have written this program to find all primes between two given nos.... using the [sieve of eratosthenes.]("http://en.wikipedia.org/wiki/Sieve_of_eratosthenes")

could you give me tips on how to optimize performance for the code in terms of processing time and memory usage...


Not much to do there once you have fixed your algorithm, moreover with a simple algorithm as this one.

---

### Post by Maveric3477 on 2008-08-20
I'm no pro at this, and I'm not 100% sure it's a better way, but I'd create a list to store your prime numbers, and each time you find a new one push it onto the list. Then you just need to check each number to see if any of the primelist will go into it evenly.. If so, it's not a prime. If not, sweet! another prime.

I think that way should save you a lot of computations, but again, I'm not sure. I just used that sieve once before and it was slow as hell.

---

### Post by dribeas on 2008-08-20
> **dribeas said:**
> Not much to do there once you have fixed your algorithm, moreover with a simple algorithm as this one.

Oh, well, I just thought of a small trick, you can have a number of primes precomputed, that will save time and space.

   David

---

### Post by cszikszoy on 2008-08-20
Using the Sieve of Eratosothenes, you only need to loop to n/2 to check for multiples.

Think about it this way,  Say you want to find all of the primes less than 100.  What you do, is start with 2, then cross out all multiples of 2.  Next continue with 3.  4 is already crossed out, so move on to 5.  Basically, you can stop checking at 50. (well 49 actually).  The numbers 50-100 don't even need to be checked for one of two reasons:

a) they will already be correctly marked as prime by checking the numbers from 2-49
or
b) Why do you need to check multiples of the number 75 if you stop at 100?  The next multiple of 75 is 150, which is already beyond our limit.

Does that make sense?

If you understand this fact, then you can effectively cut your program's loop in half.

---

### Post by hod139 on 2008-08-20
> **cszikszoy said:**
> Using the Sieve of Eratosothenes, you only need to loop to n/2 to check for multiples.
You actually only need to loop until you reach a number greater than the sqrt(n).

---

### Post by cszikszoy on 2008-08-20
> **hod139 said:**
> You actually only need to loop until you reach a number greater than the sqrt(n).


Ahh, yes, that's right.  It's been a while since I wrote a program to calculate this.  I forgot about that, thanks!

---

### Post by nebu on 2008-08-21
> **hod139 said:**
> You actually only need to loop until you reach a number greater than the sqrt(n).
if i check numbers to sqrt n.... then wont i end up missing multiples..... n/2 makes more sense to me...

---

### Post by NovaAesa on 2008-08-21
Remeber that if you have your loop conditional value set to the sqrt of something, it's a good idea to calculate the sqrt out side of the loop. This way, you aren't calculating the square root of thingthing everytime the loop runs.

---

### Post by dribeas on 2008-08-21
> **nebu said:**
> if i check numbers to sqrt n.... then wont i end up missing multiples..... n/2 makes more sense to me...

You are just trying to find prime numbers, not all factors. 

There can be factors higher than sqrt(n), lets call it f. If f is a factor of n and is greater than sqrt(n) then there must be a factor f1 such that f * f1 = n, and f1 must be smaller than sqrt(n). But if you found no factors of n smaller than sqrt(n) then that is not possible.

---

