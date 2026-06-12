---
title: "how to be a ubuntu programer?"
date: 2008-03-12
forum: Programming Talk
---

### Post by imax36581 on 2008-03-12
hi my freinds
i want to know how can i be a ubuntu programmer...
can you tell me about whats the best language in linux programing and how can i learn it and give me the resources like ebook ,tutorials,...
thanks in advance

---

### Post by themusicwave on 2008-03-12
Ubuntu tends to prefer python.  They like patches and Apps to be created in it.

Python is also a good language for beginners.  Because Ubuntu likes it so much there are also lots of people who know it well here on the forums.

Learning Python is a good book.  It would get you started well.

Also, I found this free book How to  Think Like a Python Progammer [http://www.greenteapress.com/thinkpython/]("http://www.greenteapress.com/thinkpython/")

It was pretty helpful for learning python and has good pointers about programming in general.

The underlying kernel and such is written in C, which is a good bit harder to learn than Python.

Also, Java tends to be less popular in the Linux world(I happen to like it).

Hope that helps,

Jon

---

### Post by ukripper on 2008-03-12
You can use python, C, C++

But if you want to build GUI you would need either QT toolkits or GTK+

[http://www.gtk.org/](http://www.gtk.org/)

Here is good one to use with python [http://www.pygtk.org/](http://www.pygtk.org/)

---

### Post by LaRoza on 2008-03-12
See the sticky, see my wiki.

---

### Post by srilyk on 2008-03-12
I'll echo the python kick... python rocks my socks ^_^

take a month of python (or less) and a month of pyGTK (or less) and I was already able to create some rather spiffin programs.

Some examples of programs written in python:

pidginIM(formerly GAIM)
GIMP
ndisgtk (a gtk frontend for ndiswrapper for those fun wireless cards)

Good times, that's what python is :D

Plus, with py2exe or shedskin, you can fairly easily create ports of your programs.

:guitar: rock on, python (plus it's named after monty python, not the snake... cool? yeah, I thought so too :D)

---

### Post by LaRoza on 2008-03-12
> **srilyk said:**
> 
Plus, with py2exe or shedskin, you can fairly easily create ports of your programs.


No, Python is portable as it is. py2exe will make it less portable.

The sticky addresses all the questions here.

---

### Post by Zugzwang on 2008-03-12
Dear OP, please see the so called stickies.

srilyk is a little bit too enthusiastic, at least GIMP is definitely *not* written in Python. There might be extensions for it written in that language, but that's not the same.

---

### Post by pmasiar on 2008-03-12
You did not mention your experience, if any... :-)

Python is easiest way to start programming. See wiki in my sig for guides and training tasks about how to learn Python.

But many (most!) programs distributed by ubuntu are in different languages, it depends on project you are interested to work in.

---

### Post by imax36581 on 2008-03-12
thanks a lot for all of your answers** themusicwave,ukripper,LaRoza,srilyk and Zugzwang**
i thinks its better to start with python

> **ukripper said:**
> 
But if you want to build GUI you would need either QT toolkits or GTK+

also i want to build GUI....
i thinks i must learn QT too
and about c i can say its my favorite language...,i write all of my university projects with c and i think in this case just i must khow some command in it for linux programing.but having a GUI in c is difficult maybe i must use QT.
**thanks again**
please if you have any idea or resources that help me to starting ubuntu programing,tell me....

---

### Post by LaRoza on 2008-03-12
> **imax36581 said:**
> 
also i want to build GUI....
i thinks i must learn QT too
and about c i can say its my favorite language...,i write all of my university projects with c and i think in this case just i must khow some command in it for linux programing.but having a GUI in c is difficult maybe i must use QT.
**thanks again**
please if you have any idea or resources that help me to starting ubuntu programing,tell me....

Learn the language first.

For reference:

* QT is used in KDE apps and for KDE.
* GTK+ is used in GNOME apps

Also, GTK is for C, so you can use it with what you know.

See my wiki, it will give you a lot of resources for many languages (and for GUI's). See pmasiar's for Python (but my wiki has Python references also. My wiki has a different intent from pmasiar's)

---

### Post by pmasiar on 2008-03-12
Yes, my wiki is for Python beginners without all the other distraction what LaRoza has :-)

---

### Post by LaRoza on 2008-03-12
> **pmasiar said:**
> Yes, my wiki is for Python beginners without all the other distraction what LaRoza has :-)

Any beginner looking to learn (and follow the appropriate link) will be on your wiki in no time.

(The OP had mentioned experience in C, and wanting to make GUI's, my wiki has a new section on GUI's)

---

### Post by jespdj on 2008-03-12
> **srilyk said:**
> Some examples of programs written in python:

pidginIM(formerly GAIM)
GIMP
ndisgtk (a gtk frontend for ndiswrapper for those fun wireless cards)
You are mistaken; Pidgin and GIMP are both written in C, not Python.
ndisgtk is indeed written in Python.

---

### Post by themusicwave on 2008-03-12
> **imax36581 said:**
> thanks a lot for all of your answers** themusicwave,ukripper,LaRoza,srilyk and Zugzwang**
i thinks its better to start with python


also i want to build GUI....
i thinks i must learn QT too
and about c i can say its my favorite language...,i write all of my university projects with c and i think in this case just i must khow some command in it for linux programing.but having a GUI in c is difficult maybe i must use QT.
**thanks again**
please if you have any idea or resources that help me to starting ubuntu programing,tell me....

Also, if you are writing python take a look at Tkinter.  It is the GUI engine bundled with python.

It is fairly easy to use and is cross platform.  Probably a good place to start.

---

### Post by CptPicard on 2008-03-12
> **themusicwave said:**
> Ubuntu tends to prefer python.  They like patches and Apps to be created in it.

This is just simply wrong... the Ubuntu distribution integrators tend to prefer Python, but of course the distribution itself is composed of packages from all over, which can be in any language. The majority of big, important apps are in C or C++, not to mention the kernel itself, which is in C.

But Python is a good language in general for beginners...

There really is no difference in becoming an "Ubuntu programmer" and "becoming a programmer" in general...

> 
Also, Java tends to be less popular in the Linux world(I happen to like it).

I am not sure what you base this on. Compared to what.. the Windows world? My own view would be that Java actually fits much more nicely into a Linux environment than a Windows one, but YMMV...

---

### Post by Daveski on 2008-03-12
> **imax36581 said:**
> 
and about c i can say its my favorite language...,i write all of my university projects with c and i think in this case just i must khow some command in it for linux programing.but having a GUI in c is difficult maybe i must use QT.

If you are happy with c, then stick with it. A GUI is usually just a complex library that you can interface with in ANY language. QT and GTK+ are frameworks which allow your code (what ever language it is coded in) to create and maintain all the bits and bobs that make up a modern GUI.

---

### Post by LaRoza on 2008-03-12
> **Daveski said:**
> If you are happy with c, then stick with it.

I wouldn't recommend anyone to stick with any single language. I do recommend you stay with one while learning, but once you "get it" you should learn more. (Learning Haskell now...)

C is a must know language, especially in Linux, but higher level languages are very useful tools and should be learned.

---

### Post by pmasiar on 2008-03-12
> but higher level languages are very useful tools and should be learned.

Exactly. 

Stick with C if you think it makes sense, but many people found that learning high-level language first is simpler and faster (with dynamic typing, you don't have to worry about variable types: if opertion is valid, it just works). Become competent in that one language, then learn couple more. **Only after learning multiple languages** you become real programmer and not one-trick joker: you realize that **part of what you though was programming difficulties was just syntax complication of that particular language**, and other languages might not have that problem (and might have diffoerent other interesting problems). 

And some parts of programming are genuinely hard, no matter what language do you use.

Then you realize why people say "right tool for the job": because for a good reason there are many different languages, each good for different job, and **you need to know the right tool if you want to be efective at that job.**

Read sticky FAQ about what you need to learn beyond syntax of one language.

---

### Post by imax36581 on 2008-03-13
thanks.....
it seems to learning python is not too difficult for who program with c.
and i must know how can i merge my code with other language....

---

### Post by frankos44 on 2008-03-13
PHP5 is a good language because it integrates well with mysql database and is the perfect choice for web page development. It can also be used without browser for  local apps when the cli is installed.

---

### Post by LaRoza on 2008-03-13
> **imax36581 said:**
> thanks.....
it seems to learning python is not too difficult for who program with c.
and i must know how can i merge my code with other language....
You just have to get used to it :) There isn't much stuff that is "new".

> **frankos44 said:**
> PHP5 is a good language because it integrates well with mysql database and is the perfect choice for web page development. It can also be used without browser for  local apps when the cli is installed.
I wouldn't say it is the "perfect" choice. The language does have some flaws (PHP), and Python (and Ruby) may be better if one has a choice, or doesn't already know PHP.

---

### Post by pmasiar on 2008-03-13
> **frankos44 said:**
> PHP5 is a good language because it integrates well with mysql database and is the perfect choice for web page development. It can also be used without browser for  local apps when the cli is installed.

I am not sure if you know Python or Ruby, and how qualified are you to compare. I know enough PHP to know that Python is better choice in most cases (as LaRoza mentioned above).

Also, in many cases SQLite is enough, so additional hassle with MySQL (server, user administration etc) are not worth it. Or does your experience with MySQL suggest otherwise?

While talking about that, PostgreSQL is comparable with MySQL and in some aspects vastly superior: ie you can write embedded procedures for Pg in Python, as i recently learned. MySQL is adding Pg features one by one (ie  lacked transactions for a while), but AFAIK no plans to add that one - and I do like it! :-)

---

### Post by mssever on 2008-03-13
> **frankos44 said:**
> PHP5 is a good language because it integrates well with mysql database and is the perfect choice for web page development. It can also be used without browser for  local apps when the cli is installed.

I used to think that, until I learned a few other languages and realized what I was missing. Now, I try to avoid PHP whenever practical. It's still good for quick projects that don't justify loading up a whole web framework, but other than that, PHP is just too annoying when compared with Ruby or Python.

---

### Post by frankos44 on 2008-03-14
The problem here is there is no answer. Firstly there are 3 things to consider.

1. Where is the software going to run, locally of on a web server.

2. Do you need this software to be cross platform

3. In some cases a compiled program is the best choice while in other cases a scripting language is a better choice.

Here are some quotations from "Ubuntu Unleashed".

PERL
"Perl appeals to many Linux system administrators  because it can be used to fill the a gap between the capabilities of shell scripts and compiled C programs".

PHP
"Part of the success of PHP has been its powerful integration with databases", "PHP is a cross between Java and Perl" and the "General style of writing borrowed from C"

PYTHON
"As PHP had come to dominate the world of web scripting, Python is increasingly dominating the world of command line scripting"

MONO
"Compile once run anywhere"

My background skills started with assembler programming for micro-controllers followed by C. It depends on your needs. In my case I am now a web developer and PHP is the best choice for me with its good object orientated and strong MYSQL integration capabilities.

I am currently programing in C for my widgets and PHP together with a raft of browser client side scripting for work. The latter pays for my groceries. 

Language of choice will always be C.  Python is slightly interesting but looks as if I can do what python does in C anyway, In my case quicker and thats only down to familiarity, however Python being a scripting language could be a plus point sometimes.

In a nutshell, don't wear blinkers.

---

### Post by themusicwave on 2008-03-14
> **frankos44 said:**
> 
MONO
"Compile once run anywhere"


If you really want to get close to Write Once run Everywhere you should  be using Java.  The whole write once run everywhere thing isn;t always perfect, but Java is pretty close.

Mono is a nice idea, but lets face it, C# is Microsoft's attempt to destroy Java and lock people into Windows.  It was never intended to run anywhere, but Windows and the Mono version will always lag behind the Microsoft one in features.  

Why someone would want to use Mono instead of Java is puzzling to me, especially now that Java is open source.

I say this as someone who writes code in a variety of languages for a living including C#, Java, VBScript, and python.  It's a strange mix I know...

---

### Post by ukripper on 2008-03-14
> **themusicwave said:**
> If you really want to get close to Write Once run Everywhere you should  be using Java.  T

Exactly!

---

### Post by pmasiar on 2008-03-14
It is a standard [Shibboleth](http://en.wikipedia.org/wiki/Shibboleth) test in Perl community that if someone writes PERL, s/he lacks any clue or standing about anything written in that comment. :-) Just to warn you for next time. For any programmer, spelling and case is important, IMHO. So it is C, and MySQL. :-)

> **frankos44 said:**
> Language of choice will always be C.  Python is slightly interesting but looks as if I can do what python does in C anyway, In my case quicker and thats only down to familiarity, however Python being a scripting language could be a plus point sometimes.

In a nutshell, don't wear blinkers.

Yup, the last advice applies to you to :-) It seems like classic case of [blub](http://en.wikipedia.org/wiki/Blub) programmer. It is hard to take seriously advice from someone not seeing difference between dynamically typed OOP language like Python and statically typed non-OOP like C.

---

### Post by frankos44 on 2008-03-14
> **themusicwave said:**
> If you really want to get close to Write Once run Everywhere you should  be using Java.  The whole write once run everywhere thing isn;t always perfect, but Java is pretty close.

Mono is a nice idea, but lets face it, C# is Microsoft's attempt to destroy Java and lock people into Windows.  It was never intended to run anywhere, but Windows and the Mono version will always lag behind the Microsoft one in features.  

Why someone would want to use Mono instead of Java is puzzling to me, especially now that Java is open source.

I say this as someone who writes code in a variety of languages for a living including C#, Java, VBScript, and python.  It's a strange mix I know...

I agree

---

### Post by frankos44 on 2008-03-14
> **pmasiar said:**
> It is a standard [Shibboleth](http://en.wikipedia.org/wiki/Shibboleth) test in Perl community that if someone writes PERL, s/he lacks any clue or standing about anything written in that comment. :-) Just to warn you for next time. For any programmer, spelling and case is important, IMHO. So it is C, and MySQL. :-)



Yup, the last advice applies to you to :-) It seems like classic case of [blub](http://en.wikipedia.org/wiki/Blub) programmer. It is hard to take seriously advice from someone not seeing difference between dynamically typed OOP language like Python and statically typed non-OOP like C.

Now now ha ha!

---

### Post by LaRoza on 2008-03-14
> **themusicwave said:**
> If you really want to get close to Write Once run Everywhere you should  be using Java.  The whole write once run everywhere thing isn;t always perfect, but Java is pretty close.

I say this as someone who writes code in a variety of languages for a living including C#, Java, VBScript, and python.  It's a strange mix I know...

The Java platform (not language) can be used with more than just Java. Python and Ruby can be used as well.

That is not  a strange mix. They are all similiar languages (in that there are some very different ones out there)

---

### Post by Wybiral on 2008-03-14
> **frankos44 said:**
> Python is slightly interesting but looks as if I can do what python does in C anyway, In my case quicker and thats only down to familiarity

Like: classes, closures, lambdas, decorators, dictionaries+lists, generators, list comprehension, generator expressions, dynamic code execution (eval/exec), default arguments, ..., exception handling. Those are just some of the features I can name off the top of my head, and that's not even mentioning the MASSIVE standard library that comes with Python.

Sure, you could write your own dictionary (hashtable) or list implementations in C, but it would be a major waste of time that could be spent developing your actual applications (not to mention the extra effort to test and debug them).

The only "advantage" C has is runtime / memory efficiency, but since Python and C are such good friends (google: SWIG / PyRex / ctypes) that's not even clearly an advantage.

---

### Post by themusicwave on 2008-03-14
> **LaRoza said:**
> The Java platform (not language) can be used with more than just Java. Python and Ruby can be used as well.

That is not  a strange mix. They are all similiar languages (in that there are some very different ones out there)

Good point about the other platforms.

---

### Post by CptPicard on 2008-03-14
> **frankos44 said:**
> 
"Part of the success of PHP has been its powerful integration with databases"

Read: in the 1990s people used to embed SQL queries straight into HTML. Easy, maybe, and thus popular... and "powerful" in the brute force sense, but hardly elegant or the Right Way To Do It. Pretty much all other languages integrate with databases just as well.

> "PHP is a cross between Java and Perl" and the "General style of writing borrowed from C"

Somehow, this sounds to me like a big minus instead of a plus.. ;)

{quote]PHP is the best choice for me with its good object orientated and strong MYSQL integration capabilities.[/quote]

OOP in PHP is an afterthought that was tacked on it because otherwise it produced "C embedded in HTML". Which was Not  Good.... the MySQL integration capabilities exist everywhere else as well.

> 
Language of choice will always be C.

Why on Earth? :) There's so much more expressive power and speed of coding to be found elsewhere. Use C when you must, others always when you can.

> Python is slightly interesting but looks as if I can do what python does in C anyway

Admittedly some of Python's abstractions could be even more powerful (proper lambdas come to mind as first thing), but seriously, implementing high-level concepts in Python is much simpler than in C. And if you ever need the speed, interfacing the two isn't too hard.

Programming should always be about raising your level of abstraction...

---

### Post by Wybiral on 2008-03-14
> **CptPicard said:**
> Programming should always be about raising your level of abstraction...

Absolutely. I don't know about anyone else, but I don't program because I love to type or because I love to implement everything on my own. I program because I have an idea that I want to see come to life or a problem that I need to solve. The logical solution is to find a language that's going to do as much work FOR you as possible while still being expressive enough to solve your problem.

---

### Post by frankos44 on 2008-03-15
Ok guys.... yur ganging up on me now. I am so familiar with PHP and C so naturally I would be slightly biased. 

I better take a closer look at Python in my tea breaks. Like i said, "you cant wear blinkers", one must practice what you preach!

---

### Post by frankos44 on 2008-03-15
I just thought about the the initial thread  "how to be a Ubuntu programmer". The poor guy must be even more confused now than when he initially started the thread.

---

### Post by pmasiar on 2008-03-15
> **frankos44 said:**
> Ok guys.... yur ganging up on me now. I am so familiar with PHP and C so naturally I would be slightly biased. 

I better take a closer look at Python in my tea breaks. Like i said, "you cant wear blinkers", one must practice what you preach!

Yup. Learning same functionality in Python what PHP has will be easy. Learning different functionality (above PHP) will be harder, because right now "you don't need it" - you learned to live without it. 

It is like chicken grown in huge hangar, noticed door opened to the outside: but outside does not look familiar, who would want to go there? :-) But once you try new features, you will realize that C and PHP lack them - and you will be enlightened :-) You will be better programmer after the experience.

