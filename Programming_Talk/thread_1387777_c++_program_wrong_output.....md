---
title: "c++ program wrong output...."
date: 2010-01-22
forum: Programming Talk
---

### Post by abhilashm86 on 2010-01-22
i'm calculating sum of multiples of 3 and 5 till 1000. But i'm getting a wrong answer, whats wrong with my code? 
```
#include<iostream>
using namespace std;
        int main()
        {
                long int i, sum = 0;


                for(i=1; i <1000; i++)
                {
                        if((i%3) == 0 )
                        {
                                sum   = sum + i ;
                        }

                        if((i%5) == 0)
                        {
                                sum   = sum + i ;
                        }

                }
                        cout<<sum<<endl;
        }

```

---

### Post by MindSz on 2010-01-22
I think you're using the same accumulator for 3 and 5, so when i=3, sum =3, but then i=5 and sum=8...and then 11, 16, etc.

So yeah, try using different accumulators (like sum1 and sum2)

---

### Post by unknownPoster on 2010-01-22
> **abhilashm86 said:**
> i'm calculating sum of multiples of 3 and 5 till 1000. But i'm getting a wrong answer, whats wrong with my code? 
```
#include<iostream>
using namespace std;
        int main()
        {
                long int i, sum = 0;


                for(i=1; i <1000; i++)
                {
                        if((i%3) == 0 )
                        {
                                sum   = sum + i ;
                        }

                        if((i%5) == 0)
                        {
                                sum   = sum + i ;
                        }

                }
                        cout<<sum<<endl;
        }

```

you just have a simple logic error. For example, when i = 30, since 30 is both of multiple of 3 AND 5 it gets added to your sum twice. I would suggest thinking of a way to create a compound if statement to avoid this. If you need further hints/guidance, feel free to ask. :)

> **MindSz said:**
> I think you're using the same accumulator for 3 and 5, so when i=3, sum =3, but then i=5 and sum=8...and then 11, 16, etc.

So yeah, try using different accumulators (like sum1 and sum2)

That is incorrect

---

### Post by dwhitney67 on 2010-01-22
> **abhilashm86 said:**
> i'm calculating sum of multiples of 3 and 5 till 1000. But i'm getting a wrong answer, whats wrong with my code? 

I dunno?  Is it the indentation of the code?  (Ah... I see the problem... well actually, 'unknownPoster' saw it first.)

Did you want to include the value 1000 in your result?  It is divisible by 5.

To simplify your code, try something like:
```

if ((i % 3 == 0) || (i % 5 == 0))
{
   sum += i;
}

```

---

### Post by unknownPoster on 2010-01-22
> **dwhitney67 said:**
> 

Did you want to include the value 1000 in your result?  It is divisible by 5.


This is the first project euler problem. 

> 
 If we list all the natural numbers below 10 that are multiples of 3  or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
 Find the sum of all the multiples of 3 or 5 below 1000. 

---

### Post by MindSz on 2010-01-22
Oh yeah, I should've read the post with more care. I thought the OP wanted multiples of 3 and 5. My bad :)

---

### Post by HarrisonNapper on 2010-01-22
> **unknownPoster said:**
> If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
 Find the sum of all the multiples of 3 or 5 below 1000. 			 		

So below 1000 not including 1000 :D

---

### Post by Can+~ on 2010-01-22
I suggest solving this as an [arithmetic progression]("http://en.wikipedia.org/wiki/Arithmetic_progression").

```
Multiples of 3 + Multiples of 5 - Multiples of 15
```

edit: I wrote the above a bit in a hurry, not sure if I'm right, let's see:

[PHP]>>> set3 = set(range(0, 100, 3))
>>> set5 = set(range(0, 100, 5))
>>> set3 & set5
set([0, 75, 45, 15, 90, 60, 30])[/PHP]

It seems right.

---

### Post by dwhitney67 on 2010-01-22
@ can+~

