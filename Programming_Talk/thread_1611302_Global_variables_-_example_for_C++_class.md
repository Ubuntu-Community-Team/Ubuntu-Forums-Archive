---
title: "Global variables - example for C++ class"
date: 2010-11-01
forum: Programming Talk
---

### Post by ElofTurtle on 2010-11-01
Unusual as it may be, I'm not a student :lolflag:

However, I would like to get some ideas for when using a global variable may seem like a really good idea, but isn't. Or perhaps the odd case when global variables are handy.

I could easily make some school construct to illustrate a principle in class, but I'd much rather show them something that they could encounter as a real world problem.

Any suggestions are most welcome.

Oh, and I'll write all the code myself, so it is not one of *those* questions :P

---

### Post by dwhitney67 on 2010-11-01
There is never any reason to have a global variable, although one that does stick out is *errno* (from cerrno.h).

As for custom applications, variables should be encapsulated within a class.  So if you are asking for an example where the use of a global variable is justified, well, only a mediocre programmer can help you with that.

P.S.  One could argue that a singleton class object is window-dressing around a global variable.

---

### Post by trent.josephsen on 2010-11-01
You'll find that people define "global variable" differently, and, as with goto, hold different opinions on whether their use is ever appropriate.

N.B. C and C++ don't exactly have "global" variables in the sense other languages do, so the term is usually used to refer to "file scope"; you might read what the standard has to say about scope, which might give you some idea how to better approach this problem.

In C++, (if memory serves) everything is put in a namespace, so "global" has little real meaning.  At least, I suppose, you could make an argument against cluttering up namespaces, but that's a broader topic than just whether and when to use global variables.

---

### Post by worksofcraft on 2010-11-01
I used a global variable today.
It is an integer counter. It is used to generate distinct identifiers for things as they are constructed. It is very handy for diagnostics and also to keep track of where copied items were originally derived from.

Well known global data are things like stdout and cin. Also when programming with a graphical user interface you might want to create a global instance of some class that holds all your widget pointers, because it can get a bit tedious passing them round as parameters all the time.

p.s. if you have people nagging you not to use global variables you can always just "encapsulate" them. So like instead of:
[php]
extern unsigned gIdGen; // to generate sequential identifiers
// and elsewhere
    iD = gIdGen++;
[/php]
you can write:
[php]
unsigned idGen() {
	static unsigned gIdGen = 0; // generate sequential identifiers
	return gIdGen++;
}
// and elsewhere
    iD  = idGen();
[/php]
... see no more global data :shock:

---

### Post by dwhitney67 on 2010-11-02
> **worksofcraft said:**
> Also when programming with a graphical user interface you might want to create a global instance of some class that holds all your widget pointers, because it can get a bit tedious passing them round as parameters all the time.

