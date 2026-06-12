---
title: "why is one language &quot;slower&quot; than other ?"
date: 2008-06-28
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-28
i had previously questioned the efficiency of one language (java) over the other ( basically python).
various arguments were given , and almost all of them gave practical examples of which "brand" uses which language/tool.

but here i would like to know, the "why" behind all these differences, that is , both python and java being interpreted languages, "why" is one efficient over the other ?
please answer these questions NOT as the user of the technology , but as a developer of the technology.

---

### Post by Phristen on 2008-06-28
Python is supposed to be "simpler", so there is a lot more abstraction...
More abstraction = slower code :)

Besides, early versions of java were slow as hell, too, so maybe python will get better with time.

---

### Post by -grubby on 2008-06-28
Python is an interpreted language. Some other languages are compiled languages. A world of difference in speed. But also, not having to compile every time you make a change is great. Not that I have any experience in compiling

---

### Post by LaRoza on 2008-06-28
> **dexter.deepak said:**
> 
but here i would like to know, the "why" behind all these differences, that is , both python and java being interpreted languages, "why" is one efficient over the other ?
please answer these questions NOT as the user of the technology , but as a developer of the technology.

It depends on what you are measuring. Java can be slow for certain tasks as well.

For many tasks, speed isn't a problem. Look at browsers for instance, a common type of application. Three browsers written in C, Python and Java wouldn't be much different (assuming they used the same engine) because most of the time a browser just sits there, and the only "speed" would be in rendering the page, where the backend is used (which is written in a lower level language).

So the "speed" question is really "Is it worth the time to speed this up?". The "time" being the time it takes to write. 

> **Phristen said:**
> Python is supposed to be "simpler", so there is a lot more abstraction...
More abstraction = slower code :)


Python isn't that slow. IronPython is actually faster than CPython I hear.

---

### Post by LaRoza on 2008-06-28
> **nathangrubb said:**
> Python is an interpreted language. Some other languages are compiled languages. A world of difference in speed. But also, not having to compile every time you make a change is great. Not that I have any experience in compiling

Java and Python (and Perl) are compiled to byte code then run.

---

### Post by CptPicard on 2008-06-28
> **dexter.deepak said:**
> 
but here i would like to know, the "why" behind all these differences, that is , both python and java being interpreted languages, "why" is one efficient over the other ?

Modern Java is not interpreted, it's JIT-compiled. This is what mostly is responsible for the speed boost.

But in general, yes, the runtime speed difference is due to the abstraction layer present in the interpreter, whichever form it takes.

> please answer these questions NOT as the user of the technology , but as a developer of the technology.

That's gonna be hard, I am neither Guido van Rossum or James Gosling... sorry. You may have to ask them directly :)


> **Phristen said:**
> Python is supposed to be "simpler", so there is a lot more abstraction...
More abstraction = slower code :)


Perhaps the latter is true, but I have to take some issue at the "simplicity" thing... actually, some of python's more abstract concepts are not "simpler" in a straightforward sense... they are just more... abstract :) Java is on the other hand a very simple language as far as constructs go.

---

### Post by Npl on 2008-06-28
java is typically compiled (the first time code is used - valled Just-In-Time Compiler), not interpreted (though thats also possible). This puts its ahead of interpreted languages.

---

### Post by -grubby on 2008-06-28
> **LaRoza said:**
> Java and Python (and Perl) are compiled to byte code then run.

Oh, I didn't know that counted as compiling

---

### Post by LaRoza on 2008-06-28
> **nathangrubb said:**
> Oh, I didn't know that counted as compiling

Well, gcc compiles to assembly code (which is then assembled and linked). Python compiles to an assembly code as well (which is easy to read, actually) and Java does as well.

---

