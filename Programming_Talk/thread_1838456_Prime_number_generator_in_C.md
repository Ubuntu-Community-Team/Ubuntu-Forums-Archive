---
title: "Prime number generator in C"
date: 2011-09-03
forum: Programming Talk
---

### Post by renkinjutsu on 2011-09-03
I'm trying my hand at some of the Project Euler problems and one of them requires that I calculate every prime number below 2 million.

I already had a working implementation for generating prime numbers. Basically what it did was take every odd number and check if it was divisible by half the odd numbers below it.

While this method worked, it was very inefficient. The website stated that none of the challenges should take over a minute to complete. So I thought I should revise my algorithm.

I gave it a simple tweak by storing prime numbers into an array and using them to check the divisibility of every subsequent odd number. This should hopefully speed things up a bunch.

But when I ran the program, it only generates 3 additional prime numbers and then stops.. I can't spot the error myself. Extra eyes would be good.

```
#include<stdio.h>
main(void) {
	
	int number, prime, i, j;
	// max defines the upper-bound. 
	// Example: find all prime numbers between 1-900000
	int max = 900000;
	// amount defines the amount of prime numbers to calculate
	// Example: Calculate 10001 prime numbers
	int amount = 10001;
	int primes[] = {2,3,5,7};

	j = 3;

	printf("2\n3\n5\n7\n");
	for(number = 9; number < max && j < amount; number = number + 2) {

		prime = 1;
		for(i = 0; i <= j; i++) {
			if(number % primes[i] == 0)
				prime = 0;
		}
		if(prime) {
			printf("%d\n", number);
			j++;
			primes[j] = number;
		}
	}
	printf("number %d ; j %d ; i %d \n", number, j, i);
}
```

---

### Post by Bachstelze on 2011-09-03
Consider yourself lucky your program doesn't crash with a segmentation fault. C is not Python, what do you think happens when you do this?

```
int primes[] = {2,3,5,7};
primes[4] = 11;
```

---

### Post by Arndt on 2011-09-03
> **renkinjutsu said:**
> I'm trying my hand at some of the Project Euler problems and one of them requires that I calculate every prime number below 2 million.

I already had a working implementation for generating prime numbers. Basically what it did was take every odd number and check if it was divisible by half the odd numbers below it.

While this method worked, it was very inefficient. The website stated that none of the challenges should take over a minute to complete. So I thought I should revise my algorithm.

I gave it a simple tweak by storing prime numbers into an array and using them to check the divisibility of every subsequent odd number. This should hopefully speed things up a bunch.

But when I ran the program, it only generates 3 additional prime numbers and then stops.. I can't spot the error myself. Extra eyes would be good.

```
#include<stdio.h>
main(void) {
	
	int number, prime, i, j;
	// max defines the upper-bound. 
	// Example: find all prime numbers between 1-900000
	int max = 900000;
	// amount defines the amount of prime numbers to calculate
	// Example: Calculate 10001 prime numbers
	int amount = 10001;
	int primes[] = {2,3,5,7};

	j = 3;

	printf("2\n3\n5\n7\n");
	for(number = 9; number < max && j < amount; number = number + 2) {

		prime = 1;
		for(i = 0; i <= j; i++) {
			if(number % primes[i] == 0)
				prime = 0;
		}
		if(prime) {
			printf("%d\n", number);
			j++;
			primes[j] = number;
		}
	}
	printf("number %d ; j %d ; i %d \n", number, j, i);
}
```

Your code seems to write into primes[4], primes[5], etc., but you have only allocated memory for four elements.

---

### Post by JRV on 2011-09-03
> **renkinjutsu said:**
> 
Basically what it did was take every odd number and check if it was divisible by half the odd numbers below it.


You only need to check up to the square root.

---

### Post by renkinjutsu on 2011-09-03
> **Bachstelze said:**
> Consider yourself lucky your program doesn't crash with a segmentation fault. C is not Python, what do you think happens when you do this?

```
int primes[] = {2,3,5,7};
primes[4] = 11;
```

> **Arndt said:**
> Your code seems to write into primes[4], primes[5], etc., but you have only allocated memory for four elements.

