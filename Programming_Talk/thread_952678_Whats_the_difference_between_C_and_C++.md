---
title: "Whats the difference between C and C++?"
date: 2008-10-19
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-19
3 minutes ago I decided to make an awesome open-source multiplayer megarealistic fps game for linux :D

But should do it with C or C++? What are the differences? Is C++ better? :confused:

---

### Post by PandaGoat on 2008-10-19
C and C++ are pretty much the same syntactically. C++ has more keywords and things C does not have in the standard library (but C++ can also use C libraries).  Also, C++ is focused on Object Oriented Programming, where OOP is not part of C at all, and has a lot more exceptions you need to learn about.


But if you do not know the difference between C and C++, I really doubt you can make "an awesome open-source multiplayer megarealistic fps game for linux" in either.

---

### Post by Canis familiaris on 2008-10-19
AFIAK Syntax wise they are similar(not same) but they are different in approches (Object Oriented v Procedural)

BTW programming a 3D game particularly an Engine from scratch is "HARD" particularly for new person and that too a single one.

I think you should first try creating a 2D game in any language you know or wish to learn and then move on and create a mod using any of those gaming engines eg. Doom Engine or maybe the Source Engine (HL2 mod) though the Source Engine is not yet ported to Linux. Then as you will gain experience then maybe you should learn OpenGL, then collabrate with some open source 3D game projects and only then you can think of creating a 3D game.
Best of Luck.

---

### Post by snova on 2008-10-19
C++ is C with classes, templates, exceptions, and a few other things added. They're mostly compatible, but there's a few quirks sometimes.

---

### Post by crazyfuturamanoob on 2008-10-19
Ok thanks. Actually I know basics of OpenGL, and I made [_this_]("http://www.youtube.com/watch?v=e3H3H3KO2Ak") thing with python.

BTW I wasn't serious when I wrote I'm gonna to make that game (I am still going to make at least something).

---

### Post by Canis familiaris on 2008-10-19
> **crazyfuturamanoob said:**
> Ok thanks. Actually I know basics of OpenGL, and I made [_this_]("http://www.youtube.com/watch?v=e3H3H3KO2Ak") thing with python.

BTW I wasn't serious when I wrote I'm gonna to make that game (I am still going to make at least something).

Good one.

Now you should go ahead and learn C. Since you are already experienced with Python, learning C would be a good next step.

Here are few good resources for C:
[http://laroza77.wikidot.com/c](http://laroza77.wikidot.com/c)

---

### Post by nvteighen on 2008-10-19
The difference between C and C++ lies on the latter being an attempt of embracing several programming paradigms in a language based on C: Object-oriented, generic and procedural programming all in an imperative programming style. That makes C++ a lot "bigger" (to use a neutral term) than C and therefore, longer to take grasp of it.

---

### Post by StOoZ on 2008-10-19
the difference is that C++ has two suffix '++' after of the C.

---

### Post by LaRoza on 2008-10-19
> **Anurag_panda said:**
> 
Here are few good resources for C:
[http://laroza77.wikidot.com/c](http://laroza77.wikidot.com/c)

Yes, the founder of that wiki is a genius beyond compare.

About C and C++, C was a language designed to make writing operating systems more portable, instead of machine specific assembly.

C is small, compact, and simple.

C++ is (I think) trying to make C higher level while remaining lower level. The result is a language that can do similiar things to C, but if you do it the "C way", you are doing it wrong, and if you do it the "C++ way", you are doing it the hard way. I am sure C++ is a good language for something, but I think it is very narrow. 

C++ also has some design issues which makes it less suitable for things that C is perfect for.

---

### Post by snova on 2008-10-19
> **LaRoza said:**
> Yes, the founder of that wiki is a genius beyond compare.

...

C++ also has some design issues which makes it less suitable for things that C is perfect for.

Amusing...

I've never heard people complain about C++ until recently on these forums. Precisely what are these "design issues"?

---

### Post by Nemooo on 2008-10-19
> **snova said:**
> Amusing...

I've never heard people complain about C++ until recently on these forums. Precisely what are these "design issues"?

No, don't get them started on that topic :(

Try some searching in these forums and you should find lots of threads on the subject. Some reasons are described [here]("http://yosefk.com/c++fqa/").

EDIT: [Why to Love/Hate C++]("http://ubuntuforums.org/showthread.php?t=765733")

---

### Post by slavik on 2008-10-19
> **LaRoza said:**
> C++ also has some design issues which makes it less suitable for things that C is perfect for.

May I ask for some examples???

---

### Post by snova on 2008-10-19
> **Nemooo said:**
> No, don't get them started on that topic :(

Oops, forgot about that. Thanks for the link, though.

---

### Post by LaRoza on 2008-10-19
> **slavik said:**
> May I ask for some examples???

RTTI and name mangling for starters.

I can think of no situation where one would say "this looks like a job for C++" that would justify its widespread popularity.

---

### Post by JupiterV2 on 2008-10-19
As the name implies, and others have already stated, C++ is standard C plus additional features. This is a bit of a misnomer because if you're wanting to write pure C code "in C++" then...you're really just writing C. Essentially, while they have a similar look and feel due to syntactical similarity, C++ is a very different language with "backwards compatibility" with C.

Despite what others may say, no language is perfect nor is any language "crap." Whether the poster cares to use their head or not, each language fills a function and place. If C++ were such a horrible, terrible, useless language, it wouldn't be one of the most widely used languages in the world. Is it the best for all tasks, though? Certainly not.

Any programmer with half a brain will tell you: Use a language which best serves a) your ability, and b) your task.

I won't delve into any more depth than that but please take what some people say with a grain of salt. Always ask yourself, "does what this person is saying make sense with what I already know?"

---

### Post by PandaGoat on 2008-10-19
It is not really about C++ being badly designed, although we could argue over a vague definition.  To add clarity, it is more that C++ has so many exceptions and complications, it almost encourage bad design in programming.

I do not believe I can give very many examples, without just copying and pasting from some website so: [http://yosefk.com/c++fqa/defective.html](http://yosefk.com/c++fqa/defective.html)

I would agree that this means C++ is badly designed, but not in the way some may think.  It is a good language, just unbelievably convoluted.  I would say the substrate of C++ is good, but its facade is ugly.

If you think you can pull off writing something in C++ well, then do it.  C is just a really nice simple--clean--language.

---

### Post by dwhitney67 on 2008-10-19
> **LaRoza said:**
> RTTI and name mangling for starters.
Yeah, these affect every application I write.  :rolleyes:

> **LaRoza said:**
> 
I can think of no situation where one would say "this looks like a job for C++" that would justify its widespread popularity.
C++, like other OOP languages, allows one to define classes that use inheritance to push code commonalities to a base-class, thus obviating the need to rewrite the same code over, and over, again.

I've been programming in C++ for a little over 9 years.  Here are some of the projects I have supported that have employed C++:

[Astrolink]("http://www.comlinks.com/satcom/astrol.htm")
[AEHF]("http://www.globalsecurity.org/space/systems/aehf.htm")
[JTRS]("http://en.wikipedia.org/wiki/Joint_Tactical_Radio_System")
[GOES ABI]("http://ams.confex.com/ams/Annual2006/techprogram/paper_105816.htm")
[Medical Devices]("http://www.natus.com/index.cfm?page=products_1&crid=115")

Why was C++ chosen?  In a lot of cases because access to h/w was needed, and in other cases, it was because the language was known by many software developers.  Thus it was easier to put together large teams of s/w developers in short order.

Many companies today complain that they cannot find enough s/w developers to support their projects.  One of the reasons is that they choose poorly the platform and/or the software language that will be used on the project.  Pick a language that is fairly easy to learn, that is taught in most schools, and that is practical for the application at hand.  Pick a proprietary language, and you limit the pool of available candidates.

---

### Post by pmasiar on 2008-10-19
> **LaRoza said:**
> I can think of no situation where one would say "this looks like a job for C++" 

Job for C++ (where nothing less would be enough):

investment bank writing automatic stock trading program. All banks do the same: read ticker in real time and respond with buy/sell orders, according to trading algorithms. The guy who can make order 5 milisecond sooner wins, others lose.

You need really complicated (in-memory) database with rules, which runs really fast. C++ is obvious choice. C does not allow you for the abstraction, OOP in C++ does.

Anything else: C++ is probably overkill 8-)

---

### Post by ghostdog74 on 2008-10-19
@OP, are you proficient in Python yet ? Have you done a project in Python that you can proud of? If not, i suggest to take it slow and don't language hop.

---

### Post by anystupidname on 2008-10-19
2 pluses. :lolflag:

---

### Post by boz on 2008-10-19
It's easy to do stupid things in C++, sure.  But that's why you, as the programmer, have to make yourself "unstupid", for lack of a better term.  I just started working as a SW Engineer last year programming C++ weather algorithms and have seen the good, the bad, and the ugly.  One of its biggest problems is also one of its biggest advantages: backward compatibility with C.  I've seen a lot of C programmers using C solutions to C++ problems.  Their general lack of knowledge in object oriented design patterns can spell trouble for a C++ software project.  I'm not even that experienced and it still makes me cringe.

In the end, I believe it's up to programmer to know how to write effectively in the language they're using.  If you don't know it, learn it.  C++ takes time, but I believe it's definitely worth learning.  It will make you appreciate how simple it is to program in Java.  Really, the only difficult thing to do in Java is to be able to find the right package(s) for the job. 

Anyway, if you truly want to learn C++, here are a few good references:
C++ For Game Programmers
Modern C++ Design: Generic Programming and Design Patterns Applied
Inside the C++ Object Model
Effective C++: 55 Specific Ways to Improve Your Programs and Designs

Those are all references for those who already know a little bit of C++.  If you're a beginner, you shouldn't start with those books.  And I highly recommend C++ For Game Programmers and Inside the C++ Object Model.  I could find each of them at my University's library.

---

### Post by LaRoza on 2008-10-20
> **pmasiar said:**
> Job for C++ (where nothing less would be enough):

investment bank writing automatic stock trading program. All banks do the same: read ticker in real time and respond with buy/sell orders, according to trading algorithms. The guy who can make order 5 milisecond sooner wins, others lose.

You need really complicated (in-memory) database with rules, which runs really fast. C++ is obvious choice. C does not allow you for the abstraction, OOP in C++ does.


Ah, I should have written where "I" instead of "one".

---

### Post by Ferrat on 2008-10-20
It's kinda funny to see arguements like this but really I don't see the point, arguing about languages is like, well arguing about languages.

It's like saying English is the best languange, much better than German, French, Hindi or Mandarin, it all depends on where you're going, sure English might get you what you want almost anywhere but if you're in China Mandarin(or Cantonese) would be better, if you really know it well that is.
But if you're moving to Bolivia, deep inside the Amazon then Mandarin nor English will be much help, then you might consider learning Spanish or one of the 2 major native Indian languages.

So if you're never traveling to China then Mandarin might be more or less pointless for you to learn, specially since it's often a hard language to learn and not that global.

The point of this language is better or worse is a matter of taste, what you apply it on and why.

---

### Post by ilrudie on 2008-10-20
For the OP:
[c++ FAQ]("http://www.research.att.com/%7Ebs/bs_faq.html")*

Explains a lot about the reasons why c++ is the way it is.  Explains some of the differences between c and c++.  Its a good, interesting and informative read.

*Its written by Bjarne Stroustrup the designer and implementer of c++.

---

### Post by crazyfuturamanoob on 2008-10-20
So you say C is better? Or easier? I think it's better than python.

It takes a long time to learn a programming language. So wouldn't it be smart to start with a good language? 

If I make something with python, all devices that run my script, will need python interpreter. 
But if I make something with C/C++, the devices don't need an interpreter. And along with python interpreter, 
the devices also need all kinds of other python add-ons like pygame, pyopengl, pygtk and wxpython wrappers if I use them.

Also, compiled C works faster than python if the task is very processor heavy.

This really does not matter much to me, but to people that run my script, it means a lot. Or at least the ones who I know.


[QUOTE=ghostdog74]@OP, are you proficient in Python yet ? Have you done a project in Python that you can proud of? If not, i suggest to take it slow and don't language hop.[/QUOTE]
I can be proud of my very own cellphone game, although it sucks. Made with nokia's pys60 and works on my N73.

---

### Post by slavik on 2008-10-20
C++ requires a compiler for that platform ... either way, you need something for that platform and if there is a Python interpreter available for a platform, all the Python libraries will work without problems.

---

### Post by Canis familiaris on 2008-10-20
> **crazyfuturamanoob said:**
> 
If I make something with python, all devices that run my script, will need python interpreter. 


You can create Frozen Binaries with Python (i.e. the PVM is embedded so no need for external interpreter)

---

### Post by crazyfuturamanoob on 2008-10-20
But once I compile a program written in C, there is no need for a compiler to run it? Only for the source code.

---

### Post by Canis familiaris on 2008-10-20
> **crazyfuturamanoob said:**
> But once I compile a program written in C, there is no need for a compiler to run it? Only for the source code.

It would be needed to recompile it under every architecture. Python code on the other hand is machine independent.

<rant>
OK I know neither of Python or C is a better language overall but the point I wish to make is every language has its own domain and so as to speak advantage and disadvantage. So there's not a overall better language.
I hate these Python v C arguments and the flak given to C++ in this forum. 
A Programming Language is just a toolkit...not a social group...
</rant>

---

### Post by pmasiar on 2008-10-20
> **Ferrat said:**
> The point of this language is better or worse is a matter of taste, what you apply it on and why.

That's not true. COBOL has no recursion, so no matter your taste, some programs are impossible to write in it. There **are** substantial differences between languages, trick is you need to deeply grok couple of very different ones to understand the difference. 

People who say "it's just matter of taste" are people who do not have deep understanding of languages from different families, so for them all C-like languages are about the same, because all the languages they know **are** about the same: but it does not say much about that languages those people **did not know**, it says about the people who express "expert" opinion about the matter they have little understanding.

