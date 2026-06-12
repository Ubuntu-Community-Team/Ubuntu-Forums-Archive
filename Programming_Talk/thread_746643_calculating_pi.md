---
title: "calculating pi"
date: 2008-04-05
forum: Programming Talk
---

### Post by papermoon on 2008-04-05
hey, im new to python as well as programming on the whole.
I know that pi can be approximated by the series :-

(pi/4) = 1 - (1/3) + (1/5) - (1/7) + (1/9)..... etc

I want to implement this in a python program but I'm not sure how to do it

any help would be appreciated!

---

### Post by papermoon on 2008-04-05
oh and i don't want to guys to code it/do it for me. I just want hints and/or a little push start.
I want to do most of it by myself so i can learn. copy pasting code wouldn't do me much good >_>

---

### Post by Shining Arcanine on 2008-04-05
You want an integer, say Pi, outside of the loop declared to 0. Then you want to iterate the loop from i = 0 to some upper bound and have something like:

if i & 1 == 1 then Pi += (-1) / (2 * i + 1) else Pi += 1 / (2 * i + 1)

2 * i could and probably should be replaced by (1 << i), which is a bit shift in binary. It is analogous to the fact that multiplying by powers of 10 in base 10 means you just need to shift the numbers over. i & 1 is a binary operator that will compare the least significant bit of the base 2 representation to 1, returning 1 if it is 1 and 0 if it is 0. This enables you to test for whether or not the number is odd or even, which is necessary as a consequence of the alternating signs.

I tried to keep the code like stuff in my post to a minimum. I hope that helps.

---

### Post by tamoneya on 2008-04-05
you dont actually want it to be an integer.  Otherwise it will just = 3 eventually.  You want to make it a floating point number the easiest way to do this is to place as a declaration.```
Pi = 0.0
```

---

### Post by jpkotta on 2008-04-05
[http://docs.python.org/tut/node6.html#SECTION006200000000000000000](http://docs.python.org/tut/node6.html#SECTION006200000000000000000)

Also, that series converges incredibly slowly.  You will be much better off with a faster converging series.

---

### Post by papermoon on 2008-04-05
this might seem like a really stupid question but what's the syntax for a for next loop in python?
i want to do  i for 1 to 500

oops i now saw your post jpkotta 

thanks

---

### Post by jpkotta on 2008-04-05
[http://docs.python.org/tut/node6.html#SECTION006200000000000000000](http://docs.python.org/tut/node6.html#SECTION006200000000000000000)

Also, that series converges incredibly slowly.  You will be much better off with a faster converging series. 

From a numerical point of view, it is almost always better to add the smallest terms first.  Addition is commutative, but what computers do is an approximation of the pure mathematical notion of addition, so order does matter.

---

### Post by papermoon on 2008-04-05
I wrote this code in BASIC but it doesn't give me the right answer. What's wrong with it?

> i = 0
pi = 1
n = 3

DO WHILE i < 20
        pi = pi - (1 / n)
        n = n + 2
        pi = pi + (1 / n)
        i = i + 1
LOOP

PRINT pi

The program outputs 0.6899225

oh i now remembered it gives .25 pi and not pi.
.6899225 * 4 still doesn't give me pi though :(

---

### Post by Lux Perpetua on 2008-04-06
Execute your code manually on paper, keeping track of all your variables explicitly as you go along. You'll soon see what's wrong.

Also, note that looping while i < 20 will not get you a good approximation to pi. N terms of the series will only get to within about 1/N of the true value of pi, so to get n correct digits, you'll need about 10^n terms (!).

---

### Post by tamoneya on 2008-04-06
like jpkotta said.  That series takes a long time to converge and will be less than pi one time and then greater than pi the next.  It eventually equals pi but it takes a while before it is close enough.

---

### Post by Quikee on 2008-04-06
> **tamoneya said:**
> It eventually equals pi..

Actually, it will never equal pi. ;)

---

### Post by Shining Arcanine on 2008-04-06
> **tamoneya said:**
> you dont actually want it to be an integer.  Otherwise it will just = 3 eventually.  You want to make it a floating point number the easiest way to do this is to place as a declaration.```
Pi = 0.0
```

Thanks for catching that. I am not sure what I was thinking yesterday.

---

### Post by jpkotta on 2008-04-06
A reasonably simple formula that converges reasonably fast is the Machin formula.

[http://en.wikipedia.org/wiki/Machin-like_formula](http://en.wikipedia.org/wiki/Machin-like_formula)
[http://en.wikipedia.org/wiki/Arctan#Infinite_series](http://en.wikipedia.org/wiki/Arctan#Infinite_series)

---

### Post by alexforcefive on 2008-04-06
> **papermoon said:**
> (pi/4) = 1 - (1/3) + (1/5) - (1/7) + (1/9)..... etc!

Wow, I didn't know that! That's pretty crazy!

Is there any benefit to calculating pi this way rather than just importing the math module? Or did you just want to figure out how to do it?

---

### Post by Quikee on 2008-04-07
> **alexforcefive said:**
> 
Is there any benefit to calculating pi this way rather than just importing the math module? 

None, what so ever as probably PI in the math module is a constant value.

---

### Post by hums07 on 2008-04-07
> **papermoon said:**
> I wrote this code in BASIC but it doesn't give me the right answer. What's wrong with it?

The program outputs 0.6899225

oh i now remembered it gives .25 pi and not pi.
.6899225 * 4 still doesn't give me pi though :(

Needs 300 terms to make it correct to 2 decimal places, [http://en.wikipedia.org/wiki/Pi](http://en.wikipedia.org/wiki/Pi)

---

