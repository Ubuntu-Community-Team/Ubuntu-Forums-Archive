---
title: "The Advantages(Criticism?) of Object Oriented Programming/Design"
date: 2010-08-14
forum: Programming Talk
---

### Post by noobermin on 2010-08-14
I've at least understood OOP concepts and implementations since I was in high school, and used them only in pet projects (although at this point in life, all I really do are pet projects).

So my standpoint may not be the most experienced, but still, I find OOP philosophy to at least lead to very bloated and inefficient implementations. Really, I'd think that the benefits of OOP can be matched if not surpassed in procedural languages such as C if programmers just are more careful and more diligent.

However, I have very little professional experience with OOP anyway , so I'm willing to open myself to be convinced for the other side. I'm going to get more familiar with class design anyway since I've been thinking of getting into game design, and it's largely popular there.

EDIT: used better words.

---

### Post by dwhitney67 on 2010-08-14
> **noobermin said:**
> ...

So my standpoint may not be the most experienced, but still, I find OOP philosophy to at least lead to very bloated and inefficient implementations. Really, I'd think that the benefits of OOP can be matched if not surpassed in functional languages such as C if programmers just are more careful and more diligent.

...

Yay!  One less competitor in the job market.

---

### Post by Bachstelze on 2010-08-14
C: it's a functional language.

---

### Post by noobermin on 2010-08-14
So that's it? Just because everyone else uses it?

EDIT: Yes...I said that it is a functional language...

---

### Post by djheadley on 2010-08-14
I was one of those old-school programmers who felt completely lost when things went OOP.  I just couldn't get past having to run 5 lines of required code in order to run 2 lines of my code and no I can't give you any examples because I lost everything in a flood a couple of years ago.

---

### Post by wojox on 2010-08-14
Reusability, cleaner code, and you can intertwine C with C++. It's hybrid like that.

---

### Post by Bachstelze on 2010-08-14
> **noobermin said:**
> 
EDIT: Yes...I said that it is a functional language...

Yes, and it's not. ;)

---

### Post by noobermin on 2010-08-14
> **Bachstelze said:**
> Yes, and it's not. ;)

Okay...I guess I meant imperative/procedural. Sorry about that.

> **wojox said:**
> Reusability, cleaner code, and you can intertwine C with C++. It's hybrid like that.

I understand the re-usability, but can you explain how it's cleaner? (not a challenge, just a question)

---

### Post by eveningsky339 on 2010-08-14
OOP, *if done correctly*, results in less lines of code, modularity, and reusability.  I like procedural programming because it's much simpler, but larger programs can become unwieldy.  

I will say that C++'s use of classes and objects can be confusing.  I didn't understand OOP until I learned Python.

---

### Post by worseisworser on 2010-08-14
Hm, trying to think of an example. Let's see if this works ..

How would you express the following scenario in C:

* You have shapes.
* You have a function that accepts shapes.
* This function wants to tell each shape passed to it to *draw* itself.


..? E.g., using CLOS I'd go about this something like this:

```

CL-USER> (defclass shape () ())
#<STANDARD-CLASS SHAPE>

CL-USER> (defclass circle (shape) ())
#<STANDARD-CLASS CIRCLE>

CL-USER> (defclass rectangle (shape) ())
#<STANDARD-CLASS RECTANGLE>

CL-USER> (defmethod draw ((circle circle))
           (write-line "code for drawing a circle goes here"))
#<STANDARD-METHOD DRAW (CIRCLE) {1003D4D161}>

CL-USER> (defmethod draw ((rectangle rectangle))
           (write-line "code for drawing a rectangle goes here"))
#<STANDARD-METHOD DRAW (RECTANGLE) {1003E35691}>

CL-USER> (defun handle-shapes (list-of-shapes)
           (map nil #'draw list-of-shapes))
HANDLE-SHAPES

CL-USER> (handle-shapes (list (make-instance 'circle)
                              (make-instance 'rectangle)))
code for drawing a circle goes here
code for drawing a rectangle goes here
NIL

CL-USER> 

```


So **no matter** what kind of shape we're dealing with we should always be able to tell it to *draw* itself. This is better than having several *drawRectangle*, *drawCircle* etc. functions, no?

---

### Post by noobermin on 2010-08-14
> **worseisworser said:**
> Hm, trying to think of an example. Let's see if this works ..

How would you express the following scenario in C:

* You have shapes.
* You have a function that accepts shapes.
* This function wants to tell each shape passed to it to *draw* itself.

code...

So **no matter** what kind of shape we're dealing with we should always be able to tell it to *draw* itself. This is better than having several *drawRectangle*, *drawCircle* etc. functions, no?


It is no different than what happens in reality.

And also, you could use function pointers.

---

### Post by wojox on 2010-08-14
> **noobermin said:**
> 
I understand the re-usability, but can you explain how it's cleaner? (not a challenge, just a question)

It may be a personal preference, but I can look at the source and follow along better than some of that spaghetti code I've run across.

---

### Post by worseisworser on 2010-08-14
> **noobermin said:**
> It is no different than what happens in reality.

I'm not sure what you mean here. In "reality", you are fiddling with electrons and stuff representing 0 and 1, but the point is to forget about this and work on a (or several) levels above it -- just as is the point to work on a (or several) levels above other "realities" you deem uninteresting given some current context.

> **noobermin said:**
> And also, you could use function pointers.

How would it look like?

---

