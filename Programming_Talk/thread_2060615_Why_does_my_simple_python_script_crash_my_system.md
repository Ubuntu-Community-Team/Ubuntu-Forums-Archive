---
title: "Why does my simple python script crash my system?"
date: 2012-09-20
forum: Programming Talk
---

### Post by iclestu on 2012-09-20
Hey guys,

I am a novice programmer at best but i do like to play around with the problems on projecteuler.net.  I concentrate on getting some 'general' algorithm to work out the answer and am not overly concerned about asthetics as (usually!) i am the only one to read my code and i am not generally picky about going about things the 'wrong way' unless they stop my code from working....

I am working on problem 243 and have a little python function, to which i pass an integer, *d*, and a list of the prime divisors of d, *prmList* and the function returns the number of integers between 1 and d-1 which is co-prime with d.

Given that even with efficient gcd algorithms this was too slow to implement directly I am approaching it in a similar way to the sieve of erothasenes for primes in that have an array of bool values (of length d) initialised at True (except d[1] as 1 is always coprime with d). I then cycle through the primes in *prmList* changing every multiple of it to False in the array then return the sum of the 1's in the array....

Hope that makes sense! Here is the code:

```
def resNum1(d,prmList):
  isRes=[0,1]               ####
  for i in range(2,d):   ### these lines just initialise array
    isRes.append(1)    ###
  for i in prmList:
    tmp=i
    while tmp<d:
      isRes[tmp]=0
      tmp+=i
  return sum(isRes)
```This works great when I pass it all values up to (2*3*5*...*19,[2,3,5,...,19])

but it crashes my whole system if i pass it the values (2*3*5*...*19*23,[2,3,5,...,19,23])

Why?

I know I am giving it much more work (23 times more) but when i hit ctrl+esc to try and kill it my system monitor suggests its taking up 1.2Gb of memory!!!

How it that possible? Surely that array (well, i know its actually a list) of bools cant take up THAT much space?

any gurus able to enlighten me as to whats going on?

---

