---
title: "Delay calculation calibrate.c"
date: 2010-04-09
forum: Programming Talk
---

### Post by tapas_mishra on 2010-04-09
Well its a very simple problem I am not clear with some C syntax I am reading C and other books and I hope I shall be able to figure it out any ways but if some one feels I should be clear of some thing let me know I am not clear with the working of calibrate.c

I will quote the important lines of code that I think are confusing me and explain the aspects of them that I think I don't understand.


```
loops_per_jiffy = (1 << 12); /* Initial approximation = 4096 */
```
The choice of number 4096
power of 2 that is 12 why is that choosen.

Secondly
[http://lxr.linux.no/#linux+v2.6.33/init/calibrate.c#L54](http://lxr.linux.no/#linux+v2.6.33/init/calibrate.c#L54)
In comments it is mentioning

So, we do
* 1. pre_start <- When we are sure that jiffy switch hasn't happened
* 2. check jiffy switch
* 3. start <- timer value before or after jiffy switch
* 4. post_start <- When we are sure that jiffy switch has happened
What is all that pre_start and why is it needed to be used over here?

Here is some thing which I am wondering not because of logic in same program
while (ticks == jiffies);/* Wait till the start of next jiffy */

Till the start of next jiffy what is the processor busy with or how is the delay introduced here?Not the mathematical calculation for udelay or ndelay.
May be I am not clear with what I should search for.

---

### Post by MindSz on 2010-04-09
> **tapas_mishra said:**
> 
Here is some thing which I am wondering not because of logic in same program
while (ticks == jiffies);/* Wait till the start of next jiffy */

Till the start of next jiffy what is the processor busy with or how is the delay introduced here?Not the mathematical calculation for udelay or ndelay.
May be I am not clear with what I should search for.

I don't really know about the rest of your question, but in the while statement the delay is in the comparisson. So you keep comparing ticks to jiffies and you will only exit when they are different.

Usually people puts sleep() calls inside the loop so you free up some processor time (at least in embedded systems, where computing power is limited)

---

### Post by MadCow108 on 2010-04-09
1. 
init/main.c 225
/*
* This should be approx 2 Bo*oMips to start (note initial shift), and will
* still work even if initially too large, it will just take slightly longer
*/
unsigned long loops_per_jiffy = (1<<12);
this is just a starting guess. the first loop increases it to a value greater than loops_per_jiffy
in the second loop it is then reduced until it is an approximate loops per jiffy
4096 is probably just a good guess for modern architecture
[http://en.wikipedia.org/wiki/BogoMips](http://en.wikipedia.org/wiki/BogoMips)

2. concerning the pre_start and post_start I need to guess, so following may be incorrect:
I assume read_current_timer reads some value from the chip where the timer value is saved, but this timer is probably asynchron and only updated periodically.
So it could be that read_current_timer reads a value which so old that it predates the jiffy switch check.
Additionally the code could get interrupted by some event between the jiffy check and the read timer code

To solve this you do it three times, pre_start, real and post_start
by looking at the difference of pre_start and post_start you can determine if above problems have happened, and it is just retries until it works.


3. while (ticks == jiffies);
this is a busy wait. the cpu compares these two memory locations until they differ. Comparisons take time so its a delay. (it will not get optimized away because jiffy is volatile)
this is necessary because one wants to be as close to the beginning of the jiffy switch as possible to get an accurate approximation.

---

### Post by pbrane on 2010-04-10
It might also be that the delay is not always calculated in the delay loop. This is from my log:

**Calibrating delay loop (skipped), value calculated using timer frequency.. 3988.05 BogoMIPS**

---

### Post by tapas_mishra on 2010-04-18
> **MadCow108 said:**
> 

To solve this you do it three times, pre_start, real and post_start
by looking at the difference of pre_start and post_start you can determine if above problems have happened, and it is just retries until it works.

Ok from what I understood is pre_start you are trying to find out wether jiffy value has increased or not?

> **MadCow108 said:**
> 
3. while (ticks == jiffies);

this is necessary because one wants to be as close to the beginning of the jiffy switch as possible to get an accurate approximation.
I am new to this thing.Why would some one want to be as close to the beginning of the jiffy switch as possible?

---

### Post by MadCow108 on 2010-04-18
> **tapas_mishra said:**
> Ok from what I understood is pre_start you are trying to find out wether jiffy value has increased or not?

that is done anyway.
one just wants to avoid problems due to asynchronous events and ordering issues by measuring multiple times and discarding values with to high deviations.
the problem described below is solved by that too.
> 
I am new to this thing.Why would some one want to be as close to the beginning of the jiffy switch as possible?

lets say jiffies change every 250 ms (which is rather big compared to clock frequency)
assume we enter delay calibration 125ms after the last jiffy change
If we now measure the loops until the next jiffy change, and we get the value for the remaining 125ms, clearly wrong
so we wait in the calibration until a jiffy has changed. Then the time to the next jiffy is approximately one jiffy and we get a relatively good measurement when there is no delay code between the wait and the measurement

---

### Post by tapas_mishra on 2010-04-24
> **MadCow108 said:**
> that is done anyway.
one just wants to avoid problems due to asynchronous events and ordering issues by measuring multiple times and discarding values with to high deviations.
the problem described below is solved by that too.

Ok its getting a bit clearer.
> **MadCow108 said:**
> 
lets say jiffies change every 250 ms (which is rather big compared to clock frequency)
assume we enter delay calibration 125ms after the last jiffy change
If we now measure the loops until the next jiffy change, and we get the value for the remaining 125ms, clearly wrong

Not clear on this part you measured the value from 125 to 250 ms time interval is that what is done?

---

