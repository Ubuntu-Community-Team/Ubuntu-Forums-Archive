---
title: "Something I learned in Python"
date: 2009-10-18
forum: Programming Talk
---

### Post by thunderdan on 2009-10-18
I've just started learning Python, and I got excited about something I learned, and I wanted to share it. I made my computer count from 1 to a million, and I did it with 2 lines of code! Here is the program:
```
for x in range(1, 1000001, 1):
    print x

```
That's it! It's so fun to make the computer do what I want it to, no matter how useless it is. I wonder what I should make it do next.

---

### Post by j7%&lt;RmUg on 2009-10-18
Nice, if you experiment lots you can do some awesome things with python.

Just curious, how long(approximately) does it take that script to count to a million?

---

### Post by ghostdog74 on 2009-10-18
wow...such a big deal..but good job nonetheless.
```

# seq 1 1000000

```

---

### Post by thunderdan on 2009-10-18
> **nisshh said:**
> Nice, if you experiment lots you can do some awesome things with python.

Just curious, how long(approximately) does it take that script to count to a million?

About 15-20 seconds. I know what I'll do next! I'll figure out how to make Python record what time it is when it starts counting, and record the time again when it's finished, and print those results so we will know the exact amount of time it took.

I have research to do! Thanks for the idea! :):):):)

---

### Post by ghostdog74 on 2009-10-18
> **thunderdan said:**
> About 15-20 seconds. 
```

# time python -c "for x in range(1, 1000001, 1): print x" > /dev/null

real    0m2.199s
user    0m2.097s
sys     0m0.034s

# time seq 1 1000000 >/dev/null

real    0m1.941s
user    0m1.908s
sys     0m0.004s

# time awk 'BEGIN{for(i=1;i<=1000000;i++)print i}' >/dev/null

real    0m1.456s
user    0m1.442s
sys     0m0.002s


```
awk rules !

---

### Post by thunderdan on 2009-10-18
> **ghostdog74 said:**
> ```

# time python -c "for x in range(1, 1000001, 1): print x" > /dev/null

real    0m2.199s
user    0m2.097s
sys     0m0.034s

# time seq 1 1000000 >/dev/null

real    0m1.941s
user    0m1.908s
sys     0m0.004s

# time awk 'BEGIN{for(i=1;i<=1000000;i++)print i}' >/dev/null

real    0m1.456s
user    0m1.442s
sys     0m0.002s


```
awk rules !

I hope to someday understand what you have said in this post. :P

---

### Post by wmcbrine on 2009-10-18
Note that most of the time is in the printing, not the counting. Even when redirecting it to /dev/null.

---

### Post by ghostdog74 on 2009-10-18
> **wmcbrine said:**
> Note that most of the time is in the printing, not the counting. Even when redirecting it to /dev/null.

it doesn't matter, as long as the criteria remains the same across each subject that are tested.
```

# time python -c "for x in range(1, 1000001): pass"  

real    0m0.371s
user    0m0.322s
sys     0m0.034s

# time awk 'BEGIN{for(i=1;i<=1000000;i++){;}}' 

real    0m0.276s
user    0m0.274s
sys     0m0.002s


```

---

### Post by thunderdan on 2009-10-18
> **wmcbrine said:**
> Note that most of the time is in the printing, not the counting. Even when redirecting it to /dev/null.

I think your message originally said something about xrange. I looked that up in Python help, and it said xrange is usually faster than range. So there's another idea I can do: Once I figure out how to record the time, I'll write a program that times itself for counting to a million using range, and then have it time itself for counting to a million using xrange, and compare the difference.

I've found some information about time in Python, but I'm still figuring out how I can use it for my purposes. I'll update again once I have something.

---

### Post by Flimm on 2009-10-18
> **thunderdan said:**
> I've just started learning Python, and I got excited about something I learned, and I wanted to share it. I made my computer count from 1 to a million, and I did it with 2 lines of code! Here is the program:
```
for x in range(1, 1000001, 1):
    print x

```
That's it! It's so fun to make the computer do what I want it to, no matter how useless it is. I wonder what I should make it do next.
You can make it into just one line:
[php]for x in xrange(1, 1000001, 1): print x[/php]

---

### Post by thunderdan on 2009-10-18
> **Flimm said:**
> You can make it into just one line:
[php]for x in xrange(1, 1000001, 1): print x[/php]

Right on. Also, I learned that if the increment desired is 1, it is not necessary to type that in the argument for range() or xrange(). So it would be like this:

```
for x in xrange(1, 1000001): print x
```

Thanks for the tip! :)

---

### Post by -grubby on 2009-10-18
Generally speaking, eschewing indentation is not a good thing

---

### Post by thunderdan on 2009-10-18
> **-grubby said:**
> Generally speaking, eschewing indentation is not a good thing

Cool cool. I will stick to the original 2 lines, then. I see how your point is especially true with longer code blocks.

---