I did this
```
#include<stdio.h>
main(void){
  int primes[] = {4,5,6,7};
  int i;

  primes[4] = 11; 
  for(i = 0; i <=4; i++){
    printf("%d\n", primes[i]);
  }
}

```
and it output
```
4
5
6
7
11
```
So it works like I would expect.. So this breaks down when it's scaled up?
Sorry. I'm taking a CS course right now (java) and we haven't even learned about arrays yet. But I also wanted to try learning C on my own time.

Also, thanks for the square-root tip.

---

### Post by simeon87 on 2011-09-03
> **renkinjutsu said:**
> I did this
```
#include<stdio.h>
main(void){
  int primes[] = {4,5,6,7};
  int i;

  primes[4] = 11; 
  for(i = 0; i <=4; i++){
    printf("%d\n", primes[i]);
  }
}

```
and it output
```
4
5
6
7
11
```
So it works like I would expect.. So this breaks down when it's scaled up?
Sorry. I'm taking a CS course right now (java) and we haven't even learned about arrays yet. But I also wanted to try learning C on my own time.

Also, thanks for the square-root tip.

It also breaks down at that level, it just depends on "luck" whether you get that result or not. It may also crash or give an arbitrary number from memory as you have no idea where the array is located and what's immediately next to it in memory.

Rule of thumb: Never read or write outside array bounds.

---

### Post by Bachstelze on 2011-09-03
> **renkinjutsu said:**
> I did this
```
#include<stdio.h>
main(void){
  int primes[] = {4,5,6,7};
  int i;

  primes[4] = 11; 
  for(i = 0; i <=4; i++){
    printf("%d\n", primes[i]);
  }
}

```
and it output
```
4
5
6
7
11
```
So it works like I would expect.. So this breaks down when it's scaled up?


The reason it works when you add just one element is that the compiler will typically allocate more space on the stack than is needed, so you will have room for a couple more elements. However, this extra space is not a lot (typically a dozen bytes at most), so you quickly run out of it. And obviously, you should not rely on it, because it is perfectly possible that the compiler will allocate exactly the amount of space you asked for, which in this case is 4 ints, so even one extra element could very well oveflow.

---

### Post by matchett808 on 2011-09-03
I need to pick up on one thing - the way that your calling your array is a bit off aswell.

In C and array of integers is called as:
```

int primes[i];

```where i is the number of elements you wish to create.

Try calling your array that way and it should help.

I'm not sure if :
  ```

int primes[] = {4,5,6,7};

```Is c++ or java but its not ansi c. (it may compile but thats because many compilers support c++ syntax in a c compiler and so on and so forth)

I'm going to have a look at the code and see what Else I can contribute :)

---

### Post by lisati on 2011-09-03
As matchett808 has pointed out, you might want to take a look at the way you define your array. 

With **int primes[] = {4,5,6,7};** you can only count on enough memory being allocated for 4 items. Better to use something like **int primes[i];** with "i" having a large enough value to allow for ALL the data you're likely to need to store.

---

### Post by Bachstelze on 2011-09-03
> **matchett808 said:**
> 
I'm not sure if :
  ```

int primes[] = {4,5,6,7};

```Is c++ or java but its not ansi c. (it may compile but thats because many compilers support c++ syntax in a c compiler and so on and so forth)


It is perfectly valid C99.

```
6.7.5.2 Array declarators

4. If the size is not present, the array type is an incomplete type.


6.7.8 Initialization

22. If an array of unknown size is initialized, its size is determined by the largest indexed
  element with an explicit initializer. At the end of its initializer list, the array no longer
 has incomplete type.

25. EXAMPLE 2
The declaration
int x[] = { 1, 3, 5 };
defines and initializes x as a one-dimensional array object that has three elements, as no size was specified
and there are three initializers.
```

> **lisati said:**
> Better to use something like **int primes[i];** with "i" having a large enough value to allow for ALL the data you're likely to need to store.

And get a nice stack overflow. :)

---

### Post by NovaAesa on 2011-09-03
Your approach could be improved by using a different algorithm. If you need to calculate every prime below 2 million, it would be better to use a sieving method (such as the Sieve of Eratosthenes) rather than performing a prime test on every number below 2 million. If you are serious about completing Project Euler (or at least getting a good way into it) you will need some kind of prime sieve algorithm anyway in the future challenges.

