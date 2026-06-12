---
title: "Trying to find the total time of a program"
date: 2012-06-28
forum: Programming Talk
---

### Post by Miltnoid on 2012-06-28
Hey guys, I'm trying to find out the runtime of a program.  It's a python program, and I'm having it fork a lot, and then those children fork some more, until there's 256 processes, then use those subprocesses to all concurrently do something.  I want to find out the total runtime of everything being run.  So I attempted to run using 'time python myprogram.py', but that only checks how long the main process runs for.  This doesn't check how long it takes for the main process and all its children to run for.  Is there any way to check for that as well?

---

### Post by satsujinka on 2012-06-28
In the past I used bash and the date command to figure out rough times of how long something took. I don't know whether the python program would exit before the child processes return, but you could give it a try.

Another idea, is if you could pull out all of the process ids you might be able to check to see if they're still running.

---

### Post by 11jmb on 2012-06-28
This looks like a job for some callgraph profiling. Try the valgrind tool callgrind

Out of general curiosity, why so many subprocesses? Are they all waiting for I/O at some point, or are you running on a 256-core machine?

---

### Post by click4851 on 2012-06-28
I'm not familiar with Python, there must be no "top" like command....

did find this though, and an answer for me about "top"......

[http://www.python-forum.org/pythonforum/viewtopic.php?f=16&t=4776](http://www.python-forum.org/pythonforum/viewtopic.php?f=16&t=4776)

---

### Post by Garyu on 2012-06-28
You could maybe use the timeit module. 

[http://docs.python.org/library/timeit.html](http://docs.python.org/library/timeit.html)

I know that can be used to see how long it takes to execute one function or a few lines of code. Not sure if you can do it directly on a __main__ or if you have to incorporate it somehow into a special function. Never actually used it myself.

---

