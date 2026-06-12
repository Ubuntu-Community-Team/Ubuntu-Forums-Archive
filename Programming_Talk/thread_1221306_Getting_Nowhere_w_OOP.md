---
title: "Getting Nowhere w/ OOP"
date: 2009-07-23
forum: Programming Talk
---

### Post by mvalviar on 2009-07-23
Hi,

I'm programming with php. I know the how to code php including the oop syntax but is still do procedural programming. I've read books on OOP but I still can't use it.

I know how to use classes from libraries. But that's just about it. I don't know when I should extend them or when to use interfaces and abstract classes.

Lets say I want to make a blogging web app. How do I start? I can't 'envision' the objects that I will use. 

Whenever I try to start a small exercise that is object oriented I can't code it.

---

### Post by dwhitney67 on 2009-07-23
Well, the first problem you are having is that you are attempting to jump from concept to code.

Have you ever considered defining your requirements first?  Perhaps from there, put together a description of how your requirements will be met (ie. put together one or more Use Cases).  Then from there, perhaps you will see some areas in which you can develop the design for your code, OO or otherwise.

Lastly, you can implement the code that will perform the actions that you have conceived.

---

### Post by HotCupOfJava on 2009-07-23
I can empathize with your situation. Years ago, I dabbled in BASIC. Once I finally took some programming classes, they started me with COBOL. Then I moved on to C and MS Visual Basic (which wasn't REALLY OOP). When I finally got to Java, I had so much procedural background that OOP made my head spin. It actually took me walking away and coming back to it on my own for me to finally grasp it. The terminology the teachers were using didn't help. I was trying to apply what I knew about procedural programming and interpret what they were telling me through that. Terms like "methods", "interfaces", and "instance variables" just didn't make sense in that context. 

Now that I have gotten a good handle on Java, I really can't imagine ever going back to pure procedural programming. There will always be procedural elements to the code, but the ease of maintaining an OOP app AND the speed with which one can be developed makes OOP the way to go (for me, anyway).

---

### Post by Drone022 on 2009-07-24
I too was taught Java as a way of introducing me to object orientation. If your struggling to grasp it then sit down with some problems and try to identify the classes you would need plus the methods they might contain. 

I dont have much knowldege about the OOP aspects of PHP but I would suggest learning some Java in order to help you grasp concepts. I always found the object orientated programming concepts tutorial on the Sun site to be pretty good.

[http://java.sun.com/docs/books/tutorial/java/concepts/index.html]("http://java.sun.com/docs/books/tutorial/java/concepts/index.html")

Obviously its not PHP but it might help you out.

---

### Post by apoth on 2009-07-24
I've not tried it with PHP, but it may be worth looking at Java as, to some extent, it's a little more enforced. Always worth seeing how problems are solved in a different language anyway.

Don't worry though, stick at it, I spent ages struggling with it when I was first trying to pick it up and had very much a Eureka! moment one day.

---

### Post by mvalviar on 2009-07-24
I know how to code in Java too. I started with C so it's real easy to pick up C like languages. 

With Java it's like I know how to read and write the language but I can't write a piece of literature with it. 

And that's a whole other problem with me. I know how to read/write a number of programming languages. But I'm not an expert at any of them. Except php/javascript (html/css/mysql) since I earn a living using them. A number of resources on the net says OOP can boost productivity. I've been lucky since I haven't encountered a project that will enforce me to code OO style.

How can I join the 'bazaar' so I can put these languages in practice and at the same time learn and contribute?

---

### Post by hoboy on 2009-07-24
> **mvalviar said:**
> I know how to code in Java too. I started with C so it's real easy to pick up C like languages. 

With Java it's like I know how to read and write the language but I can't write a piece of literature with it. 

And that's a whole other problem with me. I know how to read/write a number of programming languages. But I'm not an expert at any of them. Except php/javascript (html/css/mysql) since I earn a living using them. A number of resources on the net says OOP can boost productivity. I've been lucky since I haven't encountered a project that will enforce me to code OO style.

How can I join the 'bazaar' so I can put these languages in practice and at the same time learn and contribute?

I know precisely what you are struggling with, I had similar problem but, then learn how to design applications in OO, I was confusing coding and design, learn to design in java.
Take you time to listen to this 

[http://www.youtube.com/results?feature=moby&search_query=stanford+java+programming&search_type=&aq=0&oq=stanford+java](http://www.youtube.com/results?feature=moby&search_query=stanford+java+programming&search_type=&aq=0&oq=stanford+java)

---

### Post by hoboy on 2009-07-24
> **hoboy said:**
> I know precisely what you are struggling with, I had similar problem but, then learn how to design applications in OO, I was confusing coding and design, learn to design in java.
Take you time to listen to this 

[http://www.youtube.com/results?feature=moby&search_query=stanford+java+programming&search_type=&aq=0&oq=stanford+java](http://www.youtube.com/results?feature=moby&search_query=stanford+java+programming&search_type=&aq=0&oq=stanford+java)

[http://www.youtube.com/results?feature=moby&search_query=Lecture+by+Professor+Mehran+Sahami&search_type=&aq=f](http://www.youtube.com/results?feature=moby&search_query=Lecture+by+Professor+Mehran+Sahami&search_type=&aq=f)

---

### Post by howlingmadhowie on 2009-07-24
i would say that oop is basically about namespaces (defining variables and functions in such a way that they can only be accessed in certain ways). namespaces are often logically useful as a way of managing code complexity (if i change something small, how often do i have to make allowances for that in my program?), but there are ways to get something similar without using the word 'class'. in some cases, object orientation forces you to ask yourself pointless questions (if i add an instance of float to an instance of int, which class should know how that works?), so it may be that your way of thinking just doesn't fit into object orientation.

---

### Post by mvalviar on 2009-07-24
Thank you very much for the replies. OOP is really something in the programming world. I believe that I can never call my self a programmer without mastering OOP.

---

### Post by altonbr on 2009-07-24
> **hoboy said:**
> I know precisely what you are struggling with, I had similar problem but, then learn how to design applications in OO, I was confusing coding and design, learn to design in java.
Take you time to listen to this 

[http://www.youtube.com/results?feature=moby&search_query=stanford+java+programming&search_type=&aq=0&oq=stanford+java](http://www.youtube.com/results?feature=moby&search_query=stanford+java+programming&search_type=&aq=0&oq=stanford+java)

> **Drone022 said:**
> I too was taught Java as a way of introducing me to object orientation. If your struggling to grasp it then sit down with some problems and try to identify the classes you would need plus the methods they might contain. 

I dont have much knowldege about the OOP aspects of PHP but I would suggest learning some Java in order to help you grasp concepts. I always found the object orientated programming concepts tutorial on the Sun site to be pretty good.

[http://java.sun.com/docs/books/tutorial/java/concepts/index.html]("http://java.sun.com/docs/books/tutorial/java/concepts/index.html")

Obviously its not PHP but it might help you out.

Those are some really great resources. Thanks guys.

Also, if you want to check out a PHP framework that is coded in OOP, is open source and may enable you to learn OOP by reading the code, I suggest looking at [KohanaPHP]("http://kohanaphp.com").

Good luck!

---

### Post by apoth on 2009-07-24
> **mvalviar said:**
> I know how to code in Java too. I started with C so it's real easy to pick up C like languages. 

With Java it's like I know how to read and write the language but I can't write a piece of literature with it.

Ok, cool. You're probably further down the route than you realise then. All it's about really is dividing logic up into bite size portions instead of 50000 line procedural programs, so programmers can develop different parts of a system largely in isolation and producing something more manageable.

There's only one way you're really going to get a grasp on it and that's to keep programming with it. Perhaps think of problems you'd like to solve in OOP and post how you think you'd solve it using OOP and ask for feedback?

---

### Post by wmcbrine on 2009-07-25
As I think others have implied here, it seems to me that the main problem in grasping OOP is that it's been made out to be a much bigger deal than it really is. When I finally got around to learning it, my reaction was, "Is that all there is?". It's kind of trivial, really. I mean, a fine programming technique, sure, but not something to build a cult around, as has been done. Understanding it is no deeper than understanding, say, recursion.

---

### Post by nvteighen on 2009-07-25
Object Oriented Programming is **not** a programming paradigm, but a design paradigm. You can have OOP in C, Forth, C++, C#, Lisp, Perl... heck, in any language that has means of combining smaller data structures into a bigger one and give it a name.

(The proof that OOP is not a programming paradigm but a design one is that you can have OOP in imperative programming and functional programming... and maybe even in declarative programming (XHTML). If it was a programming paradigm, then that wouldn't be possible as programming paradigms are exclusive).

Procedural programming (also a design paradigm) is about modelling some reality using procedures (actions) as the building block. So, some reality will be a sequence of actions performed.

OOP is about modelling some reality using objects as the building block and stating how these objects relate and interact with eachother. The reality then will be considered as a set of objects that, in contact, do stuff.

Chances are that you are doing OOP without even noticing. Don't be afraid by those language-specific features like polymorphism, inheritance, virtual methods, explicit OOP syntax, etc. that are great aids to make better object abstraction, but they're not part of the definition of OOP. OOP in C is possible, but a pain to write, because there's no explicit syntax for it... and you'll have to implement inheritance, polymorphism, etc. by your own (or use some library)... but it's still possible (and here I throw the usual example: look at GTK+).

Let's say you want to program how a kid rides his bike.

In procedural programming, you'd say that there's a ride with two parameters, the rider (kid) and the vehicle (bike). In OOP, you could say there is a kid and there's a bike... and that the relationship between those objects is that the kid rides the bike.

If you program thinking in terms of stuff that relates to other stuff, you're doing OOP. If you program thinking in terms of processes that happen sequentially, you're doing procedural programming. 

That's all there is :)

---

### Post by Yacoby on 2009-07-25
> **nvteighen said:**
> Object Oriented Programming is **not** a programming paradigm, but a design paradigm. You can have OOP in C, Forth, C++, C#, Lisp, Perl... heck, in any language that has means of combining smaller data structures into a bigger one and give it a name.Just because I can write stateless programs in C++ doesn't mean that Functional Programing is not a programming paradigm

---

### Post by HotCupOfJava on 2009-07-25
> **nvteighen said:**
> Object Oriented Programming is **not** a programming paradigm, but a design paradigm. You can have OOP in C, Forth, C++, C#, Lisp, Perl... heck, in any language that has means of combining smaller data structures into a bigger one and give it a name.

Yes, but I think that a strong case can be made that some languages are designed with OOP in mind much more so than others. Inheritance and polymorphism are certainly much easier to pull off in Java than they would be in say, C. If you are intending to use such design methods, you usually DON'T turn to C. And from an educational perspective, such concepts usually aren't taught in languages that existed prior to the 1990's. So, we tend to associate OOP with certain languages, and NOT with others. Not that it can't be done, but why on earth would you attempt it?

---

### Post by issih on 2009-07-25
Hmmn..slightly arrogantly I will whitter on about the point when I "got" it.

I was writing a version of freecell (that silly card game), whilst learning about OO coding.

My initial version basically has arrays for all the different piles of cards, and then a big Game class that defined functions for moving a card (or pile of cards) from one area to another. The move functions all lived on the Game class and performed a validation check and then moved the cards from one array to the other.

This worked, but it was no different to how I would have done things in a procedural language.

Once I'd begun to see the light, I rewrote it entirely, my new Game class had nothing but an array of "GameAreas", and one function that allowed you to tranfer cards from one gamearea to another, by calling an add method on one object and passing the other object as a parameter.

The subclasses of GameArea (stack, freecells, piles) overrode the add method to add custom validation routines, whilst the basic mechanics of moving cards from one class to another were defined at the GameArea level.

That is the whole game. Each individual area knows the rules associated with it, there is no overriding monolithic control centre. The main advantage of this, is that to implement a new card game, all you need to do is create different subclasses of GameArea, with new validation routines, and add those to the top level Game class. 

That is what OO is about, put the functionality close to the relevant data, rather than simply putting all the functionality in one place, and its aim is to allow fast reuse of as much of the existing code as possible when repurposing things

Hope that helps

---

### Post by Can+~ on 2009-07-25
> **HotCupOfJava said:**
> Yes, but I think that a strong case can be made that some languages are designed with OOP in mind much more so than others. Inheritance and polymorphism are certainly much easier to pull off in Java than they would be in say, C. If you are intending to use such design methods, you usually DON'T turn to C. And from an educational perspective, such concepts usually aren't taught in languages that existed prior to the 1990's. So, we tend to associate OOP with certain languages, and NOT with others. Not that it can't be done, but why on earth would you attempt it?

Isn't that what nvteighen just said?

[QUOTE=nvteighen]OOP in C is possible, but a pain to write, because there's no explicit syntax for it... and you'll have to implement inheritance, polymorphism, etc. by your own (or use some library)... but it's still possible (and here I throw the usual example: look at GTK+).[/QUOTE]

> Just because I can write stateless programs in C++ doesn't mean that Functional Programing is not a programming paradigm

I'm not entirely convinced by the argument of nvteighen either.

If I code (with a lot of free time) a program that could create a list which can hold operations and data like a Scheme clone, and use it on my C code, like [FONT="Courier New"]run_operation(list)[/FONT], can I consider that I just build the Functional Paradigm on my code? Or it doesn't count as I'm creating a new abstraction layer?

---

### Post by nvteighen on 2009-07-25
> **Yacoby said:**
> Just because I can write stateless programs in C++ doesn't mean that Functional Programing is not a programming paradigm

No, it means that it is a programming paradigm: It is a set of rules on that will define what is allowed and what not in the code. A design paradigm seems more like a set of rules to start a model. 

OOP is not a programming paradigm because you can use it with different programming paradigms. For example, you can use OOP in an imperative paradigm (with state) or without state. And it'd still be OOP, no matter if you use C++, Java, Forth, Haskell or any Lisp.

> **Can+~ said:**
> 
I'm not entirely convinced by the argument of nvteighen either.

If I code (with a lot of free time) a program that could create a list which can hold operations and data like a Scheme clone, and use it on my C code, like [FONT="Courier New"]run_operation(list)[/FONT], can I consider that I just build the Functional Paradigm on my code? Or it doesn't count as I'm creating a new abstraction layer?

In my opinion, what you would have done there is an abstraction layer that now allows you to use functional programming. That's exactly what happens in any Scheme implementation written in C, for example. Not because it was written in C it means that the Scheme interpreter will not be functional.

But I do see some inconsistency or maybe a lack of clarity in my argument... I'll try to make it clearer (or drop it if it turns out I'm wrong); a debate will of course help me :)

---

### Post by Can+~ on 2009-07-25
> **nvteighen said:**
> In my opinion, what you would have done there is an abstraction layer that now allows you to use functional programming. That's exactly what happens in any Scheme implementation written in C, for example. Not because it was written in C it means that the Scheme interpreter will not be functional.

But then I could define your previous example as creating an abstraction layer when creating inheritance, methods. Probably I would have to change the way I code, even if I'm working on C, to do that kind of job, same as I would have to push new elements to my Scheme example.

> **nvteighen said:**
> But I do see some inconsistency or maybe a lack of clarity in my argument... I'll try to make it clearer (or drop it if it turns out I'm wrong); a debate will of course help me :)

The most crucial point is defining when we "raise the abstraction level". To my point of view, we would have to consider a paradigm once we have created a new abstraction on a language that originally didn't support it (ironically, creating one that does).

In other words, if I create my scheme list and start adding/extracting elements from it, I would have to reconsider that I've created a new abstraction level where this language is a subset of operations I've created for it (not implying a new syntax).

Same with the OOP, if I have created a new system that uses structs to hold pointers to function and call it "methods", I would have to redirect my flow to this new structures and pointers.

(Edit: we should probably move this subject to *another place*)

---

### Post by nvteighen on 2009-07-26
> **Can+~ said:**
> But then I could define your previous example as creating an abstraction layer when creating inheritance, methods. Probably I would have to change the way I code, even if I'm working on C, to do that kind of job, same as I would have to push new elements to my Scheme example.

The most crucial point is defining when we "raise the abstraction level". To my point of view, we would have to consider a paradigm once we have created a new abstraction on a language that originally didn't support it (ironically, creating one that does).

In other words, if I create my scheme list and start adding/extracting elements from it, I would have to reconsider that I've created a new abstraction level where this language is a subset of operations I've created for it (not implying a new syntax).

Same with the OOP, if I have created a new system that uses structs to hold pointers to function and call it "methods", I would have to redirect my flow to this new structures and pointers.


Now I see your point and it's a pretty good one. I'll medidate on this, as everything related to the abstraction problem interests me a lot.

So, what you seem to imply is that (Turing-complete I suppose) languages that aren't multiparadigm can get to support new paradigms by creating new abstraction layers... Seen that way, OOP in C would effectively be an abstraction layer done with a set of primitives (structs, pointers + the opaque pointer technique).

The question now is the following, IMO. What about the possibility of coexistance of OOP with imperative programming and with functional programming? That's a point that confuses me... Are paradigms exclusive or not?

> 
(Edit: we should probably move this subject to *another place*)

Why? This is one of the few times we can discuss something interesting here! And so in the future, people will refer to the "great discussion nvteighen and Can+~ had about OOP in which subtle matters like the difference of abstraction and model constraints had been touched" :)

(If you mean splitting the thread, I agree)

---

### Post by CptPicard on 2009-07-26
Hmmh... interesting question here. I am not sure I am willing to start defining the differences between design/programming paradigms too strictly in particular so that I could exclusively assign OOP to one or the other. These things are lines drawn in water not least because in the end you can always hack up enough code to emulate whatever.

Object-orientedness is a feature that shows up in a lot of languages in various incarnations -- more often than not you are working with some abstract "things" in your language, and that can be seen as an object.

On the other hand, a reasonable argument can be made (IMO) that the most explicitly object-oriented languages really do try to make the entire view of computation to consist of objects. This is where  you could reasonably call OOP a "programming paradigm".

I would be inclined to reserve the "paradigm" label to the major branches of formalizing computable processes though... the distinction is really the most obvious if one considers for example declarative logic-programming like in Prolog, or pure-functional programming, or "sequential commands manipulating state that are grouped into blocks" imperative programming. All of these really require much more implementation in emulation as we're talking about a different take to the entire "big picture"...

---

### Post by Can+~ on 2009-07-26
> **nvteighen said:**
> Why? This is one of the few times we can discuss something interesting here! And so in the future, people will refer to the "great discussion nvteighen and Can+~ had about OOP in which subtle matters like the difference of abstraction and model constraints had been touched" :)

(If you mean splitting the thread, I agree)

Yeah splitting. I mean, the thread was about "I don't know how to get my mind on OO" and we changed to "is OO a paradigm or a design pattern?" and now it's going "How to distinguish a new Abstraction?".

> **nvteighen said:**
> The question now is the following, IMO. What about the possibility of coexistance of OOP with imperative programming and with functional programming? That's a point that confuses me... Are paradigms exclusive or not?

I don't see why a Paradigm can't coexist with another.

Fun thing is that I've been trying to explain why, but I'm in a mental block right now. Will do some research.

*edit: Maybe they don't "coexist" but can be nested; for example, a function could be described as an object (in fact, CptPicard proved this on Python another time).

This nesting behaviour could explain why my previous example of C worked, I'm not creating another available paradigm right next to the one I was already using, but describing a new one to be used "inside" the previous.

---

### Post by slavik on 2009-07-26
> **mvalviar said:**
> Hi,

I'm programming with php. I know the how to code php including the oop syntax but is still do procedural programming. I've read books on OOP but I still can't use it.

I know how to use classes from libraries. But that's just about it. I don't know when I should extend them or when to use interfaces and abstract classes.

Lets say I want to make a blogging web app. How do I start? I can't 'envision' the objects that I will use. 

Whenever I try to start a small exercise that is object oriented I can't code it.
there are a few ways of doing this:

posts are objects, so are comments, etc.
there is one object that takes these and stores them in DB (or retrieves them) or each object could have a method to store/retrieve from DB (implementing an interface).

posts could also contain the comments.

then you have a page object that contains the footer object, the header object, other "widget" objects and a post object (and either post object contains the comments, or the page contains the comments).

Hope I gave you some ideas there.

---

### Post by nvteighen on 2009-07-27
> **Can+~ said:**
> 
I don't see why a Paradigm can't coexist with another.

Fun thing is that I've been trying to explain why, but I'm in a mental block right now. Will do some research.

I'm in mental block too... :p

> 
*edit: Maybe they don't "coexist" but can be nested; for example, a function could be described as an object (in fact, CptPicard proved this on Python another time).

This nesting behaviour could explain why my previous example of C worked, I'm not creating another available paradigm right next to the one I was already using, but describing a new one to be used "inside" the previous.

Yup... I sorta see a problem on the whole thing... but again, my mind is blocked and I'm not sure...

---

### Post by issih on 2009-07-27
In response to nvteighen and Can+'s meta thread...

In essence, any programming language, even brain**** can be used to implement any process/program/feature that you want.

To that end, all languages above assembly are nothing more than abstractions. Those abstractions are made in order to help us humans in some way...either in terms of readability, usability, eas of reuse, compactness of source code, whatever.

Therefore, every design paradigm is a nothing more than an abstraction, and every langauge we use is actually written within another (via an interpretter or a compiler) and this goes all the way down until you end up back at machine code.

There is no distinction between the paradigm and the abstraction to my mind, they are the same thing. The only thing that makes it a paradigm is that enough people get a bee in their bonnet about it.

---

### Post by CptPicard on 2009-07-27
Hmm, that one in turn sounds like the "it's just library calls" argument. Anything can be interpreted in terms of anything else, but I get this feeling that it confuses the entire picture a bit too much... what is discussed becomes meaningless, and I don't think it is. 

I mean there is certainly a *reason why* programming is looked at differently in different languages. And what constitutes a "paradigm" here has to do with the most profound underlying ideas of the languages; we can't just brush them off as just different layers on top of machine code.

As a theoretical example, consider the equivalent, yet different, "paradigms" of computation on the theory side -- lambda calculus and the Turing machine. Both can simulate the other, but their formalisms are completely different. Likewise, consider the difference between imperativeness and declarativeness; functional-programming and logic-programming... you will build abstractions in terms of them, but the "paradigm" side of the language really permeates everything you do in those languages. You might say that it is the all-encompassing foundation for the abstractions used, if you will...

---

### Post by mvalviar on 2009-07-27
Thanks for the discussion. I'm no expert but IMHO object oriented programming is a programming paradigm which is of course easy to write in oo programming language like Java. 

By the way I've been watching the Stanford lectures. Excellent material. I hope a few weeks I can look back to this thread and say "I can do OPP".

---

### Post by Copernicus1234 on 2009-07-27
I would recommend reading a book about Design Patterns since a lot of books also describes situations where they are useful. It should make it easier for you to know when you want to extend classes and so on.

But honestly, I also think its a problem, specially in large programs. I often find myself refactoring the code constantly because I didnt take the time to plan the entire program before starting to code. Im just not that sort of person I guess. I start coding, then the ideas of what I want to do comes to me while coding. Not before.

---

### Post by mvalviar on 2009-07-27
> **Copernicus1234 said:**
> I would recommend reading a book about Design Patterns since a lot of books also describes situations where they are useful. It should make it easier for you to know when you want to extend classes and so on.

But honestly, I also think its a problem, specially in large programs. I often find myself refactoring the code constantly because I didnt take the time to plan the entire program before starting to code. Im just not that sort of person I guess. I start coding, then the ideas of what I want to do comes to me while coding. Not before.

Bingo! Since I'm only coding because I want to I don't have any predefined goals. Often I code before decide on what functionalities my program will have.

---

### Post by CptPicard on 2009-07-27
> **Copernicus1234 said:**
> 
But honestly, I also think its a problem, specially in large programs.

I have always felt like a lot of design patterns are outright symptomatic... they tell you "how to get around issues you get stuck on having to do things the rigid static-typed OOP way". It's a collection of dark art invocations... in particular I find it very typical that a beginner is stuck not being able to do *anything* because they have not yet coded enough to know what kind of objects to create where (I was like that 10 years ago..)


> I often find myself refactoring the code constantly because I didnt take the time to plan the entire program before starting to code.

Exploratory programming is the really educational kind of programming, and rigid OOP slows it down. I find it somewhat unlikely that a hobbyist hacker would draw up UML diagrams in advance. :)

At least in the case of Java you have good IDEs that make common refactorings fast and relatively easy... my Java coding actually gained surprising fluidity when I started coding-by-refactoring, just slapping something together first and then starting to crack out pieces into classes...

---

### Post by Reiger on 2009-07-27
> **CptPicard said:**
> Exploratory programming is the really educational kind of programming, and rigid OOP slows it down. I find it somewhat unlikely that a hobbyist hacker would draw up UML diagrams in advance. :)

