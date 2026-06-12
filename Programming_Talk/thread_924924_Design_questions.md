---
title: "Design questions"
date: 2008-09-20
forum: Programming Talk
---

### Post by hoboy on 2008-09-20
I have problem, I have learned Java syntax, but still I am a poor programmer, the reason I have found is that I am a very poor program designer.
I need a advices--links--tutorials-- in short a help from other programmers what did you do to pass this stage of your programming learning,please help me with your experiences.
As I am poor designerit makes me a poor code.
I want to understand program design.
Any suggestion is very welcome.
How do I define what is an interface in a given problem ?
How do I dicide if a method should take a parameter/parameters.

---

### Post by Reiger on 2008-09-20
Well in Java the idea of an interface is that you define 'what methods you' have for a given 'type'. The benefit is that you can create methods that operate on anything which implements the interface and that you can rely on the interface-methods to be available. Essentially interfaces work like an API: you say "I don't know how you should do it, but I do know that you do it; so I can count on you to do that for me."

This is useful if you have a (potential for a) lot of similar cases but details differ subtly from one case to another. For instance if you were writing a paint like program you may find that the difference between a filled rectangle and an empty rectangle is not that great. Just a call to a different AWT.Graphics method. And similarly you may have tools for a line and for an empty circle and for a filled circle.

Now instead of writing 4 or 5 different classes for that one (and future, not yet implemented tools); you could also define an interface:

```

/* imports required?... */
public interface PaintTool
void update([params]); // when drawing an as of yet unfinished thing
void createIcon([params]); // the sample in the GUI
void paint([params]); // the finished product
void restore([params]); // if redo is pressed, or if loaded from a save
[Object] p1; // the origin of the object
[Object] p2; // the end of the object
void getDimensions([params]) // getting the dimensions of the object...
/* further things required? ... */

```

You still have to write classes to do the actual work, but in the future you can easily integrate new tools which must conform to the interface. All you need to do is add the appropiate (subclasses) and update your GUI -- and it is (provided your future code does its stuff correctly) guaranteed to work.

And you can imagine such interface definitions greatly help with 'plugins' for you application. Your application cannot know the how and what but your application can define an interface and rely on the plugin to conform to the interface:

```

/* imports? */
public interface Plugin
void configure([params]); // pass configuration stuff to the plugin?
void deferTo([params]); // defer work to the plugin?
[Object] getSetings([params]); // get settings if updated to write to config file
[Object] getInput ([params]); // get data to perform input handling for the plugin
[Object] getOuput ([params]); // get data to perform output handling for the plugin
void kill (); // quickly finish off a misbehaving plugin?
[Object] start(); // start doing things; and return output about errors...?
/* further methods? */

```

---

### Post by Reiger on 2008-09-20
Part two: methods.

Well first of all if you think of a method you know roughly what you want it to do right?
Say you were writing something to implement/simulate a Queue. You would need something to represent your Queue, right?

So you would need a bunch of methods that do:
```

void add([params]); // add things to (end of) the queue
[Object] serve(); // a Queue always is FIFO, therefore serve which returns the FI element doesn't need data to determine what to return...
int size(); // at times you want to know what size your Queue has ... but do you need params to determine it?
String toString(); // you may want to dump the entire Queue to a String?
void fromString(String s); // reading a Queue from a string...?
boolean isEmpty(); // you may need to know that...?

```

Essentially the params you pass to a method is the data the method should operate on (requires). The data you get greatly depends on 'what' you want it to do, but also 'what you wish to use it for'. I.e. if you wish to do something on the entire Queue you may write:
```

while(! myQueue.isEmpty()) {
    [Object] o = serve();
    [expression] doStuffWith(o);
}

```

From that idea (data passed is the data required) it is a bad idea to use globals for each and every thing. They aren't evil but it is difficult to debug methods which rely on data that can be modified at any time at any place inside any method of its object.

---

### Post by hoboy on 2008-09-20
> **Reiger said:**
> Part two: methods.

Well first of all if you think of a method you know roughly what you want it to do right?
Say you were writing something to implement/simulate a Queue. You would need something to represent your Queue, right?

