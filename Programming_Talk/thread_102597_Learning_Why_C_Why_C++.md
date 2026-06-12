---
title: "Learning: Why C? Why C++?"
date: 2005-12-12
forum: Programming Talk
---

### Post by bored2k on 2005-12-12
[CENTER]I'm currently starting to learn **C** reading 
[[IMG]http://images.amazon.com/images/P/0131103628.01._AA240_SCLZZZZZZZ_.jpg[/IMG]]("http://www.amazon.com/gp/product/0131103628/104-0085013-9267907?v=glance&n=283155").[/CENTER] 

My questions are the following: 

[LIST=1]
[*]**Why** should I choose learning C first over C++ (or viceversa)?
[*]What's **easier**: C --> C++ or C++ --> C ?  Why?
[*]Which one is **harder** to work with?
[*]What **program** do you code in? (I'm currently using Jed and sometimes Anjuta)
[/LIST]

[center]Thanks for your thoughts (or not) :).[/center]

---

### Post by psusi on 2005-12-12
C is mostly a subset of C++ so if you know C++, you ( mostly ) know C.  Because of this, most people say to learn C++ first.  

I learned C first ( C++ wasn't really around back then ) and I feel that by learning C first, you will have a better appreciation for C++.  C++ is certainly much more rich and complicated than C, so learning it is harder, but using it can have great benefits on non trivial programs.  

These days I both.  Various projects that I do some hacking on are already written in C, so when modifying them, you stick with C.  Also at work the embeded system I develp on only supports C, so that's what I am stuck with.  I still greatly prefer C++ though, when given a choice.

---

### Post by earobinson on 2005-12-12
C is not an object orianted lauange c++ is.
however if you have programed in java before, it is very easy to figure out how to program in C++ if you have learned C

Also note if you learn C++ You will learn C.

IMO learning C first is a good step.

2. That depends on the task, for example I would never make a linked list or a tree in C, it is easyer in C++, but a program that dose very simple steps I would do in C for example a simple contact list.

3. C++ in general but only by a small ammount.

4. gedit mostly

---

### Post by arpunk on 2005-12-12
1) C++ is sorta like *upgraded C*, so i would recommend C first, them move to C++ and finally C# (mono :D).

2) C, because its an structured language (it was easier for me to think structured first).

3) Depend of what you coding. Some stuff can be easily accomplished using C++ and it can be a pain in the ass doing them in C.

4) vim

---

### Post by thumper on 2005-12-12
I'd say to learn first the language that you see yourself using more often.

I went from C to C++ so I can't comment on the other way around.  However when I switched, there was no standard C++, so all the class libraries were proprietory.  These days I'd say learn C++ first, but hey, that's just me.

Harder is a very subjective term.  Is C harder because you have to do more yourself with fewer language features or is C++ harder because of more features? Hard to say really.

I write code in emacs. I have been using it for years and love the macro functionality, and have got used to my keybindings.

---

### Post by amohanty on 2005-12-12
C is a procedural language [http://en.wikipedia.org/wiki/Procedural_programming](http://en.wikipedia.org/wiki/Procedural_programming)
while C++ is object oriented.

Althought they are quite similar in basic syntax, they are different tools for different jobs. If you are programming for low-level subsystems C is fast, uncomplicated and (although properly designed and implemented C++ is just as fast) .. well more widely used. 

For more complicated software systems where the interaction and relatioships between various components are not so simple OO is a better choice since it reflects the real relationships/interactions more closely. 

IMO neither is harder and as thumper said - harder is a very subjective term - as other posters have noted, it depends....

Although I learned C first I would suggest learning C++ first because IMO, C style programming is easier to reconcile with after learning OOP as opposed to the other way round.

HTH

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=bored2k][*]**Why** should I choose learning C first over C++ (or viceversa)?[/quote]You shouldn't, unless your only reason for learning either language is kernel-level programming, or embedded systems programming.  Then, C can be a superior choice because it's less complicated and eaiser to get exact control over your memory. 

More importantly, most kernels don't support C++ code offically (if at all) and many embedded platforms lack a C++ compiler completely or their C++ is worthless.

> [*]What's **easier**: C --> C++ or C++ --> C ?  Why?Eaiser how?  To understand?  The underlying concepts of C are eaiser to understand because they're slightly more orthogonal and there are few of them. C++ is a far more "cluttered" language and has several deeper features.
> [*]Which one is **harder** to work with?For most tasks?  C.  You can't write as featureful data structures that encapsulate as much of the functionality for dealing with them as necessary.

It's impossible for example, to have RAII in C: you always must free the resource manually.

Whatever anyone says, ***do not*** learn one to learn the other.  Treat them as conceptually different languages.  The best way to do something in C is the wrong-way in C++, and vice-versa (usually because the best way in C++ is impossible in C).

For example, you must use arrays in C, you have little choice.  But for data storage, you should almost never use an array in C++, you should use a std::vector instead.  

In C, if you need a generic container, your only real resource is to use a (void*) and casts.  In C++, you write a templated class.

These sort of differences are why you shouldn't use one to learn the other.  "Everything is permissible, not everything is benefical" and all that.

---

### Post by psusi on 2005-12-12
I also thought I would point out that most people seem to think that C = procedural, and C++ = OOP.  This is not the case.  C++ has language features that facilitate OOP, but you can write procedural code in C++, and you can use OOP in C.  

Another popular myth is that C++ is slower and more bloated than C.  It is equally possible to write either tight efficient code, or slow and bloated code in either language.

---

### Post by arpunk on 2005-12-12
[QUOTE=psusi]I also thought I would point out that most people seem to think that C = procedural, and C++ = OOP.  This is not the case.  C++ has language features that facilitate OOP, but you can write procedural code in C++, and you can use OOP in C.  

Another popular myth is that C++ is slower and more bloated than C.  It is equally possible to write either tight efficient code, or slow and bloated code in either language.[/QUOTE]
Can you be a more specific when saying that *you can use OOP in C*? I agree you can write procedural code in C++, but i would like to know your point about OOP in C.

---

### Post by LordHunter317 on 2005-12-12
You can create structures in C that use function pointers and a non-invisible this/self.

But you cannot do inheritence, abstraction, type-safe upwards casting without writing something that looks suspicously like the innards of a C++ compiler.

So no, you really can't do object-oriented programming in C, unless you define OOP as functions that operate on a fixed data structure.  But by that logic, all languages are OOP, so it's really bunk.

---

### Post by arpunk on 2005-12-12
[QUOTE=LordHunter317]You can create structures in C that use function pointers and a non-invisible this/self.

But you cannot do inheritence, abstraction, type-safe upwards casting without writing something that looks suspicously like the innards of a C++ compiler.

So no, you really can't do object-oriented programming in C, unless you define OOP as functions that operate on a fixed data structure.  But by that logic, all languages are OOP, so it's really bunk.[/QUOTE]
That was my point, thanks.

---

### Post by thumper on 2005-12-12
Another thing that hasn't been fully pointed out is that C++ can also be used in a functional way with the use of templates and generics.

