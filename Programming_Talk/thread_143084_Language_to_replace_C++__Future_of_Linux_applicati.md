---
title: "Language to replace C++ / Future of Linux application programming"
date: 2006-03-11
forum: Programming Talk
---

### Post by kar-tar on 2006-03-11
C++ looks to be fading away.

Both C# are Objective C are much stronger, more modern, and better designed languages, and Microsoft and Apple (respectively) are pushing hard for their developers to move away from C++ for developing large, graphical, desktop applications.

What compiled, object-oriented language do you think is likely to replace C++ as the Linux development language of choice?  Or does free software have legacy issues that will keep C++ around in our world much longer than in theirs?

Personally I'd really like to see Linux development moving to Objective C.  It's a really nice language, if you aren't familiary with it, it's basically a relatively elegant addition of the SmallTalk object model ontop of C.  (That is to say, unlike in C++, C is a proper subset of Objective C, you can write any traditional C program and compile it with an objective C compiler and it will work.

However, it seems like there will likely be a lot more developers with C# experience, and so, it's likely that a lot of new GPL projects will be in C# (unless I'm missing something and there's some patent issue with C# that will make that impossible), especially since the C# community looks to be doing everything it can to make the migration from java to C# as easy as possible.

Or is there perhaps some other language that could move in to take C++ place.

I've never much liked C++, it's always seemed to me to be a shotgun approach at addressing the shortcomings of C, rather than a well-designed solution.  It's done its job well for a couple of decades now, but better languages are finally stepping up to the plate.

What will I need to know to work on a GPL desktop app project 5 years from now?

I'd love it if the answer turned out to be bytecode Ruby, but that seems unlikely.

---

### Post by hw-tph on 2006-03-11
There is no one language that fits all purposes. Writing more or less advanced applications for Gnome/GTK can be done pretty quickly with Python and wxPython. And yes, I know Python is not a compiled language but it certainly is object oriented and modern.

Good old C won't go away, neither will C++. And the new breed of scripting languages like Python and Ruby will only gain momentum and use. And I don't see Objective C enjoying much use outside the Apple world.


Håkan

---

### Post by atoponce on 2006-03-11
Objective C is nice until you find out there is no garbage collection, and it is NOT a user-friendly programming language.

---

### Post by sapo on 2006-03-11
[QUOTE=hw-tph]There is no one language that fits all purposes. Writing more or less advanced applications for Gnome/GTK can be done pretty quickly with Python and wxPython. And yes, I know Python is not a compiled language but it certainly is object oriented and modern.

Good old C won't go away, neither will C++. And the new breed of scripting languages like Python and Ruby will only gain momentum and use. And I don't see Objective C enjoying much use outside the Apple world.


Håkan[/QUOTE]
Just a correction, gnome/gtk can be done with pygtk, wxpython is kinda different and is more recommended for cross-plataform development, cause it uses the default look of the OS, windows, Mac, Linux, etc.

I personally advice the use of pygtk, i ve tried wxpython, its great, but its  support and documentation are still very poor, sometimes you find yourself in a dead end and dont have anybody or any place to get help.

Currently i m very happy with pygtk, you can read more about it here: [www.pygtk.org](www.pygtk.org)

---

### Post by engla on 2006-03-11
[QUOTE=atoponce]Objective C is nice until you find out there is no garbage collection, and it is NOT a user-friendly programming language.[/QUOTE]
What is the issue with user-friendliness?


I really like Obj-C, its only drawback really is the very small spread and portability (only OS X and GNUStep are "native" platforms)

I don't think the lack of garbage collection is a problem; I've written quite a few small projects in Obj-C, and I generally like the memory model. It's not very hard when you get used to it and know how to handle it.

---

### Post by gord on 2006-03-11
no user-friendlyness meens that lots of people won't use it and will use something that has good user friendlyness (see: python, ruby and the lot). id estimate that thngs will go more down the c# road than this objective-c.

im just gonna keep doing things in my loverly python, if other people want to use other stuff thats fine. tis one of the great things about the programing language landscape. theres so much choise :)

---

