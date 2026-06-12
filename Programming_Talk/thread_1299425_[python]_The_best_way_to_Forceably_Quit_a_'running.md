---
title: "[python] The best way to Forceably Quit a 'running' function"
date: 2009-10-23
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-23
Hey,

My current method for exiting a program after ***X *****seconds **is like this:
[php]
def _exit(): global _cont; _cont = False
def myFunction():
    x = 120 #Exit after 2 minutes
    t = threading.Timer(x, _exit)
    t.daemon = True
    t.start()
    
    _cont = True
    while _cont:
        
        '''
            Run the task multipule times until the timer is up
        '''
        
#Main Body Before
myFunction()
#Main Body After
[/php]

This has a bit of complications and can be quite messy at times. Especially when i want to check if the function has ended.

My preferred method (using pseudo code) would be like this.

[LIST]
[*]Start **myFunction()** in a separate thread
[*]Attach a method **.endAfter(X)** where X is the number of seconds we want the function to fun.
[LIST]
[*]Would pause the main script as-well.
[/LIST]
[*]After the ***X*** seconds are up the function (or thread) will be forcefully terminated and the main body of the script will continue to run.
[/LIST]
Thanks
~Cody Woolaver

---

### Post by dwhitney67 on 2009-10-23
Great question/post!

In C/C++, one could cancel the thread, using pthread_cancel().  Surely Python has written a wrapper around this feature.  But in lieu of that... why not just tell the daemon/thread that you are running how much time it has to do its job?  I know there are better ways (ie using signals, semaphores, mutexes, etc.).

---

### Post by Pyro.699 on 2009-10-23
I'm not sure how to tell a thread its maximum aloud time to run.

---

### Post by dwhitney67 on 2009-10-23
> **Pyro.699 said:**
> I'm not sure how to tell a thread its maximum aloud time to run.

Allowed, not aloud.

The "thread" should be an object... that is a class in which you can provide initial values via its constructor.  One value you can give it is the TTL (Time To Live).  Once the thread object is constructed, then you "run" it.  It will self-terminate if its TTL has expired.

---

### Post by Pyro.699 on 2009-10-23
Im not exactly sure what your saying. Well i do, but not being able to apply it to python code. What lines of code do i have to include in order for the TTL to close the thread after the time is up.

---

### Post by dwhitney67 on 2009-10-23
> **Pyro.699 said:**
> Im not exactly sure what your saying. Well i do, but not being able to apply it to python code. What lines of code do i have to include in order for the TTL to close the thread after the time is up.

Maybe you are not aware of this, but Python is not my strong suit.

Nevertheless, a Python app (or thread) should be able to capture the current system time when it is started, and then, while it is managing whatever task it is assigned, it can obtain the "newer" system time.  If the delta between the original system time and the new system time are greater than the TTL, then the thread will exit.

Another approach is for the main-thread (ie the parent of the other thread that is started) to do something similar as described above, and when appropriate, inform the thread to stop.

---

### Post by mr_steve on 2009-10-23
I've used this technique before. Basically, you want to store the current system time in a variable when your function starts running. On each loop through the function, check if the current time minus the original time is greater than the amount of time you'd like the function to run for. If it is, exit the function. This way you can also do whatever clean-up might be required before returning from the function.

---

### Post by CptPicard on 2009-10-24
Hmmh... it is annoying that Python does not seem to have the Java-style thread-interrupt mechanism that would break the thread out of a wait state on that signal so it could then clean up and quit on its own.

