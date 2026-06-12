---
title: "Object orientated vs structured?"
date: 2010-02-10
forum: Programming Talk
---

### Post by munky99999 on 2010-02-10
Could someone post 2 examples between say C and C++ showing the difference between object orientated vs structured?

I'm teaching myself programming from the guides in stickies. Did C first then C++ now. I guess I dont grasp the difference between the 2. They look so similar with differences being more like syntax differences.

PS. Yes I cant program worth nothing. Only language I'm comfortable with is BASH; pretty simple to use that one :)

---

### Post by SaintDanBert on 2010-02-10
First, don't expect the forums to do your homework if this is a classroom question!!

Second, let me offer some food for thought instead of an answer.
Take a look at the traditional C-language library calls:
[list]
[*]fopen()
[*]fclose()
[*]fread()
[*]fwrite()
[/list]
[http://en.wikipedia.org/wiki/C_file_input/output](http://en.wikipedia.org/wiki/C_file_input/output)

All of these require a **FILE *** (pointer to FILE structure) for their operation. Does this qualify as "object oriented"?  Don't go all academic!! I'm sure that there is a PhD Computer Science definition of "object oriented," but just be practical.

The **FILE** -- actually a typedef for **struct File** or similar -- data structure has all of the attributes needed to do input and output operations, and there are a family of functions -- aka, methods -- that manipulate those attributes. Now other languages, like C++, offer compiler and run-time support to protect you and your data from misadventure and other syntactic sugar.
This feels pretty *object oriented* to me. 

Cheers,
~~~ 0;-Dan

PS/ I'd love to continue this discussion but will not engage in a flame war or similar.

---

### Post by MadCow108 on 2010-02-10
the wikipedia article may help
[http://en.wikipedia.org/wiki/Structured_programming](http://en.wikipedia.org/wiki/Structured_programming)
to the right are loads of links to other paradigms to compare it to

---

### Post by napsy on 2010-02-10
in structured programming, you use functions to modify data. in OO programming data and functions(methods) are combined and together they make a "class". That would be a summary.

---

### Post by nvteighen on 2010-02-10
Well, the thing is that object-oriented programming can't be opposed to structured programming... :p

**Structured programming** is about using local flow control constructs to control execution without allowing to jump between call stacks except by function calls. This roughly means no goto's nor longjmp's... and the use of loops to locally control the execution inside a single call stack. There are some different opinions about whether break's, continue's and exceptions are to be considered structured programming or not... 

**OOP** is basically about modelling your code focusing on data instead of procedures and it's opposed to **procedural programming** (i.e. focus on procedures). The thing is that you create data structures you call structs or classes which group smaller data structures' instances that are somehow interrelated... and then you design procedures to use and/or modify those structures. Procedural programming basically becomes quite unpractical if not impossible when your code starts to grow up... the tendency, because of a human tendency to think in objects, makes you inevitably code in objects... :P

But, don't confuse **syntactic OOP support** with OOP. In C you've got no OOP syntactic support, but a library like GTK+ (or even the C Standard Library itself) is quite easy to recognize as OOP. In C++ and other languages, you get language constructs that make you write OOP code much easily.

Also, don't oppose OOP against **imperative programming** (programming considered as a succession of execution states)... For some reason some people show up confusing imperative and procedural programming and then they oppose it to OOP. No. Usually, people write imperative OOP, but you can have functional OOP (**functional programming** is stateless programming)... or even declarative OOP (HTML + CSS...).

I hope to have cleared things a bit up.

---

### Post by munky99999 on 2010-02-10
> All of these require a FILE * (pointer to FILE structure) for their operation. Does this qualify as "object oriented"? Don't go all academic!! I'm sure that there is a PhD Computer Science definition of "object oriented," but just be practical.
I think I understand this; but how I understand it is that... C programming isnt object orientated but still can interact and have object related actions.


The way I'm seeing it. Typical bash script or C is that you essentially are always running down the program; only moving up the code because of loops. Then when you start to introduce the ability to jump around; it quickly gets out of hand and hard to follow. Making it hard to maintain. So C++ wasnt so much of a increase in capability; but rather just an organization of a mess to allow easier programming; which then makes the degree of capability vs effort relatively higher.

Im probably so wrong :(

---

### Post by MadCow108 on 2010-02-10
> **munky99999 said:**
> I think I understand this; but how I understand it is that... C programming isnt object orientated but still can interact and have object related actions.

Object orientation is a design paradigm. You can do it in any turing complete language (as any other paradigm)
C just lacks dedicated syntax for it.

A simple C object would be a struct with functions dedicated to operate on it. But its a lot messier and less safe (you have less compiler checks like for private members)

There also frameworks for object oriented C like gobject.

For a clean C with object oriented syntax (and without all this complicated C++ stuff) have a look at objective-C or Vala(which is basically just adds syntax for gobject and outputs C code).

---