### Post by Can+~ on 2009-10-18
The same principle of [FONT="Courier New"]range(start, end, step)[/FONT], applies to slicing:

[PHP]>>> x = "Hello World!"
>>> x[:] # All (same as x)
'Hello World!'
>>> x[2:] # From 2 onwards
'llo World!'
>>> x[2:5] # From 2 to 5
'llo'
>>> x[::2] # start to end, jump 2
'HloWrd'
>>> x[::-1] # Backwards
'!dlroW olleH'[/PHP]

---

### Post by thunderdan on 2009-10-18
> **Can+~ said:**
> The same principle of [FONT="Courier New"]range(start, end, step)[/FONT], applies to slicing:

[PHP]>>> x = "Hello World!"
>>> x[:] # All (same as x)
'Hello World!'
>>> x[2:] # From 2 onwards
'llo World!'
>>> x[2:5] # From 2 to 5
'llo'
>>> x[::2] # start to end, jump 2
'HloWrd'
>>> x[::-1] # Backwards
'!dlroW olleH'[/PHP]

Neato :)

---

### Post by wmcbrine on 2009-10-18
> **thunderdan said:**
> I think your message originally said something about xrange.Yeah, I took that paragraph out because I thought it might sound like I was being picky (though that was not my intent), and here you were just expressing the joy of discovery, and I didn't want to step on that.

---

### Post by -grubby on 2009-10-18
> **thunderdan said:**
> Cool cool. I will stick to the original 2 lines, then. I see how your point is especially true with longer code blocks.

Eschewing indentation only works for one statement anyway.

---

### Post by thunderdan on 2009-10-18
> **wmcbrine said:**
> Yeah, I took that paragraph out because I thought it might sound like I was being picky (though that was not my intent), and here you were just expressing the joy of discovery, and I didn't want to step on that.

LOL, you're very considerate!

---

### Post by thunderdan on 2009-10-18
I found this thread: [http://ubuntuforums.org/showthread.php?t=876479](http://ubuntuforums.org/showthread.php?t=876479)

Even though it's more than a year old and the thread is closed, I decided to try the exercises anyway. Here is my answer to the first challenge:

```
## a program for printing the lyrics to "99 Bottles of Beer"
## using a simple xrange loop
for beer_bottles in xrange (99, 2, -1):
    print str(beer_bottles) + " bottles of beer on the wall,"
    print str(beer_bottles) + " bottles of beer,"
    print "Take one down, pass it around,"
    print str(beer_bottles-1) + " bottles of beer on the wall"
    print
## to make the grammar correct, the last 3 verses are printed manually
print "2 bottles of beer on the wall,"
print "2 bottles of beer,"
print "Take one down, pass it around,"
print "1 bottle of beer on the wall"
print
print "1 bottle of beer on the wall,"
print "1 bottle of beer,"
print "Take one down, pass it around,"
print "No more bottles of beer on the wall"
print
print "No more bottles of beer on the wall,"
print "No more bottles of beer,"
print "Go to the store, buy some more,"
print "99 bottles of beer on the wall"

```

I figure I could put some if statements in there to get the other verses into the main loop. I'll work on it a little bit more and post the new code later.

---

### Post by unutbu on 2009-10-18
LOL, well if you wish to go that route, you might as well use a multiline string:
[PHP]
print """2 bottles of beer on the wall,
2 bottles of beer,
Take one down, pass it around,
1 bottle of beer on the wall

1 bottle of beer on the wall,
1 bottle of beer,
Take one down, pass it around,
No more bottles of beer on the wall

No more bottles of beer on the wall,
No more bottles of beer,
Go to the store, buy some more,
99 bottles of beer on the wall"""
[/PHP]
:)

---

### Post by Can+~ on 2009-10-18
And you can use format strings

[PHP]print """print %(beer)d bottles of beer on the wall,
%(beer)d bottles of beer,
Take one down, pass it around,
%(beer_after)d bottles of beer on the wall" % {"beer":beer_bottles, "beer_after":beer_bottles-1}[/PHP]

---

### Post by thunderdan on 2009-10-18
> **unutbu said:**
> LOL, well if you wish to go that route, you might as well use a multiline string:
[PHP]
print """2 bottles of beer on the wall,
2 bottles of beer,
Take one down, pass it around,
1 bottle of beer on the wall

1 bottle of beer on the wall,
1 bottle of beer,
Take one down, pass it around,
No more bottles of beer on the wall

