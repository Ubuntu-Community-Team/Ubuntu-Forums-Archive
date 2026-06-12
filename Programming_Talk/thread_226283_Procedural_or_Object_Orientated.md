---
title: "Procedural or Object Orientated"
date: 2006-07-31
forum: Programming Talk
---

### Post by muz1 on 2006-07-31
Okay okay. I know mosty of you out there are going to say OO. Currently I program PHP (with other variants of c) and I use Procedural based programming. I have had people come at me from different angles telling me that I will not get a job as a programmer if I do not use OO. I have also had people tell me that OO is so much better than Procedural and that OO is so much more flexible.

My response is that well written code in Procedural is modular, highly flexible / re-usable. It is straight forward, easy to follow and in the situations I have seen both OO and Procedural side by side, Procedural takes less time and lines of code.

**NOTE**
I am not having a go at OO based methodolodies. It is just that if it is so great, how come no-one can explain the benefits over procedural. Then you also get these people that are stricly OO. Even a small program that can be done in afew lines Procedural they will drag out and make it in OO. What's the deal? Isn't that overkill?

I would like to learn procedral however each time I try, I end up getting a headache. I just cannot seem to break through. I keep thinking what is the point when I can do it all in Procedural

Do you know the advantages of OO? I mean do you really know the advantages? I am really interested in hearing from people that are open minded to discussing the pros and cons of both methodologies. Lets make a big deal out of it becasue I am not the only one that has been asking.

Cheers n propz
Muz1

---

### Post by thumper on 2006-07-31
I would consider myself primarily a OO person, but I will not add objects to a simple program just for the hell of it.  Do what you need to do.  Some OO languages will let you do this (not all ie Java), so use what you want.

One of the biggest gains of OO methodologies is to keep the data together with the methods that work on that data.  Also keeping the data hidden (for some definition of hidden) from outside messing around.

I'm not going to go into full details, as there are so many benefits, and I only have limited time :)  I will though add comments every now an then.

---

### Post by LordHunter317 on 2006-07-31
> **muz1 said:**
> Okay okay. I know mosty of you out there are going to say OO. Currently I program PHP (with other variants of c) and I use Procedural based programming. I have had people come at me from different angles telling me that I will not get a job as a programmer if I do not use OO.C# and Java are "OO" languages but most of their frameworks are procedural in nature.  S.W.F and ASP.NET certainly are, Struts mostly is.  The problem is that because they pretend to be OO the procedure flow is hidden from you (which is a bad thing).  They're definitely psuedo-OO frameworks.

It might be more correct to call them "event-driven", but event-driven isn't necessarily OO in nature.  

> Do you know the advantages of OO? I mean do you really know the advantages?My data is together with the code that access and works with.  It allows me to write more ***correct*** code, because I can strictly enforce how you access the data and what you can do with it.  This is impossible in procedural languages.

---

### Post by ifokkema on 2006-08-01
Another example: abstraction. Say you work with another developer on the same project. He's on the other side of the world and you can't easily sit down and discuss all implementations of the project together. But:
He's written an class that handles the GUI and you don't want to mess with it, because you do the internal work. Now you can do:

*Pseudo code*
$input = GUI::getInput();
<do what you need>
GUI::printMessage('Input accepted, action taken');
GUI::makeSound('bell.wav');
GUI::blinkScreen();

You don't have to care about how the GUI class is implemented. The only things you want to know about the class are it's methods, that is, the funtions within, and the parameters to use.
Of course this can be done by a set of functions as well:
gui_printMessage(), gui_makeSound() and gui_blinkScreen(), but if they have to share lots of data, they'll have to use global variables, which may interfere with yours. If they're in the class, the class has it's own variables that cannot interfere with yours (a class has it's own variable scope).

I don't often use classes, but for larger projects with more than one developer, it's so much easier if you're working on separate classes.

---

### Post by LordHunter317 on 2006-08-01
> **ifokkema said:**
> Another example: abstraction.You did not demonstrate abstraction, at least in formal OO terms.  You didn't really demonstrate it in more general terms either, and abstraction certainly can be achieved in procedural languages.

> You don't have to care about how the GUI class is implemented.Actually you probably do because for most tasks, the way we process and handle data is intimately tied to the way it's displayed.

You may not care about how a button or a textbox is rendered, but you care intmiately about the fact you are rendering a button or a textbox, and you need the ability to pick.

Only rarely does one develop frameworks to further abstract the presentation from the data, because it's rarely worthwhile.

> The only things you want to know about the class are it's methods, that is, the funtions within, and the parameters to use.That's never true, even with the simplest classes.

> Of course this can be done by a set of functions as well:
gui_printMessage(), gui_makeSound() and gui_blinkScreen(), but if they have to share lots of data, they'll have to use global variables, which may interfere with yours.No, that's not true in the least unless you're using a really poor language.

---

### Post by yaaarrrgg on 2006-08-01
Another advantage is it's sometimes easier (or cleaner) to solve a problem for multiple cases, or slightly different cases.  

For example, if you write a graphical widget class (corectly), it's easy to put N widget instances on the screen.  Each can be a self-contained instance that manages its own properties.  Solving a problem for one case can also solve the problem for N cases.

Also, say you need a special type of widget.  In OOP, you can extend the base class, and just override the code that is different (or add code).  It's a nice way to organize things.

---

### Post by jstueve on 2006-08-01
polymorphism
overloading
inheritance

---

### Post by ifokkema on 2006-08-01
> **LordHunter317 said:**
> That's never true, even with the simplest classes.
Because...? What did I leave out, then?

