---
title: "Delay calculation in init/calibrate.c"
date: 2010-04-04
forum: Programming Talk
---

### Post by tapas_mishra on 2010-04-04
I will quote the important lines of code that I think are confusing me and explain the aspects of them that I think I don't understand.


```
loops_per_jiffy = (1 << 12); /* Initial approximation = 4096 */
```The choice of number 4096 
power of 2 that is 12 why is that chosen?

Secondly
[http://lxr.linux.no/#linux+v2.6.33/init/calibrate.c#L54](http://lxr.linux.no/#linux+v2.6.33/init/calibrate.c#L54)
In comments it is mentioning
```

 So, we do
 * 1. pre_start <- When we are sure that jiffy switch hasn't happened
 * 2. check jiffy switch
 * 3. start <- timer value before or after jiffy switch
 * 4. post_start <- When we are sure that jiffy switch has happened

```What is all that pre_start and why is it needed to be used over here?

Here is some thing which I am wondering not because of logic in same program
```

 while (ticks == jiffies);/* Wait till the start of next jiffy */
```Till the start of next jiffy what is the processor busy with or how is the delay introduced here?Not the mathematical calculation for udelay or ndelay.
May be I am not clear with what I should search for?

---

### Post by pbrane on 2010-04-04
Have you seen this?
[http://en.wikipedia.org/wiki/Jiffy_%28time%29]("http://en.wikipedia.org/wiki/Jiffy_%28time%29")
It doesn't answer youor question directly but may give some insight into the kernel time mechanism.

There is also this link:
[http://www.kernel.org/doc/man-pages/online/pages/man7/time.7.html]("http://www.kernel.org/doc/man-pages/online/pages/man7/time.7.html")

---

### Post by tapas_mishra on 2010-04-04
> **pbrane said:**
> Have you seen this?
[http://en.wikipedia.org/wiki/Jiffy_%28time%29]("http://en.wikipedia.org/wiki/Jiffy_%28time%29")
It doesn't answer youor question directly but may give some insight into the kernel time mechanism.

I am aware of above that you mentioned.
> 
There is also this link:
[http://www.kernel.org/doc/man-pages/online/pages/man7/time.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/time.7.html)[/QUOTE]
This did not help much but thanks any ways.

---

