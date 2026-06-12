---
title: "Bit Arrays"
date: 2007-10-29
forum: Programming Talk
---

### Post by Slychilde on 2007-10-29
I've been working on the problems at [http://www.projecteuler.net](http://www.projecteuler.net), and one of the things I came across was a bit array.  What I used it for was on problem #10: to create a [sieve of eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") to find the sum of all primes below one million.

Now, what I'm wondering is what are bit arrays all used for commonly (can they be called boolean arrays too?) in the programming world? At first, I didn't quite get that the number was the array position, and the actual data was true/false - 0/1, which saved me the trouble of making a multi-dimensional array.  

Here's my code, if that helps explain:

```
#! /usr/bin/python
'''From http://www.projecteuler.net problem 10: Find the sum of all
the primes below one million. Uses a Sieve of Eratosthenes fuction
to quickly find all primes up to any given amount.

Sieve of Eratosthenes: Write a list of numbers from 2 to the highest
number you want to test.  Check the first number for primality; if so
mark all it's factors up to the max size as not prime.  Go through the list
until you find the next number not marked, then do the same with that until
the list is complete. All unchecked  numbers are prime.'''

def sievePrimes(size):
        '''Sieves an array for primes up to a given size. Check above 
        comment for Sieve of Eratosthenes information.'''
        primes = [1] * size #makeshift bit array. 1 = prime, 0= not prime.
        primes[:2] = 0, 0
        for i in range(2, len(primes)-1):
                if primes[i] == 1:
                        mult = 2*i
                        while mult < len(primes):
                                primes[mult] = 0
                                mult += i
        return primes

sum = 0
mil = sievePrimes(1000000)
for x in range(len(mil) - 1):
        if mil[x] == 1: sum += x
print sum
```

Also, is there anything in there that I could improve coding-wise? Including documentation.

---

### Post by smartbei on 2007-10-29
You may want to think about removing all of the even values, and just adding a 2 to the final value. this should pretty much cut execution time in half - Very noticable.

Also, you don't want to do len(primes), that is slow since it must loop through all of the items in the list to find their count. Since the length is really the same as your size parameter, why nor use that?

Just for fun, how long does that take to run? With/without my suggestions?

This kind of code is very easy to do in c++, and it is MUCH faster there, so that is one improvement I guess you could implement. :D

---

### Post by Slychilde on 2007-10-29
The runtime of the original is 2.40354585648 seconds.

> Also, you don't want to do len(primes), that is slow since it must loop through all of the items in the list to find their count. Since the length is really the same as your size parameter, why nor use that?

Thank you!  That is great information to know; I totally missed that. :)

> You may want to think about removing all of the even values, and just adding a 2 to the final value. this should pretty much cut execution time in half - Very noticable.

I'm not entirely sure I did this right, but I tried it.  Let me know if there's a better way.

```
#! /usr/bin/python
'''From http://www.projecteuler.net problem 10: Find the sum of all
the primes below one million. Uses a Sieve of Eratosthenes fuction
to quickly find all primes up to any given amount.

Sieve of Eratosthenes: Write a list of numbers from 2 to the highest
number you want to test.  Check the first number for primality; if so
mark all it's factors up to the max size as not prime.  Go through the list
until you find the next number not marked, then do the same with that until
the list is complete. All unchecked  numbers are prime.'''

import time
import math

s = time.time()

def sievePrimes(size):
        '''Sieves an array for primes up to a given size. Check above 
        comment for Sieve of Eratosthenes information.'''
        if size % 2 == 0:
                primes = [0,1] * (size/2) #makeshift bit array. 1 = prime, 0= not prime.
        else:
                primes = [0,1] * (size/2 + 1)
        primes[1:3] = 0,1 #Makes 2 prime.
        for i in range(3, size):
                if primes[i] == 1:
                        mult = 2*i
                        while mult < len(primes):
                                #if primes[mult] == 1:  primes[mult] = 0
                                primes[mult] = 0
                                mult += i
        return primes

sum = 0
mil = sievePrimes(1000000)
for x in range(len(mil) - 1):
        if mil[x] == 1: sum += x
print sum
print time.time() - s
```

