---
title: "python speed up"
date: 2010-09-07
forum: Programming Talk
---

### Post by nbo10 on 2010-09-07
I'm averaging the values in a matrix with piece of code like this 

```

   for i in range(0,H,1):
        for j in range(0,W,1):
            IntRed[i,j] = np.mean(RawRed[i-length:i+length,j-length:j+length])
            IntGreen[i,j] = np.mean(RawGreen[i-length:i+length,j-length:j+length])
            IntBlue[i,j] = np.mean(RawBlue[i-length:i+length,j-length:j+length])

```
With a H = W = 512 the run time is about a minute. Is there any way I can rewrite this code to speed up the execution time? Thanks

---

### Post by schauerlich on 2010-09-07
In general, python is faster the longer it spends "in C" (meaning using fewer separate language constructs). If you could rephrase this into a list comprehension or generator expression, it would probably be faster. No guarantees though.

---

### Post by raffaele181188 on 2010-09-07
You are executing 512 * 512 cycles! eheh don't expect it to finish soon
Anyway, you could using 3 threads to take advantage of multicore machines, or even multithreading in C

---

### Post by StephenF on 2010-09-07
The NumPy module does matrices. Perhaps you could look into that.

---

### Post by Wybiral on 2010-09-08
Without investigating the situation too much (meaning there may be more you can do here to speed it up some), but one suggestion is to avoid doing some of your computation in the inner loop. Right away, I can see that i-length and i+length are computed W * 3 times for each i, when really they each only need to be done once, in the H loop, just create a y1 and y2 variable to store those ranges.

But yes, if there's any way you can toss more of this computation onto NumPy or the Python interpreter itself, that will speed it up some.

---

### Post by StephenF on 2010-09-08
Your code is calling Raw[colour] on each iteration j with an overlap of length*2-2 (consider that value to have a close relationship to the time wastage factor). It would be quicker to use a collections.deque object over a window of size W and append/pop(0) as you go along using the values going into and out of to maintain an impression of the sum value. The mean is that value divided by W (except at the edges obviously). I would do the divide step on a separate pass so the edge calculations can be optimised.

Thought number two is that averaging is occurring over one dimension whereas photographs have two the last time I looked. I guess you just run similar code again over the other axis.

---

### Post by smartbei on 2010-09-08
You might want to try profiling your code - see the profile module.

---

### Post by juancarlospaco on 2010-09-08
Numpy+Psyco

---

