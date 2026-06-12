---
title: "Not sure the best way to do this in Python"
date: 2011-03-03
forum: Programming Talk
---

### Post by raf-kig on 2011-03-03
The following code snippet is to evaluate all possible 5-card poker hands from a simulated deck of cards. If there's a more optimum way of coding it I would appreciate some help because this one is S-L-O-W. Thanks. (Needless to say I'm a Python noob.)
```

deck = range(1,53)
hand = range(5)
for k in range(0, 48):
    hand[0]=deck[k]
    for k in range(1, 49):
        hand[1]=deck[k]
        for k in range(2, 50):
            hand[2]=deck[k]
            for k in range(3, 51):
                hand[3]=deck[k]
                for k in range(4, 52):
                    hand[4]=deck[k]
                    # evaluate the hand here

```

---

### Post by NovaAesa on 2011-03-03
There are only 52 C 5 possible hands (2,598,960). At the moment you are checking 52 P 5 hands (311,875,200). While both ways are doable with a brute force attack, using combinations rather than permutations will make things quicker.

I would suggest taking a look at combinations() in itertools:
[http://docs.python.org/library/itertools.html#itertools.combinations](http://docs.python.org/library/itertools.html#itertools.combinations)

---

### Post by DaithiF on 2011-03-03
well there are 254 million permutations, so if you're going to evaluate each its going to take time!

---

### Post by NovaAesa on 2011-03-03
> **DaithiF said:**
> well there are 254 million permutations, so if you're going to evaluate each its going to take time!

You're right, it will take a while but it's still doable if it only has to be computed as a one off.

To the OP, if you have to do stuff in real time e.g. as part of a tool to assist while playing poker you might want to look into Monte Carlo simulations as an alternative.

---

### Post by LemursDontExist on 2011-03-03
Assuming the calculation you're performing is of any complexity at all, you're going to need to seriously reduce the number of computations you're doing.  As NovaAesa noted, order doesn't matter in a poker hand, so you're better off looking at combinations rather than permutations - but I doubt that'll be enough.

You can get a further improvement by taking advantage of symmetries - for instance, the particular suit of a card doesn't matter as long as it is correctly related to the later cards.  You could force the suit of the first card to be spades, and that'll reduce the number of possibilities by a factor of 4.  You can similarly force the second suit, if there is one, to be hearts, and that'll get you another improvement, the exact amount would take some thinking, but I'd bet at least a factor of 2.

You're still looking at 300,000 odd computations though. I would test the runtime of your evaluation code and see if this is practical.  The timeit module can be very helpful for this sort of testing.

I'm generally a big promoter of python, but for this particular sort of heavily algorithmic code where speed is necessarily important you really would probably be better served using C.  If you intend to stick with python, you should look up the psyco module, which should substantially speed up your for-loop execution.

Anyway, I hope this all helps!

---

### Post by raf-kig on 2011-03-03
> **NovaAesa said:**
> You're right, it will take a while but it's still doable if it only has to be computed as a one off.

To the OP, if you have to do stuff in real time e.g. as part of a tool to assist while playing poker you might want to look into Monte Carlo simulations as an alternative.

Oh no, this has nothing to do with playing poker in real time. I'm learning Python and as an exercise decided to translate some of my C programs into Python as a learning aid. I took [this]("http://www.suffecool.net/poker/evaluator.html") and made a variation using only prime numbers with no table lookups. Then I got the bright idea to translate it into Python.

---

### Post by raf-kig on 2011-03-04
I made big mistake in trying to *literally* emulate a C for-loop in Python, which I found out is not possible. Here's the way that code snippet should've been written, and this executes in a reasonable amount of time:```
    
    a = b = c = d = e = 0
    deck = range(1, 53)
    hand = range(5)
    while(a < 48):
        hand[0]=deck[a]
        a = b = a+1;
        while(b < 49):
            hand[1]=deck[b]
            b = c = b+1
            while(c < 50):
                hand[2]=deck[c]
                c = d = c+1
                while(d < 51):
                    hand[3]=deck[d]
                    d = e = d+1
                    while(e < 52):
                        hand[4]=deck[e]
                        e = e + 1
                        # evaluate hand here

``````
$ time ./allfive.py

real    0m1.967s
user    0m1.908s
sys     0m0.016s


```

---