### Post by noobermin on 2010-08-14
Okay.

You have a "shape" structure. It contains point data and dimension data. Point data can be vertices for a polygon or the center for a circle. Dimension can be be dimensions or radius, etc.

And it also contains function pointers to rendering commands/ scale commands, etc. You then make corresponding functions for each type. Then you make a creation function for each possible shape that sets these up. Then you make a single creation function that could give the user what s/he wants and switches between the creation functions.

So you can't avoid a switch statement (or a set of if-else if's). I guess I can say that's worthy of some complaint, although it's really not that terrible unless you have 250 shapes. Then again, that would imply a poor design in trying to make too many specific objects when a general object (such as a poylgon) would suffice.

Plus, I'm sure you guys know of a few APIs out there in C that aren't too messy, like GTK+ and SDL. Applying SDL_Foo_Foo2...is just as wordy as AClass.ItsBaby.ItsGrandChild etc. And I'm in favor of uses such wordiness anyway because it keeps the programmer aware of what s/he's doing.

---

### Post by worseisworser on 2010-08-14
> **noobermin said:**
> So you can't avoid a switch statement (or a set of if-else if's). I guess I can say that's worthy of some complaint, although it's really not that terrible unless you have 250 shapes. Then again, that would imply a poor design in trying to make too many specific objects when a general object (such as a poylgon) would suffice.

You do not want to think or talk about (program) polygons when writing the AI machinery for some game.

Again, and if you are to do anything even remotely non-trivial in programming; you *must* be able to build constructs that allow you to forget about parts not relevant or interesting to your current context!

OOP, but also other paradigms -- helps here.

edit:
Note that I agree with you; nothing is really needed; everything is optional and "the same" from the machine or end-results' point of view, but from our point of view as humans dealing with this in terms of language used to describe constructs that make sense for both the machine and our minds; moving a couple of levels up is very useful.

I sometimes like to think of it as analog vs. digital; converting an analog signal into a digital one removes some data from the original source signal, but it is worth it; it very much *adds* way beyond what was lost to what we (or us via machines) can deal with or do.


edit2:
Oh, and there's a lot more to OOP than what's found in e.g. C++. If you do not need C++ -- stuff like CLOS and the MOP found in Common Lisp is very interesting for instance. AMOP (the book about MOP) was described by Alan Kay as the most important book about OOP out there. Still, if you go for C++, the OOP support found there is not something to ignore.

---

### Post by trent.josephsen on 2010-08-14
Let me say to the OP that I completely understand where you're coming from and sympathize with you.  It's my position that OOP is nothing but unnecessarily confusing when taught (as it often is) to new programmers; it's one of the reasons <flamebait>Java is a bad first language</flamebait>.

And examples (like the shape thing) that try to show why OOP is so great are most often hideously contrived.  Let's look at the explanation:  you have a function that takes a shape and tells the shape to draw itself.  Sure, that is only really possible with OOP.  But the idea of telling an object to do something is an inherently OO-based idea.  If the program were well designed from a functional or procedural standpoint, you'd never run into a problem like that.  (The key being "good design" -- bad design will inevitably trash the best of intentions.)

That said, OOP comes into its own on extremely large projects (thousands, not hundreds, of lines).  I wouldn't use OOP for most things I do, but most things I work on are comparatively quite small (hundreds of lines; some only tens of lines).  OOP can lend more stability and flexibility to a design than procedural programming.  (Functional programming might be a contender in this area, but that's another topic.)

Finally, don't mix C with C++, or your maintenance programmers will curse you and your descendants to the ends of the Earth.

---

### Post by worseisworser on 2010-08-14
> **trent.josephsen said:**
> Let's look at the explanation:  you have a function that takes a shape and tells the shape to draw itself.  Sure, that is only really possible with OOP.  But the idea of telling an object to do something is an inherently OO-based idea.  If the program were well designed from a functional or procedural standpoint, you'd never run into a problem like that.  (The key being "good design" -- bad design will inevitably trash the best of intentions.)

I think this is backwards; paradigms aren't created (or discovered) to invent problems for them to solve; the problems are there even if the paradigms to solve them in a nice or nicer fashion ("good design") are lacking.

"Best design possible given some *current* constraints" is another matter though.

---

### Post by myrtle1908 on 2010-08-14
> **trent.josephsen said:**
> It's my position that OOP is nothing but unnecessarily confusing when taught.

Agreed.  Not to mention the stupid and often impractical examples so commonly preached - such as Dog extends Animal extends Being extends Lifeform extends SomeOtherRubbish - are so pointless they would drive the common man to to nonchalance.

---

### Post by worseisworser on 2010-08-14
> **myrtle1908 said:**
> Agreed.  Not to mention the stupid and often impractical examples so commonly preached - such as Dog extends Animal extends Being extends Lifeform extends SomeOtherRubbish - are so pointless they would drive the common man to to nonchalance.

But why? It matches how we sort and deal with information outside programming. 

What's the alternate route to take in your example? How would you denote the property of being alive or not "across" these things in your example?

----
edit: 
Note that you are somewhat misquoting him; he is talking about this in context of *newbie programmers* who perhaps shouldn't be exposed to OOP *initially*, but other paradigms like the imperative or procedural one.

---

### Post by myrtle1908 on 2010-08-14
> **worseisworser said:**
> But why? It matches how we sort and deal with information outside programming. 

What's the alternate route to take in your example? How would you denote the property of being alive or not "across" these things in your example?

