---
title: "Is Ruby a good starting point?"
date: 2007-01-30
forum: Programming Talk
---

### Post by Patrick-Ruff on 2007-01-30
hey all, I've been learning ruby and several of my programming buddies told me that it was a good starting point for what I wanted to learn.  what I plan to do is learn ruby, get fluent with it, then go on to learning other programming languages like C/C++, Java, Lisp, etc. 

I would like to know everyone else's thoughts on this.  no biased comments please.

---

### Post by lnostdal on 2007-01-30
> **Patrick-Ruff said:**
> hey all, I've been learning ruby and several of my programming buddies told me that it was a good starting point for what I wanted to learn.

learning ruby (or "MatzLisp") as a nuby? i don't see why not -- find a good book/resource and start reading/hacking/experimenting! :)

---

### Post by Wybiral on 2007-01-30
I think ruby or python are great languages to start with, they're also great languages to stay with for most applications.

---

### Post by Patrick-Ruff on 2007-01-30
awesome thanks.

---

### Post by tc101 on 2007-02-03
I want to install Ruby.  I am getting it from 
[http://www.ruby-lang.org/en/downloads/](http://www.ruby-lang.org/en/downloads/)

The instructions are:

--------------
% sudo apt-get install ruby irb rdoc

For irb and rdoc you will need to enable the universe repository.
----------------

So what does it mean to enable the universe repository, and how do I
do it?

---

### Post by lnostdal on 2007-02-03
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by tc101 on 2007-02-03
Thanks.  I got it now.

---

### Post by tc101 on 2007-02-03
I enabled the universe repository, then went to the terminal and did 

% sudo apt-get install ruby irb rdoc

termianl showed me that ruby was set up.  I thought I would see it under Application>Programming but I did not.

I then did Application>Add/Remove and did a search for Ruby.  I installed KDevelop:Ruby, IDE for Ruby.   Is this what I was supposed to do?

I then went to  Application>Programming and opened KDevelop:Ruby.  Is this correct so far?

I then went to help but it did not work.  I got a message "Could not launch the KDE help center, Could not find service khelpcenter".  How do I fix that?

---

### Post by lnostdal on 2007-02-03
just type irb and press enter .. find some editor/ide later when you've confirmed that this works

---

### Post by tc101 on 2007-02-03
This is what I get:

tomcarr@tomcarr-desktop:~$ irb
irb(main):001:0>

---

### Post by tc101 on 2007-02-03
lnostdal, I found this quickstart page which answers lots of my questions.

[http://www.ruby-lang.org/en/documentation/quickstart/](http://www.ruby-lang.org/en/documentation/quickstart/)

I am going to work with this for now.  I can see that I do have ruby installed.  I will be back tomorrow with more questions.  Thanks for your help.

---

### Post by Mrfo on 2007-02-04
Personally I vote Java.  Its high level enough to not have to deal with memory management, but at the same time allows for easy learning of C/C++.  Most high schools and universities seem to be going the Java -> C++ -> C route now a days to ease into the programming experience.  I'd look into Java, but Ruby is still a nice starting point.

---

### Post by LordHunter317 on 2007-02-04
> **Mrfo said:**
> Personally I vote Java.  Its high level enough to not have to deal with memory management,So what's all this code like:```
MyObject foo = new MyObject(bar);
```I've seen?

Memory management is a subset of resource management and that's still manual allocation and deallocation in Java.  Java doesn't free you from the problem.  Even "pure" functional languages such as Haskell rarely totally free you from the problem, but they do tend to force you into techniques where making resource lifetime mistakes are much harder (because lifetime and scope have stronger correspondance).

> Most high schools and universities seem to be going the Java -> C++ -> C route now a days to ease into the programming experience.No, they do it because it's what the business world demands.

---

### Post by Mrfo on 2007-02-04
> **LordHunter317 said:**
> So what's all this code like:```
MyObject foo = new MyObject(bar);
```I've seen?
I would call that more of an understanding of the way objects work then dealing with memory management.  While java doesn't free you from the memory problems it lets you understand the core elements of software development rather then getting hung up on specifics.  Pointers and other memory issues have eaten alot of programmers starting out.

[QUOTE=LordHunter317]No, they do it because it's what the business world demands.[/QUOTE]
Isn't that the main point of higher education these days?  It's not like universities only teach you Java,C/C++.  Learning Ruby, Python, PHP or whatever else you would like to learn is a quite a bit easier after you've learned the basics.  But to get back to the original issue, it's more of a personal preference.  Ruby is relatively new in the programming world.  While it's here to stay, I think the OP would be better able to adapt to other languages starting with Java.  Just my 2 cents. :)

---

### Post by LordHunter317 on 2007-02-04
> **Mrfo said:**
> I would call that more of an understanding of the way objects work then dealing with memory management.Not really.  It's both, you're being forced to be bothered with the (irrelevant) detail that storage has to be allocated for objects.

Haskell doesn't bother us with such things so it's really inexecuable.  It's a detail we just don't need to be concerned with (in theory)[1]

> Pointers and other memory issues have eaten alot of programmers starting out.Java has pointer semantics though and all the issues associated with, save for those associated with pointer math.


> Isn't that the main point of higher education these days?Unless I'm crazy, it's never truly been the point of higher education, just a nice target that sometimes is hit.

[1]We do occasionally have to deal with it to avoid generating too much GC pressure and be sure to mark "dead" objects null if a long-lived object has a reference to them.

---

### Post by Patrick-Ruff on 2007-02-04
I'm sticking with ruby.  I've been told by my friend who codes java that ruby would probably help me more in the long run concept wise.  I'm only really going this high level to help me understand concepts in C/C++, unless I decide that ruby fits my programming needs. we'll see as far as that goes.

---

### Post by tc101 on 2007-02-04
What is your main goal Patrick-Ruff?  Do you want to learn programming to make a living or as a hobby or what?

I am a recently retired programmer.  I did this to make money for 30 years.  Now I will probably never write a line of code for money again, so I am learning Ruby because I am curious about cutting edge technology.  If I were still in the job market my focus would be totally different.  

What are you trying to achieve?

---

### Post by tc101 on 2007-02-04
I have a question I will try here, although maybe it belongs in a KDE topic.

I have installed KDevelop and would like to try using it for Ruby.  When I open help I get a message  "Could not launch the KDE help center, Could not find service khelpcenter". How do I fix that?

---

### Post by pmasiar on 2007-02-04
> **Mrfo said:**
> Most high schools and universities seem to be going the Java -> C++ -> C route now a days to ease into the programming experience.  I'd look into Java, but Ruby is still a nice starting point.

MIT uses Python for intro to programming. Ruby will run circles around java for web development. Just try to read up on Struts, the most popular java web framework,

UPDATE: read up on Struts - to understand how  much better off you are with Ruby/Rails, or with Python :-)

---

### Post by LordHunter317 on 2007-02-04
Please don't.  Struts is horrible and shouldn't be used at all on new applications.  Only learn if it you have to.

---

### Post by jblebrun on 2007-02-04
> **LordHunter317 said:**
> So what's all this code like:```
MyObject foo = new MyObject(bar);
```I've seen?

Memory management is a subset of resource management and that's still manual allocation and deallocation in Java.  Java doesn't free you from the problem.  Even "pure" functional languages 



This is just a syntactical reminder that you are allocating memory (and a holdover from the C++ derivation), if you happen to already know that that is what is happening. You don't have to know ANYTHING about memory management to understand what the statement is doing (creating a new object for you). It's exactly the same as typing:

```

thing = A()

```

In Python. 

You do not have to be in charge of de-allocation of objects in Java. You CAN de-allocate them, but it's almost never necessary.  You can de-allocate them manually in Python, too, but there's no need to.

---

### Post by LordHunter317 on 2007-02-04
> **jblebrun said:**
> This is just a syntactical reminder that you are allocating memory (and a holdover from the C++ derivation), if you happen to already know that that is what is happening. You don't have to know ANYTHING about memory management to understand what the statement is doing (creating a new object for you).Yes, that's *exactly* my point.  It's totally redundant and so it shouldn't exist. 

It's even worse in C# since value types (structs) are still created with new yet aren't allocated on the heap.   So now is new not only superflurous, it's ambiguous.  Hard to get worse than that, honestly. 

> You do not have to be in charge of de-allocation of objects in Java. You CAN de-allocate them, but it's almost never necessary.No, you cannot.  You cannot deterministically collect anything in Java.

---

### Post by Patrick-Ruff on 2007-02-04
and yes, I do plan to do programming for a living (but I'm only in high school so for now it's going to be my own little expirementation :D.

---

### Post by lnostdal on 2007-02-04
```
Base object = new Derived();
```

..might be a "reason" for the extra stuff(?). But I've kind of forgotten why you then couldn't just say: 

```
object = new Derived();
```

..in the first place then add the boring type declarations later when/if you need the extra runtime speed (as is common practice in Common Lisp). Compile time type-safety you say? Give me a break. :)

Though, Javas GC and automatic memory management are in most cases good things compared to the alternative of doing that kind of crap-work manually. Even if Java do lack a way of explicitly/deterministically deleting an object it's way better in most cases IMHO. 

Setting stuff to NULL only makes it happen somewhat sooner, if I remember correctly (1997 .. 10 years .. wow).

The static type thing seems ridiculous to me though. Ruby is wayway better or more productive in this regard while still holding on the benefits of GC and automatic memory management from Java (uhm, well - Lisp had it first of course).

Maybe not to related, but Common Lisp has something that allows you to control deterministically the lifetime of objects without relying on GC to eventually pick stuff up: [http://www.lisp.org/HyperSpec/Body/dec_dynamic-extent.html](http://www.lisp.org/HyperSpec/Body/dec_dynamic-extent.html) It basically declares that the compiler can allocate objects on the stack. Many implementations also have ways of explicitly calling/manipulating the GC-mechanism.

Maybe Java could have had:

```
object = new SomeClass(); // heap
object = SomeClass(); // stack
SomeClass object = new SomeClass(); // head + compile-time type-checking
SomeClass object = SomeClass(); // stack + compile-time type-checking

```

...? I dunno. I might be talking total gibberish as I haven't done any Java for a long time, and I'm not really thinking this through. :)

What was this thread about again? .. Oh, right .. yes, I'd say stick with Ruby instead of Java. You'll have no problem learning Java or C# later (for job?) besides the fact that you will probably totally hate it. When/if you need low-level stuff take a jump straight down to C skipping the horrible hybrid C++ - this way you avoid most overlap. If you want to try something really fun/weird/cool try Lisp; the language oriented language with no locked-in style, no form, no syntax .. only structure while at the same time formless like water. :)

---

### Post by Patrick-Ruff on 2007-02-04
I did get into C/C++ for a while, I got as far as functions (after declaring variables and all that stuff.) and then I was warned by professional programmer that it would be in my best interest to go with a higher level before I continued, to help me understand some other concepts of C/C++. 

so, ruby seems pretty cool :)

---

### Post by jblebrun on 2007-02-04
> **LordHunter317 said:**
> Yes, that's *exactly* my point.  It's totally redundant and so it shouldn't exist. 

It's even worse in C# since value types (structs) are still created with new yet aren't allocated on the heap.   So now is new not only superflurous, it's ambiguous.  Hard to get worse than that, honestly. 

No, you cannot.  You cannot deterministically collect anything in Java.

Yeah, sorry. I shouldn't have said "deallocate." I just meant that you could explicitly set reference to an object to null, which conceptually "deletes" it, even though it may never be collected by GC.  I did assume, though, that there was a way to force GC... and that I'd just never used it. So that's good to know (although if I'm lucky I'll never have to program in Java again :-P) 

Anyway, this is drifting away from your main point, so I stand corrected.  And I see your point.

---

### Post by LordHunter317 on 2007-02-04
> **lnostdal said:**
> ```
Base object = new Derived();
```

..might be a "reason" for the extra stuff(?).No. Why would it?  

> ..in the first place then add the boring type declarations later when/if you need the extra runtime speed (as is common practice in Common Lisp).Becuse Java is statically typed, so you'd have to cast at every point you wanted to use a method that's not a member of object.

That's why.  Of course, ideal is type inference (cf. Nemerle, Scala, C# 3.0):```
var foo = new SomeType(bar, baz);
```typeof(foo) will be SomeType.  I could post some longer Nemerle examples that show just how great even partial type inference is.

> Even if Java do lack a way of explicitly/deterministically deleting an object it's way better in most cases IMHO. It's not a problem, I don't think I ever protrayed it as one.  

> Setting stuff to NULL only makes it happen somewhat sooner, if I remember correctly (1997 .. 10 years .. wow).It makes it possible.  The issue is that for long-running applications 

> The static type thing seems ridiculous to me though.Not really.  Compile-time type safety isn't something to underestimate.  The issues are the shortcomings of Java's type system.

> Ruby is wayway better or more productive in this regard while still holding on the benefits of GC and automatic memory management from Java (uhm, well - Lisp had it first of course).Static vs. Dynamic typing has nothing to do with GC or memory management.

> ...? I dunno. I might be talking total gibberish as I haven't done any Java for a long time, and I'm not really thinking this through. :)It's apparent you haven't thought it through at all.  That would be a terribly bad idea for a lot of things.

> When/if you need low-level stuff take a jump straight down to C skipping the horrible hybrid C++ - this way you avoid most overlap.There's no overlap besides some syntax, so this makes no sense.

>  the language oriented language with no locked-in style, no form, no syntax ..All LISPs have conventional or enforced forms of all 3.

---

### Post by LordHunter317 on 2007-02-04
> **jblebrun said:**
> Yeah, sorry. I shouldn't have said "deallocate."No, beacuse that would be wrong.  You can't deterministically deallocate memory in Java either.

All you can do is remove all references to an object.  I'm only being an *** about this because the whole issue is about object lifetimes, and in a managed environment, the fact that an object can outlive *all* its references is important.   Why?  Because in a non-managed environment, that would be a memory leak.  But in a managed environment, this is OK, because you don't have to clean up your trash, typically.[1]

> I just meant that you could explicitly set reference to an object to null, which conceptually "deletes" it, even though it may never be collected by GC.  I did assume, though, that there was a way to force GC... and that I'd just never used it.System.gc(), but there's no guarantee your object will be collected.  Whether the garbage collector is even deterministic is implementation defined, nevermind it's collection rules.

[1]Python, despite being managed, couldn't collect objects with circular references until additon of a garbage collector.  It used reference-counting to determine dead objects.

---

### Post by Patrick-Ruff on 2007-02-04
heh, a flame war with language that is beyond me atm :D lol.

---

### Post by lnostdal on 2007-02-04
> **LordHunter]
[quote=lnostdal]
```

Base object = new Derived() said:**
> 

..might be a "reason" for the extra stuff(?).
No. Why would it?


Yeah, I think I'm mixing the original point (new/resources etc.) with type-safety or something like that while thinking about Ruby vs. Java.


> **LordHunter]
[quote=lnostda]
..in the first place then add the boring type declarations later when/if you need the extra runtime speed (as is common practice in Common Lisp).
[/quote]
Becuse Java is statically typed, 
[/quote]
Uhm, well, that's kind of what I'm of saying or asking. Why is it statically typed in this straight-jacket way? What's the point in forcing this on users at an early point while developing? Why not let the user add declarations later - if they want to?

[quote=LordHunter]
That's why. Of course, ideal is type inference (cf. Nemerle, Scala, C# 3.0):
```
var foo = new SomeType(bar, baz) said:**
> 

..looks like (type-of var) to me :)

[quote=LordHunter]
[quote=lnostdal]
Even if Java do lack a way of explicitly/deterministically deleting an object it's way better in most cases IMHO.

It's not a problem, I don't think I ever protrayed it as one.[/quote]

It can be, but in most cases I don't think it is. It was something I thought I should mention regardless of what you portrayed.

> **LordHunter][quote=lnostdal]The static type thing seems ridiculous to me though.[/quote]Not really. [/quote]

Ok, we disagree. I want to be able to add type-declarations when and if I want to. I could never accept anything less flexible.


[quote=LordHunter][quote=lnostdal]
Ruby is wayway better or more productive in this regard while still holding on the benefits of GC and automatic memory management from Java (uhm, well - Lisp had it first of course).[/quote]
Static vs. Dynamic typing has nothing to do with GC or memory management.[/quote]

Of course not. But static typing does reduce the productivity when doing exploratory programming which was what I was trying to say. So Ruby having both GC and a better type-solution is a win-win in my eyes comparing with Java only having the GC-part. 

edit: i'm not always referring to your post or GC here said:**
> [quote=lnostdal]...? I dunno. I might be talking total gibberish as I haven't done any Java for a long time, and I'm not really thinking this through.

It's apparent you haven't thought it through at all. That would be a terribly bad idea for a lot of things.[/quote]

Like what? Introducing some lexical-scope requirements for stack-allocation would solve the first thing I can think of off-hand here. I'm pretty sure this would work out as I'm seeing it happen in other languages, but then again - it would not be Java at all in the end then I guess. 


> **LordHunter]
[quote=lnostdal]
When/if you need low-level stuff take a jump straight down to C skipping the horrible hybrid C++ - this way you avoid most overlap.
[/quote]
There's no overlap besides some syntax, so this makes no sense.
[/quote]
C++ tries to be a high-level version C with meta-programming, exceptions, generics etc. I disagree said:**
> 
[quote=lnostdal]the language oriented language with no locked-in style, no form, no syntax ..
All LISPs have conventional or enforced forms of all 3.
[/quote]
Then you do not understand Lisp.

edit:
* no locked-in style because OOP-style was added as a library (CLOS) .. AOP is now being added .. and lots of other styles are being added all the time .. while java is locked-in OOP
* no syntax because you are always working directly at the tree that is beneath all syntax in all languages .. you're working directly at the structure (i think it's called an "abstract syntax tree" or something)
* no form .. well, basically the same thing as no syntax and no style; it's a formless non-static language that you can adapt yourself

---

### Post by LordHunter317 on 2007-02-04
> **lnostdal said:**
> Uhm, well, that's kind of what I'm of saying or asking. Why is it statically typed in this straight-jacket way?Language decision.  I'm not sure a debate on the merits of static and dynamic typing is very benefical here.

At either rate, I simply do not wish to have it here.

> What's the point in forcing this on users at an early point while developing?It enforces program correctness, when a programmer properly avails themself of it.

> Why not let the user add declarations later - if they want to?Because Java doesn't have any way way to determine how to make the method calls without the type information.  Even the reflection facilities are statically typed.

> Ok, we disagree. I want to be able to add type-declarations when and if I want to. I could never accept anything less flexible.Then Java isn't a language for you.  FWIW, Nemerle and VB.NET support both late-binding and static-binding on types.  You can pick and choose and mix-and-match.  You pay a fairly large (but not huge) cost for late-binding in .NET.  For most applications, it's not a performance issue.  Useful portions of ASP.NET, S.W.F., and WPF use reflection anyway, so even if your code is 100% static you can end up paying the cost.

> Of course not. But static typing does reduce the productivity when doing exploratory programming which was what I was trying to say.Sometimes, sure.  When you need a REPL loop, certainly.  But for production software?  It's not apparent the loss of immediate feedback is a sufficentl loss to offset the type safety gains.

Especially in expressive type systems like C++ or Haskell where you can verify domain-specific data at compile time (e.g., units of measure).  Or in systems with strong macro facilities where you can do arbitrary checks at compile time (e.g., Nemerle's macro facility). 

Not only can I verify my types, I can verify logic too before a single piece of code is run.

> Like what? Introducing some lexical-scope requirements for stack-allocation would solve the first thing I can think of off-hand here.I'm not sure what you're thinking off hand here, but I'm pretty sure it's a non-issue.  My point is simple: new is spurious line-noise 100% of the time[1].  Not being able to allocate objects on the stack isn't an issue.  So integrating that in as a concern pretty much makes you wrong automatically.

> C++ tries to be a high-level version C with meta-programming, exceptions, generics etc.And has resulted in becoming a language that shares some syntax and a minor portion of it's standard library.  Idomatic C looks nothing like idomatic C++, and Idomatic C++ isn't even expressible in C.  As such, you miss everything important about C++.

If you don't believe me, I have a challenege that pretty clearly proves the point, without much argument.

> Then you do not understand Lisp.No, you don't understand the three things you're talking about.

[1]Slight lie: new does differentiate between the heap and stack allocated objects in Java (as I said before, C# loses this distinction badly).  But given that at least in Java 5, stack-allocated types are automatically boxed/unboxed as needed, I fail to see the need for distinction.  They're all nasty special cases anyway, and all special cases in situations that "new" does not cover.

---

### Post by LordHunter317 on 2007-02-04
> **lnostdal said:**
> * no locked-in style because OOP-style was added as a library (CLOS) .. AOP is now being added .. and lots of other styles are being added all the time ..Uhh, LISP (at least Common LISP) has **always** been multi-disciplinary, so this is an inductive fallacy.

> while java is locked-in OOPNo it isn't.  There are AOP libraries in Java.  Generics (albiet very crappy ones) were added to the language in Java 5.  You can do limited forms of functional programming, though the lack of real closures is a PITA (use Scala instead).

> * no syntax because you are always working directly at the tree that is beneath all syntax in all languages .. you're working directly at the structure (i think it's called an "abstract syntax tree" or something)Actually S-expressions aren't ASTs and vice-versa.  And that doesn't change the fact the source-code has a well-defined syntax.  The syntax just doesn't cover as many defined language structures as other languages.

LISP originally had M-Expressions anyway, so you'd still be incorrect as it turns out.

> * no form .. well, basically the same thing as no syntax and no style; it's a formless non-static language that you can adapt yourselfBut it's not formless.  That's just it.  The form may not be as well-defined, but that's a world of difference from none.

---

### Post by Patrick-Ruff on 2007-02-04
lol wow . . .

---

### Post by lnostdal on 2007-02-05
> **LordHunter]
It's not apparent the loss of immediate feedback is a sufficentl loss to offset the type safety gains.
[/quote]

I get feedback at runtime. It's not a problem. Heck, just get rid of all the "times" and let debug-time/runtime/compile-time meld then I'll get way better feedback and control.

If you disagree, then I agree said:**
> 
I'm not sure what you're thinking off hand here, but I'm pretty sure it's a non-issue.  My point is simple: new is spurious line-noise 100% of the time[1].


Yeah, I don't think I'm disagreeing with that. If it seemed like I did it's not what I mean(t). 

I was thinking the type declaration is line-noise also, or that it should be optional. Still  disagree about this? Absolutely fine, no point in discussing.


[quote=LordHunter]
Not being able to allocate objects on the stack isn't an issue.  So integrating that in as a concern pretty much makes you wrong automatically.
[/quote]

hahaha - are you some kind of type safe filter-function or something? I'm not integrating it into some grand proof of why "`new' really is needed". Get over yourself. I'm just talking and I do think I mentioned "somewhat unrelated", and I was kinda hoping that it was obvious the places it wasn't mentioned.

Just in case here -- being able to say that the life of an object is controlled by scope can be an optimization sometimes. I'm having a hard time seeing how you cannot see this, but then again this integration-thingy of yours might explain this. Maybe I'll need to add type-declarations before each sentence or something.

Having a hard time seeing the blurry connection? Java lacked deterministic collection of objects => putting them on the stack is one way of doing it.


[quote=Lordhunter]
And has resulted in becoming a language that shares some syntax and a minor portion of it's standard library.  Idomatic C looks nothing like idomatic C++, and Idomatic C++ isn't even expressible in C.
[/quote]

It shares the problems while adding its own. It accumulates the crap from C while making it even worse by making the user believe that they can escape both sets of problems with things like meta-programming etc.

.. I'm bored with this .. I'm bored talking about C++ .. I don't care .. I've moved along .. I'm done with it, and have been for a long time now ..


[quote=LordHunter]
If you don't believe me, I have a challenege that pretty clearly proves the point, without much argument.
[/quote]

I'm having a hard time seeing your point, so that's pretty much a challenge in it self. If you're about to post some C++ code or whatever; don't .. I do not care .. at all.

---

### Post by LordHunter317 on 2007-02-05
> **lnostdal said:**
> I get feedback at runtime. It's not a problem.That's a problem for huge classes of systems.  On emedded systems, runtime feedback varies from "full debugger and monitor support on board" to "full debugger and montior on host PC" to "blinkenlights" to "nothing".

I've worked with 3/4 in the past 12 months alone.

> Heck, just get rid of all the "times" and let debug-time/runtime/compile-time meld then I'll get way better feedback and control.That's not feasible for whole classes of systems.  It's physically unpossible.  On others, the cost outweights the benefit.

> If you disagree, then I agree; no point in discussing this as I don't really care that much about what you think.That's incredibly disheartening, trollish and against the spirit of this forum.

> Point is this is why _I_ think (this is the important bit .. lol) Ruby is a good choice compared with Java, and it has nothing to do with your post about `new' either.I'm not sure I believe that, since you keep trying to forward Ruby's superiority.  At least, your words don't match your intentions well.

> I was thinking the type declaration is line-noise also, or that it should be optional. It cannot be in a statically typed language, a fundmental fact you seem to still be missing.  That, or trying to troll to forward a static vs. dynamic debate I do not wish to have.  It's difficult to tell which now.

Simply put, **Java *must* have a type definition somehow because it is *statically typed***.  No way around it.  So saying, "They should be optional in Java" is nonsense.  Saying, you don't like languages that use static typing is another, but I simply do not wish to go there.

> I'm not integrating it into some grand proof of why "`new' really is needed".**But you did**:> ```

object = new SomeClass(); // heap
object = SomeClass(); // stack
SomeClass object = new SomeClass(); // head + compile-time type-checking
SomeClass object = SomeClass(); // stack + compile-time type-checking
```Lines one and two make a distinction based on presence/absence of new.

> I'm just talking and I do think I mentioned "somewhat unrelated", and I was kinda hoping that it was obvious the places it wasn't mentioned.Well, then whatever point you're trying to make you're making it rather poorly.

> Just in case here -- being able to say that the life of an object is controlled by scope can be an optimization sometimes.Sure.  But that's not a useful optimization in Java for a host of reasons.  Not to mention it breaks the language semantics horribly.  The autoboxing/unboxing is proof-positive of this.  We don't want to have to further such nasty behaviors.

> I'm having a hard time seeing how you cannot see this,I do see it.  But I see all the other issues in Java that make it a bad idea.  There's a reason why only a few small types can be on the stack at all, and it's really more heartache than gain.

> Having a hard time seeing the blurry connection?Yes, because you refuse to compose anything you write into complete, coherent, reasoned thought with connection between A and B.

>  Java lacked deterministic collection of objects => putting them on the stack is one way of doing it.But it's not.  Because then objects cannot outlive their scope.  That's a property that cannot generally be removed in Java.  If it could, we wouldn't need a GC *at all*.


> It accumulates the crap from CExcept for all the stuff they removed.  Like huge parts of the broken type system.

> while making it even worse by making the user believe that they can escape both sets of problems with things like meta-programming etc.But they clearly can.

> I'm having a hard time seeing your point, so that's pretty much a challenge in it self. If you're about to post some C++ code or whatever; don't .. I do not care .. at all.Write an application to safely and correctly read into RAM and print out a file of arbitrary length in C.  Do the same in C++, using the STL and proper C++ idioms.  You'll see why you cannot learn anything about C++ from C.

---

### Post by Patrick-Ruff on 2007-02-05
chill you guys.

what's a really good ruby IDE for windows? (that's free, and not Eclipse, and other then SciTE, I didn't like it.)

---

### Post by Wybiral on 2007-02-05
> I'm having a hard time seeing your point, so that's pretty much a challenge in it self. If you're about to post some C++ code or whatever; don't .. I do not care .. at all.


lol, you say you don't care... But yet you wasted your time to post?

Anyway... Personally, I think Ruby or Python are great languages to learn and they are both very easy to learn. They will teach you good habits and offer more complex methods of programming, withing boring you to pieces while learning tiny little details.

Details can be learned later, don't worry about GC and static typing/type safety right now... Learn how to program, use functions/objects... Learn about loops/conditions and program flow. Ruby and Python are both great for this.

Personally, I enjoy using Ruby, Python, C, AND C++ it just depends what I'm doing.

I will also throw out there... Just for opinion sake, that Ruby is much easier to learn than Java. But, that is, *my opinion*

I just think dynamic typing/interactive environment/automatic GC/simple syntax/object oriented capabilities (but not enforced) make Ruby and Python great places to start.

Like I said... Worry yourself about the details after you figure out if programming is right for you and get used to controlling program flow before you worry about the rest.

---

### Post by Patrick-Ruff on 2007-02-05
lol, I got all the way into functions in C++ before I decided to go to ruby.  also, I think you may want to edit your post to avoid being flammed about the *oh but you do care* crap.

---

### Post by lnostdal on 2007-02-05
.. well, this is turning off topic ..

> **LordHunter317 said:**
> Uhh, LISP (at least Common LISP) has **always** been multi-disciplinary, so this is an inductive fallacy.

it's not the state of what lisp "has" at any given point in time i'm talking about..  

..it's how things have changed by adding to lisp without changing the core and how easy it is to do this whenever you want at any level ..   in other languages they must change the core to add new language features..

(well; there are limits when i say only "lisp" of course .. 1958-LISP is not what i mean .. i mostly mean "common lisp" when i say "lisp")


> **lordhunter]
No it isn't.  There are AOP libraries in Java. 
[/quote]

nah said:**
> 
 Generics (albiet very crappy ones) were added to the language in Java 5.


nah, they changed the language instead of adding a library to it while keeping the core the same


> **lordhunter]
  You can do limited forms of functional programming, though the lack of real closures is a PITA (use Scala instead).
[/quote]

i don't know about scala or functional programming in plain java .. i have never tried it said:**
> Actually S-expressions aren't ASTs and vice-versa.

ok, forget all that, try this instead ..  you can manipulate code as it was data.. no need to parse anything as there is no intermediate syntax; only data all the time + there lines between runtime and compile-time are blurred..  when everything is the same there is no syntax to talk about..   lisp is working directly at the stuff that is beneath syntax inside a compiler -- the things you see is just the structure of it or data


[quote=lordhunter]But it's not formless.  That's just it.  The form may not be as well-defined, but that's a world of difference from none.[/QUOTE]

with formless i mean it can represent anything; it's so flexible .. not thinking visually about what you see at the syntax-level at all here

---

### Post by jblebrun on 2007-02-05
> **LordHunter317 said:**
> 
[QUOTE=jblebrun;2107436]Yeah, sorry. I **shouldn't** have said "deallocate." 

No, beacuse that would be wrong.  You can't deterministically deallocate memory in Java either.

[/QUOTE]

I think you mis-read my response.

---

### Post by LordHunter317 on 2007-02-05
> **lnostdal said:**
> it's not the state of what lisp "has" at any given point in time i'm talking about.. Then your argument is literal nonsense.  LISP has always supported multi-disclipinary programming, like it or not.  If it didn't, then why the presence of (progn) and other forms for imperative operations?

> ..it's how things have changed by adding to lisp without changing the core and how easy it is to do this whenever you want at any level ..That doesn't prove your claim.  It doesn't come close.

> nah; they've just added a compiler in front of java .. it's no longer java ..  AOP in lisp is just a libraryThis, once again, just shows your gross ignorance on the subject.  Check out Aspectwerkz or similar, which solely hook into the runtime.

> nah, they changed the language instead of adding a library to it while keeping the core the sameAnd? Some changes to LISP require language changes, look at the mess Scheme is going through for the next revision.

> no need to parse anything as there is no intermediate syntax;Incredibly false.  Has to be translated to machine code, no?  Then it must be parsed at some point.

> when everything is the same there is no syntax to talk about..Wrong.  Please go read the Dragon Book.  If you don't know what that is then you just need to stop talking about syntax.  You're historically, factually, and logically wrong. 

>   lisp is working directly at the stuff that is beneath syntax inside a compilerNo, it isn't.  It's closer than most languages, but it isn't there. 

> with formless i mean it can represent anything;That's trule of any turing-complete language so that's nonsensical.

---

### Post by LordHunter317 on 2007-02-05
> **jblebrun said:**
> I think you mis-read my response.No, I did not.  The action of deallocation is different from the act of setting a reference to null. If it wasn't, then memory leaks would be impossible.

I'm only being an *** about terminology because it's very important here and I explained why.

---

### Post by Wybiral on 2007-02-05
> **Patrick-Ruff said:**
> lol, I got all the way into functions in C++ before I decided to go to ruby.

C++ isn't that bad once you understand some OOP and basic memory management.

Actually, I generally prefer using it over most languages, but it's probably not the best to start with... I will definitely admit that.

Ruby should help you understand classes which are a core concept in a number of languages.

As far as an IDE goes... I'm not sure, I don't usually use them... But, I learned Ruby and Python from the command line... Having an interactive environment like that really lets you play with things and get a feel for whats going on, it's a time saver for learning them IMO.

Ruby and Python have a lot in common... Learn one and the other makes sense almost instantly. They're also very great places to pick up on OOP if you've never used it.

BTW, is this you FIRST time programming?

> also, I think you may want to edit your post to avoid being flammed about the *oh but you do care* crap.

I just thought it was funny, I don't need to justify myself.

---

### Post by Patrick-Ruff on 2007-02-05
yes I suppose this is my first time programming, I just really hate the process of learning the initial concepts is all, otherwise I would have been programming 3 years ago ;).

---

### Post by jblebrun on 2007-02-05
> **LordHunter317 said:**
> No, I did not.  The action of deallocation is different from the act of setting a reference to null. If it wasn't, then memory leaks would be impossible.

I'm only being an *** about terminology because it's very important here and I explained why.

So, just to be clear, you were _confirming_ my self-correction, and not _correcting_ me? Because I already said that I **shouldn't** have said de-allocate.

---

### Post by LordHunter317 on 2007-02-05
Ok you were right and I misread it and I totally apologize.  My sincere bad.

---

### Post by jblebrun on 2007-02-05
> **LordHunter317 said:**
> Ok you were right and I misread it and I totally apologize.  My sincere bad.

It's ok. I was afraid that I was severely mis-understanding you, so now I'm relieved. Anyway, I should've just paid more attention and not said "de-allocate" in the first place ;-)

I have a horrible habit of spouting malapropisms because I turn off portions of my brain when I write. Let's pretend that this exchange has made me a little less likely to do that, then it wasn't all in vain! ;-)

---

### Post by Wybiral on 2007-02-05
> **Patrick-Ruff said:**
> yes I suppose this is my first time programming, I just really hate the process of learning the initial concepts is all, otherwise I would have been programming 3 years ago ;).

I know what you mean by getting the initial concepts down... It all looks awkward and non-nonsensical at first. But, I promise, once you do get used to programming, learning new languages becomes pretty natural. I bet once you learn Ruby and you start to grasp the concepts and learn how the programs flow... It will make much more sense.

And then you can migrate through other languages more easily... But, who knows... You may like Ruby and it may be enough for you. However, I don't think it's ever a bad thing to learn new languages... Why stop? You know... All it's going to do is show you different ways to solve problems and new possibilities for writing programs.

Also... I personally learned from challenges. Look for some beginner challenges and try to use what you're learning to solve those challenges.

One of my first programs was this (it was in QBasic btw)...

The number guessing game.
Your program generates a random number and stores it with a variable.
Then you ask the user to guess the number.
If the user guessed too high, you tell them they guessed too high and let them guess again... If they guess to low, you tell them it was too low and let them guess again. If they guess it, tell them they won.
You also keep count of the number of guesses that were made and report that as the score (where you are obviously trying to get a low score)

Little challenges like that let you use what you're learning in context... That one makes  you use: random numbers, user input, output, comparison, and some form of loop to repeat the guesses.

If stuff like that is too easy for you... Look for harder problems and DEFINITELY look through source code of experienced programmers. You can learn a lot by studying other peoples code because simply learning a languages isn't enough... You have to learn how to build programs with the language.

---

### Post by jblebrun on 2007-02-05
So, Patrick, back to your issue. My advice is: if you're enjoying learning Ruby, then by all means, continue pursuing it! The most important thing you can do, especially early on, is to find a learning endeavor that you can be excited about! If you find yourself learning a language because you feel that it's something you *have* to do, then you're probably never going to learn it very well.

I hope you're enjoying Ruby so far. I just started exploring it a few months ago, because of the Ruby on Rails project. I'm still learning how to use it to its full potential, but it's a really nifty language, and I think Rails really flexes a lot of its need qualities. 

It does have rather poor performance in a number of situations, but you shouldn't let that concern you in this early learning stage. In fact, sometimes it may be better, because it will force you to think harder about how to optimize your code or algorithm to make better use of the resources that you have. 

I hope you don't mind the heated discussion that the other guys have been having here in your thread. Even though they get cranky and upset with each other, there are still often interesting tidbits of information embedded in the arguments/debates!

---

### Post by lnostdal on 2007-02-05
> **LordHunter317 said:**
> That's a problem for huge classes of systems.  On emedded systems, runtime feedback varies from "full debugger and monitor support on board" to "full debugger and montior on host PC" to "blinkenlights" to "nothing".

I've worked with 3/4 in the past 12 months alone.


Ah, that old argument. Yes, I (or the OP) was obviously talking about a 1024MB light bulb here. Find another straw man; I'm not that dim.


> **lordhunter]That's incredibly disheartening, trollish and against the spirit of this forum.[/quote]

well, uhm - you was the one who did not want to discuss typing? .. i stand my case said:**
> 
I'm not sure I believe that, since you keep trying to forward Ruby's superiority.  At least, your words don't match your intentions well.


i have no idea what you're saying here

> **lordhunter]
It cannot be in a statically typed language,
[/quote]
uhm, yeah? "because it _is_ a statically typed language", right? wow, fascinating work there sherlock .. a real zen-moment said:**
>  a fundmental fact you seem to still be missing.  
no? i'm discussing what i view as benefits in ruby .. i'm wondering; what do you see as benefits in ruby vs. java if not for non-static typing?


> **lordhunter]
That, or trying to troll to forward a static vs. dynamic debate I do not wish to have.  It's difficult to tell which now.
[/quote]

hey, let's keep this interesting said:**
> 
Simply put, **Java *must* have a type definition somehow because it is *statically typed***.  


lol - *silence* .. ah ..  1 == 1  ? O_O

> **lordhunter]
  Saying, you don't like languages that use static typing is another, but I simply do not wish to go there.[/quote]

then it's settled then


[quote=lordhunter]
**But you did**:Lines one and two make a distinction based on presence/absence of new.
[/quote]

haha.. are you kidding me? it was about another issue? new != collection of objects? get it?

replace that syntax-suggestion with whatever you see fit so it doesn't disturb your `new'-thingy  -- the point was not `new' .. the point was collection of objects .. 


[quote=lordhunter]
Well, then whatever point you're trying to make you're making it rather poorly.
[/quote]

get over yourself .. i wasn't talking about you or your new-issue


[quote=lordhunter]Sure.  But that's not a useful optimization in Java for a host of reasons.  Not to mention it breaks the language semantics horribly.  The autoboxing/unboxing is proof-positive of this.  We don't want to have to further such nasty behaviors.[/quote]

this might, for a change - be the first thing you've said in a while that isn't totally paranoid or weird .. i do not know if or what this little (yes, unrelated to `new' in your context) idea of mine might break and i did mention (hm, somewhere) that "it would probably not end up as java in the end" 

maybe i'm just using the verbose syntax of static-typed java as an example of what you could remove leading to a simpler language, like ruby


[quote=lordhunter]
I do see it.  But I see all the other issues in Java that make it a bad idea.  There's a reason why only a few small types can be on the stack at all, and it's really more heartache than gain.
[/quote]

ok - this might be true said:**
> 
Yes, because you refuse to compose anything you write into complete, coherent, reasoned thought with connection between A and B.

But it's not.  Because then objects cannot outlive their scope.  That's a property that cannot generally be removed in Java.  If it could, we wouldn't need a GC *at all*.


uhm - do you think i meant adding a feature that meant _all_ objects was allocated in this way at all times? .. O_O .. man, i'm stuck in some kind of tar pit trap here aren't i ..


[quote=lordhunter]Write an application to safely and correctly read into RAM and print out a file of arbitrary length in C.  Do the same in C++, using the STL and proper C++ idioms. [/quote]

err .. no, i've got better things to waste my time on

---

### Post by Patrick-Ruff on 2007-02-05
> **Wybiral said:**
> I know what you mean by getting the initial concepts down... It all looks awkward and non-nonsensical at first. But, I promise, once you do get used to programming, learning new languages becomes pretty natural. I bet once you learn Ruby and you start to grasp the concepts and learn how the programs flow... It will make much more sense.

And then you can migrate through other languages more easily... But, who knows... You may like Ruby and it may be enough for you. However, I don't think it's ever a bad thing to learn new languages... Why stop? You know... All it's going to do is show you different ways to solve problems and new possibilities for writing programs.

Also... I personally learned from challenges. Look for some beginner challenges and try to use what you're learning to solve those challenges.

One of my first programs was this (it was in QBasic btw)...

The number guessing game.
Your program generates a random number and stores it with a variable.
Then you ask the user to guess the number.
If the user guessed too high, you tell them they guessed too high and let them guess again... If they guess to low, you tell them it was too low and let them guess again. If they guess it, tell them they won.
You also keep count of the number of guesses that were made and report that as the score (where you are obviously trying to get a low score)

Little challenges like that let you use what you're learning in context... That one makes  you use: random numbers, user input, output, comparison, and some form of loop to repeat the guesses.

If stuff like that is too easy for you... Look for harder problems and DEFINITELY look through source code of experienced programmers. You can learn a lot by studying other peoples code because simply learning a languages isn't enough... You have to learn how to build programs with the language.

heh, I know how to do that challenge in C++ except the whole randomly generating number part :D.

anyways, the main reason behind my going to ruby is so I could get down concepts for C++ ;). 

so believe me, I intend on getting into more languages then just ruby ;).

---

### Post by lnostdal on 2007-02-05
[quote=lordhunter]That's trule of any turing-complete language so that's nonsensical.[/QUOTE]
..and this, my friend - closes the case totally .. i have nothing further to add to this as it alone speaks totally for itself for what i am concerned ..

..but do rest assured the rest of it is also either wrong, misunderstood or simply do not count as counter-arguments even though they might seem to.. but i will not bother with adding anything further as i do not really care _that_ much.. :}

---

### Post by LordHunter317 on 2007-02-05
> **lnostdal said:**
> Ah, that old argument. Yes, I (or the OP) was obviously talking about a 1024MB light bulb here. Find another straw man; I'm not that dim.It's not a strawman.  No small part of software development goes into embedded systems.

I can point out tons of other examples too.  You're backpeddling.  Stop.


> i have no idea what you're saying hereIf you weren't trying to say Ruby was better than Java, you would not mention in every post.  Yet you manage to somehow...

> uhm, yeah? "because it _is_ a statically typed language", right? wow, fascinating work there sherlock .. a real zen-moment; i'm intrigued ..I'm only pointing out because you appear blisfully ignorant of that.  Your language and misuse of terms implies that you are, at least.

> haha.. are you kidding me? it was about another issue? new != collection of objects? get it?No, it patently was that.  Only a slipperly slope could reach that conclusion.  You are now backpeddling.  Stop, just admit you were wrong.

> get over yourself .. i wasn't talking about you or your new-issuePatent lie.  Stop backpeddling.

> this might, for a change - be the first thing you've said in a while that isn't totally paranoid or weirdI'm not hte one backpeddling in my argument.

> . do not know if or what this little (yes, unrelated to `new' in your context) idea of mine might breakI pointed it out.  It's obvious.  Your idea requries all objects to exist solely in scope.  That's not possible in Java, as the class library stands.  Nevermind that all all non-value types have pointer and not value or reference semantics; and that value types have transparent pointer semantics when necessary.

> maybe i'm just using the verbose syntax of static-typed java as an example of what you could remove leading to a simpler language, like rubyRuby's not simpler, though.

> err .. no, i've got better things to waste my time onThen you have no right to compare C and C++ because it's patently apparent you understand nothing about their differences.

---

### Post by Patrick-Ruff on 2007-02-05
> **jblebrun said:**
> So, Patrick, back to your issue. My advice is: if you're enjoying learning Ruby, then by all means, continue pursuing it! The most important thing you can do, especially early on, is to find a learning endeavor that you can be excited about! If you find yourself learning a language because you feel that it's something you *have* to do, then you're probably never going to learn it very well.

I hope you're enjoying Ruby so far. I just started exploring it a few months ago, because of the Ruby on Rails project. I'm still learning how to use it to its full potential, but it's a really nifty language, and I think Rails really flexes a lot of its need qualities. 

It does have rather poor performance in a number of situations, but you shouldn't let that concern you in this early learning stage. In fact, sometimes it may be better, because it will force you to think harder about how to optimize your code or algorithm to make better use of the resources that you have. 

I hope you don't mind the heated discussion that the other guys have been having here in your thread. Even though they get cranky and upset with each other, there are still often interesting tidbits of information embedded in the arguments/debates!


haha yeah, too bad I'm too tired to process everything they're saying ;).

thanks for the info, I'll be checking back to see if this thread has anymore tidbits of information ;).

---

### Post by LordHunter317 on 2007-02-05
> **lnostdal said:**
> ..and this, my friend - closes the case totally .. i have nothing further to add to this as it alone speaks totally for itself for what i am concerned ..Then you're admitting you're 100% wrong?  Thank you, I appreciate that.

---

### Post by lnostdal on 2007-02-05
> **LordHunter317 said:**
> Then you're admitting you're 100% wrong?  Thank you, I appreciate that.

yes, i am 100% wrong

(*sneaks out and reaps all the benefits*)

---

### Post by Patrick-Ruff on 2007-02-05
lol wow . . .

*goes to sleep now*

---

### Post by Wybiral on 2007-02-05
Is this evolving into a C vs C++ vs Jave battle?
Haven't I seen you guys somewhere before? lol...


> so believe me, I intend on getting into more languages then just ruby
That's always a good thing. Especially since different languages have different strong points.

If I need to write something quickly and that doesn't require 100% CPU speed... I reach for some Ruby or Python (it depends on the mood for me with those two, I mostly use ruby to keep it fresh in my mind in case I ever get to work on a rails project).

But when I'm writing something that I know needs a lot of speed... I use C or C++

C if it's going to be smaller and easier to manage (mainly device related stuff or command line tools)

C++ if I know it's going to be big and require more complicated ways of handling data.

If it's going to be small and runtime speed isn't an issue, why waste the time to type out a big C/C++ program if you can do it quicker in Ruby or Python?

Personally I don't see why there are so many die-hard, one-language programmers. Use the tool thats right for the job. If something else does the kind of work better... Consider learning it.

---

### Post by lnostdal on 2007-02-05
> **Wybiral said:**
> Personally I don't see why there are so many die-hard, one-language programmers.

yeah, i try to stick with at least two strong, in their separate fields - languages that do not overlap in too many ways .. if they did there would be almost no point in learning the second one

..i'm having a hard time keeping more than 1.5 languages "fresh" in my mind at a time though .. context-switching is a bottleneck :)

die-hard one-language, and also one-paradigm - programmers are usually newbies or intermediates (edit: or ppl. doing only one kind of task *shrug*) hoping brute force will get them through in the end .. it doesn't work unless you have 10 programmers working full time for you (lol - so forget turing completeness unless you're rich or want to start a flame-war O_o)