---

### Post by renkinjutsu on 2011-09-03
> **NovaAesa said:**
> Your approach could be improved by using a different algorithm. If you need to calculate every prime below 2 million, it would be better to use a sieving method (such as the Sieve of Eratosthenes) rather than performing a prime test on every number below 2 million. If you are serious about completing Project Euler (or at least getting a good way into it) you will need some kind of prime sieve algorithm anyway in the future challenges.

You're absolutely right.
I got my program to work, and it takes 874 ms to complete.

I browse the forum over on Euler (a hidden thread only accessible by those who've solved the problem), and people were posting their code. This one guy posted something pretty amazing that can complete in around 32 ms.. I tried to see if I could learn anything from reading his code, but it went way over my head.

There's also a bunch of notations that I have no idea what they mean.. Anyone mind breaking it down for me?

Here's the code:
```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
 
int main() {
        int LIM = 1000000, SQRTLIM=1000;
        bool *a = calloc(LIM+1000, sizeof(bool));
        int count=0;
        unsigned long long sum = 0;
        for(int p=2; p<LIM;) {
                if(++count==10001) printf("#%d: %d\n", count, p);
                sum+=p;
                for(int i=p*p; p<SQRTLIM&&i<LIM; i+=p) {
                        a[i]=1;
                }
                while(a[++p]==1);
        }
        printf("sum: %llu\n", sum);
}
```

Also, is there some sort of C interpreter so I don't have to compile things just so I can see what certain commands/syntax/notations do?

---

### Post by Arndt on 2011-09-04
> **renkinjutsu said:**
> I did this
```
#include<stdio.h>
main(void){
  int primes[] = {4,5,6,7};
  int i;

  primes[4] = 11; 
  for(i = 0; i <=4; i++){
    printf("%d\n", primes[i]);
  }
}

```
and it output
```
4
5
6
7
11
```
So it works like I would expect.. So this breaks down when it's scaled up?
Sorry. I'm taking a CS course right now (java) and we haven't even learned about arrays yet. But I also wanted to try learning C on my own time.



I tried this both with and without optimization and debugging. With -O, the last number I get is not 11, but 4. I guess that in this case, you have hit the variable 'i'. You can not count on any extra memory being there at all, except if nothing more has been put on the stack. And you call printf, so there will have been more put on the stack.

---

### Post by renkinjutsu on 2011-09-04
So I based my new algorithm on the Sieve of Eratosthenes. It *seems* wicked fast now, but it only works with small numbers. I can't scale it to 2 000 000, which is what the problem needs.

I get segmentation faults when the number is too big.

Old (working) code:
```
#include<stdio.h>
#include<math.h>

int main(void) {

  int number, prime, i, j;
  // max defines the upper-bound. 
  // Example: find all prime numbers between 1-900000
  int max = 2000000;
  // amount defines the amount of prime numbers to calculate
  // Example: Calculate 10001 prime numbers
  int amount = 2000000;
  int primes[amount];

  primes[0] = 2;
  j = 0;

  printf("2\n3\n5\n7\n");
  for(number = 3; number < max && j < amount; number = number + 2) {

    prime = 1;
    for(i = 0; primes[i] <= sqrt(number) && prime == 1; i++) {
      //printf("number %d being divided by %d\n", number, primes[i]);
      if(number % primes[i] == 0)
        prime = 0;
    }
    if(prime) {
      printf("%d\n", number);
      j++;
      primes[j] = number;
    }
  }
}

```

New code that uses sieve:
This one doesn't accept large numbers
```
#include<stdio.h>

int main(){
  int limit = 10000;
  int a[limit];
  int p = 2;
  int p_0;

  for(int i = 1; i < limit; i++)
    a[i] = 1;

  for(p; p < limit;){
    p_0 = p;

    for(int i = p * p; i < limit; i += p)
      a[i] = 0;

    for(int i = p + 1; i < limit; i++){
      if(a[i]){
        p = i;
        break;
      }

    }

    if(p == p_0)
      break;

  }

  for(int i = 1; i < limit; i++){
    if(a[i])
      printf("%d\n", i);
  }
}
```

Why is it that I can make a 2mill long array in the fist code, but not in the second?

EDIT: Nevermind, I found what was wrong. My 'i's and 'p's should've been long integers.

---

### Post by Bachstelze on 2011-09-04
You should not allocate that much memory on the stack. Allocate it on the heap with malloc().

---

### Post by Longinus00 on 2011-09-04
> **renkinjutsu said:**
> You're absolutely right.
I got my program to work, and it takes 874 ms to complete.

I browse the forum over on Euler (a hidden thread only accessible by those who've solved the problem), and people were posting their code. This one guy posted something pretty amazing that can complete in around 32 ms.. I tried to see if I could learn anything from reading his code, but it went way over my head.

There's also a bunch of notations that I have no idea what they mean.. Anyone mind breaking it down for me?

Here's the code:
```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
 
int main() {
        int LIM = 1000000, SQRTLIM=1000;
        bool *a = calloc(LIM+1000, sizeof(bool));
        int count=0;
        unsigned long long sum = 0;
        for(int p=2; p<LIM;) {
                if(++count==10001) printf("#%d: %d\n", count, p);
                sum+=p;
                for(int i=p*p; p<SQRTLIM&&i<LIM; i+=p) {
                        a[i]=1;
                }
                while(a[++p]==1);
        }
        printf("sum: %llu\n", sum);
}
```

Also, is there some sort of C interpreter so I don't have to compile things just so I can see what certain commands/syntax/notations do?

It's an implementation of the sieve of Eratosthenes.
[http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)

If you want to know what certain things do then read the manpage/online reference? For all the simple things you're doing that should be more than enough.

---

### Post by renkinjutsu on 2011-09-04
> **Longinus00 said:**
> It's an implementation of the sieve of Eratosthenes.
[http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)

If you want to know what certain things do then read the manpage/online reference? For all the simple things you're doing that should be more than enough.

Yeah. I figured that out when I started getting rid of some lines of code in my program. It started to look more like his. However, his is still faster by about 20 ms and I can't figure out why.

---

### Post by Arndt on 2011-09-04
> **renkinjutsu said:**
> You're absolutely right.
I got my program to work, and it takes 874 ms to complete.

I browse the forum over on Euler (a hidden thread only accessible by those who've solved the problem), and people were posting their code. This one guy posted something pretty amazing that can complete in around 32 ms.. I tried to see if I could learn anything from reading his code, but it went way over my head.

There's also a bunch of notations that I have no idea what they mean.. Anyone mind breaking it down for me?

Here's the code:
```
#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
 
int main() {
        int LIM = 1000000, SQRTLIM=1000;
        bool *a = calloc(LIM+1000, sizeof(bool));
        int count=0;
        unsigned long long sum = 0;
        for(int p=2; p<LIM;) {
                if(++count==10001) printf("#%d: %d\n", count, p);
                sum+=p;
                for(int i=p*p; p<SQRTLIM&&i<LIM; i+=p) {
                        a[i]=1;
                }
                while(a[++p]==1);
        }
        printf("sum: %llu\n", sum);
}
```

Also, is there some sort of C interpreter so I don't have to compile things just so I can see what certain commands/syntax/notations do?

I have heard of C interpreters, but never used one, so I don't know. But is compiling that much of a problem?

---

### Post by Arndt on 2011-09-04
> **renkinjutsu said:**
> Yeah. I figured that out when I started getting rid of some lines of code in my program. It started to look more like his. However, his is still faster by about 20 ms and I can't figure out why.

Hard to say without seeing both.

---

### Post by Bachstelze on 2011-09-04
> **Arndt said:**
> I have heard of C interpreters, but never used one, so I don't know. But is compiling that much of a problem?

There is one compiler (tcc) that has an option to run a program after compilation, and can therefore be used with a shebang line:

```
firas@applejack ~ % cat hello.c             
#!/usr/bin/tcc -run

#include <stdio.h>

int main(void)
{
        puts("Hello, world!");
        return 0;
}
firas@applejack ~ % ./hello.c 
Hello, world!

```

---

