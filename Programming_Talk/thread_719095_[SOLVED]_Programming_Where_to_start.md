---
title: "[SOLVED] Programming: Where to start?"
date: 2008-03-08
forum: Programming Talk
---

### Post by null-cipher on 2008-03-08
Hi there everybody!
Now, I'm sure that somebody would have posted something similar to this in the past, and I apologise in advance for that...

I'm 15 years of age, and am slowly ticking through a book on C++ for Linux, and I am wondering, where is it that I can learn more about programming? Is it imperative to have taken a course in computer science to write effective code?

Basically, I'm asking all the wonderful contributors out there, where I have to go and what I have to do to learn to become a contributing member of the Linux community.

Thanks!:)

---

### Post by LaRoza on 2008-03-08
The sticky is a good place to start.

You don't need formal education to program, although it can help...

(I am entirely self taught)

[http://laroza.freehostia.com/home/apps/programming/index.php](http://laroza.freehostia.com/home/apps/programming/index.php)

---

### Post by lnostdal on 2008-03-08
learn a language, program, find an itch, program ... etc. .. you don't have to "go" anywhere in particular .. start building and it will come

about c++ .. if i met myself back when i was 15 i'd tell myself to stay away from c++ .. i'd tell myself to use a higher level language, then optimize by rewriting small parts in c when needed (very, very seldom) .. c++ (and Windows btw.) almost killed my interest in computers entirely .. i like intelligent, beautiful and elegant things - not bloated, unpredictable, evil crap .. but that's just me, and me

edit:
if you feel you need to understand the "inner mechanics" of things learn c instead .. and/or read [http://savannah.nongnu.org/projects/pgubook/](http://savannah.nongnu.org/projects/pgubook/)

---

### Post by LaRoza on 2008-03-08
> **lnostdal said:**
> 
about c++ .. if i met myself back when i was 15 i'd tell myself to stay away from c++ .. i'd tell myself to use a higher level language, then optimize by rewriting small parts in c when needed (very, very seldom) .. c++ (and Windows btw.) almost killed my interest in computers entirely .. i like intelligent, beautiful and elegant things - not bloated, unpredictable, evil... but that's just me, and me

It is not just you, I started with C++, haven't used it since.

---

### Post by Can+~ on 2008-03-08
Still remember what Linus crapped someone for talking about C++

> From: Linus Torvalds <torvalds <at> linux-foundation.org>
Subject: Re: [RFC] Convert builin-mailinfo.c to use The Better String Library.
Newsgroups: gmane.comp.version-control.git
Date: 2007-09-06 17:50:28 GMT (26 weeks, 2 days, 7 hours and 54 minutes ago)

On Wed, 5 Sep 2007, Dmitry Kakurin wrote:
> 
> When I first looked at Git source code two things struck me as odd:
> 1. Pure C as opposed to C++. No idea why. Please don't talk about portability,
> it's BS.

*YOU* are full of ********.

C++ is a horrible language. It's made more horrible by the fact that a lot 
of substandard programmers use it, to the point where it's much much 
easier to generate total and utter crap with it. Quite frankly, even if 
the choice of C were to do *nothing* but keep the C++ programmers out, 
that in itself would be a huge reason to use C.

In other words: the choice of C is the only sane choice. I know Miles 
Bader jokingly said "to piss you off", but it's actually true. I've come 
to the conclusion that any programmer that would prefer the project to be 
in C++ over C is likely a programmer that I really *would* prefer to piss 
off, so that he doesn't come and screw up any project I'm involved with.

C++ leads to really really bad design choices. You invariably start using 
the "nice" library features of the language like STL and Boost and other 
total and utter crap, that may "help" you program, but causes:

 - infinite amounts of pain when they don't work (and anybody who tells me 
   that STL and especially Boost are stable and portable is just so full 
   of BS that it's not even funny)

 - inefficient abstracted programming models where two years down the road 
   you notice that some abstraction wasn't very efficient, but now all 
   your code depends on all the nice object models around it, and you 
   cannot fix it without rewriting your app.

In other words, the only way to do good, efficient, and system-level and 
portable C++ ends up to limit yourself to all the things that are 
basically available in C. And limiting your project to C means that people 
don't screw that up, and also means that you get a lot of programmers that 
do actually understand low-level issues and don't screw things up with any 
idiotic "object model" crap.

So I'm sorry, but for something like git, where efficiency was a primary 
objective, the "advantages" of C++ is just a huge mistake. The fact that 
we also piss off people who cannot see that is just a big additional 
advantage.

If you want a VCS that is written in C++, go play with Monotone. Really. 
They use a "real database". They use "nice object-oriented libraries". 
They use "nice C++ abstractions". And quite frankly, as a result of all 
these design decisions that sound so appealing to some CS people, the end 
result is a horrible and unmaintainable mess.

But I'm sure you'd like it more than git.

			Linus

[http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918)

As my recommendation for started, as usual:
-Go for python since it's easy, and teaches you the idea of functions, classes and iterations. Later you go low level to learn the heart of everything.
btw, I'm also self taught, by I learnt through AS2, then low level (C) and then went up again to python.

---

### Post by LaRoza on 2008-03-08
> **Can+~ said:**
> Still remember what Linus told someone for talking about C++

[http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918)

As my recommendation for started, as usual:
-Go for python since it's easy, and teaches you the idea of functions, classes and iterations. Later you go low level to learn the heart of everything.
btw, I'm also self taught, by I learnt through AS2, then low level (C) and then went up again to python.

Well, Linus is a kernel hacker, so that is understandable :) But yes.

I layout my personal recommendations on my homepage, and in the link I gave. (Python, C and Lisp. In that order)

---

### Post by Acglaphotis on 2008-03-08
Darn that makes me feel bad for learning C++...

But anyway, here you go, there are a lot of good exercises here:

[http://projecteuler.net/index.php?section=view](http://projecteuler.net/index.php?section=view)

Only 13 people have done the hardest one.

18519 did the easiest one.

It's good practice : ).

BTW: I went Python then C++ (yeah, yeah...)

---

### Post by elithrar on 2008-03-09
Another one for Python here. Started with Ruby, but migrated across to Python because of its' more widespread adoption, the cleaner syntax and documentation (oh, and Django!).

[http://docs.python.org/tut/](http://docs.python.org/tut/) - the official Python tutorial, by Guido himself.
[http://www.developer.com/lang/other/article.php/3624681](http://www.developer.com/lang/other/article.php/3624681) - another tute.
[http://python.objectis.net/](http://python.objectis.net/) - and yet more!

I'm no fanboy, but I will praise Python for the fact that it's flexible - you can use it for scripting, web development & developing GUI applications. It's also fairly mature, which means that finding Python support in the enterprise environment is fairly common - relevance is important to me, because I like to dedicate my time to something I can **use**.

Oh, and the language just makes a lot of sense. I've got 3 O'Reilly books on Python that I started with, and still refer to.

---

### Post by null-cipher on 2008-03-09
Ah yes, I recall a friend telling me that I should learn python first...
Also, I'm only learning C++ because a friend gave me a book, myself I always had an inkling toward C... so I think I might pursue that.
Appreciating the input. :D

---

### Post by Acglaphotis on 2008-03-09
If you are going with python, buy Python Phrasebook (Brad Dayley, Developers Library) and Python Pocket Reference from O'reilly. Also, don't think C++ is bad just because Linus says so.

---

### Post by pmasiar on 2008-03-09
There was expereiment in some high school: half the students learned "professional" language like Java or C++ (I forgot which), and other group started with Python, and after 3 months as they finished basics, moved to the "professional" language.

Result was surprising - but maybe not. Mixed group was able to cover more features of Java, because they were able to see through verbose syntax to see underlying paradigms. Single-language group struggled with that.

I definitely would advise against learning C++ as first language, alone by yourself. Python is much better choice (see wiki in my sig). But of course do what you want, you have freedom to choose.

---

### Post by null-cipher on 2008-03-09
Well, it's not just Linus really. Most of the people who I have told I am learning C++ have screwed up their nose to a varying degree...
I have somewhat aspired to learning to write device drivers in the distant future... something that I assume would need a more rounded knowledge of computers (Comp. Scie. course), and am a bit curious to learn about the kernel a bit more, so C has always been on my agenda...

Trouble is, with school and work I'm finding myself with very little time for learning to program...

Wouldn't it be great if we could all do GNU software full time! Haha! :D

EDIT: I do have a eBook a friend gave me for Python (O'Reilly Programming Python 3rd Edition), and along with your suggestions I am choosing to learn it. My C++ book looks bigger than the Lord of The Rings trilogy, and having got halfway through it, I've found that I'm not as eager to pick it up as I used to be. So I think python might be the new beginning I need.

---

### Post by Acglaphotis on 2008-03-09
Is it THAT bad?

---

### Post by null-cipher on 2008-03-09
Well, I can't really say one way or the other... I'm kinda new to all this sorta stuff. I've only been on Linux for about a year or 2, and I'm loving it!

I think the reactions I got may have been because it's a bit of an odd choice for a beginning language... but I can't really be sure...

---

### Post by Fbot1 on 2008-03-09
> **Acglaphotis said:**
> Is it THAT bad?

If you practice some restraint and not fall for its stupid crap it's okay.

---

### Post by slavik on 2008-03-09
null-cipher, you picked a language and that is good. stick to it. you are learning, it doesn't matter which language you learn first as long as you stick with it. if you have problems/questions with C++, ask ... also say that "C++ is a hard requirement" or you'll get everyone and their grandma to "suggest" Python. ;)

---

### Post by horse1bun on 2008-03-10
I recently started learning C++ via online tutorials (hello world!), and have since switched to python myself. 

I have found the learning curve quite steep as I don't know anything about exactly HOW a computer processes information.

The way I was learning C++ felt too much like a typing class and I am very impatient, I have trouble seeing "the bigger picture" starting with low level coding, and so am finding Python a bit easier for me - like getting in a hot tub shock vs. getting into ice water shock.
:guitar:

good luck

---

### Post by null-cipher on 2008-03-10
> **horse1bun said:**
> I recently started learning C++ via online tutorials (hello world!), and have since switched to python myself. 

I have found the learning curve quite steep as I don't know anything about exactly HOW a computer processes information.

The way I was learning C++ felt too much like a typing class and I am very impatient, I have trouble seeing "the bigger picture" starting with low level coding, and so am finding Python a bit easier for me - like getting in a hot tub shock vs. getting into ice water shock.
:guitar:

good luck

I think I would probably have to agree with you there. I'm understanding all the concepts in my book, but it's just a little tedious, and like you, I am mildly impatient.

I'm still going to learn the rest of C++, but I am certainly going to learn C afterwards. But perhaps I should take a break and learn python. I've heard that it's pretty good for all sorts of things.

---

### Post by lapubell on 2008-03-10
i use python all over my comp.  Little scripts to do repetitave tasks are great for python (or jsut BASH) but I am no professional programmer.  I do PHP and other web devel and only code in python (and BASH) for my desktop.  It would probably be worth the break in learning C and C++ just to put those concepts to practice.

---

### Post by naugiedoggie on 2008-03-10
> **null-cipher said:**
> Hi there everybody!
Now, I'm sure that somebody would have posted something similar to this in the past, and I apologise in advance for that...

I'm 15 years of age, and am slowly ticking through a book on C++ for Linux, and I am wondering, where is it that I can learn more about programming? Is it imperative to have taken a course in computer science to write effective code?

Basically, I'm asking all the wonderful contributors out there, where I have to go and what I have to do to learn to become a contributing member of the Linux community.

Thanks!:)

As you are in high school, try this story out.

[A Scheme Story]("http://www.trollope.org/scheme.html")

Thanks.

mp

---

### Post by Ricky93 on 2008-03-10
I'm not much of a programmer myself, but I advise you to learn Python.

Start with the official documentation:
[http://docs.python.org/tut/](http://docs.python.org/tut/)

---

### Post by null-cipher on 2008-03-11
> **naugiedoggie said:**
> As you are in high school, try this story out.

[A Scheme Story]("http://www.trollope.org/scheme.html")

Thanks.

mp

Thanks for that article. I think that's somewhat hit the nail on the head!
But at my school, all the way down in New Zealand... we don't have the funding to run a computer science class in my year level. -_-
I'm learning to touch type in "Information Management" when I want to be learning software...

Ah well. I'll get there eventually.

---

### Post by pmasiar on 2008-03-11
You don't need classroom lessons to learn programming. in fact, many/most people learned programming by themselves, from the book. All you need is access to a computer, a book (online is fine), and determination.

Python ie easier to learn than most other languages, but any language will do. GameMaker is fun way to program games (and games only) in GUI, without much/any code, but only on Windows.

You need to solve problems. See wiki in my sig for training task, or [this thread](http://ubuntuforums.org/showthread.php?t=721061)

---

### Post by naugiedoggie on 2008-03-11
> **null-cipher said:**
> Thanks for that article. I think that's somewhat hit the nail on the head!
But at my school, all the way down in New Zealand... we don't have the funding to run a computer science class in my year level. -_-
I'm learning to touch type in "Information Management" when I want to be learning software...

Ah well. I'll get there eventually.

Yes, the difference between "learning to program" and "learning to program in python" is critical.  It is somewhat like "learning to learn."  If you learn how to *program*, then you can pick up any language easily.  But, if you just learn how write programs in python, then you'll find the structure of another language to be an impediment, because "it isn't like python."

You can also look at the information in this article at wikipedia, on the computer science text [Structure and Interpretation of Computer Programs]("http://en.wikipedia.org/wiki/Structure_and_Interpretation_of_Computer_Programs").  This is one of those "classic" texts more talked about than read, I think.  But, you might get some ideas about directing your studies from the article.

Thanks.

mp

---

### Post by bharadwaj on 2008-03-11
BASH, Python, C#, Java, Perl, Ruby, Javascript....

---

### Post by pmasiar on 2008-03-11
> **naugiedoggie said:**
> Yes, the difference between "learning to program" and "learning to program in python" is critical.  It is somewhat like "learning to learn."  If you learn how to *program*, then you can pick up any language easily.  But, if you just learn how write programs in python, then you'll find the structure of another language to be an impediment, because "it isn't like python."

But this is true for any first language, isn't it? Would java be different?

You can learn programming only by writing programs in some concrete language. When you learn your **second **language, you realize which part of programming is syntax of first language, and which part is common to any language.

---

### Post by mssever on 2008-03-11
> **naugiedoggie said:**
> Yes, the difference between "learning to program" and "learning to program in python" is critical.  It is somewhat like "learning to learn."  If you learn how to *program*, then you can pick up any language easily.  But, if you just learn how write programs in python, then you'll find the structure of another language to be an impediment, because "it isn't like python."
While it's absolutely true that learning to think like a programmer is more important than learning a particular language, you have to start with some language. Inevitably, a beginning programmer will be quite influenced by that language. So if that language helps teach good habits, great (which suggests a high-quality language is good to start with, even if it isn't commercially as popular as others). I imagine there will always be a barrier to learning the second language--especially if it's quite different--before you learn to distinguish between programing thought and the semantics of a particular language.

---

### Post by naugiedoggie on 2008-03-11
> **pmasiar said:**
> But this is true for any first language, isn't it? Would java be different?

You can learn programming only by writing programs in some concrete language. When you learn your **second **language, you realize which part of programming is syntax of first language, and which part is common to any language.

Hello,

I'm not picking on python, it is just a natural example when so recommended.  What matters about the language picked is how much time is expended learning syntax versus how much time is spent learning concepts.  That was the point of the article that I keep on my website, to which I gave the link.

I'm a Java programmer and I think Java is a horrible first language for precisely the reason that you have to spend so much time on syntax.  However, there are some texts that use Java as an *illustration* rather than just teaching the language.  

[SICP]("http://mitpress.mit.edu/sicp/full-text/book/book.html") has the right idea.  It requires a high degree of mathematical sophistication, however.  That may be because Scheme is so syntactically simple, you can learn it in a day.  But that simplicity means that you as the programmer have the burden of creating the complex structures that other languages create syntactically.  Less code, more brainwork.

Thanks.

mp

---

### Post by slavik on 2008-03-11
> **naugiedoggie said:**
> Hello,

I'm not picking on python, it is just a natural example when so recommended.  What matters about the language picked is how much time is expended learning syntax versus how much time is spent learning concepts.  That was the point of the article that I keep on my website, to which I gave the link.

I'm a Java programmer and I think Java is a horrible first language for precisely the reason that you have to spend so much time on syntax.  However, there are some texts that use Java as an *illustration* rather than just teaching the language.  

[SICP]("http://mitpress.mit.edu/sicp/full-text/book/book.html") has the right idea.  It requires a high degree of mathematical sophistication, however.  That may be because Scheme is so syntactically simple, you can learn it in a day.  But that simplicity means that you as the programmer have the burden of creating the complex structures that other languages create syntactically.  Less code, more brainwork.

Thanks.

mp
I had a professor explain scheme syntax to me in 2 minutes. :) (with regular talking)

---

### Post by shinems on 2008-03-12
i have programmed in java.it seems a bit complicated.

i have programmed in php.its good.but can only be used for websites.

now i want to try python.

which is the best tutorial on net?

:popcorn:

---

### Post by kaens on 2008-03-12
> **mssever said:**
> While it's absolutely true that learning to think like a programmer is more important than learning a particular language, you have to start with some language. Inevitably, a beginning programmer will be quite influenced by that language. So if that language helps teach good habits, great (which suggests a high-quality language is good to start with, even if it isn't commercially as popular as others). I imagine there will always be a barrier to learning the second language--especially if it's quite different--before you learn to distinguish between programing thought and the semantics of a particular language.

Well said.

I tend to think that people who are looking to learn how to program should start with a more minimalist language, and a course that teaches the process of breaking down problems into abstractions that can be expressed elegantly through code. [SICP]("http://http://mitpress.mit.edu/sicp/") lends itself well to this purpose, although it may be a bit heady for someone with no programming experience at all, or someone with a weak math background (I had a very weak math background before going through SICP, ended up going through Concrete Mathematics in the middle of it, and then felt like I had a much firmer grasp of math in general and the process of writing programs), and in that case, [HTDP]("http://www.htdp.org/") may be a better choice.

I find scheme to be a very nice language for learning how to program - it's a lisp, so it's syntax is extremely uniform (some may say non-existant), and it's rather minimal while still providing very high-level abstraction utilities.

On the other hand, if you want to learn how to program just to get some stuff done, python is a great choice - and supports most of the high level concepts supported by the lisp family of languages. 

I do think that the free courses for scheme do a better job at getting someone in the right mindset to create good, maintainable programs - but then again the lisps will spoil you and you'll always be feeling like you're banging your head against the language when using most other languages - at least in my experience.

---

### Post by oleksus on 2008-03-12
I'm not a programmer, my knowledge of it used to be limited by basic BASIC. The language that got me started (because I wanted to write text adventures) was LUA.
(I'm a bit surprised nobody mentioned it. It's an outrage.)

Now my long time dream has come true: I'm writing and publishing my own text games.

I'd suggest, if you are absolute beginner, 
1) start with finding a problem which you want to solve by programming.(game development, improving existing applications to suit your needs, writing text advenures)
2) dig LUA or PYTHON as your languages of choice.
3) Get yourself a friend who is a programmer, and whom you might bugger with questions. (better yet, if (s)he is working on solving the same problem as you are learning to)
4) push forward your learning; skip the unimportant, steal pieces of code, try to incorporate it in your programs, see what happens, experiment, read, study - LEARN!

