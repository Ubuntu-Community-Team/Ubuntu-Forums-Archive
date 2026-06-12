---
title: "Looking for an easy programming language"
date: 2008-09-03
forum: Programming Talk
---

### Post by askander on 2008-09-03
Hi guys, I know many people have made threads about programming languages and which one is the best. But I wanted to ask for something that fit my needs.

I'm a Pl/Sql developer and DBA since a long time, and I'd like to make a personal project for linux. So, I'd need a REALLY EASY programming language, with an available IDE, that allows me to connect to an oracle database and bring results, and maybe create some charts with them, obviously, using a GUI (Gnome Hopefully).

I don't know if that too much to ask for, but I'd like you people to give me some advice, I hope C++ don't appear as a suggestion (too much for me :) )

Thanks in advance,

---

### Post by Tomosaur on 2008-09-03
> **askander said:**
> Hi guys, I know many people have made threads about programming languages and which one is the best. But I wanted to ask for something that fit my needs.

I'm a Pl/Sql developer and DBA since a long time, and I'd like to make a personal project for linux. So, I'd need a REALLY EASY programming language, with an available IDE, that allows me to connect to an oracle database and bring results, and maybe create some charts with them, obviously, using a GUI (Gnome Hopefully).

I don't know if that too much to ask for, but I'd like you people to give me some advice, I hope C++ don't appear as a suggestion (too much for me :) )

Thanks in advance,

Well, python is probably going to be suggested a million times here so I'm just going to jump in with 'FIRST!' :P

[Python]("http://www.python.org/")
[Python and Oracle]("http://www.oracle.com/technology/pub/articles/devlin-python-oracle.html")
[pyGTK (Gnome GUI toolkit for Python)]("http://www.pygtk.org/")

Oh, and for an IDE, check out [Eclipse]("http://www.eclipse.org") with the [PyDev]("http://pydev.sourceforge.net/") plugin.

Good luck!

---

### Post by StOoZ on 2008-09-03
> **tomosaur said:**
> well, python is probably going to be suggested a million times here so i'm just going to jump in with 'first!' :p

[python]("http://www.python.org/")
[python and oracle]("http://www.oracle.com/technology/pub/articles/devlin-python-oracle.html")
[pygtk (gnome gui toolkit for python)]("http://www.pygtk.org/")

oh, and for an ide, check out [eclipse]("http://www.eclipse.org") with the [pydev]("http://pydev.sourceforge.net/") plugin.

Good luck!

+1

---

### Post by OutOfReach on 2008-09-03
If you want a 'simpler' and more lightweight IDE I would strongly suggest [Geany]("http://www.geany.org/"), it works out of the box with Python (no plugins needed)

---

### Post by LaRoza on 2008-09-03
> **OutOfReach said:**
> If you want a 'simpler' and more lightweight IDE I would strongly suggest [Geany]("http://www.geany.org/"), it works out of the box with Python (no plugins needed)

Or Gedit, which has an integrated Python terminal (plugins).

---

### Post by pmasiar on 2008-09-03
Python is excellent language for developer like you who has no patience to fight with quirks of C++ or such. Python is simple to start and scales well. See wiki in my sig for links.

Just warning: I tried to use devlin's guide to install Python bindings for  Oracle drivers on non-LTS release and failed. Dapper (old LTS)  was fine, and I am too busy with Java to try Oracle bindings on newest LTS :-( 

Oracle prefers RH (forked it).

Any decent editor will do, just set replacing tabs with 4 spaces.

I like SciTE (lightweight and Windows too), or try the simplest one: IDLE, which is also multiplatform.

---

### Post by askander on 2008-09-04
Well, Thank you all for your advices, I guess I'll try Python then and some of the IDE's you recommended. I've reading about it and looks promising.

Thanks.

---

### Post by jinksys on 2008-09-04
Learn C.

Ill try to elaborate.  It is my opinion that you should learn C first.  After that learn some form of assembly, I recommend Professional Assembly Language by WROX.  If you need a free book google Dr carter assembly and youll find a free ebook.  I wouldn't dive into C++ until you have the time and need.

This should provide you with a firm understand in how your system actually works.  Once you understand that you can appreciate higher level languages, like Perl, Python, C#

---

### Post by LaRoza on 2008-09-04
> **jinksys said:**
> Learn C.

Although I know why you posted that, I'll try to ignore that.

C is a very simple and small language. Any competant programmer could learn the basics (and standard library) of it in a very small amount of time. Learning to use it (like any language) takes some more time (10 years...).

---

