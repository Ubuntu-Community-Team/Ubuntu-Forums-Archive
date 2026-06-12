---
title: "Getting serious about programming: Recommendations?"
date: 2005-07-21
forum: Programming Talk
---

### Post by darkmatter on 2005-07-21
Hi all.

After having dabbled in programming/hacking for some time (most of the time I had was allocated to other needs), I now find myself able to afford the time to pursue one of my lifelong passions to the fullest.

So now I need some real advice. Where should I start? (my current status: I have some minor experience with Python, C/C++, XML, HTML) What IDE's do you recommend (must be easy on the eyes, as I plan to spend long hours at the keyboard)? Libraries, etc?

My interest is primarily directed towards development/streamlining/modularization of applications/libraries for GNOME and GNU/Linux in general, with the hope of eventually being able to give back to the community.

Any recommendations for serious study would be most appreciated.

---

### Post by doclivingston on 2005-07-21
[QUOTE=darkmatter]So now I need some real advice. Where should I start? (my current status: I have some minor experience with Python, C/C++, XML, HTML) What IDE's do you recommend (must be easy on the eyes, as I plan to spend long hours at the keyboard)? Libraries, etc?[/quote]

The best place to start depends on what you want to do - try to think of something that will interest you, and go from there.

A good way to start would be to find an project (application, etc) that you have an interest in, and wouldn't mind working to improve. Next ask the developers on the mailing list (or IRC, if it has a channel) if there are any "low hanging fruit" - which are things they think shouldn't be too hard  for someone unfamiliar with the code of the project to work on, which will let you gain an understanding of how the application is written. If you're serious about helping, most developers are only too happy to help you get started and give you pointers on how to go about things.

> My interest is primarily directed towards development/streamlining/modularization of applications/libraries for GNOME and GNU/Linux in general, with the hope of eventually being able to give back to the community.

