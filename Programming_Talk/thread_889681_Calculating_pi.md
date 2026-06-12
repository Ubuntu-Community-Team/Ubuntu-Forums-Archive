---
title: "Calculating pi?"
date: 2008-08-14
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-08-14
I've always wondered how to do this but i have no clue on how to go about it

i want to create a console app that keeps on computing pi until i close the app (and have the app not lock up because it is in an infinite loop)

i have tried the basic 22.0/7.0 in python and that only gets me the first few digits the same with using doubles in C# and floats in C++

i checked google and wikipedia and i got nothing for typing in "pi calculation programming algorithm"

i have a feeling im going to get a simple answer that i missed somewhere

thanks for any help with this and it will probably teach me something i will need later

---

### Post by Zugzwang on 2008-08-14
Wikipedia? There are plenty of methods for computing Pi in the [Pi]("http://http://en.wikipedia.org/wiki/Pi") article.

---

### Post by azr on 2008-08-14
I have been meaning to get around to doing something similar, but never struck upon a good idea. However - this [http://www.math.hmc.edu/funfacts/ffiles/20010.5.shtml](" this ") looks promising. It describes a way to calculate the Nth digit of pi, albeit in base 16.

---

### Post by Qtips on 2008-08-14
Hi,

One solution to approximate the value of pi come from the book : Python programming - An introduction to computer science from John Zelle. 

You need to sum the terms in the following series:
4/1 - 4/3 + 4/5 - 4/7 + 4/9 - 4/11 + ...

My program to do it is the following:

> # pb15ch3.py
# Write a program that approximates the value of pi by summing the terms of this series:
# 4/1 - 4/3 + 4/5 - 4/7 + 4/9 - 4/11 + ...
# The program should prompt the user for n, the number of terms to sum, and then output the
# sum of the first n term of this series. Have your program substract the approximation from 
# the value of math.pi to see how accurate it is.

def main():
	import math

	print
	print "This program approximate the value of pi by summing a series of n terms."

	n = input("Enter the numbers of terms to be summed: ")

	sum = 0
	for i in range(n):
		sum = sum + 4.0 * (-1) ** i / (2 * i + 1)

	accuracy = 100 * abs(math.pi - sum) / sum

	print "The approximation of pi with", n, "terms is", sum
	print "The accuracy of this approximation is", accuracy, "%."

	print

main()

Hope this helps.

---

### Post by Lster on 2008-08-14
For the fun of it, I've coded up the following to program to demonstrate calculating pi.

The first program see quite slow to converge and uses the information from:

[http://en.wikipedia.org/wiki/Pi#Classical_period](http://en.wikipedia.org/wiki/Pi#Classical_period)

[PHP]
#This method seems quite slow.

from decimal import Decimal

one = Decimal(1)

pi = 0

i = 0
sign = 1
while i <= 100:
	pi += sign*one/Decimal(2*i+1)
	sign *= -1
	i += 1

pi *= 4
print pi
[/PHP]

This program seems much faster to calculate digits with:

[PHP]
#This method seems better!

from decimal import Decimal, getcontext

getcontext().prec = 100
one = Decimal(1)
sixteen = Decimal(16)

pi = 0

k = Decimal(0)
while k <= 100:
	pi += sixteen**(-k)*(4/(8*k+1)-2/(8*k+4)-1/(8*k+5)-1/(8*k+6))
	k += 1

print pi
[/PHP]

:popcorn:

---

### Post by NovaAesa on 2008-08-14
You might want to check out [http://en.wikipedia.org/wiki/Gauss%E2%80%93Legendre_algorithm](http://en.wikipedia.org/wiki/Gauss%E2%80%93Legendre_algorithm). It's converges to pi very quickly, but uses alot of memory.

---

### Post by jimi_hendrix on 2008-08-14
any way i can get it so i can do 22.0/7.0 and it doesnt round?

---

### Post by Lster on 2008-08-14
What do you mean? Do you want fractions?

---

### Post by finer recliner on 2008-08-14
> **jimi_hendrix said:**
> any way i can get it so i can do 22.0/7.0 and it doesnt round?

22/7 does not equal pi. it was used as an approximation way back in the old days.

---

### Post by eddVRS on 2008-08-14
> **jimi_hendrix said:**
> any way i can get it so i can do 22.0/7.0 and it doesnt round?
 
22/7 is not pi, but merely an approximation-
 
22/7 = 3.14285714285714 [to 14DP]
[COLOR=white]....[/COLOR]pi = 3.14159265358979 [to 14DP]

<edit> the finer recliner beat me to it :p </edit>

---

### Post by jimi_hendrix on 2008-08-14
so i better get used to the big formulas...ill try it out later and post my code

---

### Post by lukjad on 2008-08-14
I was always interested to learn how to calculate pi. Whenever I would ask my teachers I would get the brush off. So, you take 4 and divide it by 1 and subtract 4 divided by the next odd number? Then 4/5 - 4/7 etc.?

---

### Post by Zugzwang on 2008-08-14
Note that you will have too look into computing using big floats. If you just use the regular "double" or "float" data types, then the precision is limited anyway so you can just use the constants provided in the respective language - you won't get any closer.

---

### Post by eddVRS on 2008-08-14
there is a CLI based app to calculate pi. Might be worth having a look to see how they calculate...

---

### Post by jinksys on 2008-08-14
> **lukjad007 said:**
> I was always interested to learn how to calculate pi. Whenever I would ask my teachers I would get the brush off. So, you take 4 and divide it by 1 and subtract 4 divided by the next odd number? Then 4/5 - 4/7 etc.?

Pi is simply the ratio of a circles circumference to its diameter.

The equation for the circumference of a circle is C=Pi*D, which D being the diameter.  Solve this for Pi and it becomes, Pi=C/D.

If you wish to calculate Pi for yourself, go trace a circle onto a sheet of paper.  Get a string and measure the diameter and circumference.  Plug your numbers into the above equation and you have an approximation of Pi.  This is why our approximation of Pi gets better as technology progresses.  We now have computers that can measure circles very accurately.

---

### Post by hod139 on 2008-08-14
My favorite way (not the fastest by a long shot though) of calculating Pi is by throwing darts (Monte-Carlo simulation).  We actually had a thread related to this some time back ([http://ubuntuforums.org/showpost.php?p=2695585&postcount=11](http://ubuntuforums.org/showpost.php?p=2695585&postcount=11))

---

### Post by tamoneya on 2008-08-14
recession of fourths (4/1-3/4+5/4-7/4 ...) does eventually converge on PI however it converges VERY slowly.  I would recommend that you use this formula.[IMG]http://upload.wikimedia.org/math/0/3/7/037bcc5ddc36d7cb44f83b6c5365027f.png[/IMG]

---

### Post by jimi_hendrix on 2008-08-14
dumb math question...what does the greek E (epsilon?) mean in math

---

### Post by Kadrus on 2008-08-14
If i am not mistaken Sigma.

---

### Post by happysmileman on 2008-08-14
> **jimi_hendrix said:**
> dumb math question...what does the greek E (epsilon?) mean in math

It means "sum of" AFAIK, so the equation above would be you do it for k from 0 - infinity (Maybe don't go quite that high to save some time) and add up all the results

---

### Post by tamoneya on 2008-08-14
the E is actually a Sigma which is roughly equivalent to "S". what it means is you sum the terms between two limits of a variable.  In this case we are summing from k = 0 to k = infinity.  And we the expression we are summing is all the crap to the right of the sigma.  I dont feel like writing it but lets call it f(k).  In summary: pi = f(0) + f(1) + f(2) ... F(infinity).  So if you keep recursively adding f(k) you will converge on pi.

---

### Post by cszikszoy on 2008-08-14
the "E", is not Epsilon.  It's Sigma.  They use Sigma to represent an infinite **S**um.

I used to TA and Tutor C++ and Java programming at my University.  One of my favorite assignments to give was to teach beginning programmers to use loops to approximate things like pi and e^x using an infinite series.

Part of the assignment was to determine how many iterations of the loop (or sum) it took for the approximated value to come to within 1 * 10^-10 of the "built-in" value for whatever was being approximated.

I've wanted to propose this exact problem as the next "Beginner Programming Challenge", but I did'nt want step on LaRoza's toes.  I sent him a Message with my problem proposal, and saying I would help out...

**AHEM LaRoza... if you're reading this, check your PM Inbox...**

---

### Post by jimi_hendrix on 2008-08-14
> **cszikszoy said:**
> 
I've wanted to propose this exact problem as the next "Beginner Programming Challenge", but I did'nt want step on LaRoza's toes.  I sent him a Message with my problem proposal, and saying I would help out...

**AHEM LaRoza... if you're reading this, check your PM Inbox...**

actually figuring this out would make a good challenge...but a different formula would work...like Celsius to Fahrenheit or vise versa only harder with things like sigmas and sines that would take some work

---

### Post by cszikszoy on 2008-08-14
> **jimi_hendrix said:**
> actually figuring this out would make a good challenge...but a different formula would work...like Celsius to Fahrenheit or vise versa only harder with things like sigmas and sines that would take some work

What I suggested to LaRoza was to do things like decimal approximations of Taylor series functions, such as ln(1-x), e^x, and all trigonometric functions.  That was always one of my favorite assignments to give and explain :)

---

### Post by jimi_hendrix on 2008-08-14
what im saying is (this may be what your suggesting because i have non clue what the taylor series of functions is...) but im  saying is you could have a great challenge if you take the formula for the distance of a projectile it uses some obscure math as well as order of operations and this would teach you the ability to do complex math (programming is all math after all)

---

### Post by nickgaydos on 2008-08-14
Man, I can't even understand dimension of shapes or whatever that well :P

---

### Post by cszikszoy on 2008-08-14
> **jimi_hendrix said:**
> what im saying is (this may be what your suggesting because i have non clue what the taylor series of functions is...) but im  saying is you could have a great challenge if you take the formula for the distance of a projectile it uses some obscure math as well as order of operations and this would teach you the ability to do complex math (programming is all math after all)

Taylor series is easy.
[IMG]http://upload.wikimedia.org/math/9/4/c/94c80ea78d3a7bc148500c303f13d324.png[/IMG]and also
[IMG]http://upload.wikimedia.org/math/0/0/2/0028748ab96e054f7ea813bb9f19d69f.png[/IMG]
Add those up forever and you get the value of e^x and sin(x)

**from wikipedia.com

---

### Post by tamoneya on 2008-08-14
> **cszikszoy said:**
> Taylor series is easy.
[IMG]http://upload.wikimedia.org/math/9/4/c/94c80ea78d3a7bc148500c303f13d324.png[/IMG]and also
[IMG]http://upload.wikimedia.org/math/0/0/2/0028748ab96e054f7ea813bb9f19d69f.png[/IMG]
Add those up forever and you get the value of e^x and sin(x)

**from wikipedia.com

While those are examples of taylor series just knowing that doesnt mean you know taylor series.  You need to know derivatives.  This is one of the reasons why it shouldnt be a programming challenge.  While math is important and closely linked with computer science there is no reason to require calculus for a beginner challenge.

---

### Post by cszikszoy on 2008-08-14
> **tamoneya said:**
> While those are examples of taylor series just knowing that doesnt mean you know taylor series.  You need to know derivatives.  This is one of the reasons why it shouldnt be a programming challenge.  While math is important and closely linked with computer science there is no reason to require calculus for a beginner challenge.

While I agree that the derivations are important, the object is to illustrate the mechanics of loops.  The point is to prove to beginners that you can do powerful things with programming.  I have a double major in Electrical Engineering and Computer Engineering, and a minor in math - I've done enough derivations :)

While derivations are important, they aren't the end-all-be-all.  You don't ask a 4th grader to derive pythagorean's theorem, yet, they are still required to know how to use it.  Programming is the same way!  You don't ask someone to 'derive' all of the functions in the C stdlib, you teach them how to *use* them.

---

### Post by tamoneya on 2008-08-14
> **cszikszoy said:**
> While I agree that the derivations are important, the object is to illustrate the mechanics of loops.  The point is to prove to beginners that you can do powerful things with programming.  I have a double major in Electrical Engineering and Computer Engineering, and a minor in math - I've done enough derivations :)

While derivations are important, they aren't the end-all-be-all.  You don't ask a 4th grader to derive pythagorean's theorem, yet, they are still required to know how to use it.  Programming is the same way!  You don't ask someone to 'derive' all of the functions in the C stdlib, you teach them how to *use* them.

When I said derivatives i meant as in d/dt.  That comment was mostly pointed at your claim: "taylor series are easy" and then just showed to examples of a taylor series.  You didnt explain at all what it is and how they are found or what their significance.  As for programming challenges you can teach the same thing but instead use simpler series that dont come from calculus.  Exmamples would be the Fibonacci sequence or pascals triangle.

---

### Post by hosk on 2008-08-14
While we're on the subject of difficult things for beginner programmers to do, how about the Jacobi method. OH SNAP, can't you use that for making images like, uglier? Double bonus!!

---

### Post by slavik on 2008-08-15
look up the "Chudnovsky method" or "Ramanujan pi", both are supposedly accurate pi representations.

---

### Post by Lux Perpetua on 2008-08-15
As has been noted, the series 4 - 4/3 + 4/5 - 4/7 + 4/9 + ... converges very slowly. How slowly: being generous, computing N terms gives you absolute accuracy of only about 1/N. Want 4 digits after the decimal? No problem, just compute 10,000 terms!

One that I like is the infinite product of nested radicals

2/pi = sqrt(1/2) * sqrt(1/2*(1 + sqrt(1/2))) * sqrt(1/2*(1 + sqrt(1/2*(1 + sqrt(1/2))))) * ...

It's also a rather old formula (16th century) and easy to prove using trigonometry alone, no calculus. It converges tolerably fast: with the first N factors, your absolute error in approximating pi is about (pi^3)4^(-N)/24.

---

### Post by wenuswilson on 2008-08-15
> **jimi_hendrix said:**
> dumb math question...what does the greek E (epsilon?) mean in math

"If epsilon is greater than zero then for all integers N there exists an integer n greater than N such that the absolute value of the infinite sequence x 'sub' n minus the limit L is less then epsilon."

That's how I know epsilon. Proving limits where epsilon is *any* real number greater than zero.

Otherwise it's used in physics "epsilon zero" to mean "permittivity  of free space" equaling ~ 8.854 187 817 x 10^-12 F/m. [Constant taken from [Physics reference]("http://www.alcyone.com/max/reference/physics/constants.html")]

---

### Post by lordhaworth on 2008-08-15
One quite cool way of using a program to find PI is to approximate it using Monte Carlo Methods.

You program a square of radius **2R** containing a circle radius **R**
[IMG]http://code.google.com/edu/parallel/img/inscribe.png[/IMG]
then use a random number generator to simulate "throwing darts" at this square/circle. Then PI can be found as the ratio

    PI / 4 = Number Of Darts In Circle / Number Of Darts in total

You will find that the more darts you throw the closer the approximation will be.

---

### Post by lordhaworth on 2008-08-15
If you have any other questions on how that works ^ just ask!

The accuracy of this method depends on your patience

---

### Post by Lster on 2008-08-15
The Monte Carlo method seems quite slow really. I didn't throw darts - instead I just tried each point.

[PHP]

#This method basically tries every point in a one quadrant of a circle.
#As pi*r^2 = area, pi = area/r^2; but the area we calculated is only one
#quarter, so we must multiply by 4.

n = 100

count = 0
for x in xrange(n):
	for y in xrange(n):
		if x**2+y**2 < n**2:
			count += 1

count = float(4*count)
count /= n**2

print count

[/PHP]

The other way, mentioned by NovaAesa, is the Gauss-Legendre algorithm:

[http://en.wikipedia.org/wiki/Gauss%E2%80%93Legendre_algorithm](http://en.wikipedia.org/wiki/Gauss%E2%80%93Legendre_algorithm)

[PHP]
from decimal import Decimal, getcontext

getcontext().prec = 50
m = 10

a = [0]*m
b = [0]*m
t = [0]*m
p = [0]*m

one = Decimal(1)
two = Decimal(2)
four = Decimal(4)
half = one/two

a[0] = one
b[0] = one/two**(one/two)
t[0] = one/four
p[0] = one

lastpi = 0

for n in xrange(m-1):
	a[n+1] = (a[n]+b[n])/two
	b[n+1] = (a[n]*b[n])**half
	t[n+1] = t[n] - p[n]*(a[n]-a[n+1])**2
	p[n+1] = two*p[n]
	
	pi = (a[n+1] + b[n+1])**2/four/t[n+1]
	if lastpi == pi: break
	lastpi = pi

print n, pi
[/PHP]

:popcorn:

---

### Post by jimi_hendrix on 2008-08-15
so i have this code
[PHP]#!/usr/bin/env python
#
#       pi.py



def main():
	K = 0
	calculate();
	#print calculate()
	return 0

def calculate():
	k = 0
	times = 100
	while k <= times:
		pi = (1/16**k)((4/8*k + 1)(2/8*k+4)(1/8*k+5)(1/8*k+6))
		k += 1
		print pi
	return pi
if __name__ == '__main__': main()
[/PHP]

but i get something on how an int isnt callable when i run it?

---

### Post by Lster on 2008-08-15
That error is caused by the way you multiply your bracket's together. You can't do:

[PHP](2+3)(4+5)[/PHP]

In Python; you have to do:

[PHP](2+3)*(4+5)[/PHP]

But your formula is wrong anyway, I'm afraid. And at each iteration, you are supposed to add the result, not set pi equal to that. If you didn't do that, you could just just set k to 100 and be done with iteration! ;)

Here's your program with the a few changes:

[PHP]#!/usr/bin/env python
#
#       pi.py

def main():
    K = 0
    print calculate()
    return 0

def calculate():
    k = 0.0
    pi = 0.0
    times = 10
    while k <= times:
        pi += (1/16**k)*(4/(8*k+1)-2/(8*k+4)-1/(8*k+5)-1/(8*k+6))
        k += 1
        print pi
    
    return pi

if __name__ == '__main__': main()
[/PHP]

Notice how I've set k to 0.0. This is because when we do operations on k, we want the result to be decimal not rounded down. I recommend having a play around to see what happens when you change various bits... :)

---

### Post by jimi_hendrix on 2008-08-15
ya when i believe it was yours i was copying and i misread it as just an = sign between pi and the opperation instead of =+

---

### Post by jimi_hendrix on 2008-08-15
thanks it works...now these numbers that print just get infinitly closer to pi?

---

### Post by jimi_hendrix on 2008-08-15
ok 1 more error...."neumeric result out of range"

---

### Post by hod139 on 2008-08-15
> **Lster said:**
> The Monte Carlo method seems quite slow really. I didn't throw darts - instead I just tried each point.

[php]

#This method basically tries every point in a one quadrant of a circle.
#As pi*r^2 = area, pi = area/r^2; but the area we calculated is only one
#quarter, so we must multiply by 4.

n = 100

count = 0
for x in xrange(n):
    for y in xrange(n):
        if x**2+y**2 < n**2:
            count += 1

count = float(4*count)
count /= n**2

print count

[/php]
This is not the way monte-carlo simulation works.  The point is to avoid sampling all the points inside the square, and rely on probability theory.  See this post: [http://ubuntuforums.org/showthread.php?p=2695585#post2695585](http://ubuntuforums.org/showthread.php?p=2695585#post2695585)

---

### Post by Lster on 2008-08-15
Theoretically. The only problem is that you are using Python's inbuilt floats which are only accurate to about 7 significant figures. If you were using a Decimal (which I used in my example), you could determine the precision you wanted... They're quite simple to use, so you might be able to work out how to use them from my code, but if not you could have a look at:

[http://docs.python.org/lib/module-decimal.html](http://docs.python.org/lib/module-decimal.html)

Algorithmically, each iteration gives you another hexadecimal digit, so if you want pi accurate to 100 decimal digits I think you can do this:

16^k = 10^a (with k the number of iterations and a the desired number of significant figures)
k*log10(16) = a
k = a/log10(16)

So it's easy to see that for every iteration you get about 1.2 significant figures. I'm not too confident about this so could anyone confirm it for me (it seems right).

---

### Post by Lster on 2008-08-15
[QUOTE=hod139]This is not the way monte-carlo simulation works.[/QUOTE]

Agreed, but it is very similar. Here's is the true Monte Carlo simulator:

[PHP]
from random import randint

n = 100

count = 0
for n in xrange(10000):
	x = randint(0, n+1)
	y = randint(0, n+1)
	if x**2+y**2 <= n**2:
		count += 1

count = float(4*count)/10000

print count

[/PHP]

---

### Post by Lster on 2008-08-15
[QUOTE=jimi_hendrix]neumeric result out of range[/QUOTE]

I'm guessing that is because you have put times up. When it comes to execute 16**k it will find that the result would be too big to store in a float. Again, using Decimals would fix this.

---

### Post by Pyro.699 on 2008-08-15
I do believe that this works

[php]
#!/usr/bin/python

from __future__ import division
import copy
import sys
from types import IntType,FloatType,LongType,ListType,TupleType,InstanceType,ClassType

# set error output to stdout instead
#__errout = sys.stderr
__errout = sys.stdout

#
# Define class contfrac
# Continued Fraction object version 1
#
class contfrac:

  def __init__(self,numerator,denominator=0,limit=256,epsilon=2e-9):
    self.classname="contfracv1"
    # if called by A=contfrac(3.1416)
    if denominator==0:
      if type(numerator)==IntType or type(numerator)==LongType:
        self.num=numerator
        self.den=1
        self.cf=[numerator]
      elif type(numerator)==FloatType:
        self.cf = decimal2contfrac(numerator,limit,epsilon)
        (self.num,self.den) = contfrac2rational(self.cf)
      elif type(numerator)==ListType:
        self.cf=copy.copy(numerator)
        self.num,self.den=contfrac2rational(numerator)
      elif is_contfrac(numerator):
        self.num=numerator.num
        self.den=numerator.den
        self.cf=copy.copy(numerator.cf)
      else:
        # if all else fails its the devil's number
        self.num=666
        self.den=1
        self.cf=[666] 
    # if called by A=(2,3)
    else:
      self.cf = rational2contfrac(long(numerator),long(denominator))
      (self.num,self.den) = contfrac2rational(self.cf)

  def __len__(self):
    return len(self.cf)



def lid(cfobj):
  return lazy_identity(cfobj)

#
# Define class lazy_identity
# Lazy connector for contfrac objects
#
class lazy_identity:

  def __init__(self,cf):
    self.classname="lazy_identity"
    self.cfobj=cf
    self.n=0
    self.a=0
    self.b=1
    self.c=1
    self.d=0

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a digit
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    while 1 :
      if self.c == 0 and self.d == 0 :
        break
      if self.c <> 0 and self.d <> 0 and (self.a//self.c) == (self.b//self.d) :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must ingest one term from cfobj
      if debugflag : print >> __errout,"n=%d len(cfobj)=%d" % (self.n,len(self.cfobj))
      if self.n < len(self.cfobj) :
        p=self.cfobj.cf[self.n]
        if debugflag : print >> __errout,"term ingested is ",p
        self.n=self.n+1
        # Now calculate the new a,b,c,d
        self.a,self.b,self.c,self.d=self.b,self.a+self.b*p,self.d,self.c+self.d*p
      else :
        if debugflag : print >> __errout,"term ingested is INF"
        self.n=self.n+1
        self.a,self.b,self.c,self.d=self.b,self.b,self.d,self.d
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    # out of the while loop
    if self.c== 0 and self.d == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      q=self.a//self.c
      if debugflag : print >> __errout,"egest the number ",q
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.c,self.d,self.a-self.c*q,self.b-self.d*q
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      return q
      

#
# Define class lazy_rcf_4onpi
# Lazy connector for 4/pi in regular continued fractions format
# [(1,1),(3,4),(5,9),(7,16),(9,25),(11,36),...]
#        (2n+1,(n+1)^2)
#
class lazy_rcf_4onpi:

  def __init__(self):
    self.classname="lazy_rcf_4onpi"
    self.n=0

  def egest(self,debugflag=False):
    a=  self.n * 2 + 1
    b= (self.n + 1) * (self.n + 1)
    self.n = self.n + 1
    return (a,b)


#
# Define class lazy_rcf2cf
# Lazy connector for turning regular continued fractions
# into standardize continued fractions
#
class lazy_rcf2cf:

  def __init__(self,rcf):
    self.classname="lazy_rcf2cf"
    self.cfobj=rcf
    self.a=0
    self.b=1
    self.c=1
    self.d=0

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a digit
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    while 1 :
      if self.c == 0 and self.d == 0 :
        break
      if self.c <> 0 and self.d <> 0 and (self.a//self.c) == (self.b//self.d) :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must ingest one term from cfobj
      (p,q)=self.cfobj.egest()
      if debugflag : print >> __errout,"term ingested is ",p
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.b*q,self.a+self.b*p,self.d*q,self.c+self.d*p
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    # out of the while loop
    if self.c== 0 and self.d == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      q=self.a//self.c
      if debugflag : print >> __errout,"egest the number ",q
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.c,self.d,self.a-self.c*q,self.b-self.d*q
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      return q
      

#
# Define class lazy_decimal
# Lazy connector for contfrac objects
#
class lazy_decimal:

  def __init__(self,lazycf):
    self.classname="lazy_decimal"
    self.cfobj=lazycf
    self.a=0
    self.b=1
    self.c=1
    self.d=0

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a digit
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    while 1 :
      if self.c == 0 and self.d == 0 :
        break
      if self.c <> 0 and self.d <> 0 and (self.a//self.c) == (self.b//self.d) :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must ingest one term from cfobj
      p=self.cfobj.egest()
      if p == 'INF' :
        if debugflag : print >> __errout,"term ingested is INF"
        self.a,self.b,self.c,self.d=self.b,self.b,self.d,self.d
      else :
        if debugflag : print >> __errout,"term ingested is ",p
        # Now calculate the new a,b,c,d
        self.a,self.b,self.c,self.d=self.b,self.a+self.b*p,self.d,self.c+self.d*p
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    # out of the while loop
    if self.c== 0 and self.d == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      r=self.a//self.c
      if debugflag : print >> __errout,"egest the number ",r
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.c,self.d,self.a-self.c*r,self.b-self.d*r
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      # Now calculate the egestion of r2=0 and s2=10
      # new_a = c * s2
      # new_b = d * s2
      # new_c = a - c * r2
      # new_d = b - d * r2
      self.a,self.b,self.c,self.d=self.c*10,self.d*10,self.a,self.b 
      if debugflag : print >> __errout,"after renormalisation a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      return r
      

#
# Define class lazy_base
# Lazy base for lazy operators
#
class lazy_base:

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a term
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%di,e=%d,f=%d,g=%d,h=%d" % (self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h) 
    while 1 :
      self.count= self.count + 1
      if self.e == 0 and self.f == 0 and self.g == 0 and self.h == 0 :
        # We need to return INF
        break
      if self.e <> 0 :
        Zoo= self.a // self.e
      else:
        Zoo='INF'
      if self.g <> 0 :
        Zoi= self.c // self.g
      else:
        Zoi='INF'
      if self.f <> 0 :
        Zio= self.b // self.f
      else:
        Zio='INF'
      if self.h <> 0 :
        Zii= self.d // self.h
      else:
        Zii='INF'
      if debugflag : print >> __errout,"Zoo=",Zoo," Zoi=",Zoi," Zio=",Zio," Zii=",Zii
      if Zoo <> 'INF' and Zoo == Zoi and Zoi == Zio and Zio == Zii :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must decide which lazy input to ingest from
      if Zio == 'INF' or Zoo == 'INF' :
        alpha='INF'
      else:
        alpha=abs(Zio - Zoo)
      if Zoi == 'INF' or Zoo == 'INF' :
        beta='INF'
      else:
        beta=abs(Zoi - Zoo)
      if debugflag : print >> __errout,"alpha=",alpha," beta=",beta
      if alpha=='INF' and beta=='INF' :
        if self.count % 2 == 0 :
          target='X'
        else:
          target='Y'
      elif alpha=='INF' and beta<>'INF' :
        target='X'
      elif beta=='INF' and alpha<>'INF' :
        target='Y'
      elif alpha > beta :
        target='X'
      else :
        target='Y'
      # Now we must ingest one term from cfobj
      if target=='X' :
        p=self.X.egest()
        if p == 'INF' :
          if debugflag : print >> __errout,"term X ingested is INF"
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.b,self.b,self.d,self.d,self.f,self.f,self.h,self.h
        else :
          if debugflag : print >> __errout,"term X ingested is ",p
          # Now calc the new a b c d e f g h 
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.b,self.a + self.b*p,self.d,self.c + self.d * p,self.f,self.e + self.f * p,self.h,self.g + self.h*p
      else :
        p=self.Y.egest()
        if p == 'INF' :
          if debugflag : print >> __errout,"term Y ingested is INF"
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.c,self.d,self.c,self.d,self.g,self.h,self.g,self.h
        else :
          if debugflag : print >> __errout,"term Y ingested is ",p
          # Now calc the new a b c d e f g h 
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.c,self.d,self.a+self.c*p,self.b+self.d*p,self.g,self.h,self.e+self.g*p,self.f+self.h*p
      # After ingestion
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d,e=%d,f=%d,g=%d,h=%d" % (self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h) 
    # out of the while loop
    if self.e == 0 and self.f == 0 and self.g == 0 and self.h == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      if debugflag : print >> __errout,"egest the number ",Zoo
      # Now calculate the new a,b,c,d,e,f,g,h
      self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.e,self.f,self.g,self.h,self.a-self.e*Zoo,self.b-self.f*Zoo,self.c-self.g*Zoo,self.d-self.h*Zoo
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d,e=%d,f=%d,g=%d,h=%d" % (self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h) 
      return Zoo
    

#
# Define class lazy_add
# Lazy addition for lazy objects
#
class lazy_add(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_add"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=1
    self.c=1
    self.d=0
    self.e=1
    self.f=0
    self.g=0
    self.h=0


#
# Define class lazy_sub
# Lazy subtraction for lazy objects
#
class lazy_sub(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_sub"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=1
    self.c=-1
    self.d=0
    self.e=1
    self.f=0
    self.g=0
    self.h=0


#
# Define class lazy_mul
# Lazy multiplication for lazy objects
#
class lazy_mul(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_mul"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=0
    self.c=0
    self.d=1
    self.e=1
    self.f=0
    self.g=0
    self.h=0


#
# Define class lazy_div
# Lazy division for lazy objects
#
class lazy_div(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_div"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=1
    self.c=0
    self.d=0
    self.e=0
    self.f=0
    self.g=1
    self.h=0



if __name__ == '__main__':
  rpi=lazy_rcf_4onpi()
  V=lazy_rcf2cf(rpi)
  A=lazy_decimal(lazy_div(lid(contfrac(4)),V))
  x=1
  while 1:
    digit=A.egest()
    sys.stdout.write(str(digit))
    if(x==1):
        sys.stdout.write(".")
        x=2
    sys.stdout.flush()
[/php]

---

### Post by jimi_hendrix on 2008-08-15
> **Lster said:**
> I'm guessing that is because you have put times up. When it comes to execute 16**k it will find that the result would be too big to store in a float. Again, using Decimals would fix this.

[PHP]#!/usr/bin/env python
#
#       pi.py

from decimal import Decimal

def main():
	getcontext().prec = 100
	one = Decimal(1)
	sixteen = Decimal(16)
	K = 0
	calculate();
	#print calculate()
	return 0

def calculate():
	k = 0.0
	pi = 0.0
	times = 10000
	while k <= times:
		pi =+ sixteen**(-k)*((4/(8*k + 1))*(2/(8*k+4))*(1/(8*k+5))*(1/(8*k+6)))
		k += 1
		print pi
	return pi
if __name__ == '__main__': main()
[/PHP]

i get some error on how getcontext is not defined

---

### Post by Lster on 2008-08-15
You need to import it! ;) Change:

[PHP]from decimal import Decimal[/PHP]

[PHP]from decimal import Decimal, getcontext[/PHP]

And that *should* do it.

---

### Post by jimi_hendrix on 2008-08-15
works...i think (the output is numbers that i dont know if they are right)

---

### Post by Pyro.699 on 2008-08-15
The script i provided does work, i compared it to several sites that give billions of digits of pi, and in 5 minutes i got 124000 numbers

---

### Post by jimi_hendrix on 2008-08-15
so each iteration gets closer to the real pi?...and the last iterateration should be the largest right

---

### Post by Lster on 2008-08-15
Yes.

---

### Post by jimi_hendrix on 2008-08-15
then something is definitly wrong with my math [PHP]def calculate():
	k = Decimal(0)
	pi = Decimal(0)
	times = 1000
	one = Decimal(1)
	iteration = 1
	sixteen = Decimal(16)
	while k <= times:
		pi =+ sixteen**(-k)*((4/(8*k + 1))*(2/(8*k+4))*(1/(8*k+5))*(1/(8*k+6)))
		k += 1
		print pi
		print " "
		print iteration
		iteration += 1
	return pi
[/PHP]

it goes to the 1000 iteration and the 1000 one is > the 999 which is less then 998...:(

---

### Post by Lster on 2008-08-15
This:

[PHP]pi =+ sixteen**(-k)*((4/(8*k + 1))*(2/(8*k+4))*(1/(8*k+5))*(1/(8*k+6)))[/PHP]

Should be:

[PHP]pi += sixteen**(-k)*((4/(8*k + 1))-(2/(8*k+4))-(1/(8*k+5))-(1/(8*k+6)))[/PHP]

Note how the "=+" should be "+=" and you have multiplied many of the brackets together while you must, in fact, subtract them.

---

### Post by tamoneya on 2008-08-15
> **jimi_hendrix said:**
> then something is definitly wrong with my math [PHP]def calculate():
	k = Decimal(0)
	pi = Decimal(0)
	times = 1000
	one = Decimal(1)
	iteration = 1
	sixteen = Decimal(16)
	while k <= times:
		pi =+ sixteen**(-k)*((4/(8*k + 1))*(2/(8*k+4))*(1/(8*k+5))*(1/(8*k+6)))
		k += 1
		print pi
		print " "
		print iteration
		iteration += 1
	return pi
[/PHP]

it goes to the 1000 iteration and the 1000 one is > the 999 which is less then 998...:(

It is fine for the calculated value of pi to oscillate while it converges.  This is actually fairly typical.  look at this sequence (I am not doing any calculations here I am just making a sequence that approaches pi.  The numbers themselves have no significance).

4,3,3.5,3.1,3.2,3.12,3.16

Notice that it is approaching from both above pi and below.
Here is above: 4,3.5,3.2,3.16 (it gets closer to pi)
and now below: 3,3.1,3.12 (it also gets closer to pi)

So it is totally fine for this to occur.  That being said though you should make the changes suggested by Lster

---

### Post by jimi_hendrix on 2008-08-15
*hits head*

too early in the morning for algabra

thanks all

---

### Post by slavik on 2008-08-15
another method is to place the circle's center at the origin and integrace the circle function for the upper right part, then multiply that by 4 and you get the area area. :) (with radius of 1, the area is pi)

---

### Post by Lster on 2008-08-15
I basically did that above but it converges very slowly compared to other methods.

---

### Post by slavik on 2008-08-15
but it is very easy to distribute the workload :)

---

### Post by Lster on 2008-08-15
Coefficient speed increases won't help. A few iterations of a second-order convergent algorithm will provide far more precision.

---

### Post by wenuswilson on 2008-08-16
> **jimi_hendrix said:**
> so each iteration gets closer to the real pi?...and the last iterateration should be the largest right

Momma always told me to never forget about rounding errors.

---

### Post by NovaAesa on 2008-08-16
This is true about rounding. If you are using a 32 bit float, you wont get much higher precison than about 6 decimal places. If you use a 64 bit float, it will be about 15 decimal places.

---

### Post by jimi_hendrix on 2008-08-16
in my new code i used decimals

---

### Post by tamoneya on 2008-08-16
> **jimi_hendrix said:**
> in my new code i used decimals

that by default will give you 28 digits of precision.  While that is nice you could very quickly surpass that.  Set the precision like this:[PHP]getcontext().prec = 100
[/PHP]
That sets it to 100 digits.

---

### Post by British0zzy on 2008-08-16
[here]("http://www.lacim.uqam.ca/~plouffe/Simon/articlepi.html") is a great link about some pi algorithms. Doesn't go deep into how to implement them, but very informative.

---

### Post by kool_kat_os on 2008-08-16
> **Pyro.699 said:**
> I do believe that this works

[php]
#!/usr/bin/python

from __future__ import division
import copy
import sys
from types import IntType,FloatType,LongType,ListType,TupleType,InstanceType,ClassType

# set error output to stdout instead
#__errout = sys.stderr
__errout = sys.stdout

#
# Define class contfrac
# Continued Fraction object version 1
#
class contfrac:

  def __init__(self,numerator,denominator=0,limit=256,epsilon=2e-9):
    self.classname="contfracv1"
    # if called by A=contfrac(3.1416)
    if denominator==0:
      if type(numerator)==IntType or type(numerator)==LongType:
        self.num=numerator
        self.den=1
        self.cf=[numerator]
      elif type(numerator)==FloatType:
        self.cf = decimal2contfrac(numerator,limit,epsilon)
        (self.num,self.den) = contfrac2rational(self.cf)
      elif type(numerator)==ListType:
        self.cf=copy.copy(numerator)
        self.num,self.den=contfrac2rational(numerator)
      elif is_contfrac(numerator):
        self.num=numerator.num
        self.den=numerator.den
        self.cf=copy.copy(numerator.cf)
      else:
        # if all else fails its the devil's number
        self.num=666
        self.den=1
        self.cf=[666] 
    # if called by A=(2,3)
    else:
      self.cf = rational2contfrac(long(numerator),long(denominator))
      (self.num,self.den) = contfrac2rational(self.cf)

  def __len__(self):
    return len(self.cf)



def lid(cfobj):
  return lazy_identity(cfobj)

#
# Define class lazy_identity
# Lazy connector for contfrac objects
#
class lazy_identity:

  def __init__(self,cf):
    self.classname="lazy_identity"
    self.cfobj=cf
    self.n=0
    self.a=0
    self.b=1
    self.c=1
    self.d=0

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a digit
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    while 1 :
      if self.c == 0 and self.d == 0 :
        break
      if self.c <> 0 and self.d <> 0 and (self.a//self.c) == (self.b//self.d) :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must ingest one term from cfobj
      if debugflag : print >> __errout,"n=%d len(cfobj)=%d" % (self.n,len(self.cfobj))
      if self.n < len(self.cfobj) :
        p=self.cfobj.cf[self.n]
        if debugflag : print >> __errout,"term ingested is ",p
        self.n=self.n+1
        # Now calculate the new a,b,c,d
        self.a,self.b,self.c,self.d=self.b,self.a+self.b*p,self.d,self.c+self.d*p
      else :
        if debugflag : print >> __errout,"term ingested is INF"
        self.n=self.n+1
        self.a,self.b,self.c,self.d=self.b,self.b,self.d,self.d
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    # out of the while loop
    if self.c== 0 and self.d == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      q=self.a//self.c
      if debugflag : print >> __errout,"egest the number ",q
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.c,self.d,self.a-self.c*q,self.b-self.d*q
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      return q
      

#
# Define class lazy_rcf_4onpi
# Lazy connector for 4/pi in regular continued fractions format
# [(1,1),(3,4),(5,9),(7,16),(9,25),(11,36),...]
#        (2n+1,(n+1)^2)
#
class lazy_rcf_4onpi:

  def __init__(self):
    self.classname="lazy_rcf_4onpi"
    self.n=0

  def egest(self,debugflag=False):
    a=  self.n * 2 + 1
    b= (self.n + 1) * (self.n + 1)
    self.n = self.n + 1
    return (a,b)


#
# Define class lazy_rcf2cf
# Lazy connector for turning regular continued fractions
# into standardize continued fractions
#
class lazy_rcf2cf:

  def __init__(self,rcf):
    self.classname="lazy_rcf2cf"
    self.cfobj=rcf
    self.a=0
    self.b=1
    self.c=1
    self.d=0

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a digit
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    while 1 :
      if self.c == 0 and self.d == 0 :
        break
      if self.c <> 0 and self.d <> 0 and (self.a//self.c) == (self.b//self.d) :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must ingest one term from cfobj
      (p,q)=self.cfobj.egest()
      if debugflag : print >> __errout,"term ingested is ",p
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.b*q,self.a+self.b*p,self.d*q,self.c+self.d*p
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    # out of the while loop
    if self.c== 0 and self.d == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      q=self.a//self.c
      if debugflag : print >> __errout,"egest the number ",q
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.c,self.d,self.a-self.c*q,self.b-self.d*q
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      return q
      

#
# Define class lazy_decimal
# Lazy connector for contfrac objects
#
class lazy_decimal:

  def __init__(self,lazycf):
    self.classname="lazy_decimal"
    self.cfobj=lazycf
    self.a=0
    self.b=1
    self.c=1
    self.d=0

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a digit
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    while 1 :
      if self.c == 0 and self.d == 0 :
        break
      if self.c <> 0 and self.d <> 0 and (self.a//self.c) == (self.b//self.d) :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must ingest one term from cfobj
      p=self.cfobj.egest()
      if p == 'INF' :
        if debugflag : print >> __errout,"term ingested is INF"
        self.a,self.b,self.c,self.d=self.b,self.b,self.d,self.d
      else :
        if debugflag : print >> __errout,"term ingested is ",p
        # Now calculate the new a,b,c,d
        self.a,self.b,self.c,self.d=self.b,self.a+self.b*p,self.d,self.c+self.d*p
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
    # out of the while loop
    if self.c== 0 and self.d == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      r=self.a//self.c
      if debugflag : print >> __errout,"egest the number ",r
      # Now calculate the new a,b,c,d
      self.a,self.b,self.c,self.d=self.c,self.d,self.a-self.c*r,self.b-self.d*r
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      # Now calculate the egestion of r2=0 and s2=10
      # new_a = c * s2
      # new_b = d * s2
      # new_c = a - c * r2
      # new_d = b - d * r2
      self.a,self.b,self.c,self.d=self.c*10,self.d*10,self.a,self.b 
      if debugflag : print >> __errout,"after renormalisation a=%d,b=%d,c=%d,d=%d" % (self.a,self.b,self.c,self.d) 
      return r
      

#
# Define class lazy_base
# Lazy base for lazy operators
#
class lazy_base:

  def egest(self,debugflag=False):
    # First check if we can egest
    # if we can then egest a term
    # otherwise loop until we can
    if debugflag : print >> __errout,"a=%d,b=%d,c=%d,d=%di,e=%d,f=%d,g=%d,h=%d" % (self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h) 
    while 1 :
      self.count= self.count + 1
      if self.e == 0 and self.f == 0 and self.g == 0 and self.h == 0 :
        # We need to return INF
        break
      if self.e <> 0 :
        Zoo= self.a // self.e
      else:
        Zoo='INF'
      if self.g <> 0 :
        Zoi= self.c // self.g
      else:
        Zoi='INF'
      if self.f <> 0 :
        Zio= self.b // self.f
      else:
        Zio='INF'
      if self.h <> 0 :
        Zii= self.d // self.h
      else:
        Zii='INF'
      if debugflag : print >> __errout,"Zoo=",Zoo," Zoi=",Zoi," Zio=",Zio," Zii=",Zii
      if Zoo <> 'INF' and Zoo == Zoi and Zoi == Zio and Zio == Zii :
        if debugflag : print >> __errout,"We can egest"
        break
      # Now we must decide which lazy input to ingest from
      if Zio == 'INF' or Zoo == 'INF' :
        alpha='INF'
      else:
        alpha=abs(Zio - Zoo)
      if Zoi == 'INF' or Zoo == 'INF' :
        beta='INF'
      else:
        beta=abs(Zoi - Zoo)
      if debugflag : print >> __errout,"alpha=",alpha," beta=",beta
      if alpha=='INF' and beta=='INF' :
        if self.count % 2 == 0 :
          target='X'
        else:
          target='Y'
      elif alpha=='INF' and beta<>'INF' :
        target='X'
      elif beta=='INF' and alpha<>'INF' :
        target='Y'
      elif alpha > beta :
        target='X'
      else :
        target='Y'
      # Now we must ingest one term from cfobj
      if target=='X' :
        p=self.X.egest()
        if p == 'INF' :
          if debugflag : print >> __errout,"term X ingested is INF"
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.b,self.b,self.d,self.d,self.f,self.f,self.h,self.h
        else :
          if debugflag : print >> __errout,"term X ingested is ",p
          # Now calc the new a b c d e f g h 
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.b,self.a + self.b*p,self.d,self.c + self.d * p,self.f,self.e + self.f * p,self.h,self.g + self.h*p
      else :
        p=self.Y.egest()
        if p == 'INF' :
          if debugflag : print >> __errout,"term Y ingested is INF"
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.c,self.d,self.c,self.d,self.g,self.h,self.g,self.h
        else :
          if debugflag : print >> __errout,"term Y ingested is ",p
          # Now calc the new a b c d e f g h 
          self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.c,self.d,self.a+self.c*p,self.b+self.d*p,self.g,self.h,self.e+self.g*p,self.f+self.h*p
      # After ingestion
      if debugflag : print >> __errout,"after ingestion a=%d,b=%d,c=%d,d=%d,e=%d,f=%d,g=%d,h=%d" % (self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h) 
    # out of the while loop
    if self.e == 0 and self.f == 0 and self.g == 0 and self.h == 0 :
      if debugflag : print >> __errout,"egest the number INF"
      return 'INF'
    else:
      if debugflag : print >> __errout,"egest the number ",Zoo
      # Now calculate the new a,b,c,d,e,f,g,h
      self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h=self.e,self.f,self.g,self.h,self.a-self.e*Zoo,self.b-self.f*Zoo,self.c-self.g*Zoo,self.d-self.h*Zoo
      if debugflag : print >> __errout,"after egestion a=%d,b=%d,c=%d,d=%d,e=%d,f=%d,g=%d,h=%d" % (self.a,self.b,self.c,self.d,self.e,self.f,self.g,self.h) 
      return Zoo
    

#
# Define class lazy_add
# Lazy addition for lazy objects
#
class lazy_add(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_add"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=1
    self.c=1
    self.d=0
    self.e=1
    self.f=0
    self.g=0
    self.h=0


#
# Define class lazy_sub
# Lazy subtraction for lazy objects
#
class lazy_sub(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_sub"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=1
    self.c=-1
    self.d=0
    self.e=1
    self.f=0
    self.g=0
    self.h=0


#
# Define class lazy_mul
# Lazy multiplication for lazy objects
#
class lazy_mul(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_mul"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=0
    self.c=0
    self.d=1
    self.e=1
    self.f=0
    self.g=0
    self.h=0


#
# Define class lazy_div
# Lazy division for lazy objects
#
class lazy_div(lazy_base):

  def __init__(self,XX,YY):
    self.classname="lazy_div"
    self.count=0
    self.X=XX
    self.Y=YY
    self.a=0
    self.b=1
    self.c=0
    self.d=0
    self.e=0
    self.f=0
    self.g=1
    self.h=0



if __name__ == '__main__':
  rpi=lazy_rcf_4onpi()
  V=lazy_rcf2cf(rpi)
  A=lazy_decimal(lazy_div(lid(contfrac(4)),V))
  x=1
  while 1:
    digit=A.egest()
    sys.stdout.write(str(digit))
    if(x==1):
        sys.stdout.write(".")
        x=2
    sys.stdout.flush()
[/php]

it does work...i compared the first 20 number's and they were the same...but then i got dizzy looking at all of those numbers...and then started typing this post:)

---

### Post by wenuswilson on 2008-08-17
> **British0zzy said:**
> [here]("http://www.lacim.uqam.ca/~plouffe/Simon/articlepi.html") is a great link about some pi algorithms. Doesn't go deep into how to implement them, but very informative.

[This one is pretty spiffy too.]("http://mathworld.wolfram.com/PiFormulas.html") I still like the Method of Exhaustion the best. (For the sake of simplicity and Archimedes was one smart guy.)

---

### Post by Lster on 2008-08-17
I'll add this as yet another way of approximating pi:

[PHP]
#This example uses the fact that:
#pi = sqrt(6*(1/1+1/4+1/9+1/16+...))
#It seems quite slow to converge and is probably not the best choice.

from decimal import Decimal

one = Decimal(1)
two = Decimal(2)
half = one/two

i = one
pi = 0
while i < 500:
	pi += one/i/i
	i += one

pi = (6*pi)**half
print pi
[/PHP]

---

### Post by jimi_hendrix on 2008-08-17
> **kool_kat_os said:**
> it does work...i compared the first 20 number's and they were the same...but then i got dizzy looking at all of those numbers...and then started typing this post:)

well that doesnt mean it doesnt work...it just means that after his precision ended the number just got rounded

---

### Post by wenuswilson on 2008-08-18
Alright, I made this in c++. It doesn't really work and I'm not a good programmer by any stretch but, other than that, I can't figure out why I'm not getting things to work. I'm using g++.

1st -- cout doesn't equal Pi.

2nd -- The decimals end after going out 50 places.

[IMG]http://mathworld.wolfram.com/images/equations/PiFormulas/NumberedEquation11.gif[/IMG]

> #include <iostream>
#include <stdlib.h>
#include <math.h>
#include <iomanip>

using namespace std;

int main()
{
	int i, n;
	double Pi = 0;
	float x;
	cout << "this guys should find pi... key word, should" << endl;
	cout << "enter the number of iterations in the summation" << endl;
	cin >> i;
	for (n = 0; n <= i; n++)
		{
		x = pow(-1,n) * ( - pow(2,5)/(4*n+1) - 1/(4*n+3) + pow(2,8 )/(10*n+1) - pow(2,6)/(10*n+3) - pow(2,2)/(10*n+5) - pow(2,2)/(10*n+7) + 1/(10*n+9))/ pow(2,(10*n)); 	
		Pi = Pi + x;
		}
		cout << fixed << showpoint << setprecision(100) << Pi / (pow(2,6)) << endl;
return 0;
}


---

### Post by DavidBell on 2008-08-18
@ wenuwilson, Your main problem is you are using floats and doubles, which only have 6 and 15 places precision respectively (pow is also only double too), in order to calculate 50+ places. Just can't be done.

You need to find a high/arbitary precision library to use in their place, it will have approporiate types and functions to go with them.

Sorry can't suggest any as I've never needed more than double.

DB

---

### Post by Lster on 2008-08-18
A very good library for stuff like arbitary integbers, fractions and decimals is GMP:

[http://gmplib.org/](http://gmplib.org/)

---

### Post by Pyro.699 on 2008-08-18
> **jimi_hendrix said:**
> well that doesnt mean it doesnt work...it just means that after his precision ended the number just got rounded
It is accurate up to atleast 1000 decimal places of pi, i compaired it with several sites:

[http://www.math.utah.edu/~pa/math/pi.html](http://www.math.utah.edu/~pa/math/pi.html)
[http://3.141592653589793238462643383279502884197169399375105820974944592.com/](http://3.141592653589793238462643383279502884197169399375105820974944592.com/)

i got up to 600,000 before i stopped the script and every value has matched up with another number.

---

### Post by Lster on 2008-08-18
Isn't it easier to prove it works? ;) That's a nice program by the way, I'll have to have a go at something like that soon. Does computing each digit take the same amount of time or does the program get slower and slower as it has to find later and later digits?

---

### Post by Pyro.699 on 2008-08-18
It does get slower and slower as time progresses, im working on something like this program which i must admit i am quite jealous of....

[http://home.istar.ca/~lyster/pi.html](http://home.istar.ca/~lyster/pi.html)

it calculated 1mb of pi in under 1 second... and it took me 2 days to get 600kb... so im still improving (also, im using python, something tells me he didnt)

---

### Post by cszikszoy on 2008-08-18
> **Pyro.699 said:**
> It does get slower and slower as time progresses, im working on something like this program which i must admit i am quite jealous of....

[http://home.istar.ca/~lyster/pi.html]("http://home.istar.ca/%7Elyster/pi.html")

it calculated 1mb of pi in under 1 second... and it took me 2 days to get 600kb... so im still improving (also, im using python, something tells me he didnt)


Python is too slow for hardcore number crunching like that.  Use C++.

See this for example: [http://tenser.typepad.com/tenser_said_the_tensor/2006/08/python_vs_perl_.html](http://tenser.typepad.com/tenser_said_the_tensor/2006/08/python_vs_perl_.html)

He shows that in Python, doing a simple add is 141 times slower than C++.  Understandably, Python gets MUCH slower than C++ when you are doing things like adding many fractions together, then multiplying the sum.

---

### Post by Pyro.699 on 2008-08-18
I asumed so, im working on getting my gear together to learn C++ but with my first year of university coming up soon and they will be throwing java stuff at us im going to wait a bit to learn it. I wish i knew enough of C++ to modify what i have into much better code.

---

### Post by cszikszoy on 2008-08-18
> **Pyro.699 said:**
> I asumed so, im working on getting my gear together to learn C++ but with my first year of university coming up soon and they will be throwing java stuff at us im going to wait a bit to learn it. I wish i knew enough of C++ to modify what i have into much better code.

Email me what you have and I'll help you out.  I used to tutor and teach C++ at my university, when I was going to school.

---

### Post by wenuswilson on 2008-08-18
> **DavidBell said:**
> @ wenuwilson, Your main problem is you are using floats and doubles, which only have 6 and 15 places precision respectively (pow is also only double too), in order to calculate 50+ places. Just can't be done.

You need to find a high/arbitary precision library to use in their place, it will have approporiate types and functions to go with them.

Sorry can't suggest any as I've never needed more than double.

DB

> **Lster said:**
> A very good library for stuff like arbitary integbers, fractions and decimals is GMP:

[http://gmplib.org/](http://gmplib.org/)

Everything all said and done, I should be getting at least 6 decimals for Pi perfect... Right?

My code : 3.14506
Real    : 3.14159

I think I'm going to scrap it and move on to something else, thanks for the advice otherwise.

---

### Post by DavidBell on 2008-08-18
> **wenuswilson said:**
> Everything all said and done, I should be getting at least 6 decimals for Pi perfect... Right?


That would depend on your value for n, just looking at the formula I would guess you need something like n = 10000 for 5 places, you ont get much better than five places with floats due to cumulative errors.

DB

---

### Post by wenuswilson on 2008-08-18
> **DavidBell said:**
> That would depend on your value for n, just looking at the formula I would guess you need something like n = 10000 for 5 places, you ont get much better than five places with floats due to cumulative errors.

DB

10000000 for n --> 3.14506 ...So...

[Edi] I changed my code from the double to float, same result.

---

### Post by DavidBell on 2008-08-19
You also have a problem with the last term in your formula
```
pow(2,(10*n))
```

The range for doubles is about +/-10E350 = approx 2E1000, so any value of n greater than about 100 for that term is going to give a false value (equal to  max limit of double). If you use exceptions it should throw an error.

DB

---

### Post by patmos7 on 2010-07-14
> **Qtips said:**
> Hi,

One solution to approximate the value of pi come from the book : Python programming - An introduction to computer science from John Zelle. 

You need to sum the terms in the following series:
4/1 - 4/3 + 4/5 - 4/7 + 4/9 - 4/11 + ...

My program to do it is the following:



Hope this helps.


Hi thanks for the elegant code! I am working on the same problem on the tutorial as a newbie!

---

