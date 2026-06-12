---
title: "Learning Python/C++ need help finding problem solving reading material"
date: 2006-08-25
forum: Programming Talk
---

### Post by Omnios on 2006-08-25
Hi I have been playing around with Python trying to learn and found a dud 404 page on programming problem solving. Anyways does anyone know any good online/pdf reading materials on this subject or a good page of everyday examples of code. I think this will realy help me understand things better.

---

### Post by Woei on 2006-08-25
> **Omnios said:**
> Hi I have been playing around with Python trying to learn and found a dud 404 page on programming problem solving. Anyways does anyone know any good online/pdf reading materials on this subject or a good page of everyday examples of code. I think this will realy help me understand things better.

Well, uhm, I should really advice you *against* picking up C++ first as it is an extremely complex language where even good, experienced programmers have trouble getting the code just right. You'll really need some programming experience with an easier to read language, as C++'s syntax will just scare you otherwise and obscure general coding patterns like inheritance, object composition and API design. Python, on the other hand, is excellent as a first language. It's simple to learn but has all the features of a good OO language and then some. Moreover, the standard library that comes with Python is large and there are several good introductory books on Python.

One you can get for free is '[How to think like a computer scientist](http://www.ibiblio.org/obp/thinkCSpy/)'. It's written for an outdated version of Python, but most will still apply. I advice on getting an updated book (like Learning Python) for fully grokking the new features of modern Python versions. If you need some sample code on how to use Python's standard library, look no further than '[The Standard Library](http://effbot.org/librarybook/)', also available for free on the web. If that has you craving for more, you can pick up more advanced Python books.

As for C++. First, learn Python. You'll probably be able to do everything you want with it, and there are excellent bindings for both GTK and QT available. If you really must do C++, then begin with a cheap introductory, second hand book on C++. Skim over it to absorb the nasty syntax, but you'll already know the semantics of classes, methods, inheritance and object composition through Python, making the C++ learning process much easier. After that, it's either the painful route of *the* reference on C++: 'The C++ Porgramming Language' by Bjarne Stroustrup, but that book is 1000 pages long written in an incredibly obtuse way. Better would be getting the more lively 'Effective C++' from Scott Myers coupled with the seminal book 'Design Patterns' (*Gang of Four*) on modern, object oriented programming.

Happy reading. ;)

---

### Post by LordHunter317 on 2006-08-25
> **Woei said:**
> Well, uhm, I should really advice you *against* picking up C++ first as it is an extremely complex language where even good, experienced programmers have trouble getting the code just right.That's not really exclusive to C++, but C++ doesn't make a lot of things any harder than any other language.

