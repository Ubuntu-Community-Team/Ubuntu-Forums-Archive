---
title: "Can you direct me to the right path?"
date: 2008-02-17
forum: Programming Talk
---

### Post by mortizx on 2008-02-17
During the 10 years of my career, I’ve dealt with many types of Microsoft Windows applications, hardware and networking issues successfully from providing support to bringing up and configuring servers and warehouse databases.

I decided after 9/11 to start a remodeling company in order to bring in sufficient funds for the last 6 years, which I am no longer interested in continuing. I want to get back to my technical field. I would like
to learn Linux, so, the only programming language I used before was VB. What are my steps to learning linux in and out and programming in it? Im very rusty, and I want to learn network administration also.

Please Help...

---

### Post by 1337455 10534 on 2008-02-17
If you are going to be using Linux for adminstration mainly, be comfortable with BASH [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html) and Python.
Both are extremely useful.
No BASH means no work gets done.
Python isn't really meant for system management, but is very scalable, powerful, and awesome for the rapid application development you may be used to ([http://www.python.org/](http://www.python.org/), [http://glade.gnome.org/](http://glade.gnome.org/)). Python and BASH are installed by default on pretty much all Linuxes too.

---

### Post by mortizx on 2008-02-17
Thanks, but I want to be able to be part of ubuntu in development process, which language should I learn first.  There is lots of talk about jave, cpp, c, python... pretty confused.

---

### Post by LaRoza on 2008-02-17
> **mortizx said:**
> Thanks, but I want to be able to be part of ubuntu in development process, which language should I learn first.  There is lots of talk about jave, cpp, c, python... pretty confused.

A quick guideline that I give those with no heavy requirements and who want to program.

Start with Python, then learn C, then Lisp.

See my wiki for information on these languages, you will find Python pretty easy to start with.

The reasoning:

* Python is used heavily in Ubuntu, and is very powerful and multipurpose. It is crossplatform and can be used with C easily.
* C is what Linux and most apps are programmed in. It is low level, and requires an understanding of how computers work to use effectively. Learning a higher level language like Python makes it easier to focus on the power of C, rather than trying to wrestle with programming concepts and C itself.
* Lisp:
[quote="Eric Raymon"]
"Lisp is worth learning for the profound enlightenment experience you will have when you finally get it; that experience will make you a better programmer for the rest of your days, even if you never actually use Lisp itself a lot."
[/quote]

---

### Post by ruy_lopez on 2008-02-17
It depends on what level of the process you are aiming at. If you are comfortable with the nitty-gritty of interfacing with hardware, learn C. C is also used for a lot of enterprise grade servers. If you are more comfortable developing GUI interfaces, higher level languages are better. It depends on the package. Not everything shipped with Ubuntu is developed by Ubuntu. Each package maintainer has his/her own approach. Python is apparently easy to learn. Familiarize yourself with the network admin utilities and daemons available in Ubuntu, then download the source, and see what language it uses.

---

### Post by mortizx on 2008-02-17
So, basically, start with learning all linux commands, then learn bash, then learn python?  Do you recommend any good books?

---

### Post by LaRoza on 2008-02-17
> **mortizx said:**
> So, basically, start with learning all linux commands, then learn bash, then learn python?  Do you recommend any good books?

You should start with Python. Bash (and Shell scripting) is good for using Linux, but development is not usually done in it.

See my wiki, before buying any books. In the sticky, there is a link to a thread on books we recommend, see that thread first.

---

### Post by mortizx on 2008-02-17
Thanks again to everyone here......:KS

---

### Post by CptPicard on 2008-02-17
Don't bother too much with bash (except up to the point of being a "power-user") if you're more into application development... if you need to do system administration so much you really need bash, you will know it when you need it, and will learn it as you go. Python+C is a good start.

---

### Post by mortizx on 2008-02-17
I was told if I can learn Cpp instead of C would be better productivity.  What do you think?

---

### Post by Fbot1 on 2008-02-17
> **mortizx said:**
> I was told if I can learn Cpp instead of C would be better productivity.  What do you think?

Learn C first. If you know C then C++ will be simple.

---

### Post by mortizx on 2008-02-17
Thanks Again....

---

### Post by LaRoza on 2008-02-17
> **mortizx said:**
> I was told if I can learn Cpp instead of C would be better productivity.  What do you think?

They are entirely different languages. C is C, C++ is C++.

They are used differently, and should never be thought of as the same language.

---

### Post by CptPicard on 2008-02-17
> **Fbot1 said:**
> Learn C first. If you know C then C++ will be simple.

C++ is actually way more complex than C... it really is...

---

### Post by Fbot1 on 2008-02-17
> **CptPicard said:**
> C++ is actually way more complex than C... it really is...
Considering that a lot of it's features are generally not used (at least from what I've seen), the stuff he/she will probably see wont be too much harder.

---