### Post by Bachstelze on 2012-09-20
[http://effbot.org/zone/python-list.htm#performance](http://effbot.org/zone/python-list.htm#performance)

---

### Post by iclestu on 2012-09-20
> **Bachstelze said:**
> [http://effbot.org/zone/python-list.htm#performance](http://effbot.org/zone/python-list.htm#performance)

:confused:I dont get it....

Sorry

---

### Post by iclestu on 2012-09-20
> **iclestu said:**
> :confused:I dont get it....

Sorry

well i DO get that there is a MUCH easier way to initialise my list :D but dont get why my function crashes everything above a certain value

---

### Post by vexorian on 2012-09-20
2*3*5*7*11*13*17*19*23 = 223092870

You will run append d-3 times. ( 223092870 * 4 ) / 1024 / 1024 is 851 MB (That's a lot of MB, it can freeze your system if you don't have enough RAM). And since you use append every time, you will keep allocating memory. It crashes everything over a certain value, because that is the limit of your system.

Edit: When d is 2*3*5*7*11*13*17*19 then you only need 37 MB, so it is not a wonder there is such a strong difference (not crashing vs crashing) between 37MB and 851MB.

What you could do is this:

```

isRes=[1]  * d
isRes[0] = 0

```
It does the same as your loop, but only allocates once. The problem is that even in that way, 851MB may be too heavy for you.
---
I think you are approaching the whole problem the wrong way.

Your improvement to use sieve of Erathostenes is not that good. Originally you would use O(d * log(d)) operations (log(d) are needed for Euclid's gcd (I hope you were using Euclid's gcd). With your current approach, you are going to need about the same in CPU time, but O(d) memory.

So, regarding how to solve this project Euler problem. I will only share a suggestion: 
* The maximum number of prime factors of a number is O(log(n)).
* Given a number X, can you count the number of multiples of X and are less than d?
* Ever heard of inclusion-exclusion? How to count the number of numbers less than d that are multiples of X *or* Y?

---

### Post by iclestu on 2012-09-20
> **vexorian said:**
> I think you are approaching the whole problem the wrong way.

Story of my life but, that's half the fun! :D

> **vexorian said:**
> 
2*3*5*7*11*13*17*19*23 = 223092870

You will run append d-3 times. ( 223092870 * 4 ) / 1024 / 1024 is 851 MB (That's a lot of MB, it can freeze your system if you don't have enough RAM). And since you use append every time, you will keep allocating memory. It crashes everything over a certain value, because that is the limit of your system.

What you could do is this:

```

isRes=[1]  * d
isRes[0] = 0

```It does the same as your loop, but only allocates once. The problem is that even in that way, 851MB may be too heavy for you.
 
Ok - will give this approach a try...

> **vexorian said:**
> 


Your improvement to use sieve of Erathostenes is not that good. Originally you would use O(d * log(d)) operations (log(d) are needed for Euclid's gcd (I hope you were using Euclid's gcd). With your current approach, you are going to need about the same in CPU time, but O(d) memory.

Hmm - im not great on this amortised log O(n) time stuff :) but i WAS using Euclids algorithm and anecdotally it seemed to make a decent difference when i tried running both functions one after another


> **vexorian said:**
> 
So, regarding how to solve this project Euler problem. I will only share a suggestion: 
* The maximum number of prime factors of a number is O(log(n)).
* Given a number X, can you count the number of multiples of X and are less than d?
* Ever heard of inclusion-exclusion? How to count the number of numbers less than d that are multiples of X *or* Y?

I will give the last question some thought as I do see where you are going (never heard of inclusion-exclusion) 

I HAD considered just dividing d by each i in prmList but would then need to take off the number divided by 2 divisors and it got all complicated when i started to think of the multiple divisor possilities!!! (which is, of course, why you asked if i could find a way to find out if its divided by X or Y). 

Getting back to my original approach COULD work... Was getting close to the target ratio in reasonably quick computation times till the sudden crash! (quite apart from solving the euler puzzle, id like to work out whats going wrong with the above code)

I also just noticed that it crashes with the first value that would be a LONG integer. Is that the problem or do you reckon its the LIST.append thing?

Anyway - Many Thanks for your help, its appreciated

---

### Post by vexorian on 2012-09-20
There are currently two possibilities. One is that 851MB is too big for your system. The other is that it is not too big for your system, but running append that many times is (I think your allocation approach might as well triple the needed memory, append is allocating too frequently ). So, perhaps your approach will work once you get rid of all those .append calls. But if it does not, then you will need to use an approach that does not need O(d) memory.

---

### Post by iclestu on 2012-09-20
> **vexorian said:**
> There are currently two possibilities. One is that 851MB is too big for your system. The other is that it is not too big for your system, but running append that many times is (I think your allocation approach might as well triple the needed memory, append is allocating too frequently ). So, perhaps your approach will work once you get rid of all those .append calls. But if it does not, then you will need to use an approach that does not need O(d) memory.

:)

Yeah, taking out those .append()'s helped but not quite enough! Its excruciatingly close to the required ratio with 2*3*5*...*23 and anything higher crashes again...

I guess 'attempting' the next logical choices in the website without actually computing them isn’t really in the projecteuler spirit!!! (nor is buying an extra couple of gb of RAM for that matter!!!). 

As such ill find a means to look at the method you suggested (having had a quick google, I am familiar with the *inclusion-exclusion* principles you referred to but just was not familiar with the term itself). Guess my code is about to get a little more complicated!

Many Thanks again for lending me your helpful knowledge.

Incidentally - if this was implemented in an actual array (in C or something) would it dramatically cut down on memory usage? I remember reading something today that suggested a python list uses memory according to the number of elements rather than the size of those elements? 

I only need a single bit for each bool value.....

No matter - an euler solution ought not really to need to utelise swap space! :D

---

