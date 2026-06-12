---
title: "What's the best way to learn C?"
date: 2006-02-18
forum: Programming Talk
---

### Post by LordRaiden on 2006-02-18
I'm really interested in learning just C before I go onto C++, so that I have a better background on the whole language. I have some experience in Java and VB so I understand most of the OO concepts. Any suggestions of books or websites would be appreciated. I learned most of my Java from Sun's Beginner documentation so anything along those lines I find myself to be comfortable with.

---

### Post by LordHunter317 on 2006-02-18
Learn C is not the path to C++.  The languages share nothing in common besides some syntax.

Just learn C++.  *Thinking in C++* is available for free online, but I really recommend *Accelerated C++* for a book.

---

### Post by Adrian on 2006-02-18
I agree. The problem with C++ for most people is to "forget" how they used to program in C and adapt to the OO way of thinking. If learning C++ is your goal, then start with C++. I'd say that it's not more difficult than C, just different (and in a lot of ways easier, actually).

If you really want to learn another language before starting with C++, I think Java is a much better choice.

---

### Post by thumper on 2006-02-18
Another vote to learn C++ not C if C++ is your destination.

I also recommend "Accelerated C++" by Koenig and Moo.

---

### Post by kvorion on 2006-02-19
C is a wonderful language to learn for its own merit. But if you want to learn C only so that it would help you to learn C++, then I suggest you start with C++ directly.

---

### Post by LordRaiden on 2006-02-24
I want to learn C so that I can use it if need it. I know that it is used in programming some drivers and embedded systems. A friend of mine also told me that having a good understanding of both languages can help when designing an application.

---

### Post by LordHunter317 on 2006-02-24
[QUOTE=LordRaiden]I want to learn C so that I can use it if need it. I know that it is used in programming some drivers and embedded systems.[/quote]Yes, but the point is, if you want to learn C, learn C.  If you want to learn C++, learn C++.  They're essentially two totally different languages except for syntax.

>  A friend of mine also told me that having a good understanding of both languages can help when designing an application.I would suggest your friend doesn't know what he's talking about, unless you're intentionally designing C++ code for access from C or similar.

---

### Post by earobinson on 2006-02-24
if you know c++ you can usualy figure out c, but it is harder the otheway around however it can be done.

---

### Post by carcrashnights on 2006-02-24
I won't try to sway you from your position of learning C first, as I did the same thing. I was in a very similar position as you, but only knew Java. Unlike the other posters, I believe that it is an acceptable path. However, I certainly agree with them that if you do not plan to use C, then don't learn it.

After stopping and starting with other books, I am certain that "The C Programming Language" by Brian Kernighan and Dennis Ritchie is an excellent way to learn C if you know a language already. Concern yourself with the the first seven chapters and just simply read the last one. The exercises aren't terribly interesting, but doing a couple per chapter wouldn't hurt.

When you are done with that, learn how to use GNU Make or scons for automating your builds. Make certain to know how to separate properly into header files and source files.

Next, when moving on to C++, find a nice tutorial. I learn from books and therefore chose Steve Oualline's "Practical C++ Programming." Using a web tutorial would be fine. You should ultimately get Bjarne Stroustrup's "The C++ Programming Language."

Please note that C++ is huge. It is impractical to consistently use the entire language. Write good code using what you know, and don't shy away from virtual functions and other heavily OOP C++.

Good luck!

---

### Post by Lux Perpetua on 2006-02-25
I recommend the book *Teach Yourself C in 21 Days* by Sam's Publishing. 

Given what you have said, that you want to learn *both* C and C++, I agree with your proposal to learn C first and then to tackle C++. The reasons are (1) your C knowledge won't be wasted in C++, since the C language is (essentially) a subset of C++; (2) C is much simpler than C++ and will be easier to learn. Knowing C **will** help you learn C++. C++ programming style is a lot different from C style, but you shouldn't have much trouble with that, coming from an OO background.

---

### Post by abhaysahai on 2006-02-26
Knowing Object oriented programming language  has nothing to do with programming in Object oriented manner. 
Most users programm in procedural form even using C++, I used to do that untill I went for a training on design patterns. 
If you already know Java, I would suggest learn OOAD with UML and design patterns before opting out for another OO Language. 
Language has more to do with syntax, learn concepts first and then go for Language. 
Might I ask the reason why you want to learn C++ when u already know Java. 

