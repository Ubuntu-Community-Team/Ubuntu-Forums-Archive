---
title: "Python: Threading!"
date: 2010-06-18
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-06-18
What's Up?

OK, So my first ever Python project is under way, I've hit a problem however in terms of, I need to perform some commands in a loop, But I also need to carry on and performing other tasks, Now apparently this means using threading, But I'm too stupid to figure it out. Could someone show an Example of how to make a new thread and perform a while loop inside of it?

Thanks Bye!

---

### Post by NoBugs! on 2010-06-18
I found this to be a helpful start:
[http://www.saltycrane.com/blog/2008/09/simplistic-python-thread-example/](http://www.saltycrane.com/blog/2008/09/simplistic-python-thread-example/)

---

### Post by patchwork on 2010-06-18
Nobugs link is a good start.  To break this process down a little bit, what I would do is :

1. import threading
2. create a function that contains your loop
3. define the thread (i.e. t = threading.Thread(target=FUNCTION_NAME, args=(ARGUMENTS TO PASS TO FUNCTION)
4. start the thread with t.start()

More info on the threading module:
[http://docs.python.org/library/threading.html](http://docs.python.org/library/threading.html)
[http://www.doughellmann.com/PyMOTW/threading/](http://www.doughellmann.com/PyMOTW/threading/)

---

### Post by soltanis on 2010-06-18
[php]
import threading

final_val = 0

def process_loop(x):
    global final_val
    while condition:
         x += 1
    final_val = x

t = threading.Thread(process_loop, args=(x_val))
t.start()
# do other things in the main thread, or if you want the entire program to wait...
t.join()

print final_val
[/php]

You should take the time to note several things here.

First, in the Python threading paradigm, you're function won't have its return value interpreted in any intelligent way, so results you want to store need to get tucked away in either some global variable or some reference you pass to the thread, or something similar.

Then, you will run into problems such as, well what if at lot of people are accessing the same variable at once, how can I keep them all consistent? The answer to that case is mutexes (locks) which you can read all about in:

[http://docs.python.org/library/threading.html](http://docs.python.org/library/threading.html)

Finally, take special heed that threads in Python suck for doing anything except I/O waiting. What I mean by that is, if your program is something that makes a bunch of sockets and then talks to a bunch of remote peers at once, then chances are you'll spend most of your time waiting for input or output on those sockets and not a lot of time actually doing computations. But if you are doing real computations or manipulations on some variables, then threads will not help your performance; in fact, they will drastically decrease your performance in Python.

The reason this is the case is the awesome idea of the "Global Interpreter Lock" and the fact that Python has no control over its own thread scheduling, combining to give you a surely miserable experience if you are trying to get serious work done on a multiprocessor machine. The only answer to that problem is to do a fork() operation, splitting your program into separate processes (with separate address spaces), a slightly more expensive operation and one which makes sharing data between the processes more difficult, but which will leave the kernel to schedule your threads across multiple cores.

[http://en.wikipedia.org/wiki/Global_Interpreter_Lock](http://en.wikipedia.org/wiki/Global_Interpreter_Lock)

---

### Post by StephenF on 2010-06-19
> **soltanis said:**
> Finally, take special heed that threads in Python suck for doing anything except I/O waiting. What I mean by that is, if your program is something that makes a bunch of sockets and then talks to a bunch of remote peers at once, then chances are you'll spend most of your time waiting for input or output on those sockets and not a lot of time actually doing computations. But if you are doing real computations or manipulations on some variables, then threads will not help your performance; in fact, they will drastically decrease your performance in Python.

The reason this is the case is the awesome idea of the "Global Interpreter Lock" and the fact that Python has no control over its own thread scheduling, combining to give you a surely miserable experience if you are trying to get serious work done on a multiprocessor machine. The only answer to that problem is to do a fork() operation
The idea behind the GIL is that Python is slow enough as it is in single threaded applications. Presumably things will remain the same until CPUs sport 256 cores as standard.

Before using fork directly I suggest taking a look at the multiprocessing module which produces code of a more self-documenting quality to the same end.

---

### Post by Queue29 on 2010-06-19
> **StephenF said:**
> The idea behind the GIL is that Python is slow enough as it is in single threaded applications. Presumably things will remain the same until CPUs sport 256 cores as standard.

Before using fork directly I suggest taking a look at the multiprocessing module which produces code of a more self-documenting quality to the same end.

But before doing that, I would recommend switching to a language that doesn't make you use hacks and workarounds just so you can have true (yet still easy to use) multiprocessing. (Think C#, Java)

---

### Post by Penguin Guy on 2010-06-19
I would suggest that you look into multiprocessing rather than multithreading. Very similar thing, but seems to be held in higher esteem.

---

### Post by soltanis on 2010-06-19
> **Queue29 said:**
> But before doing that, I would recommend switching to a language that doesn't make you use hacks and workarounds just so you can have true (yet still easy to use) multiprocessing. (Think C#, Java)

Like Go.

---

### Post by StephenF on 2010-06-20
> **Queue29 said:**
> But before doing that, I would recommend switching to a language that doesn't make you use hacks and workarounds just so you can have true (yet still easy to use) multiprocessing. (Think C#, Java)
There is probably more benefit in Python from writing performance critical  modules in C. Using multiple processors is just going to slow the machine.

---