### Post by luisito on 2008-06-28
Python compiles to platform independent byte code. It is not the same as the JIT-compiling of Java, which is into native machine code. This is why java is so much faster than python. See [http://en.wikipedia.org/wiki/Just-in-time_compilation](http://en.wikipedia.org/wiki/Just-in-time_compilation).

---

### Post by LaRoza on 2008-06-28
Rats. I should have waited before posting. Don't worry, someone will come along shortly to do a little housekeeping.

---

### Post by LaRoza on 2008-06-28
> **luisito said:**
> Python compiles to platform independent byte code. It is not the same as the JIT-compiling of Java, which is into native machine code. This is why java is so much faster than python. See [http://en.wikipedia.org/wiki/Just-in-time_compilation](http://en.wikipedia.org/wiki/Just-in-time_compilation).

"So much faster" isa bit misleading. When is the speed of Java significant?

[http://www.ferg.org/projects/python_java_side-by-side.html](http://www.ferg.org/projects/python_java_side-by-side.html)

The Java platform is the important part.

---

### Post by dwhitney67 on 2008-06-28
Is it just me, or are these type of questions becoming increasingly annoying.

Dexter - Please do your own research, or place your questions in one of the forums of the Community Discussion area ([http://ubuntuforums.org/forumdisplay.php?f=175](http://ubuntuforums.org/forumdisplay.php?f=175))

Personally, I think you probably have already done sufficient research before asking your questions, and are merely trolling for answers from others, perhaps seeking to affirm your conclusions.  Damn... get a life!

If you have a programming questions, please present your code for review, and maybe someone can help you.

I hope the moderators will see my point of view that this forum cannot serve as your personal Comp-Sci 101 forum.

[/rant]

---

### Post by xlinuks on 2008-06-28
> **LaRoza said:**
> Rats. I should have waited before posting. Don't worry, someone will come along shortly to do a little housekeeping.
I would suggest deleting (or closing) this post ( I mean thread) since the man who posted it evidently didn't even bother searching a bit the internet before posting.

---

### Post by LaRoza on 2008-06-28
> **xlinuks said:**
> I would suggest deleting (or closing) this post since the man who posted it evidently didn't even bother searching a bit the internet before posting.

Surprisingly, most people don't on this forum.

Most of my "beans" are from "read the stickies". Following the Ubuntu Code of Conduct is mandatory at all times. 

It would be nice if everyone read "How to ask questions" by ESR (see the link in my sig under articles), but only the CoC is important (see Codes of Conduct link)

---

### Post by lisati on 2008-06-28
Assembled? Compiled? Interpreted? "Just in time compilation"? Byte Code? Something else? Some combination of methodologies?
I'm surprised no-one has mentioned microcode!

---

### Post by dexter.deepak on 2008-06-28
i am extremely sorry for this behaviour of mine.
actually the discussions you people make, give me a  lot of useful links to help me understand a lot lot better.
but if it's a matter of pain to the community....i will change my way.
thanks for the advice.

---

### Post by LaRoza on 2008-06-28
> **dexter.deepak said:**
> i am extremely sorry for this behaviour of mine.
actually the discussions you people make, give me a  lot of useful links to help me understand a lot lot better.
but if it's a matter of pain to the community....i will change my way.
thanks for the advice.

It is not a problem to ask questions :-) That is why the forum exists.

In case you aren't use to it, Wikipedia.org (which has many languages) is a great source of information.

---

### Post by tiachopvutru on 2008-06-28
I wonder if his question is actually "Why is one language 'slower' than other when they eventually become 0 and 1 anyway?"

If that's the case, I'm curious as well... Even if you explain that you gotta compile this, interpret that, and that there are some abstraction layers... it's still, well, abstract explanation.

The answer is probably going to be complicated, though.

---

### Post by CptPicard on 2008-06-28
> **tiachopvutru said:**
> I wonder if his question is actually "Why is one language 'slower' than other when they eventually become 0 and 1 anyway?"

Because for some languages there are more steps involved before they do become 0s and 1s :) Simple...

---

### Post by LaRoza on 2008-06-28
> **CptPicard said:**
> Because for some languages there are more steps involved before they do become 0s and 1s :) Simple...

...and 0's and 1's are just abstractions themselves.

---

### Post by lisati on 2008-06-28
> **tiachopvutru said:**
> I wonder if his question is actually "Why is one language 'slower' than other when they eventually become 0 and 1 anyway?"

There are a couple of things which can contribute:

[LIST]
[*]The main difference between "compile" and "interpret" is when the translation is done. "interpret" is usually done when you run the program, and has to be done over and over each time you you run it. "Compile" is usually done "once" before the program is done, assuming there are no bugs to fix the translation doesn't need to be repeated.
[*]The main difference between "compile" and "assemble" is the level of abstraction involved - Assembled languages are generally closer to the native binary than compiled langauges
[*]There are different ways of translating source into native binary: it's theoretically possible to take the exact same source code, run it past different compilers (or use different options on the same compiler) and get different binary files that are functionally equivalent.
[/LIST]

---

### Post by pmasiar on 2008-06-28
> **xlinuks said:**
> Can people in India use the wikipedia?

Can people with "Location: Heaven" behave like angels? :-)

Unless you are God (or mod: almost the same thing :-) ) you should not judge others, IMHO.