And you need to learn up about [Model-view-controller](http://en.wikipedia.org/wiki/Model_view_controller) to understand why mixing SQL, HTML and code (PHP or any else) in one file makes people cringe.

---

### Post by frankos44 on 2008-03-15
> **pmasiar said:**
> Yup. Learning same functionality in Python what PHP has will be easy. Learning different functionality (above PHP) will be harder, because right now "you don't need it" - you learned to live without it. 

It is like chicken grown in huge hangar, noticed door opened to the outside: but outside does not look familiar, who would want to go there? :-) But once you try new features, you will realize that C and PHP lack them - and you will be enlightened :-) You will be better programmer after the experience.

And you need to learn up about [Model-view-controller](http://en.wikipedia.org/wiki/Model_view_controller) to understand why mixing SQL, HTML and code (PHP or any else) in one file makes people cringe.

As it happens I dont mix markup, sql and php together. I use objects to do the work for me wherever possible, having said that the objects are complex and difficult to write and do contain a mixture but once written they are are forgotten. 

I am always a bit concerned over "Generated mark up" from a program I have not written because it rarely validates against "W3C strict specification" something I am particular about on website projects. Not sure how Python fits in here or even if python is a good choice for web development.

---

### Post by CptPicard on 2008-03-15
> **frankos44 said:**
> 
I am always a bit concerned over "Generated mark up" from a program I have not written because it rarely validates against "W3C strict specification" something I am particular about on website projects. Not sure how Python fits in here or even if python is a good choice for web development.

In your typical TurboGears app you never generate HTML in code, but it's in the view part which consist of XHTML kid templates. You can even view the templates on your browser and/or validate them separately, and all your Python is in the controller/model layer.

---

### Post by ruy_lopez on 2008-03-15
> **Wybiral said:**
> I program because I have an idea that I want to see come to life or a problem that I need to solve. The logical solution is to find a language that's going to do as much work FOR you as possible while still being expressive enough to solve your problem.

I agree in principle. However, implementing a solution using abstractions you have created yourself can be even more rewarding. It all depends on the scale of the enterprise. Some problems are so unwieldy you cannot.

And there's different levels of abstraction. Using berkely db, for instance, might be considered low-ish level these days, but it wasn't always so. C itself was once considered high-level, and expensive to run.

The determining factor is the level of control you need. If you need more granularity, drop down a level, if not, use the most adaptable labour-saving solution.

---

### Post by imax36581 on 2008-03-15
if you are forget it i'll remember that the subject of this topic is **how to be a ubuntu programmer**....not discuss about some features that we do not need in this topic ;)
thanks again

---

### Post by CptPicard on 2008-03-15
> **imax36581 said:**
> if you are forget it i'll remember that the subject of this topic is **how to be a ubuntu programmer**....not discuss about some features that we do not need in this topic ;)


Well, you can always take home the lesson from this that *how you become an ubuntu programmer* is equivalent to *becoming a versatile, competent programmer in general*, who knows how to make use of the various solutions available on Ubuntu.

If you hang out here long enough and read the postings of the more experienced forum members, you will find out that they have advanced beyond the level where they derive pleasure from "writing it all by themselves". They most certainly could, but that is not the point -- the coolness factor is making use of suitable abstractions that fit the  bill for a certain problem.

And mind you, those high-level abstractions are not the easy way out intellectually -- try Scheme's continuations, which originally gave me much headache when I first met them -- or Haskell's monads, which currently are giving me trouble. But I intend to understand them and ultimately use them, as Haskell seems like something that both expresses some problems of mine in 50 lines of code, *and* compiles to native for speed as well.

On Ubuntu, you don't wear blinkers and most importantly, try not to become a blub programmer... ;)

EDIT: One slightly more specific answer would certainly be to learn about UNIX-like platforms. But even that applies more to C/C++ programmers...

---

### Post by LaRoza on 2008-03-15
> **CptPicard said:**
> 
And mind you, those high-level abstractions are not the easy way out intellectually -- try Scheme's continuations, which originally gave me much headache when I first met them -- or Haskell's monads, which currently are giving me trouble. But I intend to understand them and ultimately use them, as Haskell seems like something that both expresses some problems of mine in 50 lines of code, *and* compiles to native for speed as well.

On Ubuntu, you don't wear blinkers and most importantly, try not to become a blub programmer... ;)

Yes, I am on Monads also (fun to learn, a little tricky for someone just learning)

I am learning Haskell as well...

I agree with everything you said, programming transcends the platform and language.

---

### Post by ghostdog74 on 2008-03-15
> **imax36581 said:**
>  **how to be a ubuntu programmer**....
so after all these, what's your conclusion? if you are still confused, then learn how to make money instead.

---

### Post by imax36581 on 2008-03-15
i know that the best programmer must know the best languages that can help him to create the best program.
but the important note is im a human ;)...i cant learn three or four or.... languages at the same time ..but im **trying to** if i learn a language i become a master in it.
exept programing i must learn my university book,and of course im a newbie in ubuntu and i i say it  better in linux... i must know all of the thing that i can,all of the thing that help me to be a better programmer and so on.
if i divided my interest in computer i can divided it in to: 1.network and specially network security 2.programming after i work with windows server 2003 i understood that network security in windows server 2003 = 0 and  for me its too late to came back and study linux so the other intrest of me can help me to secure my network with learn to how to use program  and programing to secure my network with linux so i must start learn  programming in linux and after that learn that how can i use programming to secure my network.