### Post by Wybiral on 2008-09-04
> **jinksys said:**
> Learn C.

Ill try to elaborate.  It is my opinion that you should learn C first.  After that learn some form of assembly, I recommend Professional Assembly Language by WROX.  If you need a free book google Dr carter assembly and youll find a free ebook.  I wouldn't dive into C++ until you have the time and need.

Why not start at assembly then? Here's my question... Why is assembly the goal?

---

### Post by Kadrus on 2008-09-04
> **jinksys said:**
> Learn C.

Ill try to elaborate.  It is my opinion that you should learn C first.  After that learn some form of assembly, I recommend Professional Assembly Language by WROX.  If you need a free book google Dr carter assembly and youll find a free ebook.  I wouldn't dive into C++ until you have the time and need.

This should provide you with a firm understand in how your system actually works.  Once you understand that you can appreciate higher level languages, like Perl, Python, C#

He asked for an easy programming language that he can learn and use and that will help him get the job done quickly..You are miss-leading him with a bad advice,and confusing his thoughts.

---

### Post by pmasiar on 2008-09-04
> **jinksys said:**
> Learn C.

Ill try to elaborate.  It is my opinion that you should learn C first.  After that learn some form of assembly, 

You in your advice completely ignore needs of OP - and have the guts to accuse me of suggesting Python as silver bullet for any problem, even if Python is **exactly** good (and was designed for) for this situation?

[quote=OP]I'd need a REALLY EASY programming language, with an available IDE, that allows me to connect to an oracle database and bring results, and maybe create some charts with them, obviously, using a GUI (Gnome Hopefully).

I don't know if that too much to ask for, but I'd like you people to give me some advice, I hope C++ don't appear as a suggestion (too much for me[/quote]

After this, you suggest C and ASM? access database in ASM? Yeah, those are **some** experts, who know why Python is always wrong. Brilliant.

Maybe there should be infractions for people like jinksys, for knowingly giving wrong advice  based on "language religion" bias? So we can avoid wasting good flamewars in obvious situation like this one?

---

### Post by LaRoza on 2008-09-04
> **jinksys said:**
> 
This should provide you with a firm understand in how your system actually works.  Once you understand that you can appreciate higher level languages, like Perl, Python, C#

That is true. However, why is that the goal? The point of a computer and abstraction is so you don't have to worry about how the system works unless you need to.

When one wants to learn how to drive, almost no knowledge of how cars work is needed, just how to control it. One can be a good driver before knowing how it works internally, but one can't be a good driver with only the knowledge of how it works.

---

### Post by LaRoza on 2008-09-04
> **pmasiar said:**
> 
Maybe there should be infractions for people like jinksys, for knowingly giving wrong advice  based on "language religion" bias? So we can avoid wasting good flamewars in obvious situation like this one?

Possibly, but I'd rather people do their best to help people and keep flamewars and extensive debates in the appropriate threads. That way new users aren't confused by things that aren't important (it hardly matter to the op that jinksys is just rebelling against what she perceives as a "religion" and probably not posting real advice) and people can debate all they want.

---

### Post by nbayiha on 2008-09-04
Python Or Php i will suggest you.

---

### Post by pmasiar on 2008-09-04
> **LaRoza said:**
> (it hardly matter to the op that X is just rebelling against what she perceives as a "religion" and probably not posting real advice) 

But knowingly posting wrong advice (which has no way to be reasonable: C/ASM for Oracle database?) has no other way to be resolved but to start flamewars. So it's just another (more sophisticated) way of trolling, AFAICT.

---

### Post by CptPicard on 2008-09-04
It is quite fascinating that although I have written my share of inline asm in my C code during my high school years to get my cube rotations faster and indeed do know how the machine works under the hood, it really never, ever has contributed *anything* to my understanding or appreciation of higher-level languages or my ability to work with computational problems and solve them in general.

The concepts you come into contact with in HLLs are simply not applicable to and do not exist in lower-level languages, in particularly not in asm. If you wanted to use them, you'd have to write a whole runtime system, and even then you really would need to *know* of the existence of these features from somewhere.

Then there is the whole issue of a big part of your problem being about language-agnostic abstractions .. which doesn't mean you might just as well use asm -- it means you might just as well use anything that helps you model them most efficiently. Some languages really come out of the box better suited to this task. Asm on the other hand is just steps drawn from very basic instruction set that manipulate bits in registers and ram.

---

### Post by Snowm4n on 2008-09-04
Python of course :D

---