### Post by CptPicard on 2008-02-17
What's the point of using C++ if you're not making use of its features?

All modern half-decent C++ code makes use of a lot of advanced stuff, for example templates...

---

### Post by scruff on 2008-02-17
Also, read [this book]("http://rute.2038bug.com/index.html.gz"). It is a good free online intro to many aspects of Linux administration.

---

### Post by mortizx on 2008-02-17
So stick with C first?
Also, should I learn the languages in this order? (python, c., lisp)
What about JAVA, leave that alone for now?  Isn't it crossplatform?

---

### Post by CptPicard on 2008-02-17
Lisp is more of an "enlightenment about the zen of programming" language... I like it, I don't really use it :p

Java is an ok tool to get a crossplatform job done, but if you're interested in *Linux* programming, why invest in that capability? There's nothing really great about the language itself, and it forces you on top of a big VM too.

---

### Post by ghostdog74 on 2008-02-17
> **mortizx said:**
> 
I would like
to learn Linux, so, the only programming language I used before was VB. What are my steps to learning linux in and out and programming in it? Im very rusty, and I want to learn network administration also.

Please Help...
the first step to learning Linux, is to learn how the OS came about and how it works, not how to program in a language. By that, you should probably search the net using google or go to your library for some "Unix internals" books and materials...After that, you can learn shell scripting. Its a must if you want to learn about linux and want to do network admin in linux. after that you can learn other things if you want.

---

### Post by ghostdog74 on 2008-02-17
> **mortizx said:**
> So stick with C first?
Also, should I learn the languages in this order? (python, c., lisp)
What about JAVA, leave that alone for now?  Isn't it crossplatform?
learn how the OS works and its internals. A [random search]("http://www.cyberciti.biz/tips/understanding-unixlinux-file-system-part-i.html").

---

### Post by CptPicard on 2008-02-17
Bash (or any other specific shell) != Linux.

I started with Linux in 1996 and have set up a Linux From Scratch box and was a Gentoo user for years, and I have never written a non-trivial bash script.

You can set up any binary as your login shell.

Admittedly, in actual network/sysadmin work avoiding bash may be difficult, but as pmasiar pointed out a long time ago, if you want to be a "developer", knowing as much bash as you need to pick up at any given time is usually sufficient.

---

### Post by Fbot1 on 2008-02-17
> **CptPicard said:**
> What's the point of using C++ if you're not making use of its features?

All modern half-decent C++ code makes use of a lot of advanced stuff, for example templates...

Sure it will but, my point it wont use most of them.

---

### Post by CptPicard on 2008-02-17
> **Fbot1 said:**
> Sure it will but, my point it wont use most of them.

Such as..? :)

Idiomatic, proper C++ is far from C exactly because of C++ features being made heavy use of. You pretty much have to know "all of them" in order to be competent. That's why C++ can have a steep learning curve.

---

### Post by mortizx on 2008-02-17
lol...NOW IM REALLY CONFUSED....  A reminder, I've dealt with, supported, administer and program VB in Windows since 3.11- Windows 2000...  But because I havent been in the technical arena for 6 years, and I want to return to a stable market and I think linux is going there.  So, I have done some programming and a lot of TSQL with SQL Server.  So, im not new to the technical arean, just confused.....  I know everyone has some  great opinions, but the one im looking for, im hoping directs me to the correct proficent way....

---

### Post by CptPicard on 2008-02-17
It really shows you're coming from the Microsoft world... see, there is no "correct proficient way". Linux is a great open platform for all sorts of approaches, and you just need to find the one that suits you best.

Considering you're coming from VB, I think Python would suit you best to get you hacking on Linux.

---

### Post by ghostdog74 on 2008-02-17
> **mortizx said:**
> lol...NOW IM REALLY CONFUSED....  A reminder, I've dealt with, supported, administer and program VB in Windows since 3.11- Windows 2000...  But because I havent been in the technical arena for 6 years, and I want to return to a stable market and I think linux is going there.  So, I have done some programming and a lot of TSQL with SQL Server.  So, im not new to the technical arean, just confused.....  I know everyone has some  great opinions, but the one im looking for, im hoping directs me to the correct proficent way....
what are you planning to do eventually? you have mentioned network admin. So i presume you want to set up networks  etc etc? you should probably describe what's your ultimate goal. also 
Python !=Linux.

---

### Post by mortizx on 2008-02-17
Ultimate goal is to be marketable as fast as I can.  As mentioned before, I come from a Microsoft World, supporting systems, users, hardware and programming applications and SQL.  I've done very little C years ago, then I stop once VB came out..  So, Linux (UBUNTU) seems to be a system I would like to know in and out and to become part of the community in making it better.  Is it like learning DOS all over again?

---

### Post by CptPicard on 2008-02-17
> **mortizx said:**
> Ultimate goal is to be marketable as fast as I can.  ... Is it like learning DOS all over again?

