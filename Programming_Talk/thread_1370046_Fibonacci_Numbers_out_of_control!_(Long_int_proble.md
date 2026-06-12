---
title: "Fibonacci Numbers out of control! (Long int problem)"
date: 2010-01-01
forum: Programming Talk
---

### Post by Quarg on 2010-01-01
Hi
I've got this program Fibonacci.c that I'm using to mess with fibonacci numbers. I've got to deal with some huge numbers, and the eventual goal of the program is to find the Fibonacci number whose digital sum (adding each number, so 111 would be 1+1+1 = 3) meets or exceeds 100. So I'm basically writing a loop that finds fibonacci numbers, adds them in an array, sees what the digital sum is, and moving on if it doesn't get to 100. Here's the code:

```

#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>
#include<limits.h>
int FindFibonacciTerms(void) 
 {
	bool done = false; 
	bool FibonacciDone = false;
	     int i;  
	     int d; 
	unsigned long long int FibonacciNumberTwo; 
	unsigned long long int FibonacciSum; 
	unsigned long long int FibonacciNumber0 = 1;
	unsigned long long int FibonacciNumber1 = 1; 
	unsigned long long int FibonacciNumber2 = 2; 
	unsigned long long int DigitalSum100 =  100000000000; 
	unsigned long long int FibonacciArray[12]; 	
//	while(FibonacciDone != true)
	for(d = 0; d < 100; d++)
	 {	
		FibonacciNumber0 = FibonacciNumber1; 
		FibonacciNumber1 = FibonacciNumber2; 
		FibonacciNumber2 = FibonacciNumber0 + FibonacciNumber1; 
		printf("New FibonacciNumbers: %lld, %lld, %lld\n", FibonacciNumber2, FibonacciNumber1, FibonacciNumber0);
		FibonacciNumberTwo = FibonacciNumber2; 
		for(i = 0; i < 12; i++)
		 {
			FibonacciArray[i] = FibonacciNumberTwo % 10; 
			FibonacciNumberTwo = FibonacciNumberTwo / 10; 
		  }
			  
			
		while(done = false)
		 {
			
			for(i = 0; i < 12; i++); 
			 {
				if(FibonacciArray[i] > 9)
				 {
					done = true;
				 }else {
	 
					FibonacciSum = FibonacciArray[i] + FibonacciSum; 
				 }
			 } 
		 }  
		if(FibonacciSum >= 100)
		 {
			FibonacciDone = false; 
		 } else {
			FibonacciDone = true; 
		 } 
			
	 } 
	printf("Final FibonacciNumber = %lld\n", FibonacciNumber2); 

 return 0; 
 } 

int main()
 {
	FindFibonacciTerms(); 
	return 0; 
 } 

```

my problem is, when it gets to really large numbers, it starts going crazy and giving me negative numbers that aren't Fibonacci numbers at all. I think I may be misusing my unsigned long long int's, but I don't know how. Any help?

---

### Post by hanlin on 2010-01-01
I think the issue is with your printf statement. Use %llu instead

---

### Post by Quarg on 2010-01-01
That seems to do the trick, thanks.

---

### Post by Reiger on 2010-01-02
FYI/spoiler: 

Fibonacci sequences are approximately phi^n for large n, with phi the golden ratio (1 + sqrt 5)/2.

Consequentially you can solve for n approximately by simply computing log <number> / log phi. Assuming 199999999999 as number you get 54-55.

---

### Post by MadCow108 on 2010-01-02
> **Reiger said:**
> FYI/spoiler: 

Fibonacci sequences are approximately phi^n for large n, with phi the golden ratio (1 + sqrt 5)/2.

Consequentially you can solve for n approximately by simply computing log <number> / log phi. Assuming 199999999999 as number you get 54-55.

it gets better:
the n'th fibonacci number is **exactly** (phi^n - (1 - phi)^n)/sqrt(5)
on a computer you just have to handle the imprecision of the sqrt and you get the correct integer in O(log(n)) time

---

### Post by Reiger on 2010-01-02
I know that... It's inevitably part of first term computer science Math: a crash course in making sure all students know their basic (induction based) math & number theory. 

My point was more about how the log <number>/log phi provides you with a good heuristic for a starting point in solving the OP's problem. (Which places additional constraints on finding the appropriate number.) :P

---

### Post by Arndt on 2010-01-02
> **MadCow108 said:**
> it gets better:
the n'th fibonacci number is **exactly** (phi^n - (1 - phi)^n)/sqrt(5)
on a computer you just have to handle the imprecision of the sqrt and you get the correct integer in O(log(n)) time

Shouldn't it be 1/phi, rather than 1-phi?

---

### Post by Reiger on 2010-01-02
Assuming you mean -1/phi; The two are equivalent.

---

### Post by DiegoTc on 2010-01-02
You should try to do it on a recursive way better.

#include <iostream>
using namespace std;

int fibonacci(int number){
   if(number==1||number==0)
    return number;

    else
    return fibonacci(number-1)+fibonacci(number-2);

}

this is a simpler way

---

### Post by Arndt on 2010-01-02
> **Reiger said:**
> Assuming you mean -1/phi; The two are equivalent.

So they are, and I should have known - I never saw the formula written that way before.

---

### Post by ve4cib on 2010-01-05
> **DiegoTc said:**
> You should try to do it on a recursive way better.

```
#include <iostream>
using namespace std;

int fibonacci(int number){
   if(number==1||number==0)
    return number;

    else
    return fibonacci(number-1)+fibonacci(number-2);

}
```

this is a simpler way


Please, PLEASE tell me you're joking.  Calculating fibonacci numbers using the recursive algorithm you show is quite possibly *the* worst way of doing it, and is often used as an example of where easy recursive solutions are not the best way of doing things.

The problem here is that you wind up re-calculating the same values over and over.

For example, let's say you want to calculate fib(100):

```

fib(100) = fib(99) + fib(98)
    fib(99) = fib(98) + fib(97)
        fib(98) = fib(97) + fib(96)
            fib(97) = fib(96) + fib(95)
                fib(96) = fib(95) + fib(94)
                    ...
                ...
            fib(96) = fib(95) + fib(94)
                ...
        fib(97) = fib(96) + fib(95)
            fib(97) = fib(96) + fib(95)
                fib(96) = fib(95) + fib(94)
                    ...
                ...
            fib(96) = fib(95) + fib(94)
                ...

    fib(98) = fib(97) + fib (96)
        fib(97) = fib(96) + fib(95)
            fib(96) = fib(95) + fib(94)
                ...
            ...
        fib(96) = fib(95) + fib(94)
            ...

```
(indentation indicates recursive depth)

See how the same values (like fib(96)) keep showing up?  That's duplicated work, which is just plain inefficient.

---

### Post by iharrold on 2010-01-05
> **ve4cib said:**
> See how the same values (like fib(96)) keep showing up?  That's duplicated work, which is just plain inefficient.

Not always true in the case of Tail Recursion (not shown in the recursion example mind you).

I think the greater issue is overflowing the call stack on very large recursion.

---

### Post by WitchCraft on 2010-01-05
If at all do it iteratively.

The negative numbers are either arithmetic or stack overflow.
You need a bigint library.

I've once used the bigint one from Mat McCutchen:
[http://mattmccutchen.net/bigint/](http://mattmccutchen.net/bigint/)

It's a solution that is pretty for its simplicity.

As for the most efficient calculation:
A recursive algorithm is just a straighforward matrix math multiplication:

say you have the first start vector for the fibonacci numbers [n+1,n], e.g. [1,0]
then you calculate the next by left multyplying the matrix [1,1;1,0] to this start vector.

So you get the n'th number by [1,1;1,0]^n * [1,0]

Remember from basic linear algebra that A^n = landa^n * Eigenvector(A).

So you get: [1-landa,1;1,-landa] 
which leads to det(A-landa*I) = landa^2 - landa -1
.

It follows that the k'th fibonnaci number is  round(1/sqrt(5) * ((1+sqrt(5))/2)^k;0)
[Linear Algebra, Gilbert Strang, page 309 + 315, ISBN: 3-540-43949-8]

Note Operator precedence: ((1+sqrt(5))/2) must be raised to k befor multiplying with 1/sqrt(5).

---

