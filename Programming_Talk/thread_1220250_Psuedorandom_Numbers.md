---
title: "Psuedorandom Numbers"
date: 2009-07-22
forum: Programming Talk
---

### Post by Godd on 2009-07-22
I was thinking about the Random Number Generator in Python and I decided to see about analyzing the output.

The first thing that came to mind was to generate a range from 0 to 100 and count the number of times the generator repeated numbers.

[PHP]#!/usr/bin/python
#for me

import random

repeat = 0


randlist = []
repelist = []

while len(randlist) < 100:
    suitor = random.randrange(0,100,1)
    if randlist.count(suitor) != 0:
        repeat = repeat + 1
    if randlist.count(suitor) == 0:
        randlist.append(suitor)
        repelist.append(repeat)


print repeat,"numbers were repeated"

print repelist
[/PHP]

I graphed this data.(In the attached file)

As the number of filled slots in the list increases to expect to see the number of repeats increase. So I was expecting an exponential graph. Which I got. 

However, the hills in the graph are the interesting things, the greater the size/number of hills I believe to be the psuedo in psuedorandom.

I'm currently writing a code to check the number of conncurrent random numbers in multiple instances of the generator.

I don't know of a way to directly output the data into graph form, I input it manually. If someone could make an example code I could output more data for analysis.

EDIT: Let me also add that I am no mathematician. I'm just putting the data up for analasys. And to learn for that matter.

---

### Post by smartbei on 2009-07-22
IANAC (I Am Not A Cryptanalyst) but...
In general, to analyze the distribution of random numbers, where each number is of the size X (in your case, 100), you will want far, far more than X numbers. Think along the lines of X**2 or more. Otherwise, the statistical distribution will be meaningless.

Also, the random number generator in python is the Mersenne Twister ([http://en.wikipedia.org/wiki/Mersenne_twister](http://en.wikipedia.org/wiki/Mersenne_twister)). It is actually especially good at exactly what you are trying to test. It has been extensively studied academically and it's distribution is perfect in this manner, as long as a very big test set is used (which is exactly how it should be).

Here are the results of a simple test I conducted:
```

d = {}
for a in xrange(256):
    d[a] = 0
for a in xrange(10**6):
    d[random.randrange(0, 256)] += 1

```
and the results:
```

min(d.values()) ## == 3732
max(d.values()) ## == 4103
avg(d.values()) ## == 3907

```
In summary, pretty well-distributed.

---

### Post by Godd on 2009-07-22
I did a run of the program 100000 times but I wasn't able to compute all of the data.

How can I average the corresponding numbers in two lists? I remember in the very early portions of the python tutorial there was was to do it so I'll go back and re-read it.

---

### Post by Can+~ on 2009-07-22
[PHP]#!/usr/bin/python
#for me

import random
from pylab import plot, show

#your code

plot(repelist, linestyle='None', marker='+')
show()
[/PHP]

Requires library python-matplotlib

---

### Post by CptPicard on 2009-07-22
I would be very surprised if these sorts of tests showed anything of interest, you'd at least run a proper statistical test. :)

---

### Post by Godd on 2009-07-22
@ Can+~

 SWEET! Thankyou again! I Always like finding cool modules. And I've been dying to find an innate graphing function within python. I'll have to do some reading on that sweet function tonight.

---

### Post by Godd on 2009-07-22
@Picard 

*Facepalm*

I'm a mechanical/electrical engineering major. Ha. I'm really new to coding, much less statistical analysis. 

I'm good at interpreting graphs but thats about the extent of my statistics knowledge. Ha. I just thought this would be an interesting topic of discussion. Ha.

---

### Post by MadCow108 on 2009-07-22
you're not going to see much from the generated random of a mersenne twister or other sophisticated algorithms.

But if you like to see something implement a simple linear congruential generator r = (a*r+c) mod m with no though put into the choice of parameters a, c and m.
you'll see some interesting effects if you plot pairs of random numbers :)

tests of pseudorandom numbers consist of the test of uniformity and independance.
First can be tested with frequency tests (chisquare tests, Kolmogorov-Smirnov test)
The latter by all sorts of correlation tests, gab test combined with Kolmogorov-Smirnov or poker tests combined with chisquare test.

google should bring further material about mentioned methods (the list is far from complete)

---

### Post by soltanis on 2009-07-22
look into xgraph, its a pretty simple program that takes straight text data and graphs it.

---