That is much harder to do in C (I won't say impossible as there may be some C guru who can).

---

### Post by amohanty on 2005-12-12
[QUOTE=psusi]I also thought I would point out that most people seem to think that C = procedural, and C++ = OOP.  This is not the case.  C++ has language features that facilitate OOP, but you can write procedural code in C++, and you can use OOP in C.  [/QUOTE]


You are right in that C++ programs can always be written in a procedural style, but IMO that defeats the purpose of OOP.  AFAIK other than using Objective-C (which is a superset) I am not sure how you can use _true_ OOP in C. You can use structures, statics and typedefs to simulate OOP, but I think, if not used properly they can be far more dangerous than useful.

[QUOTE=psusi]
Another popular myth is that C++ is slower and more bloated than C.  It is equally possible to write either tight efficient code, or slow and bloated code in either language.[/QUOTE]

Although I agree with you there, unfortunately I have not seen too many real world C++ applications (in the problem domain where C is best - as LH mentioned - "kernel-level programming, or embedded systems programming") achieve the kind of performance C programs have, not that there are too many of them. Thus given the history of applications I usually stay away from  using C++ for applications in those domains. Hence my comment.

---

### Post by cwaldbieser on 2005-12-12
[QUOTE=arpunk]Can you be a more specific when saying that *you can use OOP in C*? I agree you can write procedural code in C++, but i would like to know your point about OOP in C.[/QUOTE]
He means that OOP is a way of modeling your program.  C++ has features that explicitly support this model, but that doesn't mean you can't use the model without explicit feature support.

---

### Post by arpunk on 2005-12-12
I could agree with you but, i was talking about the *real* statment he did, which was pointed here: 

[http://ubuntuforums.org/showpost.php?p=567299&postcount=11](http://ubuntuforums.org/showpost.php?p=567299&postcount=11)

---

### Post by psusi on 2005-12-12
When you get down to the bare metal, a class is just a struct that contains a hidden pointer to a vtable, and member functions just have the name of the class embeded into their mangled symbol name, and a 'this' pointer added as a parameter.  This can be implemented in C, it just takes a bit more effort.  Remember that the original C++ compiler just translated the code to C and fed it to the C compiler.  

I remember back in the day I did some hacking on the eggdrop IRC bot.  I think it was between version 1.1.5 and 1.3.x that they did some massive rewrites and were using OOP in C.  It looks different at first glance, but when you think about what the machine is actually doing, it amounts to the same thing, even though the source language looks quite a bit different.  

As an example, in C++ you might have code like this:

```

class point {
public:
  int x;
  int y;
  point &operator+=(point &pt) { x += pt.x; y += pt.y; return *this; }
};

```
You can translate that to C as:
```

struct point {
  int x;
  int y;
};

void point_plusequals( struct point *this, struct point *that )
{
  this->x += that->x;
  this->y += that->y;
}

```

[QUOTE=arpunk]Can you be a more specific when saying that *you can use OOP in C*? I agree you can write procedural code in C++, but i would like to know your point about OOP in C.[/QUOTE]

---

### Post by arpunk on 2005-12-12
Yes, true, but what about *inheritence* and *abstraction*? classes arent OOP by itself, its the whole *paradigma* that makes OOP AFAIK. C++ wouldnt make sense if all of OOP could be done in C.

---

### Post by amohanty on 2005-12-12
> When you get down to the bare metal, a class is just a struct that contains a hidden pointer to a vtable, and member functions just have the name of the class embeded into their mangled symbol name, and a 'this' pointer added as a parameter. This can be implemented in C, it just takes a bit more effort. Remember that the original C++ compiler just translated the code to C and fed it to the C compiler.

But that amounts to the same thing as LH mentioned, you would be essentially redoing parts or all of any modern C++ compiler, now wouldnt you?

---

### Post by psusi on 2005-12-12
[QUOTE=cwaldbieser]He means that OOP is a way of modeling your program.  C++ has features that explicitly support this model, but that doesn't mean you can't use the model without explicit feature support.[/QUOTE]

You hit the nail on the head.  It may not be very easy or wise to use OOP in C, but it is possible.  I say that to point out that OOP is not a property of a language.  You can not say that C++ is OOP, and C is not OOP.  A language can not BE OOP.  OOP is a programming paradigm.  

Before OOP, the popular paradigm was structured programming.  It would not be proper to say that C is structred programming.  It strongly supported structured programming by providing things like do..while loops, and discouraging the use of goto, but if you really wanted to, you could refuse to use the provided control structures and instead use goto everywhere.

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=cwaldbieser]He means that OOP is a way of modeling your program.  C++ has features that explicitly support this model, but that doesn't mean you can't use the model without explicit feature support.[/QUOTE]Except that's crap.  You cannot do multimethods without language support (even in C++, emulation of them is poor and ends up looking alot like the innards of a language compiler/interpreter that does support them), you cannot do generics without language support, and you cannot do a sensical definition of OOP without language support.

When I say "cannot" above, I mean with the compiler caveat I'm repeated several times.  You certainly can, but ultimately, you'll just end up inventing that other language, but probably in a far poorer way.  Square peg, round hole and all that.

[quote=psusi]I say that to point out that OOP is not a property of a language. You can not say that C++ is OOP, and C is not OOP. A language can not BE OOP. OOP is a programming paradigm.[/quote]But that's not true.  If your definition of OOP is reasonable and includes the ability to perform polymorphic operations and inherit data types, then no, C is not OOP.  It cannot do those operations without essentially writing a C++ compiler into your C code.  At which point, you might as well call it "almost C++" or just use C++.

---

### Post by psusi on 2005-12-12
[QUOTE=LordHunter317]Except that's crap.  You cannot do multimethods without language support (even in C++, emulation of them is poor and ends up looking alot like the innards of a language compiler/interpreter that does support them), you cannot do generics without language support, and you cannot do a sensical definition of OOP without language support.

When I say "cannot" above, I mean with the compiler caveat I'm repeated several times.  You certainly can, but ultimately, you'll just end up inventing that other language, but probably in a far poorer way.  Square peg, round hole and all that.[/QUOTE]

I have never heard the term 'multimethod' before, maybe you could explain?  I certainly can not find a reference to it in the C++ standard.  Also you seem to be nearly agreeing with me.  It is not a good idea, and takes a good deal of work that the compiler does for you in C++, but it is possible to use the OOP paradigm in C.  Before C++ added templates to the language, people were doing generic programming using macros.  There are a number of problems associated with doing it that way, and it's rather hard to do, which is why templates were created, but it is still possible ( though not a good idea ) to use macros for generic programming.  

[QUOTE=LordHunter317]But that's not true.  If your definition of OOP is reasonable and includes the ability to perform polymorphic operations and inherit data types, then no, C is not OOP.  It cannot do those operations without essentially writing a C++ compiler into your C code.  At which point, you might as well call it "almost C++" or just use C++.[/QUOTE]

Again, it is entirely possible to perform polymorphic operations in C.  Yes, it takes a lot of work that is done for you in C++ by the compiler, but it is possible.  Obviously OOP in C is not C++, and if you are using OOP, you would be better off in C++, but if you are stuck with using C, you can apply the OOP paradigm there with some benefit.

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=psusi]I have never heard the term 'multimethod' before, maybe you could explain?[/quote]A multimethod is a method that's virtual with respect to more than one (generically, an arbitrary number) of types.  

>   I certainly can not find a reference to it in the C++ standard.That's because C++ doesn't support them.  LISP w/ CLOS does, however.  They're very powerful and necessary in certain situations.

> Before C++ added templates to the language, people were doing generic programming using macros.Yes, using real macros like found in LISP and other languages.  They weren't doing it with C preprocessor macros.

> Again, it is entirely possible to perform polymorphic operations in C.  Yes, it takes a lot of work that is done for you in C++ by the compiler, but it is possible.And when you do that work, I question the value of calling the code 'C'.  In all reality, to do it generically, you're going to end up with some sort of code preprocessor, at which point I'd offically say you've stopped writing C and have instead written "OOP-C" that's compiled to C first.

---

### Post by psusi on 2005-12-12
[QUOTE=LordHunter317]
Yes, using real macros like found in LISP and other languages.  They weren't doing it with C preprocessor macros.[/QUOTE]

No, they WERE doing it with C preprocessor macros.  It was an ugly hack with all kinds of problems, but they did it.  

[QUOTE=LordHunter317]And when you do that work, I question the value of calling the code 'C'.  In all reality, to do it generically, you're going to end up with some sort of code preprocessor, at which point I'd offically say you've stopped writing C and have instead written "OOP-C" that's compiled to C first.[/QUOTE]

It is still C because it can be compiled with a C compiler.  Depending on exactly how much OOP you are trying to use, and how you do it, it might be very ugly C, but it is still C.

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=psusi]No, they WERE doing it with C preprocessor macros.  It was an ugly hack with all kinds of problems, but they did it.[/quote]I've yet to see any C macros that would pass muster for a valid generics system of any sort.  None of the ones I've seen are type-safe. 

> It is still C because it can be compiled with a C compiler.**No, it cannot be**, because it must **be preprocessed first**.

If we use the standard you suggest, then all code is assembly because it's all converted to assembly first, and then can be assembled with an assembler.  Obviously, that's a worthless definition.

---

### Post by psusi on 2005-12-13
[QUOTE=LordHunter317]I've yet to see any C macros that would pass muster for a valid generics system of any sort.  None of the ones I've seen are type-safe. [/QUOTE]

Lack of type safety is one of the things I meant when I said that it was an ugly hack.  Being ugly and error prone does not mean it wasn't a form of generic programming any more than assembly's lack of type safety means it doesn't have variables.  

[QUOTE=LordHunter317]
**No, it cannot be**, because it must **be preprocessed first**.
[/QUOTE]

Yes, by the C preprocessor, which is a part of the C language.  

[QUOTE=LordHunter317]If we use the standard you suggest, then all code is assembly because it's all converted to assembly first, and then can be assembled with an assembler.  Obviously, that's a worthless definition.[/QUOTE]

