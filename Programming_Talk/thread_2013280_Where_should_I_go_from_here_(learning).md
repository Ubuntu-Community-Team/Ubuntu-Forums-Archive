---
title: "Where should I go from here (learning)?"
date: 2012-06-30
forum: Programming Talk
---

### Post by JackOConnor on 2012-06-30
Ok, I'm 15 and I have been learning java for some time now. I did all the tutorials on this website [http://www.java-made-easy.com]("http://www.java-made-easy.com/")

At the moment I am working through problems on project euler and the beginner programming problems here, [http://ubuntuforums.org/showthread.php?t=1714324](http://ubuntuforums.org/showthread.php?t=1714324)

I want to know where should I go next? I want to work on linux and someday hopefully my own distro:smile: So I want to learn as many languages as possible without rushing through them.

Oh and I am currently running ubuntu 11.10 but I'm thinking of switching to debian to try out a different distro and because I was told before that ubuntu works too well "straight out of the box" to learn much from it.

So I have the following questions:

[LIST=1]
[*]Is the website I learned java from good? Does it leave anything important out?
[*]Should I continue with java alone or start learning a new language alongside it? And if I should continue with just java for now, how will I know when I'm ready to move on?
[*]Where can I learn to apply what I have learned to large scale projects and real world situations rather than to the really fun but theoretical problems I am currently doing (project euler)?
[*]How can I start working on linux? Do I need more experience? Do I need to learn c/c++ or any other language first?
[/LIST]
Oh and I read the FAQ!!!\\:D/

If someone could answer my queries I would be very grateful.

---

### Post by llanitedave on 2012-06-30
Not coming from an expert here, but if it's distros you're interested in, I think in addition to Java, C and Python are going to be involved.

---

### Post by JackOConnor on 2012-06-30
Yea that's what I thought alright, except I'm not sure if you need java too much for it, but hey knowledge is power!

---

### Post by gardnan on 2012-06-30
What exactly do you mean by working on "Linux"? That could be ambiguous. 
However, if you are talking about the Linux Kernel, then you have to know C. And I mean *know* C.

---

### Post by JackOConnor on 2012-06-30
I mean contribute to distros. I'd probably want to start off with something like fixing bugs, is that correct? Also can you answer any of my other questions?

---

### Post by trent.josephsen on 2012-06-30
I made a cursory examination of the Java tutorials you linked, and I'll say that they seem to be accurate, but very simplistic in their treatment of Java. That's not a criticism, merely an observation; they look to be effective at their real purpose: introducing beginning programmers to Java. (Notice that although they have sections labeled "Beginner's", "Intermediate" and "Advanced", all the stuff there is really just the baseline, entry-level knowledge for programming in Java; you'll need practice to become useful.)

As for distros, you can reasonably develop just about anything under Ubuntu, but if you're thinking of switching distros or adding a new one *as a learning experience*, I recommend Gentoo to you, for several reasons:

1) It's different from any Debian-based distro in terms of installation and maintenance, so you'll get a broader experience than just Debian derivatives.
2) The Gentoo install process is very transparent and very technical; you'll learn a lot about how distros are put together. Notably, configuring and compiling your own kernel is one of the first things you'll do, and you'll have to do a **lot** of that if you want to get into distro development.
3) Maintaining Gentoo involves a great deal of care and technical know-how. It's fairly easy to install Gentoo, less easy to use it for your day-to-day activities, and downright difficult to keep it running smoothly every day for a long time. But you'll learn by doing and by having fewer decisions made for you by the developers and packagers.
4) Not much of an argument -- but Gentoo comes with development tools, and all the header files and source code for installed libraries, by its nature as a source-based distro. Also, you'll normally be compiling against the *latest stable upstream version*, thereby avoiding accidentally writing code dependent on patches and backports done by your distro developers.

I'm not suggesting you should get rid of Ubuntu -- but consider installing Gentoo in a VM, or dual booting.

Best of luck

---