Abhay

P.S : VB is not object oriented.

---

### Post by xhie on 2006-02-26
[QUOTE=Lux Perpetua]I recommend the book *Teach Yourself C in 21 Days* by Sam's Publishing. [/QUOTE]

I 2nd that, thats a great book if your just starting out in C, the C++ version is good as well for the basics. 

On the C / C++ issue, I HAD to learn C really quickly when I first started in school, most CS/CE departments, ours included teach theory in C. Luckly I've known C++ forever, dont ask why, I was a really nerdy kid I guess. Anyways, the C++ to C transition took like a week... it really did, once you know C++, C is cake, well not cake, but it makes life easier, some of the more *elegant*  points I didnt pick up untill later, actually not untill I forced myself to work soley in C for like half a year. But my nerdyness I not the issue here....

We have a LOT of people here in school that come in knowing absoutly nothing about programming other than that you can type stuff into your computer to make it do stuff. Learning C for them starting from nothing is always hard and my advice to them is always to go learn C++ or java, then pay better attention to C. 

The java -> C++ -> C transition would go alot smoother then the java -> C -> C++ transition. Think about it for a second, C++ is built on C, its OO where C is not, java is a VERY good first language to learn because it makes learning and understaning OO programming fun, well I suppose "fun" is a relative term, anyways, go from what you know, a very good OO language, to a an *intermediate* step with C++, then down to the procedual C language, dont loose that inbetween step.

---

### Post by LordHunter317 on 2006-02-26
> **Lux Perpetua]I recommend the book *Teach Yourself C in 21 Days* by Sam's Publishing.[/quote]The way you know a book is crap is that it starts with "Teach Yourself " and ends in "XX Units of Time".  I've read it some ages ago for some class, it's not very good.  It's a passable syntax tutorial.

> The reasons are (1) your C knowledge won't be wasted in C++, since the C language is (essentially) a subset of C++ said:**
> Yes, it will.  The right way to do something in C is almost universally the wrong way to do it in C++.  Conversely, the right way to do something in C++ is impossible in C.

[quote] Knowing C **will** help you learn C++.No, it won't.  It'll only serve to confuse.  

[quote=abhaysahai]Might I ask the reason why you want to learn C++ when u already know Java. Because Java is a poor language in lots of ways?

> P.S : VB is not object oriented.VB6 barely clears the bar.  VB.NET clears it with room to spare, despite being excessively verbose.

---

### Post by Lux Perpetua on 2006-02-26
[QUOTE=LordHunter317]The way you know a book is crap is that it starts with "Teach Yourself " and ends in "XX Units of Time". [/quote]Potshot.> I've read it some ages ago for some class, it's not very good.  It's a passable syntax tutorial.It's a very readable book, but it is aimed at people without much computer experience. It's basically a beginner's tutorial. 
[QUOTE=LordHunter317]Yes, it will.  The right way to do something in C is almost universally the wrong way to do it in C++.  Conversely, the right way to do something in C++ is impossible in C.[/quote]That wasn't my point. C++ is easier to learn if you're already comfortable with the fundamentals (data types, variables, functions, etc.) and can concentrate on the bigger things. 
> No, it won't.  It'll only serve to confuse. Your opinion, I guess. I, and others, didn't find it confusing.

Edit: Think of it this way: if you know C, then you already know *some* C++. Therefore, you have less work to do to learn the rest. The unlearning you have to do is only an issue if you are really set in your ways style-wise and design-wise; the only language features to unlearn are things like "use new instead of malloc" and various features of the library. If you know C++, then you don't necessarily have any idea what C is (knowing that it is some subset of what you already know doesn't help). If you now have to learn C, you have to unlearn most of the C++ language. This can be a painful process. I experienced it when I recently started learning Fortran 77, having programmed in more modern languages.

I am not saying that a person should learn C first if the goal is only to learn C++. I am saying that if both C and C++ are to be learned, then it makes sense to go for the more primitive one first.

---

### Post by LordHunter317 on 2006-02-26
[QUOTE=Lux Perpetua]That wasn't my point. C++ is easier to learn if you're already comfortable with the fundamentals (data types, variables, functions, etc.) and can concentrate on the bigger things. [/quote]Not especially.  Books like Accelerated C++ exist for a reason, and are well expected for a reason.  And you don't need to know C to read it.