I don't have the answer.  I wish I did.  In my opinion the common  analogies are simply too trivial, inherently obvious and are not interesting enough to hold attention.

---

### Post by trent.josephsen on 2010-08-14
> **worseisworser said:**
> But why? It matches how we sort and deal with information outside programming.

Baloney.  I hear this claim from every angle and not once have I heard anyone back it up.  It takes considerable thought to construct a hierarchy like Corgi extends Dog extends Mammal extends Animal [...]  Other associations, like "oh, that's the receipt for the screws I bought at Home Depot the other day" (to take a random example from among the crap on my desk at the moment) are complex, border on instantaneous, and don't fit nicely into an OO hierarchy.  My brain works more like a relational database.  But hey, maybe I'm just odd.

Solve problems with your brain, not with code.  Figure out how to solve a problem before plunging headfirst into some paradigm or another.  This is true no matter what you're looking at (OO, procedural, functional, whatever), and is the main point of my post.

---

### Post by noobermin on 2010-08-15
I guess it depends on how you think. Believe it or not, I'm actually somewhat of a visual person, so I can understand how OOP might be more intuitive. Things and beings like a dog can have a state (wet, hungry, barking) and perform actions(bite, sit, fetch). To think that the dog being wet is part of the dog you're looking at but information on how the dog sits is somewhere else in the room is somewhat counter-intuitive...to me(but would be really interesting, actually!)

Again, I'm not complaining too much about understanding OOP. It's more of how it could lead to needlessly bloated code (although, I guess it is true it depends on how it is implemented) and  slower programs(which is what I really meant when I said inefficient...sorry!).

We've talked a bit about the bloat...here's my complaints about the slowness. Often times, stuff like RTTI are needed to enforce object oriented-ness and make sure I don't try calling a dog->bark() on a dishwasher. Now for scripting languages and VM languages like java, it adds overhead, but you're on a interpreter already, so it's not like you're going to make it that much faster. Still, for C++, I'm more of the opinion that it should be up to the programmer to keep mind of those things like it was in C.

---

### Post by bcz on 2010-08-15
IMHO

You are absolutely right

However there is a shortage of competent programmers

What OO does is force programmers to follow a set of standards which help to keep things in order.

This allows lots of average programmers to work on large projects producing large programs which require powerful computers to produce the same results that were previously produced by less powerful computers, often in less time

Just last week I read a 3 page document from the web.  It was 1.5 Mb in size and contained only text..  no graphics whatsoever.  An efficient system would have used less than 20K characters; or  maybe 10K

Lufthansa airlines was able to handle 30 seat bookings per second in the 1970s on a computer about as powerful as a Pentium 1.

Computer systems are now so inefficient that a system 100 times as powerful is too slow to do a child's homework.

Where do we go from here?

---

### Post by crampus on 2010-08-15
So called "OO programming paradigm' is just one of the many weired and wonderful ideas that are continuously appearing and fading away in all technical production fields, not just computer software building. Some of them are ridiculed, some of them are tried and some are not, some of them are rejected by the industry after a short spell of popularity, some survive and get surprisingly entrenched despite their obvious shortcomings. OO programming is simply one of those that survived. 

Why?

OO trades the burdening of the run-time CPU with many, many unnecessary instructions and CPU cycles for one thing and one thing only: programmer's competency. It forces a simple-minded hierarchical modularization and code invocation scheme upon a programmer that lacks the skill and experience to achieve the same if not put in a straitjacket. It reduces significantly a very high cost item for any enterprise: that to properly train, guide and supervise the beginners.  
 
OO is not an "engineering thing", its a "production management thing". It is just one among the many, to be found in all industries and all engineering disciplines. 

crampus

---

### Post by DanielWaterworth on 2010-08-15
> **bcz said:**
> IMHO
However there is a shortage of competent programmers

What OO does is force programmers to follow a set of standards which help to keep things in order.

This allows lots of average programmers to work on large projects producing large programs which require powerful computers to produce the same results that were previously produced by less powerful computers, often in less time

Spot on. C++ and OOP in general were created for the masses. Average programmers can't handle C. When they try to they introduce bugs that are difficult to track down and waste the time of competent coders.

I do disagree on one point though, sometimes trading CPU time for development speed is a good idea. Therefore, if all programmers were competent then we'd all be coding in C when we needed fast code and python when we needed code fast.

---

### Post by howlingmadhowie on 2010-08-15
> **worseisworser said:**
> But why? It matches how we sort and deal with information outside programming. 

What's the alternate route to take in your example? How would you denote the property of being alive or not "across" these things in your example?

----
edit: 
Note that you are somewhat misquoting him; he is talking about this in context of *newbie programmers* who perhaps shouldn't be exposed to OOP *initially*, but other paradigms like the imperative or procedural one.

no, i'm not sure we think like that. unless you allow multiple inheritance and prototyping.

an example: think of something green. immediately you have a whole hierarchy of green things in your head, all interwoven. 

how about: try to compare 10 people's noses. automatically you create a categorisation with similarities and differences with respect to different parts of the nose. 

notice i'm talking about things which could be modelled very well in an oop fashion. things which are green could implement an interface, or noses could be instances of a class.  but how we deal with them---how we create and modify and compare them---has little to do with object oriented programming concepts.  you could say it's more like a relational database with millions of tables for cross products of other tables.

---