When implementing a GUI in C++, all child GUI components should hopefully be contained within a parent component.  Of course, there are occasions when the child components have children themselves.  At any rate, each child should be instantiated with a reference to their parent object, or with references to the particular objects necessary for it to operate.  This approach helps mitigate (but doesn't always prevent) child objects having full-access to all other widgets.  It also obviates the need for global variables and/or for singleton objects.

---

### Post by worksofcraft on 2010-11-02
> **dwhitney67 said:**
> When implementing a GUI in C++, all child GUI components should hopefully be contained within a parent component.  Of course, there are occasions when the child components have children themselves.  At any rate, each child should be instantiated with a reference to their parent object, or with references to the particular objects necessary for it to operate.  This approach helps mitigate (but doesn't always prevent) child objects having full-access to all other widgets.  It also obviates the need for global variables and/or for singleton objects.

Your widget call back functions need to be able to find your instances. Gtk solves this by connecting them to pass a single "user data" pointer. It's basically a static instance pointer with an accessor method, which as I explained above is just about the same thing as a global variable with a clumsy interface :D

---

### Post by nvteighen on 2010-11-02
The only good use for global variables is to use them for the only truly global information in any program: report the program's status. That's why errno does no harm.

But as soon as you use a global variable that's going to affect the local behaivor of anything, you're beaking modularity. Any function's behaivor should be predictable only from the arguments it gets passed to and its local variables, not anything else... Otherwise, abstraction gets lost and the code gets more difficult to debug.

---

### Post by korn101 on 2010-11-02
Do you mean Global as in: System Global Variable, or Class/Project Global variable?

---

### Post by ElofTurtle on 2010-11-02
> **dwhitney67 said:**
> There is never any reason to have a global variable, although one that does stick out is *errno* (from cerrno.h).

As for custom applications, variables should be encapsulated within a class.  So if you are asking for an example where the use of a global variable is justified, well, only a mediocre programmer can help you with that.

P.S.  One could argue that a singleton class object is window-dressing around a global variable.
Yes I know most globals are from hell. I was more thinking along the lines of where a student might think
"Oh this is easily solved by putting X outside of main..."
And then do something stupid like calling a function using X inside another function also using X, making a mess.

Korn101: I mean global as in just putting the thing outside main. This is a beginner's programming course, so they won't discover classes and stuff within the scope of the course. 

I know I could go all "THOU SHALT NOT USE GLOBAL VARIABLES OR I SHALL SMITE THEE", but I thought I should at least try to expand their little minds first :P

Thank you all for the ideas - I'll leave the thread on for another day or so, and then I'll begin sieving through the collected forum wisdom ^_^

---

### Post by worksofcraft on 2010-11-02
> **ElofTurtle said:**
> 
...
I know I could go all "THOU SHALT NOT USE GLOBAL VARIABLES OR I SHALL SMITE THEE", but I thought I should at least try to expand their little minds first :P

Thank you all for the ideas - I'll leave the thread on for another day or so, and then I'll begin sieving through the collected forum wisdom ^_^

:D That is very wise... the way to do that IMO is to produce a **practical demonstration**.

Incidentally you might want to point out to them that it's not just a problem of variables that have static allocation. One can equally make a huge mess by passing the same variable by reference to multiple places.

e.g. Recently I made an affine transform matrix and had a method to apply one transformation to another (i.e. operator*= ).

In this case, pass by reference seemed sensible to avoid copying all the matrix coefficients. It passed all my preliminary tests... and failed spectacularly the moment I used it: I had applied the transformation to itself, thus altering matrix coefficients that were still needed for calculating the other coefficients. (I was attempting to rotate a 30 degree rotation by another 30 degrees to be exact) :shock:

IOW the perils of "global scope" is a red herring as it is just a special case of implicit "pass by reference".

---

### Post by worksofcraft on 2010-11-03
ooh... I just used another global variable and it's a big container... decide for yourself if it's justified :P

In my graphics application is the concept of "layers" these are like transparent sheets of paper so you can separate different aspects of your diagram. Each layer has a set of attributes that the user can set, such as whether it is visible or not, and the pen shape, line style, color...

I made a global look up table of the current attributes for each layer so that when it comes to drawing something it can look them up on the fly without having to pass the whole lot around as yet another reference :popcorn:

---

### Post by dwhitney67 on 2010-11-03
Look into the Singleton Design Pattern for one-of-a-kind type of objects.

---

### Post by interval1066 on 2010-11-03
The design goals of C++ are that everything is an object, so anything that needs to be "global" should be an object and put in the global namespace. How well or not you want to stick to this design philosophy is up to you of course, but its kind of bad form to force a C++ design to use global/static data, even if not illegal. There's certainly the odd expedience or exception, but those I find are usually due to bad planning/design. If you're thinking seriously about globals and statics in your design you may want to rethink it and see if plain C might not be better for your application.

---

### Post by worksofcraft on 2010-11-03
> **dwhitney67 said:**
> Look into the Singleton Design Pattern for one-of-a-kind type of objects.

Yes, I googled [Singleton Design Pattern]("http://en.wikipedia.org/wiki/Singleton_pattern") wrt my layer attribute class, but TBH it seems like a lot of extra complication making things hard to follow. Most programmers deal with many disparate languages and have enough problems getting simple things right. So I wonder from a practical point of view just what **does** it achieve over and beyond a straight forward and simple one off global container instance?

As an afterthought, one day I might even want to have two of these containers: That way the user can toggle between current settings and default settings.

As an alternative to a getinstance method it might be better to just have get and set methods for the various attributes and encapsulate the selection of which instance to get and set from... but it all would produce pages and pages of very boring and tedious code that achieve very little IMHO.

---

### Post by dwhitney67 on 2010-11-12
> **worksofcraft said:**
> Also when programming with a graphical user interface you might want to create a global instance of some class that holds all your widget pointers, because it can get a bit tedious passing them round as parameters all the time.

If you design correctly, you would not need to do this.  All one has to do it pass the parent class to the child when it (the child) is instantiated.  The child can maintain a reference to its parent.

For example:
```

class Parent;

class Child
{
public:
   Child(Parent& parent) : myParent(parent) {}
private:
   Parent& myParent;
};

class Parent
{
public:
   Parent() : myChild(new Child(*this)) {}
private:
   Child* myChild;
};

```

---

### Post by worksofcraft on 2010-11-12
> **dwhitney67 said:**
> If you design correctly, you would not need to do this.  All one has to do it pass the parent class to the child when it (the child) is instantiated.  The child can maintain a reference to its parent.

For example:
```

class Parent;

class Child
{
public:
   Child(Parent& parent) : myParent(parent) {}
private:
   Parent& myParent;
};

class Parent
{
public:
   Parent() : myChild(new Child(*this)) {}
private:
   Child* myChild;
};

```

When you get an event on one widget you often want to call methods of other widgets and manipulate data in the application that is not a member of the widget that received the event, nor of any of it's parents. Besides that you may want to restructure the GUI widget hierarchy, so walking up and down hard coded references between them isn't a very good way to do it.

Like say you click the "clear" button: The event call back of that button may have to find some other display widget and wipe that. It may have to find some data container you have been stashing things in and remove all the data items stored in it. It may have to set a flag that will be available when the application exits to prompt the user if he/she wants to save.

What many programmers do is to make a "user data" structure with miscellaneous pointers and flags that gets passed round ALL the call backs... I agree that you can often disguise this to look like a legitimate parameter, but effectively it's just an aggregate of global application data IMO.

---

### Post by dwhitney67 on 2010-11-13
> **worksofcraft said:**
> When you get an event on one widget you often want to call methods of other widgets and manipulate data in the application that is not a member of the widget that received the event, nor of any of it's parents. Besides that you may want to restructure the GUI widget hierarchy, so walking up and down hard coded references between them isn't a very good way to do it.

Like say you click the "clear" button: The event call back of that button may have to find some other display widget and wipe that. It may have to find some data container you have been stashing things in and remove all the data items stored in it. It may have to set a flag that will be available when the application exits to prompt the user if he/she wants to save.

What many programmers do is to make a "user data" structure with miscellaneous pointers and flags that gets passed round ALL the call backs... I agree that you can often disguise this to look like a legitimate parameter, but effectively it's just an aggregate of global application data IMO.

If a child widget needs to interface with a sibling widget, it goes through the parent to get a reference to that sibling, or it could call a redundant method within the parent itself; I prefer the former approach.  Like:
```

void clearCallback(...)
{
   myParent.getSibling().clearInfo();   // go direct to the source

   myParent.clearInfo();   // expect parent to summon sibling
}

```

---