---

### Post by pmasiar on 2008-03-12
@OP:

See wiki in my sig for links to Python tutorials for beginners, and training tasks. If you are experienced programmer, "Dive into Python" is the best. Sticky FAQ has more links.

---

### Post by null-cipher on 2008-03-13
Hmmm... Lots of good suggestions here....
Is there anything I could study at school that would improve my understanding? I'm aware of Maths. Haha!

---

### Post by pmasiar on 2008-03-13
What to study? As usually, it depends... :-) on what are your interests and goals.

It is certainly possible to become programmer without deep math background, even if slightly unusual: math requires same degree of detail-oriented mind and handling different levels of abstractions which have no counterpart in real-life reality, as programming does. But certainly people with rather different backgrounds can become competent programmers - but level of math proficiency restricts kinds of tasks they are able to solve. Programming is about clear thinking, so being philosophy major is not inherently wrong.

**Solving programming tasks** certainly is better training for a programmer than solving differential equations :-)

---

### Post by themusicwave on 2008-03-13
If by school you mean college then a degree in any of the following doesn't hurt:

computer engineering - more hardware than software focused
Software engineering - Building software, large systems, the discipline of  making software

computer science - All the cool theory behind the software, lots of theory and math usually and algorithms.

---

### Post by null-cipher on 2008-05-10
Been awhile since I posted in this thread, recently had to change my email and haven't updated everything!

