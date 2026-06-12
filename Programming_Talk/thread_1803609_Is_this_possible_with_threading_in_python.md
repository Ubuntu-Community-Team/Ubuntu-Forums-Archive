---
title: "Is this possible with threading in python?"
date: 2011-07-13
forum: Programming Talk
---

### Post by ownaginatious on 2011-07-13
So I have this python program that reads in a bunch of data and then must wait a set amount of time before processing it.

For example, the program will read in data telling it to do things at specific times. The program calculates the time between now and when the next closest 'thing' needs to happen, and then sleeps until then (just like thread.wait() in Java).

So right now I'm assuming that time.sleep(seconds) (I only need second procession) can full-fill that process for me.

Now the other thing I would like to do is be able to 'wake up' the program in the event that there is a change in the data. I wouldn't be counting on the program to watch the data for changes, and I would instead signal it with SIGUSR1 or SIGUSR2.

I figure I can just jump into an interrupt routine, which again reads the data and then goes back into sleeping... but then that would leave my programs old sleeping state on the stack... or so I would assume since I just jumped out of a method I'm supposed to return to.

-----

Anyway, does this seem like a good way to do this? I would think the best way would be to somehow interrupt the sleeping state externally and 'wake up' the method, which would then check again that it is indeed supposed to execute at that instant. I don't really know how to do that though :/.

Sorry if my explanation is hard to follow, here is some python/pseudo code of what I mean.

```

data = readData()

for job in data:
   executionStack.push(job)

executionStack.sortByClosestDateTime()

for job in executionStack:
   time.sleep(job.timeUntilJob())

   if wokenUpByTimeout():
       job.do();
   else
       recall this method because something in the data must have changed...

```

---

### Post by StephenF on 2011-07-14
Yes it's possible and it's possible to do it without threads also.
```

#!/usr/bin/python

import glib

loop = glib.MainLoop()

job_list = [(5, "f1", "Data"), (10, "f2", "More data"), (15, "f3", "Last ", 10)]
completed = 0
job_functions = {}

def job_handler(f):
    def inner(*data):
        global completed
        f(*data)
        completed += 1
        if completed == len(job_list):
            loop.quit()
    job_functions[f.func_name] = inner
    return inner

@job_handler
def f1(data):
    print data

@job_handler
def f2(data):
    data = data.swapcase()
    print data

@job_handler
def f3(*data):
    print data[0] * data[1]

for j in job_list:
    glib.timeout_add_seconds(j[0], job_functions[j[1]], *j[2:])

loop.run()

```
[s]I'm not advocating this coding style for anything other than quick scripts and the use of glib, an external module is unfortunate.[/s]

> 
Now the other thing I would like to do is be able to 'wake up' the program in the event that there is a change in the data. I wouldn't be counting on the program to watch the data for changes, and I would instead signal it with SIGUSR1 or SIGUSR2.
It's possible to use that particular signal though D-Bus is the modern, more nuanced way of inter process communication and will work very naturally with glib. You could even send the data over the DBus and might want to parse it outside the program and D-Bus it in considering how you have (or plan to have) some kind of watch on the data.

On the other hand inotify is good too.

---

### Post by nvteighen on 2011-07-14
> **StephenF said:**
> 
I'm not advocating this coding style for anything other than quick scripts and the use of glib, an external module is unfortunate.

Eh? How can using an external module be unfortunate? Why implement something that already exists for you and works perfectly fine?

---

### Post by psusi on 2011-07-14
What is that @job_handler syntax?

---

### Post by StephenF on 2011-07-14
> **psusi said:**
> What is that @job_handler syntax?
It's [Python function decorator syntax]("http://www.python.org/dev/peps/pep-0318/").

---

