---
title: "My frustration about Java (vs Python)"
date: 2010-10-11
forum: Programming Talk
---

### Post by bigdidz on 2010-10-11
Last winter, I programmed a complex genetic mapping using Python.  To map genes, I need to build genealogies and that takes a lot of times.  Typically, it takes about 5 seconds by genealogy (in python) and I need more than 500 000 ones for one simulation.

In order to accomplish my duty,I made a full optimized Python's program.  Moreover, I used parallel python to distribute the program on an ad hoc grid.  The result is quite impressive.  In fact, 5 sec by generation is very good.

But, all the post on Internet telling that python is slow was still in my mind.  This summer, on a bicycle in Peru, I had an idea:  use python and parallel python to manage the raw data and use Java to makes the genealogy (an nothing more).  So I went in a café to write my (even more) full optimized algorithm (on a sheet of paper).  Than, two month later and back home, I implemented my algorithm in Java.

It took a s**t load of time.  Finally, yesterday, I was able for the first time to make one genealogy.  At my big surprise, the new program is less than 2 times faster than the python counter part.  My question is, where is my 30 times faster expected (c.f.: [shootout]("http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=python&lang2=java"))????

I profiled my program and I found no (unexpected) bottle neck.  The program is just slow!!!

I use a lot of HashMap and ListArray.  I suspect java.util.* slows my program.  I loop all the time over them and I believe it might the problem.  Java cannot deal with base type elements in those containers and I must use wrappers (principally Integer) to be able to work with java.util.* .

I know that there is a package call [Trove]("http://trove4j.sourceforge.net/") that makes containers for base types.  Is it really faster?  Do you have any information about it more than the JavaDoc?  Do you have any idea what can I do?


For conclusion and recommendations, if you are a situation where you need to implement a slow and complicated algorithm: use Python!!  It is not that slow and, I fact, the optimisation and modification is that faster than it will be faster than the Java counter part.

Thanks a lot for your help and empathy.

D.A.

P.-S.:  I use Java and not C++ because I want to use my program on a grid made of heterogeneous computers without recompiling and exterior dependencies.

---