The arithmetic progression is beyond my aging brain's capability to comprehend, well at least on a Friday.

Since the values up to 1000 are only iterated over once, is there really a need to check for a value that is a multiple of 15?

If the number is evenly divisible by 3 OR is evenly divisible by 5, then we have a 'winner'.  As I am sure you are aware, when two conditionals are conjoined with an OR operator, should the first conditional resolve to 'true', then the other conditional is not  evaluated, for the entire statement will be 'true'.

A short list of the values that would be of interest are:

[ 3 5 6 9 10 12 15 18 20 21 ... 993 995 996 999 ]

---

### Post by Some Penguin on 2010-01-22
It's not strictly necessary to view things as arithmetic over arithmetic series... but as N grows larger it scales better to do so, since you can sum up an arithmetic series with very few computations.

i.e. n*(a_{1}+a_{n})/2 takes the same amount of math for n=1000 as it does for n=10^5.  For some n, probably fairly small, the cost of the constant number of multiplications, shifts and additions is going to be cheaper than the iterative approach.

---

### Post by Can+~ on 2010-01-22
> **dwhitney67 said:**
> Since the values up to 1000 are only iterated over once, is there really a need to check for a value that is a multiple of 15?

The sum of the arithmetic progression is a simple formula. For instance, if I want to know the sum of all numbers between 1 and 100:

```
100*101 / 2 = 10100 / 2 = 5050
```

R:
```
> sum(1:100)
[1] 5050
```

The current algorithm goes from 0 to 1000 (N). Thus it's O(n). On the other hand, applying a simple function is O(1). Here's the formula on python:

[PHP]
def arithmetic_sum(n, diff=1, start=1):
	return n/2*(2*start + (n-1)*diff)[/PHP]

And now, I could just do the sum between all the multiples of 3 and 5, but that would leave repeated elements (the multiples of 15), that's why you need to substract. And it's still O(1), and still better than iterating and testing.

I accept the friday excuse, though.

---

### Post by LKjell on 2010-01-22
Can+~ may I remind the main language it C++ and not Python.

Another thing is that when you are going to make these series you are using precious time. It is much faster to just loop the whole series once and use
dwhitney67 code.

---

### Post by Can+~ on 2010-01-22
> **LKjell said:**
> Can+~ may I remind the main language it C++ and not Python.

Another thing is that when you are going to make these series you are using precious time. It is much faster to just loop the whole series once and use
dwhitney67 code.

Friday is striking, huh? Did you actually read the equation? No series must be created, you don't even need arrays or lists, or any form of storage, just a single freaking function.

What series? The equation above doesn't even have to build a series, the above usage of R and python were to demonstrate that it does actually equal to the result of the function.

Here's the code in C++, it's the exact same thing (if there are errors in the result, it's probably related to the bounds, I didn't test properly. I'll edit later):

[PHP]#include <iostream>

int arithmetic_sum(int max, int diff=1)
{
	// Let's say that the progression starts in the first multiple, e.g:
	// diff=2: 2, 4, 6, 8... diff=3: 3, 6, 9, ...
	
	// Calculate the maximum possible amount of the term diff in the range start..n
	// If you have 1000 numbers, there must be floor(1000/3) times a multiple of 3.
	max /= diff;
	
	// Computes the result of the sum of an arithmetic progression
	return max*diff*(max + 1)/2;
}

int composed_sum(int max, int numa, int numb)
{
	// Returns A+B-(A*B) in the range [1..n], where A and B are the
	// sum of the progression for numa and numb, respectively.
	return arithmetic_sum(max, numa)+arithmetic_sum(max, numb)-arithmetic_sum(max, numa*numb);
}

int main(int argc, char **argv)
{
	std::cout << "Result:" << composed_sum(1000, 3, 5) << std::endl;
	
	return 0;
}[/PHP]

*Edit: Ok, I solved the problem I had, the problem was with very small numbers.

Testing (To 20):
```
Result O(1):98
```

Comparing with Python sets:
[PHP]>>> A = set(range(0, 21, 3))
>>> B = set(range(0, 21, 5))
>>> A.union(B)
set([0, 3, 5, 6, 9, 10, 12, 15, 18, 20])
>>> sum(A.union(B))
98[/PHP]

The question I have, is, do you consider the last number? For example, if the range is from 0 to 30, do you consider 30 too?

*Edit 2: LKJell was right about the division screwing up, I forgot I'm working with plain integers (I've been using R for far too long).

