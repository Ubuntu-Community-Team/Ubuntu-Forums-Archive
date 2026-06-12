---
title: "java - multithreaded design question"
date: 2008-09-19
forum: Programming Talk
---

### Post by badperson on 2008-09-19
Hi,

I just build a new machine, an 8-core amd machine, so I'm psyched to start doing some more sophisticated multithreaded stuff. 

I'm just wondering what are some good strategies for using threads; the kind of stuff I'll be doing is opening and parsing large xml files...what are some good design issues to think about when using mulitple threads for a purpose like that?
thanks,
bp

---

### Post by henchman on 2008-09-19
Well, the most simplest would be of course opening multiple files parallel, one per thread.

i don't think it's reasonable to read the files in in one thread and then process the data in another one. well that maybe would make sense if you have data in the file which is time-intensive to process. any other opinions?

---

### Post by bfhicks on 2008-09-19
I haven't done this with XML, and not sure if there would be a smart way to do it, but one way I have utilized multiple cores in one of my applications. It wasn't as complex as parsing XML, but it was getting the values from large files of XYZ points.

I read the file in as binary and dumped it to memory, then did a division of the memory (smartly to handle splitting up in the middle of the line) and sent each part to its own thread for parsing.

Typically reading in the XML you'd have a key and value which, I guess you could approach it the same was I have, just keep a set of keys and values for each thread and then combine them all at the end.

---

### Post by Reiger on 2008-09-19
Well if you are searching for some patterns you can do so on chunks of data evaluating the 'boundaries' of this data at the very end. For instance if you are searching for a regex (byte) pattern of which you know it may take up to X bytes; you can run this on chunks of Z bytes and afterwards evaluate the 2X bytes of which the border between two chunks of Z bytes is right in the middle:

```
[Z bytes ([X bytes]]|[[X bytes]) Z bytes ([X bytes]]|[[X bytes]) Z bytes] *etc*
```

So if you happen to be processing very large files this should gain you some speed increase; of course if you cannot be sure of the maximum length of a pattern to look for, or if your pattern length is close to (or greater than) 1/2 Z it will not really be a viable option.

---

### Post by tinny on 2008-09-19
Unfortunately if you are using Java threads you are not actually taking full advantage of a multi core cpu.

To do this properly you need to look at something like [DataRush]("http://www.pervasivedatarush.com/"). I would only look into this if you are doing something serious.

---

### Post by kavon89 on 2008-09-19
I don't know if there are any design concepts with multi-threaded programs, but here is what I've learned on my own:

Pretty much just split things into threads when you need to do them at the same time, or to help stabilize your program by making the thread doing lots of work report back to another thread every so often... and if it doesn't get a report back it would be a sign that the thread froze and the other thread would take care of closing that thread without locking up your application.

Example (unsure if this is efficient but it definitely should be):

The GUI thread gets data from a processing thread which gets it's data as it loads from a thread which gets information from a huge file. Essentially just splitting the work so things can get done at the same time and nothing stops to wait on another step to complete in a certain order because things will be done simultaneously.

Threads are really funny when you try making them share data though, and you must have controls within the threads so that everything happens at the right time and threads don't inappropriately try and access another thread's stuff.

Another example: CyclicBarrier, I used this to help control my threads in a fun little benchmarking program, when the threads were done they waited at the "barrier" until the correct amount of threads were waiting there to continue.

---

### Post by tinny on 2008-09-19
FYI: Here are some things you can Google that will give you some tips / recourses that can be applied to Java multi threading.

Critical section [http://en.wikipedia.org/wiki/Critical_section](http://en.wikipedia.org/wiki/Critical_section)

Thread synchronization [http://www.ibm.com/developerworks/java/library/j-threads1.html](http://www.ibm.com/developerworks/java/library/j-threads1.html)

Dead locks [http://java.sun.com/docs/books/tutorial/essential/concurrency/deadlock.html](http://java.sun.com/docs/books/tutorial/essential/concurrency/deadlock.html)

Inter thread communication (Producer / consumer problem)

If you get the above 4 concepts under your belt you will be fine.

Also ["Operating System Concepts with Java"]("http://www.wiley.com/WileyCDA/WileyTitle/productCd-047176907X.html") is a good book for learning these concepts.

---

### Post by kavon89 on 2008-09-20
:) tinny saves my terrible post which vaguely refereced all of those with some links for you.

---

### Post by badperson on 2008-09-21
> **tinny said:**
> Unfortunately if you are using Java threads you are not actually taking full advantage of a multi core cpu.

To do this properly you need to look at something like [DataRush]("http://www.pervasivedatarush.com/"). I would only look into this if you are doing something serious.


that's an interesting link...I'm more of an intermediate programmer, I'm not super erudite when it comes to java concurrency, but it's definitely an area where I want to spend some time on. I'll check out that link for sure. 

Also, is there a way to run processes in different threads, and log which processor is running a given thread? 
bp

---

### Post by CptPicard on 2008-09-21
I tend to do most of my concurrent architecturing with "actors" which are essentially an object with an associated message queue and a worker thread. Essentially, the only thread that ever is active inside the object is the worker thread, and all processing is delayed asynchronously in the message queue. This keeps you from having to build complicated locking strategies for managing shared state (actually, shared mutable state is the root of the problem, so you want to get rid of it as much as you can -- see Clojure for this approach).

Java's anonymous inner classes help with an ability to construct the "message" in the queue as an ad hoc Runnable that yanks whatever method that needs asynchronous execution. The "downside" of this approach is that you need some bookkeeping state inside your object... it becomes a kind of "state machine" that reacts of the messages it receives. But I think this is a small price to pay for the ability to always know that the object itself is single-threaded.

```

public void printInt(final Integer i) {
        pa.post(new Runnable() {
            public void run() {
                pa.print(i.toString());
            }        
        });
    }

```

This is btw another of these things that I started thinking of after using HLLs where I got used to the idea of just shoving an anonymous function into a queue for later delayed execution...

---

