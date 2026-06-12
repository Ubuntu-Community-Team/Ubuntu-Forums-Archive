---
title: "How to round up on floating point numbers in Python?"
date: 2009-07-19
forum: Programming Talk
---

### Post by Jimleko211 on 2009-07-19
I want to calculate dollar amounts for a loan calculator problem, but I rain into a problem.  If you divide 106 dollars by 12 months, you get $8.833333333333333333333333 to infinity.  I want to know how to round that up to $8.84.  Any help?

---

### Post by escapee on 2009-07-19
I don't suppose you've checked the Python docs for this answer, have you?

---

### Post by Kazade on 2009-07-19
[Use Decimal instead.]("http://docs.python.org/library/decimal.html")

---

### Post by smartbei on 2009-07-19
That doesn't solve the problem. In fact, in his case, it makes it worse (Now you've got unlimited precision .3333333) :-)

There is the built-in 'round' function. Try 'help(round)' in the shell.

---

### Post by tqx on 2009-07-19
As the above poster said, use round:

```

>>> print round(106./12, 2) # The second argument is the place to round to.
8.83

```

---

### Post by Kazade on 2009-07-19
> **smartbei said:**
> That doesn't solve the problem. In fact, in his case, it makes it worse (Now you've got unlimited precision .3333333) :-)

There is the built-in 'round' function. Try 'help(round)' in the shell.

My point is that floating point should never be used for currency values. He should be using Decimal throughout. He could use round, but that's just patching over the problem for final output, it doesn't prevent off-by-one errors. :)

Edit:

You can also use locale which might be better, see the example here: [http://stackoverflow.com/questions/320929/currency-formatting-in-python](http://stackoverflow.com/questions/320929/currency-formatting-in-python)

---

### Post by unutbu on 2009-07-19
[PHP]#!/usr/bin/env python
from decimal import (Decimal,ROUND_UP)

class Money(object):
    q=Decimal('0.01')
    def __init__(self,val):
        '''
        val can be an int, float, Decimal, or Money instance 
        or a string representation of a number
        '''
        #
        # The quantize() call rounds val to 2 decimal places
        #
        self.money=Decimal(str(val)).quantize(self.q,rounding=ROUND_UP)
    def __div__(self,other):
        try:
            #
            # If other is also Money, then divide their .money attributes
            # and return another Money instance
            #
            return Money(self.money/other.money)
        except AttributeError:
            # If other is not Money, then try dividing by the value of 'other' itself.
            # This should work for int, floats, Decimals.
            # Of course, once the calculation is done, return a Money instance.
            # (It takes Money to make Money? :))
            return Money(self.money/other)
    def __mul__(self,other):
        try:
            return Money(self.money*other.money)
        except AttributeError:
            return Money(self.money*other)
    def __sub__(self,other):
        try:
            return Money(self.money-other.money)
        except AttributeError:
            return Money(self.money-other)
    def __add__(self,other):
        try:
            return Money(self.money+other.money)
        except AttributeError:
            return Money(self.money+other)
    def __str__(self):
        return str(self.money)
[/PHP]
```

a=Money(106)
print(a)
# 106.00
b=12
print(b)
# 12
c=a/b
print(c)
# 8.84
print(type(c))
# <class '__main__.Money'>
```

PS. Are you sure you want money to always be rounded up?
Sometimes it seems money is rounded down or just rounded...
See [http://docs.python.org/library/decimal.html#module-decimal](http://docs.python.org/library/decimal.html#module-decimal) for more rounding options. (Search for "ROUND_05UP").

---