In fact, if you wanted to learn C, it's probably a better text than any C text I could recommend.  I don't know any good C texts that serve as a tutorial that actually teach both the language and sound design at once.

> Your opinion, I guess. I, and others, didn't find it confusing.You're clearly confused if you're suggesting one to the other.  What value other than syntax does knowing C give to writing correct C++ code?

---

### Post by Lux Perpetua on 2006-02-26
Sorry, I didn't see your post. I edited my reply above. 

The value is this: knowing a relatively easy language like C makes it easier to learn a complex extension of it like C++. On the other hand, knowing a full-featured and powerful language like C++ makes it harder to learn a more restricted subset of it.

---

### Post by LordHunter317 on 2006-02-26
> **Lux Perpetua] The unlearning you have to do is only an issue if you are really set in your ways style-wise and design-wise said:**
> Which is infinitely more important than lanmguage.

>  the only language features to unlearn are things like "use new instead of malloc" and various features of the library.ITYM you mean all the features of the library.  Save for a few small things (e.g., ctype, math) you shouldn't be using the C standard library *at all* in C++, especially if you're a beginner.

[quote]If you know C++, then you don't necessarily have any idea what C is (knowing that it is some subset of what you already know doesn't help). If you now have to learn C, you have to unlearn most of the C++ language.You have to do it anyway if you go the other way, so it's a non-sequitur.

> I am not saying that a person should learn C first if the goal is only to learn C++. I am saying that if both C and C++ are to be learned, then it makes sense to go for the more primitive one first.I don't think that's true, as the carryover is limited to solely syntax.

---

### Post by abhaysahai on 2006-02-26
[QUOTE=LordHunter317]The way you know a book is crap is that it starts with "Teach Yourself " and ends in "XX Units of Time".  I've read it some ages ago for some class, it's not very good.  It's a passable syntax tutorial.

Because Java is a poor language in lots of ways?
[/QUOTE]

I realize that Teach Yourself is just a syntactical book, but no book in my openion is crap, its just that they target a different set of readers. 

Java -- a poor language ???? 
Java is much better structured in comparison to C++. It implements all the possible sortcomming of earler languages like C++. 
For instance, we all know multiple inheritance can lead to problems in C++, but C++ still allows it. The solution is to use pure virtual base class. Java on the other hand implements this as part of syntactical regulations. 
chances of doing error in Java is much less than in C++. That apart, I am a pure C/C++ programmer and have limited knowledge of Java. Could you please highlight some of the shortcommings of Java w.r.t C++.

---

### Post by LordHunter317 on 2006-02-26
> **abhaysahai]Java -- a poor language ????[/quote]Yes, it's fundamentally poor in several ways.  It lacks closures, and desperately needs them (made all the more irksome by the fact they were stripped before 1.0).  The single class hierarchy is a mistake.  Object should really be the equivalent of (void*), not all of those operations make sense on all child objects, hence, they shouldn't be in the parent.  It was done to make their life eaiser.  Generics aren't real generics, but just cast wrappers.  This was originally done for backwards compatibility, but then they broke the latter anyway and forgot to fix the generics.  Oops.

I could go on, but Java has plently of major, boneheaded decisions about it.

> Java is much better structured in comparison to C++.If by structure you mean syntatically cleaner, sure.  No arguments here said:**
> It implements all the possible sortcomming of earler languages like C++.If by implements you mean, "fixes", no it doesn't.  

> For instance, we all know multiple inheritance can lead to problems in C++, but C++ still allows it.Which is why you use it judiciously and correctly.  Just because something lets you do bad things isn't a reason to remove it, *per se*.

>  The solution is to use pure virtual base class. Java on the other hand implements this as part of syntactical regulations.No, it doesn't.  Interfaces aren't pure virtual base classes, they're not implemented this way.  And Java's weak MI has more flaws than C++ complicated MI: specifically, there's no way to provide different implementations of inherited methods of the same name.  This isn't normally a problem in C++, nor is it a problem in C#.

> chances of doing error in Java is much less than in C++.Ahh, but in Java, when you commit it, it's impossible to correct it.  The language won't let you.  It's impossible.

---