Particular to Gnome a couple of pages that might interest you:
General helping out with gnome - [http://live.gnome.org/JoinGnome](http://live.gnome.org/JoinGnome)
"Gnome Love" - [http://live.gnome.org/GnomeLove](http://live.gnome.org/GnomeLove)
"Gnome Love" bugs (some low hanging fruit) - [http://bugzilla.gnome.org/reports/keyword-search.cgi?keyword=gnome-love](http://bugzilla.gnome.org/reports/keyword-search.cgi?keyword=gnome-love)
How to start developing for Gnome - [http://live.gnome.org/GnomeLove/HowToStart/](http://live.gnome.org/GnomeLove/HowToStart/)

---

### Post by darkmatter on 2005-07-21
Thanks for those links, they should come in very useful.

As for what I want to do. My current idea was to start small (example: maybe help bring the GNOME-games up to standard with the rest of the UI-graphical selection of cards, etc. thumnails and short descriptions of the different games in a selection dialog -and thats just the general UI), thewn move on to bigger challenges such as integrating the existing media apps (modularization) into a more streamlined 'media center' so to speak. My main interests have always been Interface design/usability (from mundane enhancements all the way to full blown window management).

---

### Post by LordHunter317 on 2005-07-21
While it sounds like you want to dive right into application writing, if you want to learn the true fundamentals of programming, I recommend you start with a book like *Structure and Intepretation of Computer Programs*, available free online.  

Also, taking a class at a local college couldn't hurt.   Having a good foundation is important to write good programs.  There's more to programming than just knowing the syntax and semantics of a language.

---

### Post by darkmatter on 2005-07-21
Just googled it. Looks like a rather good read. I've been looking into taking some courses again, just have to wait for them to start up. You guys are just a wellspring of useful information :)

---

### Post by Natja on 2005-07-21
[QUOTE=darkmatter]Hi all.

 What IDE's do you recommend (must be easy on the eyes, as I plan to spend long hours at the keyboard)? 
[/QUOTE]

Hi,

I think Anjuta is a good choice, particularly if you want to develop gnome applications ;)

---

### Post by jerome bettis on 2005-07-21
i'd recommend you get very good with the command line and a nice editor right away instead of using an ide.  just something you might want to look into.

i also agree with lord hunter, take a some classes so you know what's actually going on instead of just writing code.  learn how the architecture, compiler, operating system that you're using effect your program and you'll write better code.

i recommend you check out the book object oriented software construction by bertrand meyer as well.  those two books will give you a very very good grounding and you'll be much better off than 80% of the idiot CS majors i have to put up with from the very start.

---

### Post by Abd-al-Karim on 2005-07-24
Hi I am in a similar sitituation as dark matter and also want to get more serious about my programming and go beyond my current capabilities. However I want to find out more about hardware & assembly language because it seems, to me at least, that I lack a lot of knowledge in this area.

I want to find out more about CPU's, ISA's and how high level programming functions become assembly language. I was wondering if anyone knew a good book or site on the subject, I've been told that the Intel 32bit Architecture is a good place to start but I do want to move on to other architectures in the future. Any advice is appreciated and thanks a lot in advance.

---

### Post by Gsibbery on 2005-07-24
[QUOTE=Abd-al-Karim]Hi I am in a similar sitituation as dark matter and also want to get more serious about my programming and go beyond my current capabilities. However I want to find out more about hardware & assembly language because it seems, to me at least, that I lack a lot of knowledge in this area.

I want to find out more about CPU's, ISA's and how high level programming functions become assembly language. I was wondering if anyone knew a good book or site on the subject, I've been told that the Intel 32bit Architecture is a good place to start but I do want to move on to other architectures in the future. Any advice is appreciated and thanks a lot in advance.[/QUOTE]

This is one of the better books on assembly under Linux: 
[http://savannah.nongnu.org/download/pgubook/](http://savannah.nongnu.org/download/pgubook/)

It uses AT&T syntax. Your as aseembler should work just fine. 

Paul Carter has a book that uses Intel syntax:
[http://www.drpaulcarter.com/pcasm/](http://www.drpaulcarter.com/pcasm/)

Get nasm to compile these examples.

---

### Post by LordHunter317 on 2005-07-24
Learning assembly on x86 is generally an exercise in pain, because IA-32 assembly is crap.

Most schools teach assembly / machine-language on just about any other processor, because it's so much eaiser.

And if you want to learn about hardware, there are better ways to do it than learning assembly.  I'm not knocking the value of knowing assembly, but rather, I'm not sure it's the best way to learn want to learn.

---

### Post by Gsibbery on 2005-07-24
[QUOTE=LordHunter317]Learning assembly on x86 is generally an exercise in pain, because IA-32 assembly is crap.

Most schools teach assembly / machine-language on just about any other processor, because it's so much eaiser.

And if you want to learn about hardware, there are better ways to do it than learning assembly. I'm not knocking the value of knowing assembly, but rather, I'm not sure it's the best way to learn want to learn.[/QUOTE]

It's not so bad once you get used to it a bit.

---

### Post by dataw0lf on 2005-07-26
[QUOTE=Gsibbery]It's not so bad once you get used to it a bit.[/QUOTE]

Alot of stuff 'isn't so bad once you get used to it'.  That doesn't make it right.

Learning asm as a first language is probably some of the worst advice I've ever heard.    I'm not saying learning assembly is a bad idea altogether;  however, starting with a higher level language, learning it's intricacies and semantics, and THEN dissecting the assembly code it generates would probably be a much easier, and better in the long run, plan.

Personally, I'd advise learning C as a first language.  You'll become intimate with memory management and basic data types and structures, whilst still being able to maintain a grip on your sanity.  Then, if you want to learn an assembly language, you'll have a much easier time doing so.

---

### Post by LordHunter317 on 2005-07-26
[QUOTE=dataw0lf]Personally, I'd advise learning C as a first language.[/quote]C is a terrible first language, much for the same reasons that any assembly is a terrible language.

However, if you're suggesting learning C on the path to learning assembly, that's not a terrible idea.  Learning assembly is much eaiser with C background, generally, as you're used to doing things you must do in assembly.

Another path is the High-Level Assembly book, which takes the same path essentially as above but wraps the syntax into one slightly more complicated, but brillant, language.

---

### Post by dataw0lf on 2005-07-26
[QUOTE=LordHunter317]C is a terrible first language, much for the same reasons that any assembly is a terrible language.
[/QUOTE]

I think you're wrong.  C is a great language as a base;  it's a good compromise betwixt the arcane magic of assembly and the hold-your-hand-and-explain-nothing-to-you of most interpreted and/or higher level languages.  Starting with C, you'll have a fundamental grasp of memory management and other 'behind the scenes' operations in programming.  You won't be held back by enforced paradigms (Java, C#) or weak, dynamic typing (which I think is a horrible way for someone to start).  
If I was to advise a language other than C as a first language, I'd probably have to say Python, but that's just because it's 1) incredibly easy to learn, 2) has strong typing, 3) it's elegant, 4) and it doesn't protect you _too_ much.

I'm curious as to what language you'd advise for a beginner.

---

### Post by LordHunter317 on 2005-07-26
> **dataw0lf]C is a great language as a base said:**
> The problem is, most of those skills aren't useful.

> Starting with C, you'll have a fundamental grasp of memory management and other 'behind the scenes' operations in programming.And the majority of the languages don't require you to manage memory at all, or only in certain situations.

So the value of learning classical C-style memory managment is very questionable in the modern world for a new progammer.

C also required you to write code to tasks that nearly every other language (including C++) does for.  And it's all tedious code, especially for a beginner: the return on the code they write is rather low, because you spend all day having to be careful to not leak memory and handle strings correctly instead of learning more important, fundamental concepts like data structures and algorithms, which can be taught in any language.  And should be taught in a language that has features so the primary focus of the code can be the data structures and their behaviors, not allocating memory for them and deallocating them.

[quote]I'm curious as to what language you'd advise for a beginner.I don't, generally.  Many schools agree with me and don't teach a language at all in the beginning semesters of their CS or software engineering curiculums.  SCIP for example, uses Scheme to teach it's examples, but it's not a book about Scheme at all.  If you wanted to be a good Scheme programmer, you'd have to read a Scheme book.

Most of the really fundamental concepts of programming are language independent.  So, they should be taught in whatever language minimizes the amount of work necessary to teach them.  That's not C.  That's not C++.  It's not really Java or C# for most things, due to the type casting issues.  Scheme is a fine choice.  Ruby or Python would be fine choices, mostly due to the fact they have automatic memory mangement and duck typing, and a wealth of existing libraries so that beginning programmers can create useful or cool applications to them after learning the fundamental precepts.

---

### Post by dataw0lf on 2005-07-26
> **LordHunter317]The problem is, most of those skills aren't useful.
[/QUOTE]

Useful? Perhaps not.  Fundamental to understanding programming and exactly what you're doing? Hell yes.

> 
C also required you to write code to tasks that nearly every other language (including C++) does for.  And it's all tedious code, especially for a beginner: the return on the code they write is rather low, because you spend all day having to be careful to not leak memory and handle strings correctly instead of learning more important, fundamental concepts like data structures and algorithms, which can be taught in any language.  And should be taught in a language that has features so the primary focus of the code can be the data structures and their behaviors, not allocating memory for them and deallocating them.


A valid point.  I don't really have an argument for this said:**
> 
Most of the really fundamental concepts of programming are language independent.  So, they should be taught in whatever language minimizes the amount of work necessary to teach them. 


Obviously, I agree that most programming concepts are language independent.  However, the ability to grasp the 'really fundamental concepts of programming' is language independent as well, largely so, anyways.  

If you want to be a great programmer, imho you're going to have to tackle low level topics eventually.  And why not start out with a strong base, rather than working your way from the top?

---

### Post by LordHunter317 on 2005-07-26
> **dataw0lf] Fundamental to understanding programming and exactly what you're doing?[/quote]Not really, no.

Understanding how to properly allocate and deallocate *resources* is an essential concept in programming said:**
>  And why not start out with a strong base,Because the features you're suggesting aren't part of a programming base.  Like it or not: memory management isn't a base skill of a programmer.  We moved passed that eons ago.

Resource managment is.  But I can learn that in any language, and learn the concepts and implementations of resource management in languages that make it much eaiser than C. 

And even if I agreed memory management was that fundamental, the other flaws of C make learning it as a starting language still very debatable still.

---

### Post by dataw0lf on 2005-07-26
> **LordHunter317]
You're confusing two issues, I think.  Memory management isn't a fundamental concept in programmer anymore. 

Because the features you're suggesting aren't part of a programming base.  Like it or not: memory management isn't a base skill of a programmer.  We moved passed that eons ago.
[/QUOTE]

*(**Disclaimer**: use of male pronouns to follow, if you're offended *shrug* I'm a man)*
I didn't confuse anything.  I'm talking about a programmer understanding what's happening behind his application that he's writing.  Whether or not a language abstracts this for him, I think it's wise that he knows and understands what's going on at that level. Is it necessary? No.  You can be a half decent code monkey without knowing alot of stuff.  I'm not arguing that a programmer can't get by or will fail to succeed without this knowledge said:**
> 
And even if I agreed memory management was that fundamental, the other flaws of C make learning it as a starting language still very debatable still.


That it's _hard_?  That's not an argument at all.  Suck it up, troop.

---

### Post by LordHunter317 on 2005-07-26
> **dataw0lf]I'm talking about a programmer understanding what's happening behind his application that he's writing.[/quote]Why should he care, unless it impacts his application in a negative way?

