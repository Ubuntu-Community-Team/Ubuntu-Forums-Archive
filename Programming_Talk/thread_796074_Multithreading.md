---
title: "Multithreading"
date: 2008-05-16
forum: Programming Talk
---

### Post by nebu on 2008-05-16
i dont realy know much about multithreading.... just learning now.....

i wrote this code in python....

```
from math import floor
import threading


class euler(threading.Thread):
    def __init__(self,low,high):
        threading.Thread.__init__(self)
        self.low = low
        self.high = high
    def run(self):
        #Statements


thread1 = euler(0,5000)
thread2 = euler(5001,10000)
thread2.start()
thread1.start()

thread1.join()
thread2.join()

print "Program Execution Over"


```from what i see.... the threads are not running simultaneously.....

i have a intel dual core processor.... so shouldnt the thing theoretically be able to run both threads at the same time???

how can i make it run both threads at the same time

---

### Post by Verminox on 2008-05-16
If the threads are doing trivial jobs like say printing 100 lines each, then you might not even notice the difference because the first thread will complete the job before the second thread can even start. 

Is your run() method large enough for it to take a lot of time?

PS: I don't know Python so if there are coding/logic errors I wouldn't know.

---

### Post by nebu on 2008-05-16
no... the run method is not very long....

the first thread is not ending before the 2nd begins....

the first thread is looping from 1->50000 and the second is looping from 50000->1000000

and they are printing their current state(value of loop variable)....

the output comes out like ->
```

Thread 1 - 1
Thread 1 - 2
Thread 1 - 3
Thread 1 - 4
^
^
^
^
^
^
^
^
^
^
^
^
^
^
^
^
^
^
^
^
Thread 2 - 1
Thread 2 - 2
Thread 2 - 3
Thread 2 - 4
 ^
^
^
^
^
^
^
^
^
^
^
^
^
^

Thread 1 - 1000
Thread 1 - 1001
Thread 1 - 1002
Thread 1 - 1003
 ^
^
^
^
^
^
^
^
^
^
^
^
^
and so on


```

so the first thread is sleeping when the second is running!!??!!

---

### Post by Verminox on 2008-05-16
Oh, well, your output is showing that the threads are indeed running in parallel. 

You may expect Thread 1 and Thread 2 to print one line at a time but that's not how multithreading works. Multithreading will just make sure that if Thread 1 has an ever so small delay before the executing the next statement then instead of being idle for that small interval, the next Thread in queue will be given the program flow. If Thread 2 can rapidly process a large batch of instructions (such as printing 1000 lines in your case) then it will do so at one go. If you want each of the threads to process one line at a time then you have to implement logic yourself. In Java, this can be done using the wait() and notify() methods, but I don't know about Python.

Try doing something like prompting for user input after printing 300 in Thread 1. Although generally the program would have held on until you enter something, in this case Thread 2 will take its turning in printing the numbers. Once you give your input and press enter Thread 1 will be ready again and it will print its share of numbers whenever it gets the chance to.

---

### Post by rye_ on 2008-05-16
I'm impressed if python can use multiple cores, when multi-threading.  ruby can create several threads (separate processes) but I was under the impression that only one core could be used, one thread stopping for the other.  I also thought it was complicated enough that it may be better avioded.

Are you sure python can take advantage of several cores?

ryan

---

### Post by skeeterbug on 2008-05-16
> **rye_ said:**
> I'm impressed if python can use multiple cores, when multi-threading.  ruby can create several threads (separate processes) but I was under the impression that only one core could be used, one thread stopping for the other.  I also thought it was complicated enough that it may be better avioded.

Are you sure python can take advantage of several cores?

ryan

No, it only uses one.


[http://smoothspan.wordpress.com/2007/09/14/guido-is-right-to-leave-the-gil-in-python-not-for-multicore-but-for-utility-computing/](http://smoothspan.wordpress.com/2007/09/14/guido-is-right-to-leave-the-gil-in-python-not-for-multicore-but-for-utility-computing/)

---

### Post by dwhitney67 on 2008-05-16
[post deleted]

---