You might not value that definition very much, but I do.  All code IS compiled into assembly, and when writing code in a higher level language, it can be very helpful to remain concious of that fact, and be thinking in the back of your mind what the assembly that your code will be compiled into looks like.

One of the reasons C got so popular was because it was relatively easy to look at some C code and know what assembly the compiler would turn it into, and hence, understand exactly what the hardware was doing when it ran your code.

---

### Post by LordHunter317 on 2005-12-13
[QUOTE=psusi]Lack of type safety is one of the things I meant when I said that it was an ugly hack. [/quote]It also makes it useless.  If I have to cast the data in and out, I'm not really doing generic programming.  I haven't gained anything and I've given up something major.  I might as well move to a dynamically-typed language.

> Being ugly and error prone does not mean it wasn't a form of generic programmingYes, in this case, it does.

Just like the level of OOP you can emulate in 
 any more than assembly's lack of type safety means it doesn't have variables.  

> Yes, by the C preprocessor, which is a part of the C language.  No, I never said the C preprocessor.  In fact, I explcitly meant one you wrote on your own.  Apologies if I wasn't clear.


> You might not value that definition very much, but I do. But it's useless.  Saying all native code becomes assembly at some point in the process, therefore it is assembly (which is what you tried to do) is not only logically awkward, it doesn't help anything.  What's the merit of this definition, especially when it's flaws are particularly clear?


>  All code IS compiled into assembly,Native code is.  

> and when writing code in a higher level language, it can be very helpful to remain concious of that fact, and be thinking in the back of your mind what the assembly that your code will be compiled into looks like.Not typically, unless you're dealing with a broken compiler or likely have to hand-optimize anyway.  Neither of which are common.

---

### Post by psusi on 2005-12-13
[QUOTE=LordHunter317]It also makes it useless.  If I have to cast the data in and out, I'm not really doing generic programming.  I haven't gained anything and I've given up something major.  I might as well move to a dynamically-typed language.[/QUOTE]

Generic programming does not really have anything to do with type safety.  That IS a nice feature of C++, but the core of generic programming is writing code once, and being able to apply that code to manipulate all kinds of different objects later.  

When you write a template, you write code that uses a placeholder for the type name, which you fill in at a later time when you instantiate the template.  Once instantiated you can think of the code as having had the placeholder for the typename replaced by the type you give when you instantiate it in much the same way that you can write C preprocessor macros that will replace a placeholder with other text, which very well could be a real type.  

In the early days, people used C preprocessor macros for that very purpose.  They invented templates to solve a number of problems with that aproach, one of which is that the C preprocessor will substitute whatever text you pass  to the macro when you "instantiate" so you can really shoot yourself in the foot if that text is not the name of a data type.  Assuming that you do use it correctly though, the results of the macro expantion are very similar to template instantiation.  While this method had it's share of problems, it was generic programming because it allowed you to write the code once, and then apply it to various data types down the road that you had no idea about when you wrote it.  

[QUOTE=LordHunter317]
No, I never said the C preprocessor.  In fact, I explcitly meant one you wrote on your own.  Apologies if I wasn't clear.[/QUOTE]

I have been trying to say that you assumed that I meant some other preprocessor, but I was in fact, refering only to the C preprocessor.  


[QUOTE=LordHunter317]But it's useless.  Saying all native code becomes assembly at some point in the process, therefore it is assembly (which is what you tried to do) is not only logically awkward, it doesn't help anything.  What's the merit of this definition, especially when it's flaws are particularly clear?[/QUOTE]

I didn't say it IS assembly, but it does become assembly, and having at least a rough idea of what that assembly will look like in the back of your head can keep you from writing slow and bloated code when you realize that it may look nice in C++, but it's going to generate a lot of assembly.

---

### Post by LordHunter317 on 2005-12-13
[QUOTE=psusi]Generic programming does not really have anything to do with type safety.  That IS a nice feature of C++, but the core of generic programming is writing code once, and being able to apply that code to manipulate all kinds of different objects later.[/quote]By having the compiler generate the code for you.  

> I have been trying to say that you assumed that I meant some other preprocessor, but I was in fact, refering only to the C preprocessor.  Again, I haven't seen an effective vtable system written in C preprocessor and C preprocessor only.

> I didn't say it IS assembly, but it does become assembly,In my original comparsion, that was the claim.

> and having at least a rough idea of what that assembly will look like in the back of your head can keep you from writing slow and bloated code when you realize that it may look nice in C++, but it's going to generate a lot of assembly.And as I pointed out, if you care about what the assembly looks like, you ought to be writing assembly.

---

### Post by psusi on 2005-12-13
[QUOTE=LordHunter317]By having the compiler generate the code for you.  [/QUOTE]

Yes... which is exactly what happens when you use the C preprocessor to "instantiate" a macro-template.  It takes your generic code and turns it into code that performs the algorithm on a new data type that you specified.  

[QUOTE=LordHunter317]Again, I haven't seen an effective vtable system written in C preprocessor and C preprocessor only.[/QUOTE]

I think you are looking for the wrong thing.  If you are looking for something that will look and work like vtables in C++, then yes, you won't find it.  What I am talking about looks nothing like C++ at the source level, but at the machine level, it does the same thing.  It isn't very nice to use from a source code perspective, but as far as the machine is concerened, it is the same thing, and as far as the higher level application design goes, it is still OO.  

Remember, OO is a design paradigm, not a language feature.  You have to think in terms of application design, not source code.  

[QUOTE=LordHunter317]
In my original comparsion, that was the claim.

And as I pointed out, if you care about what the assembly looks like, you ought to be writing assembly.[/QUOTE]

This is gross generalization.  Writing in a high level language you can get the job done a lot faster than in assembly, but just because you want to get the job done sooner does not mean you don't give a damn about performance.  

You can get the best of both worlds by understanding both worlds and the relationships between them.  Often in a higher level language there are a dozen different ways you can choose to write a block of code.  Choosing which one is best requires an understanding of how it is going to execute on the machine so that you can make a decision on the tradeoffs between each method.

---

### Post by LordHunter317 on 2005-12-13
[QUOTE=psusi]I think you are looking for the wrong thing.[/quote]Ok, let me generalize: I've never seen an effective inheritence system written in C and C macro and only those two.

> Remember, OO is a design paradigm, not a language feature.That can only really be done with some language support.

> This is gross generalization.  Writing in a high level language you can get the job done a lot faster than in assembly, but just because you want to get the job done sooner does not mean you don't give a damn about performance.  If you care about performance at the machine level, you write machine code.  You can get so many gains before reaching that level it's silly to even try to claim otherwise.

>  Choosing which one is best requires an understanding of how it is going to execute on the machine so that you can make a decision on the tradeoffs between each method.And you figure that out through a profiler, not through looking at the machine code.  On a modern CPU, the machine code may not tell you anything anyway due to OOOE.

---

### Post by psusi on 2005-12-13
[QUOTE=LordHunter317]Ok, let me generalize: I've never seen an effective inheritence system written in C and C macro and only those two.

That can only really be done with some language support.[/QUOTE]

Again, OO is a design paradigm, it is independant of the language.  You can design OO software entirely on paper ( maybe documented in UML ) without ever writing one line of code or even choosing which language you will write the software in.  

Various languages have various features that make it convinient to write the code that implements an OO design patern, but it is the design that defines object orientation, not the code or the language the code is written in.  

[QUOTE=LordHunter317]If you care about performance at the machine level, you write machine code.  You can get so many gains before reaching that level it's silly to even try to claim otherwise.[/QUOTE]

Life is not black and white, there are many shades of grey.  It isn't either one or the other, you can use and understand both at once.  

[QUOTE=LordHunter317]And you figure that out through a profiler, not through looking at the machine code.  On a modern CPU, the machine code may not tell you anything anyway due to OOOE.[/QUOTE]

When you understand assembly and how it relates to the high level source code you write, you can predict the results the profiler will give you without having to do it wrong, profile it, then go back and fix it later.  And of course, knowing the details of the cpu executing the assembly, you can predict exactly what it will do even with OOOE.  Usually though, you don't care exactly how many clocks it will take to execute, only that doing it this way is going to take about 10 times longer than doing it that way.

---

### Post by LordHunter317 on 2005-12-13
[QUOTE=psusi]Again, OO is a design paradigm, it is independant of the language.[/quote]Then where is this C preprocessor code that gives me inheritence?

Clearly, if we're talking about writing OO code in a programming language (which we were) then the language has to have some mechanism to support it.