The entire point of modern programming paragdims like object-oriented programming is abstraction of such details: your code only cares about the promises it needs to operate and doesn't care at all about **how** those promises are met, only that they are **met**.

> Whether or not a language abstracts this for him, I think it's wise that he knows and understands what's going on at that level.That may be true at some point,  but you need to show it's necessary at the **introductory level**.  Which I don't believe you really think it is.  

[quote] I'm not arguing that a programmer can't get by or will fail to succeed without this knowledge said:**
> Wonderful.  That doesn't mean they need to learn it right away.  Beginning programmers aren't taught how to create templates/generic code right away either, but certainly a programmer who knows how to write a class that uses a template instead of a fixed type is more useful than one who does not.  That doesn't mean CS101 or even 103 or even 2xx should teach generic programming.

Progammers who've taken a compilers course are useful, because they get a thorough understanding of parsing, and the difference between syntax and semantics as it relates to a language.  Yet compilers, compiler theory, or even the globally applicable portions of compilers (e.g., parsing) aren't taught at anywhere near an introductory level.

[quote]That it's _hard_?  That's not an argument at all.  Suck it up, troop.Not only is it hard, it's difficuilt and error prone.  Most of the errors in C code, including those that create most of the security vulnerabilities in C code, come from two classes: mismanagement of memory, and mishandling of strings.

So it makes a lot of sense to not teach C as a beginning language, give the fact that it requries you to do both of those tasks, and even those programmers who are experts at C make frequent mistakes performing those two tasks.

---

### Post by dataw0lf on 2005-07-26
> **LordHunter317]
The entire point of modern programming paragdims like object-oriented programming is abstraction of such details: your code only cares about the promises it needs to operate and doesn't care at all about **how** those promises are met, only that they are **met**.
[/QUOTE]

Which is another argument entirely, and one that I don't agree with (advocacy of incredible amounts of abstraction and encapsulation).One of the main reasons I recommend the C language is because it DOES remove that abstraction and encapsulation said:**
> 
That may be true at some point,  but you need to show it's necessary at the **introductory level**.  Which I don't believe you really think it is.  


I'm not arguing that you'll need such information at an introductory level.  I already stated that I was against working from top to bottom, no?  

> 
Progammers who've taken a compilers course are useful, because they get a thorough understanding of parsing, and the difference between syntax and semantics as it relates to a language.  Yet compilers, compiler theory, or even the globally applicable portions of compilers (e.g., parsing) aren't taught at anywhere near an introductory level.


Agreed, that's why C, as I've stated before, is a compromise solution. 

> 
Not only is it hard, it's difficuilt and error prone.  Most of the errors in C code, including those that create most of the security vulnerabilities in C code, come from two classes: mismanagement of memory, and mishandling of strings.


Learning C is frustrating, yes (and dealing with C after 'knowing' it for 10 years, well, it can be even more frustrating ;) ).  However, I don't see it being 'difficult' or 'error prone' as necessarily a bad thing for beginning programmers.  I'm sorry, but I think that a baptism through fire can be extremely healthy for one starting out.   I've already stated that the easiest road isn't always the best, no?  

Personally, I think after tackling the numerous errors C likes to throw you (and yes, they can be frustrating and depressing at times), you'll grow to 1) appreciate the higher level languages more 2) and, as I've already stated time and again, you'll have a better grasp of programming.  Whether it's debugging, an understanding of lower level functionality, or just plain love for X interpreted language, in the end, I think it's worth it.

---

### Post by LordHunter317 on 2005-07-26
> **dataw0lf]Which is another argument entirely, and one that I don't agree with (advocacy of incredible amounts of abstraction and encapsulation).[/quote]You're in the general minority said:**
>  This is the 'hacker' mentality;  you don't just want to know that something _does_ work, you want to know how and why it works, and you're better off in the long run for taking the time to do so.But you haven't shown you actually will be better for taking the time to do so, **especially** at the introductory level.

Consider this: if every other language I'll program in doesn't require me to do memory managment, why should I go out of my way to learn it?

It's the same as suggesting everyone who drives standard must learn to heel-toe shift.  Are the drivers who can heel-toe shift better drivers?  By and large, yes.  But is it a commonly used or needed skill?  No.

Remember, if it isn't about learning it off the bat, it's not germane to the argument, so please don't introduce it.  

> However, if you want to be working professionally in a month doing code monkey, cookie-cutter work for 30 bucks an hour, then by all means go and learn X high level language.I don't do cookie-cutter work generally and C is the last language I use.
  