sorry....im not chatty but i must say that things.
thank you very much....

---

### Post by CptPicard on 2008-03-15
Being a competent network administrator is a different issue from being a programmer. Being a programmer is not going to help you much making your boxes secure. Moreover, becoming a Linux programmer is not going to help you make a Windows box secure ;)

Linux is a good platform to learn about networking on, though. Lots of material out there on the net about it, and while you're at it, you will learn a lot about the UNIX/Linux platform as well... also those things that will help you become a better Linux programmer using those tools that are more platform-specific.

---

### Post by imax36581 on 2008-03-15
> **CptPicard said:**
> Being a competent network administrator is a different issue from being a programmer. Being a programmer is not going to help you much making your boxes secure. Moreover, becoming a Linux programmer is not going to help you make a Windows box secure .
thats true
but my means it i khow that i come on to linux to learn about it and after it i learn programming in it.
maybe i can learn to create network program that provide a special feature to secure more my linux (not my win server 2003 ;) ).but first i must khow how can i learn it.
in other way i like programming in linux,even my program do not secure some thing for example sending mail or maybe messengers or totally about network.....just it.
thanks again.

---

### Post by mssever on 2008-03-15
@imax36581:
You might be interested in reading [*The Art of UNIX Programming*]("http://www.catb.org/%7Eesr/writings/taoup/html/index.html") by Eric S. Raymond (a.k.a. ESR). ESR is one of the more influential open source programmers, and this book addresses UNIX programming from a philosophical, language independant, perspective. It isn't so much a how-to book as it is a why-to. It would be relevant both to a programmer and a system administrator.


