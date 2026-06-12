---
title: "LISP, C++, C, Java???"
date: 2006-04-25
forum: Programming Talk
---

### Post by n0dl on 2006-04-25
Hello everybody. Can someone suggest a good first langauge to learn? My friend need help picking a good first computer language. I was considering he should learn one of the four above. At the moment I am leaning more toward Java or C. Your suggestions are appreciated :)

---

### Post by RavenOfOdin on 2006-04-26
I'd say your friend should go with C++ - in the long run. Not only is it one of the main programming languages, and used in pretty much every system, you can do whatever you want with it.

But since it would be easier to learn the basics first, my official response is "C."

---

### Post by LordHunter317 on 2006-04-26
Except C doesn't teach the basics of anything, but C.

I'll repeat my standard recommendations of *How to Design Computer Programs* and *Structure and Intreperation of Computer Programs*.  At this point, you should be focused on the concepts of how to write a computer program and the thinking required to do so rather than learning how to implement such things in a single language.

---

### Post by adamkane on 2006-04-26
Another one of those endless debates with no answer. I vote for Ruby.

Whatever you decide to learn, use the O'Reilly series.

---

### Post by tsrjzq on 2006-04-26
to be a good programmer, C and C++ are necessary. others can be learned quickly on the basis of C or C++, I think. 
for script laguage, python will be a good choice.

---

### Post by GoldBuggie on 2006-04-26
I second the last comment.

Learn C/C++. You will not only learn programming but also how the internals of the computer work. Held a teaching course "C++ for Java Programmers" and I was supriced of how little knowledge Java programmers had of computerinternals(streams, memory layout etc)(No ill intend meant with this statement just something I observed).

BUT...and this is  the thing...what do you want  to do with your programming knowledge? If you  feel that it might become a future thing then decide between C/C++, Java or C#.

Some tips:
Java is for: Networkprogramming.
C/C++: Realtime, embedded-devices, applications and cool airplane guidence systems.
C#: Very nice for gui-application usage together with database.

Oh well...it isn't easy...but as former post said...learn C/C++ and the rest is easy from there. Learning something else first might put you in the "C/C++ is so hard" catogory which is a bad thing. Start with it at the beginning and the other languages will be easy.

---

### Post by RavenOfOdin on 2006-04-26
[QUOTE=LordHunter317]Except C doesn't teach the basics of anything, but C.
[/QUOTE]

*Absolutely* wrong.

C++ is an enhanced version of C - both of the languages bear enough of a similarity at their fundamental levels to be considered so - and it behaves accordingly. That comment is almost like saying "HTML doesn't teach the basics of web design."

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=GoldBuggie]Learn C/C++. You will not only learn programming but also how the internals of the computer work.[/quote]Most computer programming requires knowing very little of how internals works.  And if you want to learn how the internals of a computer work in a meanigful way, it's better to take a hardware course designed to teach that, then attempt to approach it from the software side.

> and I was supriced of how little knowledge Java programmers had of computerinternals(streams, memory layout etc)(No ill intend meant with this statement just something I observed).And if they can write working code without having to know it, this is an excellent thing.


> Some tips:
Java is for: Networkprogramming.No, it's for many more things that that.  Network programming isn't even common in Java.

> Oh well...it isn't easy...but as former post said...learn C/C++ and the rest is easy from there.No, it isn't, because they're not focused on what you need to learn first.  They flood you with generally irrelevant implementation and platform details.

[quote=RavenOfOdin]*Absolutely* wrong.[/quote]No, you're absolutely and totally wrong.  The correct way to do something in C++ is never the correct way to do something in C, and vice-versa.

> C++ is an enhanced version of C - both of the languages bear enough of a similarity at their fundamental levels to be considered soNo, they don't.  They have completely dissimilar:[list][*]Type systems[*]Standard APIs[*]File handling[*]String handling[/list]to name just a few. 

Learning to program C *correctly* doesn't teach you correct C++.  And vice-versa.

As a general rule, the fact that C++ compilers can compile most C code is meaningless.  Good, correct, best-practice following C++ looks nothing like C.

>  - and it behaves accordingly. No, it doesn't.

---

### Post by RavenOfOdin on 2006-04-26
[QUOTE=LordHunter317]Most computer programming requires knowing very little of how internals works.[/quote]

What's ASM, chopped liver? :p

[QUOTE=LordHunter317]
No, you're absolutely and totally wrong.  The correct way to do something in C++ is never the correct way to do something in C, and vice-versa.