> Life is not black and white, there are many shades of grey.  It isn't either one or the other, you can use and understand both at once.  You've failed to show how the assembly output will help me better understand what the C++ except in the cases I mentioned: broken compiler, and being so performanced concerned I'm dangerously close to having to rewrite the machine language anyway.

> When you understand assembly and how it relates to the high level source code you write, you can predict the results the profiler will give you without having to do it wrong, profile it, then go back and fix it later.But you can't necessarily, that's the point.  Especially on a modern operating system.  The issue is likely not to be in the assembly being generated being inefficent, it's almost always an issue of algorithms.  Which is inarguably better solved at a higher level.

> And of course, knowing the details of the cpu executing the assembly, you can predict exactly what it will do even with OOOE.Not necessarily.  Branch prediction isn't necessarily a deterministic operation on all processors in existance.

> Usually though, you don't care exactly how many clocks it will take to execute, only that doing it this way is going to take about 10 times longer than doing it that way.Which a profiler tells you without the fuss.  You're not helping your argument.

---

### Post by psusi on 2005-12-13
> **LordHunter317]Then where is this C preprocessor code that gives me inheritence?[/QUOTE]

You still don't get it.  You need to decouple your concept of OOP from code and think about design paterns.  Inheritence is not just a language feature said:**
> Clearly, if we're talking about writing OO code in a programming language (which we were) then the language has to have some mechanism to support it.

No, I'm not talking about writing OO code in a programming language; my point this entire time has been that OOP is a software design paradigm, and as such, is independant of the language used to implement it.  Once you design the software using OO techniques, you can implement it in any language you choose.  I only gave examples of using OO techniques in C to exemplify this.  

[QUOTE=LordHunter317]You've failed to show how the assembly output will help me better understand what the C++ except in the cases I mentioned: broken compiler, and being so performanced concerned I'm dangerously close to having to rewrite the machine language anyway.[/QUOTE]

I'm not sure how else I can explain that your world view is wrong.  Things are never absolute.  You can be concerned about performance without being so worried about it that you have to write the entire program in assembly.  There is a healthy middle ground where you are not so worried that you can use a high level language to get the job done easier, but be concerened enough that you give some thought to the efficiency of the code as you write it.  


[QUOTE=LordHunter317]But you can't necessarily, that's the point.  Especially on a modern operating system.  The issue is likely not to be in the assembly being generated being inefficent, it's almost always an issue of algorithms.  Which is inarguably better solved at a higher level.[/QUOTE]

Sometimes is is useful to think in more abstract terms, like big O() notation.  Sometimes it is more useful to think more specifically, especially when the two choices are not orders of magnitude different.  

[QUOTE=LordHunter317]Not necessarily.  Branch prediction isn't necessarily a deterministic operation on all processors in existance.

Which a profiler tells you without the fuss.  You're not helping your argument.[/QUOTE]

You still have to write the code wrong the first time, then use the profiler, then redo it right later.  It is much easier to just do it right the first time by giving it a little bit more thought up front.

---

### Post by LordHunter317 on 2005-12-13
> **psusi]You still don't get it.  You need to decouple your concept of OOP from code and think about design paterns.[/quote]No, I don't.  A useful definition of Object-Oriented Programming includes the ability to have classes inherit from one another.

This was my original point: OOP in C usually refers to objects and non-member functions that access them, which isn't really OOP.  As I pointed out, by that definition, any language supports OOP, so it's probably not that useful of a definition.

>  Inheritence is not just a language feature said:**
> **Which requires languages features to implement.** No matter how you try to state your point, you can't get around it.  Even if I accept that OOP is just a paradigm, you must concede that it's not useful to anyone unless I can actually use it.  And you've failed to demonstrate how it can be used in any useful way unless the language has some mechanism for supporting it.

You don't get around the problem by calling it something else.  A pardigm is only useful if I can use it.

[quote]No, I'm not talking about writing OO code in a programming language; my point this entire time has been that OOP is a software design paradigm, and as such, is independant of the language used to implement it.That's irrelevant to my counter claim: you can't use the paradigm without language support for it.

[quote]I only gave examples of using OO techniques in C to exemplify this.  You've yet to give a valid example using a reasonable definition of OOP. 

> Things are never absolute.  You can be concerned about performance without being so worried about it that you have to write the entire program in assembly.Then if you don't need to write it in assembly, **why do you care what the assembly** looks like?  You've made the claim it's benefical to look at it, you've yet to show how that's the case.

> but be concerened enough that you give some thought to the efficiency of the code as you write it."So look at teh assembly" doesn't follow from that.  I covered that case: use a profiler.

> It is much easier to just do it right the first time by giving it a little bit more thought up front.Look at the generated assembly doesn't follow from that.  You haven't shown how looking at the assembly actually gives you any insight, especially if we're talkign about a high-level language where a small change may totally change the generated output.

---

### Post by psusi on 2005-12-13
[QUOTE=LordHunter317]No, I don't.  A useful definition of Object-Oriented Programming includes the ability to have classes inherit from one another.[/QUOTE]

If you are refering to classes in the abstract, then yes.  If you are refering to the C++ class keyword, then no.  A class is an abstract concept which can be modeled in C++ with the class keyword, or in other languages using other means.  

[QUOTE=LordHunter317]This was my original point: OOP in C usually refers to objects and non-member functions that access them, which isn't really OOP.  As I pointed out, by that definition, any language supports OOP, so it's probably not that useful of a definition.[/QUOTE]

Member functions are not so simply because of their C++ syntax.  What makes a member function is the conceptual association of several related functions that manipulate the same class of objects.  It does not really matter if the function's name is foo::bar() or foo__bar() as long as it is conceptually associated with an encapsulated class of objects.  

[QUOTE=LordHunter317]**Which requires languages features to implement.** No matter how you try to state your point, you can't get around it.  Even if I accept that OOP is just a paradigm, you must concede that it's not useful to anyone unless I can actually use it.  And you've failed to demonstrate how it can be used in any useful way unless the language has some mechanism for supporting it.[/QUOTE]

I have already shown how you can implement several OO features without C++'s support for them.  You very well could design an entire program that is OO all on paper in UML, then implement it in assembly.  There may be better ways to implement it, but that does not change the fact that the design is OO.  

One of the core design aspects of OOP is encapsulation.  That is a matter of concept, not syntax.  Syntatically in C++ it may look very different from the C syntax, but the design can be encapsulated either way, so long as you conceptually group functions with the data that they manipulate.  

[QUOTE=LordHunter317]You don't get around the problem by calling it something else.  A pardigm is only useful if I can use it.

That's irrelevant to my counter claim: you can't use the paradigm without language support for it.

You've yet to give a valid example using a reasonable definition of OOP. [/QUOTE]

See above.  

[QUOTE=LordHunter317]Then if you don't need to write it in assembly, **why do you care what the assembly** looks like?  You've made the claim it's benefical to look at it, you've yet to show how that's the case.[/QUOTE]

There is no need to show this is the case, it is patently obvious that one can do a better job the better one understands what one is doing.  

[QUOTE=LordHunter317]"So look at teh assembly" doesn't follow from that.  I covered that case: use a profiler.[/QUOTE]

And I already covered that it is easier to do it right the first time, than to profile it and fix it later.  

[QUOTE=LordHunter317]Look at the generated assembly doesn't follow from that.  You haven't shown how looking at the assembly actually gives you any insight, especially if we're talkign about a high-level language where a small change may totally change the generated output.[/QUOTE]

You just explained exactly how it gives insight.  A small change at the source level can have a large change at the assembly level.  Understanding the impact of that change can influence your decision to make that change or not.

---

### Post by LordHunter317 on 2005-12-13
[QUOTE=psusi]A class is an abstract concept which can be modeled in C++ with the class keyword, or in other languages using other means. [/quote]No, I'm referring to both: the ability ot have a class ("abstract" in the design sense or not, it doesn't bloody matter) inherit from another class.

My point is: if I designed my code around that "paradigm" and I can't implement said "paradigm" in a specific language, then that paradigm isn't supported by the language.

Now, replace "paradigm" with inheritance, and "specific language" with C.  It doesn't matter what word you use, you're still deflecting the point:
**Some paradigms required language support to be used.**

You haven't shown that to not be the case.

> What makes a member function is the conceptual association of several related functions that manipulate the same class of objects.No, that's not really true.  I've never seen a definition that cares about it only conceptually: every language supporting OOP I've ever head of lets you define functions as part of a class definition, such functions are called member functions.  Additionally, some languages allow you to define methods that aren't part of any class definition, such functions are called non-member functions.