@frankos44:
I used to be in your position. There was a time when I really liked PHP a lot and argued that if you knew PHP, you didn't need any other language for server-side web work. Now that I've learned more languages, I'm amazed at how ignorant I was and didn't even realize it. Nowadays, I avoid PHP as much as possible, because I know other languages that provide useful features that PHP doesn't have, and avoid PHP's pitfalls. I'm still glad that I learned PHP; it taught me the basics of programming. But I've moved on, and I think that most of the other programmers here (most of whom are probably more experienced than I am) have moved on, too.

---

### Post by imax36581 on 2008-03-15
[QUOTE=mssever;4521920]@imax36581:
You might be interested in reading [*The Art of UNIX Programming*]("http://www.catb.org/%7Eesr/writings/taoup/html/index.html") by Eric S. Raymond (a.k.a. ESR). ESR is one of the more influential open source programmers, and this book addresses UNIX programming from a philosophical, language independant, perspective. It isn't so much a how-to book as it is a why-to. It would be relevant both to a programmer and a system administrator.

10x

---

### Post by pmasiar on 2008-03-15
> **mssever said:**
> [*The Art of UNIX Programming*]("http://www.catb.org/%7Eesr/writings/taoup/html/index.html") ... ESR is one of the more influential open source programmers,


ESR is more **vocal** than influential.:-)  But he **is** quite extrovert (a rarity between hackers), knows how to write clearly, and is not afraid of self-promotion. He is more influential **writer** than hacker, IMHO :-)