No more bottles of beer on the wall,
No more bottles of beer,
Go to the store, buy some more,
99 bottles of beer on the wall"""
[/PHP]
:)

Interesting. Now I know. This forum is awesome. I always learn more than I expect every time I come here. :)

---

### Post by thunderdan on 2009-10-19
OK, I changed my "99 Bottles of Beer" program to include some if statements, so only the last verse is printed manually now. Here is the code:

```
## a program for printing the lyrics to "99 Bottles of Beer"
## using a simple xrange loop
for beer_bottles in xrange (99, 0, -1):
    if beer_bottles == 1:
        print str(beer_bottles) + " bottle of beer on the wall,"
    else:
        print str(beer_bottles) + " bottles of beer on the wall,"
    if beer_bottles == 1:
        print str(beer_bottles) + " bottle of beer,"
    else:
        print str(beer_bottles) + " bottles of beer,"
    print "Take one down, pass it around,"
    if beer_bottles == 2:
        print str(beer_bottles-1) + " bottle of beer on the wall!"
    elif beer_bottles == 1:
        print "No more bottles of beer on the wall!"
    else:
        print str(beer_bottles-1) + " bottles of beer on the wall!"
    print
## the last verse is different, so it is printed manually
print """No more bottles of beer on the wall,
No more bottles of beer,
Go to the store, buy some more,
99 bottles of beer on the wall!"""
```

---

### Post by thunderdan on 2009-10-19
OK, back to the original counting program. I figured out how to time it and ran three tests, with some interesting results. Here is the code:

```
import time
timea = time.time()
for x in xrange (1, 1000001):
    print x
timeb = time.time()
for x in range (1, 1000001):
    print x
timed = time.time()
timec = timeb - timea
timee = timed - timeb
print "start time for xrange: " + str(timea)
print "finish time for xrange: " + str(timeb)
print "time spent counting for xrange: " + str(timec)
print "start time for range: " + str(timeb)
print "finish time for range: " + str(timed)
print "time spent counting for range: " + str(timee)
if timee < timec:
    print "range was faster by " + str(timec - timee) + " seconds."
if timec < timee:
    print "xrange was faster by " + str(timee - timec) + " seconds."
if timee == timec:
    print "both xrange and range took the same amount of time."
```


And here are the results:
First run:
start time for xrange: 1255977357.3
finish time for xrange: 1255977382.77
time spent counting for xrange: 25.4743750095
start time for range: 1255977382.77
finish time for range: 1255977408.85
time spent counting for range: 26.079105854
xrange was faster by 0.604730844498 seconds.

Second run:
start time for xrange: 1255977471.88
finish time for xrange: 1255977497.17
time spent counting for xrange: 25.290241003
start time for range: 1255977497.17
finish time for range: 1255977523.41
time spent counting for range: 26.2443261147
xrange was faster by 0.954085111618 seconds.

Third run:
start time for xrange: 1255977579.69
finish time for xrange: 1255977606.15
time spent counting for xrange: 26.4612441063
start time for range: 1255977606.15
finish time for range: 1255977631.83
time spent counting for range: 25.6800680161
range was faster by 0.78117609024 seconds.

On the third run, range was faster than xrange. My hypothesis is that while the program was running, there were other processes also running that affected performance. But nonetheless, this was a very interesting and exciting experiment. I hope you liked it. :)

---

### Post by thunderdan on 2009-10-19
I ran the program on my Mac at work, and here are the results:

start time for xrange: 1255992115.95
finish time for xrange: 1255992146.58
time spent counting for xrange: 30.6299138069
start time for range: 1255992146.58
finish time for range: 1255992177.12
time spent counting for range: 30.5452132225
range was faster by 0.0847005844116 seconds.

I think I will rewrite the program to do each type of loop 100 times, and print out the average time taken for each type of loop.

---

### Post by thunderdan on 2009-10-20
OK! I wrote my program to average the times for the xrange vs. range loops. Here is the code:

```
###################
# averagetimecount.py
# a program to test the average speed of xrange loops vs. range loops
# by Daniel Veazey
# 20 Oct 2009
# version 1.0
###################

import time
add_time_xrange = 0
for xrange_run in xrange(100):
    time_a = time.time()
    for x in xrange (1000000):
        print x
    time_b = time.time()
    add_time_xrange = add_time_xrange + (time_b - time_a)
average_time_xrange = add_time_xrange / 100
add_time_range = 0
for range_run in xrange(100):
    time_a = time.time()
    for x in range (1000000):
        print x
    time_b = time.time()
    add_time_range = add_time_range + (time_b - time_a)
average_time_range = add_time_range / 100
print "Average time for xrange: " + str(average_time_xrange)
print "Average time for range:  " + str(average_time_range)
if average_time_xrange < average_time_range:
    print "On average, xrange was faster by " + str(average_time_range - average_time_xrange) + " seconds."
if average_time_range < average_time_xrange:
    print "On average, range was faster by " + str(average_time_xrange - average_time_range) + " seconds."
if average_time_range = average_time_xrange:
    print "Xrange and range had equal average times."
```


And here are the results:

```
Average time for xrange: 25.7742125916
Average time for range:  25.7971578288
On average, xrange was faster by 0.0229452371597 seconds.
```

Now I need to add this as a project on sourceforge.net. Just kidding. I wonder what I should learn to do next ...

---

