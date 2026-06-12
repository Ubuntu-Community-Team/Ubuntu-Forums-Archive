---
title: "Questions about Java"
date: 2008-06-20
forum: Programming Talk
---

### Post by Exershio on 2008-06-20
Since Java supposedly ditched virtual machines and went to JIT compilation (from what I've heard), why are Java apps so slow and unresponsive (Azureus, Netbeans, Eclipse, etc..)? Is Java really a slow language or is there something I'm missing?

I'm thinking of trying it out for game designing, but if it's slow as hell then I'll have to look somewhere else.

---

### Post by xlinuks on 2008-06-20
> **Exershio said:**
> Since Java supposedly ditched virtual machines and went to JIT compilation (from what I've heard), why are Java apps so slow and unresponsive (Azureus, Netbeans, Eclipse, etc..)? Is Java really a slow language or is there something I'm missing?

I'm thinking of trying it out for game designing, but if it's slow as hell then I'll have to look somewhere else.

Roughly saying Java is 50% slower than C/C++ and about 20 times faster than what you get by default when using Python or Ruby (thus it's very fast, the technology sucks).
But besides that there are 3 factors that hugely affect the user
1) The JVM startup takes a while, especially when you start Java for the first time.
2) Java Swing draws anything by itself, it's pure software rendering, not bindings to system calls like python does, but Eclipse does use bindings as well, it's called SWT.
3) Java is fast _after_ it compiles such and such thing.

> "Remember how HotSpot works. It starts by running your program with an interpreter. When it discovers that some method is "hot" -- that is, executed a lot, either because it is called a lot or because it contains loops that loop a lot -- it sends that method off to be compiled. After that one of two things will happen, either the next time the method is called the compiled version will be invoked (instead of the interpreted version) or the currently long running loop will be replaced, while still running, with the compiled method. The latter is known as "on stack replacement" and exists in the 1.3/1.4 HotSpot based systems."

As a side note, there's lots of not-so-experienced-programmers who do stuff like this (because they rely too much on "write dumb code - java will optimize it"):
```

for( int i=0; i<myVector.size(); i++ ) {}

```

