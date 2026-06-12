---
title: "Busy loops?"
date: 2008-07-11
forum: Programming Talk
---

### Post by Phristen on 2008-07-11
There is a process I am communicating with via standard input & output.
Once I write something to it, I wanna make sure that I get some specific reply within a certain period of time.
Every time I read something I update *lastRead* variable (i.e. lastRead = currentTimeMillis()), and every time I write I update *lastWrite*.

The code I am thinking about looks something like this:

[php]public String getResponse (String in, int withinMillis) {
		tellProcess(in); //lastWrite is also updated here
		long expire = lastWrite + withinMillis;
		while (lastWrite > lastRead || System.currentTimeMillis() >= expire);
		return lastWrite <= lastRead? lastString : null;
	}
[/php]
There is also a separate thread running in the background that reads input from the process, and updates lastRead and lastString properties.
So, getResponse method will basically return the last string if it was received withing the "withinMillis" after the call, or null if nothing was received. This method has to be blocking and it has to return as soon as the input is received.

The problem here is that ugly-looking busy loop, so how do I get rid of it? I obviously haven't done a lot of process sync before :(

---

### Post by Zugzwang on 2008-07-11
> **Phristen said:**
> 
The problem here is that ugly-looking busy loop, so how do I get rid of it? I obviously haven't done a lot of process sync before :(

Basically, you do it the following way. You start a thread waiting for I/O. 
Then in the caller thread you call wait(timeout) for some object and make sure that the I/O thread will notify() the object when it got some data. 
There are a lot of details to consider with this approach. You should look out for some tutorial on these if you want to use this approach.

Alternatively, you can reduce the system-load of the caller thread by invoking the Thread.sleep method for some low number of milliseconds in each iteration in the busy look.

---

### Post by Phristen on 2008-07-11
Thread delays give me IllegalMonitorStateException.
Do I need another thread for writing as well?

---

### Post by Zugzwang on 2008-07-13
> **Phristen said:**
> Thread delays give me IllegalMonitorStateException.
Do I need another thread for writing as well?

I don't think so. As already stated, you should look into some tutorials as my advice is incomplete since I never used this features.

---