. . .

No, they don't.  They have completely dissimilar:[list][*]Type systems[*]Standard APIs[*]File handling[*]String handling[/list]to name just a few. 
[/quote]

So you're saying that functions are structured differently, and header files as well? That the simplest of commands and operators are used differently? I think not.


[QUOTE=LordHunter317]
Learning to program C *correctly* doesn't teach you correct C++.  And vice-versa.
[/quote]

See above.

[QUOTE=LordHunter317]
As a general rule, the fact that C++ compilers can compile most C code is meaningless.  Good, correct, best-practice following C++ looks nothing like C.
[/quote]

And the fact that the preprocessor cannot compile C code is in the end meaningless, but does it in any way influence how C/C++ looks?

That's all for now, I'll check back here when I get home.

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=RavenOfOdin]What's ASM, chopped liver? :p[/quote]It's programming that does require knowing how *some* internals work.

> So you're saying that functions are structured differently, and header files as well?Yes, they are.  They must be, because of C++'s richer type system.

>  That the simplest of commands and operators are used differently? I think not.The 'simplest of commands and operators' that C and C++ share in common they share in common with *almost all high-level languages*, so this is an obvious non-sequitur.

> See above.A non-sequitur is a non-sequitur no matter how many times you repeat it.  How about debating me on point instead of just trolling?  Eveything I stated was you know, a *fact*.

> And the fact that the preprocessor cannot compile C code is in the end meaningless,Non-sequitur.  You're confusing capability with desire. My entire point is just because something is permissible doesn't mean it's desirable.

> but does it in any way influence how C/C++ looks?Yes, it umm, does.  Good C++ looks nothing like good C.  In fact, good C++ won't even compile as C.  And good C is poor C++, because you cannot use the advances C++ brought you.

> That's all for now, I'll check back here when I get home.If this is the level of debate you're holding yourself too, please don't.  Either have a discussion on level or bow out, but please stop being (apparently) intentionally obtuse and constructing strawmen and obvious non-sequiturs.

---

### Post by Jessehk on 2006-04-26
> **LordHunter317]Except C doesn't teach the basics of anything, but C.

I'll repeat my standard recommendations of *How to Design Computer Programs* and *Structure and Intreperation of Computer Programs*.
[/QUOTE]
I'll take academics' word for it, and agree with you that it is a good book. My problem with it is that assumes you are comfortable with advanced concepts in mathamatics. And no, I am not interested in starting a 500-word quoting competition.  said:**
> 
At this point, you should be focused on the concepts of how to write a computer program and the thinking required to do so rather than learning how to implement such things in a single language.

Agree completely. I learned C (and later C++, Python, Ruby), and now all I know with C is how C works.

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=Jessehk] My problem with it is that assumes you are comfortable with advanced concepts in mathamatics.[/quote]Yes, it's not a hand-holding book, which is a negative.  I'm pretty much of the mind at this point though that the best way to learn is a proper education, which is difficult for many to acquire.

---

### Post by MichaelZ on 2006-04-27
[quote=n0dl]Hello everybody. Can someone suggest a good first langauge to learn? My friend need help picking a good first computer language. I was considering he should learn one of the four above. At the moment I am leaning more toward Java or C. Your suggestions are appreciated :)[/quote] 
IMHO, C++ (ISO C++) is a good language to start with. You can then relatively easy switch to another language (e.g., Java, C).

Lisp is essentially used in artificial intelligence and I am not sure it would make a suitable first language. May be later, if you intend to study artificial  intelligence.

Best wishes,
Michael

---

