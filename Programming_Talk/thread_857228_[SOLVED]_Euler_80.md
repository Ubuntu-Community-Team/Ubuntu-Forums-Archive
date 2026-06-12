---
title: "[SOLVED] Euler 80"
date: 2008-07-12
forum: Programming Talk
---

### Post by KMuchane on 2008-07-12
Habari,  

I was wondering where I am going wrong on this problem ? Using Python 's decimal module, I have tried everything but  I get a wrong answer . Surprisingly, for square root of 2, I get the sum as 475.  I would appreciate a nudge in the right direction.   
Thanks!

---

### Post by ghostdog74 on 2008-07-12
here's the first nudge, post your code. How do you suppose anyone can help without these information?

---

### Post by Replicon on 2008-07-12
Heh sweet, I totally forgot about projecteuler. I just logged back in. I solved the first 97 problems and then kinda stopped going there.

I just checked, and I still have my solution available. I used Java, just because BigDecimal makes things nicer. I computed the sqrts using some form of iterative process, which relies on starting with a number that's 'sufficiently close'. One comment in my file:

```

        // wow it converges to 100 digits after only three iterations!! (given that the
        // start point is already at sqrt(n) hehe).

```

This should be a sufficient hint ;-)

---

### Post by KMuchane on 2008-07-12
Habari, 

Replicon, you have just confounded me farther. A not too giving away example perhaps ?

---

### Post by Replicon on 2008-07-12
Sorry, didn't mean to!

If you're gettng 475 for sqrt(2), there's a good chance you're doing things right. Remember, they ONLY want sums from irrational square roots (so don't go including digits from numbers like sqrt(25)).

Looks like the method I used to actually compute sqrt was the Babylonian method: [http://en.wikipedia.org/wiki/Methods_of_computing_square_roots#Babylonian_method](http://en.wikipedia.org/wiki/Methods_of_computing_square_roots#Babylonian_method)

Combine that with BigDecimal (where you can arbitrarily specify your desired accuracy), and you've pretty much got a guarantee that your computation will be accurate to 100 digits. I imagine you can do the same with Python.

But like I said, if you get the 475, I bet the problem is what's in the first paragraph :)

---

### Post by kavon89 on 2008-07-12
Just create your own method to compute square roots imo. This should help get you started:

EDIT2: I'm retarded, Replicon isn't OP, KMuchane is. There is the code that Replicon is talking about in Java. It's pretty straightforward if you compare the variable's values with the line saying to add and divide etc.

```
        BigDecimal approx = new BigDecimal(1);
        BigDecimal onehalf = new BigDecimal(0.5);
        BigDecimal sqrt = new BigDecimal(2);
        MathContext prsc = new MathContext(1001);

for (int i = 1; i < 32; i++) {
                approx = onehalf.multiply(approx.add(sqrt.divide(approx, prsc)));
            }
```

It is pretty efficient, and uses [the Babylonian method]("http://en.wikipedia.org/wiki/Methods_of_computing_square_roots#Babylonian_method") of computing square roots.

Edit the MathContext and lower the amount of times the loop occurs if you don't need 1000 decimal places etc. The number of loops is the accuracy of the result.

---

### Post by Replicon on 2008-07-13
That's exactly right. And if your initial estimate (approx) starts out as Math.sqrt(<whatever>), you can lower that 32 to 3 :-)

---

### Post by KMuchane on 2008-07-13
Habari, 

I think I should have my head examined ! The problem was that I was not including the number to the left of the decimal !

---