So you would need a bunch of methods that do:
```

void add([params]); // add things to (end of) the queue
[Object] serve(); // a Queue always is FIFO, therefore serve which returns the FI element doesn't need data to determine what to return...
int size(); // at times you want to know what size your Queue has ... but do you need params to determine it?
String toString(); // you may want to dump the entire Queue to a String?
void fromString(String s); // reading a Queue from a string...?
boolean isEmpty(); // you may need to know that...?

```

Essentially the params you pass to a method is the data the method should operate on (requires). The data you get greatly depends on 'what' you want it to do, but also 'what you wish to use it for'. I.e. if you wish to do something on the entire Queue you may write:
```

while(! myQueue.isEmpty()) {
    [Object] o = serve();
    [expression] doStuffWith(o);
}

```

From that idea (data passed is the data required) it is a bad idea to use globals for each and every thing. They aren't evil but it is difficult to debug methods which rely on data that can be modified at any time at any place inside any method of its object.

Sir tks for your time.
specially santance like "Essentially the params you pass to a method is the data the method should operate on (requires). The data you get greatly depends on 'what' you want it to do, but also 'what you wish to use it for'. I.e. if you wish to do something on the entire Queue you may write:
" helps to clarify my problem,witch is the decision taking process of defineing a method, its parameters.

---

### Post by tinny on 2008-09-20
You need to approach program design in a way that focuses on the problem you are trying to solve. Start with a top down approach and keep the problem in the forefront of your mind at all times (Dont get hung up on the code). For me java design is all about object decomposition, breaking real world things and processes down into software objects. [UML]("http://en.wikipedia.org/wiki/Unified_Modeling_Language") is a tool that I think would be worth while for you to learn. UML allows you to model these real world things into a sort of blue print that maps nicely to software objects.

You should also learn from more senior programmers code by reverse engineering it (E.g. have a look on sourceforge etc..). 

TIME, this skill of design can take time to acquire. Just keep practicing and you will get there.

---

### Post by CptPicard on 2008-09-20
Unfortunately, this is why static-typed OOP languages like Java are problematic -- you are forced into learning a lot of "design methodology" which is IMO a bit of a black art and can actually be pretty remote from the problem itself when you are trying to come up with the kinds of objects that would model the *problem* in terms of the *facilities of the language*.

I really like duck typed and functional programming and very flexible, generic languages like Lisp for this reason -- you can model more directly in terms of the problem than when you have to cast everything into objects in inheritance tree that then "own the verbs" and encapsulate data. As I like to say, Lisp is essentially an art of directly mapping the abstract syntax tree of your language to problem structures.

I'd have to say "God please no" to the UML suggestion... :) Considering the OP is having issues with figuring out method parameters, he's still very much a beginner... maybe even getting to grips first with Python wouldn't be too bad an idea.

But if Java it is, a good hand-holding IDE that autocorrects and refactors for you will probably help with the design process. I went through something like this a long time ago and didn't really even consider programming much fun anymore as I knew exactly how the problem itself is solved, but was pretty bad at the OOP-design parts of actually implementing anything. Then, through a lot of exposure to "design patterns" and usage of Eclipse and Netbeans, I can these days pretty directly think in terms of objects... which is not necessarily a good thing really, but a kind of perversion of the mind :p

---

### Post by tinny on 2008-09-20
> **CptPicard said:**
> 

I really like duck typed and functional programming and very flexible, generic languages like Lisp for this reason -- you can model more directly in terms of the problem than when you have to cast everything into objects in inheritance tree that then "own the verbs" and encapsulate data. As I like to say, Lisp is essentially an art of directly mapping the abstract syntax tree of your language to problem structures.


Domain specific languages (DSL), right? Do you think DSL is easier to learn than good old tree based OOP? Im finding DSL quite tough right now, but perhaps thats just because ive been thinking in obsessive OO for so long?

> **CptPicard said:**
> 
I'd have to say "God please no" to the UML suggestion... :) Considering the OOP is having issues with figuring out method parameters


Yeah, got to learn some syntax and basic constructs first. After learning this I think a little UML will help, just basic class diagrams and maybe use cases. But dont go to far into UML. (UML if you want to be a Java coder)

---