> I'm not arguing that you'll need such information at an introductory level.Then your suggestion of C as a starting language is a poor one, if the things it teaches you **beyond** other languages aren't necessary when you're  first starting to program, no?

I don't care if learning memory mangement is helpful eventually.  I don't want to disucss that.  I'm only interested in you trying to support your position that C is a good starting language.

And you've already conceded that the added things C makes you teach aren't necessary to learn up-front, so you've already conceded a lot of ground, I think.

> Agreed, that's why C, as I've stated before, is a compromise solution. But that doesn't make a good **starting** solution.

>  However, I don't see it being 'difficult' or 'error prone' as necessarily a bad thing for beginning programmers.The wash of security vulnerabilties out there in C code tend to disagree with you.  And like I said, they're all generally of the same types: string-handling issues, or memory-mangement issues.

It's hard to say C memory mangement and strings aren't tedious and error prone when the number of mistakes committed in those arenas are so utterly common.  

> and, as I've already stated time and again, you'll have a better grasp of programming.**You haven't actually provided substantiated proof of this**.  And you've agreed that the most fundamental concepts of programming can be taught in **any** language, so you need to show what C has that makes it better than those other languages.  And you've already conceded that C's core differences don't make it any better.

> in the end, I think it's worth it.While it may be worth it in the end, it's not worth in the beginning, or if it is, you haven't demonstrated how it is.

---

### Post by dataw0lf on 2005-07-26
> Remember, if it isn't about learning it off the bat, it's not germane to the argument, so please don't introduce it.  
  

You're quoting business practices, and, while applicable to consulting or working in general, I don't see how that's about learning it off the bat.  So please don't introduce it.

> 
I don't do cookie-cutter work generally and C is the last language I use.


I certainly am not saying that other languages are for cookie-cutter work.  However, your philosophy seems to be 'get the programmer out the door as quickly as possible and into the workforce' which seems to be a rather poor way to approach learning how to program, or anything in general for that matter.

> 
I don't care if learning memory mangement is helpful eventually.  I don't want to disucss that.  I'm only interested in you trying to support your position that C is a good starting language.


And such shortsightedness seems to be your argument's major weakness.  I'm not talking about what 1) will be most productive 2) is most applicable in a business sense 3) what's easier.  Perhaps you forgot who originally posted.  To refresh, it was darkmatter, and he was hoping to pursue 'his lifelong passion to the fullest' and was looking for 'serious advice'.  Unless I missed some hidden meaning in his words, he wasn't looking for the quickest way to make a buck.

> 
And you've already conceded that the added things C makes you teach aren't necessary to learn up-front, so you've already conceded a lot of ground, I think.


Again, your shortsightedness coming around.  I never argued (as you pointed out) that C was a great solution as a quick way to learn programming.  However, I was arguing that C is a good language to pick up first for someone who's in love with programming and wants to explore everything involved (see darkmatter's first post, again, if you haven't read it). 

> 
**You haven't actually provided substantiated proof of this**.  And you've agreed that the most fundamental concepts of programming can be taught in **any** language, so you need to show what C has that makes it better than those other languages.  And you've already conceded that C's core differences don't make it any better.


I can't believe I have to keep repeating myself.  Here's my 'arguments' (when you look closer, you can see alot of 'this is what I believe' or 'my opinion': 

1) C will provide you with an indepth knowledge of lower level functionality, thus understanding what is going on behind the scenes or otherwise.  

2) I believe that number one is important for any programmer who takes himself seriously or has a 'love of programming'.  Again, see darkmatter's first post.  You've already conceded this.

3) It's my opinion that it's better to learn such things from the ground up, rather than from the top down.

4) C has your basic programming concepts, and, in fact, many programming languages derive their own syntax from C.  

5) Yes, C is hard and difficult to deal with.

Every time I've argued this it's been 'my opinion'.  From 'my experience'.  As an accomplished programmer, this is what I believe the best approach is.   Take particular note of #3.  Read it again if you have to.  Possibly multiple times, if it doesn't sink in right away (hasn't yet).  Then go to #2.  Rinse.  Repeat.  Don't hit reply until you do.  Thanks.

---

### Post by LordHunter317 on 2005-07-26
> **dataw0lf]  However, your philosophy seems to be 'get the programmer out the door as quickly as possible and into the workforce'[/quote]No, it isn't. If it were, I'd be suggesting they learn C# or Java, which you'll note I didn't do.

My philosophy is to teach the new progammer the most fundamental skills they need to know, using whatever method and language makes that the eaisest for them to learn those skills.

> And such shortsightedness seems to be your argument's major weakness.The only shortsightedness is on your behalf. You're assuming I'm making a case I haven't even suggested.


>  I'm not talking about what 1) will be most productive 2) is most applicable in a business sense 3) what's easier.Yet, all of those factors have some weight when determining what language to teach a programmer initially.  In fact, one of those factors is probably the sole reason Java is commonly taught as a introductory language.  So you can't ignore those factors said:**
>  Perhaps you forgot who originally posted.  To refresh, it was darkmatter, and he was hoping to pursue 'his lifelong passion to the fullest' and was looking for 'serious advice'.And this is relevant to your suggestion of learning C first how, or my counter to that suggestion?

> Unless I missed some hidden meaning in his words, he wasn't looking for the quickest way to make a buck.And you'll note I never suggested a method to put him on that path.  I wouldn't have suggested *Structure and Interpretation of Computer Programs* in that case.

> However, I was arguing that C is a good language to pick up first for someone who's in love with programming and wants to explore everything involvedAnd when challenged on it, failed to provide reasonable support for your view.

> 1) C will provide you with an indepth knowledge of lower level functionality, thus understanding what is going on behind the scenes or otherwise.  And you haven't show the value of learning this **at the beginning**.

> You've already conceded this.No, I haven't.  I've conceded that it can be important to know, but I haven't coneceded the fact it's important to know initally.

> 3) It's my opinion that it's better to learn such things from the ground up, rather than from the top down.I'm not sure what you mean ground up versus top down here.  Fundamental things like resource mangement and data structures and algorithms don't have a top down versus group-up methodology to them.  A linked list is a linked list whether you write it in C, Scheme, or plain English.