I've recently hacked my way through an O'Reilly PHP and MySQL book, and it has really opened my eyes somewhat.
Having got halfway though my C++ book (which I now intend to finish) and learning a second language has helped me to understand the fundamentals a little better.
I'm also planning to take a course in Computer Science when I finish school, mostly because I want to learn how to **structure** my programs, rather than just learn syntax.

I'm sure any real programmer would tell me that it's more about structure than anything.

Also, I'd just like to take a second to thank everybody that has posted. It's because of this community spirit, that I love working with Linux and open source. You guys rock. :D

---

### Post by grashdur on 2008-05-10
My deepest apologies for posting in the wrong place here, but: How do you start a new thread? I've done it once or twice before, but now I can't find any button in the entire forum where I can click to start a new thread. I've spent the past half hour looking all over, but I still can't find any buttons, options, discussions, or instructions anywhere to address this. Is there a glitch in the forums? :(

---

### Post by LaRoza on 2008-05-10
> **grashdur said:**
> My deepest apologies for posting in the wrong place here, but: How do you start a new thread? I've done it once or twice before, but now I can't find any button in the entire forum where I can click to start a new thread. I've spent the past half hour looking all over, but I still can't find any buttons, options, discussions, or instructions anywhere to address this. Is there a glitch in the forums? :(

There should be an option on the upper (ish) left.

The Forum Feedback and Help forum has a sticky with a "Guide to Forum Features"

See first link: [http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219)

If you have further problems, take a screenshot and let a staff member know.

---