Most of people do not read FAQ and do research, that's sad fact of life. Just suggest wikipedia page and "how to ask questions smart way" (see my sig).

@OP: no need to feel bad about your question. Most people learn by mistakes (some rather embarrassing), trick is not to avoid mistakes by any cost (thus hamper the learning): trick is to learn from mistakes, not repeat them, and help others to avoid them.

Back to topic:

Performance (on same CPU) is based what CPU is doing. Difference between Java and Python is not as much in compiling, but in dynamic typing: Java is statically typed, and compiler can solve all casting problems (or better, forces programmer to track and handle casting). With Python, type information is checked at runtime, and only at runtime is decided what exactly '+' (or any other method/operation) means. This of course adds work for CPU, but it dramatically simplifies programmer's tasks. No more that ugly casting code all over the place, compare:

[php]
HashMap gene = (HashMap)genes.getItem(i); // Java
gene = genes[i] # Python

# or even the 'loop through the collection' version:
for gene in genes: # Python
   # use gene here
for(Iterator ..... // !@#$% Java, I cannot do it without the IDE
[/php]

As speed of CPU increases, price drops, and it idles most of the time anyway, it increasingly makes more sense to offload more work to the CPU.

[The hundred year language](www.paulgraham.com/hundred.html) (forces governing evolution of languages in next 100 years, and possible results)

Read also [Dynamic Languages Strike Back](steve-yegge.blogspot.com/2008/05/dynamic-languages-strike-back.html) - essay about problems with JIT in JVM, and progress of JIT compilers for dynamically typed languages. Summary: best info about the variable's type is available at the runtime, and runtime JIT compilers can do much better optimization of the code than static compilers. Compilers for Python are also available, but not used too much, because in most cases it makes little sense: If 90% of the program runtime is spend in library calls to database, network calls, disk access and stuff, no matter of code speedup will change that.

Benchmarks often misleadingly measure speed of single inner loop of something which works as a part of complex system. Python's approach is to build app quickly, profile performance, and optimize bottlenecks you found based on real data, not on your wild guess and bias. Optimize by redesigning algorithm, or recoding little part as C library.

---

### Post by LaRoza on 2008-06-28
> **pmasiar said:**
> 
Unless you are God (or mod: almost the same thing :-) ) you should not judge others, IMHO.
sabdfl is like Azathoth. ubuntu-geek is like Nyarlathotep. Admins are like Yog-Sothoth, mods are like Cthulhu, a few other minor mod categories are like the Deep Ones, and the average forum member is like  the Cult of Dagon.

Blub programmers and banned people (with the exception of Lars) are like the typical human.

---