> **LordHunter317 said:**
> No, that's not true in the least unless you're using a really poor language.
Would you please show me then how to share variables within a distinct set of functions, without passing them around as parameters (since I mentioned sharing lots of data)? In C++, for example?

---

### Post by LordHunter317 on 2006-08-02
> **yaaarrrgg said:**
> For example, if you write a graphical widget class (corectly), it's easy to put N widget instances on the screen.That isn't a special property of object-oriented languages over procedural ones.  I could just have:```
for (int i=0; i<10; ++i) {
    char buf[3];
    sprintf(buf, "%d", i)
    render_button(buf);
}
```That being said, OOP would win here if we were trying to render more than just a button in my example.  But it has nothing to do with quantity.

The importance here isn't that it's eaiser to create 'N' objects, because it is not. What is important is it's eaiser to operate on objects with similiar behaviors, because you have strong typing.

> In OOP, you can extend the base class, and just override the code that is different (or add code).Sometimes you can do this.  However, composition is a far preferable technique a lot of the time (can't be as easily done in procedural) because inheritance carries a strong relationship requirement with it.     Most things don't meet the 'is-a' requirement that inheritance brings.

This is a requirement that is fundamental, but frequently misunderstood.

> **ifokkema]Because...? What did I leave out, then?[/quote]Consider any of the STL classes.  I cannot express in C++ that a std::vector is implemented as an array, but I care intimately about that fact.   Why?  Because it defines the performance characteristics of the class, which I care about when picking one collection over another.

It also defines operational characteristics.  For example, It's perfectly legal to do something like:```
std::vector<char> mystr said:**
> , "ab");
```But there's no way to describe that incredibly useful property in C++ either.  

It's impossible to express all of the semantics details we care about within the language.  We don't have any ability for providing constraints based on performance characteristics, for eaxmple.  Nor can we prove all constraints at runtime.  If an argument to a function cannot be NULL, then we cannot prove that all calls to that function will never pass a NULL at compile-time unless we make the caller of the function handle the NULL. That is passing-the-buck to the caller, though perhaps it would be more useful to do things in that manner.

[quote]Would you please show me then how to share variables within a distinct set of functions, without passing them around as parameters (since I mentioned sharing lots of data)? In C++, for example?In modern C++ you use an anonymous namespace, like so:```
namespace {
     int foo(int a) 
     {
         return a+2;
     }

     int values[128];
} // Everything in this block has file scope.
```In C, you'd use a static variable at the file-scope.

---

### Post by orlox on 2006-08-02
Also, many thechniques of software engineering based on the OO paradigm have proven very succesful when dealing with large problems....For small programs procedural works fine for me, but when I attempt to do bigger things, using OO programming allows me to get a better picure of what to do....

---

### Post by yaaarrrgg on 2006-08-02
> **LordHunter317 said:**
> That isn't a special property of object-oriented   languages over procedural ones.  I could just have:                             
```
for (int i=0; i<10; ++i) {
    char buf[3];
    sprintf(buf, "%d", i)
    render_button(buf);
}
```                                                                                                                                                        That being said, OOP would win here if we were trying to render more than just  a button in my example.  But it has nothing to do with quantity.

The importance here isn't that it's eaiser to create 'N' objects, because it is not. What is important is it's eaiser to operate on objects with similiar behaviors, because you have strong typing.


That is a very good point...  

Although also consider a case where you are working with a function written (perhaps by someone else) on the assumption that there will only be one widget.  It's very possible your code snippet would just paint the same button 10 times.  In procedural programming, one has to explicitly design the functions/code with the ability to handle multiple instances.

In OOP, this is often a natural consequence.  Of couse, even in OOP, static variables, and shared resources must still be given thought.  But this is only a subset of the work required by procedural programming, where you might also need to rewrite functions (to operate on structs/arrays), and manually track all the widget properties.

---

### Post by thumper on 2006-08-03
> **LordHunter317 said:**
> Consider any of the STL classes.  I cannot express in C++ that a std::vector is implemented as an array, but I care intimately about that fact.   Why?  Because it defines the performance characteristics of the class, which I care about when picking one collection over another.
What do you mean by this?  The standard says that std::vector is implemented in contiguous memory.  What are you wanting to express?

---

### Post by ifokkema on 2006-08-03
> **LordHunter317 said:**
> Consider any of the STL classes.  I cannot express in C++ that a std::vector is implemented as an array, but I care intimately about that fact.   Why?  Because it defines the performance characteristics of the class, which I care about when picking one collection over another.
Sure, but in my example, when you work with another developer on a project, I'd trust (depending on how I know this other developer to code) the other developer to make a good implementation of his class, and I'll settle for the method signatures (return value, method name, used parameters).

> **LordHunter317 said:**
> In modern C++ you use an anonymous namespace, like so:
Thanks. Namespaces... handy stuff. Sadly, my C++ programming course kinda skipped namespaces :roll:

---

### Post by Mathiasdm on 2006-08-03
A good explanation: [http://csis.pace.edu/~bergin/patterns/ppoop.html](http://csis.pace.edu/~bergin/patterns/ppoop.html)


I think the benefits of OOP lie mostly in making it easier to modify large projects.

Both procedural and OOP have their advantages and disadvantages. Procedural, imho, is easier to use to start a project. However, once the project becomes more complex, it gets harder to change parts of the program.
With OOP, this is (again: imho) easier.

---

### Post by LordHunter317 on 2006-08-03
> **yaaarrrgg]Although also consider a case where you are working with a function written (perhaps by someone else) on the assumption that there will only be one widget.[/quote]I don't see how that's relevant at all here.  Unless the function does something stupid like retain a static handle to the object, it doesn't matter.  You use composition to write functions that operate on groups of widgets:```
extern bool widget_painter(struct widget*) said:**
> In procedural programming, one has to explicitly design the functions/code with the ability to handle multiple instances.One has to do that with object-oriented code too.

