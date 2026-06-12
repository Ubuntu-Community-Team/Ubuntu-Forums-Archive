---
title: "Can you help me with this C++ Array problem? :("
date: 2009-02-11
forum: Programming Talk
---

### Post by deniyc on 2009-02-11
The Sieve of Eratosthenes.
Write a program to determine all the prime numbers between 1 and N ( a number to be entered on the keyboard), using the Sieve of Eratothenes, a method of finding prime numbers, which dates back 3rd century b.c. to do this, construct an integer array, a[N+1]. **[COLOR="DarkOrange"]_Initialize all the elements of this array to 1, except  a[1] which is to zero_[/COLOR]**(because 1 is not a prime number).
Make two for-loop segemnts: the outer loop starting with i=2 and the inner loop with j=2, then [COLOR="DarkOrange"]_**assign all the array elements that are multiples of 2, 3, 4 and so on with zero values**_[/COLOR], so that the array elements that are not their multiples keep their initial values, that is 1. Disregard a[0]. If you make the upper limit of i and j to be less than or equal to N as shown below, the array will be out of range.
	for (i=2; i<= N;i++)
		for ( j=2; j<=N;j++)
			a[i*j]=0;
The highest subscripted variable of the array is only a[N], but the program will be processing a[N*N], for the above program segment, and this will cause an error, so take precaution in selecting the proper limit of i and j in the for-loop segment.
For illustration, if N=12, the value that the programwould assign to each array element would be:
	a[1]=0			a[5]=1			a[9]=0
	a[2]=1			a[6]=0			a[10]=0
	a[3]=1			a[7]=1			a[11]=1
	a[4]=0			a[8]=0			a[12]=0
So, array elements whose indices are prime numbers will have the value 1, while the rest will have a value of zero. [COLOR="DarkOrange"]_***[I]Output the indices of the array elements between 1 and N whose values are 1.***[/I]_[/COLOR]
[COLOR="Magenta"]**In the above example, the prime numbers between 1 and 12 are:2,3,5,7 and 11.**[/COLOR]


**Sieve of E. is indicated just below it, the next sentence explains what to do..

*THANK YOU!

---

### Post by Zugzwang on 2009-02-11
So what is the question?

---

### Post by ch0d3 on 2009-02-11
Homework?

What is your question...

---

### Post by deniyc on 2009-02-11
Yes.. homework. I don't know really where to start. I really can't understand.I'm confused wit the whole problem. :|

---

### Post by Zugzwang on 2009-02-11
> **deniyc said:**
> Yes.. homework. I don't know really where to start. I really can't understand.I'm confused wit the whole problem. :|

Start by reading the Wikipedia article of the sieve.

---

### Post by deniyc on 2009-02-11
Orang text---HOW will I do those?
Pink text---That's should be seen in the proram too.

---

### Post by deniyc on 2009-02-11
include <iostream>
#define N 100

int main()
{
//declarations and initializations
bool primes[N+1];
for( int i=0 ; i <= N ; i++ ) primes[i] = true;
primes[0] = primes[1] = false;

//set each composite number to false
for( int outer = 2 ; outer <= N ; outer++ )
if( primes[outer] )
for( int inner = 2 ; outer*inner <= N ; inner++ )
primes[outer*inner] = false;

//output the prime numbers
std::cout << "PRIMES BELOW " << N << std::endl;
for( int i = 0 ; i<=N ; i++ )
if( primes[i] )
std::cout << i << std::endl;

return 0;
}


----Is this correct? Anything wrong about this?Someone made it for me.

---

### Post by Zugzwang on 2009-02-11
> **deniyc said:**
> Orang text---HOW will I do those?

Normally by doing "for" loops. You even gave an example of such a loop.

---

### Post by deniyc on 2009-02-11
BTW, thanks..

---

### Post by Leo-nguyen on 2009-02-11
i think it will simpler than if you make a funtion ( use to check prime number---)

---

### Post by MasterProg on 2009-02-11
> **Leo-nguyen said:**
> i think it will simpler than if you make a funtion ( use to check prime number---)

Function works best if you need to check if a number is prime, while the sieve works best if you want to determine prime numbers in some range.

---