### Post by LaRoza on 2008-09-04
> **pmasiar said:**
> But knowingly posting wrong advice (which has no way to be reasonable: C/ASM for Oracle database?) has no other way to be resolved but to start flamewars. So it's just another (more sophisticated) way of trolling, AFAICT.

I think the OP has gotten the information.

@person who posted C/ASM for this, now that you have gotten it out of your system, I recommend you keep all debates in the appropriate threads. If you honestly believe C and ASM is what the OP should start with for Oracle DB, I think you should make a thread on it because that is really unique advice. Please don't in the future make posts on support threads for the sole purpose of being contrary to another.

---

### Post by loganwm on 2008-09-04
> **Wybiral said:**
> Why not start at assembly then? Here's my question... Why is assembly the goal?

I don't understand why there should be a *goal.*

---

### Post by LaRoza on 2008-09-04
> **loganwm said:**
> I don't understand why there should be a *goal.*

Read the first post again.

---

### Post by jinksys on 2008-09-04
Sorry about that, 

For some reason when I edited my post I thought the question was about the best first language, path to choose, etc.  No way am I recommending ASM for accessing DBs, that'd be torture.

But to respond to the ACTUAL question, I would say that if you are going to do a lot of DB work I'd choose one of the P's, PHP, Python, or Perl.

---

### Post by mssever on 2008-09-04
> **loganwm said:**
> I don't understand why there should be a *goal.*
Because the OP stated a goal.

---

### Post by askander on 2008-09-05
I appreciate all the suggestions (even the C with ASM :)), looking all the posts I just have to add that in my own experience, starting with an easy language is the best way to start a passion, somethings you can do it with visual basic, some things require a more advanced language, but as for cell phones, you always get the simpler first, then you develop some needs and start looking some other but this time with a little more knowledge. Who knows? maybe I'll be programming in C++ next year, but I guess I'll take a bite of Python first ;)

---

### Post by nvteighen on 2008-09-05
> **jinksys said:**
> Sorry about that, 

For some reason when I edited my post I thought the question was about the best first language, path to choose, etc.  No way am I recommending ASM for accessing DBs, that'd be torture.

But to respond to the ACTUAL question, I would say that if you are going to do a lot of DB work I'd choose one of the P's, PHP, Python, or Perl.

I really wanted to reply to you for your first post, thinking it was written with bad intention, trying to explicitly mislead the OP. Luckily, I waited and well,  I was proven wrong.

Thank you for clearing the situation. I felt I had to do the same; I'm sorry for having misinterpreted your intentions.

---

### Post by nsche on 2008-09-06
For what you want I think Ruby on Rails (a language and a framework) would work good.  I don't know about an IDE (unbeliever in them) but it does a real nice job of abstracting the database into classes.  It has automatic code generation (really just a start) and works.

YMMV

---

### Post by jimi_hendrix on 2008-09-06
> **LaRoza said:**
> Or Gedit, which has an integrated Python terminal (plugins).

> **OutOfReach said:**
> If you want a 'simpler' and more lightweight IDE I would strongly suggest [Geany]("http://www.geany.org/"), it works out of the box with Python (no plugins needed)

+1 for both i use geany for a bunch of languages and i find i code the quickest in gedit with plugins

> **jinksys said:**
> Learn C.

OT thread hijack...can u make GUI's in a non OO language like C?

> **Wybiral said:**
> Why not start at assembly then?

<joke>punch cards are much more fun and you dont have to hassle with an IDE... </joke>

---

### Post by mssever on 2008-09-06
> **jimi_hendrix said:**
> can u make GUI's in a non OO language like C?
Of course. GTK is written in C. But that's irrelevant to this thread, as you acknowledged. :)

---

### Post by Wybiral on 2008-09-06
> **jinksys said:**
> Sorry about that, 

For some reason when I edited my post I thought the question was about the best first language, path to choose, etc.  No way am I recommending ASM for accessing DBs, that'd be torture.

But to respond to the ACTUAL question, I would say that if you are going to do a lot of DB work I'd choose one of the P's, PHP, Python, or Perl.

And I apologize if I sounded offensive. It's just that when I see "easy programming language" I think "as far away from low-level as possible" and the "learn everything below" approach seems too time consuming for average high-level development.

---

### Post by slavik on 2008-09-06
> **askander said:**
> Hi guys, I know many people have made threads about programming languages and which one is the best. But I wanted to ask for something that fit my needs.

I'm a Pl/Sql developer and DBA since a long time, and I'd like to make a personal project for linux. So, I'd need a REALLY EASY programming language, with an available IDE, that allows me to connect to an oracle database and bring results, and maybe create some charts with them, obviously, using a GUI (Gnome Hopefully).