### Post by malavar on 2006-04-27
if its your first language, id suggest something simple like perl, it has syntax similar to C and is very easy to learn. BUT also it depends on what your reasons are for programming, are you programming as a hobby right now? or are you seeking a career in programming. anyways id go with perl; at least read a small book on it, that way you get a nice intro to computer programming while avoiding many advanced topics until your well developed into design and logic of programs. 
most likely your going to be developing command line apps anyways while you learn the keywords and syntax of C or java... 
a good book is : oreilly learning perl, theres also an online ebook i found here: [http://www.unix.org.ua/orelly/perl/learn/index.htm](http://www.unix.org.ua/orelly/perl/learn/index.htm)

---

### Post by RavenOfOdin on 2006-04-27
@LordHunter317: Your style sounds more like arguing than debating. And no matter who is right, I have lost absolutely all interest in carrying said debate on. You may interpret the above however you wish, I'm done. I didn't come here to start a bitching contest and I'm going to stop it before it gets out of hand.

[QUOTE=malavar] anyways id go with perl; at least read a small book on it, that way you get a nice intro to computer programming while avoiding many advanced topics until your well developed into design and logic of programs. 
most likely your going to be developing command line apps anyways while you learn the keywords and syntax of C or java... 
a good book is : oreilly learning perl, theres also an online ebook i found here: [/QUOTE]

Sams books FTW! :D

---

### Post by LordHunter317 on 2006-04-27
[QUOTE=MichaelZ]Lisp is essentially used in artificial intelligence and I am not sure it would make a suitable first language.[/quote]The books I noted originally, both teach in Scheme, which is a LISP.

LISP is actually ideally suited to being a teaching language for lots of reasons.  There are also several as to why it is not, for different reasons.  But if your goal is to learn how to think about how to design programs and algorithms, then language is rather irrelevant, quality of the text is important important.  Those are probably some of the best texts out there.

[quote=RavenOfOdin]@LordHunter317: Your style sounds more like arguing than debating.[/quote]It's nothing of the sort.  I'm being short beceause you're being apparently obtuse with me in your responses, which is offensive.  

If you'd debate on level, I'm more than reasonable.  My problem is you're not apparently being reasonable at all.  

> I didn't come here to start a bitching contest and I'm going to stop it before it gets out of hand.Then next time, please don't insult whoever you're having any discussion with by responding to their points with a non-sequitur.

---

### Post by asimon on 2006-04-28
[QUOTE=MichaelZ]IMHO, C++ (ISO C++) is a good language to start with. You can then relatively easy switch to another language (e.g., Java, C).[/quote]
IMO C++ isn't a very good language for beginners. I saw it used in beginner's courses and saw the students bother with pointers, memory management, castings, syntax and many others C++ thingies instead of focusing on the more important stuff.

[QUOTE=MichaelZ]
Lisp is essentially used in artificial intelligence and I am not sure it would make a suitable first language. May be later, if you intend to study artificial  intelligence.
[/QUOTE]
At least LISP and it's children have the advantage being extremly simple languages, for example there isn't much syntax to learn so a student can focus more on the important concepts instead of language idiosyncrasies.

IMO it's most valuable to get a good understanding of the fundamental concepts of progarmming languages. If you reach that goal, learning (and understanding) specific languages will be much easier and you a better programmer.

---

### Post by MichaelZ on 2006-04-28
[quote=asimon]IMO C++ isn't a very good language for beginners. I saw it used in beginner's courses and saw the students bother with pointers, memory management, castings, syntax and many others C++ thingies instead of focusing on the more important stuff.
[/quote] 

C++ is not an easy language. I have learn it by myself when developing an MFC application and having only some knowledge in C and Java.

If C++ is teached in a wrong way, then it can be a hell for the student.

C++ is an excellent language, but need to be teached with methodology. Moreover, it should be avoided to mix C and C++.

[quote=asimon]
At least LISP and it's children have the advantage being extremly simple languages, for example there isn't much syntax to learn so a student can focus more on the important concepts instead of language idiosyncrasies.
[/quote] 
IMO Lisp is not so easy and I would not choose it as first language. IMO, a first language should be general enough to give you a vision of all the possibilities (console applications, GUI, etc.) and programming paradigms.

[quote=asimon]
IMO it's most valuable to get a good understanding of the fundamental concepts of progarmming languages. If you reach that goal, learning (and understanding) specific languages will be much easier and you a better programmer.[/quote] 
Yes, I agree. Understanding the fundamental concepts of programming languages is very important.

C++ for example offers several progamming paradigms. You can learn procedural programming, OOP, and so on. This is IMO really useful.

Anyway, you should never blindly follow the advices of someone, but give a look yourself. Have a look at the different languages, ask some people's advice, try yourself and then choose the progamming language  that most fit your wishes and knowledge.

Best wishes,
Michael

---

### Post by asimon on 2006-04-28
[QUOTE=MichaelZ]IMO, a first language should be general enough to give you a vision of all the possibilities (console applications, GUI, etc.) and programming paradigms.[/quote]
IMO GUI is absolutly worthless in teaching programming, it only distracts. Programming GUIs (not usability) is really bathtube stuff, i.e. can be easily and very quickly learned once you understand the underlying concepts and thinking. Simple primitive console input/output is more than enough for the start and bindings for different GUI toolkits are available for most languages should the need be there.

[QUOTE=MichaelZ]
C++ for example offers several progamming paradigms. You can learn procedural programming, OOP, and so on. This is IMO really useful.[/quote]
But still too many nasty things get into your way when trying to concentrate on the concepts.

There are multi-paradigm languages like Oz which support much more than C++, like for example functional programming, (transparent) distributed programming, constraint and logic programming, but I see no big advantage in sticking to a single language for teaching these different paragidms instead of using different languages which are (hopefully) easy and straight-forward in their domain.

Anyway, as LordHunter wrote, the quality of the teaching itself is much more important then the used language. And having read the Abelson and Sussman book myself I can affirm that it's one of the best books ever written to really learn programming and not just learning some programming language.

So if your goal is to quickly be able to hack some GUI apps or writing device drivers for the Linux kernel then starting with Lisp is not the way to go, but if you want to dig deeper and get a profound understanding of concepts first, then starting with Lisp is good just because those great books are using Lisp.

---

### Post by MichaelZ on 2006-04-28
[quote=asimon]IMO GUI is absolutly worthless in teaching programming, it only distracts. Programming GUIs (not usability) is really bathtube stuff, i.e. can be easily and very quickly learned once you understand the underlying concepts and thinking. Simple primitive console input/output is more than enough for the start and bindings for different GUI toolkits are available for most languages should the need be there.
[/quote] 
Of course, I did not mean that you have to learn GUI from the beginning, but as an advanced topic. As you said simple primitive console input/output is more than enough for the start.

Anyway, you do not have to underestimate GUI programming. Even if there are several toolkits to help you, developing a good GUI is not that easy. And I know something myself as I develop GUI with Qt, WxWidgets and AWT/Swing.

[quote=asimon]
But still too many nasty things get into your way when trying to concentrate on the concepts.
[/quote] 
Not really. You can begin with simple things and increase the complexity progrssively.

[quote=asimon]
There are multi-paradigm languages like Oz which support much more than C++, like for example functional programming, (transparent) distributed programming, constraint and logic programming, but I see no big advantage in sticking to a single language for teaching these different paragidms instead of using different languages which are (hopefully) easy and straight-forward in their domain.
[/quote] 
Here I not fully agree. Of course you should not sticky to a language for all the paradigms and is better to have a wide vision. Anyway, if you learn with a multi-paridgm language, you will not have the necessity to re-study the fundaments of the new language when you change paradigm.
 
[quote=asimon]
Anyway, as LordHunter wrote, the quality of the teaching itself is much more important then the used language. And having read the Abelson and Sussman book myself I can affirm that it's one of the best books ever written to really learn programming and not just learning some programming language.
[/quote] 

Yes, I fully agree with you and LordHunter. 

I find the books written by Bjarne Stroustrup really good and useful. The Design and Evolution of C++ is very useful to understand the C++.

[quote=asimon]
So if your goal is to quickly be able to hack some GUI apps or writing device drivers for the Linux kernel then starting with Lisp is not the way to go, but if you want to dig deeper and get a profound understanding of concepts first, then starting with Lisp is good just because those great books are using Lisp.[/quote] 
I think that here we have quite different opinions :). 