I refuse to accept "all the languages are the same" from someone who does not know at least  from one language from **each** family: (C Pascal) (Java C++ VB), (Perl Python Ruby) (Lisp Scheme) (any two from Prolog Forth Haskel XSLT ASM or any non-trivial non-C language).

Really guys if all you know are C-like languages, you 
(1) are right that all languages **you know** are about the same
(2) have no clue what variety of different languages is out there. No clue at all. 
So just stop making noise, it does not make any sense for people who know more than C and Java.

---

### Post by CptPicard on 2008-10-20
> **boz said:**
> It's easy to do stupid things in C++, sure.  But that's why you, as the programmer, have to make yourself "unstupid", for lack of a better term.

I much prefer a language where I don't need to become "unstupid" because of the language, but because of the problem. If a language is in the way, it's the fault of the language.

> I've seen a lot of C programmers using C solutions to C++ problems.  Their general lack of knowledge in object oriented design patterns can spell trouble for a C++ software project.  I'm not even that experienced and it still makes me cringe.

The design patterns are a sort of symptom though... this one is not the fault of C++, but the problem of static-typed object-oriented languages in general (Java included). Think of it as having to learn some black art of how to force the language to express what you have in mind, instead of being able to just express it.

> C++ takes time, but I believe it's definitely worth learning.  It will make you appreciate how simple it is to program in Java.

And to think that C++ and Java are conceptually so similar and express things very much the same way... something really has to be wrong with C++ if it is in comparison much harder to write stuff in it, and yet it doesn't give you all that much in abstraction capability over Java :)

---

### Post by nvteighen on 2008-10-20
> **Ferrat said:**
> 
It's like saying English is the best languange, much better than German, French, Hindi or Mandarin, it all depends on where you're going, sure English might get you what you want almost anywhere but if you're in China Mandarin(or Cantonese) would be better, if you really know it well that is.
But if you're moving to Bolivia, deep inside the Amazon then Mandarin nor English will be much help, then you might consider learning Spanish or one of the 2 major native Indian languages.


Your analogy is absolutely misleading. You miss a very important point: natural languages were born with **no specific task in mind** except providing communication among a community (which is a propierty of all languages...), because there's no single author behind the design of English, Spanish, German, etc. So, as they have no external task, we just can't compare if one's better than the other... 

But, artificial languages are created with a specific task in mind. Esperanto was created to provide communication among its speakers (as any language), but also to convey a pacifist-philanthropic ideology, which feeds the use of Esperanto. Lisp was created as an algorithmic language. Tolkien's Sindarin and Quenya were created for aesthetical pleasure (and interesting Diachronic Linguistics research), etc. So, you can legitimely ask whether an artificial language fulfills its external task or not... and if one shares the same task with another and fulfills it better, then it is better. Of course, you have to show why it's better with some argument.

---

### Post by estyles on 2008-10-20
This debate has gone on for a pretty long time, and I feel like I am missing an important part of it.  I haven't done coding everyday in close to 5 years - currently doing IT where I occasionally write some VBScript or modify already-written VB or C++ programs, but I'm a little out of the loop in terms of real development.  So, please take this not as a statement that I think is correct, but more of a statement of my viewpoint and a request for edification if I'm totally off base...

I feel like C++ is really the only language to use for commercial software development.  Now when you talk about Linux, that's kind of an oxymoron - you certainly can make commercial software under Linux, even commercial software that is Open Source.  But what I primarily think of in this context is enterprise software like Word Processing, Databases, etc., or retail-box games for the PC.  Which, for the most part, means Windows software (although I also wonder if large linux-based open source programs, like Open Office and GIMP are written in C++ or not?).

A lot of this type of software (at least on the lower end) is programmed in Visual Basic, but while that's a solution for "fast and dirty" development, it doesn't lead to good, robust, fast programs.  I've used VB myself when I need something quick and if it's for in-house use, but heck, I've also used VC++ for quick and dirty tool development as well - I think the "ease of use" of VB is sometimes overstated, and the shackles that it imposes on you don't usually seem worth it to me, depending on the application.

I've only just barely scratched the surface of teaching myself Python, and while it seems fine for development of small programs and tools, I don't see it as being something that you can develop a large multi-function program or suite of programs in.  Again, I'm not saying this is true - it's my impression, and if someone wants to set me straight, please do.

It just seems like, as far as python goes, it's not a replacement for C++ when it comes to power.  It seems like there's a large backlash among programers against C++ (on here, and I've also noticed it in threads at codeproject), but I never seem to hear a good argument for what to replace it with.  Can enterprise-level development really be done under python (maybe it is done, for all I know?), or is there some other reasonable substitute for C++ that is actually used for large-scale development and is as powerful when it comes down it?

---

### Post by LaRoza on 2008-10-20
> **nvteighen said:**
> 
But, artificial languages are created with a specific task in mind. Esperanto was created to provide communication among its speakers (as any language), but also to convey a pacifist-philanthropic ideology, which feeds the use of Esperanto.
And Esperanto's use of non latin characters leads to Ido, a language that is easier to learn (with the same general purpose as Esperanto).

Klingon, on the other hand, was designed to be different from any human language (it was designed by a linguist...).

Esperanto and Klingon have the same capabilities in theory, but like programming languages, their use is restricted by their original purpose. There are speakers of Esperanto and Klingon and one could have a conversation in it, but a conversations about wars and weapons would be hard in Esperanto (without using non-Esperanto words), but very easy in Klingon, and one could have a "romantic" conversation in Klingon, but it would be very...awkward (consider the Klingon greeting that is most polite means "What do you want?", it isn't the most intimate language).

---

### Post by pp. on 2008-10-20
> **Ferrat said:**
> The point of this language is better or worse is a matter of taste, what you apply it on and why.

> **pmasiar said:**
> That's not true. .... There **are** substantial differences between languages, trick is you need to deeply grok couple of very different ones to understand the difference. 

People who say "it's just matter of taste" are people who

If you care to read the post again which you are replying to, you might realise that the sentence continued after "matter of taste". You are replying to the 'matter of taste' bit while ignoring the 'what you apply it on and why' bit.

While the wording appears to bit un-orthodox, I would think that Ferrat meant to express that the choice of language is given by the problem you want to solve with it, and that it is a good idea to know why one chose a particular language for a particular job.

---

### Post by CptPicard on 2008-10-20
> **nvteighen said:**
> Your analogy is absolutely misleading. You miss a very important point: natural languages were born with **no specific task in mind** except providing communication among a community

Well, I  would like to suggest that the best general-purpose programming languages are designed with the goal in mind of providing communication about computational problem solutions among the programmer community. Then we have the even more specialized languages like HTML which are no longer special-purpose programming languages...

And this is where the "expressiveness continuum" we argue about (that exists regardless of Turing-completeness) comes to play -- we tend to argue that some languages are just more flexibly general-purpose, and thus communicate better about problems, without tripping over themselves.


> **estyles said:**
> written VB or C++ programs, but I'm a little out of the loop in terms of real development.  So, please take this not as a statement that I think is correct, but more of a statement of my viewpoint and a request for edification if I'm totally off base...

Well, if VB is your representative idea of non-C++ development, then yes indeed *please* look elsewhere for formulating a good opinion ;)


> 
I feel like C++ is really the only language to use for commercial software development.

And it is because of this sort of opinions why you see the "backlash" against C++. Those sorts of opinions tend to come people who really just know C++ and are therefore a bit religious about. I know it must feel fun to be able to jump through hoops to get your code working, but other people prefer to use more convenient tools when available.

> 
It just seems like, as far as python goes, it's not a replacement for C++ when it comes to power.

Define "power". Do you just mean runtime execution speed? My definition of power has something to do with Lisp's homoiconic program structure and code-data duality, for example. There are loads of threads about this issue on this forum :)

> It seems like there's a large backlash among programers against C++

It's mostly a backlash just against a cult-like adherence to C++ really, mostly by people who have never programmed in much anything else...

> but I never seem to hear a good argument for what to replace it with.

Anything you can, given your problem and requirements? Personally, I have a strong preference for using C for low level speed critical stuff and then interfacing it as a library to anything higher-level I actually enjoy hacking in...


> 
  Can enterprise-level development really be done under python (maybe it is done, for all I know?)

Define "enterprise-level". Your typical distributed database enterprise apps are probably most comfortably written using Enterprise Java these days. But that is a very special niche.

If you are thinking of something like a shrink-wrapped desktop app, for Windows you typically replace C++ with C#, and elsewhere... well, Python is a good choice really. Just find performance bottlenecks and code those in C if necessary.

> 
, or is there some other reasonable substitute for C++ that is actually used for large-scale development and is as powerful when it comes down it?

Again we find this concept of "power" here... become proficient in a high-level language and you appreciate a whole different kind of "power" :)

---

### Post by stevescripts on 2008-10-20
> **CptPicard said:**
> 
...
Again we find this concept of "power" here... become proficient in a high-level language and you appreciate a whole different kind of "power" :)

+1 Big-time :)

Steve

---

### Post by nvteighen on 2008-10-20
> **LaRoza said:**
> And Esperanto's use of non latin characters leads to Ido, a language that is easier to learn (with the same general purpose as Esperanto).

And other quirks lead to revisions of Esperanto. The so-called *Esperantidoj* ("Esperanto derivations", in Esperanto).

Actually, Esperanto is really full of flaws... it was created by a language-lover, but not by someone specialized on Linguistics.

> Klingon, on the other hand, was designed to be different from any human language (it was designed by a linguist...).

I read about it some time ago... (and I'll have to read about it again, as I've been assigned a little research work on artificial languages... programming languages will also be included). Yeah, it's interesting to see how superior artificial languages created by linguists are compared to people playing around intuitions.

Interestingly, I've been reading a bit about Perl. It's interesting that's the only programming language that not only relies on syntax, but also on morphology (e.g. the sigils). Yeah, they might be annoying for programming (actually, it depends on your tastes... :p), but quite interesting to see that in a programming language. But, Perl just doesn't use sigils as BASIC did... Perl supports "conversion" without change of morphology (using an array on scalar context gives the array's length) ... exactly the same you do in English with "to play" > "play" (noun)!

> **CptPicard said:**
> Well, I  would like to suggest that the best general-purpose programming languages are designed with the goal in mind of providing communication about computational problem solutions among the programmer community. Then we have the even more specialized languages like HTML which are no longer special-purpose programming languages...

+1234

> And this is where the "expressiveness continuum" we argue about (that exists regardless of Turing-completeness) comes to play -- we tend to argue that some languages are just more flexibly general-purpose, and thus communicate better about problems, without tripping over themselves.

And that's why we argue about high-level languages being better to solve problems not-specific to computer internals (which are only a subset of the infinite problems there are waiting to be solved!).

> Define "power". Do you just mean runtime execution speed? My definition of power has something to do with Lisp's homoiconic program structure and code-data duality, for example. There are loads of threads about this issue on this forum :)

In my opinion, Lisp's power comes the very fact that it was created without a computer in mind ;) (Is it true that McCarthy got mad when he knew Steve Russell implemented eval in a computer??)

> It's mostly a backlash just against a cult-like adherence to C++ really, mostly by people who have never programmed in much anything else...

We've got the Sacred Cult of C: Worshipers of the Mighty Pointer. What's the name for the C++ cult? (trying to put some fun here... :D)

---

### Post by dribeas on 2008-10-20
> **crazyfuturamanoob said:**
> 3 minutes ago I decided to make an awesome open-source multiplayer megarealistic fps game for linux :D

But should do it with C or C++? What are the differences? Is C++ better? :confused:

There is a lot of bias against C++ from people that don't know it in depth. C++ FQA is a good example of those.

First I want to state that C++ is NOT C with some extensions, it is a different language (just as java is not C++ with GC, or C is not assembler with ...)

C++ is probably one of the hardest languages, I favor it, but I won't say it is easy. As I said, lots of people start it but not so many get to understand some of the principles.

Now, as any and all languages, it deserves some true critic. If you want informed criticism search for Andrei Alexandrescu's articles on the reasons why he is designing D instead of programming C++. But don't take FQA as truth as it is widely biased, false at points and demagogic almost everywhere. 

I just don't have the time or energy to discuss articles one by one, moreover when I do think that it is useless. This is a lost war, language is like religion, most people will never convert, not even want to hear about others as prejudice is so strong.

As a sidenote. There are quite a lot of hardcore C++ programmers, and many important software systems based on it. Either all of them are wrong, or there must be some reason why C++ is not so crooked as some will say here.

On what is better C or C++, C++ has a wider library and you can use other paradigms than procedural. For most people, getting to a good OO design is easier than getting to a good procedural design. One of the advantages of C++ is that you can program procedural when it suits the problem or scale up to OO when needed.

---

### Post by LaRoza on 2008-10-20
> **nvteighen said:**
> 
I read about it some time ago... (and I'll have to read about it again, as I've been assigned a little research work on artificial languages... programming languages will also be included). Yeah, it's interesting to see how superior artificial languages created by linguists are compared to people playing around intuitions.

Klingon is truly unique. It has a complete grammar and morphology. It is a complete language (although, it has an awkward vocabulary sometimes).

> 
We've got the Sacred Cult of C: Worshipers of the Mighty Pointer. What's the name for the C++ cult? (trying to put some fun here... :D)

C++ cult? "The Cult of the Heavily Invested".

---

### Post by CptPicard on 2008-10-20
> **nvteighen said:**
> 
+1234

Uh, of course I meant that it's no longer general-purpose because it's too specialized for purpose...

> We've got the Sacred Cult of C: Worshipers of the Mighty Pointer. What's the name for the C++ cult? (trying to put some fun here... :D)

Cult of the Mighty Polymorphic Pointer? :)

> I just don't have the time or energy to discuss articles one by one, moreover when I do think that it is useless. This is a lost war, language is like religion, most people will never convert, not even want to hear about others as prejudice is so strong.

IMO the religious aspects still seem to be stronger among programmers who don't know other languages except either C or C++ ... and typically people who are "religious" about languages like Lisp are perfectly competent enough in those other, non-Lisp languages to have a good idea of the distinctions. The genuinely uninformed prejudice is almost always directed at high-level languages, not the other way around.