> You'll really need some programming experience with an easier to read language, as C++'s syntax will just scare you otherwise and obscure general coding patterns like inheritance, object composition and API design.Excpet that none of those are drastically anymore complicated (assuming you're only talking about OO API) than any other OOP language.  It's more complicated than say C# or Java if you exploit all the fancy MI features, but someone learning programming won't be doing that.

Seriously.  You can't even show the syntax is more complicated because it isn't.

> If you really must do C++, then begin with a cheap introductory, second hand book on C++.Or get a good book like *Accelerated C++* and then good reference material like the Effective C++ series and *The C++ Standard Library: A Tutorial and Reference.*


> but you'll already know the semantics of classes, methods, inheritance and object composition through Python,Except for the whole part where using the C++ standard library requires understanding very little about objets.

>  Better would be getting the more lively 'Effective C++' from Scott Myers coupled with the seminal book 'Design Patterns' (*Gang of Four*) on modern, object oriented programming.Actually GOF would be a terrible choice for C++.  There's always a better path then what they describe in that book, because it ignores generic-programming techniques available in C++ that aren't available in most other languages.

It bothers me greately when people give advice on a language and clearly do not understand it.

---

### Post by Woei on 2006-08-25
> **LordHunter317 said:**
> That's not really exclusive to C++, but C++ doesn't make a lot of things any harder than any other language.

***Cough*** manual memory management ***Cough***
***Cough*** insane and nearly incomprehensible compiler errors of tens of lines ***Cough***
The rediculous virtual/non virtual soup. Templating. Include guards. Edit, compile, run cycle. Forgot to make your destructor virtual ? See your app blow up in some unspecified way later on.

> Excpet that none of those are drastically anymore complicated (assuming you're only talking about OO API) than any other OOP language.  It's more complicated than say C# or Java if you exploit all the fancy MI features, but someone learning programming won't be doing that.

Someone learning how to program doesn't need the power, flexibility and speed of C++. They want something that will not scream murder if they forget a ; after their class declaration.

> Seriously.  You can't even show the syntax is more complicated because it isn't.

Right. C++'s syntax is just as easy as Python's or Ruby's is. I bet you find Perl a joy to read too, hmm ?
```

template <typenema Child>
class Base {
     void foo() {
     static_cast<Child*>(this)->foo();
     }
};

```

Or what about the 4 places you can put the *const* keyword in a method declaration, each semantically completely different, only based on their surrounding ? What about something more trivial, like the difference between . and -> to dereference something. Or why the copy constructor needs a reference as its argument instead of a pointer or a plain type ? All things newcomers needn't concern themselves with to get a grasp of programming.

> Except for the whole part where using the C++ standard library requires understanding very little about objets.

Java, .NET languages, all modern scripting languages: they all favor object oriented libraries and abhor templated functions as in C++'s library. Yes, they do basically the same, but conceptually, the 'everything is an object' approach is easier to grasp.

> Actually GOF would be a terrible choice for C++.  There's always a better path then what they describe in that book, because it ignores generic-programming techniques available in C++ that aren't available in most other languages.

Note that the OP asked for introductory material, not some deep template voodoo magic like in 'Modern C++'. Do all examples in that book compile already BTW ? The ideas presented in the GoF book are pretty timeless and can be easily transplanted to Java or C#. Knowing how to conceptually think about a Visitor or a Decorator will help you far more than knowing how template metaprogramming works or how vtables work. It's about the *libraries* and *concepts* these days, not about speed and knowing a complex language like C++ inside out.

> It bothers me greately when people give advice on a language and clearly do not understand it.

How nice of you to judge me about what I supposedly know or don't know based on a short forum post, trying to help someone getting their feet wet on programming. Newsflash: C++ is being replaced by Java, .NET and scripting languages for mainstream development. C++ is *hard* and the speed benefits don't outweigh the loss of developer productivity, general library availability, documentation, mindshare and general ease of use.

Frankly, I find your attitude elitist. Yes, I started with C and later C++. That doesn't mean I think new programmers should go through the pains of learning to work with the C or C++ libraries and hunting down some strange memory leak that originated who knows where in your program. If I would had a go at it again, I'd gladly 'remove' all what I've learned from C and C++ to go directly to something like Java or Python. The general concepts remain the same, but all with an easier syntax, no memory management and greater productivity.

Have a nice day.

---

### Post by chonger on 2006-08-25
I find it more helpful to get into a project, rather then just reading from a book. You can start by taking some of the scripts you have previously written and re-write them using python. If you are a web developer, try writing some simple web applications using python. 

Here are some links for good python reading. You can find a bunch of them at python.org, but I think these two to be the best to start with.

[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)
[http://diveintopython.org/](http://diveintopython.org/)

---

### Post by LordHunter317 on 2006-08-25
> **Woei said:**
> The rediculous virtual/non virtual soup.Which is a feature of Java and C# too.  It's technically a feature of all OOP languages featuring static methods, if you want to get technical and nasty.  But a language without the ability to force a method to be non-virtual is really a negative, IMO.  It's hardly rediculous.  It gives you better control over mutable behaviors, which is a good thing.  

The only negative thing about C++ is that pure virtual functions have ugly syntax and can have a definition.  But the former isn't horrible, and the latter is a little-known, rarely-used secret.  Certainly not relevant to an introductory programmer.  Certianly not relevant to 99% of C++ programmers.

> Templating.Their usage isn't ugly, only their declaration.  Introductory programmers won't be creating them, so who cares?  And if you're doing basic templating, on the level of generics, it's only one line of extra uglyness over Java or C#.
 
> Include guards.What about them?  Introductory programmers don't need to worry about them, and they're not really that complicated.

> Edit, compile, run cycle.This is a potential negative, but it's not hardly exclusive to C++.

> Forgot to make your destructor virtual ? See your app blow up in some unspecified way later on.And?  Taught properly, an introductory programmer won't have that problem.

But it's not like Python is issue free either.

> Someone learning how to program doesn't need the power, flexibility and speed of C++.And?  They don't need the power of Python or Scheme either, yet people are taught programmer in both of those languages all the time.  

> They want something that will not scream murder if they forget a ; after their class declaration.And?  Python won't scream murder if you screw up your indentation (*per se*) but your code won't work.  That's arguably worse, because you don't immediately know what's wrong.

> Right. C++'s syntax is just as easy as Python's or Ruby's is.In the context of an introductory programmer, sure.  Your code sample is a total non-sequitur **because it goes outside the bounds of what *you* and I were talking about.**

Nevermind I can't even figure out why the hell someone would do that.

> Or what about the 4 places you can put the *const* keyword in a method declaration, each semantically completely different, only based on their surrounding?Seeing that the meanings are clear in context, and there aren't four different semantic meanings, no.

> What about something more trivial, like the difference between . and -> to dereference something.If you get it wrong, it's not like the compiler doesn't tell you.  That's not perfect, but at least it's enforced.

> Or why the copy constructor needs a reference as its argument instead of a pointer or a plain type ?It's fairly obvious.  But it's not like Python tells you when you forget 'self' as the first argument to a member function.

> All things newcomers needn't concern themselves with to get a grasp of programming.Neither are lots of things in Python.

The problem with your argument is it's fundamentally bad tact.  All your issues are language inconsistencies.  I can easily leverage arguably equally bad inconsistencies at Python.  What you should be doing is noting an inconsistency or bad feature, and then using other logic to explain why it's bad for a learning programmer to deal with.  An argument with a main thrust of, "The language is inconsistent" is a strawman unless you're arguing for them to learn Scheme.

>  they all favor object oriented libraries and abhor templated functions as in C++'s library.Which is why Java **5** and .NET 2.0 **added** generics?  Don't think so.

> Yes, they do basically the same,They most certainly do not.  This makes it clear you don't understand the limitations of OOP static-typing and how templates can be a solution to many of their problems.

Write me a swap function in Java that doesn't use generics, and works for any class.  You can't do it.  It's *unpossible*.

> but conceptually, the 'everything is an object' approach is easier to grasp.No, it isn't.  Most of the common properties of the parent object class are simply not useful, or are best implemented in other ways.

> Note that the OP asked for introductory material, not some deep template voodoo magic like in 'Modern C++'.And did I recommend that?  No.  Please read what you're responding to. 

> Do all examples in that book compile already BTW ?I don't know, I've never read it.  I didn't even recommend it.  I don't even know who it's by.

> The ideas presented in the GoF book are pretty timeless and can be easily transplanted to Java or C#.And?  That doesn't make them *good*.

> will help you far more than knowing how template metaprogramming works or how vtables work.I've never once written a template MP nor do I know about or care about the inner workings of vtables.  You don't have to know that.

> It's about the *libraries* and *concepts* these days,Computer science is strictly about the theories of computation.  You don't even have to know a language to study it.  Applied programming is also mostly about that, because learning libraries is generally easy.  And, because if you understand how to write the algorithms, you ultimately don't need them.

> not about speedThe whole point of CS is finding ways to do things faster (or in less space, but that's really the same deal).  You just thumbed your nose at the whole industry.

> and knowing a complex language like C++ inside out.Which no one here suggested.  You're arguing against a ghost.

> How nice of you to judge me about what I supposedly knowSorry, but it's rather apparent.  You would not make the comments you did if you really understood modern, standardized C++ programming.

>  Newsflash: C++ is being replaced by Java, .NET and scripting languages for mainstream development.And?  Scheme isn't used in the mainstream at all, yet *MIT* uses it as their *first* language.  Might want to go talk about to them about it.  This is a fundamental non-sequitur.

> C++ is *hard* You've failed to demonstrate that.  Just because a language has "hard" features doesn't mean you have to use them.  Macros in Scheme are hard, yet there is no onus to use them.

> and the speed benefits don't outweigh the loss of developer productivity, general library availability, documentation, mindshare and general ease of use.You've failed to prove any of those statements.  You haven't even supported them.  More importantly, I don't believe you can.

> Frankly, I find your attitude elitist.It isn't, because my position is supported with facts and reason.  Your argument has no valid standing, because your position is just as vulnerable to the same line of reasoning.  Mine, OTOH, is not.  Mostly because *I haven't presented any argument for C++ yet, because your haven't presented any valid reasoning against it.*

>  Yes, I started with C and later C++. That doesn't mean I think new programmers should go through the pains of learning to work with the C or C++ libraries and hunting down some strange memory leak They umm, don't. Not if they're properly taught.

> The general concepts remain the same, but all with an easier syntax, no memory management and greater productivity.Java OOP syntax is almost identical.  Certainly for the concepts that can be expressed in Java, the changes are:[list][*]Protection levels are labels at class-level, not function modifiers[*]All non-final functions get virtual and all final functions do not[*]You list parents after the colon[*]Initialization lists[/list]Done.  Besides a few extra semicolons, they're identical in syntax.  Initialization list rules are by far the most complicated subject, and you didn't even touch on them.  Frankly, I shouldn't have to be writing your argument for you.

---

### Post by matthew on 2006-08-25
Wow! I go offline for a couple of hours and come back to discover this is becoming a bit of an off-topic flamewar. This thread has already been reported by users, but I would like to keep it open, so may I politely suggest we all take a huge step back and only post in this thread if you have a suggestion for Python/C++ reading material. 

Maybe we can all take a deep breath and choose not to post until tomorrow...that should be enough time to cool down and avoid the backyard/locked thread syndrome.

---

### Post by Omnios on 2006-08-25
Hi I have been reading "How to Think Like a Computer Scientist" Python edition on and off again and it is a real good book. I opened this post to see if there is reading material more on the lines of problem solving and good code that is not normally coverd in some of these books. I heard Dive into python was pretty good in that respect.

---

### Post by neilp85 on 2006-08-26
> **Omnios said:**
> I heard Dive into python was pretty good in that respect.
I will second that. Dive Into Python was the book that I started with and couldn't have been happier. May I also suggest Python Cookbook once you have a grasp on the language. I'm currently reading that and it has tons of good code samples.

---

### Post by Omnios on 2006-08-26
I was also looking for a indepth article or books on loopes and conditionals and the different ways of using etc.

---

### Post by dwblas on 2006-08-28
I like FAQTS for python examples
[http://www.faqts.com/knowledge_base/index.phtml/fid/199/](http://www.faqts.com/knowledge_base/index.phtml/fid/199/)
also, there is active state
[http://aspn.activestate.com/ASPN/Cookbook/](http://aspn.activestate.com/ASPN/Cookbook/)
and python eggs has a lot of links
[http://www.python-eggs.org/](http://www.python-eggs.org/)

---

### Post by cptnapalm on 2006-08-28
I opened this thread looking for some Python stuff.  I'm old, but I want to learn to do stuff.

Anyhow, while I do understand the mod's point about sticking to topic, I have to say that language flamewars are the last vestige of a long *nix tradition of flaming.  Usually, a flame war goes something like <fill in the blank> suX0Rz!!!!1!!  <fill in the blank> RuL3Z!!!11!

having seen a few vi vs. emacs flame wars and KDE vs. Gnome ones, but not for a long time, I have to say that i was rather enjoying the mini language war that kicked off, even though I didn't understand half of it.

But ON TOPIC, I have Learning Python.  The beginning chunk is tedious and pointless, but once it gets started, its pretty good.  I also am fond of How to think like a Computer Scientist.

Good resource is to go to python.org and check out the Documentation section.  There is a healthy number of links for people of various levels of experience.

---

### Post by dwblas on 2006-08-29
Sometime in your Python travels, you also want to look at John Grayson's book on Tkinter and Python (it may be on the web) for GUI apps.

---

### Post by rplantz on 2006-08-30
> **cptnapalm said:**
> I opened this thread looking for some Python stuff.  I'm old, but I want to learn to do stuff.

I am also old, and retired. It's fun having the time to learn new things.
> 
having seen a few vi vs. emacs flame wars and KDE vs. Gnome ones, but not for a long time, I have to say that i was rather enjoying the mini language war that kicked off, even though I didn't understand half of it.


Language arguments remind me of when we decided to move from Pascal to C as our introductory teaching language at my university in the late 80s. I was the first prof. to teach the 4-unit class. We also had a 2-unit class on C for Pascal programmers, which I taught during the same semester.

I chose the Deitel & Deitel book. I thought that the Pascal savvy students knew the concepts, so I could quickly move through the slightly different (in my view) syntax and move onto the more interesting later chapters.

Wrong! The C syntax was so new to the Pascal students, that I had to cover the same material in both classes. About the only advantage they had over the completely naive students is that they knew how to use the editor, compile, submit projects, etc.

Although this was certainly not a statistically valid study, I concluded that most of us really need to learn several languages before we fully understand the concepts. I think it's because it helps to see how a concept is implemented in several different ways.

My other observation relates to books. Students often told me that they had found a better book. Early in my teaching career I felt bad about not picking the best book. Then it dawned on me that the second book is almost always easier to read than the first one you read on any subject. In addition, learning is very individual. It's very difficult to select a book that works well for all the students.

---