I still think that C++ is a better language to start with, but this is just me :).

Best wishes,
Michael

---

### Post by asimon on 2006-04-28
[QUOTE=MichaelZ]Anyway, you do not have to underestimate GUI programming. Even if there are several toolkits to help you, developing a good GUI is not that easy. And I know something myself as I develop GUI with Qt, WxWidgets and AWT/Swing.[/quote]
Yes, I meant just the task of using the widgets to compose some interface, that is easy. It's true that making good GUIs, as in good usability (which is a very interesting field itself), is not easy and most programmers have no idea how to make good GUIs.

[QUOTE=MichaelZ] 
Not really. You can begin with simple things and increase the complexity progrssively.[/quote]
Of course, that's always the way to go. If you learn how to design programs with LISP its not otherwise. But you don't have to bother with many things you have to in C++ which don't increase your knowledge and understanding in the concepts but only your knowledge in C++.

[QUOTE=MichaelZ] 
Here I not fully agree. Of course you should not sticky to a language for all the paradigms and is better to have a wide vision. Anyway, if you learn with a multi-paridgm language, you will not have the necessity to re-study the fundaments of the new language when you change paradigm.[/quote]
Yes, but to learn a new paradigm you have to learn new constructs anyway, even if you stay in the same language. In my case I learned functional programming with SML and switched to Prolog for learning logic programming. There wasn't much language learning involved before we could start doing intersting things in Prolog, a very short introduction was enough. It's also a very clear cut in that now you do something different, no longer functional programming but logical and are not temped to solve some things in a previously learned paradigma. But in the end this again comes down to the quality of teaching. I saw once an Oz course teaching beginners OO, procedural, logic and functional programming. Sticking to one language wasn't helpful in this case, at the end of the course the students were just confused.
 