### Post by Phristen on 2008-06-28
> Performance (on same CPU) is based what CPU is doing. Difference between Java and Python is not as much in compiling, but in dynamic typing: Java is statically typed, and compiler can solve all casting problems (or better, forces programmer to track and handle casting). With Python, type information is checked at runtime, and only at runtime is decided what exactly '+' (or any other method/operation) means. This of course adds work for CPU, but it dramatically simplifies programmer's tasks. No more that ugly casting code all over the place, compare:Oh, please, Java has a foreach loop too nowdays, as well as generics (which takes care of most of the casting ugliness).

---

### Post by days_of_ruin on 2008-06-28
> **luisito said:**
> Python compiles to platform independent byte code. It is not the same as the JIT-compiling of Java, which is into native machine code. This is why java is so much faster than python. See [http://en.wikipedia.org/wiki/Just-in-time_compilation](http://en.wikipedia.org/wiki/Just-in-time_compilation).
If you are using intel chips there is a JIT for python called psyco.

---

### Post by CptPicard on 2008-06-28
> **Phristen said:**
> Java has a foreach loop too nowdays, as well as generics (which takes care of most of the casting ugliness).

Java's foreach loop is mere syntactic sugar on top of Iterators, in Python "iterability" goes very deep. Java has a good start in its loop though.

Now, as far as generics go... Python's genericity is again a much deeper feature that has to do with the idea of protocols (such as the iteration protocol). Java's Generics are nothing but essentially sort of type variables with optional inheritance constraints. I get the impression that you just have to fight the type system more with them, instead of less.

Python's genericity really is something you have to experiment and work with to understand its benefits :)

---

### Post by Phristen on 2008-06-28
Yeah, but this wasn't my point.
I was saying that Java has all the same syntax sugar (dispite pmasiar's argument), and yet it is faster.
> in Python "iterability" goes very deepWell, how deep exactly does it go, I wonder?
Java's iterators are quite efficient, what else can you do besides hiding them in a nice foreach loop?
> I get the impression that you just have to fight the type system more with them, instead of less.I have no such impression. I know Java uses erasure to deal with generics but nevertheless it makes programming so much easier.
Although there is definitely a lot of room for improvement, as far as performance goes... One of the reasons for such implementation though was to keep compatibility with older versions of java.

---

### Post by CptPicard on 2008-06-28
> **Phristen said:**
> Yeah, but this wasn't my point.
I was saying that Java has all the same syntax sugar (dispite pmasiar's argument), and yet it is faster. ...
Well, how deep exactly does it go, I wonder?

The whole point is that anything that fulfills the iterator protocol (i.e. behaves as an iterator) can be used in the for loop, which is, interestingly, the only for loop. So we get conceptual economy there. For example a lot of stuff can be modelled in just terms of list comprehensions and the for-in loop.

Python is full of duck typing like this. You do not need explicit interfaces as long as you can just "do something" on some object and it can respond to whatever you request it to do.

Ok, so far so good, you could implement the Iterator interface in Java and get similar effects (although it would result in a less straightforward modelling).

The best Python feature related to this are certainly generators. They are almost  close to being continuations, but aren't quite, unfortunately... with a generator "yield" you can just store a state of a computation, which then acts as an iterable. Each time you "next" the iterator, you just resume where you left off.

> I have no such impression. I know Java uses erasure to deal with generics but nevertheless it makes programming so much easier.

... and my impression is that Java's generics just make me architecture so much more, because now there are not only the OOP problems, but generics-type-mismatch problems.. :p

The really useful genericness isn't explicit, but implicit -- stuff is only really usefully generic if you don't have to *explicitly be managing all the type relationships* but it just happens automatically because of the assumption that if you make some object have some behaviour, then it can me automatically made use of. This is interestingly expressed to a degree even in the Java doctrine of "programming to interfaces", and not really even trying that hard to create inheritance hierarchies of actual classes.

But of course it's something one has to make use of to really appreciate. I willingly admit I didn't quite get it myself either before I got into Python and Lisp :)

> Although there is definitely a lot of room for improvement, as far as performance goes...

I frankly am not too concerned regarding the last bits of performance. I can use C if I really need it, otherwise I am more interested in the abstractions I am able to construct using any language I'm using. :)

---