This one ran in 2.09392809868 seconds.

I do have a question: why does it take longer to run with the if statement I commented out, than with it in there?  I'm speculating that although it takes some redunancy out of it, that having to access the bit twice is more work?

Although I know enough C++ to code the problem in it, I really like working in Python, and I can wait the two seconds for an answer.  I'm more curious about the code itself, because my memory is a bit rusty and I don't want any bad habits to creep in.  Really, I should be doing this in Java, since that's what the school will be working in....I'm not a big fan of Java, though.

Thanks for the help, I really appreciate it.  I'm working on going back to school for Comp Sci. and it's been 3 years since I've taken a programming class.  If anyone has information about bit arrays in the original post, I would still like to know. :)

---

### Post by smartbei on 2007-10-29
Ok, the reason there wasn't a major speed decrease is because you are doing this really odd :p.

Note however, that len(primes) is about 1/2 of size, so some of your code needs changing.

Also, there is still one len(primes) in there. I doubt however that the current code gives a correct result.

Unfortunately, I am not next to a python interpreter. I will be happy to reply with a (slightly) changed code when I am.

---

### Post by YetAnotherNoob on 2007-10-29
I have used the C++ std::bitset on occasion.  super-fast!  It is a nice way to hold a bunch of booleans, without having loads of variables laying about.

---

### Post by Slychilde on 2007-10-29
It gives the answer 37550402023, which is right according to the website.  I think the majority of the time is actually in just making the array.  When I open IDLE and put in primes = [1]  * 1000000, it takes a few seconds for the pc to give back control.

---

### Post by smartbei on 2007-10-29
Well, I apologize for saying it gives a wrong result :D. There is another puzzle on projecteuler (not sure which one)  in which I alocated lists in a similar fashion and quickly found that it is not very scalable, since it becomes very slow.

---

### Post by pmasiar on 2007-10-29
To make numerical calculation faster in Python, you may want to use numpy module. I would be really interested how much will be the speed increase compared with plain Python.

---

### Post by smartbei on 2007-10-29
When I get home tonight I will try it and post source and times. Should be interesting indeed. Maybe I will also post a basic c++ program for speed comparison :).

---

### Post by smartbei on 2007-10-29
I wrote my own version of this function. Here it is for you inspection:
```

def sievePrimes(size):
	test=0
	
	if size%2 != 0:
		size+=1 #this is to include the last prime-possible if size is odd.
	
	l=[0,1]*(size/2)
	l[:2] = 0,0
	
	for a in xrange(3,size,2):
		if l[a] == 1:
			for b in xrange(a*3,size,a*2):
				l[b]=0
	return l

size=1000000

primes = sievePrimes(size)
Sum=2
for a in xrange(3,size,2):
	if primes[a] == 1:
		Sum+=a
print Sum

```
I was not sure how to incorporate numpy into this - suggestions welcome. This runs in 0.5225 seconds on my computer, as compared to the original which runs in 1.4488 seconds.

Here is the c++ code:
```

#include <stdio.h>
#include <time.h>
#define SIZE 1000000

int main ()
{
	clock_t start = clock();
	bool ar[SIZE+1];
	ar[0]=false;
	ar[1]=false;
	unsigned int i, j;
	unsigned int size;
	double sum=2;
	size=SIZE;
	
	ar[SIZE]=0;
	
	if (SIZE %2 != 0)
		size+=1;
	
	for (i = 3; i < size; i+=2)
		ar[i]=true;
		ar[i-1]=false;

	ar[2]=true;
	
	for (i = 3; i < size; i+=2)
		if (ar[i] == true)
			for (j = i*3; j < size; j += i*2)
				ar[j]=false;
	
	for (i = 3; i < size; i += 2)
		if (ar[i])
		{
			sum+=i;
		}
	clock_t end = clock();
	printf("Answer: %lf Took: %lf\n\n",sum,(double)(end-start)/CLOCKS_PER_SEC);
}

```
This runs in 0.01 seconds or so on my computer. Quite a difference eh? 50 times slower...But then, this is not exactly what Python is intended for.