### Post by JackOConnor on 2012-06-30
Firstly, Thank you for your answer. I'll definitely have a look at Gentoo, your reasoning on it seems solid and it appears to be a great way to learn a lot about how distros are put together.

I have a question though, is doing project euler and the other challenges I mentioned the best way to practice my coding skills to become useful or are there better ways?

Thanks for your help!

---

### Post by trent.josephsen on 2012-06-30
I don't know if there's a "best way" to practice coding. Project Euler is cool and most folks seem to like it; it's practice problem-solving if nothing else (I never got very far with it due to lack of interest). But there is no substitute for real-life problems. There's a world of difference between "find the 10001st prime" and "Convert this wiki from the [Confluence](http://www.atlassian.com/software/confluence/overview) format to MediaWiki markup" (which was the first project with real-world application that I worked on).

Project Euler is definitely a way to stay sharp and practice your general problem-solving skills, but when you get a job as a developer, you may wish you knew more about Makefiles, revision control, package management, file management, string manipulation, networking, memory models, or whatever and less about toy math problems.

---

### Post by JackOConnor on 2012-06-30
Although I find project euler enjoyable I want to learn stuff that is applicable in the real world.

So, what would you do if you were in my shoes?

---

### Post by MG&amp;TL on 2012-06-30
> **JackOConnor said:**
> I mean contribute to distros. I'd probably want to start off with something like fixing bugs, is that correct? Also can you answer any of my other questions?

Yup, fixing bugs is a good way to get started, although you'll want to become less specified in terms of programming languages if you want to fix a lot. Browse [http://bugs.launchpad.net](http://bugs.launchpad.net) and go from there.

---

### Post by PaulM1985 on 2012-06-30
I found that a great way to learn was to work on something that I had a personal interest in.  There were many times when I thought that a project I found online was interesting so I got involved but after a while that interest died.

Instead of looking for projects that sound interesting, why not start something of your own.  It could be an application that would make your life easier, or a game, or something else....

For example, when I learnt how to program here are a list of projects I did from scratch on my own, what languages I used and how far I got:
[LIST]
[*]Simple copy of pong - Java - Finished
[*]Media player UI - C++ - Finished, I did this to learn how to use C++ GUI libs in linux, after working out how to connect a wii mote to linux, I had a fancy media player connected to my TV :-)
[*]Distributed pong server so two players can play online - Java - Worked if only two people were ever going to play and connection happened in "the right order"
[*]Cross Platform Remote Desktop App - Java - Worked, but not what I would call finished
[*]Copy of Breakout for Nokia - Java - 2 levels done
[/LIST]

Also, remember, there is nothing wrong with quitting, or taking a break from what you are working on.  You might come back to it in the future, or find that you need it for something and the incentive comes back.

Good luck with what you decide to do.

Paul

---

### Post by JackOConnor on 2012-06-30
That sounds cool alright. I had started playing around with android applications but then the exams came 'round, "There will be plenty of time for you to program over the summer". Then when I got my holidays, I never really got back to it, in fact I forgot all about it!!! 

However, what I want to do someday is make my own distribution of Linux (with some help probably!!!) So, if I want to do that, I'll have to work my way up from the bottom. It'll probably be fun anyway and if I lose interest in one thing I can just move onto something else that takes my fancy!

I am going to recommence my learning of android now!!! I might even make a bit of money out of it and a teen needs his money (no standard income!).

Go raibh mile maith agat! (Thanks in Irish)

---

### Post by David Andersson on 2012-06-30
> **JackOConnor said:**
> 
I have a question though, is doing project euler and the other challenges I mentioned the best way to practice my coding skills to become useful or are there better ways?


I think such challenges are useful. Any practice is good.

You mention learning Linux. I think there are many directions you can take.

**Operating and maintaining systems**. Learn about the boot process, file systems, command line tools, etc. A lot of what you learn in one Linux is applicable to other Linuxes or Unixes.

**Systems programming**. Want to code in the kernel, device drivers, file systems? Learn programming, but also get a thorough understanding of how the **hardware** works.

