---
title: "[Java] Serializing a huge object"
date: 2008-07-31
forum: Programming Talk
---

### Post by CptPicard on 2008-07-31
So, I've got a "state" in my program which is essentially one big array plus contents, and it's around 2 gigabytes big. Computing this state is expensive, so I need to store it for future manipulation.

I run into out-of-memory problems when serializing though, probably because serialization of such a huge state consumes a lot of RAM in itself. It's as if the ObjectOutputStream never flushes while serializing.

I wonder if writing my own serialization code would help? Like, flushing the underlying stream after serializing each array item? Otherwise I suspect I'm SOL...

---

### Post by Diabolis on 2008-07-31
A 2 gigs array its too much, do you really need to save that much info?

What I would do is this:

Break the array and encapsulate its parts in different objects that best represent the type of information they store. So you can serialize each object one after the other without running out of memory.

---

### Post by CptPicard on 2008-07-31
Well, yes I need to do it, because I have millions of array items that the array is a kind of perfect hash for -- allowing quick access by "address".

My current attempt is to write a writeObject method for the array item class that does an out.defaultWriteObject() and then out.flush() and out.reset() to clean the handle cache (it's useless, all items are guaranteed different). I'll see how it works tomorrow when I get back to work on it...

---

### Post by ZylGadis on 2008-07-31
Provide more information about the particular application. Otherwise you'll only get general advice. The general advice I can give is to serialize the array elements separately, which you don't want to do for some reason that I don't understand. If you want to store a hash, include it in the object.

Also, be aware that the x86 JVM breaks when using more than a certain amount of memory, and I think you're pushing the limit. That is a common problem researchers face. The possible solutions are to use the server JVM, which is better suited for such tasks (and also has a 64bit version on x86/64/whatever it is called), or to use Solaris's JVM. I think IBM have two JVMs built specifically for high-memory use, but both are internal only. Another solution is, of course, to reduce your memory consumption, which is difficult because you can't force the gc. Look into JVMTI, writing a C agent that forces gc under certain conditions might help.

---

### Post by Diabolis on 2008-07-31
What about a hash table that contains smaller hash tables?

With an object like that you can serialize smaller objects one at a time and you keep the quick access feature. Maybe a bit slower, but probably the reduction in access speed won't be noticeable.

---

### Post by tinny on 2008-08-01
> **CptPicard said:**
> So, I've got a "state" in my program which is essentially one big array plus contents, and it's around 2 gigabytes big. Computing this state is expensive, so I need to store it for future manipulation.

I run into out-of-memory problems when serializing though, probably because serialization of such a huge state consumes a lot of RAM in itself. It's as if the ObjectOutputStream never flushes while serializing.

I wonder if writing my own serialization code would help? Like, flushing the underlying stream after serializing each array item? Otherwise I suspect I'm SOL...

:shock:

Maybe you can store the result as you go...? If you are able to take a sort of divide and conquer approach to this computation.

E.g.

So you have 1 massive problem now, can you break it up into say 10 parts??? Then store the 10 parts. Then when you need to retrieve this 1 massive result you instead retrieve 10 smaller ones and sum (or whatever) those together.

Basically can you use a divide and conquer technique for this calculation?

FYI: [http://en.wikipedia.org/wiki/Divide_and_conquer_algorithm](http://en.wikipedia.org/wiki/Divide_and_conquer_algorithm)

If so you can store the sub-problems and then only have to combine these to get your final result.

Am I making sense??? Im confused :)

Also manual object serialization is a common technique that is used in J2ME applications. 

You may find this interesting...

[http://java.sun.com/developer/J2METechTips/2002/tt0226.html#tip2](http://java.sun.com/developer/J2METechTips/2002/tt0226.html#tip2)

EDIT: Also, in your Object tree are there any fields that you can make transient (data contained within this structure that you dont need)?

---

### Post by CptPicard on 2008-08-01
Unfortunately, the computation is very intense and the stuff in the array are interrelated and I need to memoize into the array and get into those related items *fast* so this is why I have a "humongous array solution". :) Trying anything else would result in a crazy hit on computing time.

The reason why I like to preserve the state as is is encapsulation... it's nice to be able to just "save" and "load" it. But I am now experimenting with writing custom serialization code inside the state that flushes the ObjectOutputStream as it goes, as I typed above, so we'll see how it works sooner or later... can't test it right now.

---

### Post by tinny on 2008-08-01
> **CptPicard said:**
> Unfortunately, the computation is very intense and the stuff in the array are interrelated and I need to memoize into the array and get into those related items *fast* so this is why I have a "humongous array solution". :) Trying anything else would result in a crazy hit on computing time.