### Post by rplantz on 2006-03-12
[QUOTE=gord]no user-friendlyness meens that lots of people won't use it and will use something that has good user friendlyness (see: python, ruby and the lot).[/QUOTE]

"User-friendly" is largely in the eye of the beholder. I learned how to program in assembly back in the 1960s. I've used it extensively on projects ranging from a CT scanner to a shipping container handling system. I still like C a lot because I can get close to the machine. There are times when I can get the job done faster in assembly.

I have a friend who had trouble with Pascal (back in the early 80s). He said that when he saw lisp, it all came together for him. I've tried lisp several times. Just hasn't clicked for me.

I've used C++ and java in an academic setting, and I've played with objective-C. Of these, C++ is easiest for me, but I'm quite sure that's because I learned it before the other two.

A colleague recently asked if I could think of a shell script that would limit the length of time a program would run. I'm a rank beginner at scripting. The C program was a snap for me. My current project is learning ruby. I've just started and have already run into an example in the rubybook that doesn't work. I could easily write it in C.

"User-friendly" is often equivalent to "familiar." It's rare that we see a new design that appears user-friendly to a majority of people. We are creatures of habit.

---

### Post by LordHunter317 on 2006-03-12
[QUOTE=kar-tar]C++ looks to be fading away.[/quote]No, it isn't.

> Both C# are Objective C are much stronger, more modern, and better designed languages,You're wrong on all three counts. Both are notably less expressive, both aren't more modern and neither was better designed.  C# is arguably worse than C++ (cribbed from Java, which is pretty much the star case of how not to design a language by committe) and Objective-C is certainly no better, though it's not really worse in terms of design per se.   Objetive-C isn't more popular, either.  Only Apple uses it, and that's far fewer people than those who use C++.

And w.r.t to GUIs, Objective-C doesn't have a *cross-platform* GUI in widespread use, and my understanding is that making Cocoa cross-platform would be extraordinarly difficult.  It's extermely tightly tied to the Apple way of doing things, which is very difference from the X11 and Windows way (Win32s and X11 share more in common than one might think).

[qoute]What compiled, object-oriented language do you think is likely to replace C++ as the Linux development language of choice?[/quote]Maybe C#.  Doubtful for the next several years.  I really wouldn't want it replaced, C++ is superior for these sorts of things IMO.

> Personally I'd really like to see Linux development moving to Objective C.  It's a really nice language, if you aren't familiary with it,No, it's really a terrible language with tons of limitations.  It does nothing to relieve the pain of unmanaged memory (even C++ manages this extremely well) and adds very slow and complicated dynamic binding that turns out to just not be that useful for really nifty things that often.  GUIs just don't benefit from it, and the non-GUI code takes a terrible performance penalty.

> I've never much liked C++, it's always seemed to me to be a shotgun approach at addressing the shortcomings of C, rather than a well-designed solution.It never was really meant to address C's shortcomings, but augment them.

Unforuntately, that mindset has lead to some bad design choices.  But no worse than C# or Java or Objective-C.  And at least it has a class library that's worth using, as opposed to the other three.

> I'd love it if the answer turned out to be bytecode Ruby, but that seems unlikely.Ruby isn't ready for the enterprise.  Ruby 2.0 may be, but it's still lacking some very core and fundamental features that are just requirements these days (e.g., Unicode support).


[quote=engla]I don't think the lack of garbage collection is a problem; I've written quite a few small projects in Obj-C, and I generally like the memory model. It's not very hard when you get used to it and know how to handle it.[/quote]It's harder than every other language mentioned other than C.

---

### Post by atoponce on 2006-03-12
[quote=engla]What is the issue with user-friendliness?[/quote] Personal opinion.  For some reason, C++ just clicks with me.  Objective C doesn't.  I find myself writing more code, in many cases, to accomplish the same task.  Personally, I just avoid it.  I don't code much in Objective C because of the "aftertaste" it leaves.

---

### Post by tbrownaw on 2006-03-12
[QUOTE=kar-tar]C++ looks to be fading away.

Both C# are Objective C are much stronger, more modern, and better designed languages, [/QUOTE]

I don't know anything about Obj-C, but C# is *not* better. It pointlessly complicates resource management by getting rid of destructors.

