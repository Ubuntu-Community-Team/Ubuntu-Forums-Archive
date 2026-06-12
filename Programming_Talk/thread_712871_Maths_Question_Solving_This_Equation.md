---
title: "Maths Question: Solving This Equation"
date: 2008-03-02
forum: Programming Talk
---

### Post by Lster on 2008-03-02
Hi!

I was wondering if there is anyway to solve this equation in O(1) time:

x^x / ((x-1)^(x-1)) = n

Where x and n are positive, real integers; and n is known.

Without going into to much detail, I need to do this for a program I am writing which solves a very specific problem. There are techniques I use to avoid finding this equation multiple times, but I would like to be able to calculate it, as said, in O(1) time. Is this possible - I've been playing with it for ages and have got nowhere?

Thanks,
Lster

---

### Post by a9bejo on 2008-03-02
I failed. I do not see how this could be done in O(1), since the equation is exponential by definition And I do not see how you can reduce something like x^x / ((x-1) ^ (x-1))  so that the x is removed from the exponent completely.  But then, I'm not a pure mathematician but a cs, so maybe I just don't know what I'm talking about.

I tried rearranging the numerator to (x ^ (x-1)) * x  , but I don't know if there is a way to split (x-1) ^ (x-1) in the denominator to something like (x)^(x-1) * ANYTHING, so we could get rid of the exponent.