### Post by CptPicard on 2008-09-20
> **tinny said:**
> Domain specific languages (DSL), right? Do you think DSL is easier to learn than good old tree based OOP?

In a sense, yes... in the sense that having to cast everything into objects and to manage the type system before you can accomplish anything is harder than having something that potentially gives you a DSL (once you muck around in it long enough).

I find that the DSL mantra in Lisps is just a little bit overhyped... you don't go out of your way to always specifically design a DSL for your problem. However, Lisp tends to guide you towards structuring problems in ways that tend to often quite naturally yield something like a DSL.

---

### Post by nvteighen on 2008-09-20
The interface is something that connects two (or more) layers of abstraction and usually it only works in one direction (from layer A->B, generally A is less abstract than B). 

The implementation is the code connected by the interface. 

So, designing interfaces is to design a barrier between some parts of code and separate them, but also giving some doors to let them communicate. A usual approach I do is: if I have code A and B, and A calls functions/methods from B, I look what functions in B are not called in A in any context and mark those as "private" (not in the Java sense, but in the sense that I let them out from the public interface).

In other words, good code generally codes "everything as a library" except maybe for the most top levels. That ensures a lot of benefits like modularity, reusability, etc. At the end, you have a stack of APIs that let you build the code as it was some kind of LEGO bricks tower (or pyramid), where the interlocking studs are the interfaces.

---

### Post by nvteighen on 2008-09-20
> **CptPicard said:**
> 
I really like duck typed and functional programming and very flexible, generic languages like Lisp for this reason -- you can model more directly in terms of the problem than when you have to cast everything into objects in inheritance tree that then "own the verbs" and encapsulate data. As I like to say, Lisp is essentially an art of directly mapping the abstract syntax tree of your language to problem structures.

But the good thing at Lisp is that it doesn't either force you to that way of programming and you can have the best of all worlds!

---

### Post by the_unforgiven on 2008-09-20
In my opinion, designing of software and coding of software are two separate issues and what the OP is struggling with is designing - i.e. understanding how various pieces from the problem domain need to be mapped to programming domain. 

At this level, I think, the language is the least of a concern; if [s]he's struggling with basic design, the coding is going to be equally difficult no matter what language.

Unfortunately, design is more of creative and subjective work and there are no fixed set of rules of the trade. So, each one can have his/her own way of designing software.

@OP:
The most basic principle in software design is understanding the problem that you're trying to solve and mapping the "objects" (i.e. entities - not necessarily objects in the object-oriented programming) from the problem domain to the application domain.

This gives you an idea as to how various entities in the problem are to be modelled - i.e. how these entities interact with each other.

Once you understand the problem domain, you will automatically realise what interfaces you need, what methods to write and what parameters these methods should take.

For starters, you can take a look at:
[http://en.wikipedia.org/wiki/Software_design](http://en.wikipedia.org/wiki/Software_design)

HTH ;)

---

### Post by heikaman on 2008-09-20
Hello...

I recommend **Design Patterns** by Erich Gamma ISBN 0-201-63361-2

I think the most useful rule I learned from this book is to code to an interface NOT to a concrete class.
 
Good luck. :popcorn:

---

### Post by Sorivenul on 2008-09-20
> **heikaman said:**
> I think the most useful rule I learned from this book is to code to an interface NOT to a concrete class.
+1 to this.  Also, +1 to the use of UML.

---

### Post by pmasiar on 2008-09-20
You can learn how to do good design from reading sources of good design. Problem with Java is that with language so verbose, it takes skills (== time) to be able to read source and see the design behind it.

Also to be able to read beyond plain syntax, you need to learn more languages (to be able to see commonalities and different ways to express same concept: so you can see what is inherent complexity and what is just quirk of a syntax of particular language).

As CptPicard mentioned, duck-typed (dynamically typed) languages are substantially less verbose, so design is easier to see (and many pattern of statically typed languages are not needed at all). Learn Python and Lisp: you will be more competent programmer, and core capable to see concepts behind lines of code.

And read more advanced books about languages: Head-first series has excellent books about patterns (hands down best intro ever) and OO design. Then read more. Pragmatic Programmer is excellent series, as is Code Complete (best book published by MSFT). I have whole thread with links to advanced readings, dig it out (and post here if you like it).

---