> 
What compiled, object-oriented language do you think is likely to replace C++ as the Linux development language of choice?  Or does free software have legacy issues that will keep C++ around in our world much longer than in theirs?

None that I've heard of, because they're not an improvement (because of the first two items below).

What would be nice to see would be:
* _deterministic_ _finalization_. lexically-scoped objects. refcount GC, with a way to manually break cycles (like boost::weak_ptr). other, (possibly non-deterministic) GC for when you don't want to bother checking for reference cycles, that can be disabled when you don't want to use it. destructors/finalizers called on destruction/collection in all cases.
* (optional?)static type checking (it may be annoying for scripts, but it's very nice for bigger projects) (*not* "duck-typing". types should (be able to) include both what an object can do, and what it means. if you have 5 conceptually distinct things with the same interface, you should be able tell the type system not to let you mix them up.)
* something like templates, but without the horrid error messages and with the ability to template on the number of parameters (without needing all of the variable-count parameters to be the same type)
* a (simple) way to get a human-readable stack trace from a cought exception
* closures, so you can say "go back to what you were doing when you called me, but come back here later" without lots of messy callbacks
* managed memory, so objects can be moved around as needed to not fragment memory usage over time
* anonymous functions, for when you do need callbacks
* not be tied to a single programming model
* simple way to choose pass-by-reference or pass-by-value for each argument
* reference/pointer semantics for all objects, so I can subclass your class and replace the members with derived classes even if you didn't anticipate it
* no way to make a class "final". If you wrote it, someone else will have a valid reason to subclass it. even if you never intended that.
* interfaces are probably just as good as multiple inheritance
* some way to say, "this interface is implemented by that class", even if the class doesn't know about the interface (or maybe make it automatic, if you explicitly specify that it's a "duck-typed" interface) Probably wouldn't be a true interface in the inheritance sense (so no casting), but only be for templating.
* lexically scoped macro definitions

---

### Post by rplantz on 2006-03-12
I recommend reading "The Design and Evolution of C++" by Bjarne Stroustroup. He discusses the various issues that arose and why he made the decisions he did. The book gave me a much better understanding of how C++ works, thus allowing me to use it more effectively. This, in turn, helped me to use C more effectively.

---

### Post by LordHunter317 on 2006-03-13
> **tbrownaw]I don't know anything about Obj-C, but C# is *not* better. It pointlessly complicates resource management by getting rid of destructors.[/quote]For garbage collection, which is a plus generally, and the most straightforward way to do it.

More importantly, it was stolen straight from Java and at least it offers constructs to make manual resource management eaiser, whereas Java does not.

Ultimately, for any custom unmanaged resources, in C# you have to write:[list][*]An RAII wrapper class implementing the IDisposable interface and pattern.[*]All uses of any instance of that wrapper as:```
void Method() {
    using (MyUnmanagedRes res = new MyUnmangedRes()) {
         // code goes here
    }
}
```[/list]Compare this to C++:[list][*]An RAII wrapper class or destructor, depending on the semantics required.[*]All uses of any instance of that wrapper as:```
void function() {
    MyUnmanagedRes res said:**
> So the difference ultimately boils down to the using() statement.  This is pretty minor, given that in C#, I don't have to manage memory at all, while with C++, I have to manage memory as well.  This means that in C++, something as simple as a collections class (e.g., std::vector, std::list) require an explict destructor.  Equivalents in C# do not.

Aside: This can be done in Java as well, but requires manually writing try/finally blocks.  using in C# is shorthand for that.

> refcount GC, with a way to manually break cycles (like boost::weak_ptr).Which in a GC system, has other negative consequences.

[quote]destructors/finalizers called on destruction/collection in all cases.This already is in most languages.

> * something like templates, but without the horrid error messages and with the ability to template on the number of parameters (without needing all of the variable-count parameters to be the same type)Your latter requirest would be non-viable for a template system, and would be suited for a real macro system.

> * managed memory, so objects can be moved around as needed to not fragment memory usage over timeNo current managed memory system does this, because the performance cost is generally too great.

> * simple way to choose pass-by-reference or pass-by-value for each argumentWhy?  Java is pass-by-value all the time and it works fine.  C# is pass-by-value for all non-value types and it works well.  It might be nicer if Java and C# pointers were really references, but that's a different story.

> * reference/pointer semantics for all objects,Those aren't the same thing.  

> so I can subclass your class and replace the members with derived classes even if you didn't anticipate itReference and pointer semantics don't let you do this *per se*.  They're not necessarily relevant to polymorphism in the least.  Dynamically bound languages don't require pointers to implement polymorphism, for example.

> * no way to make a class "final".Utter insanity.

>  If you wrote it, someone else will have a valid reason to subclass it.No, they likely won't.  Concrete types should never be inherited from, as it breaks all sorts of semantics.

> * interfaces are probably just as good as multiple inheritanceJava's clearly proven they're not, unless the language supports enough workarounds to make it a non-issue.

> * some way to say, "this interface is implemented by that class",All languages in question have this already.

> even if the class doesn't know about the interface (or maybe make it automatic, if you explicitly specify that it's a "duck-typed" interface) You just argued against duck-typing, and now are arguing for it?  Pick one and stay on it.

