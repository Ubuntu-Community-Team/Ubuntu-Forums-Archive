---
title: "[PyPy/Python] Loops in PyPy slower than in Python?"
date: 2011-12-27
forum: Programming Talk
---

### Post by kramer65 on 2011-12-27
Hello,

I've got a script which I want to speed up. It currently takes about 37 seconds, which ideally would need to be reduced to about 10 seconds. So I wanted to use PyPy instead of the normal Python (Cpython it is called I think?). Some initial tests with simple for-loops gave promising results. When I test my script though, there are pieces of code (running a zillion times), which are consistently slower in pypy. I inserted some timecounting things and two of the parts which are significantly slower in PyPy are the following:

```
def first_stop_high(date_high):
    stop_high_of_the_day = fut_open[date_high].get(buy_time, 0) * stop_high
    if stop_high_of_the_day != 0:
        for time_high in sorted(fut_open[date_high]):
            if time_high >= buy_time and fut_high[date_high][time_high] >= stop_high_of_the_day:
                first_stop[date_high] = str(time_high).zfill(4)+str(stop_high_of_the_day)
                break

def first_stop_low(date_low):
    stop_low_of_the_day = fut_open[date_low].get(buy_time, 0) * stop_low
    if stop_low_of_the_day != 0:
        for time_low in sorted(fut_low[date_low]):
            if time_low >= buy_time and fut_low[date_low][time_low] <= stop_low_of_the_day:
                if date_low in first_stop:
                    if time_low <= first_stop[date_low][:8]:
                        first_stop[date_low] = str(time_low).zfill(4)+str(stop_low_of_the_day)
                else:
                    first_stop[date_low] = str(time_low).zfill(4)+str(stop_low_of_the_day)
                break

map(first_stop_high, fut_high)
map(first_stop_low, fut_low)

```

```
while timespan <= timespan_max:
    sell_time = buy_time + timespan
    OvO_difference = []
    OvO_difference_percentage = []
    for date in fut_open:
          buy_price = fut_open[date].get(buy_time,0) 
          if date in first_stop:
               if first_stop[date][:4] < sell_time:
                    sell_price = float(first_stop[date][4:])
               else:
                    sell_price = fut_open[date].get(sell_time,0)
          else:
               sell_price = fut_open[date].get(sell_time,0)
```

There aren't any exotic features in this piece of code, so I wouldn't understand why this would run slower in PyPy instead of faster (like most of the loops).

Does anybody have any idea what's wrong here or how I would be able to speed this up (being it under PyPy or the normal Python)? All tips are welcome!

---

### Post by simeon87 on 2011-12-27
I'm guessing it's not the loop but the lookups and the function calls to dict.get(). You should run a profiler to see which function is called the most often. When you have an overview of which functions are called and how often, reduce function calls as much as you can. That alone will make it faster.

- Refactor lookups:

```
if d[key]:
    bla
if not d[key]:
    bla
```

should become

```
value = d[key]
if value:
    bla
if not value:
    bla
```

You should also avoid dots as these are always lookups in Python (due to the fact that things are dynamic in Python). A good read is also [http://wiki.python.org/moin/PythonSpeed/PerformanceTips](http://wiki.python.org/moin/PythonSpeed/PerformanceTips)

---

### Post by MadCow108 on 2011-12-27
you should definitly remove all the global namespace lookups, those are very slow in python.
concerning why it is slower in pypy I recommend looking at it in the jitviewer
[http://morepypy.blogspot.com/2011/08/visualization-of-jitted-code.html](http://morepypy.blogspot.com/2011/08/visualization-of-jitted-code.html)

my suspicion is that the branching has no pattern (= the branches are random) so you don't gain anything by jitting the code.

you could also try to place your data into numpy arrays and do the data selections there. numpy runs all loop iterations in C code so its very fast.

---

### Post by kramer65 on 2011-12-29
> **simeon87 said:**
> I'm guessing it's not the loop but the lookups and the function calls to dict.get(). You should run a profiler to see which function is called the most often.[/code]

I had never run a profiler, but that was a very good tip. I saw that dict.get was indeed a big part. I am now trying to reduce that with the tip you gave.

> **MadCow108 said:**
> you should definitly remove all the global namespace lookups, those are very slow in python.
concerning why it is slower in pypy I recommend looking at it in the jitviewer
[http://morepypy.blogspot.com/2011/08/visualization-of-jitted-code.html](http://morepypy.blogspot.com/2011/08/visualization-of-jitted-code.html)

my suspicion is that the branching has no pattern (= the branches are random) so you don't gain anything by jitting the code.

you could also try to place your data into numpy arrays and do the data selections there. numpy runs all loop iterations in C code so its very fast.

Thanks for the tip on the global namespaces and the jitviewer. I am definitely going to check it out and see how I can improve things.

One question. What exactly do you mean by "*my suspicion is that the branching has no pattern*"? Do you mean that my script is not logically set up? How would I be able to improve the branching?

---

### Post by MadCow108 on 2011-12-29
a jit works by optimizing for the common case based on the code paths chosen in the past.
if the input data causes all code paths to be taken with similar probability there is no common case to optimize for.

but it should not be much slower than unoptimized code, probably you hit some case where pypy is not very good yet. The results of the jitviewer should be interesting.
You might also want to look at how pypy optimized their pure python json library for better jit performance:
[http://morepypy.blogspot.com/2011/10/speeding-up-json-encoding-in-pypy.html](http://morepypy.blogspot.com/2011/10/speeding-up-json-encoding-in-pypy.html)
this is interesting:
> Calling methods for common infrastructure or loading globals (instead of rebinding as locals) is fast enough and improves code readability.
if you want to use pypy my previous hint of rebinding the globals could be a waste of time. (though I still think they way your code is written is very unreadable, it certainly does not fulfill the principle of least suprise [*map* editing global data is very unusual, it is normally a tool of functional = side-effect free programming])

---