> 4) C has your basic programming concepts,And lacks many concepts that may other common-place languages have today, as part of the standard.  This includes things like closures, OOP w/ inheritence, exceptions, references, anonymous contexts, safe string-handling, and a host of other things. 

> and, in fact, many programming languages derive their own syntax from C.  Wonderful.  Syntax is largely irrelvant.

> Take particular note of #3.I'm still not sure what you mean.  If you mean, it's important to learn manual memory mangement before using a garbage-collected language, you're simply being silly and missing the entire point of a host of programming techniques and ideals.

If manual memory management was as important as you suggest, then why don't all languages support it?  The very fact that most languages in common use today don't suggests that it's not really important at all.  Your support for your argument just isn't coherent with reality, I'm afraid.

Or that it's important to know how to handle a string as an character array before using the type-safe versions, it's the same.  You don't gain any useful or helpful knowledge from this, and all it does is increase the initial difficulty of learning.  

> Possibly multiple times, if it doesn't sink in right away (hasn't yet).Funny coming from someone who doesn't even understand my position.

---

### Post by dataw0lf on 2005-07-26
You're taking alot of time away from my DefCon planning.  Let's wrap this up.

> **LordHunter317]No, it isn't. If it were, I'd be suggesting they learn C# or Java, which you'll note I didn't do.
[/QUOTE]

Thank God.

> 
My philosophy is to teach the new progammer the most fundamental skills they need to know, using whatever method and language makes that the eaisest for them to learn those skills.
 

And I don't agree that 'eaisest' == 'better'.  

> 
And when challenged on it, failed to provide reasonable support for your view.


> 
And you haven't show the value of learning this **at the beginning**.


*sigh* Ok, here I go.  
I assume you'll admit that _all_ applications have to deal with memory.  Whether it's hidden from the programmer or not is irrelevant.  There can (and will) be memory leaks in languages such as, say, Python.  For example, if you leave a reference to some gigantic data structure in Python hanging around, and it isn't freed, someone new to programming who doesn't even know what memory management is will have no idea what's going on.  However, if they've approached C programming FROM THE GROUND UP, i.e. the concept of pointers and memory allocation, then they'll have a firmer grasp on what's going and will be able to 1) grasp the concept and problem significantly better and 2) be able to fix the problem easier.  Memory problems and leaks are not a lone C thing said:**
> 
If manual memory management was as important as you suggest, then why don't all languages support it?  The very fact that most languages in common use today don't suggests that it's not really important at all.  Your support for your argument just isn't coherent with reality, I'm afraid.


The whole point was to take the load off experienced programmers from the beginning.  And see above for memory management.  YOU WILL HAVE TO DEAL WITH IT SOONER OR LATER.  Don't try to fool anyone into thinking otherwise.

> 
Funny coming from someone who doesn't even understand my position.


Don't misrepresent it then.

---

### Post by LordHunter317 on 2005-07-26
> **dataw0lf]And I don't agree that 'eaisest' == 'better'.[/quote]And that's simply silly.  Would you suggest I teach you Calculus only using proofs, because the proofs are what logically define calculus?  No, it'd be too difficult for anyone to follow. and would get in the way of understand both theory and the applications of calculus.

The same is true with programming: when you start out, you want to remove as many distractions as possible from learning the things that are truly important: the differences between data and code, resource management, encapsulation, etc.

> I assume you'll admit that _all_ applications have to deal with memory.  Whether it's hidden from the programmer or not is irrelevant.But if I, as the programmer don't have to deal with it, then it isn't really relevant is it?  Because it's solidly out of my control. 

>  someone new to programming who doesn't even know what memory management is will have no idea what's going on.That's simply not true.

Memory mangement is a form of resource management.  Someone who's been taught to properly manage resources in generic terms will understand the concept of a memory leak even if they're never taught memory mangement.  Because leaking memory is no different from leaking file descriptors, or database handles, or any other scarce resource.

>  However, if they've approached C programming FROM THE GROUND UP, i.e. the concept of pointers and memory allocation, then they'll have a firmer grasp on what's going and will be able to 1) grasp the concept and problem significantly better and 2) be able to fix the problem easier.Perhaps, but what you have to show is the programmer would be incapable of doing this without learning C first.  And I believe any programmer properly trained in resource mangement would be able to correct the bug.  Because it's not any different from leaking any other kind of resource.

> And this is my whole argument said:**
> But not in the context you suggest.  Claiming learning memory mangement is important because you might one day work with a leaking application in any language is silly.

Especially when considering that in language like C# or Java, a leak is either a honest-to-god bug in the underlying language/API, meaning, you can't fix it, just work around it; or a result of using native code, meaning you'd have to know the native language anyway.

[quote]Why not approach it at the beginning, when your mind is fresh and hasn't been corrupted by various programming ideologies.Because they don't corrupt a thing, if properly taught.

[quote] Why wait until you're sitting there pulling your hair out over a problem? Because the problems you're suggesting they worry over just aren't very common in languages other than C?

Yes, memory leaks can occur in languages that provide for memory mangement.  But they're not very common things either, and thus not worth learning about at the beginning.

> The whole point was to take the load off experienced programmers from the beginning.What? No.  Complete, total, and utter non-sequitur.

> And see above for memory management.  YOU WILL HAVE TO DEAL WITH IT SOONER OR LATER.**And that fact, *no matter how true* isn't sufficent reasoning to suggesting learning manual memory mangement *from the beginning***.

The things you should learn from the beginning are things you will truly have to do everywhere.  This includes things like algorithms, data structures, seperation of code and data, and generic resource mangement.  It doesn't include things like learning how to write a string library using language primatives, or learning C-style memory mangement to debug a leak that will occur in some applicaton, "SOONER OR LATER," *especially* if the languages you are using make such leaks rather difficult or not the fault of the programmer in the first place.

> Don't misrepresent it then.Show me where I did anything of the sort.

---