The "you just have to know C++ deeply enough" apologism just makes me feel like it just essentially means "you just have to learn all the quirks and how to work around them". It is obviously true that you can become a hugely skilled hacker in any language, no matter how contrived, if you're willing to accept this kind of an argument -- but I'm in full agreement with you that languages like D nicely address a lot of C++ issues and try to introduce some orthogonality to the language...

> 
As a sidenote. There are quite a lot of hardcore C++ programmers, and many important software systems based on it. Either all of them are wrong, or there must be some reason why C++ is not so crooked as some will say here.

It's a straw man to suggest we're saying that C++ is unusable. No doubt it's used a lot, by a lot of skilled people, but it still doesn't mean you couldn't be of the opinion that looking for alternatives can be a very wise strategy indeed...

> For most people, getting to a good OO design is easier than getting to a good procedural design. 

Interesting claim.. I always felt like OOP is not quite as natural as most of the OOP-salespeople make it sound like. But it may be just the way I think -- I really feel that when you want to deal with objects, you're much better off doing the object system like CLOS does, with functions separated from the data objects, and having automagic multiple dispatch to find the correct function based on input data types.

---

### Post by pmasiar on 2008-10-20
> **estyles said:**
> I feel like C++ is really the only language to use for commercial software development. 

I don't have any stats handy to disprove you, but you are confusing market for shrink-wrapped software with the whole.

Most of the programmers code programs for internal use (not for sale). Another huge group, maybe bigger than shrink-wrap, is big expensive systems with limited userbase. Both categories are more interested in programmer's productivity than efficient use of CPU.

> enterprise software like Word Processing, Databases, etc., or retail-box games for the PC. 

This is called "shrink-wrap". "Enterprise" is something banks and big manufacturers do.

BTW the biggest of enterprise systems, [http://en.wikipedia.org/wiki/Enterprise_resource_planning](http://en.wikipedia.org/wiki/Enterprise_resource_planning) systems like SAP and BAAN are written in custom basic-like language ABAP.

> It just seems like, as far as python goes, it's not a replacement for C++ when it comes to power.  

How you define power? My definition is: to let me accomplish task in least amount of code, faster to write and debug. C++ is very low-power and low-level language for me. Only worth the pain if I really am ready to suffer to get the speed, which is rarely :-)

> Can enterprise-level development really be done under python (maybe it is done, for all I know?), 

enterprise like making tons of money? What language do you think was used for YouTube?

---

### Post by dribeas on 2008-10-20
> **CptPicard said:**
> IMO the religious aspects still seem to be stronger among programmers who don't know other languages except either C or C++ ... and typically people who are "religious" about languages like Lisp are perfectly competent enough in those other, non-Lisp languages to have a good idea of the distinctions. The genuinely uninformed prejudice is almost always directed at high-level languages, not the other way around.


Some people do know other languages (I do, even if I would like to be more competent in python and scheme) and I don't think you will read any 'C++ suits all' post. Having said that, it just bothers me finding that most posts on C++ are uninformed and biased. Any post that begins with C++ is C with ... is a good example.

In case you missed it in the previous post, there are real problems with the C++ language as it is (one of them is std::vector<bool> specialization, there are others) That was first argued by Herb Sutter, one of the standards committee chair holders, or many others that made Alexandrescu design a new language.

Most people that compares C++ with C has just programmed C inside C++ file extensions, using C++ libraries. If you do that, you'll never get to understand the power of C++ nor use it. How many people here knows about foreach in C++, or has really understood the whole rationale for iterators? Most people just go to STL and find a vector and iterate on it as if it were a plain array, iterators are there, but just as a fancy strange way of working with a vector. 

How many people know about const-correctness (and follows it?) or exception safety or RAII, references... If you don't know or fully understand those concepts and the power they unleash, then C++ is just fancy C. And I must agree, take those things (and possibly a couple I forgot to list) out of C++ and the reasons for using C++ over C are about gone.

Just to state things as clear as I can: I am not discussing other languages, I am arguing about many uninformed/biased criticism on C++. You can write shitty code in C++, as you can in about any other language you care to find, but that is never a reason to despise a language, else you should despise all languages.

---

### Post by pmasiar on 2008-10-20
> **nvteighen said:**
> Perl... the only programming language that not only relies on syntax, but also on morphology (e.g. the sigils). 

because [http://en.wikipedia.org/wiki/Larry_Wall](http://en.wikipedia.org/wiki/Larry_Wall) "and his wife were studying linguistics with the intention afterwards of finding an unwritten language, perhaps in Africa, and creating a writing system for it. They would then use this new writing system to translate various texts into the language, among them the Bible."

> In my opinion, Lisp's power comes the very fact that it was created without a computer in mind ;) (Is it true that McCarthy got mad when he knew Steve Russell implemented eval in a computer??)

I don't know that, but I learned today (and I am not sure if it's true, but: ) that ALGOL was first formulated to write about algorithms, without any idea how to implement stacked context - because stack as data structure was invented in 55-57, in parallel with Algol - in 58.

> We've got the Sacred Cult of C: Worshipers of the Mighty Pointer. What's the name for the C++ cult? 

Cult of the doubly sacred +? 8-)

Worshipers of the pointer at least have the speed and simplicity... :-/

---

### Post by LaRoza on 2008-10-20
> **pmasiar said:**
> 
Cult of the doubly sacred +? 8-)


Or:
```

cppCult = std::cult<forum::cpp>("C++").setDefensiveness(true).makeSimpleLanguagesComplicated(true)

```

---

### Post by snova on 2008-10-20
"Cult of the Reference"

"Cult of Incrementation - Taking over the world 1 at a time."

"Cult::C++"

---

### Post by CptPicard on 2008-10-20
> **dribeas said:**
> I don't think you will read any 'C++ suits all' post. Having said that, it just bothers me finding that most posts on C++ are uninformed and biased. Any post that begins with C++ is C with ... is a good example.

Yes you're correct, and I'm not assuming to read such posts from you. Neither will you get any of those "C++ is C with classes" posts from me... my issues with C++ go a bit deeper. And then there's the fact that a lot of languages seem to do much more with much less of "language" if you catch my drift...

> 
In case you missed it in the previous post, there are real problems with the C++ language as it is

Yes.. as I said, I like a lot of the rationales behind D. It is coming together into a very interesting language IMO.

> Most people that compares C++ with C has just programmed C inside C++ file extensions, using C++ libraries. If you do that, you'll never get to understand the power of C++ nor use it.

Well, I somewhat get the feeling that you're underestimating a lot of C++ critics... this is a rather trivial way of misusing C++. Of course, this phenomenon certainly exists.

> 
 How many people here knows about foreach in C++, or has really understood the whole rationale for iterators?

Well, an iterator is a general design pattern in all kinds of languages, not just C++.

A more enlightened criticism of C++ here would probably  be that it's interesting that STL and iterators need to be implemented in a templating system which is essentially a symbol-substituting preprocessor (which can be fragile)... it produces very, uh, "interesting" compiler errors sometimes. :)

> 
How many people know about const-correctness (and follows it?)

One could turn this around and ask that does one really need const-correctness, in particular when you're not going to get ironclad data encapsulation safety anyway?

> 
 or exception safety or RAII

In my book, RAII to solve exception safety issues is again in the camp of treating symptoms by design pattern you just "need to know", not a "powerful feature of language"...

(Yes, in languages like Java you still need to manage your file handles etc, but memory leaks are still the most profound resource-management issue)

> 
, references...

... which is a sugar-coated pointer...

>  If you don't know or fully understand those concepts and the power they unleash, then C++ is just fancy C.

I am not really sure if they actually do unleash significant amounts of additional power, although I am aware of them and realize that you want to know this stuff in order to be competent in C++...

> 
 And I must agree, take those things (and possibly a couple I forgot to list) out of C++ and the reasons for using C++ over C are about gone.

Polymorphism of pointers... it is, after all, IMO *the* feature of C++ over C.

---

### Post by boz on 2008-10-20
> **CptPicard said:**
> The "you just have to know C++ deeply enough" apologism just makes me feel like it just essentially means "you just have to learn all the quirks and how to work around them". It is obviously true that you can become a hugely skilled hacker in any language, no matter how contrived, if you're willing to accept this kind of an argument -- but I'm in full agreement with you that languages like D nicely address a lot of C++ issues and try to introduce some orthogonality to the language...

Okay, but what do you do until D comes around.  Complain about C++ and refuse to use it because it's "hard"?  (I know that's not what *you're* doing, Picard, but I've gotten that impression from some people on this thread). I was a complete newb at C++ before I started working with it a little over a year ago and it's not that bad.  I've also learned perl, matlab, verilog, x86 assembler, csh|ksh|bash, and Java.  C++ is my personal favorite, but I don't hesitate to use any of the other ones if they're better for the job.  (I prefer to use perl for scripting, for instance.)  By the way, I don't think you'll find a language without quirks, but then again I haven't been programming that long.  If you can point me to one that is also highly versatile, please do so.

> **CptPicard said:**
> It's a straw man to suggest we're saying that C++ is unusable. No doubt it's used a lot, by a lot of skilled people, but it still doesn't mean you couldn't be of the opinion that looking for alternatives can be a very wise strategy indeed...

If I ever hear anyone use the argument that C++ is unusable, then I would have to argue that their opinion is revealing of an uninformed and possibly lazy mind.  C++ is, like you said, used by a lot of people, and for a lot of applications.  Like 3d game engines?

---

### Post by CptPicard on 2008-10-20
> **boz said:**
> Okay, but what do you do until D comes around.  Complain about C++ and refuse to use it because it's "hard"? 

Oh, actually indeed that ;)

I just use any of the other languages that are a good fit for whatever problem I am faced with. Actually needing C++ is pretty rare for what I'm usually doing.

> If you can point me to one that is also highly versatile, please do so.

Common Lisp, or any other Lisp variant. They really are the most versatile of them all. The more comfortable I become with Lisp, the more addicted I am becoming...

> 
If I ever hear anyone use the argument that C++ is unusable, then I would have to argue that their opinion is revealing of an uninformed and possibly lazy mind.

As a matter of fact, I am confident enough in my own competence that I am not really afraid of saying that my mind is indeed "lazy" when it comes to having to jump through hoops with tools. The lazier I can be in that department the happier I am ;)

For me it is enough to know that I never found C++ programming enjoyable in the same sense as I find Lisp programming enjoyable... it's hard to describe the distinction, but with the latter you always have your problem directly at your fingertips, while with the former you need to pay much more attention to how exactly you plan on making the language do what you want to do...

---

### Post by dwhitney67 on 2008-10-20
> **CptPicard said:**
> ...

For me it is enough to know that I never found C++ programming enjoyable in the same sense as I find Lisp programming enjoyable... it's hard to describe the distinction, but with the latter you always have your problem directly at your fingertips, while with the former you need to pay much more attention to how exactly you plan on making the language do what you want to do...

Out of curiosity, is Lisp widely used in the software development industry?  Would it be prudent for one to abandon their studies of other languages so as to focus on Lisp?  Are there many job opportunities for Lisp programmers?  Do the jobs pay well?

These are sincere questions, so I hope you can answer them.

I think many developers here on the Ubuntu Forums write software as a hobby, not so much because they earn a living do it.  Other forum members, from what I gather from their posts and competence level, definitely fit the profile of a professional s/w developer.

---

### Post by estyles on 2008-10-20
> **CptPicard said:**
> Common Lisp, or any other Lisp variant. They really are the most versatile of them all. The more comfortable I become with Lisp, the more addicted I am becoming...

> As a matter of fact, I am confident enough in my own competence that I am not really afraid of saying that my mind is indeed "lazy" when it comes to having to jump through hoops with tools. The lazier I can be in that department the happier I am ;)

Umm...  programming in Lisp and NOT jumping through hoops aren't two things that I tend to link together.  I mean, I love the lambda calculus as much as the next guy, but I find that trying to write complex, sequentially-executing programs in Lisp is like trying to nail jello to a wall.

I don't believe I've ever seen a GUI written in Lisp, though I'm willing to believe it might be possible, given enough brick walls and programmer's heads.

I'm not saying you can't code in Lisp, but if that's what you consider not jumping through hoops, well, maybe C++ programmers and Lisp programmers have different ideas of what represents a circle...

---

### Post by CptPicard on 2008-10-20
> **dwhitney67 said:**
> Out of curiosity, is Lisp widely used in the software development industry?

Obviously not, but it definitely should be :) ("Beating the Averages" has good thoughts on this)

It's really a matter of popularity and momentum, unfortunately... if you want to look at this from the "getting a job" perspective, I suppose the best languages in existence are Java and C#, then. Doesn't mean they necessarily are great, though. Code-monkey languages by definition pander to the lowest common denominator.

> 
  Would it be prudent for one to abandon their studies of other languages so as to focus on Lisp?

No, it is not "the only language". Although it certainly helps one in thinking about programs.

> 
  Are there many job opportunities for Lisp programmers?  Do the jobs pay well?

If you're allowed to choose your tool, you can make your own job opportunities, and be more productive at them using a more powerful tool. Our late lnostdal is a consultant who works almost exclusively using Lisp, and his work is very impressive. I am also in the fortunate position of getting to choose my tools, but admittedly what I do is not *primarily* as much "software production" as using programming as support for the primary activities (that is, they are all analysis/processing tools that are 100% in-house). Then there's of course my CompSci background which certainly gives me a certain bias...

When using an uncommon language, pay is usually higher than when using a common language, too, because you're not competing with a million code monkeys...


> **estyles said:**
> Umm...  programming in Lisp and NOT jumping through hoops aren't two things that I tend to link together.  I mean, I love the lambda calculus as much as the next guy, but I find that trying to write complex, **sequentially-executing** programs in Lisp is like trying to nail jello to a wall.

I guess the bolded part is the tell here -- if you're very stuck in the imperative mindset, yes, Lisp can seem weird. Then again, Common Lisp in particular is multiparadigm enough that you *can* write very imperative code in it if you want to. Scheme enforces functionality much more, and Clojure even tries to get rid of mutable state and strive for pure-functionality. It's the latter that I still struggle with, but am seeking to come to grips with by slowly working myself towards proficiency in languages like Haskell...

