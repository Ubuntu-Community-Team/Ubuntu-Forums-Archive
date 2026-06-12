---
title: "python list problem, is this an acceptable solution?"
date: 2007-01-30
forum: Programming Talk
---

### Post by oldmanstan on 2007-01-30
i want to check if a particular element of a list in in the list's range or not.  in php i would use the isset() function but i don't know that an equivalent function exists in python (looked through the docs at python.org, couldn't find one but i mighta missed it)

anyway, this way of doing it seems to work but i want to know if this is "good form" and if there are any potential issues i'm not seeing:
```

alist = [1,2,3,4]
try:
    print alist[4]
except:
    print "sorry, out of range"

#should print "sorry, out of range" since there is no element 4

```
is this the best way to do what i'm trying to do?  i mean, it works but it feels sort of sloppy since i'm basically intentionally causing an error just to check if the list item exists.  i dunno.  any thoughts?

thanks

---

### Post by ssam on 2007-01-30
```
alist = [1,2,3,4]
try:
    print alist[4]
except IndexError:
    print "sorry, out of range"

```

would be an improvement. this will only catch out of range errors. otherwise the exception would catch things like spelling print wrong or, many other errors that could occur

---

### Post by cwaldbieser on 2007-01-30
> **oldmanstan said:**
> i want to check if a particular element of a list in in the list's range or not.  in php i would use the isset() function but i don't know that an equivalent function exists in python (looked through the docs at python.org, couldn't find one but i mighta missed it)

anyway, this way of doing it seems to work but i want to know if this is "good form" and if there are any potential issues i'm not seeing:
```

alist = [1,2,3,4]
try:
    print alist[4]
except:
    print "sorry, out of range"

#should print "sorry, out of range" since there is no element 4

```
is this the best way to do what i'm trying to do?  i mean, it works but it feels sort of sloppy since i'm basically intentionally causing an error just to check if the list item exists.  i dunno.  any thoughts?

thanks


If you want to see if an element is a member of a set, you should use a set rather than a list.
```

aset = set([1,2,3,4])
if 4 in aset:
     print "4 is in the set."
else:
     print "4 is not in the set."

```
If you already have the data as a list, you can turn it into a set with "aset = set(alist)".
Sets are in python 2.4.  I think you may have been able to import them python 2.3, though I am not sure.

---

### Post by oldmanstan on 2007-01-30
hmm, the example i gave was sort of bad, what i'm actually doing is iterating through a list of lists (simulating a matrix of sorts) and comparing each item with the items next to it.  however, obviously the items on the edges dont have as many neighbors so i want to be sure that the "neighbor" exists before i try to read it...

however, i just realized that my whole method is sort of flawed in python because you can access the last item with -1 so i'm going to have to puzzle out a new way...

thanks for the suggestions!

---

### Post by pmasiar on 2007-01-30
In Python, simplest solution is the best:

```
>>> alist = [1, 2, 3, 4]
>>> isThere = 4 in alist
>>> isThere
True
>>> alist.index(4)
3

```

Or you need something diferent?

---

### Post by ssam on 2007-01-30
"**It is Easier to Ask for Forgiveness than to ask for Permission**"

in python its usually best to try something and handle the exception, that write a test to see if it will work.

have a look at the exception section of [http://en.wikipedia.org/wiki/Python_syntax_and_semantics](http://en.wikipedia.org/wiki/Python_syntax_and_semantics)

also see [http://mail.python.org/pipermail/python-list/2003-May/205182.html](http://mail.python.org/pipermail/python-list/2003-May/205182.html)


also, for manipulating matrices you might want to look at [http://www.scipy.org/](http://www.scipy.org/)

---

### Post by jblebrun on 2007-01-30
> **oldmanstan said:**
> hmm, the example i gave was sort of bad, what i'm actually doing is iterating through a list of lists (simulating a matrix of sorts) and comparing each item with the items next to it.  however, obviously the items on the edges dont have as many neighbors so i want to be sure that the "neighbor" exists before i try to read it...

however, i just realized that my whole method is sort of flawed in python because you can access the last item with -1 so i'm going to have to puzzle out a new way...

thanks for the suggestions!

By the way, Python has very good matrix support via the NumPy library (available in synaptic). Of course, if the goal of the puzzle is to make you play with matrix implementations, you should keep along the route you're going.

Excellent news! You're on your way to writing pythonic python, instead of writing C/C++/Java in python! Soon you'll come to love it. Join us. *Offers kool-aid*. 

If you have some free time, scan through examples on the Python cookbook (just google it). There are surprising tricks and secrets you can learn by looking at examples that you thought you had no interest in!

---

### Post by oldmanstan on 2007-01-30
i'll check into numpy and scipy, thanks guys.  so far i'm lovin python.  it's forgiving but from what i've read can be very powerful in the right hands.  thanks!

---

### Post by ghostdog74 on 2007-02-01
> **oldmanstan said:**
> hmm, the example i gave was sort of bad, what i'm actually doing is iterating through a list of lists (simulating a matrix of sorts) and comparing each item with the items next to it.  however, obviously the items on the edges dont have as many neighbors so i want to be sure that the "neighbor" exists before i try to read it...

you could also do a minus one element when you do the such kind of iteration.

---

### Post by deuce868 on 2007-02-01
Kinda related so I fgured I'd post. I also have been working on PHP->Python transition and really missed isset(). 

What I did find is that for objects you can test to see if it contains something like so:
someobj.__dict__.get('monitor_frame', None) == None:

So this would check to see if there was a variable monitor_frame in the someobj. 

Kinda like saying isset(someobj->monitor_frame) in php

---