### Post by dataw0lf on 2005-07-26
> 
Memory mangement is a form of resource management.  Someone who's been taught to properly manage resources in generic terms will understand the concept of a memory leak even if they're never taught memory mangement.  Because leaking memory is no different from leaking file descriptors, or database handles, or any other scarce resource.


Now you're being silly.  While resource management in general and memory managent are comparable in the broadest of terms, memory management is alot more complex, and often results in something completely unexpected.  Memory management in and of itself is an art, and, unlike dealing with file descriptors, database cursors, etc, is going on at _all_ times during the run of your application.  Terrible analogy.  Perhaps you don't understand it yourself?

> 
Perhaps, but what you have to show is the programmer would be incapable of doing this without learning C first.  And I believe any programmer properly trained in resource mangement would be able to correct the bug.  Because it's not any different from leaking any other kind of resource.


See above, and note, yet again, that I'm not claiming that C is the end all and be all of existence and/or learning.  Yes, they don't need to know C to understand such things.  ITS MY OPINION THAT LEARNING C FIRST GIVES ONE AN EASIER TO PLATFORM TO DEAL WITH SUCH THINGS.  I'm tempted to ask if English is your first language or not.

> 
But not in the context you suggest.  Claiming learning memory mangement is important because you might one day work with a leaking application in any language is silly.


My point, in fact, was that memory management is _dealt with ALL the TIME_.  It's not something chosen to be dealt with.  Again, whether you're manually dealing with it, or the language in question is dealing with it, it's something that is a fundamental aspect of an application.  Thus, IN MY VIEW, it should be fundamental knowledge.

> 
Yes, memory leaks can occur in languages that provide for memory mangement.  But they're not very common things either, and thus not worth learning about at the beginning.


*sigh* See above.

---

### Post by LordHunter317 on 2005-07-26
[QUOTE=dataw0lf]memory management is alot more complex,[/quote]Only when you move beyond allocating and deallocating it, into things like strategies for allocation and the like.  But the same is true when dealing with other resources in specalized terms.

>  Memory management in and of itself is an art, and, unlike dealing with file descriptors, database cursors, etc, is going on at _all_ times during the run of your application.As is the use of file descriptors, database cursors, etc.  And the need to allocate and deallocate them both properly is the same.

In some languages, even the methodology for allocating and deallocating them is the same (C++, principally).

> Perhaps you don't understand it yourself?No, I understand the use of database cursors just fine.

> ITS MY OPINION THAT LEARNING C FIRST GIVES ONE AN EASIER TO PLATFORM TO DEAL WITH SUCH THINGS.**The problem is, the things C teaches you *beyond* any other choice of first language are not *commonplace tasks***.  Meaning the value of teaching them from the beginning is questionable.

Dealing with leaky applications isn't common in Java, Python (asumming you didn't shut the GC off), Ruby, LISP, VB.NET, C#, generally FORTRAN, even if you can create a leaky application.

It's only commonplace in C.

That's the part you have to show: You can show someone might use them eventually.  But you've even agreed they won't use it all the time: so why should I spend resources at the beginning studying things I won't do all the time?  High-level knowledge is perfectly appropriate in some situations.

As an EE, I don't expect the technican building my part to understand the low-level physics behind how the part works.  Frequently, I (who designed the thing) don't even need to understand or worry about all the actual physics behind the device's operation.  Quantum effects are irrelevant if I'm working with large gates, for example.

> My point, in fact, was that memory management is _dealt with ALL the TIME_.**But not in the manner C does it**.  Which is the point: if the way C does it is not commonplace, then why should I learn it?

> Again, whether you're manually dealing with it, or the language in question is dealing with it, it's something that is a fundamental aspect of an application.  Thus, IN MY VIEW, it should be fundamental knowledge.Yes, but in Java, if the GC has a bug where I release all references to an object but never collects it, what I can do about it?  Answer: nothing.   So even if it's a fundamental aspect, it's one that is beyond my control.  Even if I was the memory allocation god, I couldn't still do a thing, because the language provdies no mechanism to explictly make that memory go away.  I have ability to get around the leak, regardless of programmer skill.  Hence, whether I know how to solve the problem or not is irrelevant.

Do you see the point now: if the programmer doesn't have to handle the task, learning about how to do isn't necessarily helpful to the programmer.  If I was going to be the programmer who was going to fix the GC, yes, I'd have to have that knowledge.  But the number of programmers doing that are smaller in number than the programmers who won't be.

> *sigh* See above.Eventualities do not a good argument make.  By that reasoning, I should take out specality insurance in case I die on an airplane now, since that could happen to me sooner or later.  It completely ignores the fact that the odds of dying on an airplane are terribly low, and the fact that I *commonly* participate in activites that are far more likely to kill me than flying on an airplane.  But because it could happen sooner or later, I might as well be prepared from the start, right?

>  No need to get angry.  Deep breaths. :roll: I'm more angry about your childish treatment of my person than anything else.

---

### Post by dataw0lf on 2005-07-26
[QUOTE=LordHunter317]
It's only commonplace in C.
**But not in the manner C does it**.  Which is the point: if the way C does it is not commonplace, then why should I learn it?
[/QUOTE]

Because memory is something EVERY application deals with.  A comparison to the physics behind <x> is not a good analogy.  A better one would be a mechanic who knows the intricacies of fuel consumption, handling, and transformation to energy.  Does he NEED to know this to be a good mechanic? No.  But does it help? Yes, it does.  Does he NEED to learn it first? No, he doesn't.  But will it 1) give him a better 'flow' of the mechanics of the machine, and 2) allow him to slowly view the car as a whole, constructed of tiny, disparate operations ? Yes.  And thus a good mechanic doth make.  Doesn't necessarily _need_ to know such things, but it's good advice, regardless.

> 
 :roll: I'm more angry about your childish treatment of my person than anything else.


How did I treat you like a child? Or did I act childishly? You're the one who ended up cursing *shrug*

---

### Post by LordHunter317 on 2005-07-26
[QUOTE=dataw0lf]Because memory is something EVERY application deals with.[/quote]**Yes, but not in the *manner of C***.  Which calls into the question of learning the C way to do things.