### Post by r-senior on 2010-08-15
Posted on a C forum in 1972 ...

Far out man! C was created for the masses. Average programmers can't handle machine code. When they try to they introduce bugs that are difficult to track down and waste the time of competent coders.

Posted on an Eniac forum in 1946 ...

Top ho! Punch cards were created for the masses. Average programmers can't handle switches and patch cables. When they try to they introduce bugs that are difficult to track down and waste the time of competent pluggers.

Posted on a Mesopotamian programming forum in 2400BC ...

Spot on. The abacus was created for the masses. Average programmers can't handle numerals in cuneiform script. When they try to they introduce bugs that are difficult to track down and waste the time of competent scribes.

Posted on a mesolithic programming forum ...

Ug. Ug. Woo-man. Ug.

Well, we had to start somewhere. ;)

---

### Post by nvteighen on 2010-08-15
OOP is one if the several ways to handle a certain problem. If you think that a problem is better seen as objects interacting with eachother, then you use OOP. If you think that the problem is better seen as a series of actions that are executed in some order, then use procedural programming. If you think that maybe mixing both ideas is the way to go, then mix them...

But of course, in order to be able to know what to choose, you have to learn them.

And that's all there is: OOP is no magical tool suited for everything (how many times Java programmers have to create procedural code by using static class methods...). Also, procedural programming is not lame or primitive: sometimes a nice small procedural code makes more sense than an overhyped OOP version of it (this is something you see in Python code... too many peolpe just don't realize that sometimes you don't need a class!).

---

### Post by worseisworser on 2010-08-15
> **trent.josephsen said:**
> 
[quote=worseisworser]But why? It matches how we sort and deal with information outside programming.

Baloney.  I hear this claim from every angle and not once have I heard anyone back it up.  It takes considerable thought to construct a hierarchy like Corgi extends Dog extends Mammal extends Animal [...]  Other associations, like "oh, that's the receipt for the screws I bought at Home Depot the other day" (to take a random example from among the crap on my desk at the moment) are complex, border on instantaneous, and don't fit nicely into an OO hierarchy.  My brain works more like a relational database.  But hey, maybe I'm just odd.
[/quote]

I did drink a lot of beer before going to bed yesterday, but I did not expect to wake up to Bizzaro World.

