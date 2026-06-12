---
title: "have thread do work for a period of time"
date: 2011-12-26
forum: Packaging and Compiling Programs
---

### Post by Jordanwb on 2011-12-26
I'm writing a multithreaded program where additional threads perform work until the main thread tells them to stop (via a bit flag) after a certain amount of time has passed. What I want to do is have the main thread perform the same work just like the additional threads but for a period of time. 

Right now the main thread sets the bit flag to true (to do work), sleeps for 600 seconds that sets the bit flag to false and waits for each thread to stop via pthread_join.

I know I can do this:

```


void do_something ()
{
	uint64_t stop = time (NULL) + 600;

	while (time (NULL) < stop)
	{
	...
	}

}

```

is there a better solution for this? Hammering the time function tens of thousands of times a second may slow the thread down a lot. Thoughts?

---

### Post by MadCow108 on 2011-12-27
why should the main thread do the same work as the worker threads? smells like a bad design, you're mixing control and worker logic.
just start an extra worker thread and let the main thread wait.

---

