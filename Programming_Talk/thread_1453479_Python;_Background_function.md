---
title: "Python; Background function"
date: 2010-04-13
forum: Programming Talk
---

### Post by Psycho.mario on 2010-04-13
Hi.
I was wondering if it was possible to background a function, so that i could have multiple instances of the same function running with different paramaters.
for example:
```

def function():
      global funcdone
      funcdone=True
      pass
function(x) #backgrounded
function(y) #backgrounded
while funcdone == False:
      #loop till it's finished
#execute another function instance with different parameters

```Thats only a rough idea, i hope you get the picture. I would have to have some kind of different variables for each execution, but that shouldnt be too hard to achieve. So is it possible to background a function so i can run more than one at once?

Thanks

---

### Post by lavinog on 2010-04-13
I think you want to look at threading.
Haven't done it myself yet, but have been meaning to make something with it.
[http://docs.python.org/library/threading.html](http://docs.python.org/library/threading.html)
[http://docs.python.org/library/thread.html](http://docs.python.org/library/thread.html)

Maybe someone can explain which is better to use: thread or threading.

---

### Post by surfer on 2010-04-13
a simple script is (you should easily be able to customize it to your needs):

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import threading
import random
import time

class Sleep(threading.Thread):

    MAX = 10
    
    def __init__(self, thread_number):
        threading.Thread.__init__(self)
        self.thread_number = thread_number
    def run(self):
	t = random.randint(0,Sleep.MAX)
	print 'thread_number = %2i: sleeping %2isecs' % (self.thread_number, t)
        time.sleep(t)
        print 'thread_number = %2i: finished' % self.thread_number
 
    
 
jobs=[]
for i in xrange(10):
    s = Sleep(i)
    jobs.append(s)
    s.start()
    # print 'The main program continues to run in foreground.'
for job in jobs: # Wait for the background task to finish
    job.join()
print 'Main program waited until background was done.'

```

---

### Post by wmcbrine on 2010-04-13
You can threadify a single function:

```
import thread  # note, "thread" rather than "threading"

def your_func_here():
    pass

thread.start_new_thread(your_func_here, ())
```

---

### Post by croto on 2010-04-13
Although if it's a speed gain what you're looking for, python threads are not the way to go. The culprit is the Global Interpreter Lock, if you want to google it up.
With that in mind, I recommend running different instances of your function in different processes: have your python script take the arguments from the command line, for instance, and a little shell script starting your processes in the background.

Of course, disregard this if you have other kind of application in mind.

---

### Post by azzamite on 2010-04-13
Depending on what your trying to do, multiprocessing could be an option
here yo have a pieces of a code I wrote using it

Calculating perfect numbers is a tiresome task, so this way I have
5 threads running at the same time all the time...

```

# import the lib
from multiprocessing import Pool as Alberca

def esPerfecto(n):
   # tell whether n is a perfect number or not
   print n, "no"

# param: (max) number of threads to allow
alberca = Alberca(5)

# 1st param: function to call
# 2nd param: a list, the 1th element will be given the ith time
#         the function is called, you could use range() instead
alberca.map(esPerfecto, [3,4,5,6,7,8,9,10,11])

```

[http://docs.python.org/library/multiprocessing.html](http://docs.python.org/library/multiprocessing.html)

---

### Post by Psycho.mario on 2010-04-14
The main program idea was a password cracker (NOT FOR ILLEGAL PURPOSES, its just to test my programming skill) so i could run different intances of the same function so it could check, say, 3 passwords at the same time, rather than just one at once. I shall look into what you have given me.

Thanks for all the help

---

### Post by StephenF on 2010-04-14
> **croto said:**
> Although if it's a speed gain what you're looking for, python threads are not the way to go. The culprit is the Global Interpreter Lock, if you want to google it up.
With that in mind, I recommend running different instances of your function in different processes: have your python script take the arguments from the command line, for instance, and a little shell script starting your processes in the background.
A better approach would be to use the multiprocessing module. That way you never need to step outside of Python.

[http://docs.python.org/library/multiprocessing.html](http://docs.python.org/library/multiprocessing.html)

---

### Post by Psycho.mario on 2010-04-15
Thanks for all the help. After looking into the options, i have gone with this:
```

from multiprocessing import Process
def func():
    global x
    x=5
    print "infunc",x
    return
x=1
print "outfuncstart",x
Process(group=None,target=func,name=None, args=(), kwargs={}).run()
print "outfuncend",x
```
all the printing and stuff is me just looking to see if global still works.

Thanks for all the help

---

### Post by StunnerAlpha on 2010-04-16
The threading library is considered to be better than the thread library. But if you want speed, as previously mentioned, use the multiprocessing module. However there is a severe lack of information on this module but this should get you started: [http://heather.cs.ucdavis.edu/~matloff/158/PLN/ParProcBook.pdf](http://heather.cs.ucdavis.edu/~matloff/158/PLN/ParProcBook.pdf)
Go to the bottom of page 66(Section 3.4). Hope this helps.

---

### Post by smartbei on 2010-04-16
Since the goal is to improve the performance of the password-checking program, you may want to think about having each process perform more than one check - say, 1000 or more. This is because spawning a process is a relatively expensive operation (time-wise), and doing so on each check is wasteful.

You could have a list of all the passwords you want checked, and hand each process the starting index and how far to run. Each one will run that far, and return the results.

An interesting challenge is to do this with communication between the processes - creating a master process that hands out tasks to the sub processes and communicates back to the interactive shell for instance.

---

### Post by wmcbrine on 2010-04-16
> **StunnerAlpha said:**
> The threading library is considered to be better than the thread library.Why? I mean, I've certainly noticed that this attitude exists, but I haven't seen a justification for it. Personally I find spawning functions off as threads much more convenient.

---