I also tried to solve the quotation with [sage](http://www.sagemath.org/), and it also did not find a better solution as the one you provided:

[php]
sage: x,n = var("x,n")
sage: quotation = x^x / ((x-1)^(x-1)) == n 
sage: quotation.solve(x) 
[x^x == n*(x - 1)^(x - 1)]
[/php]

Maybe some kind of approximation algorithm like [Gauss-Seidl](http://en.wikipedia.org/wiki/Gauss-Seidel_method) or [Jakobi](http://en.wikipedia.org/wiki/Jacobi_method) can be useful here?

---

### Post by Lster on 2008-03-02
OK. I have no mathematical knowledge on how to deal with these problems... so I was a little stumped. I can still use another method of reducing the times it is computed.

Thank you,
Lster

---

### Post by steveneddy on 2008-03-02
Maybe the answer is......42?

:-?

---

### Post by SOULRiDER on 2008-03-02
> **steveneddy said:**
> Maybe the answer is......42?

:-?

LOL.

If I were to make a program to solve equations, I wouldnt know where to start... =/

---

### Post by Rhubarb on 2008-03-02
Apart from low values of n, it almost looks linear (it's **not** linear at all, but close to it).

---

### Post by xtacocorex on 2008-03-02
You'll have to use numerical methods for this, I suggest Newton-Raphson ([http://en.wikipedia.org/wiki/Newton's_method](http://en.wikipedia.org/wiki/Newton's_method))

Pretty much what happens is you know n and you provide a guess for x and the method keeps guessing x until it reaches n within a certain tolerance.

I have no idea what order the equation is in Big O notation because that didn't matter to me when I had to write the method for a class.

Or:
You can plot the function for given x and n in a spreadsheet and do a curve fit on the data to generate the constants for a spline ([http://mathworld.wolfram.com/CubicSpline.html](http://mathworld.wolfram.com/CubicSpline.html)) which the program could then use to estimate the values.  The spline matrix could be solved easily with the Thomas Algorithm, a method of quickly solving a tri-diagonal matrix that doesn't require matrix reduction so it's fast.

---

### Post by Lster on 2008-03-02
I will look into these methods - thanks guys. :)

I have a rather different problem in finding whether a number is will terminate when expressed as a decimal. Again my maths is not at that level and the Wikipedia page doesn't really explain how to do this.

I have the number (that I want to find whether it is a repeating decimal or not) in the format A / B where A and B are whole integers. I'm guessing the solution has something to do with prime decomposition.

Again thanks!
Lster

---

### Post by a9bejo on 2008-03-02
> **Lster said:**
> I'm guessing the solution has something to do with prime decomposition.


If I understood you correctly, I think you are on the right path: Find all primes for both A and B and then remove any prime that is found in both sets.  Whats left is the most reduced form of the number.

Here is an example for an algorithm that finds the primes for an integer range (the algorithm is limited to the maximum integer range):
[php]
import sys,math
def factorize(n):
    def isPrime(n):
        return not [x for x in xrange(2,int(math.sqrt(n)))
                    if n%x == 0]
    primes = []
    candidates = xrange(2,n+1)
    candidate = 2
    while not primes and candidate in candidates:
        if n%candidate == 0 and isPrime(candidate):
            primes = primes + [candidate] + factorize(n/candidate)
        candidate += 1            
    return primes
print factorize(int(sys.argv[1]))
[/php]

**Update**: Oh, ok, I guess this does not fully answer your question.

---

### Post by Lster on 2008-03-02
Thanks for your reply. I forgot to mention, I already have A and B as reduced as possible.

---

### Post by stroyan on 2008-03-02
If your reduced 'B' value has any prime factors other than 2 or 5 then A/B will be a repeating decimal.

---

### Post by Lster on 2008-03-02
Thank you! :)

---

### Post by slavik on 2008-03-02
When Lster said O(1), you misunderstood him. Read this: [http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)

---

### Post by a9bejo on 2008-03-02
> **slavik said:**
> When Lster said O(1), you misunderstood him. Read this: [http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)

Who do you think misunderstood him? I know I didn't.

---

### Post by Lux Perpetua on 2008-03-02
Out of curiosity, can you tell us where this problem (the equation in the OP) came up? I've definitely encountered this very equation before in my own musings, but I don't remember the context. If you can give a little more information, it's possible there's a workaround. (No promises, though.)

For the second problem, don't find the prime factors of your numerator and denominator. That's suicide. [list=1][*]While the denominator is divisible by 2: divide the denominator by 2.[*]While the denominator is divisible by 5: divide the denominator by 5. [*]If the numerator is now divisible by the (modified) denominator, then the fraction is a terminating decimal. Otherwise, it is a repeating decimal. [/list]It is very important that you do the divisibility tests using the modulus function and *not factor anything into primes*. (Actually, divisibility by 2 doesn't require the modulus operator if the numbers are represented in binary place-value: just look at the least significant bit).

---

### Post by Lster on 2008-03-02
I will definitely post the problem when I have finished. Solutions and all. For now, though, I really want to attempt this with as little help as possible. You are right about a workaround. ;)

Also, thanks for the other method. I was interested in other possibilities and this sounds good!

May I ask: have you done maths at university - you seem extremely proficient in so many aspects! I'm very interested about how you know so much and can apply it so well... I'm especially interested as maths is a subject I am very likely to pursue at university.

Thanks,
Lster

---

### Post by Lux Perpetua on 2008-03-02
> **Lster said:**
> May I ask: have you done maths at university - you seem extremely proficient in so many aspects! I'm very interested about how you know so much and can apply it so well... I'm especially interested as maths is a subject I am very likely to pursue at university.

Thanks,
LsterWonderful. I always like to hear about other people interested in mathematics. :-) To answer your question, I have an A. B. degree in math, and I'm currently pursuing a Ph. D.

---

### Post by Lster on 2008-03-02
[QUOTE=Lux Perpetua]Wonderful. I always like to hear about other people interested in mathematics. :) To answer your question, I have an A. B. degree in math, and I'm currently pursuing a Ph. D.[/QUOTE]

Cool! Good luck with that.

---

### Post by stratavarious on 2008-03-02
.

---

### Post by Lster on 2008-03-02
[QUOTE=stratavarious]I don't know if this helps any but,

x^x / (x-1)^(x-1) = e^( x*ln(x)-x*ln(x-1) + ln(x-1) )

expressing it this way at least you're only raising a constant to a power.
But I'm not sure if it is any faster than what you had originally.[/QUOTE]

Thanks for the reply. :)