---

### Post by pmasiar on 2008-10-20
> **dwhitney67 said:**
> Out of curiosity, is Lisp widely used in the software development industry? 

Of course **not** - only smartest of hackers use Lisp 8-)

As Graham says, he was always checking what kind of skills cometitors hire: he would be scared if they hired Lispers.

> Would it be prudent for one to abandon their studies of other languages so as to focus on Lisp?

Read "beating the averages". Using Lisp was rather prudent decision for Paul Graham: it made him a millionaire ;-)

>  Are there many job opportunities for Lisp programmers?  Do the jobs pay well?

not many, but some pay extremely good.

---

### Post by dwhitney67 on 2008-10-20
Well, I read the first quarter of the "Beating the Averages", and immediately I noticed that the author (Paul Graham) is biased towards Lisp.

He states that learning Lisp would make a person a better programmer, just like a better brush would yield a better painter.  That's a very strong argument to make with no empirical proof.  His statement should be regarded as merely an *opinion*, not fact.

A better brush would NOT make a better painter, just like a $200 tennis racket will NOT make a amateur tennis player into a professional.

Either you have the appropriate skill level needed for the job, or you don't.  Certain tools will make the job easier, but to jump to the conclusion that Lisp is the language of all languages is preposterous.  Rafael Nadal will kick my a$$ any day at tennis, even with a $20 tennis racket from a thrifty store.

In college I took an AI course, and as a co-requisite to that course, I also took Lisp programming.  Aside from the insane number of parenthesis I had to type, I really feel that the language did not offer me anything useful.  In fact, I feel that it has provided zero return on my investment (that is, on the time/money spent on those courses).  So as you can see, I also have an opinion.

Now, if Paul Graham and his colleague had chosen a different language other than Lisp for the ViaWeb project, I wager that the project would have succeeded nonetheless.  In turn, we would be reading the same "Beating the Averages" text, but with Graham pushing the use of the "other" language.

Anyhow, to each their own.  I for one enjoy a roof over my head, and good food on the table.  To obtain these, I need a job that pays well, and for a job market that seeks/uses the languages I know.  Whenever I check out the employment ads, I see a lot of demand for .NET, C#, J2EE, C++, C, and Python (and not necessarily in this order).  There is also a strong demand for embedded programmers, which pretty much knocks the wind out of .NET, C#, J2EE, and Python (?).

Well, I'm off to pour myself another drinkie... see my avatar to guess what I'm having!  Another 7 days and the holiday is over.  :(

---

### Post by boz on 2008-10-20
For embedded programming, C and Assembler are a must have.  I believe any programmer should be able to program in C at a minimum.  (And the greatest of hackers program in Assembler ;))  It is the opinion of this particular code monkey that knowledge of any one programming language won't make you a great programmer, but rather the ability to learn *any* language when the need calls for it.  I've never bothered to learn Lisp, but I am confident enough in my own ability that I could learn the language if the need ever called for it.  (It does look like a pretty sweet language, but I'm not wild about the syntax.)

By the way, there's nothing wrong with being "lazy" in the sense that you can use the fastest possible route to a solution.  If Lisp does that for you, then you're doing the right thing.  ;)  But in industry, the fastest route isn't always the best for a long term solution.  You always have to be concerned with maintainability of the code.  Is your code well documented?  Portable?  Reusable?  

I've seen a lot of open source code where these are significant problems.  I'm "lazy" in the sense that I don't want to have to read over 5000 lines of someone else's spaghetti code before I can add my own functionality to it (which probably means I would have to refactor and document the old code first).  If you write hacky, spaghetti code that no one else **cares** to understand it doesn't necessarily make you a better programmer.

---

### Post by estyles on 2008-10-20
> **CptPicard said:**
> 
[quote=estyles]
Umm... programming in Lisp and NOT jumping through hoops aren't two things that I tend to link together. I mean, I love the lambda calculus as much as the next guy, but I find that trying to write complex, sequentially-executing programs in Lisp is like trying to nail jello to a wall.

I guess the bolded part is the tell here -- if you're very stuck in the imperative mindset, yes, Lisp can seem weird. Then again, Common Lisp in particular is multiparadigm enough that you can write very imperative code in it if you want to.[/quote]

And that's where I say that Lisp isn't "bad" or "impossible to write in", but trying to remove commands from programming seems like jumping through, umm... what are those circular things again?  ;)

I've seen how elegantly Lisp handles certain problems, but I've also raged at my own poorly-written Lisp code enough to know that certain things weren't meant to be done in Lisp.  Or let me rephrase that... certain things weren't mean to be done in Lisp *by me* at any rate.

---

### Post by Sinkingships7 on 2008-10-21
> **boz said:**
> [...] (And the greatest of hackers program in Assembler ;)) [...]

Surely you jest?

---

### Post by boz on 2008-10-21
Okay, I misspoke.  The greatest of hackers *are able to* program in assembler.  It certainly isn't the language of choice, unless you want to do some system-level hacking.

---

### Post by dribeas on 2008-10-21
> **CptPicard said:**
> Yes.. as I said, I like a lot of the rationales behind D. It is coming together into a very interesting language IMO.

The idea here is that Alexandrescu is probably one of the most informed C++ critics. He knows the language better than 99.9% of the C++ programmers, and when he critics he does it from knowledge and experience.

> **CptPicard said:**
> A more enlightened criticism of C++ here would probably  be that it's interesting that STL and iterators need to be implemented in a templating system which is essentially a symbol-substituting preprocessor (which can be fragile)... it produces very, uh, "interesting" compiler errors sometimes. :)


Template compiler errors are horrible, that is a fact (at least as of now) but that is not strictly a language problem (try Comeau compilers). Now what I cannot take from this sentence is that templates are 'symbol substituting preprocessor' for two reasons.

First, it has nothing to do with preprocessor substitution. Before even considering the template arguments, the template is validated for consistency (thats where 'typename' keyword comes into play) as any other piece of code would. Then the template is instantiated with the type (not the text, but a real type from the C++ type system at the time [and/or compile time constants]) and the code is once again validated. 

Now, everyone agrees that compiler errors must be better, and that is why in the next revision of the standard (due next year) there is a new facility called concepts. That will not provide anything new to the language, just ease compiler errors. The idea is that you will provide prerequisites to the template arguments during template definition, so that when the compiler detects that the template argument does not fulfill the requirements instead of saying 'type X does not have method f()' it will cry out a more informed 'type X is not a ForwardIterator because f() is not defined'. But note that this is not a new functionality of the language, nothing new is added here, just helping the communication between programmers and compilers.

> **CptPicard said:**
> One could turn this around and ask that does one really need const-correctness, in particular when you're not going to get ironclad data encapsulation safety anyway?

It is a great help to detect programmer errors. Once you define your operations (and only allow mutability when needed, that is const-correctness) the compiler will help you with mistakes. If you provide a non-mutating method that by mistake changes the data underneath, you will have quite some fun going through your code base trying to find why the value changed from when it was set to when the change was detected.

I have never done any professional programming other than TCL (too long ago to remember), Java and C++. In Java I have had to go through code to detect when object state changed.

The rationale is exactly the same as avoiding globals: the compiler will limit the places where variables can change, thus limiting the possible erroneous iterations.

> **CptPicard said:**
> In my book, RAII to solve exception safety issues is again in the camp of treating symptoms by design pattern you just "need to know", not a "powerful feature of language"...

(Yes, in languages like Java you still need to manage your file handles etc, but memory leaks are still the most profound resource-management issue)


To me, the issue here is that RAII provides two advantages over GC. First off, there is a single approach to resource handling. Once you get to use it, everything will be handled uniformly and chances of leaking resources will drop.

The second part is that with RAII you do control the instant in which the resource is freed. You don't depend on the GC to run, and it does not get in the way of memory management as finalizers do in Java.

The project I work in has 10 developers and has been running for about a year and a half. There is not a single call to delete in the code and no resources (of any kind) are leaked. That is something you can do with C++ that you cannot with C. The important part is not that you don't call delete, but the fact that you don't have to remember to call it and thus cannot forget it. The same goes with all other resource handlers.

> **CptPicard said:**
> Polymorphism of pointers... it is, after all, IMO *the* feature of C++ over C.

Yes, precisely right, I subsumed that into OO and did not really specify in the list.

---

### Post by nvteighen on 2008-10-21
> **estyles said:**
> Umm...  programming in Lisp and NOT jumping through hoops aren't two things that I tend to link together.  I mean, I love the lambda calculus as much as the next guy, but I find that trying to write complex, sequentially-executing programs in Lisp is like trying to nail jello to a wall.

I don't believe I've ever seen a GUI written in Lisp, though I'm willing to believe it might be possible, given enough brick walls and programmer's heads.

I'm not saying you can't code in Lisp, but if that's what you consider not jumping through hoops, well, maybe C++ programmers and Lisp programmers have different ideas of what represents a circle...

Ah, because Lisp development is meant to be different. If you want to get the power from Lisp, you don't create an application, but just create a new language to suit whatever you need. Then, you just distribute modules and the user loads them into the interpreter and types in "commands" as it were a shell scripting language designed for a certain problem. But, if you want to have extreme power, you not only create a new language, but create a new language embedded in Lisp (therefore a new Lisp-dialect) that automatically inherits the whole set of features Lisp has. The reason of why this is possible is because Lisp works on recursive syntax (a corolary of homoiconicity) and is the only programming language capable of metalinguistic analysis (in one phrase: it's the most natural of all programming languages).

---

### Post by nvteighen on 2008-10-21
> **pmasiar said:**
> because [http://en.wikipedia.org/wiki/Larry_Wall](http://en.wikipedia.org/wiki/Larry_Wall) "and his wife were studying linguistics with the intention afterwards of finding an unwritten language, perhaps in Africa, and creating a writing system for it. They would then use this new writing system to translate various texts into the language, among them the Bible."

Yeah. This gives Perl some interesting features. Sadly, it's not a dynamic-typed language, but I really think it's worth to learn.

> I don't know that, but I learned today (and I am not sure if it's true, but: ) that ALGOL was first formulated to write about algorithms, without any idea how to implement stacked context - because stack as data structure was invented in 55-57, in parallel with Algol - in 58.

Interesting; I didn't know that. Is that the reason why ALGOL-58 didn't have I/O procedures?

---

### Post by CptPicard on 2008-10-21
Btw, little disclaimer -- now that we're talking Lisp, I am of course pushing Lisp, but I'm not *that* religious -- as in, it's not the only language around, although if I had to pick just one, it would be Lisp, because it is flexible enough to get closest.

> **boz said:**
> It is the opinion of this particular code monkey that knowledge of any one programming language won't make you a great programmer, but rather the ability to learn *any* language when the need calls for it.  I've never bothered to learn Lisp, but I am confident enough in my own ability that I could learn the language if the need ever called for it.  (It does look like a pretty sweet language, but I'm not wild about the syntax.)

Don't be so cavalier about something that apparently is outside the scope of your experience for the time being ;) (although I am sure that yes you can learn it if you put your mind to it, I don't doubt that... it just may be more enlightening than you expect!)

Learning any other C-derivative language is a triviality once you know one or two (ok, C++ is harder because there are lots of gotchas and best practices and design patterns to be aware of, plus the language itself is just large). Other languages genuinely introduce you to something conceptually new -- learning Lisp is a nice test of ability, because the syntactic part of the language is the simplest possible, but conceptually you get, to begin with, first-class function objects and the anonymous function (lambda) which is a much more powerful tool than what first meets the eye. It really is not an academic toy -- it makes you think different about stuff even in other languages, and I totally miss it in languages that don't have it, because I am so used to the "design patterns" it enables...

The syntax you're not wild about by the way is the strongest point -- code is data, language structure is homoiconic, all lisp programs are essentially recursively smaller lisp programs. You can easily dynamically build arbitrary code at runtime and either interpret it or run it through the compiler and then use the compiled function. You have a macro system that again takes arbitrary stuff at read/compile time, runs it through a completely lisp-based transformer and then compiles the result, allowing you to embed your own language rules into your code trivially...


> But in industry, the fastest route isn't always the best for a long term solution.  You always have to be concerned with maintainability of the code.  Is your code well documented?  Portable?  Reusable?  

Lisp is very readable once you get in the habit of reading it. In functional code you're dealing with transformations on entities, not procedural descriptions of "program steps", so you get a much better idea of what is being done, to what, and why.

Reusability and ability swap parts is the best I've seen anywhere simply because code usually consists of small functions put together, and a function is easy to replace. Good Lisp style discourages side-effects (although Common Lisp is practical enough to allow them), so this kind of swap is usually achievable with minimal pain.


> 
I've seen a lot of open source code where these are significant problems.  I'm "lazy" in the sense that I don't want to have to read over 5000 lines of someone else's spaghetti code before I can add my own functionality to it

Lisp code is small, short and modular, trust me :) I've been reading lnostdal's SymbolicWeb code occasionally, and it's not too hard to grok although it's the most efficient AJAX/Comet framework around and does some pretty incredible stuff -- essentially it abstracts AJAX stuff to browser behind a traditional-style event-driven GUI application API.

dwhitney, as it comes to ViaWeb... to think of the alternatives back when  it was written... I can seriously believe that sticking a Lisp REPL behind port 80 has been a totally superior solution to any set of CGI scripts :) They have even been able to directly modify the running application even while their users' sessions have been running smoothly...


> **estyles said:**
> And that's where I say that Lisp isn't "bad" or "impossible to write in", but trying to remove commands from programming seems like jumping through, umm... what are those circular things again?  ;)

Lisp's core is minimal, in particular so in Scheme. But if you look at Common Lisp, because the macro system essentially allows for arbitrary extension, you can bring in any control constructs if you desire them. I guess you're most missing the for loop... well, the [loop macro]("http://gigamonkeys.com/book/loop-for-black-belts.html") is very flexible. And I need to stress that loop isn't there in the core -- it's a macro defined in terms of core capability.