[QUOTE=MichaelZ] 
I find the books written by Bjarne Stroustrup really good and useful. The Design and Evolution of C++ is very useful to understand the C++.
[/quote]
I only know his "The C++ Programming language" book which is a great book for learning C++, but can't hold a candle against Structure and Interpretation of Computer Programs when it comes to actually teaching a beginner how to program.

[QUOTE=MichaelZ] 
I think that here we have quite different opinions :). [/quote]
Yes there are many many opinions on how to best teach something.

[QUOTE=MichaelZ] 
I still think that C++ is a better language to start with, but this is just me :).
[/quote]
But can you name a C++ book which is (in contrast to being a good book to learn C++) as good at teaching the fundamentals and concepts of programming as the two mentioned Lisp books? At least I can't.

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=MichaelZ]IMO Lisp is not so easy and I would not choose it as first language.[/quote]What's so difficult about LISP?  Nothing, really.  The expectation isn't for them to learn complex macros or special forms.

> IMO, a first language should be general enough to give you a vision of all the possibilities (console applications, GUI, etc.) and programming paradigms.No, it shouldn't.  The first you thing you need to learn is the conceptual thinking behind the design and implementation of algorithms.

> Yes, I agree. Understanding the fundamental concepts of programming languages is very important.You're contradictiing yourself.

> C++ for example offers several progamming paradigms. You can learn procedural programming, OOP, and so on. This is IMO really useful.Not for a beginner.  And you can do all of those in most LISPs without any trouble.

> Anyway, you do not have to underestimate GUI programming. Even if there are several toolkits to help you, developing a good GUI is not that easy.If you understand how to correctly write an algorithm and how to read documentation, then it is.

> I find the books written by Bjarne Stroustrup really good and useful. The Design and Evolution of C++ is very useful to understand the C++.Which isn't a teaching book.  You're showing you're not qualified to talk on this subject, because the C++ community has one or two very widely accepted C++ books for beginning students.  To be fair, asimon makes the same mistake.

Anything with Stroustroup's name on it isn't a teaching book, FWIW.  It's generally a reference.

[quote=asimon]There are multi-paradigm languages like Oz which support much more than C++, like for example functional programming, (transparent) distributed programming,[/quote]C++ supports the former except for lambda-forms (limited lambda-forms are available through boost) and the latter is supported by add-ons on many C++ toolchains, FWIW.

---

### Post by asimon on 2006-04-28
[QUOTE=LordHunter317]the C++ community has one or two very widely accepted C++ books for beginning students.  To be fair, asimon makes the same mistake.
[/quote]
The C++ book from Stroustrup is good if you already know how to program. For beginners I like the book from Deitel & Deitel. But when it comes to learning programming it's not comparable to the Abelson & Sussman. Which two C++ books do you have in mind?

[QUOTE=LordHunter317]
C++ supports the former except for lambda-forms (limited lambda-forms are available through boost)[/quote]
I wasn't aware that this is in boost. Nice.

[QUOTE=LordHunter317]
the latter is supported by add-ons on many C++ toolchains, FWIW.[/QUOTE]
Of course, I shouldn't have mentioned distributed computing.

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=asimon]The C++ book from Stroustrup is good if you already know how to program. For beginners I like the book from Deitel & Deitel.[/quote]The Deitel and Deitel book is terrible.  Everything they've written is utter garbage.  I could enumerate the reasons, but I don't have the time right now.

> But when it comes to learning programming it's not comparable to the Abelson & Sussman. Which two C++ books do you have in mind?[i]Accelerated C++[i] is the one I principally had in mind.  Certainly if one were to teach a class, this is probably what one would use.

*Thinking in C++* is acceptable, however a large portion of it's acceptance is that it's free online.

---

### Post by MichaelZ on 2006-04-28
[quote=LordHunter317]What's so difficult about LISP?  Nothing, really.  The expectation isn't for them to learn complex macros or special forms.
[/quote] 
Well, we can discuss about this for hours :). Anyway, I think (just my opinion) that it is not a language to begin with.

