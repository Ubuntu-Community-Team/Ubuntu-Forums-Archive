---
title: "Python variable name bafflement"
date: 2006-09-09
forum: Programming Talk
---

### Post by cptnapalm on 2006-09-09
I was working through [Byte of Python]("http://swaroopch.info/text/Byte_of_Python:Object_oriented_programming") and started doing the exercise teaching Class and Object variables.  While typing I only changed the names used for the variables at the very end.

I used my name, "Patrick", for "Swaroop" and "patrick" for "swaroop".
I then used "David" for "Abdul Kalam" and "dave" for "kalam"

And I get this error when running it: Exception exceptions.AttributeError: "'NoneType' object has no attribute 'population'" in <bound method Person.__del__ of <__main__.Person instance at 0xb7d66c8c>> ignored

But when I change "dave" to "david" everything works just fine.

The result of diff is:
47,48c47,48
< dave = Person('David')
< dave.say_hi()
---
> david = Person('David')
> david.say_hi()

So that is the ONLY difference.  But the top one fails and the bottom one succeeds.  I am completely confused.

---

### Post by cwaldbieser on 2006-09-09
> **cptnapalm said:**
> I was working through [Byte of Python]("http://swaroopch.info/text/Byte_of_Python:Object_oriented_programming") and started doing the exercise teaching Class and Object variables.  While typing I only changed the names used for the variables at the very end.

I used my name, "Patrick", for "Swaroop" and "patrick" for "swaroop".
I then used "David" for "Abdul Kalam" and "dave" for "kalam"

And I get this error when running it: Exception exceptions.AttributeError: "'NoneType' object has no attribute 'population'" in <bound method Person.__del__ of <__main__.Person instance at 0xb7d66c8c>> ignored

But when I change "dave" to "david" everything works just fine.

The result of diff is:
47,48c47,48
< dave = Person('David')
< dave.say_hi()
---
> david = Person('David')
> david.say_hi()

So that is the ONLY difference.  But the top one fails and the bottom one succeeds.  I am completely confused.

Could you post the entire snippet of the non-working example?

---

### Post by yaaarrrgg on 2006-09-09
I found this thread...

[http://mail.python.org/pipermail/python-list/2005-January/263401.html](http://mail.python.org/pipermail/python-list/2005-January/263401.html)

---

### Post by cptnapalm on 2006-09-10
Interestingly that is *exactly* the same little program I was using.

cwaldbieser:  Those two lines were the only difference in the entire program.  No where else were they referenced or mentioned or anything.

yaaarrrgg: Thanks for the link.  I still don't get why it does this, but at least I know that I was not just being grossly incompetent :)

---