Lisp has a core that

1) is small
2) has powerful base concepts (lambdas, macros, data-code duality)
3) ... that are generic (stuff applies the same to anything without exception)

That sort of stuff can be very flexible, and really brings out the applied thinking in the programmer...

> 
I've seen how elegantly Lisp handles certain problems, but I've also raged at my own poorly-written Lisp code enough to know that certain things weren't meant to be done in Lisp.  Or let me rephrase that... certain things weren't mean to be done in Lisp *by me* at any rate.

Just switch to an imperative style then, it's perfectly doable, esp. if you're writing in CL. You can "write C" in CL just fine :)

> **dribeas said:**
> The idea here is that Alexandrescu is probably one of the most informed C++ critics. He knows the language better than 99.9% of the C++ programmers, and when he critics he does it from knowledge and experience.

Critic regardless, and a knowledgeable one at that! :)

> The idea is that you will provide prerequisites to the template arguments during template definition, so that when the compiler detects that the template argument does not fulfill the requirements instead of saying 'type X does not have method f()' it will cry out a more informed 'type X is not a ForwardIterator because f() is not defined'.

I suppose this sort of added knowledge of what template parameters actually are is kind of what I would be after ... then again, I never became a huge fan of, say, Java Generics either...

> 
It is a great help to detect programmer errors. Once you define your operations (and only allow mutability when needed, that is const-correctness) the compiler will help you with mistakes.

Do these kinds of mistakes actually happen much? Somehow it seems like being in the same category as private variables -- programmers should be "consenting adults" and will break into the private parts anyway if they want to.

> 
 If you provide a non-mutating method that by mistake changes the data underneath, you will have quite some fun going through your code base trying to find why the value changed from when it was set to when the change was detected.

Admittedly, while I know what const-correctness is supposed to be, I have not played enough with it to have much of a valid opinion. Just simply from a language-theoretic POV I do get this gut feeling that declaring your object const may help in trivial cases that you would manage yourself anyway, and will fail in more complex, surprising ways... you don't necessarily know where your object is going to end at when you pass it to some method, declared const or not.

Interestingly, Lisp takes a different tack to this -- it really discourages side-effects to begin with, and state changes are easy to limit to clearly defined let-environments. OOP-languages have much more shared-state problems... Rich Hickey, the creator of Clojure, had much interesting things to say about this in some of his video lectures that can be found on the net...

> 
To me, the issue here is that RAII provides two advantages over GC.

Yes, I am aware of these. It's still sort of interesting that it's a language-external pattern that required the addition of templates, because the exception system is dangerous to begin with.

Also, RAII binds your stuff conceptually to the stack a bit too much for my taste... a GC at least tracks your object lifetime so that it can die independently on its own.

---

### Post by pmasiar on 2008-10-21
> **boz said:**
>  I've never bothered to learn Lisp, but I am confident enough in my own ability that I could learn the language if the need ever called for it.  (It does look like a pretty sweet language, but I'm not wild about the syntax.)

Yup, you just proved beyond reasonable doubt the lack of understanding of the important matters: Lisp syntax is trivial, trick (and power) is in different kind of semantics, which difference passed high above your head, luckily not hitting you ;-)

This is exactly why is so funny if anyone expresses opinion about Lisp based on syntax, and why everyone grokking Lisp at least a bit is ROFL. Thanks for expressing the point to clearly.

I do not doubt you can learn Lisp, if you want: your refusal to do so robs you from interesting learning experience.

---

### Post by pmasiar on 2008-10-21
> **dwhitney67 said:**
> He states that learning Lisp would make a person a better programmer, just like a better brush would yield a better painter.  That's a very strong argument to make with no empirical proof.  His statement should be regarded as merely an *opinion*, not fact.

his opinion is based on creating successful startup using Lisp which made him millionaire. How much is your opinion worth?

> I also took Lisp programming.  Aside from the insane number of parenthesis I had to type, I really feel that the language did not offer me anything useful.  

You should ask return of your tuition, you did not learned the most important lesson ;-)

> So as you can see, I also have an opinion.

My pet dog has opinion too. You forgot that this is not democracy but meritocracy. Noobs count the vote, smart people evaluate each opinion and weight it by the merit.

> Now, if Paul Graham and his colleague had chosen a different language other than Lisp for the ViaWeb project, I wager that the project would have succeeded nonetheless.  

Graham's millions says that only Lisp (and his smart colleagues) enabled him to beat the insane odds and the competition.

> I for one enjoy a roof over my head, and good food on the table.  

So you suggest that Graham is homeless bum? ;-)

---

### Post by pmasiar on 2008-10-21
> **nvteighen said:**
> Lisp works on recursive syntax (a corolary of homoiconicity) and is the only programming language capable of metalinguistic analysis (in one phrase: it's the most natural of all programming languages).

you should learn Forth, you would love it. It has even simpler syntax and even more natural uses "programming by extending the language" paradigm.

---

### Post by nvteighen on 2008-10-21
> **pmasiar said:**
> you should learn Forth, you would love it. It has even simpler syntax and even more natural uses "programming by extending the language" paradigm.

Thanks! I'll look at it whenever I have some time.

(EDIT: Actually, I'm already looking at it. It looks weird, but promising)

---

### Post by slavik on 2008-10-21
> **nvteighen said:**
> Yeah. This gives Perl some interesting features. Sadly, it's not a dynamic-typed language, but I really think it's worth to learn.



Interesting; I didn't know that. Is that the reason why ALGOL-58 didn't have I/O procedures?
Perl is not dynamically typed?! say what?!

---

### Post by nvteighen on 2008-10-21
> **slavik said:**
> Perl is not dynamically typed?! say what?!

Eh? Is it?? (If I'm an ignorant, please slap me)

---

### Post by slavik on 2008-10-21
the following is not a problem:

my $a;
$a = 5;
$a = "hello";
$a = [5,10,5];
$a = \%some_hash;

---

### Post by dwhitney67 on 2008-10-21
What is the difference between C and C++??

Hmmm... let's see...

C - C++ = Perl

That can't be right. Maybe...

C - C++ = Lisp

No...

C - C++ = Dead horse

Yes!!! Eureka... I got it right.

---

### Post by pmasiar on 2008-10-21
Of course Perl is dynamically typed.

Dynamic typing means that existence of a method is tested at runtime - so any object with needed method can polymorfically replace another, does not have to be from proper (static) inheritance tree. Improves flexibility a lot ;-)

> **slavik said:**
> 
my $a;
$a = 5;
$a = "hello";
$a = [5,10,5];
$a = \%some_hash;

Perl can do even stranger things: print "3" + 5; (prints 8) which is called "weak typing". 

One of important improvements of Python over Perl is (IMHO) that Perl is dynamically but weakly typed, Python is dynamically but strongly typed, and "3" + 5 is error, as it should be.

---

### Post by estyles on 2008-10-21
> **dwhitney67 said:**
> 
Hmmm... let's see...
C - C++ = Perl

That can't be right. Maybe...
C - C++ = Lisp

No...
C - C++ = Dead horse

C - C++ = --

Simple arithmetic.

---

### Post by nvteighen on 2008-10-21
> **pmasiar said:**
> 
One of important improvements of Python over Perl is (IMHO) that Perl is dynamically but weakly typed, Python is dynamically but strongly typed, and "3" + 5 is error, as it should be.

So, I confused dynamic typing with weak typing... Thank you very much.

> **estyles said:**
> C - C++ = --

Simple arithmetic.

You don't know substraction:

```

C - C++ = ++

```

But '++' is a C operator, so:
```

C - C++ = C

```

Therefore, to that be possible:
```

C++ = 0

```

:)

---

### Post by Canis familiaris on 2008-10-21
> **nvteighen said:**
> 
Therefore, to that be possible:
```

C++ = 0

```

:)
LValue Required?

---

### Post by Shin_Gouki2501 on 2008-10-21
Ho anyone seeks advice on Type systems, there do exist some resources:
[http://www.pphsg.org/cdsmith/types.html](http://www.pphsg.org/cdsmith/types.html)
Some others just for fun:
[http://iacobus.blogspot.com/2008/06/dont-call-it-static-or-dynamic-language.html](http://iacobus.blogspot.com/2008/06/dont-call-it-static-or-dynamic-language.html)
[http://blog.tmorris.net/javaruby-does-not-generalise-to-staticdynamic/](http://blog.tmorris.net/javaruby-does-not-generalise-to-staticdynamic/)
(this one refers to the first one)

Sometimes its just amazing how much knowledge exists out there in all the blogs, compared to wikipedia, but i guess its difficult to agree on ;)

---

### Post by estyles on 2008-10-21
> **nvteighen said:**
> 
You don't know substraction:


C - C++ = ++


No, it equals negative ++, which I assume is --.

> 
But '++' is a C operator, so:
C - C++ = C


Well, if you use ++ as an operator, then C - C++ = -1.

---

### Post by Canis familiaris on 2008-10-21
> **estyles said:**
> No, it equals negative ++, which I assume is --.



Well, if you use ++ as an operator, then C - C++ = -1.

C - C++ = Lvalue error ;)
C++ != C+1 :)

---

### Post by pmasiar on 2008-10-21
> **Shin_Gouki2501 said:**
> Sometimes its just amazing how much knowledge exists out there in all the blogs, compared to wikipedia, but i guess its difficult to agree on ;)

Of course blogs are fine, but it takes time to find relevant posts and evaluate merit of posters. Wikipedia is kinda peer-reviewed.

[http://en.wikipedia.org/wiki/Type_system](http://en.wikipedia.org/wiki/Type_system) has all the info you may want, and more.

---

### Post by snova on 2008-10-21
C - C++ = 0

It's a bit late, but thanks for reminding me of D, CptPicard. I took a look at it a while ago and thought it was a bit neater, but didn't stay with it for very long. It looks even better now!

PS. Which do you prefer, Phobos or Tango? A quick look at Phobos makes me think it could stand imporovements, so I downloaded Tango earlier to see what it was like. Still haven't opened it.

---

### Post by LaRoza on 2008-10-21
Anyone mind if I close this?

---

### Post by Sinkingships7 on 2008-10-21
> **LaRoza said:**
> Anyone mind if I close this?

It's been fun, but it would seem that it's stopped progressing.

---

### Post by nvteighen on 2008-10-21
> **LaRoza said:**
> Anyone mind if I close this?
Any particular reason? The only possible one I can think of is that discussion is absolutely off-topic.

But we must toast for an interesting language discussion without flames! Well done, fellows!

---

### Post by LaRoza on 2008-10-21
> **Sinkingships7 said:**
> It's been fun, but it would seem that it's stopped progressing.

I guess it can go to Recurring Discussions. Basically, it seems the answer is "C != C++", and it is just a redo of the why to love/hate C++.

---

### Post by LaRoza on 2008-10-21
> **nvteighen said:**
> Any particular reason? The only possible one I can think of is that discussion is absolutely off-topic.

But we must toast for an interesting language discussion without flames! Well done, fellows!

Well, once a thread gets reports, I feel something should be done.

---

### Post by CptPicard on 2008-10-21
It's getting reports?

Come on, whoever reported something... I get the feeling that nothing meaningful is allowed to be said here without someone trying to kill off discussion by hitting the report button. *Not every language discussion is a flamewar...*

---

### Post by LaRoza on 2008-10-21
> **CptPicard said:**
> It's getting reports?

Come on, whoever reported something... I get the feeling that nothing meaningful is allowed to be said here without someone trying to kill off discussion by hitting the report button. *Not every language discussion is a flamewar...*

Actually, the report was likely a misunderstanding, but misunderstandings have lead to wars...

(One of them was likely just part of a vendetta)

---

### Post by snova on 2008-10-21
> **LaRoza said:**
> I guess it can go to Recurring Discussions. Basically, it seems the answer is "C != C++", and it is just a redo of the why to love/hate C++.

It's also picked up a fair bit of language discussion in general.

PS. What does the report interface look like from the moderator's point of view? Where do they go?

---

### Post by pmasiar on 2008-10-21
> **LaRoza said:**
> Actually, the report was likely a misunderstanding, but misunderstandings have lead to wars...

(One of them was likely just part of a vendetta)

That would be exactly the wrong reason to close a thread. Freedom grows in sunshine. If any sleazy character could silence discussion with which he disagrees by reporting posts, some most interesting discussions would not happen. So far we remained withing limits of civility and arguing about the issues, is **that** a problem?

[http://en.wikipedia.org/wiki/Gresham%27s_Law](http://en.wikipedia.org/wiki/Gresham%27s_Law) says "Bad money drives out good." Same for discussion: bad debate will drive out good. Stifle good debate, and it will leave, only the bad will remain.

Maybe people who want to snuff out interesting debate by reporting it should get infractions, or even names published, so we will know them and could ignore them.

---

### Post by pp. on 2008-10-21
> **CptPicard said:**
> Come on, whoever reported something... I get the feeling that nothing meaningful is allowed to be said here without someone trying to kill off discussion by hitting the report button. 

> **pmasiar said:**
> Freedom grows in sunshine. If any sleazy character could silence discussion with which he disagrees by reporting posts, some most interesting discussions would not happen. So far we remained withing limits of civility 

...

Maybe people who want to snuff out interesting debate by reporting it should get infractions, or even names published, so we will know them and could ignore them.

If it's such an issue: I did report a post in this thread, and I did so because I felt the limits of civility have been crossed.

I will attempt to explain where I felt that such crossing has occurred, even though it might be in vain if the common sentiment here is that someone who reports post is sleazy and, hence, to be ignored.

The post I reported was this one:

> **pmasiar said:**
> his opinion is based on creating successful startup using Lisp which made him millionaire. How much is your opinion worth?

> I also took Lisp programming.  Aside from the insane number of parenthesis I had to type, I really feel that the language did not offer me anything useful.  

You should ask return of your tuition, you did not learned the most important lesson ;-)

> So as you can see, I also have an opinion.

My pet dog has opinion too. You forgot that this is not democracy but meritocracy. Noobs count the vote, smart people evaluate each opinion and weight it by the merit.

> Now, if Paul Graham and his colleague had chosen a different language other than Lisp for the ViaWeb project, I wager that the project would have succeeded nonetheless.  

Graham's millions says that only Lisp (and his smart colleagues) enabled him to beat the insane odds and the competition.

> I for one enjoy a roof over my head, and good food on the table.  

So you suggest that Graham is homeless bum? ;-)