Note - the code above (both Python and C++) could probably improved since I am somewhat rushing now. Anyway, enjoy :)

---

### Post by Wybiral on 2007-10-29
How are you timing the Python one? If you have the timer built into the C++ version, you wont have the load-time lag. If you're timing the Python from start to finish, you have to realize that it's being compiled into bytecode, loaded, then executed. You should time the algorithm, not the entire process.

---

### Post by smartbei on 2007-10-29
Here is how I do the timing:
```

from time import time

#functions defined here

t1=time()

#call first function

t2=time()

#call second function

t3=time()

print "func1:",t2-t1
print "func2:",t3-t2


```

I think that is pretty fair.

---

### Post by Wybiral on 2007-10-29
> **smartbei said:**
> I think that is pretty fair.

OK, I was just curious since your Python example didn't have any timer while your C example did. BTW, that is pure C, not C++, as a result you don't need  "using namespace std;" at all.

---

### Post by smartbei on 2007-10-29
You're right. The reason it is in there is because I was using iostream for light debugging (it is faster to type than printf) and forgot to take it out. I'll do that.

After averaging a couple more runs of the c++ program (the resolution of the time is rather low, only to the hundredth of the second) I get to around 0.015 seconds or so, so around 35 times faster.

---

### Post by hod139 on 2007-10-29
I'm confused here.  Why are you calling a C-style array of bools a bit array?  To my knowledge, the C-style array will use a full byte to store the bool value.  In your code, you do not play with any of the bits.

If you use a std::vector of bools, there is a specialization that will pack them into bits.

---

### Post by smartbei on 2007-10-29
I believe the OP meant bit arrays as in an array that only stores one of two values in each cell. In the c++ case, I don't care overmuch about how much memory the code takes since it is only a million items and I don't want the overhead associated with used a vector.

I believe you are right about a bool using a char actually to store the value. Well, you kind of have to be right, since the RAM only allows access by byte and I am not doing any fancy bit-shifting.

---

### Post by hod139 on 2007-10-29
> **smartbei said:**
> I believe the OP meant bit arrays as in an array that only stores one of two values in each cell.
When I hear bit array, this is what I think: [http://en.wikipedia.org/wiki/Bit_array](http://en.wikipedia.org/wiki/Bit_array)
And you get this for free if you use std::vector<bool>

> 
... and I don't want the overhead associated with used a vector.

The overhead of a std::vector versus a C-style array is really minimal, and the added benefits (IMO) far outway the small performance cost.  In this situation, a std::vector<bool> would be more efficient (at least in space), since the vector will pack each bool into a single bit for you.

---

### Post by slavik on 2007-10-29
bit arrays are nice when you want to have a long one (buffered output), very useful in huffman coding ;)

---

### Post by Slychilde on 2007-10-30
> bit arrays are nice when you want to have a long one (buffered output), very useful in huffman coding 

Thank you, I'll have to look up what that is.  That's exactly what I was looking for.  I also looked at the wikipedia entry mentioned below, but I don't think I understood most of it, especially what it's used for.

I read your code and it all makes sense now.  It takes about 1/3 of the time on my pc than the original - nice!    What is the xrange(start, stop, increment) function you called, i.e. how is it different from normal range?  I looked it up in the python docs and the explanation went over my head.  I also couldn't find a good explanation of numpy, either.

---

### Post by smartbei on 2007-10-30
The difference between xrange and range is that range actually returns a list of the numbers from start to end-1, while xrange returns an iterator object that always gives the loop the next value. This is generally faster for one-time-use lists like those generated in "for"s because very little memory needs to be allocated as compared to the regular range, especially when the length of the list is > 10,000 or 100,000 items.