The reason why I like to preserve the state as is is encapsulation... it's nice to be able to just "save" and "load" it. But I am now experimenting with writing custom serialization code inside the state that flushes the ObjectOutputStream as it goes, as I typed above, so we'll see how it works sooner or later... can't test it right now.

Oh ok, id be interested to see some code if it works :).

(Or maybe some sudo code???)

---

### Post by tinny on 2008-08-01
BTW: What are you flushing too? Is it a file? Or do you want to store this as a blob in a DB or something...?

Desktop application? Server Application? (J2EE?)

---

### Post by henchman on 2008-08-01
Well, as the others say, we don't know too much about your problem, but may it be a solution to start writing the results into a file/embedded db from the beginning on? if you use an existing embedded db driver, there will be caching anyway and on some drivers (i know), you can increase the size of the cache... then you can compute your dataset and after each step, write it to the file...

this may take some time, but if iam not wrong you just have to compute it once and then you have it in your file, so just have to read it out in later runs of the program... or does the data change from run to run?

---

### Post by CptPicard on 2008-08-01
> **tinny said:**
> Oh ok, id be interested to see some code if it works :).

Currently, in the class that serves as the array item (the array is an ArrayList<ItemType>, that is) I just put

```

private void writeObject(ObjectOutputStream out) throws IOException {
  out.defaultWriteObject();
  out.flush();
  out.reset();
}
```

I googled for this kind of problems and seems like the ObjectOutputStream maintains an internal cache of handles for all serialized objects so that an object that is seen again can be just serialized by handle or something. reset() helps. So this may explain why I get unexpected memory usage from serialization.


> **tinny said:**
> BTW: What are you flushing too? Is it a file?

Yep. Just a throwaway short-lived cache file that keeps state between a couple of operations (mostly queries of the state), nothing more fancy really.

> 
Desktop application? Server Application? (J2EE?)

Command-line number-cruncher :)

> **henchman said:**
> Well, as the others say, we don't know too much about your problem, but may it be a solution to start writing the results into a file/embedded db from the beginning on?

That would be a bit overkill as a solution -- I just need some lightweight short-term caching mechanism and Java's serialization is easy enough. If I started computing "through" some database (replacing the big array with an embedded db), it would absolutely destroy performance, and if I just simply saved into one between runs, I actually think it would be slower than serialization... the ability to query would be a plus though.

That said, thanks for the idea -- I am very much aware of the possibility of using something like SQLite, but it doesn't fit the bill here :)

---

### Post by tinny on 2008-08-01
> That said, thanks for the idea -- I am very much aware of the possibility of using something like SQLite, but it doesn't fit the bill here 

On a side note...

I wonder how the following would work for this application of yours.

IF you where using an embedded DB (or connecting to a DB server) you could use some sort of JPA implementation (ive used JPA in a J2SE environment with great success before). Then each time you create a &#8220;ItemType&#8221; you could attach it to the current persistence context, then when your computation is complete you can just flush the current persistence context (sync with DB). So in theory you are leaving all the caching and persistence up to JPA.

Of course ive never tried attaching millions of entities to a persistence context before. I also would guess that you would be constantly maxing out the JPA implementations cache and therefore it would be constantly merging with the DB?

---