I objected mainly to those phrases:

> using Lisp which made him millionaire. How much is your opinion worth?
> My pet dog has opinion too. 

I reported the post because telling another member that his or her opinion is not worth anything is far from respectful behaviour. It can be classified as harrassing and/or intimitating. It is, however, very well suited to make other people leave the discussion.

The argument in the post I reported centered on a person named Graham whose project done with Lisp made him a millionaire. Unfortunately, this thread does not name any facts relevant to that argument.

Standing for itself, the post I reported appears to argue that the project could not have made Graham a millionaire if Graham had used any other programming language, and the fact that Graham had become successful was an obvious proof that Lisp had been used.

Standing for itself, that argument is just silly. There are other people who have become much richer than that from producing software, and noone attributes that to their having used Lisp. Also, it is not very credible that the people posting here about their expertise in the use of the Lisp language are all millionaires.

To put it in a nutshell, I find it not conducive to the stated goal to belittle other members while citing very little evidence which actually refutes what the other member said.

That, however, is more of a side issue. My reason for reporting this post was the belittling of the other member.

---

### Post by LaRoza on 2008-10-21
> **snova said:**
> It's also picked up a fair bit of language discussion in general.

PS. What does the report interface look like from the moderator's point of view? Where do they go?

When you make a report, it is just a thread in a forum (where new threads can't be made otherwise). It has an automated title, a quote of the reported post, the reporters message, a link to the reported user's profile and a link to the reporter's profile (I think). 

We can post on this thread for discussions, although most reports are handled without discussion (spam, mostly). We used to have problems with knowing when a report was handled and to prevent cross moderation, but I suggested we use rankings to show a thread was done (those red ribbons occasionally on threads) and now with tags, we have a good solution. 

> **pmasiar said:**
> That would be exactly the wrong reason to close a thread. Freedom grows in sunshine. If any sleazy character could silence discussion with which he disagrees by reporting posts, some most interesting discussions would not happen. So far we remained withing limits of civility and arguing about the issues, is **that** a problem?

Well, the reported post could have been seen as inappropriate by some, and I followed it and posted that immediately to help prevent hasty action by other mods.

> 
Maybe people who want to snuff out interesting debate by reporting it should get infractions, or even names published, so we will know them and could ignore them.

You can guess who, can't you? :-)

---

### Post by snova on 2008-10-21
> **LaRoza said:**
> When you make a report, it is just a thread in a forum (where new threads can't be made otherwise). It has an automated title, a quote of the reported post, the reporters message, a link to the reported user's profile and a link to the reporter's profile (I think).

I suspected something like that. Some time ago I saw a forum that wasn't there otherwise in a screenshot posted by a moderator.

Unfortunately, C++ seems to fill a niche- OOP, low-level access, compiled, and a few other things. I don't know of any other languages with comparable attributes except D (unless you can tell me about them!), but it's still relatively new. It looks promising, though.

If only D had Qt bindings! But C++ support is still in an early stage. That, and I haven't figured out how to get it working in a kernel yet. It seems to require more support code than C++. I found a project written in D that I would like to use as an example, but I can't find any way to download it, nor the location of its SVN repository.

---

### Post by CptPicard on 2008-10-21
> **pp. said:**
> Standing for itself, the post I reported appears to argue that the project could not have made Graham a millionaire if Graham had used any other programming language, and the fact that Graham had become successful was an obvious proof that Lisp had been used.

It is Graham himself who argues in his essay that he was made a millionaire because he used Lisp, because it was such an agile language to develop in -- it is not pmasiar's claim.

Graham has got the millions to prove it, and as in this thread it is suggested that Lisp is not "practical" enough for real software development, I think that is a very solid counter-argument, and it *is* worth asking what a counter-opinion is worth, if Graham's opinion is worth $millions...

---

### Post by pp. on 2008-10-21
> **CptPicard said:**
> It is Graham himself who argues in his essay that he was made a millionaire because he used Lisp, because it was such an agile language to develop in -- it is not pmasiar's claim.

Graham has got the millions to prove it, and as in this thread it is suggested that Lisp is not "practical" enough for real software development, I think that is a very solid counter-argument, and it *is* worth asking what a counter-opinion is worth, if Graham's opinion is worth $millions...

I do not doubt for a minute that Lisp can be used for useful software development, having done so myself. Also, I do not doubt that said project made Graham a millionaire. I take your word for that.

I do take the self-assessment of anyone having made a fortune with a grain of salt, especially if single causes are claimed. Hence, a counter-opinion in that matter is not worth the same as a dog's opinion.

We all know that the nimbleness of the development process or the suitability of the software for any particular purpose often is not the decisive factor which makes or breaks a project. Market share or revenues are not reliable indicators for software quality or fitness of tools used in producing that software.

---

### Post by pmasiar on 2008-10-21
> **pp. said:**
> if the common sentiment here is that someone who reports post is sleazy and, hence, to be ignored.

Sorry for offending you with "sleazy" but quite often people try to silence me because they disagree but cannot argue on issues.

> "my pet dog"

IMHO everyone has right for opinion, but it does not mean that someone else has to take that opinion in count. On internet, everyone has to earn my time. Opinion by some random poster is almost worthless, unless that poster can argue why opinion is relevant and fact-based.

My pet dog was reference to [http://en.wikipedia.org/wiki/On_the_Internet,_nobody_knows_you're_a_dog](http://en.wikipedia.org/wiki/On_the_Internet,_nobody_knows_you're_a_dog) sorry I do not have dog - allergic :-)

> I reported the post because telling another member that his or her opinion is not worth anything is far from respectful behaviour. It can be classified as harrassing and/or intimitating. 

Low value of a random opinion is a fact, and facts tend not to care if they are respected or not. Random opinions are impossible to distinguish from random noise. Reminding about that fact is attempt to reduce the noise in forum discussion. IOW: even if someone has opinion, it does not mean s/he has to share it: before posting, consider if the opinion is based on some evidence and can defend it, or if it just increases the noise. 

I often do not post if someone said something close to my opinion, just thank the poster.

> The argument in the post I reported centered on a person named Graham whose project done with Lisp made him a millionaire. Unfortunately, this thread does not name any facts relevant to that argument.

Standing for itself, the post I reported appears to argue that the project could not have made Graham a millionaire if Graham had used any other programming language, and the fact that Graham had become successful was an obvious proof that Lisp had been used.

Some misunderstanding.

Fact 1: Graham is successful startup millionaire
Fact 2: Graham considers Lisp one of pillars of his success (along with work of other smart hackers  like [Rober Morris](http://en.wikipedia.org/wiki/Morris_worm) . Have you read the article? Not inspired? :-)

So argument that Lisp is not financially successful language is kinda flat, isn't it? Not supported by evidence?

> Standing for itself, that argument is just silly. There are other people who have become much richer than that from producing software, and noone attributes that to their having used Lisp. 

I do not follow your logic: One anecdote can disprove generic statement. Fact that  other people made more money using different language is completely irrelevant, but Graham disproves overly-generic statement that Lisp cannot be used for profit, or whatever poster said.

Sorry I may not be using proper terminology, I studied first order logic predicates 25 years ago in different language :-) but you get my drift?

Poster might want to argue how many millions were made by companies using which language, which would be more relevant (and Lisp would be less relevant), but poster never did that attempt, did he?

> Also, it is not very credible that the people posting here about their expertise in the use of the Lisp language are all millionaires.

Funny where you get that one from. I bet any millionaire has better things to do than waste time on forums :-)

My suggestion was, that opinion from a proven successful programmer (with wikipedia page and everything) is worth more than from just any random anonymous poster. If that poster can dig out supporting opinion from some known field expert, bring it on and we will dispute it, but without that I am strongly tempted to ignore it and go with opinions of field experts instead.

I am not telling that my opinion is worth more than any other random poster. I am just trying to link to opinions of (IMHO) experts, and follow the advice. Anybody is free to formulate own opinion. You know mine now :-)

---

### Post by LaRoza on 2008-10-21
> **pmasiar said:**
> 
IMHO everyone has right for opinion, but it does not mean that someone else has to take that opinion in count. On internet, everyone has to earn my time. Opinion by some random poster is almost worthless, unless that poster can argue why opinion is relevant and fact-based.

My pet dog was reference to [http://en.wikipedia.org/wiki/On_the_Internet,_nobody_knows_you're_a_dog](http://en.wikipedia.org/wiki/On_the_Internet,_nobody_knows_you're_a_dog) sorry I do not have dog - allergic :-)


Ha! I was right.

---

### Post by pmasiar on 2008-10-21
> **LaRoza said:**
> You can guess who, can't you? :-)

No, it takes me quite a long time to remember posters by {name: opinion} pair :-) Instead, I try to evaluate every post on merit, and respond as I feel fit :-)

---

### Post by LaRoza on 2008-10-21
> **snova said:**
> I suspected something like that. Some time ago I saw a forum that wasn't there otherwise in a screenshot posted by a moderator.

Unfortunately, C++ seems to fill a niche- OOP, low-level access, compiled, and a few other things. I don't know of any other languages with comparable attributes except D (unless you can tell me about them!), but it's still relatively new. It looks promising, though.


Try Objective-C.

That is my point also, C++ fills a niche.

---

### Post by LaRoza on 2008-10-21
> **pmasiar said:**
> No, it takes me quite a long time to remember posters by {name: opinion} pair :-) Instead, I try to evaluate every post on merit, and respond as I feel fit :-)

Oh, well I guess you'd have no way to see what was reported and by whom, so you wouldn't find an association.

---

### Post by snova on 2008-10-21
> **LaRoza said:**
> Ha! I was right.

That's a lot of tabs...

> **LaRoza said:**
> Try Objective-C.

That is my point also, C++ fills a niche.

Hmm, I don't know *anything* about that language yet. I'll probably take a better look at it after I get tired of D. A very strange syntax, at the least... Looks like the output of diff. :)

---

### Post by LaRoza on 2008-10-21
> **snova said:**
> That's a lot of tabs...

Everyone always says that, but they never see it when I do have a lot open. (So small that the close button is most of the tab). 

> 
Hmm, I don't know *anything* about that language yet. I'll probably take a better look at it after I get tired of D. A very strange syntax, at the least... Looks like the output of diff. :)
It is a strict super set of C, so valid C code is valid Objective C. My wiki has information on it.

---

### Post by dribeas on 2008-10-21
> **CptPicard said:**
> I suppose this sort of added knowledge of what template parameters actually are is kind of what I would be after ... then again, I never became a huge fan of, say, Java Generics either...


AFAIK, generics are much more limited than templates in many ways, including the fact that it applies type erasure (the compiler basically substitutes the type information with casts in and out of Object, a List<MyType> is converted by the compiler into a List (plain old Object list) and conversions are included in all method calls. Java generics don't support specialization either --this is a consequence of the former, as once the injected type is removed only one List of Object is present.


> **CptPicard said:**
> Do these kinds of mistakes actually happen much? Somehow it seems like being in the same category as private variables -- programmers should be "consenting adults" and will break into the private parts anyway if they want to.

Admittedly, while I know what const-correctness is supposed to be, I have not played enough with it to have much of a valid opinion. Just simply from a language-theoretic POV I do get this gut feeling that declaring your object const may help in trivial cases that you would manage yourself anyway, and will fail in more complex, surprising ways... you don't necessarily know where your object is going to end at when you pass it to some method, declared const or not.

You have access to the private parts if you must, the programmer of a library can completely hide the implementation of details and private parts. Even if it takes programmer effort it usually comes with additional exception safety (I am talking about the PIMPL idiom). Not that I consider it is required. Whenever I have used pimpl has been mainly for exception safety, and once to hide generated code (and tons of macros) from populating the rest of the project.

On const-correctness, besides the fact that you avoid changing data when you shouldn't, you can offer references to your internal data that are read-only, avoiding the cost of creating copies of the data just so that the caller won't modify your internal state. Of course, const-correctness is unneeded in pure functional programming, where there are no side effects.


> **CptPicard said:**
> Yes, I am aware of these. It's still sort of interesting that it's a language-external pattern that required the addition of templates, because the exception system is dangerous to begin with.

Also, RAII binds your stuff conceptually to the stack a bit too much for my taste... a GC at least tracks your object lifetime so that it can die independently on its own.

Not so much. The principle of RAII are destructors, and that has nothing to do with templates. Destructors are inherent to the language. Now, it is true that templates allow for a generic solution to a pointer holder that frees memory, but in most other cases, you will apply RAII without templates (closing a file descriptor or database connection)

Whether RAII binds your stuff to the stack or not, the simple answer is that it does so in just as much as not using RAII. You can have globals (if you like) that use RAII, or dynamically allocated objects that hold resources using this pattern (which can or cannot --even if probably should-- be handled through RAII themselves).

RAII is not just std::auto_ptr<> but any class that acquires resources during construction and frees them during destruction, whatever resource it is, however general or specific the class is.

Now, I don't see an advantage to letting objects live until they 'die independently on their own'. At the end, once you loose your last reference the object is 'dead' for your program, whether it has been freed or not. I could come up with a couple of reasons to prefer the C++ way: resources are freed instantly, no resource is yet-to-be-freed if it is unusable. The system does not need to block operations for GC. When the system runs GC the system performance degrades. First, the GC operations are not cheap, and at an unexpected point in your code, the system will just pause for GC. Then most GCs perform move the still-alive objects to new memory locations.

EDIT: Uhm... about closing the thread, besides one or two unfortunate posts, I believe that this is being an interesting, educated discussion.

---

### Post by pp. on 2008-10-21
> **pmasiar said:**
> Opinion by some random poster is almost worthless, unless that poster can argue why opinion is relevant and fact-based.

I am not telling that my opinion is worth more than any other random poster. I am just trying to link to opinions of (IMHO) experts, and follow the advice. Anybody is free to formulate own opinion. You know mine now :-)