---

### Post by pmasiar on 2007-10-30
range() generates whole list when called (which can consume huge amount of memory), xrange() generates it item by item, and is more usefull if you don't need to store items afterwards. If you store all xrange() items, they consume same memory as range().

---

### Post by slavik on 2007-10-30
think of xrange as a lazy list generator, generating one item at a time as it is asked for it.

if you want to loop for 1..10, then there isn't much point in xrange, but if it's something like 1..inf then range WILL (and must) fail ...

---

### Post by Slychilde on 2007-11-01
Ok, that makes sense; like how you can use range to popluate an array: primes = range(10).

Not to beat a dead horse, but I've been rewriting some of these in Java, to re-acquaint myself with the language and I can't figure out how to duplicate my code 100%, mainly populating the array with the [false, true] pattern.  Any suggestions?  I know I could iterate over just the odds and ignore the evens since that's what I do in the main body anyways, but I'd like the array sievePrimes returns to be correct (i.e. reusable code).  My Java is quite poor. =\

```
import java.util.*;

public class Euler10
{
        public static boolean[] sievePrimes(int size)
        /*Sieves an array for primes up to a given size. Check above 
         *         comment for Sieve of Eratosthenes information.*/
        {
                boolean[] primes = new boolean[size +1];  //There has to be a better
                Arrays.fill(primes, true);              //way to do this.
                primes[0] = false;
                primes[1] = false;
                for (int i = 4; i <= size; i+=2) primes[i] = false;
                for (int i = 3; i <= size; i+=2)
                {
                        if (primes[i] == true)
                        {
                                for (int j = i*3; j < size; j += (i*2))
                                {
                                        primes[j] = false;
                                }
                        }
                }
                return primes;
        }

        public static void main(String[] args)
        {
                long sum = 2;           //the sum truncates in int, so using long.
                int size = 1000000;
                boolean[] primes = sievePrimes(size);
                for (int n = 3; n < size; n+=2)
                {
                        if (primes[n] == true) sum += n;
                }
                System.out.println(sum);
        }
}

```

---

### Post by smartbei on 2007-11-01
Take a look at my c++ code. It shouldn't be difficult to nearly copy it over to java with minimal changes, as I am not doing anything out of the ordinary.

EDIT:
It looks like that is what you are already doing. Why do you think that there is necessarily a better way to do this?

---

### Post by Slychilde on 2007-11-02
primes = [0,1] * size/2 is so much more elegant imo, and gets rid of a for loop.

---

### Post by CptPicard on 2007-11-02
> **Slychilde said:**
> primes = [0,1] * size/2 is so much more elegant imo, and gets rid of a for loop.

In Java you just have to live with the for loops in general, as it doesn't have the kind of list handling abstractions built into the language itself that Python does...

---

### Post by Wybiral on 2007-11-02
> **smartbei said:**
> Take a look at my c++ code.

C code! There's nothing C++ about it :) (in fact, this isn't a problem for C++ to solve anyway, if you want speed and less abstraction, C is what you should use).

After taking a look at your C vs Python implementations, I have a few complaints.

First is that sievePrimes is in a function for Python and not for C? That's not fair :p

Second is that the list is being dynamically generated and then returned in the Python version, while being locally allocated in C.

Third is the summation, in Python you're comparing the element with 1, in C you're just checking if it's true. The first requires the condition to be true (element == 1) then the result to be a boolean true, while the second treats the element itself as a boolean.

Here's my test, which clocks Python in at about (4.96 - 5.10) and C in at about (0.95 - 0.98) which is only a 5 fold difference (as opposed to 50). Of course I'm just being nit-picky, you were right to say that this isn't what Python is intended for... But I wanted to be fair (because Python isn't nearly as slow as most people assume).