> It does not really matter if the function's name is foo::bar() or foo__bar() as long as it is conceptually associated with an encapsulated class of objects. Even if I gave you that point, which I'm not, you're still deflecting.  You haven't shown why my point: just having functions associated with a data structure isn't enough to say a language supports the OOP paradigm.

You have to, in order to counter my point, show my claim to be logically or technically invalid, or unreasonable.  You're just changing your definitions around, please stop.  Move on or provide real substantiation for your position.

> I have already shown how you can implement several OO features without C++'s support for them.You haven't and that's not what you were tasked with.  You were tasked with showing how to implement inheritence in C using only the C preprocessor.  I haven't see any such code produced in this thread.  Another deflection.

> There may be better ways to implement it, but that does not change the fact that the design is OO.  Wonderful, **but the implementation is not, *and that is what is relevant here.***  Another deflection.

> One of the core design aspects of OOP is encapsulation.But it's not the only one.  Supporting just one core aspect doesn't mean you support the whole.  That's an inductive fallacy.

>  Syntatically in C++ it may look very different from the C syntax, but the design can be encapsulated either way, so long as you conceptually group functions with the data that they manipulate. That's not what encapsulation means.

> There is no need to show this is the case, it is patently obvious that one can do a better job the better one understands what one is doing.  You haven't shown that knowing the generated assembly will lead to better understanding.  You're stating tautologies, support your position.

> And I already covered that it is easier to do it right the first time, than to profile it and fix it later.  You haven't shown how looking at the assembly **enables someone to do it right the first time.**  Especially in the face of my claim that the issues are usually algorithmic, and high-level.

> You just explained exactly how it gives insight.  A small change at the source level can have a large change at the assembly level.  Understanding the impact of that change can influence your decision to make that change or not.That only matters if I care about the generated assembly.  You haven't shown why I should care about that in the first place.

---

### Post by cwaldbieser on 2005-12-13
Holy moly!  I am amazed this thread is *still* going on!  Could we not just say that OOP is a very loosly defined concept, and many different people in the field have different opinions about what it really means?    

I think it is pretty clear what you can and cannot do from a practical veiwpoint in C.  Expending so much energy on whether it supports a particular paradigim seems about as fruitless as an emacs vs. vi or Gnome vs. KDE debate.

It would be great if this much conversation were generated on threads like "Check out this cool new app I wrote!" or "Build a 6 CD changer with Nautilus, a couple shell scripts, and some Legos!".

---

### Post by bored2k on 2005-12-13
[QUOTE=cwaldbieser]Holy moly!  I am amazed this thread is *still* going on!  Could we not just say that OOP is a very loosly defined concept, and many different people in the field have different opinions about what it really means?    

I think it is pretty clear what you can and cannot do from a practical veiwpoint in C.  Expending so much energy on whether it supports a particular paradigim seems about as fruitless as an emacs vs. vi or Gnome vs. KDE debate.

It would be great if this much conversation were generated on threads like "Check out this cool new app I wrote!" or "Build a 6 CD changer with Nautilus, a couple shell scripts, and some Legos!".[/QUOTE]
Heh. I think I've learned more from this thread than book I'm reading itself :-P.

---

### Post by arpunk on 2005-12-13
Indeed, this thread got interesting, and LordHunter317 made some interesting points that clarifies some aspects of C/C++ that some other people tend to misunderstand.

---

### Post by matthew on 2005-12-13
[quote=bored2k]Heh. I think I've learned more from this thread than book I'm reading itself :-P.[/quote]I've been following it closely as well and learning lots. I'm currently studying C simply because I know it is the base for C++, Java, and others. I just thought having a foundation in the language that is the foundation for so many others couldn't be a bad thing. It is interesting to follow people's opinions on OOP +- definition and so on.

---

### Post by psusi on 2005-12-14
[QUOTE=LordHunter317]No, that's not really true.  I've never seen a definition that cares about it only conceptually: every language supporting OOP I've ever head of lets you define functions as part of a class definition, such functions are called member functions.  Additionally, some languages allow you to define methods that aren't part of any class definition, such functions are called non-member functions.[/QUOTE]

That is probably because you have only seen definitions in the context of a specific language.  If you step back a bit there is a broader definition.  It is like saying that the number 543,743,288,289 is not an integer because in the C language an int can not be that large, but the term integer is broader and more general than the C language, and if you ask any mathmatician, that number is an integer.  

Step back from the specifics and think a bit more general is all I'm saying.  My original point was only that a lot of people focus too much on the specific features and syntax of a given language and forget about the bigger picture.  

[QUOTE=LordHunter317]Even if I gave you that point, which I'm not, you're still deflecting.  You haven't shown why my point: just having functions associated with a data structure isn't enough to say a language supports the OOP paradigm.[/QUOTE]

I would not say that C "supports" OOP.  C was originally designed to support structured programming, so it made effort to aid people using the structured programming design patern.  It does not make any effort to aid programmers using the OO design patern.  My original point is that too often, people forget that OO is a design patern, and not a specific syntax or language feature.  

Usually when I show people how you can do polymorphism in C, where they didn't think it was possible at all, it gets them to go "Gee, I see what you mean, polymorphism IS a more general concept and not just some magic that happens when you use the virtual keyword in C++".  It gets them to think about the bigger picture.  That's the only reason that I do that demonstration, not to prove that C *supports* OOP.  

[QUOTE=LordHunter317]You have to, in order to counter my point, show my claim to be logically or technically invalid, or unreasonable.  You're just changing your definitions around, please stop.  Move on or provide real substantiation for your position.

You haven't and that's not what you were tasked with.  You were tasked with showing how to implement inheritence in C using only the C preprocessor.  I haven't see any such code produced in this thread.  Another deflection.[/QUOTE]

You have already tasked me with showing how you can do polymorphism and generic programming in C, which I did.  I don't really see any point in also showing that you can implement inheritence in C, because that was not my original point, so this is going off topic.  

[QUOTE=LordHunter317]
That's not what encapsulation means.
[/QUOTE]

From Wikipedia:

> 
A term encapsulation is often used interchangeably with information hiding, while some make distinctions between the two [1]. It seems that people, however, fail to agree on the distinctions between information hiding and encapsulation though one can think of information hiding as being the principle and encapsulation being the technique. A software module hides information by encapsulating the information into a module or other construct which presents an interface.

Information hiding reduces software development risk by shifting the code's dependency on an uncertain implementation (design decision) onto a well-defined interface. Clients of the interface perform operations purely through the interface so if the implementation changes, the clients do not have to change.


Nowhere in there does it mention anything about specific language syntax or keywords.  Encapsulation is a concept that can be implemented in many different ways.  My point here is not to review every possible way that can be implemented, only to point out that you should not forget the fact that Encapsulation is a concept that can be implemented in many different ways, not some specific syntax or feature in any specific language.  

[QUOTE=LordHunter317]You haven't shown that knowing the generated assembly will lead to better understanding.  You're stating tautologies, support your position.

You haven't shown how looking at the assembly **enables someone to do it right the first time.**  Especially in the face of my claim that the issues are usually algorithmic, and high-level.

That only matters if I care about the generated assembly.  You haven't shown why I should care about that in the first place.[/QUOTE]

I think you may be taking me too literally here.  I don't mean knowing exactly what set of assembly instructions a specific compiler with specific options on a specific platform will turn your code into.  I only meant having a general understanding of the relationship between the high level language and the machine code, so that you understand what the heck is actually going on when the code runs rather than just understanding that when you type this particular sequence of words and press enter that "Hello World" will appear on the screen.

Having a deeper understanding of how the machine works helps you understand how to program it better.  Even buisiness majors learn some visual basic, but their level of understanding usually is limited to "If I type this, and click that, then the hello world message will pop up".  This is why they don't make nearly as good a programmer as a CSE student that has learned a few things about ALUs and DACs, and messed around a bit with an osciliscope.

---