I have read the appropriate posts very carefully indeed. I offer without any rancor at all the suggestion that you try and re-read some posts you appear to disagree with more carefully, with the same care you probably apply to pieces of code.

Said 'random poster' raised some valid points which would bear reading again. He or she also said some things I do not consider true or applicable to this thread, but that post is nowhere as random as you will have it be.

---

### Post by LaRoza on 2008-10-21
> **pp. said:**
> but that post is nowhere as random as you will have it be.

But the people are random. Anyone can post, so each post has to be judged. Naturally, it takes some effort to be able to judge and it is almost impossible for new users to really judge (so many times we hear "my friend said that..." and it turns out to be rubbish).

---

### Post by pp. on 2008-10-21
> **LaRoza said:**
> But the people are random. Anyone can post, so each post has to be judged. Naturally, it takes some effort to be able to judge and it is almost impossible for new users to really judge (so many times we hear "my friend said that..." and it turns out to be rubbish).

> All people and events are purely coincidential.

From the inside of the cover of a novel by Vonnegut.

---

### Post by slavik on 2008-10-22
> **pmasiar said:**
> 

snipped ...



By the same merit, Larry Page and Sergey Brin are millionaires if not billionaires and MapReduce is still a framework written in C++. Larry Ellison also has lots of moolah and his company was trying to sell what we call thin clients that were connected via dial up (this blew up in his face), ooh they did sell this other thing which was very experimental at this time ...I think they called it a relational database ... wonder what happened with that. ;)

If I can build a house better and faster with a toothpick than anyone else with a 100man professional construction crew and all usually used tools (cranes, etc.), then why shouldn't I use a toothpick? just because you can understand the instructions/process of using a toothpick for such a task?

---

### Post by boz on 2008-10-22
> **pmasiar said:**
> Yup, you just proved beyond reasonable doubt the lack of understanding of the important matters: Lisp syntax is trivial, trick (and power) is in different kind of semantics, which difference passed high above your head, luckily not hitting you ;-)

This is exactly why is so funny if anyone expresses opinion about Lisp based on syntax, and why everyone grokking Lisp at least a bit is ROFL. Thanks for expressing the point to clearly.

I do not doubt you can learn Lisp, if you want: your refusal to do so robs you from interesting learning experience.

I only said that I wasn't wild about its syntax.  I didn't say I refuse to learn the language because of it.  I'm not wild about the syntax of perl, either, but I still learned that one.  I just don't have time to learn a new language right now.  I work full time and going back to school for my Masters in Telecomm Engineering.  I'm taking a class in Wireless Sensor Networks in which I have to do a project with ns-2, so I'll have to learn TCL and possibly contribute my own C++ code to the project.  One new language is enough for the time being ;). Lisp sounds interesting and I've filed it in the back of my mind for later exploration.

Programming languages are a utility, period.  I will use them to make my computer do what you want it to, and try to pick the best one for the job.  By the way, I know I haven't been programming very long, but I've pushed out over 15000 lines of new (C++) code in my first year.  (I'm sure I have almost as much scripting code out there.)  Doesn't seem like much, but when you work for a company, 99% of your time is designing, documenting, reviewing, etc.  Coding is usually the easy part.  In my 15,000 lines of code, I've never once encountered a situation with C++ where I've had to say, "this is a real problem with the language".  Maybe that will happen over time.  But, I think if I use good design practices, that will never happen.

---

### Post by CptPicard on 2008-10-22
> **boz said:**
> I only said that I wasn't wild about its syntax.

... which *is* hilarious, but you'll get the joke eventually ;)

Treating entire syntax of Lisp as S-expressions which are expressed as Lisp-readable data structures (essentially, it's a Lisp list syntax tree) is exactly what lets you do a lot of the stuff with Lisp you can (in particular, arbitrary manipulation of code by code). Without the syntax, Lisp could not be Lisp.

> I'm taking a class in Wireless Sensor Networks in which I have to do a project with ns-2, so I'll have to learn TCL and possibly contribute my own C++ code to the project.

Hey, that's interesting. I wrote my Master's thesis in Sensor Networks (Data Gathering in Sensor Networks, Uni Helsinki 06, although it's in Finnish and in retrospect is garbage)... had a focus on esp. data gathering protocols that minimize different energy metrics as analyzed by linear programming models (some quadratic thrown in)...

Too bad the field is so large and diverse and at least back in 04-06 was in lacking of any cohesive theory that pulling stuff together into a good literature-based survey thesis was hell... anyway, at least results from ns-2 are quite familiar...

> 
Programming languages are a utility, period.

For a CS guy like me, that feels a bit as an understatement... but we've had a lot of interesting (and heated) discussions here about that. Some other CS guys (actually, usually they were not formally educated CS guys) refuse to recognize any language differences, and from Turing-completeness POV they are right. However, new languages have been created exactly because they communicate about programming ideas better, and because humans are language-using creatures, we want to have better symbolic-expression capabilities when working with computers.

The connection of language to computation and how that maps to our mind via the programming language is something that fascinates me a lot, and esp. because C++ needs so much explaining as to why things are the way they are, something feels a little bit amiss ;)

> But, I think if I use good design practices, that will never happen.

I'd rather not, but rather use a language where I don't have to. Most design patterns and best practices are attempted cures to a symptom.

---

### Post by dwhitney67 on 2008-10-22
> **boz said:**
> I only said that I wasn't wild about its syntax.  I didn't say I refuse to learn the language because of it.  I'm not wild about the syntax of perl, either, but I still learned that one.  I just don't have time to learn a new language right now.  I work full time and going back to school for my Masters in Telecomm Engineering.  I'm taking a class in Wireless Sensor Networks in which I have to do a project with ns-2, so I'll have to learn TCL and possibly contribute my own C++ code to the project.  One new language is enough for the time being ;). Lisp sounds interesting and I've filed it in the back of my mind for later exploration.

Programming languages are a utility, period.  I will use them to make my computer do what you want it to, and try to pick the best one for the job.  By the way, I know I haven't been programming very long, but I've pushed out over 15000 lines of new (C++) code in my first year.  (I'm sure I have almost as much scripting code out there.)  Doesn't seem like much, but when you work for a company, 99% of your time is designing, documenting, reviewing, etc.  Coding is usually the easy part.  In my 15,000 lines of code, I've never once encountered a situation with C++ where I've had to say, "this is a real problem with the language".  Maybe that will happen over time.  But, I think if I use good design practices, that will never happen.

+1000.

Don't concern yourself with what is "out there".  You did a great job at whatever you did.  I do not say this lightly.  I really mean it.  Even if your employer had required you to use a different language than C++.

Personally, I feel that the blokes using LIBRARY FUNCTIONS to program are the ones losing out.  Enough with the "Star Trek" nonsense where all is needed is to pass quantum cow manure through the deflector array to save the day.

C++ is not the language for every application.  But for some, it is used... and maybe for the wrong reason, but nevertheless it is used.  Once you have enough experience developing s/w, then it is time to migrate to a higher level.  Consider Systems Engineering (and I am not referring to Systems Administration, which is a joke in itself).

---

### Post by boz on 2008-10-22
> **CptPicard said:**
> ... which *is* hilarious, but you'll get the joke eventually ;)

Treating entire syntax of Lisp as S-expressions which are expressed as Lisp-readable data structures (essentially, it's a Lisp list syntax tree) is exactly what lets you do a lot of the stuff with Lisp you can (in particular, arbitrary manipulation of code by code). Without the syntax, Lisp could not be Lisp.

Sounds pretty cool.  It's at least a unique idea as far as I can tell.


> **CptPicard said:**
> Hey, that's interesting. I wrote my Master's thesis in Sensor Networks (Data Gathering in Sensor Networks, Uni Helsinki 06, although it's in Finnish and in retrospect is garbage)... had a focus on esp. data gathering protocols that minimize different energy metrics as analyzed by linear programming models (some quadratic thrown in)...

Too bad the field is so large and diverse and at least back in 04-06 was in lacking of any cohesive theory that pulling stuff together into a good literature-based survey thesis was hell... anyway, at least results from ns-2 are quite familiar...

It's still hell.  It's taking all the energy I have just to get all of the required reading out of the way.  I haven't really had any time to read ns-2 code yet.  I'm focusing mainly on time synchronization protocols, which as far as I can tell, there are none in ns-2 right now....at least not for WSNs.

> **CptPicard said:**
> For a CS guy like me, that feels a bit as an understatement... but we've had a lot of interesting (and heated) discussions here about that. Some other CS guys (actually, usually they were not formally educated CS guys) refuse to recognize any language differences, and from Turing-completeness POV they are right. However, new languages have been created exactly because they communicate about programming ideas better, and because humans are language-using creatures, we want to have better symbolic-expression capabilities when working with computers.

The connection of language to computation and how that maps to our mind via the programming language is something that fascinates me a lot, and esp. because C++ needs so much explaining as to why things are the way they are, something feels a little bit amiss ;)

I graduated Electronics Engineering, so programming hasn't always been the utmost of my concern.  As an undergrad, I mostly did Assembler and low-level C.  C++, to me, is in fact a high-level language! ;)  I start getting spoiled when I can make a program do exactly what it is I want it to do in under 1000 lines (although I can usually get those 1000 lines out there in a couple of hours).

> I'd rather not, but rather use a language where I don't have to. Most design patterns and best practices are attempted cures to a symptom.

I look at design patterns as saying, these things work in general and can be applied under most circumstances.  Best practices are a preventive measure against doing bad things with code.  In the end, it's always up to the programmer to not do bad things.  The language isn't going to do that for you.

---

### Post by CptPicard on 2008-10-22
> **boz said:**
> Sounds pretty cool.  It's at least a unique idea as far as I can tell.


Essentially, everything "extra" has just been stripped out of the syntax to make it totally uniform and conform directly to the format of the Lisp list datatype (or, more exactly, its reader representation so that it can be just read straight from where-ever). An interesting side note is that Lisp was originally an abstract notation of programs for analysis not on computer, but on pencil and paper and for putting programs on scientific papers. Then certain grad student wrote "eval" for it for a computer...

That way, you get essentially a meta-language... Lisp macros which transform arbitrary lists (not just valid Lisp code) into Lisp code can, be entire mini-compilers for sub-languages in their own right. :)

Lisp was also *very* early in bringing in lots of high-level concepts in 1958 and onwards already. It's a huge pity languages like that didn't take off outside of academia due to hardware constraints which are not such an issue these days anymore... our computing might look very different today.

(Of course, these days, the SBCL compiler can approach C speed...)

> 
It's still hell.  It's taking all the energy I have just to get all of the required reading out of the way.

I can actually remember having forgotten the first part of what I read for my thesis once I got through reading the latter part. :) Finally I managed to get my sources stabilized to something manageable... most of the papers in the field are remarkably bad too, which I am sure you have noticed... they are written fast, contain lots of errors etc...

> 
  I haven't really had any time to read ns-2 code yet.  I'm focusing mainly on time synchronization protocols, which as far as I can tell, there are none in ns-2 right now....at least not for WSNs.

Vaguely remember reading something about "cascading timeouts" in some paper. Wondering if anything came of that :)

By the way, Lisp would be an interesting fit for mapping expression trees on top of WSN. You would essentially specify the value to be computed by the network in Lisp (or a "sublanguage"), and then process that expression into some sort of execution plan to be run on the network and push it out there to the respective nodes...

> 
I graduated Electronics Engineering, so programming hasn't always been the utmost of my concern.  As an undergrad, I mostly did Assembler and low-level C.  C++, to me, is in fact a high-level language! ;)

Yeah, I can sort of see the engineering/CS division in this matter. It's perfectly understandable though... when you need hardware interfacing, you need hardware interfacing...

> I start getting spoiled when I can make a program do exactly what it is I want it to do in under 1000 lines (although I can usually get those 1000 lines out there in a couple of hours).

You'd be more spoiled by Lisp then ;) (Yes I am pushing it hard.. ;)

Another interesting feature is the REPL and the runtime environment which lets you essentially (even remotely) inspect and alter your running application by hot-swapping pieces of code. NASA fixed a space probe this way... now, if we only could get one of those running on a sensor node... :)

> 
I look at design patterns as saying, these things work in general and can be applied under most circumstances. 

An interesting comparison can be made between OOP design patterns and functional design patterns. There are lots of books written about OOP design patterns where all sorts of really weird sounding helper objects are introduced  just to make things happen... in functional design patterns, you usually are given more insight into the actual (mathematical) structure of the problem.

[http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)

> The language isn't going to do that for you.

Got to disagree most of the time with this, the language can do a lot in both its own design and in its own internal error-checking to either encourage programmer best-practices, or even better, be not too prone to falling flat on its face in the first place...

---

### Post by krazyd on 2008-10-22
From someone taking an undergraduate C programming course: thank you all very much. (Relatively) civil discussion, wide variety of opinions and some interesing points discussed. Great thread. Would read again. A++ :KS

---

### Post by dwhitney67 on 2008-10-22
> **CptPicard said:**
> ...NASA fixed a space probe this way... now, if we only could get one of those running on a sensor node... :)
\

What NASA are you writing about?  The "National Amature Sushi Apprentices"?

NASA does not do any worthy development (anymore).  That is left up to contractor companies that work for the lowest denominator... money.  Maybe my intel/on-the-job-experience is outdated.

---

### Post by boz on 2008-10-22
I like the idea of hot-swapping code during execution time.  Sounds a little dangerous, though.  But, I do like to live dangerously.

---

### Post by dwhitney67 on 2008-10-22
> **krazyd said:**
> From someone taking an undergraduate C programming course: thank you all very much. (Relatively) civil discussion, wide variety of opinions and some interesing points discussed. Great thread. Would read again. A++ :KS

Thank you!   But please, and I implore this... do not ever resurrect a similar thread.  It is similar to murder.

---

### Post by boz on 2008-10-22
> **dwhitney67 said:**
> Thank you!   But please, and I implore this... do not ever resurrect a similar thread.  It is similar to murder.

