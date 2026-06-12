---
title: "Project Euler 26..."
date: 2008-06-30
forum: Programming Talk
---

### Post by KMuchane on 2008-06-30
Habari,
It costs me a leg and a limb just to contact you guys and I am grateful, but I have a little problem... good old euler...

I am trying to solve Problem Number 26
([http://projecteuler.net/index.php?section=problems&id=26](http://projecteuler.net/index.php?section=problems&id=26)) on Project
Euler but apparently the answer I am submitting is wrong.

Here is the problem:


A unit fraction contains 1 in the numerator. The decimal representation
of the unit fractions with denominators 2 to 10 are given:

        1/2
        = 
        0.5
        1/3
        = 
        0.(3)
        1/4
        = 
        0.25
        1/5
        = 
        0.2
        1/6
        = 
        0.1(6)
        1/7
        = 
        0.(142857)
        1/8
        = 
        0.125
        1/9
        = 
        0.(1)
        1/10
        = 
        0.1

Where 0.1(6) means 0.166666..., and has a 1-digit recurring cycle. It
can be seen that 1/7 has a 6-digit recurring cycle.

Find the value of d < 1000 for which 1/d contains the longest recurring
cycle in its decimal fraction part.

I am giving the answer 38, because 1/38 = 0.0263157894. It seems I have
misunderstood the question or I cant solve it! Here is the code(in
Python) that I
came up with:

def aux(num):
        import re
        pattern = re.compile(r"^0?1?2?3?4?5?6?7?8?9?$")

        frac ="%.9f"%(1.0/num) 
        fracSlice = frac[2:]                    # get the decimal
fractional part, ie remove
'0.'
        
        fracList = list(fracSlice)              #convert string to a
list
        fracList.sort()                                 # I need to
sort , because I will be searching by
increasing order
        
        testFrac  = "".join(fracList)   # convert list back to a string,
phew!
        if re.match(pattern,testFrac):  # if the pattern matches, the
number is
our candidate
                print (num,fracSlice)
        
                
for b in xrange(1,1000):
        aux(b)

Er... er, that does not exactly work as expected but it narrows the
search to only 3 candidates because of the inclusion of the zero:

 (28, '035714286')
 (38, '026315789')
 (81, '012345679')

For 28, the digit, in the fractional part, after 8 is 5, so 5 is
repeated and as for, 81 the next digit after 7 is 0, so again 0 occurs
twice. But for 38, the next digit after 9 is 4, and because it has NOT
occurred before, I assume 38 is the correct answer... and I am wrong! 

I suspect I have completely misunderstood the question.

Any ideas?
Thanks!

Kinuthia...

---

### Post by Tony Flury on 2008-06-30
Just a thought :

I don't think you can guarantee that just because a single digit appears again - that the fractional part will repeat from then on in.

I have no idea how to translate the problem to code - but i don't think you can make the assumption that you do.

---

### Post by KMuchane on 2008-06-30
Thanks Tony,  I am wondering what the question is in the first place  :-)

---

### Post by Bichromat on 2008-06-30
This should help: [http://ubuntuforums.org/showthread.php?t=783653&page=6](http://ubuntuforums.org/showthread.php?t=783653&page=6)
One problem with your code is that you use floating point numbers which have a limited precision. You actually need to do the division step by step, the same way you would do by hand, to get all the digits.

---

### Post by Lster on 2008-06-30
Without giving too much away I'll say: you should have a look for something on decimal expansion. If you still need help after, and you would like me to, I will give you a few hints via PM.

---

### Post by MadnessRed on 2009-09-08
> **Bichromat said:**
> This should help: [http://ubuntuforums.org/showthread.php?t=783653&page=6](http://ubuntuforums.org/showthread.php?t=783653&page=6)
One problem with your code is that you use floating point numbers which have a limited precision. You actually need to do the division step by step, the same way you would do by hand, to get all the digits.

Or you can use long int, rather than dividing 1/d, try (1**10000)/d, that will allow you to find recurring cycles which are less than 5,000 which is enough.

Also here's a hint at finding the remainder recuring cycle

```

	for p in range(1,10001):
		if n[100:100+p] == n[100+p:100+p+p] == n[100+p+p:100+p+p+p] == n[100+p+p+p:100+p+p+p+p]:

```

That allows for 100 digits before the recuring cycle and for recuring cycles shorter than abut 2000. Obviously you can have recurring decimals which do not fit into this but there are none for 1/d, d<1000
Also its not conclusive proof of recurring it only tests for it 4 times.

---

### Post by Paul Miller on 2009-09-08
This one is easier to solve mathematically than to write a program for it.  I'd suggest looking at a couple elementary number theory books.

---

### Post by zobayer1 on 2010-12-11
> **Paul Miller said:**
> This one is easier to solve mathematically than to write a program for it.  I'd suggest looking at a couple elementary number theory books.

Yeah, there is an elegant solution based on prime number properties.

---