### Post by stuporglue on 2005-12-14
[QUOTE=bored2k]
What **program** do you code in? (I'm currently using Jed and sometimes Anjuta)
[/QUOTE]

I personally use Vim and love it. You'll need to play arround with various editors, but I'd recomend figguring out what features you need, then finding the editor. Features I like includ tab completion of variable names, easy to split the screen in as many ways as needed, auto indentation, syntax highlighting, and never crashing. There are actually a lot of editors that do this, but most programmers seem to end up liking Vim or Emacs. They've got steep learning curves, but the view from the top is good. :-)

---

### Post by LordHunter317 on 2005-12-14
[QUOTE=psusi]That is probably because you have only seen definitions in the context of a specific language.[/quote]*Several* languages, all with the same definition, or very compatible ones.

>  If you step back a bit there is a broader definition.Support it with both academically and industry-supported texts.  None of the literature I have supports your position.

> It is like saying that the number 543,743,288,289 is not an integer because in the C language an int can not be that large, but the term integer is broader and more general than the C language, and if you ask any mathmatician, that number is an integer.Your fallacy here is assuming I'm generalizing to one language when I'm clearly not.  My statements are general.


> Step back from the specifics and think a bit more general is all I'm saying.And I'm asking you to **support your position, *not restate it***.

> My original point was only that a lot of people focus too much on the specific features and syntax of a given language and forget about the bigger picture.Utter lies.  It was nothing of the sort.  

> I would not say that C "supports" OOP.Then why did you?  You even started in this thread making such claims.

>  My original point is that too often, people forget that OO is a design patern, and not a specific syntax or language feature. **WHich you haven't supported, and as I pointed out, *the implementation is the issue here.*  And you have made *ZERO* defense about my implementation claims.**

> Usually when I show people how you can do polymorphism in C,You've demonstrated nothing of the sort here.  


> You have already tasked me with showing how you can do polymorphism and generic programming in C, which I did.No, you haven't.  You haven't even posted a single shread of code in this thread (save for the "member" functions in C), or even any links to any code.  Claim you have again and you will be reported for trolling.

> I don't really see any point in also showing that you can implement inheritence in C,You claimed it could be done.  I'm claiming it cannot be, without ending up with either a seperate, external preprocessor, making the language not C. 

> because that was not my original point, so this is going off topic.  It is very much relevant to your original points.  You're still deflecting.

> Nowhere in there does it mention anything about specific language syntax or keywords.Neither did I.  It doesn't support your claims about encapsulation, either: that merely grouping functions and data together provides encapsulation.  It only does so if the only way to manipulate the data is via the functions.   There must be some information hiding, and you've failed to demonstrate how that exists.  Another deflection: you were simply quite wrong in your statement.  


> I think you may be taking me too literally here.  I don't mean knowing exactly what set of assembly instructions a specific compiler with specific options on a specific platform will turn your code into.**Yes, you did, *do not lie***.   Do it again and you will be reported for trolling.


> Having a deeper understanding of how the machine works helps you understand how to program it better.No, I'm not convinced that's true.  *Structure and Interpretation of Computer Programs* is a revered introductory CS text that covers very little about the machine hardware at all.

I can build all sorts of transistor circuits while knowing very little of the actual physics behind transistor operation and how semiconductors conduct charge.  Same for inductors and capacitors: the physics of how the devices function isn't relevant in basic circuit design.  

> This is why they don't make nearly as good a programmer as a CSE student that has learned a few things about ALUs and DACs, and messed around a bit with an osciliscope.Most of the best programmers I know have never hooked up a bus analzyer to a computer or build an ALU.  They just don't need to care about that level.

---

### Post by psusi on 2005-12-14
> **LordHunter317]*Several* languages, all with the same definition, or very compatible ones.

Support it with both academically and industry-supported texts.  None of the literature I have supports your position.[/QUOTE]

Have you read either *Design Patterns: Elements of Reusable Object-Oriented Software (Addison-Wesley Professional Computing Series)* or *Generic Programming and the STL: Using and Extending the C++ Standard Template Library*?

I don't have my copies of either handy at the moment ( I think they are in storage ) but IIRC, the former made a point to mention that while it was giving examples of using the design patterns ( including polymorphism ) in C++, the pattern was more abstract than the syntax of the language, and as such, was applicable ( in some sense ) to almost any language, and that it is the pattern that is important, not the syntax.  Also IIRC, the latter specifically covered how people used to use the C preprocessor to do generic programming prior to the creation of templates in C++, which is another topic we have discussed.  


[QUOTE=LordHunter317]
Your fallacy here is assuming I'm generalizing to one language when I'm clearly not.  My statements are general.[/QUOTE]

No, you were being specific by claiming that certain languages have specific definitions of ex: member functions, and that in languages without specific definitions of member functions ( C ) it is impossible to implement something that for all relevant intents and purposes, is also a member function.  

[QUOTE=LordHunter317]
And I'm asking you to **support your position, *not restate it***.
[/QUOTE]

There isn't anything to support said:**
> Utter lies.  It was nothing of the sort.  

I refer you to my original statement that began this:

> 
I also thought I would point out that most people seem to think that C = procedural, and C++ = OOP. This is not the case. C++ has language features that facilitate OOP, but you can write procedural code in C++, and you can use OOP in C.

Sure sounds to me like that was saying that OOP and C++ are not one and the same, but rather that C++ is meerly geared for it.  

> **LordHunter317]
Then why did you?  You even started in this thread making such claims.
[/QUOTE]

I don't believe I ever did say C *supports* OOP, or if I did I meant the word support a bit more loosely.  I said that you can use OOP even in a language not designed to support it, such as C, because OOP is a more general design pattern which is independant of the language used to implement it.  I presented examples of ways to implement several aspects of OOP in C as proof of that assertion.  

[QUOTE=LordHunter317]
**WHich you haven't supported, and as I pointed out, *the implementation is the issue here.*  And you have made *ZERO* defense about my implementation claims.**
[/QUOTE]

But I have.  I said that you can perform polymorphism in C by using non hidden virtual function table and this pointers.  It may not look like C++ and it may not use the virtual keyword, but it does allow you to write code that calls a function whose binding is performed at runtime rather than link time, based on the runtime type of the object being operated on.  The late binding based on runtime type is what makes it polymorphism, not the use of some magic "virtual" keyword.  

It also meets Wikipedia's definition:

> 
In computer programming, polymorphism is a mechanism allowing a given function to have many different specifications, depending on the type(s) to which it is applied.


[QUOTE=LordHunter317]
You've demonstrated nothing of the sort here.  


No, you haven't.  You haven't even posted a single shread of code in this thread (save for the "member" functions in C), or even any links to any code.  Claim you have again and you will be reported for trolling.

You claimed it could be done.  I'm claiming it cannot be, without ending up with either a seperate, external preprocessor, making the language not C. 

It is very much relevant to your original points.  You're still deflecting.
[/QUOTE]

See above re: non hidden virtual table and this pointers.  I also mentioned in passing use of C preprocessor macros for generic programming.  IIRC, you can find examples of this in the books I mentioned, but I will go ahead and try to show a rough example from memory:

```

#define make_list( type ) \
typedef struct _##type##_list_item { \
struct _##type##_list_item *prev, *next said:**
> Neither did I.  It doesn't support your claims about encapsulation, either: that merely grouping functions and data together provides encapsulation.  It only does so if the only way to manipulate the data is via the functions.   There must be some information hiding, and you've failed to demonstrate how that exists.  Another deflection: you were simply quite wrong in your statement.  

Very well, I thought I had hinted at it enough, but here is a concrete example of data hiding that provides access to the data in question **only** through the provided functions:

point.h:
```

struct point_t;
typedef point_t point;
void make_point( point *p, int x, int y );
void add_points( point *p1, point *p2, point *p3 );

```
and point.c:
```

struct point_t {
int x, y;
} point;

void make_point( point *p, int x, int y )
{
  p->x = x;
  p->y = y;
}

void add_points( point *p1, point *p2, point *p3 )
{
  p1->x = p2->x + p3->x;
  p1->y = p2->y + p3->y;
}