Just like Java, C#, and Pascal have pointers (well, they're called references in Java and C#, but they have pointer semantics), yet they can't do everything pointers in C can.  You can't do pointer arithmetic in Java or C#.  So why should I learn pointer arithmetic, if other languages can't do it, and it's not commonplace?

> Doesn't necessarily _need_ to know such things, but it's good advice, [regardless.And that may be true in the context of our discussion, but the point is still the same: if I don't need to know it right away, or if it's not a commonplace or universal activity, why learn it up front?

I'm not suggesting that programmers never learn C, or never learn manual memory mangement techniques.  What I'm suggesting is that don't need to learn them from the start, so why chose a language that forces you do such things?  It doesn't make a ton of sense.

> How did I treat you like a child? Or did I act childishly?See:>  I'm tempted to ask if English is your first language or not.

---

### Post by dataw0lf on 2005-07-26
Well, I don't have time to banter back and forth when 1) neither of us is budging on our position, and 2) you are simply attacking me, not putting forth an alternative (which is what, you know, debate is about).   This seems to be common behavior with you, LordHunter317, and I suggest you watch what you're doing in the future. 

However, I'd like to leave with a small kernel of advice for the programmers who're perusing this thread:  LordHunter317 and I come from entirely different backgrounds.  He seems to advocate 'learn what you need as fast as possible', while I'm more of the 'Learn everything you can, because it always applies;  knowledge builds upon itself'.  Both work;  I tend to view my opinion as more 'hacker' and his as more, well, 'corporate'.  Yes, they're both different approaches, but one often works for some, and the other works for the rest.  

However, who of those two 'groups' is getting steadily outsourced from the U.S. right now?  

I rest my case.

:)

---

### Post by LordHunter317 on 2005-07-26
[quote=dataw0lf]This seems to be common behavior with you, LordHunter317, and I suggest you watch what you're doing in the future. [/quote]How so?  If you have an issue with my behavior w.r.t. your duties as a moderator, take it up with me in private.  Otherwise, this smacks of totalitarianism on your part, whether you intend for it to or not.  Moreover, I can't correct inappropriate behaviors if you dont' tell me what I'm doing wrong.

> He seems to advocate 'learn what you need as fast as possible',:roll: I've advocated nothing of the sort.  What I've advocated is the things you should learn at the beginning of your life as a programmer should be things that will be applicable regardless of language.  Which excludes C style memory management, among other things.

>  tend to view my opinion as more 'hacker' and his as more, well, 'corporate'. Mine is distinctly academic, not corporate.  If I wanted to suggest a corporate mindset, I would have said, learn Java and C#, because you'll need those on your resume to get a job.  Yet my argument doesn't contain that as support, nor did I suggest it to anyone in this thread (nor in this forum, to the best of my memory).

You seem bent on putting me in a position I'm simply not supporting, because it's the one most counter to yours.  My position is counter to yours on one point and one point only: the value of learning C as a starting language.  We're actually in agreement on several points, but when you make sweepingly false generalizations about my position, I'm not certain you realise that.  Which is unfortunate to say the least.

> However, who of those two 'groups' is getting steadily outsourced from the U.S. right now? Umm, both, in quite equal numbers.

---

### Post by dataw0lf on 2005-07-26
I hate having to come back.  But DefCon plans can wait.  I'm not one to let parting shots go unanswered ;)

[QUOTE=LordHunter317]How so?  If you have an issue with my behavior w.r.t. your duties as a moderator, take it up with me in private.  Otherwise, this smacks of totalitarianism on your part, whether you intend for it to or not.  Moreover, I can't correct inappropriate behaviors if you dont' tell me what I'm doing wrong.
[/QUOTE]

Sorry if it sounded this way.  It's just that your actions (and a few others) have come to the attention of moderators of late.  You're not being tracked, or examined, or whatever, it's just a few threads have been heated and you a couple others seem to always be in the center of it.  I was just giving you fair warning.  But, noted.  Should've been private.

> 
:roll: I've advocated nothing of the sort.  What I've advocated is the things you should learn at the beginning of your life as a programmer should be things that will be applicable regardless of language.  Which excludes C style memory management, among other things.

What you seem to think is that there's this generic X language out there that someone can learn without making any sacrifices toward a specific language.  I advocate mastering your first language before moving onto the next.  You might not.  DON'T ARGUE THIS POINT WITH ME.  I AM EXPRESSING AN OPINION (Like I've been doing this whole time, and this is what I warned about earlier, e.g. attacking opinions)
> 
Mine is distinctly academic, not corporate.  If I wanted to suggest a corporate mindset, I would have said, learn Java and C#, because you'll need those on your resume to get a job.  Yet my argument doesn't contain that as support, nor did I suggest it to anyone in this thread (nor in this forum, to the best of my memory).
  
1) You won't need either Java or C# on your resume to get a job

2) So, as an academic, you don't tout learning theory nor the knowledge behind something.  Right.  You distinctly made references towards 1) business and 2) learning something as quickly as possible, and learning only what you needed.  Neither sound very academia to me.
> 
You seem bent on putting me in a position I'm simply not supporting, because it's the one most counter to yours.  My position is counter to yours on one point and one point only: the value of learning C as a starting language.  We're actually in agreement on several points, but when you make sweepingly false generalizations about my position, I'm not certain you realise that.  Which is unfortunate to say the least.


I do realize we agree on certain points!  I've been trying to keep you from debating with me from #1, for chrissakes!  THERE WAS NOTHING TO DEBATE! I've said this before! It's my opinion! How many times will I have to say this? Really? Honestly? Can you stop now?  No, you'll have to come up with another response that regurgitates the same thing over again.  We get it, LordHunter.  You think C isn't a good language to begin programming with.  I do.  We both agree on various issues, memory management does help programmers, etc.  I just think they should learn it early.  Do... you... finally... understand... my... point?  My... opinion.   It's like trying to drill through a steel wall here!

> 
Umm, both, in quite equal numbers.


Got a reference for that?

---