---

### Post by thumper on 2006-03-13
[QUOTE=kar-tar]C++ looks to be fading away.[/QUOTE]
No.  It isn't.

There is still extremely active standardisation going on.  A BSI C++ committee meeting is going on as I type :)

There are many extremely interesting things being standardised which should be in C++0x like auto, decltype, concepts and lambdas.  Things to make C++ more consistent, easier to write and getting better error messages.

C++ is going to be around for some time yet.

---

### Post by tbrownaw on 2006-03-13
[QUOTE=LordHunter317]So the difference ultimately boils down to the using() statement. This is pretty minor, ...[/QUOTE]

using() means that all users of a class must know implementation details. If I have a logger class where the log() function allocates some resource (file, socket, ...), uses it, and deallocates it, I don't need using(). If I then decide I want it to hold that resource between calls, everyone who uses it needs to use using(). Because of an implementation detail. Not minor at all.

[QUOTE=LordHunter317]...given that in C#, I don't have to manage memory at all, while with C++, I have to manage memory as well.This means that in C++, something as simple as a collections class (e.g., std::vector, std::list) require an explict destructor. Equivalents in C# do not.[/QUOTE]
In C++, I can use boost::shared_ptr<> (I think there's something similar in the std:: namespace too) and also not have to write destructors just for memory.

[QUOTE=LordHunter317]Your latter requirest would be non-viable for a template system, and would be suited for a real macro system.[/QUOTE]
OK, macros then. What I actually mean by "template" here is, "whatever it is that templates are an instance of", which I think it actually called something like "generic programming" or "multiprogramming".

[QUOTE=LordHunter317] >  * reference/pointer semantics for all objects,
Those aren't the same thing. [/QUOTE]
They're both "the object you want really lives over there.". And they're similar enough that Java references and C/C++ pointers act the same (can be uninitialized/null, can be made to point to / reference a different object).


[QUOTE=LordHunter317] >  * some way to say, "this interface is implemented by that class",
All languages in question have this already.[/QUOTE]
They do? I thought all they could say was "this class implements that interface".

[QUOTE=LordHunter317]
You just argued against duck-typing, and now are arguing for it?  Pick one and stay on it.[/QUOTE]
It should be available by explicit request only. And really probably only for templates/macros, as a way to describe what interface reqirements the template code has for its types.

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=tbrownaw]It should be available by explicit request only. And really probably only for templates, as a way to describe what interface reqirements the template code has for its types.[/QUOTE]Now that I can agree to. :)

---

### Post by thumper on 2006-03-13
[QUOTE=tbrownaw]In C++, I can use boost::shared_ptr<> (I think there's something similar in the std:: namespace too) and also not have to write destructors just for memory.
[/QUOTE]
There is a shared_ptr in tr1 now.

```
#include <tr1/memory>

class Foo;
typedef std::tr1::shared_ptr<Foo> FooPtr;

```

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=tbrownaw]using() means that all users of a class must know implementation details.[/quote]No, they just must know your class implements  IDisposable.  And since C# is a statically typed language, you know that ahead of time.  Failing that, the code will fail to compile if it doesn't implement IDiosposable.