[quote=LordHunter317]
No, it shouldn't.  The first you thing you need to learn is the conceptual thinking behind the design and implementation of algorithms.
[/quote] 
Yes, the way you learn at a university. Let me say so: if you would like to learn how to program, all the theory behind, then the language is not important.

But if someone would like to learn a first programming language, then I would advice her/him to begin with C++ (and a good book and a good course :)).

[quote=LordHunter317]
You're contradictiing yourself.
[/quote] 
Not really.

[quote=LordHunter317]
Not for a beginner.  And you can do all of those in most LISPs without any trouble.
[/quote] 
I respect your opinion, but I do not share it.  I still think that C++ is more suitable than LISP (or at least as suitable as LISP). Anyway, it is my personal opinion.

[quote=LordHunter317]
If you understand how to correctly write an algorithm and how to read documentation, then it is.
[/quote] 
It surely help, but all is not so simple. It is much more complicate.

[quote=LordHunter317]
Which isn't a teaching book.  You're showing you're not qualified to talk on this subject, because the C++ community has one or two very widely accepted C++ books for beginning students.  To be fair, asimon makes the same mistake.
[/quote] 
I never say that Design and Evolution of C++ is a teaching book. Moreover, it is not not a reference.

The "The C++ Programming Language" is a reference, but could be also used as teaching book.

IMO, there is not a universal teaching book. Each teacher choose the book or the books that most fit is way to teach.

Best wishes,
Michael

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=MichaelZ]Well, we can discuss about this for hours :). Anyway, I think (just my opinion) that it is not a language to begin with.[/quote]Well, yes LISP is a family of languages.   But the notion it's not a suitable teaching language isn't something to be taken as a tautology.

> Not really.Yes, really.  You say it's important to have the ability to write GUI, console, and web applications, and then turn and say it's important to focus on algorithm design and more general matters?  Which is it?  You can't possibly cover both in a reasonable time in a single-semester course, or even really in a year-long course.

 > I respect your opinion, but I do not share it.  I still think that C++ is more suitable than LISP (or at least as suitable as LISP). Anyway, it is my personal opinion.This isn't a response.  You gave as reason that you can't do certain forms of multi-paragdim programming in LISP, which certainly isn't the case.  Are you saying now your opinion has no basis in fact at all?

> It surely help, but all is not so simple. It is much more complicate.How so?  GUI programming is almost entirely following the rules of the API.  There's not much that needs to be taught beyond that.  Perhaps formal analysis of when to multithread tasks, but that's not an introductory level task either.

> I never say that Design and Evolution of C++ is a teaching book. Moreover, it is not not a reference.The clear implication of your statement was that you could use it to learn the language.  This may be true, but that's not relevant in context unless the intent of the book is to teach it to someone new to programming.  So was this just an aside and I am misunderstanding you, or was that your original intent?

---

### Post by MichaelZ on 2006-04-28
[quote=LordHunter317]
Yes, really.  You say it's important to have the ability to write GUI, console, and web applications, and then turn and say it's important to focus on algorithm design and more general matters?  Which is it?  You can't possibly cover both in a reasonable time in a single-semester course, or even really in a year-long course.
[/quote] 
What I was speaking was to advice someone (not forcely a universitary student) which first language should she/he learn. I suggested C++.

Additionally, I also confirmed that knowledge of the fundamental of programming was useful to understand how to program in C++.

[quote=LordHunter317]
This isn't a response.  You gave as reason that you can't do certain forms of multi-paragdim programming in LISP, which certainly isn't the case.  Are you saying now your opinion has no basis in fact at all?
[/quote] 
I never say that you can't do certain forms of multi-paradigm programming in LISP. I just say that in C++ you can multi-paradigm program.

[quote=LordHunter317]
How so?  GUI programming is almost entirely following the rules of the API.  There's not much that needs to be taught beyond that.  Perhaps formal analysis of when to multithread tasks, but that's not an introductory level task either.
[/quote] 
Yes, GUI programming follows the rules of the API. But is this enough? Did you means that each developer knowing how to program can develop GUIs?

[quote=LordHunter317]
The clear implication of your statement was that you could use it to learn the language.  This may be true, but that's not relevant in context unless the intent of the book is to teach it to someone new to programming.  So was this just an aside and I am misunderstanding you, or was that your original intent?
[/quote] 
Sure that you can use "Design and Evolution of C++" to learn C++. Moreover, certain information it contains could be generalized. Did you read the book, anyway?