**Application programming**. Usually involves designing and coding graphical user interfaces. Learning more than one programming language, of course. Learning APIs to databases and other things.

A broad knowledge across the fields is good. You may eventually focus into one. Or maybe you don't. You don't have to decide yet.

Besides pure programming language knowledge, I think it is very important to learn **mathematics** and **logic**. The computer science field use **discrete algebra** alot, but if you choose to be a **calculus** genius it will be very good for you.

Also there is **psychology** and **cognitive science**. How to design the **user interface**, both the broad brush and the details. How should the user explore functionality? How to report errors? What will they expect in different situations?

There are things called **design patterns**. While learning programming you will adopt some design patterns without knowing you do that.

---

Let me tell you a story. I had a technical college education. I was good at Pascal, Basic and Assembly. I tried to make a *structure editor* (combined with an *interpreter*) for a home made simple language. I tried to do it in Pascal. It was difficult. Didn't make it. Then I went to the university studying computer science. First language: *Lisp*. At the same time learned *Abstract Data Types*. Soon I made a structure editor for Lisp, written in Lisp. Then I made the combined structure editor and interpreter for my home made language, in Pascal. It was not so difficult after all.

(Don't forget thinking about error management. I hate programs that fails silently.)

---

### Post by trent.josephsen on 2012-07-01
I concur with most of what David says, but I have a nit to pick.

> **David Andersson said:**
> Besides pure programming language knowledge, I think it is very important to learn **mathematics** and **logic**. The computer science field use **discrete algebra** alot, but if you choose to be a **calculus** genius it will be very good for you.

With you on the first part, lost you by the time you mentioned calculus. <flamebait>In my personal opinion, most of computer science is completely unrelated to programming. CS teaches you to solve Project Euler problems. Programming gets real work done.</flamebait>

It's definitely important to have a solid grasp of algebra. Geometry comes in handy -- you should at least understand Cartesian coordinates even if you don't do graphical stuff. Discrete math, well, it was a lot of fun for me, and there are definitely parallels that might make you a better programmer, but not a replacement for practical experience. Calculus? Not all that useful IMO -- unless your application demands it, and most of them don't. You'll more often be using algorithms you can look up on Wikipedia rather than having to analyze new ones. Especially when waiting for cache, disk, network or input dominates the runtime of your program, as is often the case. YMMV as always.

ESR has an [excellent analysis of that topic in three paragraphs](http://catb.org/~esr/faqs/hacker-howto.html#mathematics) that I recommend. (Actually, I recommend the whole essay.)

---

### Post by Dubslow on 2012-07-01
> **trent.josephsen said:**
> <flamebait>In my personal opinion, most of computer science is completely unrelated to programming. CS teaches you to solve Project Euler problems. Programming gets real work done.</flamebait>

It's less any particular field of mathematics and more the logic, as Dave said. I agree that computer science and programming are two different things -- however there we diverge. 

I'd say computer science is a manner of thinking, a method of solving problems, a style of creativity. Programming is something that happens to

A) Work well in the computer scientist's mindset
B) Has a *lot* of real life applications.

It's easy to be a competent programmer; it's not easy to be a great (some might say elegant or beautiful) programmer. That requires some more mental gymnastics.

In that vein, be less worried about "learning this or that language" and more worried about how to solve problems, how to think like a computer scientist. "Learning that language" is then reduced to learning its syntax for doing things, perhaps with its own few quirks.** In fact, in most other languages, what in English is "Computer Science" is closer to "Informatics" in other languages, and that is more accurate. Computer science is the study of information, how to manipulate information, how to store information, how to communicate information, how to create information, and how to do it all in a timely and efficient manner. Programming is just the means to the computer scientist's ends.

What does that all mean? Well first off, it means you should probably get a handle on C; it's largely similar to Java, except that Java doesn't have pointers. Pointers, of course, are the bread and butter of C, so when I said "largely similar" I meant only on the outside. :D

