---
title: "Python; multiproccessing slower?"
date: 2010-04-15
forum: Programming Talk
---

### Post by Psycho.mario on 2010-04-15
Hi, i have this program:
```
def threaded():
    from multiprocessing import Process
    def square(x):
        int(x)
        print x*x
        return
    i=0
    while i < 25:
        Process(group=None,target=square,name=None, args=(i,), kwargs={}).run()
        i += 1
        Process(group=None,target=square,name=None, args=(i,), kwargs={}).run()
        i += 1
        Process(group=None,target=square,name=None, args=(i,), kwargs={}).run()
        i += 1
  
def normal():
    for i in range(1,25):
        print i*i
def time_it(f):
    start = time.clock()
    f()
    return (time.clock() - start)*1000

threaded = time_it(threaded)
normal = time_it(normal)

print "Threaded time: ", threaded
print "Normal time:", normal
```

it calculates the squares from 1-25, the first function is threading the multiplication, the second isnt. the third function times the runtime, and tells you how long they took. However, when i run this, the numbers are always different, and also, the one without multiprocessing goes slower. Have i done something really stupid? Could someone enlighten me as to why it's slower?

Thanks

---

### Post by azagaros on 2010-04-15
from what I see in the program and from programming knowledge in general...

Make the two thread process information exactly the same.  The way normal thread runs is different from the way treaded one runs.  Especially the way function calls are made and are broke up.

Generally the spawning of a thread has more resources associated with it and a little more overhead, but it should not be really noticeable.

To me you are comparing an apple to an orange in your code even though you have a lot of the same statements.  The flow is different for each block.  This will account for the time difference in subtle ways.

---

### Post by MadCow108 on 2010-04-15
the overhead of creating a thread is a lot higher compared to calculating 25 squares :)
For many low workload threads one often reuses created threads in a thread pool to reduce that overhead.

and as already mentioned the square calculation is so fast that the different control flow will also have a significant impact

let the threads do a lot more work and you might see a difference

---

### Post by Psycho.mario on 2010-04-15
I suspected that might be the problem...
This was just testing, the actual program will be hashing some text then comparing it to another hash
 How would i go about using a thread pool?

Thanks

---

### Post by ssam on 2010-04-15
also you have an import statement inside the function.
[http://wiki.python.org/moin/PythonSpeed/PerformanceTips#ImportStatementOverhead](http://wiki.python.org/moin/PythonSpeed/PerformanceTips#ImportStatementOverhead)

---

### Post by Cracauer on 2010-04-15
The Python interpreter itself is always inside one lock. Python code does not execute on multiple processors. Trying to split up your Python code workload onto threads will do nothing to performance except adding locking and scheduling overhead - and in your case a lot since your between-locks workload is so small.

In Python threads are exclusively for C code. Namely it prevents you from blocking on I/O. I/O will call into C functions that do the actual system calls for you, and they release the interpreter lock for you while the system call is in progress. 

So you get the multithreaded effect when it comes to (not) blocking on external resources. And you can run C code inside your interpreter process in parallel with the one Python thread if you know what you are doing and release that lock (hopefully in that order :)) But you cannot use Python threads to use more than 1 CPU on actual non-C Python code.

This is, BTW, one of the major reason why I don't use it. The year is 2010 and since about 2003 we know that more CPU resources come from more cores/CPUs, not faster cores. Languages that continue to ignore that are not to my liking.

---

