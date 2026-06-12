---
title: "random 3d walk hits 0 on even steps?"
date: 2007-02-23
forum: Programming Talk
---

### Post by qpwoeiruty on 2007-02-23
edit: Of course a random walk can be even. L=1 so a step away from the origin always has to have one back :P

---

### Post by Lux Perpetua on 2007-02-23
After every iteration, the sum of your coordinates changes by one (either increases by one or decreases by one), so it has to alternate between even and odd numbers. After an odd number of steps, the sum of your coordinates is therefore necessarily odd, so you cannot be at the origin after an odd-numbered step.

---

### Post by Wybiral on 2007-02-23
Your code looks like you're trying to randomly move or "jitter" a point in 3d... Other than that, what exactly are you trying to do? And what's wrong with the output being even?

BTW, I don't see anything stopping the "origin" variable from going over 24... This can cause overflow issues since it's indexing an array with only 25 dimensions... That's pretty dangerous!

---

### Post by qpwoeiruty on 2007-02-23
> **Lux Perpetua said:**
> After every iteration, the sum of your coordinates changes by one (either increases by one or decreases by one), so it has to alternate between even and odd numbers. After an odd number of steps, the sum of your coordinates is therefore necessarily odd, so you cannot be at the origin after an odd-numbered step.

You know... that's completely correct :P
That's one of those things I stare at for a long time and don't even consider... thanks!

> Your code looks like you're trying to randomly move or "jitter" a point in 3d... Other than that, what exactly are you trying to do? And what's wrong with the output being even?

BTW, I don't see anything stopping the "origin" variable from going over 24... This can cause overflow issues since it's indexing an array with only 25 dimensions... That's pretty dangerous!

That's exactly what I'm trying to do. See:
[http://en.wikipedia.org/wiki/Random_walk](http://en.wikipedia.org/wiki/Random_walk)
[http://mathworld.wolfram.com/PolyasRandomWalkConstants.html](http://mathworld.wolfram.com/PolyasRandomWalkConstants.html)

As for "origin", the chances of getting more than 25 entries into the array is so remote, I didn't think it necessary to do anything different. It would be a miracle or an error to produce that.

Thanks for the helP!

---

### Post by Wybiral on 2007-02-23
> **qpwoeiruty said:**
> You know... that's completely correct :P
That's one of those things I stare at for a long time and don't even consider... thanks!



That's exactly what I'm trying to do. See:
[http://en.wikipedia.org/wiki/Random_walk](http://en.wikipedia.org/wiki/Random_walk)
[http://mathworld.wolfram.com/PolyasRandomWalkConstants.html](http://mathworld.wolfram.com/PolyasRandomWalkConstants.html)

As for "origin", the chances of getting more than 25 entries into the array is so remote, I didn't think it necessary to do anything different. It would be a miracle or an error to produce that.

Thanks for the helP!

Ok... But never rely on the predictability of random numbers!

But, assuming it was a test that only you were going to run, it won't do any harm. The big risk is just the program crashing.

---

