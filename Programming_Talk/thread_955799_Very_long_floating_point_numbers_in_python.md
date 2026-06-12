---
title: "Very long floating point numbers in python"
date: 2008-10-22
forum: Programming Talk
---

### Post by sans_b on 2008-10-22
I am trying to create a program that will demonstrate an infinite harmonic series, but I am not finding the precision I need in python.  How would I allow a float to occupy more bits than the default?

---

### Post by y-lee on 2008-10-22
You could use an arbitrary precision module such as pythons [Decimal]("http://www.python.org/doc/2.5.2/lib/module-decimal.html") class or a third party module such as [GPMPY]("http://gmpy.sourceforge.net/") or [mxNumber]("http://www.egenix.com/products/python/mxExperimental/mxNumber/").

If you are motivated you could of course write your own infinite precession class, I think all programmers should do that at least once. It is doubt full you would do a better job tho than the modules I have mentioned.

---

### Post by Paul Miller on 2008-10-22
> **sans_b said:**
> I am trying to create a program that will demonstrate an infinite harmonic series, but I am not finding the precision I need in python.  How would I allow a float to occupy more bits than the default?

I'm not sure exactly what you're looking to do here.  Could you state what you want to accomplish a little more clearly?  For example, do you want to compute the nth harmonic number for some large values of n?  Are you looking to approximate Euler's constant &#947; (gamma)?  Is it an explicit requirement to use Python?  If not, some other tool (such as a computer algebra system or a tool like GNU Octave) might meet your needs better.

---

### Post by sans_b on 2008-10-22
I am trying to calculate the limit of the sum from n=2 to infinity of (1/n).  So the value of (1/2)+(1/3)+(1/4)+(1/5)+(1/6)+.....  
The problem I am running into is that after a certain point it seems that the value of 1/n reaches a certain point that is the smallest number python can handle (about 2e-7) and after that point the value of the sum increments at a constant rate.  
It is not required that I use python but since I am trying to become more familiar with python I wanted to try it there.

---

### Post by Paul Miller on 2008-10-22
The harmonic series diverges.  The sum is infinity.

---

### Post by sans_b on 2008-10-22
Right but computationally there is a limit, no?  Maybe I am on a circular path.

---

### Post by sans_b on 2008-10-22
> **y-lee said:**
> You could use an arbitrary precision module such as pythons [Decimal]("http://www.python.org/doc/2.5.2/lib/module-decimal.html") class or a third party module such as [GPMPY]("http://gmpy.sourceforge.net/") or [mxNumber]("http://www.egenix.com/products/python/mxExperimental/mxNumber/").

If you are motivated you could of course write your own infinite precession class, I think all programmers should do that at least once. It is doubt full you would do a better job tho than the modules I have mentioned.


GMPy seems to be exactly what I was looking for.  Thank you.

---

### Post by Paul Miller on 2008-10-22
Let H(n)= \sum_{k=1}^n 1/k (That is, 1/1 + 1/2 + 1/3 + ... + 1/(n-1) + 1/n).  Then, ln (n) - H(n) approaches a limit known as the Euler-Mascheroni constant, typically denoted by the Greek letter gamma.  See [http://en.wikipedia.org/wiki/Euler&#8211;Mascheroni_constant](http://en.wikipedia.org/wiki/Euler&#8211;Mascheroni_constant) for more info.

---

### Post by Lux Perpetua on 2008-10-22
> **sans_b said:**
> Right but computationally there is a limit, no?  Maybe I am on a circular path.No, it grows without bound. It will eventually exceed any fixed number.

---

### Post by sans_b on 2008-10-22
> **Paul Miller said:**
> Let H(n)= \sum_{k=1}^n 1/k (That is, 1/1 + 1/2 + 1/3 + ... + 1/(n-1) + 1/n).  Then, ln (n) - H(n) approaches a limit known as the Euler-Mascheroni constant, typically denoted by the Greek letter gamma.  See [http://en.wikipedia.org/wiki/Euler–Mascheroni_constant](http://en.wikipedia.org/wiki/Euler–Mascheroni_constant) for more info.

This is very helpful, thank you.

I was very confused in thinking I could compute a value.  I think this confusion stemmed from the fact that the terms go to 0, but I see it a little better now.

---

### Post by Lux Perpetua on 2008-10-23
It's a common source of confusion...and an easy way to lose points on a calculus exam. :-)

---

