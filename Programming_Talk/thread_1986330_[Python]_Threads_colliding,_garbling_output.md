---
title: "[Python] Threads colliding, garbling output"
date: 2012-05-24
forum: Programming Talk
---

### Post by Erdaron on 2012-05-24
I am working on a Monte Carlo simulation. The simulation uses many runs that are independent of each other, so it seems like multi-threading is appropriate.

I've never used threading before, so this is my first try. For starters, I wrote a simple script just to see if I can get it to work.

I read Python docs for modules threading and Queue. I also looked up a couple examples, but they didn't help me much.

Here is the script I wrote:
```
import threading
import time

runprmque = [(1, 2), (3, 4), (5, 6), (7, 8)]

threadmax = 3 #limit the number of simultaneous threads

threads = [] #list of current threads

def f(x, y): #work function called by the threads
    time.sleep(x+y)
    print x + y
    return None

while len(runprmque) > 0 or len(threads) > 0:
    #runs until all threads finish and no more jobs are left
    while len(threads) < threadmax and len(runprmque) > 0:
        #find available thread slots and fill them with unfinished jobs
        t = threading.Thread(target = f, args = runprmque[0])        
        print 'Job assigned: ' + str(runprmque[0]) + ' to ' + t.name
        t.start()
        del runprmque[0]
        threads.append(t)
        del t
    n = 0
    while n < len(threads):
        #remove threads that have finished
        if threads[n].is_alive():
            n = n + 1
        else:
            print 'Removing thread: '  + threads[n].name
            del threads[n]
```

When the print statement in f() is enabled, it produces orderly output:
```
Job assigned: (1, 2) to Thread-1
Job assigned: (3, 4) to Thread-2
Job assigned: (5, 6) to Thread-3
3
Removing thread: Thread-1
Job assigned: (7, 8) to Thread-4
7
Removing thread: Thread-2
11
Removing thread: Thread-3
15
Removing thread: Thread-4
```

But when it is disabled, the output becomes garbled:
```
Job assigned: (1, 2) to Thread-1
3Job assigned: (3, 4) to Thread-2

7Job assigned: (5, 6) to Thread-3

11Removing thread: Thread-1

Removing thread: Thread-2
Removing thread: Thread-3
Job assigned: (7, 8) to Thread-4
15
Removing thread: Thread-4
```

I am assuming this is because multiple threads are trying to interact with the main thread at the same time, and everything gets confusing. How can I keep the threads from piling on top of each other? In the realistic application, I won't know which job will finish first, so I can't just use .join() to keep things in order.

I am working in Python 2.7.2 64-bit on Windows 7, with a dual-core Intel.

---

### Post by MadCow108 on 2012-05-24
I don't quite understand the issue, if you remove the print, you can't get that output as you only print in one thread.
if you leave it in you may need to put a lock around it and flush stdout
or use sys.stdout.write with a newline, that should be atomic.

if your code is pure python and not IO bound you won't have much fun with multithreading. Python is littered with global locks which will make performance awful.
It may be ok if you use other libraries like numpy or scipy and spend significant amount in their C code in which they release the locks, but if its mostly python it will likely be slower then single threaded.

the recommended way around that is using processes instead via the multiprocessing module.
That modules has plentora of useful functionalities for parallelizing stuff.
Quite often a simple map/reduce approach works well, e.g. your code  could possibly look like that:

```
import multiprocessing

def f(args):
  import time
  time.sleep(x +y)
  return x + y

#get our processes, default number = #cpu
pool = multiprocessing.Pool()
runprmque = [(1, 2), (3, 4), (5, 6), (7, 8)]
results = pool.map(f, runprmque)
for r in results:
  print r
# or async:
results = pool.map_async(f, runprmque)
print "returns immediately!"
for r in results.get():
  print r
# more async
results = [pool.apply_async(f, args=(x,)) for x in runprmque]
results = pool.apply_async(f, runprmque)
for r in results:
  print r.get()

```

---

### Post by Erdaron on 2012-05-24
Thank you for pointing me in this direction! I saw the multiprocessing module, but for some reason decided to start with threading. But this looks just like the thing.

My code is pure Python (although most of internal data storage and computation is done using numpy arrays), and I have zero experience with C - so that tinkering is right out. There is some I/O, but in terms of time, it's almost entirely computation. Just saves the outputs at the end.

I imagine .map() returns results in order of completion, not in the order of submission, so it would be a good practice to attach some meta-data tags so I know what the returned data corresponds to?

Thank you! Reading multiprocessing module docs now :)

---