### Post by LordHunter317 on 2005-07-26
[QUOTE=dataw0lf]What you seem to think is that there's this generic X language out there that someone can learn without making any sacrifices toward a specific language.[/quote]No, I don't.  All languages have their limitations and learning any language at the beginning will effect what you learn, inarguably.

Which is why some schools don't teach a language *at all* in their introductory courses.  None.  No LISP, no C, no Java, no C#, no nothing.  I'm not advocating that position as correct necessarily either, but I never suggested some golden language (real or not) to avoid these issues, either.

What I did suggest is that whatever language you pick to start with, C is the wrong one.  I also hinted at the fact I felt some others were poor choices too.

> I advocate mastering your first language before moving onto the next.And I never agured with this or disagreed with it.  It's not relevant to the discussion we're having either, which is why I never brought it up.

> (Like I've been doing this whole time, and this is what I warned about earlier, e.g. attacking opinions)In which case, you can never have a discussion between two disagreeing parties on this forum, and you're in violation of your own rules, I'm afraid.  Unless I don't understand what you mean by "attack".
  
> ) So, as an academic, you don't tout learning theory nor the knowledge behind something.No, I tout learning theory or knowledge when it's necessary to do so.

That's the point:  You haven't proven learning C-style memory managment is ***necessary* for a beginning programmer**.  That's more or less the crux of our disagreement, no matter how you may try to paint it.  And if you don't want to go further down that stree, that's fine.  But you haven't explictly made it clear you don't want to, as you keep replying to my points in this regard.

> 2) learning something as quickly as possible, and learning only what you needed.Show me where.  What I said was, "at the start, learn only what applies universally," which is a more than reasonable view to take.  I went further on to say, "C and C-style programming techniques and practices, including manual memory mangement," aren't universal.  I never advocated learning this stuff quickly as possible.

> I've said this before! It's my opinion!And that's fine.  If you didn't want to debate, you could have said, "this is my opinion and the way I feel, and stopped".  You didn't do that, and hence, a debate ensured.

> I've been trying to keep you from debating with me from #1, for chrissakes!No, you haven't.

> THERE WAS NOTHING TO DEBATE!Seeing as we disagree, simply not true.  

> How many times will I have to say this? Really? Honestly? Can you stop now?  No, you'll have to come up with another response that regurgitates the same thing over again.:roll:  I could say the same about you...

> I just think they should learn it early.  Do... you... finally... understand... my... point?  My... opinion.**And I want you to provide *further* justification as to why you think your opinion is correct**.  No more, no less.  If you don't want to provide justification, or don't have any to provide, that's fine, just say so.

But you keep giving the same justifications as to why you are correct, and I'll continute to give the same responses as to where I feel they're incorrect or lacking.

> Got a reference for that?No, and neither do you, which is why I responded the way I did.  :razz:

---

### Post by az on 2005-07-26
I think this sets a record for the number of posts about one topic that has two passionate sides without it degenerating into a lockable thread.

I think both sides are well argued.  But this is getting repetitive.

Can both of you suggest one or two languages that have good adoption in both the Free and Open Source circles as well as in the "corporate" world?  Basically, can you make a career out of programming FLOSS, since I think the original question pertained to GNOME?

---

### Post by dataw0lf on 2005-07-26
Python and C.

Thank you azz. 

Eh, thought I'd add a bit more for darkmatter's sake.

Gnome, and it's underlying libraries (GTK) were designed in C from the beginning.  Thus, I'd suggest C as a first language for you, as well as the points I made earlier (understanding of low level capacities, application in nearly every field, and the amount of programming languages that are derived from it).  Python isn't too bad either;  for cross platform GUI programming, I highly suggest wxPython.  wxWidgets in and of itself is a great library / widget kit.  

Good luck, and I hope programming brings you the same level of passion and loyalty as it does to *ahem* some others.

---

### Post by jdonnell on 2005-07-27
I'm late to the party, but I thought I'd throw in my two cents anyway. Let me start by saying that I develop web applications. Not websites, I'm mean serious applications that have a web front end rather than a native gui. I also do all of the hiring of programmers for my company so I've put a lot of thought into what I look for when hiring (particulary entry level positions). I'm of the opinion that the single most important ability for programmers to have is the ability to produce clean code. Clean code is code that is easy to read and understand, easy to update and modify, and is robust. This is achieved by writing code with a good structure, good tests,good abstractions, and using good processes. If a programer is bad at this it will cost us a lot of money (lost productivity). If they are good at it then it will save us a ton of money. dataw0lf said that business shouldn't be an issue in this discussion, but I think it should be the central issue. The goal of programming is to produce a program that does something. The effeciency with which this program is created and maintained is very important for businesses, open source projects, and personal projects. This IS what's important if your goal is to make a usefull program.

Because of this I feel that high level languages (python, ruby) are better for teaching students how to be good programmers than a language like C. Manipulating null terminated strings is not important for our programmers. Handling fixed length arrays and linked lists is not important for our projects. Finally, memory manipulation is very rarely an issue in the projects we develop. I'm not saying that programmers shouldn't learn these things. However, I do think that they shouldn't start with C because in takes time away from learning what is important; writing clean code and using good processes. 

Note: This is referring to most software development. I do realize that there are exceptions like OS development, device drivers, game engines, etc.

---

### Post by darkmatter on 2005-07-27
[QUOTE=dataw0lf]Python and C.
<snip>
Good luck, and I hope programming brings you the same level of passion and loyalty as it does to *ahem* some others.[/QUOTE]

Heh...Looks like I chose he 'right' two start with then. Thanks for the input, and for the lively and entertaining debate. ;-)

---

### Post by thumper on 2005-07-28
[QUOTE=dataw0lf]Python and C.[/QUOTE]

Spanner... works... throw...

I'd say Python and C++.  Some say (and I'm sure that they will) that C++ is harder to learn than C, but I disagree with this.  The additions of the standard library and a good modern book on learning the language can do wonders.

For those of you interested in a good modern C++ book to learn from, I recommend Accelerated C++ by Andrew Koenig and Barbara Moo.

---