Then, get yourself introduced to more programming styles. Java has good Object Orientation, C is only Procedural (though I claim with structures and function pointers it can effectively be OO), but there are many more styles out there. Learning how to use make is an absolute must, and will also be a light introduction to 'Declarative' programming. Last but probably most importantly is Functional programming, i.e. Lisp. Unfortunately, I've yet to learn (or take a class) in Functional programming, so I can't tell you much about it, except this quote from the famed [ESR]("http://catb.org/~esr/faqs/hacker-howto.html"):
> LISP is worth learning for a different reason — the profound enlightenment experience you will have when you finally get it. That experience will make you a better programmer for the rest of your days, even if you never actually use LISP itself a lot. That's right in line with what I'm saying about CS vs. Programming. (The rest of his advice on that page is also, of course, very sound, the exception being [When You Really Do Use Lisp In Real Life]("http://www.paulgraham.com/avg.html").)

If you're less interested in the philosophy and more in practical programming, then start right away with Python. (If you're doing ProjectEuler though, you're probably interested in the mindset as well.) It's very easy to Do What You Mean the first time, and combining that with Python's huge standard library, it's probably one of the lowest effort/product ratios of any language. (Of course, it still makes for a very interesting philosophical study, being a mix of almost every programming style, as well as its almost-natural-language syntax. It's probably also the highest "philosophical interest + practicality" score I can think of. :P)


**Major caveat: In order to truly learn a language, you must also become pretty darn familiar with its standard library, which is  exponentially more time consuming than learning just its syntax.

[The Python (3) Tutorial]("http://docs.python.org/py3k/tutorial/index.html")
[My Favorite C Book]("http://publications.gbdirect.co.uk/c_book/")
(I don't have any experience with Perl or Lisp, though I can at least sort-of-not-really read Perl.)



I don't claim to be the first to ever expound these ideas, and I'd credit a large part of my thinking to [this guy]("https://www.google.com/?q=Lawrence%20Angrave"), who also certainly wasn't the first. Edit: Now that I think about it, as trent mentions, the [whole essay]("http://catb.org/~esr/faqs/hacker-howto.html") is worth reading, and much of what I'm saying comes from ESR's [commentary]("http://catb.org/~esr/faqs/hacker-howto.html#attitude") (perhaps from an ever-so-slightly different perspective). My only addition is that if you are of the philosophical bent, as I was/am, learning C first can be fun and interesting, but it's definitely not for the faint of heart or hairless of chest. The analogy of "give you enough rope to hang yourself" applies to C.

One last note about what to do if you're bored or not sure what to do, what you can create that's interesting: Go look through other people's code, and truly understand it. Learn what the problem is by examining someone else's solution. (Just be sure that someone else is actually a good programmer, otherwise it hinders rather than helps.) (PPS: I just went to read ESR's essay myself, and found out that he said almost exactly what I just did: > Learning to program is like learning to write good natural language. The best way to do it is to read some stuff written by masters of the form, write some things yourself, read a lot more, write a little more, read a lot more, write some more ... and repeat until your writing begins to develop the kind of strength and economy you see in your models. IMO, writing your own code is sometimes overemphasized compared to reading others code; be sure to do both.)

(PPPS: The more I read ESR's essay, the more I realize that you can just take my entire post and replace it with his essay. :tongue:)

(PS Besides its own forums, [here]("http://www.mersenneforum.org/forumdisplay.php?f=18") is a good place for ProjectEuler discussion.)

---

### Post by JackOConnor on 2012-07-01
Firstly I'd like to thank everyone for their replies:razz:

Well, about the mathematics and logic thing, no problems there! The reason I started programming apart from thinking that sort of thing is cool was because I was bored of the maths course in school, but that sounds very arrogant. And, one of the reasons I love it is because of the logical challenge. So those are probably some of my favorite things about it!!!

C was what i had planned learning next, and then either python or perhaps c++ and the tutorial that Dubslow mentioned for c looks very good.

So thanks again everyone, you've given me a lot to think about...:-k

---

### Post by Shadius on 2012-07-01
Maybe you should check out [Code Academy]("http://www.codecademy.com/#!/exercises/0"), [W3Schools]("http://www.w3schools.com/"), and [Coursera]("https://www.coursera.org/"). Those should be able to offer something for you.

---

### Post by trent.josephsen on 2012-07-01
@Dubslow I don't think we're really in disagreement. However, I like to stress the differences between CS and "real" programming because of the unwarranted emphasis on so-called "computer science" that dominates academia here in the US and presumably other places.

It's really a problem of poor public understanding and poor high school counseling. If you enjoy taking computer-related courses in high school, your counselor is going to tell you to go to college and major in computer science. (Protip for those still in high school: counselors always tell you to go to college.) They don't distinguish between computer science, software development, and information technology at that level because the differences are not widely understood. (As a hardware engineer, being lumped in with "computer people" all the time infuriates me -- and it happens **all. the. time.**)

Someone I knew once said that there are three kinds of professional programmers, who differ based on their educational background:

1. "Computer scientists", who probably know all about algorithmic analysis, formal languages, data structures, and that kind of thing, but don't often apply it to real-world problems. This is truly a branch of mathematics and calculus is just the beginning for them.

2. Electronics engineers, who by comparison know a lot about computer hardware and electronics. As for myself, I know a reasonable amount of VHDL, assembly, and C, and I consider myself an embedded systems engineer, but I don't really know the first thing about writing user-space applications despite being able to fake it convincingly.

3. Programmers for businesses, who by the work that they do have to know about bookkeeping, administration, workflow or what have you, and write software that automates or glues together real-world processes. This is a little closer to my understanding of "informatics".

I feel that academia (at least in the US) strongly emphasizes category 1, whereas most real-world programming happens in the other two areas. I'm firmly of the opinion that a two-year degree is perfectly adequate to train someone for work as an effective programmer, and certainly preferable to 4 years in a glorified math program. When you're trying to get a job, putting "Perl" on your resume means **way** more than getting an A in Programming Languages.

Which is all to say: Be *informed*, not necessarily *educated*.

---

### Post by Dubslow on 2012-07-01
A wonderful point, however I guess we have different definitions of "real world". All the truly great programmers (you might say "software engineers" or "hackers", the ESR meaning) fall into the first category, and I'd hardly say "calculus is just the beginning". Anything that isn't specifically a particular field, such as dedicated business software (meaning software *for* businesses, not necessarily *by* businesses), falls into category 1, which is a *big* category. All OSs, compilers, interpreters, language designs, OS utilities, and almost all end-user-space software all fall into category 1; I'd hardly call it disconnected from the real world. MS Windows falls into category one (though not all its programmers do *ahem*). It's certainly possible and not-too-hard to get into either category 1 or 3 without a formal education (though for 2 I imagine the electrical engineering stuff isn't easy to learn on your own, and I think the credentials are also more important). 
 
Considering that the vast majority of software out there *is* category 1, I'd hardly say it's overemphasized. Certainly at UIUC no one would mistake a computer scientist for a hardware engineer. (My dorm is full of ECE majors, many more than CS or non-Engineering majors.) Though it is branched from mathematics, at most major colleges CS is a whole separate department, as it should be.

---

### Post by CptPicard on 2012-07-01
> **trent.josephsen said:**
> 
1. "Computer scientists", ...
2. Electronics engineers, ...
3. Programmers for businesses, ...

I feel that academia (at least in the US) strongly emphasizes category 1, whereas most real-world programming happens in the other two areas. I'm firmly of the opinion that a two-year degree is perfectly adequate to train someone for work as an effective programmer, and certainly preferable to 4 years in a glorified math program.

Interesting categorization, one that I guess characterizes programmers quite well. I'm in category 1 by education, in category 3 by profession ;) When hiring new people for the firm, a category 1-background can actually be a bit of a warning sign, as it's possible that we're then dealing with a theory geek who isn't really even all that interested in the day to day real world programming... also, category 2 people can sometimes be too specialized for their own good (thinking of the masses of Symbian programmers that are getting laid off by Nokia here in Finland these days).

My own interest in programming languages and all the philosophy of "how you use them" has really not come from education at all... you need to write some code and think about it in order to get a feel for those things. Also, working with business software really needs some very pragmatic "real life" skills that pure theorists may lack. So in a lot of ways one might say my education in algorithmics was "useless"... but as long as those prerequisites for actually working in development are satisfied, a theorist does bring into the picture some of the things that were drilled into him during the academic education -- capacity for formal reasoning is always useful, and who knows, a need for understanding of some of those theoretical principles that he was exposed to may arise in the course of daily work. And in that case everybody can be pretty out of luck otherwise if a company does not have some people with formal education in the field.

---

### Post by trent.josephsen on 2012-07-01
> **Dubslow said:**
> A wonderful point, however I guess we have different definitions of "real world". All the truly great programmers (you might say "software engineers" or "hackers", the ESR meaning) fall into the first category, and I'd hardly say "calculus is just the beginning". Anything that isn't specifically a particular field, such as dedicated business software (meaning software *for* businesses, not necessarily *by* businesses), falls into category 1, which is a *big* category. All OSs, compilers, interpreters, language designs, OS utilities, and almost all end-user-space software all fall into category 1; I'd hardly call it disconnected from the real world.

I'd call OSes, most compilers and some utilities category 2, and most user space apps, such as ESR's fetchmail, category 3. CptPicard's comment about being in category 1 by education and 3 by profession is very relevant.

I guess I did say "for businesses" on category 3, which may have given the wrong impression. However, since such a huge amount of code in this category is written for businesses outside the software industry, I won't edit it.

I was actually going to say (but had to leave before I got to it) that what I'd call "software engineering" really falls outside of those three categories. If I had to describe such a field, I'd say it encompasses software tools, conventions and protocols, and applying systematic procedures to software development. This is the kind of training that would be most useful to people in a traditional computer science program.

Good discussion :)

Edit: You know, I realize after posting this that I kind of got distracted by the idea of putting *kinds of work* in these categories, when it was really meant to apply to the *people doing the work* in its original context. Regardless, it was not originally my categorization and I disclaim all inadequacies as not my fault ;)

---

### Post by gardnan on 2012-07-01
One thing that I may recommend to the OP is to maybe stick with Java for a little while longer. You probably want to work on a large project in one language before moving to another. I personally think it is better to get lots of practical experience in one language than lots of toy experience in lots of languages.

---

### Post by CptPicard on 2012-07-01
> **gardnan said:**
> One thing that I may recommend to the OP is to maybe stick with Java for a little while longer. You probably want to work on a large project in one language before moving to another. I personally think it is better to get lots of practical experience in one language than lots of toy experience in lots of languages.

Depends... to begin with you'll want to probably have one language that you really are "marketable" in and you can actually use to build things, but I'm a big proponent of exposure to all kinds of languages, in particular to those of differing paradigms. It really develops your thinking about how you program; but that is certainly a process that takes a long time.

---

### Post by JackOConnor on 2012-07-01
Thanks again for even more replies!!!:-)

The websites recommended by Shadius appear to be good at a quick look over so thank you for those. 

I think that what I will do now is stick with java alone for at least a little while longer so I can become "marketable" in it. But I'm going to install Gentoo alongside Ubuntu as a learning experience. I'll probably also go back to more android aswell (I have some ideas that will at least make my life easier if no one else's). 

Just one question, what does gardnan mean by a large project? I'm thinking an android application?

Thanks again everyone!!!:smile:

---

### Post by gardnan on 2012-07-01
I guess I didn't mean 'large' project necessarily. What I really meant was something more like, "a project that does something useful". 

Try to create some program that solves some problem that you have. Project Euler is great and all, but what you really want is to be able to take any real life problem you can think of, and solve it using programming.

---