> **thumper said:**
> What do you mean by this?Exactly what I said.  There's no way in C++ to express a public contract to say that a std::vector is implemented in contiguous memory and that if I take a pointer to the first element, I can move forward to the next one.

More importantly, even if that wasn't in the standard, there's no way in C++ to express the performance characteristics in code either.

The whole issue is: what can I express in code?  Not everything that defines an interface (even in determining 'is-a' relationships) can be expressed in code.

[quote=ifokkema]Sure, but in my example, when you work with another developer on a project, I'd trust (depending on how I know this other developer to code) the other developer to make a good implementation of his class, and I'll settle for the method signatures (return value, method name, used parameters).[/quote]You completely missed the point.

---

### Post by Paul Bramscher on 2006-08-03
I've coded since the mid-80's, got a BSci in CSci and write primarily LAMP stuff for a living in a Big-10 university setting.  And I mainly write procedural code.  Why?  A couple reasons -- keep in mind that computers ultimately don't need architectural abstraction, objects, polymorphism, inheritance, etc. to get work done.  The only abstraction they need is byte code and machine code.  Anything more abstract than this is to serve the **programmer**, and is of no use for the machine itself.  (Indeed, it's just more code for the compiler to deal with.)

So does OO help **YOU** get the job done?

We, as engineers, don't ultimately model the "real world" (unless we are writing simulation software).  Ordinarily we are implementing things that don't naturally happen on their own.  Also, I've come to conclude that problems don't exist as physical objects -- they are things we wish would happen.  So one of the intrinsic challenges in religious adherence to OO is that (a) you can't always point toward a "real world" object and (b) you are implementing things that, by their nature, often don't exist with real world corrollaries.