Quite a design problem, that. :(

---

### Post by Pyro.699 on 2009-10-24
Does anyone have an operation to exit a thread that's better than mine? Ive been looking through the ***threading*** documentation and it doesn't appear to have a "quit" method.

Thanks
~Cody

---

### Post by mr_steve on 2009-10-24
As far as I know, the only way to terminate a running thread is by letting the thread end itself. You could use something like a semaphore, or even just a global variable, and have your thread check to see if it's set, and return if so.
Obviously if your thread is making any blocking calls the thread won't exit until the blocking call returns, but that's an issue you'll always run in to with blocking I/O

---

### Post by Zugzwang on 2009-10-24
> **dwhitney67 said:**
> Great question/post!

In C/C++, one could cancel the thread, using pthread_cancel().  Surely Python has written a wrapper around this feature.  But in lieu of that... why not just tell the daemon/thread that you are running how much time it has to do its job?  I know there are better ways (ie using signals, semaphores, mutexes, etc.).

Interesting. I've googled for using phthread_cancel() in conjunction with C++ but didn't find an answer to whether the destructors of objects created by the thread but not yet destructed will be called. Do you know if this is the case? My intuition says no (as the amount of stack-inspection to be done to do so is non-trivial and also depends on the instruction pointer of the task killed). If my intuition is correct, killing the thread would result in significant memory leaking (as the classes may have allocated other objects which are then missed).

I'm asking because I recently had a similar problem which I could only solve by forking (so when a timeout occurs, the process can be killed), which is certainly not a very nice solution.

---

### Post by Pyro.699 on 2009-10-24
What if we were to do something like this:


[LIST]
[*]Create a **runFunction(threading.Thread)** class
[*]Assign the function that we want to run into a variable
[*]Under the **run** method we would run & return the function
[*]Create a **kill** method; which will **del self** or something
[/LIST]
Not too sure if that will work.

Thanks
~Cody

---

### Post by tom66 on 2009-10-24
**del self** does not work.

All it does is remove the object from the local namespace (i.e. inside the function/method).

For example:

```

thomas@orion:~$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> class TestClass:
...     def __init__(self):
...         self.a = 488433
...     
...     def my_kill(self):
...         del self
...     
...     def kill_and_try_self(self):
...         del self
...         self.a = 84832 # UnboundLocalError subclass of NameError
... 
>>> test = TestClass()
>>> print test
<__main__.TestClass instance at 0x9f95eec>
>>> test.my_kill()
>>> print test
<__main__.TestClass instance at 0x9f95eec>
>>> test.kill_and_try_self()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 10, in kill_and_try_self
UnboundLocalError: local variable 'self' referenced before assignment

```

Instead:

```

thomas@orion:~$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> class TestClass: 
...     def __del__(self):
...         # cleanup, etc. stuff here
...         print "i've been deleted!"
... 
>>> test = TestClass()
>>> print test
<__main__.TestClass instance at 0x9527eec>
>>> del test
i've been deleted!
>>> print test
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'test' is not defined

```

---

### Post by Pyro.699 on 2009-10-24
I came up with this:

[php]
import threading, time

class runFunc(threading.Thread):
    def __init__(self, func):
        threading.Thread.__init__(self)
        self.func = func
        self.daemon = True
        
    def run(self):
        return self.func()
        
    def __del__(self): pass
    
def myFunc():
    while 1:
        print 1
        time.sleep(1)
        
t = runFunc(myFunc)
t.start()
time.sleep(10)
del t
[/php]
(we really need a python tag xP maybe even a C, C# and C++ too)

The only problem is that the message ***Exception in thread Thread-1 (most likely raised during interpreter shutdown):*** shows up after it gets deleted. Is there anyway to remove that?

Thanks
~Cody

---

### Post by tom66 on 2009-10-24
The exception you report seems to indicate that your thread is still running, but it is not outputting something. 

I recommend, if possible, breaking work into 'chunks' (preferably about 10 ms in processing time), and at the end of processing each 'chunk' check for a flag to see if the thread should quit. 

However, the lack of a quit method in the threading module is a serious deficiency, and I can't see any reason not to include it. Perhaps you should file a bug report in Python.

---

### Post by tom66 on 2009-10-24
Double post, sorry, please remove.

---

### Post by kavon89 on 2009-10-24
A volatile boolean variable, break, and return should be able to substitute the missing functionality. If your function in another thread is taking a long time in a loop, have it check a boolean constantly and when the other thread feels it's necessecary to terminate, just change the value, causing a break and a return.

(No experience in Python though)

---

### Post by fiddler616 on 2009-10-25
Maybe I'm being clumsy and heavy-handed, but what's the matter with:

[PHP]
import time as t
def myFunction():
    start_time = t.time()
    while t.time - start_time <= 120: #I'm pretty sure t.time() is seconds, not milliseconds.
        doHappyThings()[/PHP]

---

### Post by Can+~ on 2009-10-25
[PHP]#!/usr/bin/env python

import threading, time

class runFunc(threading.Thread):
	def __init__(self, func):
		threading.Thread.__init__(self)
		self.func = func
		self.daemon = True
		self.running = False
		
	def run(self):
		self.running = True
		return self.func(self)
	
	def stop(self):
		print "Stopping thread"
		self.running = False
	
	def __del__(self): pass
	
def myFunc(self):
	while self.running:
		print "Process running!"
		time.sleep(1)
		
mythread = runFunc(myFunc)
mythread.start()

time.sleep(10)

mythread.stop()[/PHP]

I just came up with this. Haven't tried it. (Apparently, it works)

However, [in the doc]("http://docs.python.org/3.1/library/threading.html#threading.stack_size"), I read the following:

> The design of this module is loosely based on Java’s threading model. However, where Java makes locks and condition variables basic behavior of every object, they are separate objects in Python. Python’s Thread class supports a subset of the behavior of Java’s Thread class; currently, **there are no priorities, no thread groups, and threads cannot be destroyed, stopped, suspended, resumed, or interrupted.** The static methods of Java’s Thread class, when implemented, are mapped to module-level functions.

So we'll have to wait() :(.

Oh, also, in [Python 3.x, the "with" statement has new influence on threading]("http://docs.python.org/3.1/library/threading.html#using-locks-conditions-and-semaphores-in-the-with-statement"), now you can block/unblock, sig/stop a semaphore, etc.

This is pretty cool, since I always wondered why they didn't add something more "pretty" to handle that.

---

### Post by Pyro.699 on 2010-01-04
Hey guys,

I've STILL been looking for a good way to force-ably quit a Thread and i found it using my good friend google.

Take a look at this post: [http://www.daniweb.com/forums/thread47208.html](http://www.daniweb.com/forums/thread47208.html)

[php]
import sys, trace, threading

class Thread(threading.Thread):
    """A subclass of threading.Thread, with a kill() method."""
    def __init__(self, *args, **keywords):
        threading.Thread.__init__(self, *args, **keywords)
        self.killed = False
    
    def start(self):
        """Start the thread."""
        self.__run_backup = self.run
        self.run = self.__run # Force the Thread to install our trace.
        threading.Thread.start(self)
        
    def __run(self):
        """Hacked run function, which installs the trace."""
        sys.settrace(self.globaltrace)
        self.__run_backup()
        self.run = self.__run_backup
    
    def globaltrace(self, frame, why, arg):
        if why == 'call':
            return self.localtrace
        else:
            return None
    
    def localtrace(self, frame, why, arg):
        if self.killed:
            if why == 'line':
                raise SystemExit()
            return self.localtrace
    
    def kill(self):
        self.killed = True
[/php]I've read up on it a bit and it seems like it has abundant qualities but it does work perfectly for the use i need it for ^^ just thought id share it :D

~Cody

---