### Post by CptPicard on 2008-08-01
Theoretically it *could* work, and I have toyed with the idea. But I suppose you're right about the cache, plus do consider that the only reason why this computation is doable in a reasonable time is that I am able to very quickly find the relevant "other" Items by just doing a bunch of multiplications and additions to get an index into the array. If this were C this would be pointer math. Luckily I can also parallelize the problem by just dividing the array for all the cores I've got and doing certain operations in correct sequence so that there is never concurrent write...

I considered other data structures but they would both be too large *and* way too slow simply due to more memory access... this problem is so combinatorial that adding any constant factor to the basic ops blows straight up in your face, and it's not even algorithmically tractable in any other way except just crunching it :(

---

### Post by tinny on 2008-08-01
> **CptPicard said:**
> Theoretically it *could* work, and I have toyed with the idea. But I suppose you're right about the cache, plus do consider that the only reason why this computation is doable in a reasonable time is that I am able to very quickly find the relevant "other" Items by just doing a bunch of multiplications and additions to get an index into the array. If this were C this would be pointer math. Luckily I can also parallelize the problem by just dividing the array for all the cores I've got and doing certain operations in correct sequence so that there is never concurrent write...

I considered other data structures but they would both be too large *and* way too slow simply due to more memory access... this problem is so combinatorial that adding any constant factor to the basic ops blows straight up in your face, and it's not even algorithmically tractable in any other way except just crunching it :(

Brute force is soooo underrated! :)

---

### Post by tinny on 2008-08-06
> **CptPicard said:**
> Currently, in the class that serves as the array item (the array is an ArrayList<ItemType>, that is) I just put

```

private void writeObject(ObjectOutputStream out) throws IOException {
  out.defaultWriteObject();
  out.flush();
  out.reset();
}
```

I googled for this kind of problems and seems like the ObjectOutputStream maintains an internal cache of handles for all serialized objects so that an object that is seen again can be just serialized by handle or something. reset() helps. So this may explain why I get unexpected memory usage from serialization.




Yep. Just a throwaway short-lived cache file that keeps state between a couple of operations (mostly queries of the state), nothing more fancy really.



Command-line number-cruncher :)



That would be a bit overkill as a solution -- I just need some lightweight short-term caching mechanism and Java's serialization is easy enough. If I started computing "through" some database (replacing the big array with an embedded db), it would absolutely destroy performance, and if I just simply saved into one between runs, I actually think it would be slower than serialization... the ability to query would be a plus though.

That said, thanks for the idea -- I am very much aware of the possibility of using something like SQLite, but it doesn't fit the bill here :)

So, did it work?

---

### Post by luc_peuvrier on 2008-10-20
I developped JOAFIP for this kind of persistence problems:
[http://joafip.sourceforge.net/sample/sample.html]("http://joafip.sourceforge.net/sample/sample.html")
It make able to manage collection that can not stay in memory, make able to only update file with modification in memory.

---

### Post by CptPicard on 2008-10-20
Thanks, looks interesting, I'll check it out.

My data actually always is completely in RAM though, it would be far too slow otherwise -- it's the excessive RAM requirements of the serialization process that were the issue.

---

### Post by pp. on 2008-10-21
If the number of data types encountered in your giant array is moderate (say, nodes of but one or two types) you might be better off without a generic serialisation mechanism. Just implement for each node type a 'writeToFile' method and iterate over the array.

After all, you just want an array of (several millions of) nodes written to and read from a disk file, a database or some other representation which can be used to restore the array at a later time.

While this is the 'retail way' of looking at your problem, there also might be a 'wholesale' way: just dump an image of your RAM or of the portion occupied by the application to some persistent medium. Some programming environments call that an 'image' of a 'work space'. Can you put your app into a virtual machine?

---

### Post by luc_peuvrier on 2008-12-08
I had a problem of collection so huge that can not be stored in memory, because we do not want to use database I developped JOAFIP:
[http://joafip.sourceforge.net/]("http://joafip.sourceforge.net/").

May be it is a solution for your problem.

---

### Post by jespdj on 2008-12-09
You already said that a few posts above. ;)

---