It's much, much more than like learning DOS over again. I'd say becoming a Linux/UNIX geek is a lifelong development, a bit like becoming a programmer... it really is a system you need to become an "expert" in at your own pace by getting to know how all the various bits and pieces fit together, and that there really is no royal road to philosophy, you know?

There are some good online books that give you a decent overview of the system, you should google for them... I'll try to think of the name of the one I'm thinking of in particular...

EDIT: here's one iintro text: [http://tldp.org/LDP/intro-linux/intro-linux.pdf](http://tldp.org/LDP/intro-linux/intro-linux.pdf)  (pay no attention to the chapter about the Vile Insult text editor though)  -- [http://tldp.org/](http://tldp.org/) is full of linux docs in general, dive in...

---

### Post by Fbot1 on 2008-02-17
> **CptPicard said:**
> Such as..? :)

Idiomatic, proper C++ is far from C exactly because of C++ features being made heavy use of. You pretty much have to know "all of them" in order to be competent. That's why C++ can have a steep learning curve.

Well, just look at the source of PAQ. Regardless, our experiences are obviously going to be different.

---

### Post by mortizx on 2008-02-17
Thanks all for your advice..................

---

### Post by pmasiar on 2008-02-18
OP: Looks like you are more database application programmer, not a systems programmer (which uses more C) or administrator (who uses bash a lot). Python + SQL will cover most of your application programming needs. You may consider learning C just in case you will need more raw speed, but with database application fine-tuning SQL has better ROI, IMHO, so you may as well ignore C for couple years without much hurting yourself. In C, you can write libraries (for speed) and link them to your Python code, but likely all that low-level code is available and you just need to do business logic.

You also need to consider which database you want to switch to: MySQL and Postgres are excellent and free.

Not sure if you want desktop application or web-based apps, they of course use different approach. Yes I've seen some VB ASP pages and it was mess, don't do that anymore: [Model-view-controller](http://en.wikipedia.org/wiki/Model-view_controller) approach results in much cleaner code.

See wiki in my sig for links, "Dive into Python" should be just the book you need.

BTW you don't have to thank for advice - forums have button for that, to the left from "Quote" :-)

---

### Post by slavik on 2008-02-18
If you want to do system administration, you will have to learn Perl.

---

### Post by LaRoza on 2008-02-18
> **slavik said:**
> If you want to do system administration, you will have to learn Perl.

True, but after learning programming. No point in having this poster learn all the useful languages at once.

---

### Post by slavik on 2008-02-18
> **LaRoza said:**
> True, but after learning programming. No point in having this poster learn all the useful languages at once.
Is it me or did you go against learning just now? I thought you would be unbiased ... :(

---

### Post by LaRoza on 2008-02-18
> **slavik said:**
> Is it me or did you go against learning just now? I thought you would be unbiased ... :(

No, the poster has a full stack, I don't want an overflow which would discourage learning.

Not against Perl in anyway, I don't want a beginner to feel overwhelmed, which is easy for us to do.

(It is difficult to remember, even for me, what it was like in the beginning.)

---

### Post by ghostdog74 on 2008-02-18
the OP has chosen his path. Let's put this thread to RIP.

---

### Post by mortizx on 2008-02-18
I have ubuntu desktop, should I upgrade to server?

---

### Post by LaRoza on 2008-02-18
> **mortizx said:**
> I have ubuntu desktop, should I upgrade to server?

Do you need a server?

To get the LAMPP:

```

sudo tasksel

```

Don't uncheck anything!

---

### Post by mortizx on 2008-02-18
What do you think of Ada?

---

### Post by LaRoza on 2008-02-18
> **mortizx said:**
> What do you think of Ada?

She's nice. The first programmer, also a female. Quite an achievement.

Oh, you mean the language? It is used for many things, mostly things that fly. It is very strongly typed. 

I don't recommend using it unless you have a reason to. It is a developed programming language, but most applications won't need that kind of static typing.

---

### Post by mortizx on 2008-02-18
how can I see my post responses with out having to refresh and find my post again

---

### Post by mortizx on 2008-02-18
like for example, an alert or something that does not have to do with email

---

### Post by slavik on 2008-02-18
As for ADA, I will just support what LaRoza said. It is heavily used in airplanes (not the entertainment system) and control tower systems. At a programming contest, the ones to use ADA are usually in a branch of the military (this is in USA). :)

---

### Post by pmasiar on 2008-02-18
> **mortizx said:**
> What do you think of Ada?

[http://en.wikipedia.org/wiki/Ada_%28programming_language%29](http://en.wikipedia.org/wiki/Ada_%28programming_language%29) is language used by military contractors. Unless you are one, I do not see a reason to use it. Might be interesting to learn it to see how language might have even stronger types than C/C++/Java has. But Ada is quite old to be used in casual programming.

---