In other words it's much faster than people usually think, have a look at this benchmark where Java outperforms Pythons by orders of magnitude:
[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python")

Some Python fan will soon jump in and say that there are way to enhance the speed of python - but that's quite another story, cause same you can do with Java.

---

### Post by Quikee on 2008-06-20
If they use JIT compilation this doesn't mean they ditched virtual machines - JIT is only an optimization of code execution using just-in-time compilation to machine code, but a virtual machine is also present (to actually do JIT compilation and bytecode interpretation when necessary, garbage collection,...).

Slow? I don't think it's slow, but memory consumption is indeed high which might cause it to be slow if you don't have a decent amount of RAM available.

---

### Post by themusicwave on 2008-06-20
> **xlinuks said:**
> 


As a side note, there's lots of not-so-experienced-programmers who do stuff like this (because they rely too much on "write dumb code - java will optimize it"):
```

for( int i=0; i<myVector.size(); i++ ) {}

```


As a not-so-experienced-programmer, why is this bad and how should you avoid it?  Are you saying it would be better to use something like:

```

Object item = null;
for( item: myCollection){
      //Do Stuff
}

```

Or is it better to use an Iterator?

```

Object o = null;
for (Iterator iter =myCollection.iterator(); iter.hasNext();) {
   o  = iter.next();
}

```

For the record I do know that using something like an ArrayList<Type> saves some code with the boxing and unboxing.  However, I was not aware that a for loop like you posted was worse than the other loops I posted.  

As the sole developer at my company, I would like to do the best I can.

Also, if this is hijacking, we can move this to a new thread...

---

### Post by xlinuks on 2008-06-20
It's all about how fast Java can compare. As it turns out, Sun's Java is optimized to compare a number to -1, 0, 1, 2, 3, 4 and a few other numbers in this range.
Thus, if a vector is 4 items size it's not a big deal, however if a vector is 1000000 than Java spends a little more time comparing, because, as I said, it's optimized to compare against those small numbers, not agains (as in this case) a million or so, thus the best/fastest way of doing that would be:

```

for( int i=myVector.size()-1; i>=0; i-- ) {
//do stuff
}

```
As you can see, in this implementation after each iteration Java compares i to zero ( i>=0 ) - which is easier to do for Java. When you consider this is happens in a iteration of a million times you have some performance gains (keep in mind that "i=myVector.size()-1" is only once executed).
Sun is working on a way of doing what I've done "under the hood" so that Java can compare against zero (or a similar number) but since it's hard to figure out whether this might spoil the execution logic of the code inside the loop - there's no robust implementation about that.
It's a speed gain, but a pretty insignificant one, but if it happens a lot, the code has sensible performance troubles.

---

### Post by themusicwave on 2008-06-20
> **xlinuks said:**
> It's all about how fast Java can compare. As it turns out, Sun's Java is optimized to compare a number to -1, 0, 1, 2, 3, 4 and a few other numbers in this range.
Thus, if a vector is 4 items size it's not a big deal, however if a vector is 1000000 than Java spends a little more time comparing, because, as I said, it's optimized to compare against those small numbers, not agains (as in this case) a million or so, thus the best/fastest way of doing that would be:


I never realized that, thanks for the tip.  I never knew that Java could be optimized like that.  

I tend to use a lot more of the for( item : Collection){} just because the code is nice an concise.  I think this is also an influence of my learning Python recently as well.

---

### Post by achelis on 2008-06-20
You can use Java for games - but of course it also depends what kind of game you're wanting to make. My point being that you can press more out of the machine using C/C++. For "smaller" games however Java is fine - and with todays machines smaller can be quite big :).
I'd recommend against using Swing for graphics in games though. There is either JOGL og LWJGL for that allowing you to use OpenGL with Java. Personally I've used LWJGL which is brilliant imo.

@xlinuks: Thanks for the tip, I never knew that.

@themusicwave: As far as I know the for each in Java is simply a shorthand for creating an iterator and thus should compile to the same. Someone correct me if I'm wrong.

As for optimizing performance I prefer to try to make readable code first, and then optimize bottlenecks if performance is bad. Optimizing the entire program is just not worth the effort I think.

---

### Post by Npl on 2008-06-20
> **xlinuks said:**
> It's all about how fast Java can compare. As it turns out, Sun's Java is optimized to compare a number to -1, 0, 1, 2, 3, 4 and a few other numbers in this range.
Thus, if a vector is 4 items size it's not a big deal, however if a vector is 1000000 than Java spends a little more time comparing, because, as I said, it's optimized to compare against those small numbers, not agains (as in this case) a million or so, thus the best/fastest way of doing that would beThats totally and utterly nonsense.
The reason you shouldnt use ```
i<myVector.size()
``` in a loop is that you then call the size-method each iteration. If the size of the vector doesnt change you can use a variable instead, it doesnt matter if you compare against 0 or any other value. ```
int endIndex = myVector.size();
for( int i=0; i<endIndex; i++ ) {}
```

---

### Post by pmasiar on 2008-06-20
> **xlinuks said:**
> Some Python fan will soon jump in and say that there are way to enhance the speed of python - but that's quite another story, cause same you can do with Java.

No you cannot, because you (like other speed kiddies) compare apples and oranges: Java is JIT-compiled while Python is not. So Java cannot get another speed from compilation like Python can. 

There are JIT-compilers for Python too, they are just not as popular because using them does not gain much: if your app spends 90% of the time in DB or web server calls (and waits), there is no reason to spend much effort to make remaining 10% of the code any faster. Speed kiddies chose to ignore that simple fact - it feels so powerful to tinker with the speed-irrelevant code making it "faster".

Google works on own reimplementation of Java for [http://en.wikipedia.org/wiki/Google_Android](http://en.wikipedia.org/wiki/Google_Android) (called Dalvik), because some wrong decisions made it hard to speed Java (JVM) for mobile phones. If Java was as good as you describe, would they waste efforts to do that?

---

### Post by xlinuks on 2008-06-20
> **Npl said:**
> Thats totally and utterly nonsense.
The reason you shouldnt use ```
i<myVector.size()
``` in a loop is that you then call the size-method each iteration. If the size of the vector doesnt change you can use a variable instead, it doesnt matter if you compare against 0 or any other value. ```
int endIndex = myVector.size();
for( int i=0; i<endIndex; i++ ) {}
```

Before saying "utterly nonsense" I think you should learn beyond "basic" Java, do you know assembly? If so you would know that the CPU can compare against zero faster than comparing two numbers together. That is where it comes from. Is that again a nonsense to you?
How about learning a bit more?
You certainly haven't heard about Joshua Bloch's "Effective Java" book, he is now:
Chief Java Architect at Google, his Effective Java™ Programming Language Guide, the most practical, authoritative guidelines available for writing efficient, well-designed programs for the Java platform.
Among other things he mentions (in this book) the facts I told in this thread before.

As to your second: you are wrong again. Java (6) is no longer that dumb as you think, the guys from Sun know very well that a lot of people do stuff like "for( int i=0; i<v.size(); i++ ){}" - so Java now checks if the "v.size()" inside the loop doesn't change, if so, Java puts under the hood the actual size of the vector (or whatever object) instead of calling each time that method.
If you choose to stay in ignorance - please do so, but don't tell others are wrong.
I would tell you more, but you don't seem polite enough to share those facts with you.

---

### Post by xlinuks on 2008-06-20
> **pmasiar said:**
> No you cannot, because you (like other speed kiddies) compare apples and oranges: Java is JIT-compiled while Python is not. So Java cannot get another speed from compilation like Python can. 

There are JIT-compilers for Python too, they are just not as popular because using them does not gain much: if your app spends 90% of the time in DB or web server calls (and waits), there is no reason to spend much effort to make remaining 10% of the code any faster. Speed kiddies chose to ignore that simple fact - it feels so powerful to tinker with the speed-irrelevant code making it "faster".

Google works on own reimplementation of Java for [http://en.wikipedia.org/wiki/Google_Android](http://en.wikipedia.org/wiki/Google_Android) (called Dalvik), because some wrong decisions made it hard to speed Java (JVM) for mobile phones. If Java was as good as you describe, would they waste efforts to do that?

You partially understood me wrong, otherwise you wouldn't say "If Java was as good as you describe" - I hate it for many reasons and so on (I'm also trying to move to C++), saying that Java by default is much faster than Python doesn't mean that I love it or that I say it's better, speed is not everything.
As to the other things you say, I mean the Java -server option (and the other options available, including those for OpenGL rendering) that sometimes double the performance depending on what kind of code is being executed.

---

### Post by Npl on 2008-06-20
> **xlinuks said:**
> Before saying "utterly nonsense" I think you should learn beyond "basic" Java, do you know assembly? If so you would know that the CPU can compare against zero faster than comparing two numbers together. That is where it comes from. Is that again a nonsense to you?
I know and programmed assembly for x86, m6800 and mips CPUs... which is your 'CPU' you speak about and assume to be a reference to all other architectures?
Also some point of reference would be nice, mips simple ALU instructions execute **all** in 1 cycle. x86 (Pentiums and up surely) has also 1 cycle for comparing vs constant/register in all instances. Dont remember cycles for 68000`s, might be truth in that case, but as you simple refered to 'CPU' you are surely wrong
> **xlinuks said:**
> As to your second: you are wrong again. Java (6) is no longer that dumb as you think, the guys from Sun know very well that a lot of people do stuff like "for( int i=0; i<v.size(); i++ ){}" - so Java now checks if the "v.size()" inside the loop doesn't change, if so, Java puts under the hood the actual size of the vector (or whatever object) instead of calling each time that method.And how would it reliably know so except in corner cases?
```
MyObsucureClass o = MyObsucureClass(myVector); // has reference to myVector
for( int i=0; i<myVector.size(); i++ ){
// do something
o.someMethod(); // does it change myVector or not? maybe its even a inherited class that changed the behaviour
}
```
Can you reliably tell if myVector changes? Java cant gurantee it either and compilers HAVE to be conservative
How about own Container-Classes, does Java automatically know how to optimize if they are used?
> **xlinuks said:**
> If you choose to stay in ignorance - please do so, but don't tell others are wrong.Hmm, there goes my attempt at teaching you....

---

### Post by pmasiar on 2008-06-20
> **xlinuks said:**
> You partially understood me wrong...

Not sure what I misunderstood. You do not dispute any of my claims (because they are valid, and you, as experienced programmer, know it). Optimizing code which spends 90% of the time in library call is meaningless - you need to optimize those libraries, and if you cannot, you should stop being obsessed (like a speed kiddie) on optimizing code which has minimal effect on performance, and focus on speed of development or enhancements.

So your claim that Java code is 20 times faster than Python is equally meaningless, if both programs spend 90% in C-library calls, difference is meaningless.

There are lies, damned lies, and benchmarks. You compare apples to oranges, and kids will pick it up and repeat, without understanding, that "Java is 20 times faster than Python". If I can write Python program 10 times faster, and we use same libraries, I have enough time to try multiple different implementation, and find one which could be faster than your first guess on Java implementation - and even if not, difference in total runtime will be not 20 times, but 5-10% max.

So stop feeding misinformation to speed kiddies. Optimizing parts of code which contribute 10% to runtime is waste of time, admit it, and let speed kiddies focus on what is really important.

---

### Post by Lster on 2008-06-20
pmasiar, I agree with a lot of what you're saying but it *is* very meaningful indeed to claim "Java is 20 times faster than Python". The examples you give concern business and everyday use of a language while programming can encompass so much more.

Your claims also rely on function calls using the bulk of execution time which is often not the case (at least in many things I've seen and programmed).

---

### Post by xlinuks on 2008-06-20
Npl I gave you the book, I'm not gonna spend more time - if you have problems learning and understanding (including assembly) - that's your problem. Why don't you read the book and then come back.

---

### Post by Npl on 2008-06-20
> **xlinuks said:**
> Npl I gave you the book, I'm not gonna spend more time - if you have problems learning and understanding (including assembly) - that's your problem. Why don't you read the book and then come back.stop spreading FUD if you cant back it up yourself. If you cant argue about the points I noted, then bother replying.

---

### Post by xlinuks on 2008-06-20
> **pmasiar said:**
> Not sure what I misunderstood. You do not dispute any of my claims (because they are valid, and you, as experienced programmer, know it). Optimizing code which spends 90% of the time in library call is meaningless - you need to optimize those libraries, and if you cannot, you should stop being obsessed (like a speed kiddie) on optimizing code which has minimal effect on performance, and focus on speed of development or enhancements.

So your claim that Java code is 20 times faster than Python is equally meaningless, if both programs spend 90% in C-library calls, difference is meaningless.

There are lies, damned lies, and benchmarks. You compare apples to oranges, and kids will pick it up and repeat, without understanding, that "Java is 20 times faster than Python". If I can write Python program 10 times faster, and we use same libraries, I have enough time to try multiple different implementation, and find one which could be faster than your first guess on Java implementation - and even if not, difference in total runtime will be not 20 times, but 5-10% max.

So stop feeding misinformation to speed kiddies. Optimizing parts of code which contribute 10% to runtime is waste of time, admit it, and let speed kiddies focus on what is really important.

Please read carefully what I wrote, ok, let me remind you: "about 20 times faster than what you get by default when using Python or Ruby". Java is even sometimes even faster (flash news!). And also have a look at the benchmark I posted on the first page, and do your own (DO YOUR OWN). Remember what I wrote "by default when using Python" - not calling a C or assembly library from Python, we are talking about languages, not about calls to other languages for them to do the job.

> Optimizing code which spends 90% of the time in library call is meaningless Do you really think a program is all about 90% library calls?

I challenge you to write in Python the following code that beats (or is at least on pair with) the Java implementation from:
[http://shootout.alioth.debian.org/gp4/benchmark.php?test=spectralnorm&lang=java&id=0]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=spectralnorm&lang=java&id=0")

The Python implementation is at:
[http://shootout.alioth.debian.org/gp4/benchmark.php?test=spectralnorm&lang=python]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=spectralnorm&lang=python")

Can you rewrite that Python code so that it executes on pair with Java?

---

### Post by The Cog on 2008-06-20
If you read the white papers, you will find that the JVM performs both function inlining and constant hoisting. 
[http://www.google.co.uk/search?hl=en&q=programming+loop+constant+hoisting](http://www.google.co.uk/search?hl=en&q=programming+loop+constant+hoisting)

Arguing that java isn't much faster than python because they both slow down to the same speed if they spend all their time in C libraries is equivalent to saying that a Ferrari isn't much faster than a bus because they might both get caught in a traffic jam.

---

### Post by descendency on 2008-06-20
The question can be answered in one simple phrase: interoperation layer.

All compiled languages run through a layer of execution. Java runs through two layers of execution. One where the interpreter determines what the code is supposed to do and one where the computer actual executes what the interpreter says to do. 

Java fans claim this is nearly nonexistent, but as you can clearly see, it is in fact real and very annoying.

edit: The same thing basically occurs in Mono.

---

### Post by pmasiar on 2008-06-20
> **xlinuks said:**
> Can you rewrite that Python code so that it executes on pair with Java?

If I had real-world situation where such code takes 80% of CPU runtime, I would code that function in C and linked it to Python. In fact, there might be such library for Python - I just do not care to search for it, because I do not need it.

I do not live in ivory tower and prefer to solve real-world problems, not abstract comparisons. Real-world problem solving includes mixing of languages, optimized for a goal, not limited by some abstract "language purity".

So, even if in theory, Python is much slower than Java, in solving practical real world problems, it isn't. At least not order of magnitudes as you suggest. But difference in development time, and future flexibility, is substantial, and skewed heavily towards Python.

This obsession by execution speed of non-significant parts of your code CptPicard calls "speed kiddies", and today I felt like not let it pass unchallenged.

"In theory, there is no difference between theory and practice. In practice, there is."

---

### Post by xlinuks on 2008-06-20
Translation: Python cannot do that that fast, one has to find/write a C library and let that library do the job for Python because otherwise it would be painfully slow.

Have you done any app that does lots of animation with "pure" Python or one has to (once again) pull out a good old C library to do the job for Python?
I mean, have you done anything that I can have a look at and say kinda "cool, I was wrong, Python _can_ be as fast as Java or even faster".

Here's an animation I did with Java (just for fun), can you do that with Python alone - or is it too slow (like I said lots of time before) for something like this and Python needs C's help?

The .jar file runs at double click:
[http://xlinuks.googlepages.com/anim.jar](http://xlinuks.googlepages.com/anim.jar)

---

### Post by LaRoza on 2008-06-20
> **xlinuks said:**
> Translation: Python cannot do that that fast, one has to find/write a C library and let that library do the job for Python because otherwise it would be painfully slow.

Have you done any app that does lots of animation with "pure" Python or one has to (once again) pull out a good old C library to do the job for Python?
I mean, have you done anything that I can have a look at and say kinda "cool, I was wrong, Python _can_ be as fast as Java or even faster".


Python (the most common implementation) is written in C, as are many of its modules. Python is a tool. It is an easy to use tool, and fast to code. It is also easily used with other tools, namely, C. One can use the ctypes in Python, embed C code in the Python code, and write modules in C. 

The point is, speed has to be managed, not micromanaged. pmasiar's saying that most of the waiting is for IO and database/server connections, there is no point in trying to speed it up. Nature itself limits it. For something like animations, Python can be used.

A good old C library is very common in Python. Are you diminishing Python by saying it isn't just all pure Python? Very odd. C is a great language, it is the backbone of the open source world.

---

### Post by xlinuks on 2008-06-20
I said that Python is like 20 times slower, and pmasiar hijacked my words by moving to the usage of other languages through libs: "Optimizing code which spends 90% of the time in library call is meaningless" - I wasn't talking about calling libraries of other langs, but about what these 2 languages can do by themselves and the speed they can perform at.
"a good old C library" I mean that the libraries written in C are good and widely used.

---

### Post by pmasiar on 2008-06-20
> **xlinuks said:**
> Translation: Python cannot do that that fast, one has to find/write a C library and let that library do the job for Python because otherwise it would be painfully slow.

... but all real-life programs use libraries? :confused:

It's other way around. Python programmers live in the world where single-language purity is not of the utmost importance: They accepted that mixing languages is fact of life. They decide to implement most of the application in a language which allows to implement application 10 times faster than "traditional" statically compiled language, because Python runtime system takes care of many issues slowing down "traditional" programmers.

But even if I have to reimplement parts of code in C, I will know (1) exactly which part (2) have stable API (3) do not waste time implementing in static language 90% of the code which speedup will not benefit application as a whole.

BTW you might be surprised that recent advances in compilation suggest that runtime optimization might have better results (because at runtime, we *know* which type is used). PyPy and IronPython are efforts in this direction, and because MSFT can invest a lot into it, and change underlying engine, IronPython's speed after JIT compilation is almost C# (while keeping  all Python's flexibility).

[Dynamic languages strike back](http://steve-yegge.blogspot.com/2008/05/dynamic-languages-strike-back.html)

---

### Post by Quikee on 2008-06-21
> **pmasiar said:**
> 
BTW you might be surprised that recent advances in compilation suggest that runtime optimization might have better results (because at runtime, we *know* which type is used). PyPy and IronPython are efforts in this direction, and because MSFT can invest a lot into it, and change underlying engine, IronPython's speed after JIT compilation is almost C# (while keeping  all Python's flexibility).

[Dynamic languages strike back](http://steve-yegge.blogspot.com/2008/05/dynamic-languages-strike-back.html)

Well yes.. also Sun has [The Da Vinci Machine]("http://openjdk.java.net/projects/mlvm/"), which is a playground for VM features to make the JVM more multi-language and dynamic languages "friendly". 

(Multiple) Coexisting dynamic and static languages on a common VM are the future (and also support for features of functional languages - like continuations for example) - everybody is starting to get this and moving towards this goal.


Also is one of my fellow developers would write..
```
for( int i=myVector.size()-1; i>=0; i-- ) {
//do stuff
}
```
.. (or any other stupid upfront optimization like that) with a excuse that it is presumably faster than the plain and cleaner..
```
for( WhateverObject each : myVector) {
//do stuff
}
```
.. I would just go nuts and slap his head.

---

### Post by xlinuks on 2008-06-21
> .. I would just go nuts and slap his head.
If my boss would do that to me or anyone else I know I would make sure he (if he is lucky) goes to jail, believe me (or I'll just make sure he can't ever do that again by removing the/his (body) parts he used to do that).

And sooner or later you _will_ see code like that so prepare your feeble mind, because (flash news!) sometimes you have to iterate backwards!

---

### Post by Quikee on 2008-06-21
> **xlinuks said:**
> If my boss would do that to me or anyone else I know I would make sure he (if he is lucky) goes to jail, believe me (or I'll just make sure he can't ever do that again by removing the/his (body) parts he used to do that).

Its good that I am nobody's boss.. and my fellow developers are also my friends so even if I would do something like that nobody would sue me.. but anyway this was just an abstraction of how bad I think the idea really is. 

> **xlinuks said:**
> And sooner or later you _will_ see code like that so prepare your feeble mind, because (flash news!) sometimes you have to iterate backwards!

Of course.. what do you think a ListIterator is primarily used for? Also I was referring to do some obscure upfront optimization you were suggesting.

If you have a list of elements and it is a higher chance to find and process the right element iterating backwards I think this is of course OK. But if you do code "optimization" just because the compiler might (or not) produce a more optimal compiled code (in one version.. but who knows what happens in the future version) and sacrifice code cleanses then this is just stupid.

---

