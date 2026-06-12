---
title: "[SOLVED] Bash scripting help (using awk)"
date: 2007-10-24
forum: Programming Talk
---

### Post by Lord_Dicranius on 2007-10-24
Ok, so here's the background.  I'm running performance tests using netperf.  I'm running multiple streams, so I come out with multiple lines of output (these results are stored in a file called "results.log").  The 5th column in the output is my throughput, but I need to add them all together (adding 100 streams using a calculator gets tedious heh).

So using awk, I'm able to print all the throughputs
```

awk '/60/ { print $5 }' results.log

```
NOTE: "60" is how many seconds the test is running for, so it's constant in all the lines of output so that's what I'm using for the search :)

What I'm trying to do now is take the output of awk there and store them in an array.  So then I can use the array and add each element together.

I'm taking a class right now and part of it is learning Perl, which helps a little, but bash scripting is a whole nother world haha  Any help is greatly appreciated! :D

---

### Post by keelerm on 2007-10-24
If you just want the sum, then let awk do the work for you.  There is no need to bother with arrays.
```
awk 'BEGIN {sum=0} /60/ { sum+=$5 } END {print sum}' results.log
```

---

### Post by Lord_Dicranius on 2007-10-24
Awesome!  You are a life/time saver :)

Another quick question if ya don't mind.  If I awk $6, this'll give me all the CPU utilizations for all the streams.  How would you go about comparing them all and finding the max?

If you help me out with this too, I'll send you some candy or something hehe

---

### Post by Lord_Dicranius on 2007-10-24
Scratch that last post, using a different tool now to measure CPU utilization (sar from the sysstat toolkit).

Thanks for your help keelerm! :-D

---

### Post by ghostdog74 on 2007-10-24
> **keelerm said:**
> If you just want the sum, then let awk do the work for you.  There is no need to bother with arrays.
```
awk 'BEGIN {sum=0} /60/ { sum+=$5 } END {print sum}' results.log
```

no need for BEGIN block.
```

awk '/60/ { sum+=$5 } END {print sum}' file

```

---

### Post by keelerm on 2007-10-24
Just habit to initialize I suppose.  :)

---

### Post by Lord_Dicranius on 2007-10-24
> **ghostdog74 said:**
> no need for BEGIN block.
```

awk '/60/ { sum+=$5 } END {print sum}' file

```
Ah, good to know :)

---