### Post by Some Penguin on 2010-10-11
[http://stackoverflow.com/questions/629804/what-is-the-most-efficient-java-collections-library]("http://stackoverflow.com/questions/629804/what-is-the-most-efficient-java-collections-library")

seems relevant.

That said, if you're doing multithreading, and you're doing anything like 'Collections.synchronizedMap(new HashMap<blah,blah>()>' -- don't.  The 'synchronizedFoo' wrappers implement synchronization by having every method call require the object's intrinsic lock.  Use the ConcurrentHashMap instead, or use the MapMaker from the Google Collections framework to make a concurrent map.

Not enough detail to give more advice.  There's a lot of ways to implement things badly (like iterating over keys and doing get() rather than iterating over entry sets, or excessive use of synchronized() when using a reentrant read-write lock would do, or so forth.  Oh, and if you're using a 64-bit build that doesn't need more than 32GB of heap, Sun at least has the -XX:+UseCompressedOops option, which should improve memory utilization including caching).

---

### Post by r-senior on 2010-10-11
This has lots of good ideas here too, if you can manage to sift through it all.

[http://www.javaperformancetuning.com/tips/rawtips.shtml]("http://www.javaperformancetuning.com/tips/rawtips.shtml")

If sounds as though you are using lots of ArrayList and are having to box/unbox from Integer. Did you rule out using plain arrays of primitive types for some reason?

---

### Post by bigdidz on 2010-10-11
Thanks for thoses quick answering.

I use ArrayList to represent a sequence of gene.  I use the int 2 for ancestral gene, 3 for mutant gene and 5 for unknown gene.

I cannot use array because I need to map each sequence with an integer representing the number of that sequence in the population.

Basically, I work a bit on my sequences (ArrayList<Integer>) and than change the population (HashMap<ArrayList<Integer> , Integer>).

I always use loops like for(ArrayList<Integer> seq: pop.keySet()) and I'm doing my algorithm the most efficiant way.

D.A.

---

### Post by Reiger on 2010-10-11
Java is definitely faster than Python, especially in workloads which are highly concurrent. But Java takes also more time to start up than Python does. 

So if you are simply forking out any number of processes the cost of starting up the JVM versus the performance gain on the relatively small chunk may not work as much in your favour as you would expect. You might get more if the JVM spans multiple CPU's and you can break up its task in threads of its own. Essentially reduce the number of running instances of the JVM but make the task bigger so Java+JVM can maximize the throughput advantage.

That said those benchmarks are something you notice more in server applications where greater performance means more concurrent requests and more throughput, than in a complex algorithm which runs once on small data sets.

---

### Post by r-senior on 2010-10-11
So does your HashMap only have three values in it? Or have I misunderstood?

I'm thinking you'd have something like this using primitives ...

```

    private static final int ANCESTRAL = 2;
    private static final int MUTANT = 3;
    private static final int UNKNOWN = 5;

    ...

    int[] sequence = new int[500000];
    int ancestral = 0, mutant = 0, unknown = 0;

    ... 

    for (int i = 0; i < lengthOfSequence; i++) {
        switch (sequence[i]) {
            case ANCESTRAL: 
                ancestral++;
                break;
            case MUTANT: 
                mutant++;
                break;
            default:
                unknown++;
        }
    }

```

It must not be as simple as that?

---

### Post by bigdidz on 2010-10-11
Thanks a lot for your answers!

I'll try to clarify my situation...

My program, it is relatively big.  It is about 2000 code lines.

I use parallel python and the subprocess module to paralyze the program.  So I use only one Java thread.  Like I said, it takes now about 2.5 seconds per graph (genealogy) but I do this maybe 200 times before leaving Java.  So, I have no problem of JVM initialization.  Moreover, I'm now only debugging my program and use a Java only version. 

The memory profiling is ok.  About 200m.  Luckily, the computers I use allows me to use that space without problem.



To solve my problem, I am presently doing a "deep" profiling using netbeans.  It's profiling all methods Java use (it will take hours to make).  After I'll be sure that the bottlenecks are the containers, I'll probably use  Google Java Collections.

Thanks again,

D.A.

---

### Post by shae on 2010-10-11
You really do not need a HashMap if your keys are Ints.  You just need to map the population numbers to [0, n] where n is the number in the population.  Is this population set or does it increase?  Furthermore, you should consider moving the actual sequence into an array as well.  This will make your operations across one chunk of contiguous memory and remove the overhead of the HashMap and ArrayList.

According to your OP you already saw a 2x improvement with your new algo.  This is quite good.  Most improvements will be improvements in your algo and not in switching languages.  If you look at that comparison, they are testing very specific parts of the language that you may not be using.

---

### Post by Some Penguin on 2010-10-12
For sequences of three-valued states, ArrayList<Integer> seems heavyweight.  An ArrayList of an enumerated type should be more efficient; better still, wrap an array of bytes (for simplicity's sake, two bits per location = 4 per byte) in an object and use that.

e.g.

```

publc enum Trinary { ONE, TWO, THREE };

class ByteThing {
  private final byte[] data;
  private boolean changed = true;
  private int     hashCode = -1;
  
  public ByteThing(int capacity) {
    data = new byte[(capacity+3)/4];
    Arrays.fill(data, (byte) 0);
  }

  public Trinary get(int pos) {
    int byteIdx = pos/4;
    int quadIdx  = pos % 4;
    int bitMask = 0x11 << (2*quadIdx);
    byte b = data[byteIdx];
    
    int value = ((int) (byte & bitMask) >> (2*quadIdx);
    switch(value) {
      case 0:  // uninitialized, plz fix or do somefink
      case 1:  return Trinary.ONE;
      case 2:  return Trinary.TWO;
      case 3:  return Trinary.THREE;
    } 
  }

  public void set(int pos, Trinary value) {
    changed = true; // need to rehash
    int byteIdx = pos/4;
    int quadIdx  = pos % 4;
    int bitMask = 0x11 << (2*quadIdx);
    int newBits = (value.equals(Trinary.ONE) ? 0x01 :
       (value.equals(Trinary.TWO) ? 0x010 : 0x11)) << (2xquadIdx);

    byte b = data[byteIdx];

    b = b & (~bitMask);
    b = b | newBits;
    data[byteIdx] = b;
  }
  
  @Override
  public int hashCode() {
     if (!changed) {
       return hashCode;
     }  else {
        // compute something based on data and return it
        // actual function is not too important
        // and then clear the 'changed' flag and cache the value
     }
  }
  
  @Override
  public boolean equals(Object obj) {
     // also need to populate this; need to verify that obj is same 
     // exact class, that data arrays are of same length, that data
     // contents are same; oh, and throw NPE if obj is null.
  }
}

```

Along those lines.  Should be MUCH less memory consumption, and hash map access is probably faster as well.

---

### Post by Some Penguin on 2010-10-12
Other notes:

* One should be very leery of using mutable objects as hash keys.  Behavior is not clearly defined if you change their contents.

* As noted, iterating over a map's keySet() is /not/ going to be very efficient if you're actually going to be using the value, too.  Use the entrySet() and get both the key and value at the same time.

* A probably better data model:
  * Map:  identifier => sequence
  * Map:  identifier => population

Identifiers are immutable.  Say, plain Integers.  If you change an entire population's sequence, you just need to change the sequence itself.  If you split one (some mutate, others don't), you create a new identifier and associate it with the mutated sequence, and adjust pops accordingly.  Net effect:  you don't have to hash long sequences for many operations.

And if you want to take a census by sequence (knowing that some populations may have mutated to be the same), you can still do that -- you iterate over the first map's entry set, use the key to also look up the count, hash a version of the sequence w/ that count... but other operations will still be fast because you're not doing sequence-level comparisons all the time.

---

### Post by bigdidz on 2010-10-13
Hundred Thanks!  I'm presently using all your ideas and I already see a great improvement (about 3 times)!

I will write my results later!

D.A.

---