>  If I have a logger class where the log() function allocates some resource (file, socket, ...), uses it, and deallocates it, I don't need using(). If I then decide I want it to hold that resource between calls, everyone who uses it needs to use using().No, you only need to use it at the highest scope the logging object is used.  Everything below that scope doesn't have to do anything.

As a rule, you **always** use using to implment RAII.  That means that you declare the object in the using block, so it's scope is known.

This only breaks down when you have a class that implements IDisposable as a member.  And in that case, you make your class implement IDisposable and just pass the buck up the chain.

It does mean you have to implement IDisposable correctly but C++ still makes you do this as well.

> In C++, I can use boost::shared_ptr<> (I think there's something similar in the std:: namespace too) and also not have to write destructors just for memory.boost::shared_ptr<> can't cover all cases or anything approaching it.  The entire point is that if I write a collection class, I must write a destructor to destroy the collected objects.  Not-optional.  In C#, this very well may not be required, due to garbage collection.

While I won't argue that C++'s interface for resource management is superior, the entire point is that in C# you have to do it less often.  That very well may be ultimately more superior in the end.

> OK, macros then. What I actually mean by "template" here is, "whatever it is that templates are an instance of", which I think it actually called something like "generic programming" or "multiprogramming".Well no, you're confusing the two.  My point is that variable-argument templates wuld be difficult to support as templates, especially for arbitrary types.

Specifically, is each enumeration of the variable list a new type or are they all the same type?

Far superior would be a real macro language that could generate the template parameters, where you want variable arguments.  That way, you can constrain the variable number of parmeters or the types as necessary, but still have a variable number of types where necessary.

> They're both "the object you want really lives over there.". And they're similar enough that Java references and C/C++ pointers act the same (can be uninitialized/null, can be made to point to / reference a different object).That's because the name is misnomer.  Java "references" are really pointers.

C++ references are really references: they cannot be reseated.

> They do? I thought all they could say was "this class implements that interface".OK, I understand what you're asking now.  Yes, you can do that via a downcast (i.e., C++ dynamic_cast<>).

---

### Post by Chozabu on 2006-03-13
A disscussion about a lang replacing C++, and no-ones even mentioned D?

---

### Post by tbrownaw on 2006-03-13
[QUOTE=LordHunter317]This only breaks down when you have a class that implements IDisposable as a member.  And in that case, you make your class implement IDisposable and just pass the buck up the chain.[/QUOTE]
And if that member is a private member (ie, "implementation detail"), you've just broken encapsulation. You shouldn't have to care whether some class you're using happens to hold resources somewhere hidden in its implementation.

---

### Post by LordHunter317 on 2006-03-13
[QUOTE=tbrownaw]And if that member is a private member (ie, "implementation detail"), you've just broken encapsulation.[/quote]**No, you haven't.**  IDisposable is an *interface*.

If a class formerly didn't implement IDisposable and implements it now, it's a breaking API change.

In any case, you've never broken encapsulation: you're not exposing any details besides the fact it implements the IDosposable interface.

> You shouldn't have to care whether some class you're using happens to hold resources somewhere hidden in its implementation.But you do have to care in either language, so this is a non-sequitur.  You have to care in C++: you have to wrap unmanaged resources in unmanaged wrappers.

You have to care in C#: you have to wrap unmanaged resources in unmanaged wrappers.  In addition, you have to make a **public** class to force them to their cleanup, but that doesn't mean encapsulation is broken.

It only means it breaks if you **add** unmanaged resources and causes an *API* break in C#.  Yes, it doesn't do the same in C++, you'd be correct if you say that.  But it doesn't mean what you're saying about C# is true either.

[edit]Thta should be umanaged resources in managed wrappers.

---

### Post by vialick on 2006-03-13
I allways imagined INTERCAL would be the language of the future. I particularly like the way it enforces politeness

---

### Post by Chozabu on 2006-03-15
man, stuff like that and brainf**k worry me...

---