Perhaps I should just say "OK" and move on -- but if you head over to the Wikipedia page for Metal, [http://en.wikipedia.org/wiki/Metal](http://en.wikipedia.org/wiki/Metal) , you'll notice that your iron (probably) screws belong to a category called `transition metals'.

Further, if you head over to the Wikipedia page for Animal, [http://en.wikipedia.org/wiki/Animal](http://en.wikipedia.org/wiki/Animal) , you'll notice that various animals are categorized in various sub-kingdoms and are a part of (super-)kingdoms.

This *is* how humans deal with data and information no matter what you say or think; we place things that share characteristics into shared categorized so we can reason about them and their common properties in a similar manner without getting overloaded with tedious repetition.


> **trent.josephsen said:**
> Solve problems with your brain, not with code.  Figure out how to solve a problem before plunging headfirst into some paradigm or another.  This is true no matter what you're looking at (OO, procedural, functional, whatever), and is the main point of my post.

This is not "plunging headfirst into some paradigm or another" -- it is a totally obvious and simple way to deal with information and data; we've been doing this for 100s of years.

I'm not going to explain how this works in detail because you seem to be not interested and instead just angry at something you do not want to understand -- but your receipt *would of course not* be part of the *item*-category/hierarchy; it would be a *property* of some item-category/class; exactly as you said; it would be a relation, and this is of course possible using OOP and it is known as composition: [http://en.wikipedia.org/wiki/Object_composition](http://en.wikipedia.org/wiki/Object_composition) 

This is *very* basic stuff, so perhaps you should be careful critiquing something you quite clearly do not know a lot about.

---

### Post by worseisworser on 2010-08-15
> **noobermin said:**
> Now for scripting languages and VM languages like java, it adds overhead, but you're on a interpreter already, so it's not like you're going to make it that much faster. Still, for C++, I'm more of the opinion that it should be up to the programmer to keep mind of those things like it was in C.

Just gonna add that languages like Java tend not to be interpreted, and interpretation is not a property of the language anyway, but the implementation; any language can be interpreted or compiled.

---

### Post by worseisworser on 2010-08-15
> **bcz said:**
> IMHO

You are absolutely right

However there is a shortage of competent programmers

What OO does is force programmers to follow a set of standards which help to keep things in order.

This allows lots of average programmers to work on large projects producing large programs which require powerful computers to produce the same results that were previously produced by less powerful computers, often in less time

Just last week I read a 3 page document from the web.  It was 1.5 Mb in size and contained only text..  no graphics whatsoever.  An efficient system would have used less than 20K characters; or  maybe 10K

Lufthansa airlines was able to handle 30 seat bookings per second in the 1970s on a computer about as powerful as a Pentium 1.

Computer systems are now so inefficient that a system 100 times as powerful is too slow to do a child's homework.

Where do we go from here?

The so called non-average programmers you speak of could implement better compilers, and indeed; they are. That's the proper long-term way to solve many of these problems.

---

### Post by worseisworser on 2010-08-15
> **crampus said:**
> So called "OO programming paradigm' is just one of the many weired and wonderful ideas that are continuously appearing and fading away in all technical production fields, not just computer software building. Some of them are ridiculed, some of them are tried and some are not, some of them are rejected by the industry after a short spell of popularity, some survive and get surprisingly entrenched despite their obvious shortcomings. OO programming is simply one of those that survived. 

Why?

OO trades the burdening of the run-time CPU with many, many unnecessary instructions and CPU cycles for one thing and one thing only: programmer's competency. It forces a simple-minded hierarchical modularization and code invocation scheme upon a programmer that lacks the skill and experience to achieve the same if not put in a straitjacket. It reduces significantly a very high cost item for any enterprise: that to properly train, guide and supervise the beginners.  
 
OO is not an "engineering thing", its a "production management thing". It is just one among the many, to be found in all industries and all engineering disciplines. 

crampus

Perhaps you're one of those people who think OOP was "invented" in 1995 when Java came out. Truth is; it has been around for a long, looong time; way back from the 1960's.  ...and several of the other paradigms have been around for a long, long time also.

Each paradigm is discovered and used for a *reason* -- and you're wrong; it is of course discovered or "invented" for the engineering and design aspect of a project. Outside people like managers cannot possibly have the insight to be able to discover or "see" these things *in the first place*. You've got things backwards, but I understand you're angry as you're yet another one who has barely dipped your toe outside the imperative/procedural paradigm.

PS: I can argue quite well for **several other** paradigms also; I do not "support" one paradigm in particular.

---

### Post by worseisworser on 2010-08-15
> **howlingmadhowie said:**
> no, i'm not sure we think like that. unless you allow multiple inheritance and prototyping.


I doubt MI and prototyping would help; we do not know how our minds work internally and that is not what I'm talking about.

I'm talking about how we categorize, organize and express information _after_ our minds have come to a conclusion about something somehow.

..and of course I consider implementations of OOP that support MI and prototyping; CLOS + MOP (programmable; so can support several types of OOP mechanisms or customize already existing ones) for instance.

> **howlingmadhowie said:**
> you could say it's more like a relational database with millions of tables for cross products of other tables.

Oh, but do take care to notice that OOP is more than inheritance of data, and classification hierarchies; there is also composition.

---

### Post by DanielWaterworth on 2010-08-15
> **worseisworser said:**
> PS: I can argue quite well for **several other** paradigms also; I do not "support" one paradigm in particular.

I do. Instructions are dead! Long live data-flow programming!

---

### Post by worseisworser on 2010-08-15
Data-flow is *very* interesting, DanielWaterworth, but I'll stick with low-level stuff (haa..) like structurers, classes and OOP when I deal with my boring old data. :)

edit: 
Here's my implementation of dataflow or "reactive" paradigm programming support for Common Lisp; [http://github.com/lnostdal/SW-MVC](http://github.com/lnostdal/SW-MVC)

In addition to input-triggered flow or handling, it supports output triggered evaluation (with optional caching); sort of like lazy eval in Haskell.

---

### Post by howlingmadhowie on 2010-08-15
i think my main problem with oop is that it's rather difficult to extract combinational how-to knowledge without making arbitrary decisions. 

an example. 

let's say we have a frying pan and an egg. now i want to cook the egg. who should know how the egg is to be cooked? is that a method which should reside in FryingPan or in Egg? and what if i now want to cook a sausage. Where should this knowledge be put?

---

### Post by DanielWaterworth on 2010-08-15
> **worseisworser said:**
> Data-flow is *very* interesting, DanielWaterworth, but I'll stick with low-level stuff (haa..) like structurers, classes and OOP when I deal with my boring old data. :)

I think it will hit the mainstream when either cores rocket (likely) or FPGA coprocessors become the norm (extremely unlikely).

---

### Post by DanielWaterworth on 2010-08-15
> **howlingmadhowie said:**
> i think my main problem with oop is that it's rather difficult to extract combinational how-to knowledge without making arbitrary decisions. 

an example. 

let's say we have a frying pan and an egg. now i want to cook the egg. who should know how the egg is to be cooked? is that a method which should reside in FryingPan or in Egg? and what if i now want to cook a sausage. Where should this knowledge be put?

Sounds like a visitor pattern.

---

### Post by worseisworser on 2010-08-15
> **howlingmadhowie said:**
> i think my main problem with oop is that it's rather difficult to extract combinational how-to knowledge without making arbitrary decisions. 

an example. 

let's say we have a frying pan and an egg. now i want to cook the egg. who should know how the egg is to be cooked? is that a method which should reside in FryingPan or in Egg? and what if i now want to cook a sausage. Where should this knowledge be put?

It should be the result of consideration of both things:

[http://en.wikipedia.org/wiki/Multiple_dispatch#Multiple_Dispatch_Examples](http://en.wikipedia.org/wiki/Multiple_dispatch#Multiple_Dispatch_Examples)

I say "both things", but in other cases you might want to dispatch based on more than just two "contexts", and this is possible to do; just keep adding "contexts" or parameters! :)

edit:
You can think of it this way; a method does not have to belong to just _one_ class or object (yes, indeed you can dispatch based on objects/instances (not just their types) also! -- and even meta-objects). Again, there is *much more* to OOP (and other paradigms) than what is found in just Java and C++.


edit3:
I'll quote Alan Kay;
"Actually I made up the term "object-oriented", and I can tell you I did not have C++ in mind." -- [http://en.wikiquote.org/wiki/Alan_Kay](http://en.wikiquote.org/wiki/Alan_Kay)


..this is *not* an attack (from me) on Java or C++ in general, but an attack on the assumption of what OOP is and can do.


edit2:
I'll probably be "attacked" with a ton of potential and obvious problems from people making quick assumptions mentioning this; but ultimately, which method(s) is(are) picked is well-defined and, indeed, programmable or customizable ( [http://static.nostdal.org/hyperspec/Body/m_defi_4.htm](http://static.nostdal.org/hyperspec/Body/m_defi_4.htm) ); it is knowns as a "method combination".

---

### Post by lisati on 2010-08-15
> **howlingmadhowie said:**
> i think my main problem with oop is that it's rather difficult to extract combinational how-to knowledge without making arbitrary decisions. 

an example. 

let's say we have a frying pan and an egg. now i want to cook the egg. who should know how the egg is to be cooked? is that a method which should reside in FryingPan or in Egg? and what if i now want to cook a sausage. Where should this knowledge be put?
+1 

Electric pan or one that's stove top? If it's stove top, gas or electric (or something else)?

In other words, the programmer has to make decisions to make. This includes choosing the best tool from those available to get the job done.

And yes, I have used punched cards.

---

### Post by worseisworser on 2010-08-15
> **DanielWaterworth said:**
> I think it will hit the mainstream when either cores rocket (likely) or FPGA coprocessors become the norm (extremely unlikely).

Yes, I'm experimenting with this stuff (m-m-m-m-multi-core!) combined with STM ( [http://en.wikipedia.org/wiki/Software_transactional_memory](http://en.wikipedia.org/wiki/Software_transactional_memory) ) on a 24 core AMD system with 64GB RAM. Very, very cool stuff indeed. :)

edit:
I actually need a better GC now; more concurrency. Even though a parallel+concurrent GC is sometimes more expensive on a single core machine, it seems much better as the number of cores increase.

---

### Post by trent.josephsen on 2010-08-15
> **worseisworser said:**
> <lots of stuff snipped>
Okay, I'm not going to address every point you made or didn't make, only to clarify my meaning a little.  You pushed one of my buttons by saying, "this is the way you think."  People are always telling me they know how I think, and after 20-odd years of it I've decided that none of them have any clue what they're talking about.  From the teacher who gave me a bad grade because I wouldn't write notes in color to the people who say GUIs are easier to use than shells, they're all frauds.  If you really knew how I think, that would make you smarter than me, and you would have better things to do than argue with inferior intelligences.

howlingmadhowie made my real point better than I did.

My second paragraph was not directed towards you; it was merely an admonition to choose a proper paradigm only after solving the problem.  There seems to be a strong emphasis on using OOP to model *everything*, on the pretext that "this is how your brain works".  This works moderately well for some things and miserably fails for others.

---

### Post by DanielWaterworth on 2010-08-15
> **worseisworser said:**
> ...a 24 core AMD system with 64GB RAM. Very, very cool stuff indeed. :)

*is jealous*

> **worseisworser said:**
> edit:
I actually need a better GC now; more concurrency. Even though a parallel+concurrent GC is sometimes more expensive on a single core machine, it seems much better as the number of cores increase.

This has been my experience too. There seems to be a J-Shaped Curve. At about 4 cores it becomes worth the effort to go multi-threaded, but it's a huge paradigm shift.

---

### Post by worseisworser on 2010-08-15
> **trent.josephsen said:**
> Okay, I'm not going to address every point you made or didn't make, only to clarify my meaning a little.  You pushed one of my buttons by saying, "this is the way you think."  People are always telling me they know how I think, and after 20-odd years of it I've decided that none of them have any clue what they're talking about.  From the teacher who gave me a bad grade because I wouldn't write notes in color to the people who say GUIs are easier to use than shells, they're all frauds.  If you really knew how I think, that would make you smarter than me, and you would have better things to do than argue with inferior intelligences.


Ok, this (hierarchies and categories) being a common way for us to organize or *present* information and data is probably more accurate.


> **trent.josephsen said:**
> 
My second paragraph was not directed towards you; it was merely an admonition to choose a proper paradigm only after solving the problem.  There seems to be a strong emphasis on using OOP to model *everything*, on the pretext that "this is how your brain works".  This works moderately well for some things and miserably fails for others.

Ok, yes. I do not like the "one paradigm fits all" idea, either; it is wrong.

---

### Post by CptPicard on 2010-08-15
OOP got a bad name because marketers/bureaucratic managers got their hands on it. I never quite got it early on when all seemed to be a bunch of UML and design patterns which were almost symptomatic -- that is, you needed the patterns to get around the language...

However, in all simplicity, we're just dealing with an extensible type system where types may have a hierarchy, plus a way of resolving a function call dispatch given a data item of some type. That's all there is to it. The "drumstick" problems come from the single-dispatch paradigm; multiple dispatch generally feels like a much more sane way to do things (IMO) but of course in that case the method is no longer strictly "owned" by one class.

Personally I find that even in C most of my code ends up needing some sort of method resolution for my data structs eventually, so I end up needing *some* kind of an object system -- be it in the Objective-C or C++ family... generally it results in storing function pointers in the structs. Object-orientedness is not such a big leap if you consider that most structured data in a computer has a "struct" as is basic type, and then you just add not just data, but operation references too.

And this idea that non-lazy, great programmers automatically choose to code in C or assembler just doesn't seem to die. Sure, you can build a cathedral by essentially piling small stones on top of each other, but I fail to see the point in that -- and just because someone is willing to do it by that method does not mean that they have any understanding of how the big picture architecture is going to behave; that is, they may not be able to put those small stones together into anything genuinely functional.

---

### Post by dantefs on 2010-08-15
I agree with comments above about not generalising on how people think. My early programming experiences didn't go much further than scripting languages and didn't elect to do computing at university. I ended up working almost exclusively with SQL in my job and when I did eventually come to learn C# I found the OOP approach really difficult to really *grok*. 

This didn't surprise me, but when I did finally make progress I was surprised by how much my day-to-day SQL suffered at first. A weekend spent working on a C# project took longer to "recover" from than times when I've had 2-3 weeks without writing any SQL at all. 

I'm used to things like syntax differences tripping me up or simply having no memory of what the Windows version of grep (or whatever) is called. But this felt much more fundamental, like thinking relationally was actually *harder*.

Speculating hugely, these different models could require slightly different configuration in terms of brain chemistry/neural connectivity (or whatever). In that case, the fact that your current paradigm seems to suit your thought process would be like the old (rubbish) joke:
> Boy 1 : You know, I'm glad my mom called me Billy.
Boy 2 : Why?
Boy 1 : Because that's what everyone calls me.

---

### Post by noobermin on 2010-08-16
> **r-senior said:**
> Posted on a C forum in 1972 ...

Far out man! C was created for the masses. Average programmers can't handle machine code. When they try to they introduce bugs that are difficult to track down and waste the time of competent coders.

Posted on an Eniac forum in 1946 ...

Top ho! Punch cards were created for the masses. Average programmers can't handle switches and patch cables. When they try to they introduce bugs that are difficult to track down and waste the time of competent pluggers.

Posted on a Mesopotamian programming forum in 2400BC ...

Spot on. The abacus was created for the masses. Average programmers can't handle numerals in cuneiform script. When they try to they introduce bugs that are difficult to track down and waste the time of competent scribes.

Posted on a mesolithic programming forum ...

Ug. Ug. Woo-man. Ug.

Well, we had to start somewhere. ;)

Okay, I just had to give you grats for that. That was very funny.

 Being high level isn't bad if it fits your application...so I'm starting to be convinced of the other side a bit for larger apps (I've asked similar questions across the web), but I still think the issues are there. The question I still have is whether it meets is disadvantages (unneccesary (at times) bloat, slower speeds because of the environment needed for OOP (large heap, RTTI)). Some of the answers here say it does, especially in team management, which is fine IMO.

I'd say more, but this thread is probably about dead and it's almost 3 am :P

---

### Post by EMR on 2010-08-16
> **noobermin said:**
> I've at least understood OOP concepts and implementations since I was in high school, and used them only in pet projects (although at this point in life, all I really do are pet projects).

So my standpoint may not be the most experienced, but still, I find OOP philosophy to at least lead to very bloated and inefficient implementations. Really, I'd think that the benefits of OOP can be matched if not surpassed in procedural languages such as C if programmers just are more careful and more diligent.

However, I have very little professional experience with OOP anyway , so I'm willing to open myself to be convinced for the other side. I'm going to get more familiar with class design anyway since I've been thinking of getting into game design, and it's largely popular there.

EDIT: used better words.

Well, really, the main reason I'm into OOP is that I mostly write games and simulations.  In the end, that is what OOP was designed for.  Sure, you *Can* write it all in C with Structs, but that is lots of work for one programmer, and adding any more programmers, unless they're also mind readers, won't end well.

Now think about this:
Most games are written in C++ now-even John Carmack's engines!  You don't have to go overboard and make every different kind of item in the game it's own class, but classes will make your life much easier when writing some games.  I do mean some-Tetris would be fine without OOP, but I'd sure like it when writing anything where large numbers of things are on screen, moving, like space invaders or asteroids.

---

### Post by worseisworser on 2010-08-16
One important thing people working on trivial or small projects miss is that even when working with a huge and complex project alone you'll *actually* be working in a sort of team; the other people are *previous versions of yourself* -- aka., you will *not* remember everything you where thinking and/or doing one or two years ago.

I bet some people here have **never** experienced this; I bet some even gasp at the thought of building something that in size and complexity is perhaps equal to, hmmm, a space station. They do not have a lot of experience working pretty much daily year in and year out on just *one* large project constantly. They do not have a clue as to why OOP *and* other paradigms besides the most basic and trivial ones are *important, useful and powerful* when dealing with things or projects they've never actually touched or could have managed to finish themselves given their simplistic attitude -- actually, disrespect -- towards technology, software and other people. They do not even understand OOP or other paradigms all that well either, but *still* comment on their feasibility in a global or general fashion.

..quite .. interesting; it might actually upset some people. Should it? Should people like Alan Kay be upset? Should he care? Why should *anyone* care to comment on what *you people* say or think? Here in Norway we have a silly thing called "Janteloven"; it states that "no one should think they're anything special"; perhaps there is some truth in it, only not in the sense one might think of initially.   ....... :)


edit:
This applies especially when a project turns large in the sense of depth and complexity; not large in the sense of covering a large area -- if this makes any sense.

---

### Post by dv3500ea on 2010-08-16
All programming paradigms have their advantages and disadvantages and no particular one is the best in all situations - this is why multiparadigm languages are better (IMO). 

Advantages of OOP:
[LIST]
[*] You don't necessarily need to know the underlying data structure of an object to create/use it. You can keep a consistent API while completely changing the underlying implementation.
[*] Less 'pollution' of the global namespace. (this can be achieved many other ways; using modules, scoping, function closures etc.)
[*] Shorter function/method names. You can have arr.length(), str.length(), custom_data_structure.length() instead of array_length(arr), string_length(str), custom_data_structure_length(custom_data_structure). This can be partly achieved by having a generic function that checks the data type to decide what to do, though this doesn't lend itself to extensibility: length(arr), length(str) will work but length(custom_data_structure) is unlikely to. Function overloading is another solution to this.
[*] Object oriented code is very reusable. So is functional code. So is procedural code split into subroutines.
[*] Inheritance - You can create an object based on another object, change it slightly, base another object on that and so on. This can happen in a very organic way - sort of like evolution with mitosis. Each time you only add/remove the methods you need to, helping with code reuse. 
[*] OOP matches how we think. Some of the time. About some things. 
[/LIST]

---

### Post by ssam on 2010-08-16
> **noobermin said:**
> And also, you could use function pointers.

the structs with pointers to functions in C is object oriented programming. but you are not using the best tool for the job.

i think the best way to explain OO is that it lets you create your own data types. no programming language has enough built in types. if it did then it would be huge.

you can write a program to work on complex numbers that are stored in a struct, but its much neater to create a complex number type. same when you want a type to represent a spacetime vector, a subatomic particle, or a email.

---

### Post by Calmarius on 2012-12-04
> **dv3500ea said:**
> 
You don't necessarily need to know the underlying data structure of an object to create/use it. You can keep a consistent API while completely changing the underlying implementation.


There is no need for OOP to achieve that. You can use single functions without knowing how they work, ever used the printf, fopen, etc? Was it harder?

> **dv3500ea said:**
> 
Less 'pollution' of the global namespace. (this can be achieved many other ways; using modules, scoping, function closures etc.)


Did you ever needed to find where does a particular function used a C++ code, because you wanted to know how it works? Or were you ever assigned with a task to fix a bug in a code you never seen before? How do you find out where does a particular function/method used inside the system? In C we use PREFIX_functionName format for that. And it's ensured the function has that name everywhere and uniquely. A single multifile search will tell you where does the function is used. With methods or overloads, you cannot do it without a sophisticated parser.

> **dv3500ea said:**
> 
Shorter function/method names. You can have arr.length(), str.length(), custom_data_structure.length() instead of array_length(arr), string_length(str), custom_data_structure_length(custom_data_structure). This can be partly achieved by having a generic function that checks the data type to decide what to do, though this doesn't lend itself to extensibility: length(arr), length(str) will work but length(custom_data_structure) is unlikely to. Function overloading is another solution to this.


May makes the code shorter, sure. But if you see foo.bar(1) in a code you've never seen before, do you immediately know which function will be called? You need to know the type of 'foo' and need know bar's overloads. If foo is a virtual function, you also need to know the dynamic type of foo in runtime! It's a debugging nightmare! Makes very hard to find out how the source code works, when you need to fix a bug in it. 

In C we write FOO_bari(pFoo, 1). So we immediately know which function is it. It's the int version of FOO_bar. Nothing else.

We also use switches for dynamic binding where possible, the compiler can and will optimize these into a jump table, and it's performance is not worse than calling a virtual function, also we can save the cost of calling a function (though that's trivial). These switches must have a default block so they can assertfail, when you forget to implement something. 
And it gives the advantage of seeing the possible outcomes at a single place.