This is the first time I've ever partook in a thread such as this.  I'm quite surprised at how akin a programming language can be to a religion.  I merely use them as a tool to get a job done.

---

### Post by dwhitney67 on 2008-10-22
> **boz said:**
> I like the idea of hot-swapping code during execution time.  Sounds a little dangerous, though.  But, I do like to live dangerously.

If living dangerous is your thing.. then you should take a taxi ride along the Bangkok (Thailand) expressway during rush hour.

Swapping code during runtime (with today's technology) is only possible with a multi-processor system and a savvy OS... which, to the best of my knowlegde, does not exist yet.  I may be wrong though... today I thought thunderstorms were on the way, and behold, they passed just south of my position!

---

### Post by LaRoza on 2008-10-22
> **dwhitney67 said:**
> What NASA are you writing about?  The "National Amature Sushi Apprentices"?

NASA does not do any worthy development (anymore).  That is left up to contractor companies that work for the lowest denominator... money.  Maybe my intel/on-the-job-experience is outdated.

The point was that using Lisp made it possible to debug the code while it was running, 1000000 miles away (give or take a couple of zeros).

---

### Post by pmasiar on 2008-10-22
> **slavik said:**
> By the same merit, Larry Page and Sergey Brin are millionaires if not billionaires and MapReduce is still a framework written in C++.

Let's eliminate all fluff, down to bare logic: 

1) Opinon1 by some poster: "technology X is no good for A (making money)" 
2) I said: Graham says X was excellent for A (which according to logic I was taught refutes opinion1).
3) You say: Z is good for A. Which, is true and I do not dispute it's validity, but according to logic, is irrelevant to "X is no good for A".

What gives?

---

### Post by rnodal on 2008-10-22
OP, nice demo! Sorry that your post turned into another...language discussion.

-r

---

### Post by dwhitney67 on 2008-10-22
> **LaRoza said:**
> The point was that using Lisp made it possible to debug the code while it was running, 1000000 miles away (give or take a couple of zeros).
Can you please give specifics?

The moon is a approximately 239,000 miles away, so you must be referring to a deep-space probe, one that is (possibly) managed by JPL (aka California Institute of Technology).

---

### Post by CptPicard on 2008-10-22
> **boz said:**
> I like the idea of hot-swapping code during execution time.  Sounds a little dangerous, though.  But, I do like to live dangerously.

> **dwhitney67 said:**
> 
Swapping code during runtime (with today's technology) is only possible with a multi-processor system and a savvy OS... which, to the best of my knowlegde, does not exist yet.

At least as long as a function is not being evaluated right at the moment, swapping it is trivial under a Lisp REPL, and I would suspect that even if there is a thread in the function, it would just finish with the old code and your new function would be in use as soon as you get a new fresh entry into an evaluation of that function.

> **boz said:**
> This is the first time I've ever partook in a thread such as this.  I'm quite surprised at how akin a programming language can be to a religion.  I merely use them as a tool to get a job done.

At least for me most of what one might call "religiousness" really comes from having had experiences of enlightenment that have been valuable for me for the rest of my life really, as a problem-solver and in all languages... they have made me think differently about math, problems, algorithms, and language. And most those experiences have been received from some other languages than any C-derivative, really. It is in particular fascinating to all of a sudden see how theory and some big-picture issue about the structure of some particular problem I'm solving just nicely fit into place in an elegant abstraction, regardless of all the bit-pushing details that may be going on under the hood...

The biggest "religious cult" around here really is the one of the C- and assembly-coding speed kiddies who pride themselves on not knowing "easier" higher-level languages and whose faith is in the magical computational power of the pointer...

---

### Post by pmasiar on 2008-10-22
> **boz said:**
> I just don't have time to learn a new language right now.

Fine, then just don't post opinions abut issues you have little familiarity and/or understanding, because it might confuse innocent minds of other readers - and we cannot have that, can we? :-)

> Programming languages are a utility, period.

More helpful for your understanding of programming would be to consider as priority for a **programming language to be used to communicate computing concepts between human minds, and only as side effect by computers to execute the code**. Compilers are mature technology, we can compile and execute anything, just some company can hire bunch guys for to implement it. Hard part is to design a way how to express computing concept in a way that other human (or same human year later) understands what is going on.

Power of [http://en.wikipedia.org/wiki/Lisp_programming_language](http://en.wikipedia.org/wiki/Lisp_programming_language)  is that it was designed as theoretical concept (to think about list algorithms), as mathematical notation, not as practical way to execute code: back then, FORTRAN was the only high-level language. So it is unconcerned by practical limitation (which were much more severe back then), and focuses on expresiveness.

---

### Post by pp. on 2008-10-22
> **pmasiar said:**
> Let's eliminate all fluff, down to bare logic: 

1) Opinon1 by some poster: "technology X is no good for A (making money)" 

I have seen one poster state 'technology X does not in and of itself make a person using technology X more skilful'. I have seen the same poster state 'the claim that technology X was a decisive factor for A might be false'. I have not seen someone state that 'technology X can not be used for A'. 

Could you please prove your premise?

---

### Post by pmasiar on 2008-10-22
> **CptPicard said:**
> Another interesting feature is the REPL and the runtime environment which lets you essentially (even remotely) inspect and alter your running application by hot-swapping pieces of code. NASA fixed a space probe this way... now, if we only could get one of those running on a sensor node... :)

Forth allows you to do that (and more), and runs in trivial amount of memory: 10K is enough for development, can be compressed even to less for runtime. It was designed for such constraints.

---

### Post by LaRoza on 2008-10-22
> **dwhitney67 said:**
> Can you please give specifics?

The moon is a approximately 239,000 miles away, so you must be referring to a deep-space probe, one that is (possibly) managed by JPL (aka California Institute of Technology).

[http://www.flownet.com/gat/jpl-lisp.html](http://www.flownet.com/gat/jpl-lisp.html)

Sorry, it was 100 million miles.

Section: **1994-2000 - Remote Agent**

Anyone who argues with that article (which mentions C++ specifically, and why Lisp was used instead) has serious issues.

---

### Post by pp. on 2008-10-22
> **pmasiar said:**
> Forth allows you to do that (and more), and runs in trivial amount of memory: 10K is enough for development, can be compressed even to less for runtime. It was designed for such constraints.

Smalltalk does it as well. I rather suspect that quite a number of 'workspace environments' (of which Smalltalk is a subclass) allow you to work on your code while it's running. The Newton with its Newton Script comes to mind.

---

### Post by dwhitney67 on 2008-10-22
> **CptPicard said:**
> At least as long as a function is not being evaluated right at the moment, swapping it is trivial under a Lisp REPL, and I would suspect that even if there is a thread in the function, it would just finish with the old code and your new function would be in use as soon as you get a new fresh entry into an evaluation of that function.
...

Sorry for my ignorance, but what is a REPL?

As for replacing functions, I assume you are writing about replacing opcodes in memory, where a program is currently running.  If the new function, with its augmented capabilities just happens to exceed the footprint of the inferior/previous function, then there is a possibility that inserting it into the application will cause the heavens to excrete fire.

There are cases where a mere update to a constant or conditional statement may be possible, but for larger changes to a function, I think that you are mislead.

I have experience with ping/pong RAM areas, where code can be stored.  Unless the change to a function is "trivial", I cannot think of an instance where it would be possible to substitute a series of opcodes into the footprint of an existing series of opcodes.  I also can't think of a reason why anyone would risk modifying a one/only area of RAM for a s/w update.

Basically, if s/w is going to be updated on the fly, the application will need to be restarted.  I can think of (but not from experience), that terrestrial systems, with their .NET or CORBA protocols, may be immune to this if the s/w is updated on a particular system.  Any running application, of course, will need to wait until the affected system is restarted.

---

### Post by LaRoza on 2008-10-22
> **dwhitney67 said:**
> Sorry for my ignorance, but what is a REPL?

Basically, if s/w is going to be updated on the fly, the application will need to be restarted.  I can think of (but not from experience), that terrestrial systems, with their .NET or CORBA protocols, may be immune to this if the s/w is updated on a particular system.  Any running application, of course, will need to wait until the affected system is restarted.

See the link I posted.

[REPL](http://en.wikipedia.org/wiki/REPL)

---

### Post by nvteighen on 2008-10-22
> **CptPicard said:**
> 
Treating entire syntax of Lisp as S-expressions which are expressed as Lisp-readable data structures (essentially, it's a Lisp list syntax tree) is exactly what lets you do a lot of the stuff with Lisp you can (in particular, arbitrary manipulation of code by code). Without the syntax, Lisp could not be Lisp.


Again, that's the magic of recursive syntax that also is applied to natural languages. In theory, you could have infinite subordinate clauses in a sentence in any natural language without any trouble... Why? Because there are elements that are able to subordinate a structure of type A to another of the same type. Of course, in practice (as in Lisp), human memory is the main obstacle that proves that impossible in reality... but it's there as a possibility.

Lisp does the same. And that's because it uses a very simple syntax, but recursive. This plus the metalinguistic ability (symbolic analysis) gives this language a power no other programming languages families have even tried to adopt; maybe because they're so much Lisp-ish that any language that adopts them will turn out to be another new Lisp dialect...

---

### Post by dwhitney67 on 2008-10-22
> **LaRoza said:**
> [http://www.flownet.com/gat/jpl-lisp.html](http://www.flownet.com/gat/jpl-lisp.html)

Sorry, it was 100 million miles.

Section: **1994-2000 - Remote Agent**

Anyone who argues with that article (which mentions C++ specifically, and why Lisp was used instead) has serious issues.
Funny that you mention that article.  I read it too (after Googling).

Here's something to ponder... that is, a quote from the author of the article...

"I came to JPL in 1988..."

Notice the "I".

So simply because one person, not necessarily an expert of any sort, but just a person who happened to work at JPL (for a brief period), is all of the sudden a LISP saint?

He is probably correct that the underlying problem existed with a C application, but that does not, and should not, infer that C is a poor language.

The bottom line is that the author of that article is expressing his opinion of a situation in which he may have not been at the upper echelons of the JPL organization to understand their rationale from shifting away from LISP.

Or maybe he was... I don't know, and neither do you!

---

### Post by CptPicard on 2008-10-22
> **dwhitney67 said:**
> 
As for replacing functions, I assume you are writing about replacing opcodes in memory, where a program is currently running.  If the new function, with its augmented capabilities just happens to exceed the footprint of the inferior/previous function, then there is a possibility that inserting it into the application will cause the heavens to excrete fire.

This is where the Lisp runtime compiler / code-loader comes into play. For example SBCL compiles functions into native on the fly as you define them, and you really can swap stuff pretty much at will -- although I would have to test what happens when I actually swap code from under a running thread -- as I said, my suspicion is the old code finishes running as is. It's an interesting question...

So no, we're not rewriting opcodes straight into RAM the way you suggest, but runtime code-replacement itself is nothing strange in Lisp -- and it's certainly not as high-level as just rewriting some evaluated expression tree, which would not be the same thing. Although, you can easily do *that* in Lisp as well --- then it becomes "runtime script rewriting" :)

---

### Post by boz on 2008-10-22
> **pmasiar said:**
> Fine, then just don't post opinions abut issues you have little familiarity and/or understanding, because it might confuse innocent minds of other readers - and we cannot have that, can we? :-)

At no point in time have I posted an opinion about Lisp other than "I'm not wild about its syntax" or "it sounds interesting and unique".  My opinion about syntax is only skin-deep and never have I claimed that there are fundamental, underlying flaws with the language.  I can't, because I don't know anything about it yet, which I've been honest about from the start.

---

### Post by LaRoza on 2008-10-22
> **dwhitney67 said:**
> Funny that you mention that article.  I read it too (after Googling).

Here's something to ponder... that is, a quote from the author of the article...

The bottom line is that the author of that article is expressing his opinion of a situation in which he may have not been at the upper echelons of the JPL organization to understand their rationale from shifting away from LISP.

Or maybe he was... I don't know, and neither do you!

I pondered it and found it to be not related to this discussion. It was a reference for my statement.

The bottom line is that C++ couldn't do what Lisp could do, and that was needed to do the work.

---

### Post by CptPicard on 2008-10-22
The author of the article, Erann Gat, has apparently recently begun to have doubts...

[http://groups.google.com/group/comp.lang.lisp/msg/6f75cfb5a289d3f6](http://groups.google.com/group/comp.lang.lisp/msg/6f75cfb5a289d3f6)

It is noteworthy though that I really don't think he means C by those other languages that can be productive in, in addition to Lisp :)

For all I care, if Common Lisp was modernized a little bit around some of the old rough edges (which admittedly help the compiler to produce fast code though) and had continuations support added that allowed for a "yield" generator-producing function in the middle of any environment, I would have very little reason to code in other languages, extreme speed requirements nonwithstanding...

---

### Post by dribeas on 2008-10-22
> **dwhitney67 said:**
> Swapping code during runtime (with today's technology) is only possible with a multi-processor system and a savvy OS... 

There has always been ways of doing that, even in C. I did that back in '96 with TCL/TK (code was sent over the wire on a conference meeting software) and then in Java for the same system (bytecode sent over the wire and loaded into the VM).

In just any language you can do dynamic library loading/unloading and replace a library with another. In general there is just a substrate that you cannot replace, or can you? Linux used to have a loader that replaced the whole windows operating system. Symbian OS can be upgraded in mobiles through a wire with support from the operating system and my Siemens DVB-T recorder operating system (linux based) can be upgraded/changed over the air (from the broadcasting company) or through USB/ethernet.

From my experience, it is much easier to implement with scripting languages, then with bytecode languages and finally harder to do with compiled languages. But that does not mean that is not doable. From my own complexity rating I can see a trend: it is easier with the more providing systems. If the system does not provide anything it is harder than if it has a virtual machine (JVM byte code interpreter) and then easier if the system is a full interpreter (TCL/TK). On the other hand, the interpreter/VM cannot be upgraded (unless you fall back to the mechanisms for compiled native code) which should not be an issue in most of the cases.

---

