---
title: "python lambda if+for loop"
date: 2012-02-11
forum: Programming Talk
---

### Post by flyingsliverfin on 2012-02-11
Is it possible and/or practical to write a lambda that uses and if statement and a for loop?
I'm already in a function so I don't exactly want to write my another function to achieve this.

Pretty much what I want is to feed in a number X and a list Y. Then check each element of the list Y to see if it = X and return the index of Y that equals X.

Haha now that it's all written out it seems complicated enough to be its own function... but still, is it possible?

---

### Post by CptPicard on 2012-02-11
Sounds marginally possible. Python's lambdas are one-line, so you can't use standard for or if for syntactic reasons, however, you can use a list comprehension to achieve what you're after.

Shouldn't be too nasty to define a helper function though, either.

---

### Post by flyingsliverfin on 2012-02-11
Just figured it out using list comprehensions then just using the first index

Thanks!

---

### Post by holiday on 2012-02-11
Are you looking for a lambda exercise or do you want to find the index of p in a list q?

If the latter you can go

print q.index(p)

If the former? Then I'm looking forward to other responses.

---

### Post by The Cog on 2012-02-12
The original requirement isn't clear. What should be returned if no member of Y matches X, or if several members of Y match? Y.index(X) might fit the requirement, as holiday says.

Anyway, I would like to suggest that if the lambda is getting complicated then it is probably  better to write an inner function rather than a horribly long line lambda. By the time you've explained the lambda in comments (so you can understand what it's all about in a year's time) you might as well have written a function anyway.

---