The purpose of each function is to dynamically generate a list of 0'a and 1's that maps the primes for the given size.

```

"""
    python test.py
"""

from time import clock

def sievePrimes(size):
    if size & 1:
        size += 1
    l = [0, 1] * (size / 2)
    l[:2] = 0, 0
    for a in xrange(3, size, 2):
        if l[a]:
            for b in xrange(a * 3, size, a * 2):
                l[b] = 0
    return l

size = 10000000
t1 = clock()
primes = sievePrimes(size)
t2 = clock()
print("Time: %f" % (t2-t1))

```

```

/*
    gcc test.c -std=c99
    ./a.out
*/

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

char *sievePrimes(unsigned int size)
{
    if(size & 1)
    {
        size++;
    }

    char *l = malloc(size);
    l[0] = 0;
    l[1] = 0;

    for(int i = 3; i < size; i += 2)
    {
        l[i] = 1;
        l[i-1] = 0;
    }

    l[2] = 1;

    for(int i = 3; i < size; i += 2)
    {
        if(l[i])
        {
            for(int j = i*3; j < size; j += i*2)
            {
                l[j] = 0;
            }
        }
    }

    return l;
}

int main(int argc, char *argv[])
{
    unsigned int size = 10000000;
    clock_t t1 = clock();
    char *primes = sievePrimes(size);
    clock_t t2 = clock();
    printf("Time: %f", (double)(t2 - t1) / CLOCKS_PER_SEC);
}

```

---

### Post by smartbei on 2007-11-02
Nice. You're right my mistake - code was in C.  Here is what is interesting: I compared one up to one million, with summing at the end, and I got to a rough 37 times better speed in C (read one of my other posts in this thread). When I try your programs, with the sizes changed to 1,000,000 I get to a similar value - around 0.33 seconds for python, and around 0.01 seconds for C.

At 10,000,000 I get 0.95 Seconds for the C version, and 3.79 seconds for the Python version (around 4 times faster in C). That seems like a huge speed difference. Am I missing something?

With my code, I get 5.4 seconds in python for 10,000,000 (Note: 4 seconds once I remove the summing loop) and a Segmentation Fault in C :D

---

### Post by Wybiral on 2007-11-02
> **smartbei said:**
> At 10,000,000 I get 0.95 Seconds for the C version, and 3.79 seconds for the Python version (around 4 times faster in C). That seems like a huge speed difference. Am I missing something?

It's possible that some pre-loop code was slower in Python instead of the actual loop itself (meaning the longer the loop, the closer the results might get). For a proper benchmark, you would want to test over a wide range of lengths, probably much higher than 1000000. You would also want to run this test SEVERAL times and sum up the times to get a fair estimate. C will probably always be faster unless Python performs some kind of optimization. I was just being picky and trying to reduce the gap some.

> **smartbei said:**
> ... and a Segmentation Fault in C :D

lol... That sounds like a pretty accurate way to sum up a comparison between Python and C :) In fact, I just noticed my version would leak memory...

---

### Post by wolfbone on 2007-11-02
> **smartbei said:**
> You may want to think about removing all of the even values...

Disclaimer: I haven't carefully read all the code and suggestions  put forward so far but the OP does lack a square root cutoff too.

---

### Post by smartbei on 2007-11-02
The square root cutoff does not apply to this prime-finding algorithm. See [http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)

EDIT: Yes, I know this is wrong, left here for thread clarity.

---

### Post by wolfbone on 2007-11-02
> **smartbei said:**
> The square root cutoff does not apply to this prime-finding algorithm. See [http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)

Heh! Of course Eratosthenes (and every mathematician since) must bow to the superior wisdom of *Wikipedia!

* To be fair to Wikipedia, the article does actually get it right in the pseudocode expression.

---

### Post by smartbei on 2007-11-02
Wow, can't believe I made that mistake. You're right, of course. A significant optimization would stop the elimination once the square root of the limit was reached.

---