But his books/essays **are** worth to read, many of terms he coined ("cathedral and bazaar" etc) became commonplace. He was also influential in making Mozilla code free, and in founding more pragmatic and business-friendly "Open Source" vs "Free" software. See his wikipedia page.

---

### Post by Wybiral on 2008-03-15
> **ruy_lopez said:**
> I agree in principle. However, implementing a solution using abstractions you have created yourself can be even more rewarding. It all depends on the scale of the enterprise. Some problems are so unwieldy you cannot.

Solving the problem should be the reward, not doing the work. Some people workout to stay healthy, others workout because they like to "feel the burn". But if your goal is to solve a problem, you should aim for the least painful solution possible. But I do agree that the pain can be fun sometimes. I still write assembly and C code these days for fun. I don't, however, use it when I need to solve an actual problem (unless my problem requires the expressiveness that they provide).

> **ruy_lopez said:**
> The determining factor is the level of control you need. If you need more granularity, drop down a level, if not, use the most adaptable labour-saving solution.

Yes, that's sort-of what I was getting to:

[quote=Wybiral]
The logical solution is to find a language that's going to do as much work FOR you as possible while still being expressive enough to solve your problem.
[/quote]

By expressive, I mean capable of adequately expressing the problem at hand. If the problem is to create a device driver, you might not be able to get away with using a higher level language because they won't offer the expressiveness in terms of low-level control that you need. Luckily, most of my software isn't anywhere near that low of a level, so I can use whatever language does the most work for me.

---

