---
title: "Finding negative floats in Python"
date: 2012-04-30
forum: Programming Talk
---

### Post by duke.tim on 2012-04-30
Any help would be appreciated can't seem to figure this out :/

I am trying to create a function that compares two values in python. If the first value is positive and the second value is negative (thus a crossing past zero) increase the variable zeroCrossing by +1.

and vice versa. The code seems to work on integers but not floats

```
#____________________________________
def zeroCross(numList):

    zeroCrossing = 0
    v1Position = 0
    v2Position = 1
    v1 = float(numList[v1Position])
    v2 = float(numList[v2Position])

    while True:
        if v2Position == (len(numList) - 1):    #Checks for end of list
            print zeroCrossing
            return zeroCrossing
        if v1 < 0.00000000000001:             #if the first value is negative
            #if v2 < 0:
            #    print ""                             #not a zero crossing
            if v2 > 0.00000000000001:
                zeroCrossing = zeroCrossing + 1
        elif v1 > 0.00000000000001:        #if the first value is positive
            #if v2 > 0:
            #    print ""
            if v2 < 0.00000000000001:
                zeroCrossing = zeroCrossing + 1

        v1Position = v1Position + 1
        v2Position = v2Position + 1
```

An excerpt of the list it receives input is as follows

> -2.9296875e-03
 -1.4648438e-03
 -4.8828125e-04
  4.8828125e-04
  9.7656250e-04
  0.0000000e+00
  1.9531250e-03
  4.3945312e-03
  6.3476562e-03
  7.3242188e-03
  7.3242188e-03
  8.7890625e-03

*It doesn't exactly check for negatives but anything greater than or less than 0.00000000000001.

---

### Post by 11jmb on 2012-04-30
Are you familiar with for loops? iterating over a fixed-length list is generally going to be a job for a for loop.

As for your problem, are you positive the floats are being read in correctly from the file? Try printing out a portion of the list after it has been read to make sure, or hard-coding an array of floats to pass in and test your function. 

Also, why are you using 0.000000000000000001 instead of 0.0?

There are ways that you can detect a zero crossing in a fraction of the lines of code, but your logic looks sound to me, so I'm guessing that the values you are passing in are not what you are expecting.

---

### Post by LemursDontExist on 2012-04-30
You're not updating v1 or v2 inside the loop, so that's probably the problem.  

As 11jmb noted, a for loop is more appropriate here.  You can combine two lists to get a list of tuples with zip().

Another useful thing to note is that the product of two numbers of the same sign is always positive, and the product of different signs is always negative.

Here's one way to do what you want.

```

def zeroCross(numlist):
    zeroCrossing = 0
    for (v1, v2) in zip(numlist[:-1], numlist[1:]):
        if v1*v2 < 0: # different signs
            zeroCrossing += 1
    return zeroCrossing

```

EDIT: It's worth noting that neither this algorithm nor yours will detect a zero crossing in a list like [-1.0, 0.0, 1.0], so if there could be zeroes in numlist you'll need to add some code to handle that case.  

I didn't handle that case so as to keep the code simple, but if you want to address that case, I'd just remove the 0's before looping:

```

new_numlist = [x for x in numlist if x != 0.0]

``` 

Then you can iterate over new_numlist instead.

EDIT AGAIN: Here's a cuter way to do it
```

def zeroCross(numlist):
    newlist=[x for x in numlist if x != 0.0]
    return len([x for (x, y) in zip(newlist[:-1], newlist[1:]) if x*y < 0.0])

```

---

### Post by duke.tim on 2012-05-01
Thanks for help!

I decided to use  0.000000000000000001 instead of zero since the results seemed to return incorrectly with zero. This is mainly to insure [s]fractional values are not counted as negatives[/s], with the way I wrote the logic.

Originally I was using a for loop, but I am generally more comfortable using while loops.


I'll have to test out a hard coded array.

[s]v1 and v2 update i've tested that using print and then running the code.[/s]
* v1Position and v2Position

going from -1 to 0 to 1 is not a problem, I think.

Again, thanks for the help! will edit this post after testing the code further.

---

### Post by LemursDontExist on 2012-05-01
> **duke.tim said:**
> v1 and v2 update i've tested that using print and then running the code.
In the code above, the only place you change v1 or v2 is outside the while loop, and that only happens once per function call.  Changing v1Position doesn't automatically update v1.  Add 'print v1' to your loop, and I think you'll see that it doesn't change.

> **duke.tim said:**
> going from -1 to 0 to 1 is not a problem, I think.

You're right, [1.0, 0.000000000000000001, -1.0] is the problem case.  I forgot that you weren't using 0.0.

Incidentally, [1.0, 0.0, 1.0] is also a problem.  Your code would return 2 for that case.  Using 0.000000000000000001 just amounts to looking for 0.000000000000000001-crossings instead of zero crossings.  I'd note that in your sample data, your current algorithm would count

> 9.7656250e-04
0.0000000e+00
1.9531250e-03

as two crossings, so this is a real problem.  Just use 0.0 instead.  Whatever problem you thought 0.0 was causing, I can say with some confidence that it was being caused by something else.

---

### Post by duke.tim on 2012-05-01
LemursDontExist you are completely right, I ended up adding an assignment statement at the end after the v1,v2Position update

```
v1 = float(numList[v1Position])
v2 = float(numList[v2Position])
```

The code you posted is also much simpler than what I came up with, so i'll probably end up using that. Thanks :)

---