There are some interesting criticisms about so-called "design patterns" also: [http://en.wikipedia.org/wiki/Design_pattern_(computer_science)#Criticism](http://en.wikipedia.org/wiki/Design_pattern_(computer_science)#Criticism).  One of the problems is that excessive code resusability may indicate excessive (useless) layers of abstraction.  There's something to be said for only writing code necessary to address the problem at hand (no patterns).  Too many patterns in a single system, and maybe you aren't re-referencing things properly.  Too many identical patterns cross-system, and maybe you have too many systems.  Abstraction (check Wikipedia) is an exercise in picking & chosing aspects for a particular problem in mind.  In doing this, you don't want to err on the side of excessive, nor incomplete, information capturing of what it is you're trying to represent .  These are deep issues, not for the faint of heart to address in their entirety.

So does OO abstraction help you in a particular problem?  It doesn't necessarily help your hardware (just gives it more work).  There **are** cases when I find OO to be a natural model: especially handling user-state and most game/AI/simulation applications -- as well as handling GUI.  That's quite a bit of the computing world, but not everything.  Do you need to create a string object and String.split (java solution) or strtok (c solution)?  Which is easier for you?  The c solution is certainly lower-level (and therefore easier) for the machine.

I wouldn't focus too much on the need to learn OO to get a programming job.  Certainly you'll need to know it, and be able to put it on your resume -- since this industry is laden with buzzwords.  But if you're a structural/procedural guru and get the job done faster than someone who can talk objects all day but not finish his project, then you have an upper hand.  I tend to prefer hybrid and free languages like C++ and PHP, which allow me to use either structural/procedural or OO, depending on the problem at hand and what makes the most sense to me -- rather than the language telling me off the bat what sort of architecture I must use.

---

### Post by LordHunter317 on 2006-08-03
> **Paul Bramscher said:**
>  A couple reasons -- keep in mind that computers ultimately don't need architectural abstraction,/quote]They most certainly need this one.  An ISA is an abstraction of the hardware machine, to a certain degree.

> The only abstraction they need is byte code and machine code.No, hardware is way more complicated than that and both the physical silicon and the software care intimately about those details.  A list of the valid machine instructions is not remotely enough.

[quote]We, as engineers, don't ultimately model the "real world" (unless we are writing simulation software).Not true.  We model the real world all the time; and if we're taking a data-oriented view, we model the real world the majority of the time.

Just because something isn't tangible doesn't make it real.  Account ledgers are real, despite only being stored in a database.   Business rules are real, despite being ideas only  written down on paper or in code.

> So one of the intrinsic challenges in religious adherence to OO is that (a) you can't always point toward a "real world" object and (b) you are implementing things that, by their nature, often don't exist with real world corrollaries.OO philosophy is not about a or b, and anyone who tries to tell you it is just doesn't understand OOP.[1]

> One of the problems is that excessive code resusability may indicate excessive (useless) layers of abstraction.That's not true in the least.  Genericity is a good thing.  However, I'm not convinced that OOP is the best way to achieve that, especially in statically-typed languages.  The fact that .NET 2.0 and Java 5 support a limited form of generics lends support to that view.

> There's something to be said for only writing code necessary to address the problem at hand (no patterns).I care to point out the Gang of Four found the patterns they documented emperically.  They didn't come up with them, they looked at code, found things people did "naturally" that were repeated, and then abstracted that code.

Use of patterns is perfectly fine.  When you're using a std::vector, you're using a pattern.  Or a std::list.  Or any STL algorithm.

Algorithms are patterns by their nature.  

What is inappropriate is try to coerce things into patterns that do not fit, and that does happen frequently.  But that doesn't mean patterns or thier usage is bad.  Like all things, their usage must be weighed.


> It doesn't necessarily help your hardware (just gives it more work).That's not necessarily true.

>  Which is easier for you?String.split(), because it's not broken.

>   The c solution is certainly lower-levelAny properties of it being lower-level have to do with the language and not the code written in it.

>  (and therefore easier) for the machine.That's not necessarily true.  Machines don't work like that.  

As a friendly note, you really ought to take some computer architecture classes before talking about hardware anymore.

[1]Intial OO languages, like Simula, were intended for discrete event simulations and were usually modeling tangible phenomenon.  However, formal OO definitions and theory isn't limited to that in the least, nor even mentions "real-world" in the definition.

---

### Post by Paul Bramscher on 2006-08-03
What else can a CPU process except its instruction set, registers, etc.??  You completely missed my point: this is the only abstraction the machine needs.  Anything beyond that is for the benefit of the programmer, the machine simply doesn't need it -- since it only cares about the fundamental states of electric gates.

BTW: Please don't make suggestions that I take a computer architecture course.  As I indicated, I work in a Big-10 research environment and have been coding for 20 years.  I can claim to know the machine fairly well at this stage -- thank you.

> **LordHunter317 said:**
> [QUOTE=Paul Bramscher;1333610] A couple reasons -- keep in mind that computers ultimately don't need architectural abstraction,/quote]They most certainly need this one.  An ISA is an abstraction of the hardware machine, to a certain degree.

No, hardware is way more complicated than that and both the physical silicon and the software care intimately about those details.  A list of the valid machine instructions is not remotely enough.

Not true.  We model the real world all the time; and if we're taking a data-oriented view, we model the real world the majority of the time.

Just because something isn't tangible doesn't make it real.  Account ledgers are real, despite only being stored in a database.   Business rules are real, despite being ideas only  written down on paper or in code.

OO philosophy is not about a or b, and anyone who tries to tell you it is just doesn't understand OOP.[1]

That's not true in the least.  Genericity is a good thing.  However, I'm not convinced that OOP is the best way to achieve that, especially in statically-typed languages.  The fact that .NET 2.0 and Java 5 support a limited form of generics lends support to that view.

I care to point out the Gang of Four found the patterns they documented emperically.  They didn't come up with them, they looked at code, found things people did "naturally" that were repeated, and then abstracted that code.

Use of patterns is perfectly fine.  When you're using a std::vector, you're using a pattern.  Or a std::list.  Or any STL algorithm.

Algorithms are patterns by their nature.  

What is inappropriate is try to coerce things into patterns that do not fit, and that does happen frequently.  But that doesn't mean patterns or thier usage is bad.  Like all things, their usage must be weighed.


That's not necessarily true.

String.split(), because it's not broken.

Any properties of it being lower-level have to do with the language and not the code written in it.

That's not necessarily true.  Machines don't work like that.  

As a friendly note, you really ought to take some computer architecture classes before talking about hardware anymore.

[1]Intial OO languages, like Simula, were intended for discrete event simulations and were usually modeling tangible phenomenon.  However, formal OO definitions and theory isn't limited to that in the least, nor even mentions "real-world" in the definition.

---

### Post by Daverz on 2006-08-03
"Pure" OO languages were OK 15 years ago, but I wouldn't use a language that didn't have first class functions and closures now (unless you paid me).  A lot of ugly Java boilerplate could be eliminated if it had those features.

---

### Post by LordHunter317 on 2006-08-03
> **Paul Bramscher said:**
> What else can a CPU process except its instruction set, registers, etc.??It has to talk to devices and memory, it has to have standards for where initial program execution starts from, it has to have standards for bus moderation for SMP and DMA. 

> You completely missed my point: this is the only abstraction the machine needs.But it's not.  We as hardware designers and programmers care about more than the machine code.  We must care.  It's not optional.

Some programmers may be able to ignore such details, but that doesn't change the fact that the abstraction is richer than just machine language.

> Anything beyond that is for the benefit of the programmer,Bus moderation, a detail they usually have zero (or very limited control over) is not.  However, they certainly need it to implement higher order operations like DMA transfer for a device driver.  They care about how memory is arranged to provide optimal access for NUMA machines, something that usually has nothing to do with the processor, as it doesn't see such details.  But we obviously care about them.

> As I indicated, I work in a Big-10 research environment and have been coding for 20 years.  I can claim to know the machine fairly well at this stage -- thank you.Clearly, you do not.  You wouldn't make such statements if you did.  An ISA covers way more than just the valid machine language instructions and covers way more than stuff that occurs solely on the CPU.

---

### Post by yaaarrrgg on 2006-08-03
> **LordHunter317 said:**
> I don't see how that's relevant at all here.  Unless the function does something stupid like retain a static handle to the object, it doesn't matter.

Well, also functions may store data in variables outside of the functions scope (for example in the page scope of a cgi script).  This does matter, especially in languages like PHP.

> **LordHunter317 said:**
> You use composition to write functions that operate on groups of widgets:```
extern bool widget_painter(struct widget*);

void
widget_array_painter(struct widget*, int len)
{
    for(int i=0; i<len; i++) {
        widget_painter(widget+i);
    }
}
```


Yes, if all the functions accept struct pointers, there is little difference.  That is a good solution.... if you are writing the function from scratch in C.

But that wasn't my question.  How do you know a pre-existing function will accept a struct?  Suppose you are given a calendar widget that's written in PHP.  If you have to make multiple instances of it on a page, one approach (which is probably easiest) would be to wrap a class around the code.

> **LordHunter317 said:**
> One has to do that with object-oriented code too.


True, although for me, it's easier with an OOP approach.  I'd have to think harder if I avoided OOP.  But to be honest, if I wrote more procedural code, I might feel the opposite way.

---

### Post by LordHunter317 on 2006-08-04
> **yaaarrrgg said:**
> Well, also functions may store data in variables outside of the functions scope (for example in the page scope of a cgi script).Hence my comment about doing something dumb like storing things in static scope (at least, not doing it carefully).

> Yes, if all the functions accept struct pointers, there is little difference.One would presume they do, if they're meant to work with one object.  

The reality is that most APIs aren't designed to hold things in static memory, because it's just too poor.  The ownership issues are too onerous, as the standard C library has taught us.

> But that wasn't my question.  How do you know a pre-existing function will accept a struct?In C, the compiler will tell you.  In other languages, the same way you learn for everything else.

>  one approach (which is probably easiest) would be to wrap a class around the code.If it's using static scoping, this doesn't solve the problem.

---

### Post by Paul Bramscher on 2006-08-04
You can Google my resume if you care (I always use my real name) though it doesn't include my cv or publications.  In addition to a CSci degree, I have a degree in the behavioral sciences -- which assists me quite a bit in modeling systems.  It's posts like your "take an architecture course", "you must not have credentials if you say things like that", orthodoxical viewpoints without give-and-take, etc. which usually keep my sort **clear and wide** from open discussion forums.

The function of a CPU in standard von Neumann architecture is summed up fairly well in the Wikipedia entry ([http://en.wikipedia.org/wiki/Central_processing_unit)](http://en.wikipedia.org/wiki/Central_processing_unit)).  And, certainly, the modern computer could be fully represented as pebbles on a beach.

For my own part, I'd suggest some material by contemporary philosophers of computing (Minsky, Searle, etc.).  You can come to your own conclusions, but having done some graduate work in that field, also, I've come to conclude that the CPU is purely about physics.  It manipulates physical states.  What else can a physical entity manipulate? DeCartes was never able to reconcile his dualist view of the world, a mechanism by which the ethereal/abstract/ghostly can interact with the physical.

Probably most modern scientists, engineers, many philosophers, etc. are physicalists or materialists.  We "abstract" to model or blueprint, but the model isn't what we build in the end.  In the end, it's a physical rearrangement of matter, as real as any other thing, and the "abstraction" is purely in the eye of the beholder.  The machine has no capacity whatsoever for abstraction, it deals with physics.  It's clear that some OO fundamentalists are reading too much of their own minds into their machines (e.g. Pygmalion).  Don't imagine there's a ghost there, it's just states of switches

So with this preparation, and much more, I reiterate that programming paradigms (beyond assembly/byte/machine code) are for our benefit -- or not as the case may be -- not the machine's.

---

### Post by LordHunter317 on 2006-08-04
> **Paul Bramscher said:**
> It's posts like your [...] "you must not have credentials if you say things like that",:rolleyes: That's not what I said.  It's not remotely close to *anything* I've said. 

> orthodoxical viewpoints without give-and-take, etc.There's plenty of room for give-and-take when you're in the right ballpark.  You're not currently even in the right city, much less the ballpark.  But forgive me if I'm not too budging on farily fundamental architecture stuff.

> You can come to your own conclusions, but having done some graduate work in that field, also, I've come to conclude that the CPU is purely about physics.  It manipulates physical states.  What else can a physical entity manipulate? DeCartes was never able to reconcile his dualist view of the world, a mechanism by which the ethereal/abstract/ghostly can interact with the physical.How is any of this relevant?  It's not relevant in the least in terms of abstracting the hardware to the programmer, as it *doesn't enable the programmer to program the hardware.* This is just a deflection.

> The machine has no capacity whatsoever for abstraction, it deals with physics.And?  No one ever claimed it did.  Abstraction of hardware is purely a human constract to enable us to be better programmers, or enable us to do eaiser programmer, or both.  That fact doesn't need to be explicity stated.

> So with this preparation, and much more, I reiterate that programming paradigms (beyond assembly/byte/machine code) are for our benefit -- or not as the case may be -- not the machine's.But they're clearly not.  There's more to assembly programming than just knowing the machine code.  You have to know all sorts of details that aren't expressed in the language (and cannot be) like:[list][*]Endianness.[*]Interrupt triggering behavior: level, edge, or both.  If both, how do you determine which behavior and how do you change it (if you can)?[*]Memory alignment and access issues.  Many architectures have penalties for accessing memory that's not aligned, or simply cannot do it at all.  Such things aren't encoded into the machine language (or the assembly, frequently) but the programmer must be aware of that hardware detail and explictly program for it.[/list]So no, there's more to the hardware than just "assembly/byte/machine code".  Once again, it comes down to the fact we can't express every relevant detail in our programming language.

You obviously didn't read my prior post, where I listed all sorts of other things programmers must care about to a certain degree that aren't even related to the CPU.

In other words, you're wrong simply because **there is more hardware in a computer than just a CPU.**.  So obviously, there has to be more details than just the machine language.  Even the definition of a Von Neumann machine is clear on this.

---

### Post by yaaarrrgg on 2006-08-06
> **LordHunter317 said:**
> Hence my comment about doing something dumb like storing things in static scope (at least, not doing it carefully). 

Fair enough...  I misunderstood, since page scoped variables are not necessarily static, or dumb. :)

> **LordHunter317 said:**
> If it's using static scoping, this doesn't solve the problem.

It's just an approach, not a general solution.

Also, the philosophical discusion has turned out to be very interesting.  My degree was actually in Math / Analytic Philosophy.  A few comments:

> **Paul Bramscher]
We, as engineers, don't ultimately model the "real world" (unless we are writing simulation software).
[/QUOTE]

That has an interesting element of truth, I think.

In OOP, "objects" have qualities that "real objects" don't really have.  For example:

1. Objects in reality are not constant, but always changing.   For example, if an apple sits long enough, it becomes "not-an-apple."  We can     attach constant labels to objects, but real objects are always drifting out from underneath the labels.

2. Properties of an real object are not one-dimensional.  We might view quantity, for example, as a one dimensional property of a set, but this  is a  simplification.  How do you compare two small apples to one large apple?  Or one rotten apple to one good apple?

3. Property values are not really binary/crisp, as much as a matter of degree.  If we remove an atom from an apple, is it the still '1' apple?   What if we remove more atoms?


[QUOTE=LordHunter317 said:**
> 
Not true.


Statements are never 100% true or false.

What rule are you using to map this statement's truth value to 1 or 0?  For example the statement, "if you play in the street, you will get hit" might be false 99% of the time.  Nevertheless, the small amount of truth is very important.

> **LordHunter317 said:**
> 
We model the real world all the time; and if we're taking a data-oriented view, we model the real world the majority of the time.

We don't model reality as much as we model our ideas, or ideas about reality. 

You seem to be expressing two common views: "Naive Realism is true" and "Platonic Forms are real."  Both views have problems and are not         generally regarded as true.

> **LordHunter317 said:**
>  Just because something isn't tangible doesn't make it [not] real. Account ledgers are real, despite only being stored in a database. 

This isn't clear.  If material tangibility is not an   important criteria for realness, what is?  Given your use, the term "real" becomes        applicable to anything.

> **LordHunter317 said:**
> Business    rules are real, despite being ideas only written down on paper or in code.  

This isn't necessarily the case either.  The physical aspects involved in such processes are real, but it's not clear the rules themselves are   (removing the physical aspects).  In general, its not clear that any abstract entity is real.  Are numbers real?  If so, do imaginary numbers    exist in the real world?  Or the number 'zero' (if so how can 'nothing' exist)?  These things, I think, are only psychological.

> **LordHunter317 said:**
>  OO philosophy is not about a or b, and anyone who tries to tell you it is just doesn't understand OOP.[1]

[1]Intial OO languages, like Simula, were intended for discrete event simulations and were usually modeling tangible phenomenon.  However,       formal OO definitions and theory isn't limited to that in the least, nor even mentions "real-world" in the definition.

Formal defintions?  Who cares if the phrase "real world" isn't mentioned?  The fact that the theory has been disconnected from reality does not  refute that the claim that this is an intrisic problem of OOP.

Most axiomatic theories, like Euclidean geometry, are modeled after the real world initially.  At some point, the mathematical truth becomes     relative to the starting assumptions/definitions of formalized axiomatic framework.  But in applying the theory to the reality, there's always   an instrinic problem.  Theory and reality are always slightly at odds.  THis is not just a problem of OOP, but Mathematics as well.

Philosophical discussions are never clear cut, black and white issues.  I doubt it's even possible to define what a 'computer' even is, in a way that doesn't overly restrict the term to a particular physical instantiation, or include too many things.  For example, I view the human brain   as a kind of 'computer', but not an abacus.  A human brain does not have the hardware interupts you mentioned, and neither does an abacus.

Although, I think it's a mistake to write off the philosophical argument just because details about hardware were oversimplified.  Future computers might operate in an entirely different manner than you describe.

---

### Post by LordHunter317 on 2006-08-06
> **yaaarrrgg said:**
> Fair enough...  I misunderstood, since page scoped variables are not necessarily static, or dumb. :)They are static, at least in the C meaning of 'static' for file-scoped variables.   My fault for not being clear, the details of static aren't known to everyone.

> It's just an approach, not a general solution.My point sort of was it's not an approach at all.  Everything you've described can be done in procedural code just as easily, and most of your reasoning against procedural code has been when someone's doing something incorrectly.  But the OOP equivalent isn't immune to those issues either.

> 1. Objects in reality are not constant, but always changing.   For example, if an apple sits long enough, it becomes "not-an-apple."Sure, and if you're interested in that, then your object has to model the passing of time, which is easy enough.  You'd likely then create several objects to represent the state of a decaying apple.  You'd then use some sort of factory method to take the current apple state and hand you the next one.

The issue here is people misunderstand how to apply OOP to a problem.  People see 'apple' and say, "I should write a class to model apples."  This is wrong, because you're not modeling apples at all.  You're modeling *the decay of an apple.*  That means you need a class that models apple decay.  A small amount of thought on that premise shows that you either need a "DecayingApple" object that represents the amount of decay as some quantity (e.g., a percent) or you need multiple discrete objects to represent the discrete states of decay you're interested in.

> We can     attach constant labels to objects, but real objects are always drifting out from underneath the labels.And if you encouter this problem it means your design is wrong.  Simple enough.

> We might view quantity, for example, as a one dimensional property of a set, but this  is a simplification.Not if all we're interested in is the set.  This is an issue of apply the question to the right problem.

> How do you compare two small apples to one large apple?  Or one rotten apple to one good apple?Here then we're no longer interested in quantity.  We're interested in some subjective measure of quantity, so you write code to measure that.  Your error here is you're shoehorning a definition that simply doesn't fit the problem space.   If I'm not interested in count I don't have to provide it, there is no onus on me to do so.  

> 3. Property values are not really binary/crisp, as much as a matter of degree.Which is why we've developed number systems to allow us to express arbitrary values with sufficent precision.

> If we remove an atom from an apple, is it the still '1' apple?   What if we remove more atoms?Again, the answer is really dependent on what you decide and what code you want to write.  In some situations, 1 cell may be sufficent to create an Apple object.  In others, not so much.


> Statements are never 100% true or false.And?  the statement you're replying to isn't an absolute. 

> If material tangibility is not an  important criteria for realness, what is?Exists in some form outside the domain of the computer program?  That would include all input and output of the machine to a "human", which is probably as good as any definition when working with computers.  One might be willing to extend that to anything that *can* exist in some form outside the computer.  That's a bit better, because it includes things that we could, for example print, but choose not to do so.

Obviously, the definition has a lot of intentional play in it to model specific situations.  A physicist doing bomb simulations is going to have a different view from a systems programmer writing drivers, from a web guy designing pages.

Still, I feel this is probably the best view for a programmer to take, because it puts a clear distinction between code we write that exists purely in the computer and to enable us to do computation (e.g., a linked list) and code we write that models the "real world": our thoughts, our ideas, whatever computations we need the computer to do.  That distinction can be useful, because we can abstract the former to a greater degree and apply it to more cases.  For example in C++, it's possible to write a templated reference counting class that can apply to *any* object that needs reference counting, regardless of problem space.  My decaying apple (our "real" object) can't be applied outside of my problem space.

I'm not sure it's not worth debating along this path really. Even if I'm wrong, Paul's premise (We're not modelling real world objects) doesn't prove his two points.  Why?[list][*]There's no onus in OOP design to model real-world objects (e.g., C++ standard library).  std::istream isn't "real" anymore than other piece of code, yet it's OOP in nature.  It's certainly not a dog or a human.[*]There's no onus to use real world  corrollaries.  Ultimately, you use whatever model best fits the problem you're solving.  Even if you're modeling an unquestionably real world phenomenon, you rarely model it that accurately or precisely or even all of it.  You're usually only interested in some part and model just that.[/list]

> Formal defintions?  Who cares if the phrase "real world" isn't mentioned?Because his entire point (AFAICT) is OOP is only good for modeling "real world" things.  That's clearly not the case.  A linked list doesn't have much purpose outside the realm of a computer, yet I can model it with OOP.  It's certainly not a a cat, or a dog, or a chicken, or a human, or a plant.


> The fact that the theory has been disconnected from reality does not refute that the claim that this is an intrisic problem of OOP.But it's not.  There's no problem here.  There's no requirement whatsoever.  People who believe that is a requirement simply do not understand OOP whatsoever.  And the standard libraries of OOP languages provided incredible support for that.  Why?  The core things they all provide are purely computational constructs: input and out facilties, data structures, algorithms.

Can it be used to model cats or dogs or chicken or business processes?  Yes.  Is that the only thing it's good for?  No.

> Although, I think it's a mistake to write off the philosophical argument just because details about hardware were oversimplified.His permises are wrong, and I'm not sure you're reading what I'm saying.

From the view of *how do we program a computer,* we cannot abstract the hardware to "just machine code".  That statment, *removed from everything else he said* is wrong.  I didn't really discount the rest of his argument because he said that because it really doesn't matter.  I did discount other parts, but I showed why I did. I don't know why he latched on to that statement oppossed to the others I made, but it was really independent.

> Future computers might operate in an entirely different manner than you describe.And?  I'm farily certain none will allow us to abstract to the level of "just machine code."  I don't need to generalize to prove his statement incorrect.  I can give a specific counter-example.

---

### Post by yaaarrrgg on 2006-08-09
You have good ideas here.  

I actually read Paul's argument as saying something completely different than what you had read.  I think your take is interesting though...

> **LordHunter317 said:**
> My point sort of was it's not an approach at all.  Everything you've described can be done in procedural code just as easily, and most of your reasoning against procedural code has been when someone's doing something incorrectly.  But the OOP equivalent isn't immune to those issues either.


That's a good point. 

> **LordHunter317 said:**
> The issue here is people misunderstand how to apply OOP to a problem.  People see 'apple' and say, "I should write a class to model apples."  This is wrong, because you're not modeling apples at all.  You're modeling *the decay of an apple.*  That means you need a class that models apple decay.  

Good point.  Also interesting ... you are working with a different set of concepts than I am.

In my view, I would say you're really modeling the "idea" of the process, not the process itself.  This is a subtle difference, and I usually ignore adding the qualification.   For example, on my view,  knowledge about reality is always filtered through our ideas like such:

    "I" <-> ideas and perceptions <-> real world  

This is how I read Paul, when he said "we don't model the 'real world'."  So, I interpreted the whole argument as saying something completely different, like the following (cogent or not):

It would be difficult for a human to create an executable directly with a hex editor.  Humans do much better with a high-level computer language that models higher-level concepts (like 'if', 'then', 'true',  'false', etc).  Object Oriented Programming (OOP), for example,  introduces even higher level concepts 'object', 'property', and 'method'.  The question is: what programming language paradigm offers the greatest "conceptual" advantage for the human?

What we model, ultimately, are not objects at all, but abstract ideas.  For example, we might model the idea of an apple, or the idea of an "decay process," or the idea of a linked list (which is perhaps a more mathematical idea).  These ideas  really are not objects at all, anymore than the number 'zero' is an object.  They are just ideas.  Even the concept 'object' is just an idea.

Applying "objects" analysis to an idea adds another layer of abstraction.  Sometimes, it may both add complexity, and can even introduce problems into the model if we are not careful.

On the other hand, procedural programming can solve most problems equally well, and sometimes with fewer layers of abstraction.  For example, rather than modeling the idea of a decaying apple as a series of DecayedApple objects generated by a factory method, we might model it as an array of floats.

Which paradigm is better really depends on the problem.  With problems like GUI's, widgets, games, etc, it may be conceptually easier with an OOP approach, since these domains contain entities with map naturally to OOP objects.  Other problems do not map so easily however.  But overall, there is no clear conceptual advantage to a pure OOP approach.  

> **LordHunter317 said:**
> Here then we're no longer interested in quantity.  


Oh, I'm always interested in quantity. :) 

> **LordHunter317 said:**
> We're interested in some subjective measure of quantity, so you write code to measure that.  Your error here is you're shoehorning a definition that simply doesn't fit the problem space.   If I'm not interested in count I don't have to provide it, there is no onus on me to do so.  


I think we might be talking about slightly different issues here.  In my view, all measures of quantity are subjective, to a degree.  

You can model real apples as "Apple" or "DecayingApple."  But in reality, all apples are really decaying apples aren't they?  This means the familiar problem of "comparing apples to oranges" pops up even when comparing two apples.  This is not a problem at the modeling level, but in reality.  Quantity and quality are bound together intrinsically.  For a real world example, consider the "hanging chad" debacle in Florida's Bush/Gore 2000 election. 

> **LordHunter317 said:**
> Which is why we've developed number systems to allow us to express arbitrary values with sufficent precision.


True... most things modeled as a int would really be more accurately modeled as a float.

> **LordHunter317 said:**
> And?  the statement you're replying to isn't an absolute. 


I was misunderstanding you here.

> **LordHunter317 said:**
> Still, I feel this is probably the best view for a programmer to take, because it puts a clear distinction between code we write that exists purely in the computer and to enable us to do computation (e.g., a linked list) and code we write that models the "real world": our thoughts, our ideas, whatever computations we need the computer to do.  


I actually saw both cases as modeling ideas (where the abstractness of the ideas differ), but I like the way you have expressed this.  I will give this more thought as well .

> **LordHunter317 said:**
> His permises are wrong, and I'm not sure you're reading what I'm saying.


I had a gestalt shift. :)  I wasn't able to piece together your line of thought from the interpersed comments.

---

### Post by LordHunter317 on 2006-08-09
> **yaaarrrgg said:**
> You can model real apples as "Apple" or "DecayingApple."  But in reality, all apples are really decaying apples aren't they?But if oyu're not interested in decay, you gain nothing from modelling them as "DecayingApple".  That's the whole point: you model only the portions of reality you care about and ignore the rest. If all you're interested in is a count of number of apples on each tree in a orchard, regardless of quality, then you don't care about decay.  So don't model it.

That's the point.  Computer representations of reality inherently lack detail. 

> Quantity and quality are bound together intrinsically.Sometimes yes, and then you have to consider it.  But not always.

> True... most things modeled as a int would really be more accurately modeled as a float.Sometimes, yes, sometimes no.  I was thinking more along the lines of bounded-error and arbitrary-precision number systems.  There's a reason we don't use floats in banking.

---

### Post by yaaarrrgg on 2006-08-09
> **LordHunter317 said:**
> That's the whole point: you model only the portions of reality you care about and ignore the rest. 

I agree.  Although, this makes all models, to a degree, subjective. If two  models generate different numbers, the one that take more factors into consideration is objectively *more correct*.

> **LordHunter317 said:**
> There's a reason we don't use floats in banking.
 
People mistakenly believe that integers are accurate? :)