I don't know if that too much to ask for, but I'd like you people to give me some advice, I hope C++ don't appear as a suggestion (too much for me :) )

Thanks in advance,
when you say Pl, do you mean Perl or am I missing out on something in the DB world?

If you mean Pl as Perl, then it should be able to interface with any DB ...

---

### Post by LaRoza on 2008-09-06
> **slavik said:**
> when you say Pl, do you mean Perl or am I missing out on something in the DB world?

If you mean Pl as Perl, then it should be able to interface with any DB ...

So naïve...

[http://en.wikipedia.org/wiki/PL/SQL](http://en.wikipedia.org/wiki/PL/SQL)

---

### Post by slavik on 2008-09-06
> **LaRoza said:**
> So naïve...

[http://en.wikipedia.org/wiki/PL/SQL](http://en.wikipedia.org/wiki/PL/SQL)
I'll be quiet now. :(

PS: Perl FTW!

---

### Post by LaRoza on 2008-09-07
> **slavik said:**
> 
PS: Perl FTW!

What's FTW? Does it mean "Python?"

/me makes fun of Slavik's ignorance of PL/SQL.

---

### Post by pmasiar on 2008-09-07
> **slavik said:**
> when you say Pl, do you mean Perl or am I missing out on something in the DB world?

PL/SQL is version of PL/1 for Oracle database, which was very advanced language for it's time.

heh, I see you are quite fallible  8-)

---

### Post by nvteighen on 2008-09-07
> **jimi_hendrix said:**
> 
OT thread hijack...can u make GUI's in a non OO language like C?


<more-hijacking>
Who said C can't be OOP? Define a structure, define some accessors, use some coherent naming and syntax to call functions and you're done: very basic and yet useful OOP in C.

For inheritance, a casting system like GTK's would be enough.
</more-hijacking>

---

### Post by CptPicard on 2008-09-07
> **nvteighen said:**
> 
For inheritance, a casting system like GTK's would be enough.


But it's polymorphism and virtual functions and the related dispatching to correct code that really are the beef of OOP, so to get it all you'd have to essentially implement C++'s behind the scenes functionality...

Essentially FWIW C "does OOP" just as well as any other C-like language "does OOP" with structs + functions.

---

### Post by LaRoza on 2008-09-07
> **CptPicard said:**
> so to get it all you'd have to essentially implement C++'s behind the scenes functionality...


And this is how C++ started.

---

### Post by CarlosNYB on 2008-09-07
On that note of OOP in C...

With the right libraries, and the right conventions, it's amazing how you can make a language act AS IF it is "another kind of language" than what is usual/expected.

Some libraries are easier to work with than others, some tools easier than others (and personal mileage will vary).  Some languages, some IDEs, some libraries, etc., have solutions for easy development with databases.  What you consider easy and/or efficient may not be what someone else considers easy and/or efficient, but hey, explore.

---

### Post by fiddler616 on 2008-09-07
> **askander said:**
> I appreciate all the suggestions (even the C with ASM :)), looking all the posts I just have to add that in my own experience, starting with an easy language is the best way to start a passion, somethings you can do it with visual basic, some things require a more advanced language, but as for cell phones, you always get the simpler first, then you develop some needs and start looking some other but this time with a little more knowledge. Who knows? maybe I'll be programming in C++ next year, but I guess I'll take a bite of Python first ;)
If you take the "bite of Python" route, I recommend "A Byte of Python" by a guy named Swaroop.
Ebook: [http://www.ibiblio.org/g2swap/byteofpython/read/](http://www.ibiblio.org/g2swap/byteofpython/read/)

---

### Post by nvteighen on 2008-09-07
> **CptPicard said:**
> But it's polymorphism and virtual functions and the related dispatching to correct code that really are the beef of OOP, so to get it all you'd have to essentially implement C++'s behind the scenes functionality...

Essentially FWIW C "does OOP" just as well as any other C-like language "does OOP" with structs + functions.

Which is the reason why we use Python, right? :)

Or better: Lisp closures!!

---

### Post by CptPicard on 2008-09-07
> **nvteighen said:**
> Which is the reason why we use Python, right? :)

Or better: Lisp closures!!

Yeah, sort of. They do very "soft" kind of polymorphism. For a wonderful multiple-dispatch system, see CLOS in Common Lisp.

---

### Post by askander on 2008-09-08
Thanks fiddler616 for the guide hint

---