---

### Post by denarced on 2010-01-22
> **LKjell said:**
> Can+~ may I remind the main language it C++ and not Python.

Another thing is that when you are going to make these series you are using precious time. It is much faster to just loop the whole series once and use
dwhitney67 code.

I suppose these formulas would be handy if you're dealing with huge numbers and needed to do these kind of calculations .. I just can't think why you would need to do calculations of this type in programming.. Anyone got any ideas on that one ??

---

### Post by LKjell on 2010-01-22
My bad yea. Of course that function calculating is much faster.

---

### Post by LKjell on 2010-01-22
I did some calculation would not

```

int arithmetic_sum(int max, int diff=1)
{
	max /= diff;
    	
    	return diff*(max*max + 1)/2;
}
```

Be the same than that stuff you did?

---

### Post by Can+~ on 2010-01-22
> **LKjell said:**
> I did some calculation would not

```

int arithmetic_sum(int max, int diff=1)
{
	max /= diff;
    	
    	return diff*(max*max + 1)/2;
}
```

Be the same than that stuff you did?

Yes, actually. I used the original equation and then decided to assume that the series starts on the diff value (start = diff), and didn't relook the equation. 

Also, there are still some issues in the code I posted, regarding boundries, I don't know if the OP wants to consider the last number in the series, but I leave that to him, I proved my point that you can solve this with the formula of the sum of an arithmetic progression.

Also, in general. This is the type of optimization that most people completely miss. Instead of sticking to try to find how to solve the little details, people miss the big picture altogether. The arithmetic progression is one of those things that you probably see in the school once, and completely forget about it. Well, here is handy again, reducing a problem from O(n) to O(1) is a huge performance boost in terms of scalability. And that's why I use the quote from Donald Knuth in my sig, don't miss the big picture (the algorithm) in tiny problems.

**Edit:** Actually, now I found an error in your math:

```
diff*(max*max + 1)/2;
```

Should be:

```
diff*(max*max + max)/2;
```

Therefore:

```
max*diff*(max + 1)/2;
```

---

### Post by LKjell on 2010-01-22
Need to fix it a bit.

It is suppose to be d(m + m^2)/2

We cannot divide with 2 first because m is an int. If m is odd we lose information therefore we need to divide by two last.

---

### Post by Can+~ on 2010-01-22
> **LKjell said:**
> Need to fix it a bit.

It is suppose to be d(m + m^2)/2

We cannot divide with 2 first because m is an int. If m is odd we lose information therefore we need to divide by two last.

Corrected, also, now I don't need that if statement in there.

---

### Post by abhilashm86 on 2010-01-23
> **dwhitney67 said:**
> @ can+~

The arithmetic progression is beyond my aging brain's capability to comprehend, well at least on a Friday.

Since the values up to 1000 are only iterated over once, is there really a need to check for a value that is a multiple of 15?

If the number is evenly divisible by 3 OR is evenly divisible by 5, then we have a 'winner'.  As I am sure you are aware, when two conditionals are conjoined with an OR operator, should the first conditional resolve to 'true', then the other conditional is not  evaluated, for the entire statement will be 'true'.

A short list of the values that would be of interest are:

[ 3 5 6 9 10 12 15 18 20 21 ... 993 995 996 999 ]

that was the trick!! redundant values needs to be used just once......

---