> **dv3500ea said:**
> 
Object oriented code is very reusable. So is functional code. So is procedural code split into subroutines.


OOP reusability is a myth. How many classes have you reused so far you used in your projects? Except some very generic ones, like Vector3 or Matrix4x4, almost none of the classes are reused ever. Most functions in procedural code are never reused either. 

> **dv3500ea said:**
> 
Inheritance - You can create an object based on another object, change it slightly, base another object on that and so on. This can happen in a very organic way - sort of like evolution with mitosis. Each time you only add/remove the methods you need to, helping with code reuse. 


Inheritance is bad. OOP design principles suggest that you should avoid it where possible and prefer composition instead. No inheritance in procedural languages, if you want to use the functionality of something, you just add it's handle to your context struct and use the functions managing it, that's all.

Also there are an anti-pattern called "call-super" when the derived class invokes the base class functionality. In this case you would need to document when the base class method should be called this is an anti-pattern. Dependency inversion principle suggests that the abstract class should call the abstract virtual methods, and you only need to implement these abstract methods in the derived classes. 
The call-super problem don't occur in procedural languages because there is no inheritance. You can add behavior to the system in the form of callbacks. And the system will call it if provided.

Also look at the Strategy pattern... 

It seems that these patterns and principles just trying to reinvent the advantages of the procedural programming inside the OOP. 

> **dv3500ea said:**
> 
OOP matches how we think. Some of the time. About some things. 


You can't be serious that you tell the egg to go into the frying pan, or tell the frying pan to catch the egg, because you want to cook it.

Another problem of OOP is often with the encapsulation, the state of the object only altered and queried by its methods. But what if two objects of different type interact in a way that modifies the state of both? You cannot do that without exposing the state of at least one of them, or use language level hacks like the 'friend' keyword in C++. In C there is no encapsulation no such problem, just do it.

---

### Post by howefield on 2012-12-06
Thread closed.

---

