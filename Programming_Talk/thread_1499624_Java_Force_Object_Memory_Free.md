---
title: "Java Force Object Memory Free"
date: 2010-06-02
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-06-02
One of the nice things about Java is that the programmer does not have to worry about freeing memory.  The garbage collector handles that burden at the expense of some extra CPU cycles.  However, I think I might have a case where I have a need to free objects manually or force them to be freed.  I have a function which declares and uses two HashMaps as part of its processing.  Only 10-40 objects are entered into the maps and by function return, all objects are no longer needed and left for the garbage collector to destroy.  The problem is that this function is called thousands of times during program execution.  It's called tens of times per second and after the programming has been running for a while, the hard disk starts chugging and the program temporarily freezes during this hard disk activity.  I speculate that what might be happening is that the garbage collector gets bogged down cleaning up all the dead copies of the maps allocated in that one function called thousands of times.  Is this what is happening?  If so, is there a way I can manually destroy the objects before returning from the function?  I know there's a GC() method which calls the garbage collector, but I don't want to do that, that would be too computationally expensive to call at each function exec.  I would like to manually remove just those objects which I know will no longer be needed.

---

### Post by thebigob on 2010-06-02
calling the garbage collector manually is absolutely no guarantee it will run.

There are two ways to overcome the problem you are seeing.

Firstly make object eligible for garbage collection as soon as possible.

eg

Object o = new Object();

o.doStuff;

_**o = null;**_

//lots of of other code

This will show the runtime you have finished with the object and will clean it up much more efficiently than it having to determine if the object is finished with.

The other option is to increase the memory available to the jvm.

Some jvms only use 64mb ram as a default however when running your code you can override this with the Xmx flag

eg on the command line:
```

java -Xmx1000m MyClass

```This will allow the jvm to access a gig of ram.

Hope this helps

---

### Post by PaulM1985 on 2010-06-02
> **SNYP40A1 said:**
> It's called tens of times per second and after the programming has been running for a while, the hard disk starts chugging and the program temporarily freezes during this hard disk activity.

If the hard disk is chugging maybe it is this that is causing the problems rather than garbage collection, since large amounts of I/O can really reduce program speed.  If you are doing large amounts of I/O, maybe it would be worth reading everything into a temporary structure and then splitting it off for the appropriate processing, rather than trying doing large multiples of small accessing.

Paul

---

### Post by nvteighen on 2010-06-02
> **PaulM1985 said:**
> If the hard disk is chugging maybe it is this that is causing the problems rather than garbage collection, since large amounts of I/O can really reduce program speed.  If you are doing large amounts of I/O, maybe it would be worth reading everything into a temporary structure and then splitting it off for the appropriate processing, rather than trying doing large multiples of small accessing.

Paul

Couldn't it be that the system is swapping? (just curious...)

---

### Post by PaulM1985 on 2010-06-02
> **nvteighen said:**
> Couldn't it be that the system is swapping? (just curious...)

Yeh, I guess so.  I thought that garbage collection would run automatically if the JVM was running out of memory so I thought that swapping wouldn't be likely.  (Unless the user allocates enough memory to the JVM which over runs the remaining RAM that the computer has available)... So, erm, dunno, maybe.

Back to the original point, if you know how many objects are created (between 10-40 per call) could you set up a static variable on the class which counts the number of things which need to be freed, then release them once you hit the limit.  That way you would not be running the garbage collector with each call of the function, but only once you know you have a considerable number of things which need to be released.

Paul

---

### Post by soltanis on 2010-06-02
No, the JVM will call the garbage collector whenever it feels like it, but you can manually invoke the garbage collector when you know you have a lot of objects to clean up. To make the JVM's job easier, when you're done using an object, you should assign its reference to null so that the object doesn't have any references to it anymore. If you have objects referring to one another, consider adding a method that breaks those references as well, so that the objects can be marked more efficiently.

So what you want is

```

Object o = new Object();
// use o...
o = null;

// loop done
System.gc()

```

Oh and by the way, the last call just "hints" that the garbage collector should be called. It's up to the individual virtual machine to take the hint.

---

### Post by SNYP40A1 on 2010-06-02
The program is not intentionally reading the hard disk when all this happens.  By the time that function is called, all data has been loaded off the disk and placed into in-memory data structures.  I also allocate 2.5 GB of memory to the JVM (system has 4 GB).  So at that point, it's using swap space.  I thought about setting references to null, but since the function only creates / modifies local-variables, I figured that would be redundant.  The GC would (or should) know when the function returns that all objects referred by the local variables are no longer needed.  I'll set the locals to null and see if that helps.  

Still, there should be some way in Java to manually remove an object from the heap.  I understand that they chose not to do this for safety, but there could be some method which requests the GC to remove an object (and the GC could elect not to if it sees that something still references it).

---

### Post by Reiger on 2010-06-02
No: System.gc() suggests that the Garbage collector be run, but it makes no guarantee that it will.

What you can do is using weak references and similar objects (weak hashmap) to get more of this de-referencing behaviour. The references are more agressively freed up by the garbage collectors; the class is essentially a wrapper around other objects with the explicit intention that if you run out of memory these objects are the first to go.

---

### Post by myrtle1908 on 2010-06-02
As an aside, it is generally a good idea to set the minimum and maximum heap to the same size to prevent wasting VM resources used to constantly grow and shrink the heap.  This at least is my understanding and I use this approach in production systems.

---

### Post by Some Penguin on 2010-06-02
Read [http://java.sun.com/javase/technologies/hotspot/gc/gc_tuning_6.html](http://java.sun.com/javase/technologies/hotspot/gc/gc_tuning_6.html) .

---