Anyway, the book is not for beginners, but a useful complement in the teaching.

Best wishes,
Michael

---

### Post by LordHunter317 on 2006-04-28
[QUOTE=MichaelZ]What I was speaking was to advice someone (not forcely a universitary student) which first language should she/he learn. I suggested C++.

Additionally, I also confirmed that knowledge of the fundamental of programming was useful to understand how to program in C++.[/quote]Yes **but you also** said it was useful to have the ability to program in GUIs and console applications as well.  My point is we cannot possible accomplish all of this in  a single course, so one must choose.  Which is more important?

> I never sy that you can't do certain forms of multi-paradigm programming in LISP. I just say that in C++ you can multi-paradigm program.You see to suggest this is advantegous over a primarily functional language (e.g., a LISP) and I want to know why.  That you don't have to relearn the 'fundamentals', I persume you mean syntax, is specious.

 
> Yes, GUI programming follows the rules of the API. But is this enough? Did you means that each developer knowing how to program can develop GUIs?By and large, yes.

 
> Sure that you can use "Design and Evolution of C++" to learn C++. Moreover, certain information it contains could be generalized. Did you read the book, anyway?It's not on my shelf no, but I have read parts.

---

### Post by MichaelZ on 2006-04-29
[quote=LordHunter317]Yes **but you also** said it was useful to have the ability to program in GUIs and console applications as well.  My point is we cannot possible accomplish all of this in  a single course, so one must choose.  Which is more important?
[/quote] 

Yes, you cannot pretend to teach all in one course. You should have some priorities.

Anyway, I was referring that learning as first language a language allowing to program console applications, GUIs, and so on is an advantage.

[quote=LordHunter317]
You see to suggest this is advantegous over a primarily functional language (e.g., a LISP) and I want to know why.  That you don't have to relearn the 'fundamentals', I persume you mean syntax, is specious.
[/quote] 
This is in the context of which language should I learn as first. A multi-paradigm language allows to experiment with different paradigms withouth having to swith toward a new language for a particular paradigm.
 
[quote=LordHunter317]
By and large, yes.
[/quote] 
 
Here I do not completely agree. It is true that it helps, but GUI programming involves other requirements than just programming. Developing a good GUI is rather difficult.

Best wishes,
Michael

---

### Post by LordHunter317 on 2006-04-29
> **MichaelZ]Yes, you cannot pretend to teach all in one course. You should have some priorities.

Anyway, I was referring that learning as first language a language allowing to program console applications, GUIs, and so on is an advantage.[/quote]Again, you're being contradictory.  If you're never going to do it, it's of no advantage whatsoever.

> This is in the context of which language should I learn as first. A multi-paradigm language allows to experiment with different paradigms withouth having to swith toward a new language for a particular paradigm.But the point is the langauges suggested don't require that.  Scheme is capable of OOP programming and procedural if you really wanted said:**
> Developing a good GUI is rather difficult.*Designing* a good GUI has nothing to do with code in the least.  Coding one is indeed the matter of following requirements and APIs.

---

### Post by ZylGadis on 2006-04-30
I enter the programming forum for the first time in two months and I immediately see LordHunter is trolling again. A bit of advice to everyone else: you won't, and you can't beat him at his territory, which is pointless arguing, so I advise you to stop trying and get something useful done instead :) He'll just jump on his next victim.
On topic: LISP is a terrible language to start with, because it is functional. Functional programming requires extremely different thinking than conventional, and starting functional will pollute your mind. I am saying this as an AI professional. You won't ever get anything useful done in LISP in all its incarnations besides something vaguely resembling a rule-based machine. If you are dying to go functional, try Haskell instead; at least it allows you to write code that does something sensible. But never, and I repeat never, allow functional programming to twist your mind by being the first programming you learn.
The thread is all yours now, LordHunter :) Impress the newbies with haute phrases and wrong opinions on important matters.

---

### Post by LordHunter317 on 2006-04-30
> **ZylGadis]I enter the programming forum for the first time in two months and I immediately see LordHunter is trolling again.[/quote]I'm hardly trolling.

>  A bit of advice to everyone else: you won't, and you can't beat him at his territory, which is pointless arguing,No, it isn't.  

>  so I advise you to stop trying and get something useful done instead :) He'll just jump on his next victim.How about you do something useful and ***stop with the personal attacks?***

They're totally uncalled for.