the first language is never a "mistake" as long as the second one does not overlap too much with it, so their worries are misguided in most cases ..  they'll be spending way more time learning truly new stuff (which is good, no?) than re-learning the "same old", as the basic "same old" between (most) languages are very similar and thus very quick to learn anyways

edit: hm, it is often subtle things one do not notice while browsing a TOC that truly creates differences between languages .. just something to keep in mind

---

### Post by Patrick-Ruff on 2007-02-05
some interesting info here, I'll keep it in mind as I learn ruby :D.

---

### Post by tc101 on 2007-02-05
I am only 2 days into learning Ruby.  I notice that Python is much more popular.  There is more support, more tools, more books.  I am having second thoughts and wondering if I should do Python rather than Ruby.  

By the way, I am the retired ASP dot net, and visual basic programmer.  Remember old guys like me learn more slowly, so learning a new language is a major time investment.  I want to pick the best one to take me into the world of Non Microsoft Programming.

---

### Post by Patrick-Ruff on 2007-02-06
well I found a great programming article that is for learning ruby that I am using now, and there have been many others that have been equally good :D. 
[http://pine.fm/LearnToProgram/?Chapter=00](http://pine.fm/LearnToProgram/?Chapter=00)

the other ones, well, they exist. python just keeps their documentation more handy :D.

---

### Post by tc101 on 2007-02-06
There is already a poll and major discussion on Ruby vs Python at

[http://www.ubuntuforums.org/showthread.php?t=308831&highlight=ruby+python](http://www.ubuntuforums.org/showthread.php?t=308831&highlight=ruby+python)

If anyone is interested in this I suggest you go there.

---

### Post by Patrick-Ruff on 2007-02-11
this was a ruby vs python debate?

---

### Post by lnostdal on 2007-02-11
> **Patrick-Ruff said:**
> this was a ruby vs python debate?

well, is it a ruby vs ruby debate?

---