### Post by MadCow108 on 2012-05-25
map returns the same order as the input, there is also imap_unordered for unordered iteration, this load balances better.

---

### Post by Erdaron on 2012-06-01
I have started playing with the multiprocessing, and it certainly works, but there are a couple of oddities I wanted to ask about:

Every time I call the multiprocessing version of the function, it spawns two pythonw.exe processes. However, these processes do not go away when processing is complete. They continue to sit idle, using some memory but no CPU cycles. They go away if the script is re-run. Deleting the Pool object does not remove these processes. Should I do something to terminate the extra processes? The simulation will make this call hundreds of times - I wouldn't want to have over a thousand idle processes just hanging out.

For a small number of iterations, the single-process version of the function is significantly faster. For a large number of iterations, the multiprocessing becomes faster, approaching an improvement of a factor of two (which is reasonable, it's a dual-core computer). Why does this happen?

I am currently using the simple .map() method to process the que.

> I don't quite understand the issue, if you remove the print, you can't get that output as you only print in one thread.
Apologies - I typed the wrong word. I meant to say that if I comment out the sleep command, then everything gets garbled.

---

### Post by MadCow108 on 2012-06-02
> **Erdaron said:**
> I have started playing with the multiprocessing, and it certainly works, but there are a couple of oddities I wanted to ask about:

Every time I call the multiprocessing version of the function, it spawns two pythonw.exe processes. However, these processes do not go away when processing is complete. They continue to sit idle, using some memory but no CPU cycles. They go away if the script is re-run. Deleting the Pool object does not remove these processes. Should I do something to terminate the extra processes? The simulation will make this call hundreds of times - I wouldn't want to have over a thousand idle processes just hanging out.
normally you create one pool and pass all you commands to this pool, that way you only span processes once

you can explicitly close pools with the .close() method followed by a .join()
if something is broken use .terminate()

regarding the memory usage you must remember processes are spawn by the fork system call.
On linux (and most other operating systems) forks share the address space of the parent process in a copy-on-write manner, so if your parent process uses 50% memory at the time of the fork, the child will also be shown as using 50%, but it are the same 50% until you start modifying it.
e.g.
```
d = numpy.random.random(size=(100,100,5000)) # uses 400mb memory
p = multiprocessing.Pool(100) # -> top displays these 400mb, 100 times :O
p.close() # stop the workers
p.join() # wait for workers to stop
```


> 
For a small number of iterations, the single-process version of the function is significantly faster. For a large number of iterations, the multiprocessing becomes faster, approaching an improvement of a factor of two (which is reasonable, it's a dual-core computer). Why does this happen?

I am currently using the simple .map() method to process the que.


to answer that one must know what you mean by iterations.
do you mean iterations on the pool worker?
in that case its due to the communication overhead. If the pool worker does little work the processing time will be dominated by the data transfer to the pool (.map uses the multiprocessing.Queue for that)

only operations that take longer than the communication overhead are worth parallelizing.
you can reduce the communication overhead by using other methods of sharing data. e.g. multiprocessing offers pipes, queues and shared memory.
you can also make use of the sharing of address space the forking provides:
```
import numpy as np
d = np.random.random(size=(100,100,5000))
import multiprocessing
def f():
    return np.sum(d)
p = multiprocessing.Pool(10)
print p.apply(f)
d[:] = 0
print np.sum(d), p.apply(f) # not equal!

```
this works only because the pool is created after the data is already in memory, the worker has the same data (and the numpy import) mapped to its address space so it can work on it without having to explicitly receive it via a queue.
but any modification made to this copy-on-write data will not be seen by the other worker

---

### Post by Erdaron on 2012-06-04
Thank you, using .close() followed by .join() worked exactly as I had wanted. I at first assumed that using del on the pool object would automatically call something similar to these methods, but it didn't.

The simulation I am writing scans over a set of parameters, and runs the model many times for each set of parameters. I suppose it is easier for me to use the pool object once for each set of parameters instead of once for the whole simulation. Makes it easier to sort the output data. This is kind of lazy programming though, and I should probably fix it. I am still improving and optimizing the code, and this is my first time writing something with a heavy computation load.

---

### Post by MadCow108 on 2012-06-04
creating and killing many processes if fine as long as it does not hurt your performance
process creation on linux is very fast, on other operating systems that may be different.

python3.2 has context managers for pools, along with proper futures:
[http://docs.python.org/dev/library/concurrent.futures.html#processpoolexecutor](http://docs.python.org/dev/library/concurrent.futures.html#processpoolexecutor)

when you get bored of writing .close, .join and appropriate error handling all the time, it should not be hard to make your own context manager for the pools

---