> On topic: LISP is a terrible language to start with, because it is functional. Functional programming requires extremely different thinking than conventional, and starting functional will pollute your mind.No, it won't.  I'm hardly one to say that all algorithms are best expression in a functional manner and that generally going to great lenghts to do so is a bad thing, but tons of things are naturally expressed in a "functional" manner.  Including all sorts of things a beginning programmer should be familar with, like basic mathamatical algorithms.

In fact, the fact most data structure books, even for imperative languages, write lots of recursive code and essentially function code shows that indeed, many things have a natural functional expression.

> You won't ever get anything useful done in LISP in all its incarnations besides something vaguely resembling a rule-based machine.The point of beginning programming isn't to produce useful code *per se*.  It's to learn the concepts behind designing algorthims and the code a computer will execute.  To that goal, language is largely irrelevant, if not unnecssary.  In fact, some CS programs won't teach you any languages until second semester or second year, because it is unnecssary. 

> If you are dying to go functional, try Haskell instead said:**
> The issue with Haskell is there are no texts that teach the language that are geared to the introductory programmer.

[quote]But never, and I repeat never, allow functional programming to twist your mind by being the first programming you learn.It's hardly a twisting of the mind.  Just beause imperative programming is the dominant style doesn't mean that functional is wrong.  

[quote]wrong opinions on important matters.If I'm wrong, why don't you show me where?  I'm here to learn too, after all.  Oh wait, I forgot, it's much eaiser to troll someone than actually even attempt to correct someone.  Which is the problem with the world today.

---

### Post by sphinx on 2006-04-30
[QUOTE=ZylGadis]A bit of advice to everyone else: you won't, and you can't beat him at his territory, which is pointless arguing,[/QUOTE]

[QUOTE=LordHunter317]No, it isn't.[/QUOTE]

Ha ha ha ha. Why am I all of a sudden reminded of a Monty Python sketch.....

---

### Post by Gustav on 2006-04-30
C++: A hard language with lots of traps that can only be discovered by a pro
C: A language where you have to know a lot about how your computer works
LISP: A functional language not like most other mordern languages (although I love it :))
Java: A quite easy to use language, but I hate it so much :evil:

conclution: Don't use any of the above, use Python or Ruby instead when learning to program. The others are great when you have some programming experience but not to start with.

---

### Post by LordHunter317 on 2006-04-30
I feel the need to reiterate that language has not to do with it really, but quality of the text.  The introductory Python and Ruby texts aren't on the level of the texts I recommended.

---

### Post by MichaelZ on 2006-04-30
[quote=Gustav]
C++: A hard language with lots of traps that can only be discovered by a pro
[/quote] 
Nope. Mostly depend on how you begin to learn it. If you begin with a good book (or some good books) and possibly by following a good course for beginners, you will notice that it is not so hard to use.

[quote=Gustav]
C: A language where you have to know a lot about how your computer works
[/quote]  
Practically, same comments as before 

[quote=Gustav]
 Java: A quite easy to use language, but I hate it so much :evil:
[/quote] 
Jave is may be easy to learn and use but why? Because most of the complexity has been hidden.

[quote=Gustav]
conclution: Don't use any of the above, use Python or Ruby instead when learning to program. The others are great when you have some programming experience but not to start with.
[/quote] 
IMHO, you should learn a language that fulfill your needs and requirements.

Best wishes,
Michael

---

### Post by RavenOfOdin on 2006-05-01
[QUOTE=ZylGadis]I enter the programming forum for the first time in two months and I immediately see LordHunter is trolling again. A bit of advice to everyone else: you won't, and you can't beat him at his territory, which is pointless arguing, so I advise you to stop trying and get something useful done instead :) He'll just jump on his next victim.
On topic: LISP is a terrible language to start with, because it is functional. Functional programming requires extremely different thinking than conventional, and starting functional will pollute your mind. I am saying this as an AI professional. You won't ever get anything useful done in LISP in all its incarnations besides something vaguely resembling a rule-based machine. If you are dying to go functional, try Haskell instead; at least it allows you to write code that does something sensible. But never, and I repeat never, allow functional programming to twist your mind by being the first programming you learn.
The thread is all yours now, LordHunter :) Impress the newbies with haute phrases and wrong opinions on important matters.[/QUOTE]

I just put him on ignore. You should do the same.

---

### Post by LordHunter317 on 2006-05-01
Better to just report you.

---

### Post by Technoviking on 2006-05-01
I'm closing this thread, to cool down some tempers that are rising.

Mike

---

