---
title: "Any math wiz?(irrational numbers)"
date: 2007-08-29
forum: Programming Talk
---

### Post by triptoe on 2007-08-29
hey i am just curious... how would i generate formula's for irrational numbers? Like i know pi is an irrational number. but is there a list of irrational number formulas somewhere? Can i just multiply pi times different numbers and get diff irrational numbers?

also how do i get pi to print out up to 80 thousand digits?

my pi has a preset width

thanks!

---

### Post by LaRoza on 2007-08-29
> **triptoe said:**
> hey i am just curious... how would i generate formula's for irrational numbers? Like i know pi is an irrational number. but is there a list of irrational number formulas somewhere? Can i just multiply pi times different numbers and get diff irrational numbers?

also how do i get pi to print out up to 80 thousand digits?

my pi has a preset width

thanks!

You can calculate Pi to any precision, but you are limited by your computers processor.

For Pi, you would find a formula that describes it, and solve the formula.

You could look up Euler's Constant, for another commonly used irrational number.

---

### Post by CptPicard on 2007-08-29
Solving formulas isn't helpful as long as you're limited by your datatype precision... you need to look at algorithms for computing arbitrary digits of pi, [like here]("http://en.wikipedia.org/wiki/Computing_%CF%80") at "digit extraction methods"... also, google for "computing pi to arbitrary precision" or something like that.

---

### Post by pmasiar on 2007-08-29
> **triptoe said:**
> hey i am just curious... how would i generate formula's for irrational numbers? 

You cannot: set of 
[http://en.wikipedia.org/wiki/Irrational_number](http://en.wikipedia.org/wiki/Irrational_number) s is [http://en.wikipedia.org/wiki/Uncountable](http://en.wikipedia.org/wiki/Uncountable)
(Rational numbers are countable)

Take peek on even more interesting numbers: [http://en.wikipedia.org/wiki/Transcendental_number](http://en.wikipedia.org/wiki/Transcendental_number)

> Can i just multiply pi times different numbers and get diff irrational numbers?

Yes, but the pi you get as constant is **not** full pi but it's  approximation :-)

> also how do i get pi to print out up to 80 thousand digits?

You need to make program to calculate [http://en.wikipedia.org/wiki/Pi](http://en.wikipedia.org/wiki/Pi) . It would take long time :-) 

For the record, I would **not** recommend doing it in Python :-)  : [http://en.wikipedia.org/wiki/Pi#Numerical_approximations](http://en.wikipedia.org/wiki/Pi#Numerical_approximations)

---

### Post by rbprogrammer on 2007-08-29
i dont know if you wanted to write a program yourself, but in the repositories there is a program called [FONT="Courier New"]pi[/FONT] that can calculate pi to different precisions. you might have to enable the backports to download and install it.

---