```

The data in the point class is hidden and the only way to access it is through the provided functions.  This satisfies the data hiding criterion, thus I assert that it is a form of encapsulation.  


[QUOTE=LordHunter317]
**Yes, you did, *do not lie***.   Do it again and you will be reported for trolling.
[/QUOTE]

Now you are telling **me** what **I** *meant*?

I am sorry if I did not make my point clearly, but that **is** what I meant.  

[QUOTE=LordHunter317]
No, I'm not convinced that's true.  *Structure and Interpretation of Computer Programs* is a revered introductory CS text that covers very little about the machine hardware at all.
[/QUOTE]

So?  There are other CS texts that cover the hardware that CS students are required to study.  Why do you think that is?

[QUOTE=LordHunter317]I can build all sorts of transistor circuits while knowing very little of the actual physics behind transistor operation and how semiconductors conduct charge.  Same for inductors and capacitors: the physics of how the devices function isn't relevant in basic circuit design.  [/QUOTE]

That deeper understanding is not **required** to design circuits, but it most definately is **helpful**.  The degree to which it is helpful is moot; understanding the foundations increases your understanding of what is built on those foundations.

Another example of this that I see in the world is kids with math.  You ask kids what the sine function is and a lot will tell you "it's this button on the calculator" or something like that.  They may be able push that button on the calculator and get the answers to pass the test, but they lack the deeper understanding that the sine function relates the ratio of the length of two sides of a triangle to the angle between them.  Having that deeper understanding is what enables you to apply the trig functions to new types of problems that you have not been walked through already and are just repeating by rote.

---

### Post by Buffalo Soldier on 2005-12-14
Dear psusi,

I found this at [wikipedia](http://en.wikipedia.org/wiki/Object-oriented_programming). I'm no expert in programming language... need clarification.. is this about the same as to what you're trying to say?

> OOP is often called a **paradigm** rather than a style or type of programming to emphasize the point that OOP can change the way software is developed, by changing the way that programmers and software engineers think about software.

The paradigm of OOP is essentially not that of programming but one of design. A system is designed by defining the objects that will exist in that system, the code which actually does the work is irrelevant to the object, or the people using the object, due to encapsulation. The challenge in OOP therefore is of designing a sane **object system**.

It should be noted that there are distinct parallels between the object-oriented paradigm and **Systems theory**. OOP focuses on objects as units in a system, whereas systems theory focuses on the system itself. In between, one may find software design patterns or other techniques that use classes and objects as building blocks for larger components. Such components can be seen as an intermediate step from the object-oriented paradigm towards the more "real-life oriented" models of systems theory.

---

### Post by psusi on 2005-12-15
[QUOTE=Buffalo Soldier]Dear psusi,

I found this at [wikipedia](http://en.wikipedia.org/wiki/Object-oriented_programming). I'm no expert in programming language... need clarification.. is this about the same as to what you're trying to say?[/QUOTE]

That hit the nail on the head.  OOP is about the high level software design.  Often UML is used to document that design.  The specifics of the language are irrelevant.  It is a common misconception that OOP is about the language, not the program design.  Heck, you can even apply OO design to non software systems where no programming language at all comes into play.  

I try to show that the specifics of the language are irrelevant by showing that one can apply OOP design patterns in C, because people usually believe this is completely impossible, beause they have a false impression that OOP is about the language.  Design transcends languages... the language is only an implementation detail.  That's all I have been trying to say ( I guess not very well ).

---

### Post by LordHunter317 on 2005-12-15
[QUOTE=psusi]I don't have my copies of either handy at the moment ( I think they are in storage ) but IIRC, the former made a point to mention that while it was giving examples of using the design patterns ( including polymorphism ) in C++, the pattern was more abstract than the syntax of the language, and as such, was applicable ( in some sense ) to almost any language, and that it is the pattern that is important, not the syntax.[/quote]Wonderful, but that doesn't disprove my point:**The pattern requires *language support* to implement.**

All it means is you don't have to have a ***fixed syntax*** to claim a language supports it.  And I never claimed that.  **What I did claim was that polymorphism cannot be done without language support.**


> No, you were being specific by claiming that certain languages have specific definitions of ex: member functions,They do.  Moreover, that definition is general and applied to all languages: the definition of a "member function" applies to all languages regardless.  You haven't shown a general definition that makes it otherwise.

> and that in languages without specific definitions of member functions ( C ) it is impossible to implement something that for all relevant intents and purposes, is also a member function.Just because it looks like a duck and quacks like a duck doesn't make it a duck.  Yes, they act like them.  But by every book definition, they're not actually member functions.

But that's not really relevant here: wonderful, I can have functions related to a specific data structure.  I can do that in any language, so no matter what I call them, *that's not a useful definition of OOP* which was my original point.

> I refer you to my original statement that began this:Which is a far cry from telling people "not to focus on the syntax of the language."

>  I said that you can use OOP even in a language not designed to support it, such as C, because OOP is a more general design pattern which is independant of the language used to implement it. But you haven't substantiate that claim.

>  I presented examples of ways to implement several aspects of OOP in C as proof of that assertion.  You have not.  You gave a weak example of "member functions".  I want inheritance as well, at the very least.  Polymorphism would be nice, but not an out and out requirement.

As I said, if we fall to a definition of OOP given by your original code, I don't feel it's a useful one: it's all-inclusive.

> But I have.  I said that you can perform polymorphism in C by using non hidden virtual function table and this pointers. Show simple code that illustrates that then, or a link to code that does.  I still dont' see how you'd trivally implement it using C and C preprocessor only.

>  The late binding based on runtime type is what makes it polymorphism, not the use of some magic "virtual" keyword.  I'm well aware of that fact.  What I'm not aware of is how you'd bloody do it in C, and you're still just claiming it's possible, not showing how.

> It also meets Wikipedia's definition:Which is also plain wrong, as it fails to talk about the dynamic binding portion.  By that definition, C++ templates are polymorphic, but they're really not as a unique function is generated at the instantation.  Polymorphic functions have the same (or a perfectly compatible) type signature regardless of the actual types used in the call.  

> See above re: non hidden virtual table and this pointers.  I also mentioned in passing use of C preprocessor macros for generic programming.  IIRC, you can find examples of this in the books I mentioned, but I will go ahead and try to show a rough example from memory:Wonderful.  I found an example of generic programming.  I'm still waiting on my inhertiance example.  The only solutions I can find online rely on alignment tricks and are unportable, AFAICT.

> Very well, I thought I had hinted at it enough, but here is a concrete example of data hiding that provides access to the data in question **only** through the provided functions:And doesn't compile. You can get around it by forcing make_point to either return a point* or a point** and dynamically allocating the memory itself, but there's no other way to do it.

So yeah, you can do encapsulation at the cost of forcing everything to the  heap.  Not a very attractive solution for C.  At this point, the value becomes questionable.  

Moreover, as your code demonstrates: doing it correctly in C is non-intuitive, nor trivial.

This still isn't what I want: a polymorphic solution that is portable for all C and doesn't involve me knowing any more type information than the parent class.

> Now you are telling **me** what **I** *meant*?No, you originally posted in your first claim raising assembly:> . All code IS compiled into assembly, and when writing code in a higher level language, it can be very helpful to remain concious of that fact, and **be thinking in the back of your mind what the assembly that your code will be compiled into looks like.**(emphasis mine).  So either we have to know what the code will translate to in assembly, or we don't.  There's not much of an in between here.

I am sorry if I did not make my point clearly, but that **is** what I meant.  

> So?  There are other CS texts that cover the hardware that CS students are required to study.  Why do you think that is?Because it's not an introductory topic nor one all programmers need to be intimiate with.  Especially in the day of platform-netural languages.

> That deeper understanding is not **required** to design circuits, but it most definately is **helpful**.Not especially.  Unless specific semiconductor physics are going to be an issue, I'm going to ignore them.  If I'm going to ignore them, they might as well not exist.  Now, knowing when I can and cannot ignore them is important after a certain point, but it's more than possible to define a range of solvable problems where they will always be safe to ignore.

FET Body effects for example, can essentially ignored in discrete devices.  They cannot be ignored in integrated circuits.

>  They may be able push that button on the calculator and get the answers to pass the test, but they lack the deeper understanding that the sine function relates the ratio of the length of two sides of a triangle to the angle between them.Hell, in 99% of my work, the fact it's the ratio between two sides of a triangle is useless definition.  It's existance as one of the primary transcidental functions is far more useful to me.

>  Having that deeper understanding is what enables you to apply the trig functions to new types of problems that you have not been walked through already and are just repeating by rote.But it doesn't, especially, because trig is trig.  And knowing that definition of sine will not help you prove any of the trig identites from any of the others.

I'd argue that for most things I've learned, not knowing anything about sine but knowing it's identities has been far more useful.  The only time the definition as a ratio of two sides of a triangle has been useful is in vector math.

---

### Post by psusi on 2005-12-15
[QUOTE=LordHunter317]Wonderful, but that doesn't disprove my point:**The pattern requires *language support* to implement.**

All it means is you don't have to have a ***fixed syntax*** to claim a language supports it.  And I never claimed that.  **What I did claim was that polymorphism cannot be done without language support.**
[/QUOTE]

And I showed how several OO patterns can be implemented in a language that is considered not to provide explicit OOP support.  If that doesn't disprove your assertion, then we're just arguing semantics, which is useless.  

[QUOTE=LordHunter317]Just because it looks like a duck and quacks like a duck doesn't make it a duck.  Yes, they act like them.  But by every book definition, they're not actually member functions.[/QUOTE]

Heh, when it looks like a duck, and quacks like a duck... and for the purposes of this discussion, I don't care that it doesn't have webbed feet... it's a duck.  

[QUOTE=LordHunter317]
You have not.  You gave a weak example of "member functions".  I want inheritance as well, at the very least.  Polymorphism would be nice, but not an out and out requirement.
[/QUOTE]

Well, I showed polymorphism, and generic programming... inheritance can be modeled using aggregation.  Not perfectly, but close enough.  Yes, there are differences, but they are mostly semantic in nature.  

[QUOTE=LordHunter317]As I said, if we fall to a definition of OOP given by your original code, I don't feel it's a useful one: it's all-inclusive.[/QUOTE]

Which was my whole point:  the definition of OOP is not dependant on language specifics. 

[QUOTE=LordHunter317]Show simple code that illustrates that then, or a link to code that does.  I still dont' see how you'd trivally implement it using C and C preprocessor only.
[/QUOTE]

I didn't say it was trivial, only that it can be done.  I fully acknowleged that it is difficult, cumbersom, and not a good idea.  

[QUOTE=LordHunter317]I'm well aware of that fact.  What I'm not aware of is how you'd bloody do it in C, and you're still just claiming it's possible, not showing how.[/QUOTE]

I said by using non hidden virtual function tables and this pointers.  I am sure that you know what that means without me having to explain it further.  Please stop claiming that I have not shown how.  If you claim that manually using virtual tables and this pointers instead of having the compiler manipulate them for you, all the while keeping that implementation detail hidden, means it is not polymorphism, then you're just arguing semantics.  

[QUOTE=LordHunter317]Which is also plain wrong, as it fails to talk about the dynamic binding portion.  By that definition, C++ templates are polymorphic, but they're really not as a unique function is generated at the instantation.  Polymorphic functions have the same (or a perfectly compatible) type signature regardless of the actual types used in the call.  [/QUOTE]

Come now... it is not *wrong*.  You might argue it is incomplete, but it is one accepted definition.  

[QUOTE=LordHunter317]Wonderful.  I found an example of generic programming.  I'm still waiting on my inhertiance example.  The only solutions I can find online rely on alignment tricks and are unportable, AFAICT.

So yeah, you can do encapsulation at the cost of forcing everything to the  heap.  Not a very attractive solution for C.  At this point, the value becomes questionable.  

Moreover, as your code demonstrates: doing it correctly in C is non-intuitive, nor trivial.
[/QUOTE]

So you found an example then?  I never said it could be done without alignment tricks and portably.  I have maintained the entire time that it is ugly, problematic and not really practical to do, but the fact that it can be done at all illustrates my point that OOP is not bound to a particular programming langage or its features ( C++ ).  


This reminds me of an argument I used to have with professors in college about recursion vs. iteration.  They maintained that certain problems can only be solved using recursion.  I showed that you can implement a recursive algorithm using an explicit stack by iterating over a std::vector rather than using the processor stack and having a function call itself.  

You can argue weather or not my solution was a form of recursion or iteration until you are blue in the face, that's just semantics.  I said that it wasn't recursion because because it did not suffer from several problems that conventional recursion did, and iteration did not ( such as the processor stack is usually limited to a much smaller size than a std::vector, and when you run out, the program crashes... with a vector you can catch the exception ).  I don't really care if you call it iteration or recursion as long as you realize that my method solves several problems that plague recursion.

---

### Post by LordHunter317 on 2005-12-15
[QUOTE=psusi]Well, I showed polymorphism, and generic programming... inheritance can be modeled using aggregation.[/quote]Not portably.  The casts you have to make to do walk up the hieharchy technically leave you in implementation-defined behavior, though I doubt there's many compilers out there that would pad before the first field, as that would be silly when you can just align them.  But unless I've misread something, there's nothing stopping them from doing so.

> Which was my whole point:  the definition of OOP is not dependant on language specifics. You've failed to show why we should accept your definition though.  I don't feel like a defintion that simply includes 'member functions' is useful.

That's meaningless as it's not a different programming technique then what's already really used, even before the advent of OOP languages.  As such, there really must be more to the definition of OOP.

> I said by using non hidden virtual function tables and this pointers.  I am sure that you know what that means without me having to explain it further.Yes, but I'm still not sure how to implement it.  I did manage to dig up a crude example though.

>   Please stop claiming that I have not shown how.You haven't.  You've said the equivalent of, "You can build an amplifier from a transistor."  Great, but that doesn't get me closer to building one.

And really, a practical example would be prudent here, I think.

> Come now... it is not *wrong*.  You might argue it is incomplete,After looking at c2, I was incorrect for attacking Wikipedia, and withdraw my statements.

> So you found an example then?  I never said it could be done without alignment tricks and portably.Which means it's not portable and can't actually be done in standard C :p

While isn't a realisitic limit to implementation but it furthers my point: some paradigms require language support to use.  Inheritance is one such device.

Remove the alighment rules on structures (or providing them, one should say) would give that support, though crudely.

>  but the fact that it can be done at all illustrates my point that OOP is not bound to a particular programming langage or its features ( C++ ).**But I never claimed it was bound to a *particular one***.  I never at any point said only one language can implement it.  What I said was in order to use it in *any language*, said language must provide some mechanism for supporting it.

Which is clearly true.  It's impossible to do inheritance in portable C.  The cast isn't assured of working.  You can't get around the slicing problem.

> You can argue weather or not my solution was a form of recursion or iteration until you are blue in the face, that's just semantics.It mets the mathematical definition of recursion, so it is.  You can't get around that.  What is true is it gets around the problem of recursive function calls.

>  I don't really care if you call it iteration or recursion as long as you realize that my method solves several problems that plague recursion.And you're the one crying out for deeper understanding of the underlying concepts, not I...

---

### Post by LordHunter317 on 2005-12-15
FWIW, by [NygaardClassification](http://www.c2.com/cgi/wiki?NygaardClassification) one can define any *program* as OO.  Sure.  I won't argue that from a design perspective, anyway.  The issue here isn't the written programs, but the languages, and applying the classification to a language isn't useful.

---

### Post by psusi on 2005-12-15
It is now clear to me that we agree on everything but the semantics.  You point out various problems with implementing OOP in C, which I completely agree with.  You may say it is technically recursion... fine... as long as you realize that it solves problems with self called functions.  You may say that the C implementations are not truely OOP... fine... as long as you realize that conceptually it amounts to basically the same thing, afterall, it looks like a duck and quacks like a duck... even though it doesn't have webbed feet.  

Just remember that OO is more of a design concept than an implementation detail... and design transcends programming languages... that's all I'm saying.

---

### Post by hod139 on 2005-12-15
I know I am posting late in this thread, but I felt like the debate wasn't really getting anywhere and I decided to contribute my own two cents.  Back in 1995, (yes this thread topic is over 10 years old and people are still arguing over it!) Bjarne Stroustrup (designer and original implementor of C++) wrote a paper titled [Why C++ isn't just an Object-Oriented Programming Language]("http://www.research.att.com/~bs/oopsla.pdf"). 

[Aside] 
Earlier posts were mentioning an implementation of generic programming as a requirement of being Object-Oriented (OO), but this is wrong.  A good definition for generic programming can be found [here]("http://www.cs.rpi.edu/~musser/gp/").  David R. Musser is one of the original authors of the C++ standard template library (STL) and a very active researcher in generics.  (He has also given me my only B in grad school :mad:)   Genericity was a desing goal of C++, but this doesn't make it an OO concept.
[/Aside]

In Stroustrup's paper, he defines his understanding of ``Object-oriented" in sections 2 and 3.  If you don't want to read the whole paper, at least read these two sections before you continue posting in this discussion.  The most important remark I can make about this thread has already been stated perfectly in Stroustrup's closing remarks (section 7), and I will conclude my post with his warning:
> I would encourage you not to make object-oriented a meaningless term.  The notion of `object-oriented' is too frequently debased
  -- by equating it with good
  -- by equating it with a single language, or
  -- by accepting everything as object-oriented 

---

### Post by LordHunter317 on 2005-12-16
[QUOTE=psusi]It is now clear to me that we agree on everything but the semantics.[/quote]The issue here is the semantics are actually important, so your handwaving of them now is disappointing.

> You may say it is technically recursion... fine... as long as you realize that it solves problems with self called functions.See, but just saying fine misses the point.  Understanding the difference between a recursive *algorithm* and a recursive *function* is important.  

> Just remember that OO is more of a design concept than an implementation detail...**No, it's *clearly both***.  Definitions for it exist in both realms.  You can't claim one and then ignore the other.

> and design transcends programming languages... that's all I'm saying.And as I've said many times, I know that, and it's bloody well irrelevant.

---

### Post by bored2k on 2005-12-16
This thread has gone way too off-topic for me to allow this to continue.

---