---

### Post by LordHunter317 on 2006-08-09
No, we don't use integers either.  Generally some sort of fixed-width decimal system is used, or BCD, or some other system.

---

### Post by muz1 on 2006-08-11
Hmmmmm
I think that I am starting to see some interesting things.
The one thing that I can see coming to light is the term ***modular***.

A system is comprised of three main marts. 

1. Input
2. Throughput
3. Output

For a system to work, the right inputs need to be entered.
The centre part then takes the inputs, manipulates them and hands the result(s) to the last part.
Stage 3 simply then outputs the result(s).

For each class or function, we need to first check that we have the right data to work with. Then we take that data, do what needs to do and finally pass it out the other end.

When we write modular code, its main aim is to be flexible / versatile which saves us time and effort. After all, why reconstruct the wheel.
Alot of clients (and I have asked) that require modules to be written, don't care what methodology is used as long as the documentation states what inputs are needed and what outputs are created. If they do what is needed, then people don't really seem to care.

This is in no means an excuse to say that I can stick to function based programming and do not need OO.

I use procedural / function based methodologies, I control what inputs and outputs are created and I also output the data needed. My code is portable and can easily be adapted to other needs.

So getting back to the main aim of the thread. What am I doing now that can be done better in OO? I am really wanting to know what the hype is all about.

Thanks for your input so far. I really appreciate it.

Cheers
muz

---

