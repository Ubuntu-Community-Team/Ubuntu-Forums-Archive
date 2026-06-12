---
title: "python non-blocking"
date: 2007-11-08
forum: Programming Talk
---

### Post by bradleyd on 2007-11-08
Hello everyone,

I am having a hard time understanding blocking. I am calling a shell command from subprocess.Popen. The command runs fine but the whole application is being held up because it is waiting for it to finish. Unfortunately this binary does not exit until it is killed. So when the user pushed connect on the ui the app freezes waiting for the command to finish. I would think there is a way to make it run in a non-blocking fashion, but still be able to get pid info from it? 
Thanks for your time,
Brad

---

### Post by LaRoza on 2007-11-08
You can try using threads.

---

### Post by bradleyd on 2007-11-08
I am not that familiar with threads, kinda new to programming. Do you know any examples that would have a shell command?

---

### Post by dgar on 2007-11-08
It's a greate problem to work on, and around, until the light bulb goes off.  It also isn't easy, meaning there isn't one way to do it.

I've tried and sometimes succeeded wrapping the tar command with various interpreted scripting languages.  'tar' is especially tricky, because if it asks to change a tape it doesn't flush it's output buffer or emit a newline, often leaving the user or listening program without any indication that action is requested.

Threads, the subprocess module, the select[ ] system call, flush(), spawning a new terminal for command execution, or just appending '&' to the command passed to Popen* all address various aspects of blocking.

So, BTW, does the -u flag to python itself.

I highly recommend understanding the select[] POSIX call and the subprocess python module.

Oh, and python-twisted, where asynchronous everything was the itch that python-twisted was invented to scratch.

Good luck!

---

### Post by cwaldbieser on 2007-11-09
> **bradleyd said:**
> I am not that familiar with threads, kinda new to programming. Do you know any examples that would have a shell command?

Threads are like functions in your program that run at the same time.  The standard library module, threading, is the easiest weay to work with threads in python.  The general idea is to subclass threading.Thread.

---

### Post by dwblas on 2007-11-09
I would go with threading also, but have you tried running it in the background as dgar also suggested, i.e appending an &.

---

### Post by red_Marvin on 2007-11-09
I think using threads is the recommended way, but imo select() is much easier to use.
```
>>> import select
>>> help(select)
>>> help(select.select)
```

---

### Post by bradleyd on 2007-11-09
I did not try to background it, wanted to try others first. I did get it to work by using ```
os.spawnvp(os.P_NOWAIT, 'binary', ('binary', 'arg'))
```It seems it is deprecated, but it did work. I still believe threading is probably the way to go. I was surprised on the lack of docs for this problem. I thought this would be a common problem in applications, or at least a common problem for novice programmers. 
I still would like to learn how to adapt threading to my code. Thanks for everyones responses.

---

### Post by evymetal on 2007-11-11
I know that threading is supposed to be the better module to use, but I always use thread:

```

import thread

def long_blocked_function(param):
    pass

thread.start_new_thread(long_blocked_function,(param,))


```

- of course if you want to communicate between threads you will need to read up on "locks" - but they are quite easy in python too.

---

### Post by bradleyd on 2007-11-11
Thanks for the info, I was just reading about locks, will give it a try and report back.
Brad

---

### Post by OrangeVixen on 2012-03-24
If you searched the net and read the docs, by now then you probably have realised that there is really no perfect solution to this and many have asked this before.

"How do I execute a process and read from it without blocking?"

The problem with the subsystem module is that it is inherently designed to block and there are no methods to set it to nonblocking when you read. Both p.stdout.read() and p.communicate() will block and deadlock according to the docs:

[http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

There are solutions and work-arounds posted by others here:

[http://stackoverflow.com/questions/375427/non-blocking-read-on-a-subprocess-pipe-in-python](http://stackoverflow.com/questions/375427/non-blocking-read-on-a-subprocess-pipe-in-python)

[http://stackoverflow.com/questions/8495794/python-popen-stdout-readline-hangs](http://stackoverflow.com/questions/8495794/python-popen-stdout-readline-hangs)

[http://python.6.n6.nabble.com/Non-blocking-subprocess-Popen-stop-GUI-td1947925.html](http://python.6.n6.nabble.com/Non-blocking-subprocess-Popen-stop-GUI-td1947925.html)

But none that are truly portable, especially with subprocess.

There is talk about adding non-blocking read functionality to it though, but it's just talk.

---