+1. In fact I'd go so far as to say that it is more likely for said hobbyist hacker to pick a "easy-but-no-seatbelts" language like Python, PHP or Perl and hack together a prototype; then maybe consider "doing things properly" afterwards or -more likely: finding that they already have the thing they wanted to code in <X> however written in Python/PHP/Perl.

> 
At least in the case of Java you have good IDEs that make common refactorings fast and relatively easy... my Java coding actually gained surprising fluidity when I started coding-by-refactoring, just slapping something together first and then starting to crack out pieces into classes...

:P

---

### Post by issih on 2009-07-27
Personally I tend to recode at least once if not twice. The first pass is quick and dirty and exposes what works where, then refactor things into something that actually resembles a well coded system. Occasionally I will then realise I've approached it all wrong and completely rewrite it.

I'd argue that that has nothing to do with the coding style used though...its just about how much of a perfectionist you are. Do you stop when it works, or when its right?

An OO program is no more functional than a procedural one, its about how easily it can be repurposed. Thats what defines a good OO programmer, do the objects actually do something useful in a way that is easily extended?

I agree wholeheartedly that the only way to really get a feel for these things is to start coding and see where you end up. Architecting things in the abstract only ever goes so far, you need to get your hands dirty to find where the little subtleties that always crop up are.

---