---

### Post by stratavarious on 2008-03-02
.

---

### Post by WW on 2008-03-02
> **Lster said:**
> Hi!

I was wondering if there is anyway to solve this equation in O(1) time:

x^x / ((x-1)^(x-1)) = n

Where x and n are positive, real integers; and n is known.

What do you mean by "real integers"?  If you are using the common naming convention of x for a real variable and n for an integer, then perhaps you meant that x is a positive real number and n is a positive integer.  Is that correct?

---

### Post by [h2o] on 2008-03-03
Since Integers are a subclass of real numbers it is not really wrong. But it is redundant information ;)
I guess he meant real as in "not complex/imaginary". If you have never taken any higher calculus classes, then I think his explanation was perfectly valid because you understand exactly what he meant.

---

### Post by Lux Perpetua on 2008-03-03
> **'[h2o] said:**
> Since Integers are a subclass of real numbers it is not really wrong. But it is redundant information ;)
I guess he meant real as in "not complex/imaginary". If you have never taken any higher calculus classes, then I think his explanation was perfectly valid because you understand exactly what he meant.If x and n are really constrained to be positive integers, then it's trivial: if n = 4, then x = 2. Otherwise, there are no solutions, since if x > 2, then x-1 and x have distinct prime factors, so x^x/(x-1)^(x-1) can't be an integer.

---

### Post by Jacks0n on 2008-03-03
Hm, ok so I'm not very good with maths so if I screwed this up or it does something completely different, please don't flame me over it. It solves for x. I also realize it's a bit of a hack.

```

n = float(raw_input('What is the value of N? : '))
digits = raw_input('How accurate do you wish the calculation to be? : ')
base = float(int(n)-1)
increment = float('0.' + (int(digits)-1)*'0' + '1')

x = 0.0
while base < n:
	base += increment
	x = (base**base)/((base-1)**(base-1))

print 'The variable x is %s' % str(x)

```

Input's any integer > 0
Output is value X
Digits gets more accurate > 1, but 3-6 should be fine.

---

### Post by Lster on 2008-03-03
Lux Perpetua, I think you're right. My definitions should have been where just n is whole, positive and real. x is real and also >= 1. However, I'm nearly done anyway (I have a work around!) so it isn't too critical to solve it now. I'm still interested, though - I love hard maths!

---

### Post by Lster on 2008-03-05
Hi again. I am failing to complete this challenge and am wondering whether my function to evaluate whether a fraction (X over Y) can be represented as a terminating decimal is correct.

[PHP]...[/PHP]

I hope that code returns -1 if it is terminating and 1 if it doesn't terminate (as a decimal, of course). Can you verify that is coded correctly?

Thanks,
Lster

---

### Post by qix on 2008-03-05
It should be correct, but you should be able to replace
```
if ( fmod ( X , Y ) < 0.5 )
```
with
```
if ( Y == 1 )
```
according to
[http://mathforum.org/library/drmath/view/58073.html](http://mathforum.org/library/drmath/view/58073.html)
if your fraction is simplified. (line added with edit).


I'm wondering about a couple of things in your code though:
1. Why does the function return a double? Shouldn't it just return an int?
2. Why do you test if fmod is less than 0.5? Shouldn't you just test if it's equal 0?

---

### Post by Lster on 2008-03-05
> 1. Why does the function return a double? Shouldn't it just return an int?

I multiply it by a double later. I was trying to solve this:

[http://projecteuler.net/index.php?section=problems&id=183](http://projecteuler.net/index.php?section=problems&id=183)

---

### Post by Lster on 2008-03-05
Would using abitary precision numbers help. I think that could be an issue...?

---

### Post by Lster on 2008-03-05
* Bump *

---

