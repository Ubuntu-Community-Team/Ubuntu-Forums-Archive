---
title: "Learning programming"
date: 2007-04-19
forum: Programming Talk
---

### Post by Stoodle on 2007-04-19
[FONT="Comic Sans MS"]Hi guys! I'm new here (pretty obvious) and I want to further my programming abilities. I'm pretty much a noob compared to the rest of you since I've only seriously started programming this year in school. I programmed a little bit before then but not much because what I didn't have was aim. I knew I wanted to program but I didn't know what, so I didn't do it enough to become good at it. I have relatively recently found out about and installed Ubuntu and I'm really happy with reading about how everything is open source and modifiable. To increase my programming knowledge, I was wondering if anyone could tell me just how do you modify Ubuntu and Linux in general. I'd like to use it as a something to slowly help me increase my abilities and it'll help me get ahead in school when the time comes (although we're only doing Java for now). 

Also, unrelated to programming, should I upgrade to Feisty Fawn (what's the difference? I'm a noob, don't laugh too hard).[/FONT]

---

### Post by bicchi on 2007-04-20
First of all, no one should laugh at anybody for being a newbie. We all start at some point and you just took your first steps. Congrats.

Technically you do not modify Linux "the kernel" unless you want to be a kernel developer or you want to tweak the kernel for some desired feature. A very hard task that takes years of experience and goes beyond knowing java. 
if you are new to Ubuntu you should start playing with it before you can do programming. Learn how to use the shell, how the desktop is organized, become familiarized with the system, learn about Ubuntu, etc. Then you can move on into programming. I am of course speaking from my experience and you maybe be better using a difference approach. When I started using Ubuntu I already knew several programming languages so my main goal was to learn about Ubuntu and Debian. 

I think Linux is popular for using C as a language. The kernel been written in it with more than 6 millions lines of code. You will also find perl and python here and there as an alternative language.

Do not upgrade to Feisty yet. Learn how to use what you have now. If you upgrade now and your system breaks you will not have a good foundation on how to fix it. Then again, you can always post in the forums for help. I also find the upgrades very reliable but I just think you are not ready for it based on the way you describe yourself.

---

### Post by Wybiral on 2007-04-20
> how do you modify Ubuntu and Linux in general.

That's an awfully broad question... It could mean anything from changing the desktop background to recompiling the kernel and binary files... WIDE range between those.

What kind of programming do you want to do? Because no one can offer any suggestions unless we know what you want.

Server/client web development?
Hardware communication/drivers?
Handy scripts/applets?
3d games or screen savers?
Financial databases?

---

### Post by JT673 on 2007-04-20
Yep, don't mod unless you want to mod the kernel itself!  If you really want to do that, there are books and tutorials out there.

The major languages are C, Perl, Python, and, or course, Java.  Ruby is also interesting, and might be easier to learn.  IMO, Java is better than C++, so I wouldn't dig deep into C++.

Check out the sticky thread on favorite IDEs, or Integerated Developer Environment, which is a fancy editor for programming.  I like EasyEclipse, but it depends on your needs.

---

### Post by Wybiral on 2007-04-20
> **JT673 said:**
> IMO, Java is better than C++, so I wouldn't dig deep into C++.

Oh no... This could get messy...

IMO C++ is better than Java... And C is better than C++ :)

Of course... It depends what you are programming (and C suites my needs well)

---

### Post by rplantz on 2007-04-20
> **Stoodle said:**
> [FONT="Comic Sans MS"]Hi guys! I'm new here (pretty obvious) and I want to further my programming abilities. I'm pretty much a noob compared to the rest of you since I've only seriously started programming this year in school. I programmed a little bit before then but not much because what I didn't have was aim.[/FONT]

I'm responding from my perspective as a CS professor for over 20 years (now retired :).)

As you have seen from some of the other posts, your question is very broad. That makes you just like the vast majority of new students I taught. You're not expected to have aim at this point. Few students even have an aim when they graduate. And those that do often find themselves doing something else.

I don't know your age, but assuming you are facing several decades of working, things are going to change a LOT at least several times in your life. Therefore, I recommend that you try to learn as many different things as possible.

For example, play with several different editors. (Don't pay any attention to people who try to tell you that one is better than another.) After learning how to use several of them, you will learn the common concepts. Then you can easily learn how to use the one they use wherever you go to work and they require.

The same is true of programming languages. People will go on and on about the technical superiorities of language A compared to language B. I believe that the more programming languages you learn, the better you will understand the basic concepts. And chances are very good that wherever you work you will be required to use their preferred language, which may not be yours.

View this point in your life as a time to enjoy learning as many different things as you can. Don't worry about becoming an expert in any of them. Market forces and your living experiences will provide the paths over time.

---

### Post by bicchi on 2007-04-20
Nice to know CS professors visit these forums; I really enjoyed your post and found it inspirational. I am finally getting my CS degree this summer so I would like to give my 2 cents in the subject. 

I think that the most important thing I have learned in my 4 years of education is to push my mind into a creative process. Not let the bugs of a program get the best of me and just be myself regardless of the mistakes I make. As computer lovers like most of us are, we are driven by that passion to know the: "what if i do this, and that." That constant drive that sparks our imagination to produce something better than what was there before. The GNU License allows that flexibility to change the code to something appealing to us and in my opinion that has thought me a lot. 

I think that after one graduates you end up with limited programming knowledge considering how many languages and libraries are out there. You do have a high degree in solving problems and concentration. Its quite easy to switch from C to Java to something else provided that you have some basic programming knowledge. In the end its just syntax. The passion is what really makes a person stand out from the rest.

> Computers do not solve problems, they execute solutions. 

---

### Post by pmasiar on 2007-04-20
> **Stoodle said:**
> I want to further my programming abilities. I'm pretty much a noob 

Welcome aboard! What is important is not current skill level - nobody was  born with inherited ability to hack kernel:-)  What is important is drive, attitude, and passion to learn. If you have those (and looks like you do), rest is just question if time.

>  how do you modify Ubuntu and Linux in general. 

There isn't such a thing as "linux in general". Linux is just a kernel, one of the most complicated (and hardest to modify) programs which, together with [GNU](http://en.wikipedia.org/wiki/GNU) utilities. Ubuntu (the distribution) consists of like 10K packages, kernel (albeit very important) is only one of them. Luckily, most packages are simpler to understand/hack than the kernel.

> I'd like to use it as a something to slowly help me increase my abilities and it'll help me get ahead in school when the time comes (although we're only doing Java for now). 

Java was proprietary (source was released, but under uncampatible license) until recently, so Java is not as popular as other languages (C/C++/Python etc). But if you started with java, keep learning java till summer. Over summer, I would recommend you to look at other (dynamically typed) languages, from which Python is most popular. You will be surprised how much simpler (comparing with java) programming can be! :-)

Java is pretty popular in corporate environment - but some companies run on C# or *shrug* Visual Basic :-) In [free software](http://en.wikipedia.org/wiki/Free_software) world, much more preferred languages are C/C++, and Perl/Python/PHP, all depends for what application of course. So - "it depends" :-)

> Also, unrelated to programming, should I upgrade to Feisty Fawn (what's the difference? I'm a noob, don't laugh too hard).

You asked two questions. 

1) should I upgrade to Feisty Fawn? Wrong question. Answer is: it depends what you want.

2) what's the difference? Great question. (and asking right question is half the answer) Answer is also "it depends" - depends on what programs you need, and what changed. Don't trust blindly someone else's opinion - she might have different prioriries than you have.

You need to learn to know what packages are important *to you* and what are *your* learning priorities. So ie. if the version of java you have, now, including eclipse etc suits you well, and you are not interested in new features, it is perfectly good decision to *not* to upgrade now. 

Also, it might be wise to be "version laggard" and upgrade 2-3 weeks later, so someone else will have all the problems, and will know the answers when you will be upgrading... :-) It depends on *your* priorities - thats the whole point of using free software - you have the freedom to do what *you* need and *when* you need it - according to *your own* priorities.

So don't ask what to do in a situation "in general": ask what issues you need to consider in your specific situation, according to your (explicit) priorities.

Example: you ask: what car I should buy? I suggest : toyota camry. and then you say: "BTW, I need it to haul logs for my paper mill from Canada".  Well, for *that* you need a big truck.:-) See what I mean?

---

### Post by JT673 on 2007-04-20
> **Wybiral said:**
> Oh no... This could get messy...

IMO C++ is better than Java... And C is better than C++ :)

Of course... It depends what you are programming (and C suites my needs well)

I don't think the OO concepts are implemented in C++ very well (*cough*MI*cough*).  Sure you could use the libraries and stuff, but you can always use C (which, I agree, is oodles better than C++).  For maximum OO, Java and Ruby are there.

Of course, nowadays the compiler doesn't really care if you use C or C++...I couldn't care less about what language my apps are in, just as so long as I can run it...

The beauty of the language is in the developer's eyes...

---

### Post by Stoodle on 2007-04-20
I'm sorry, I tend to be very broad when I start a conversation. Anyway, since I've recently moved from Windoze to Linux (really, I'm duel-booting but I mainly use Ubuntu), I was wondering if there is a difference between EE and FF like the difference between Windows XP and 2000. That's why I was asking As far as editing Ubuntu, since I'm not going to be messing with the kernel for now I guess, what do you suggest I look at or mess with to improve? It's kind of hard to enjoy programming unless you have an aim. Me, I'd like to modify my computer so then I'll begin to learn programming faster and I'll be able to really  see how what I do effects things. As far as learning Java, I kind of have to for school but I'm interested in learning C++, too.

---

### Post by pmasiar on 2007-04-20
> **JT673 said:**
> I don't think the OO concepts are implemented in C++ very well (*cough*MI*cough*).  

LOL looks like you are drinking too much java - you cannot digest useful concepts like multiple inheritance, routinely existing in real life.

I read somewhere that first language you learn shapes  your brain - and later you have hard time to use useful concepts from other languages not existing (or complicated, ugly-looking)  in your first, and you need to extend great amount of effort to *unlearn* limits of your thinking created by restrictions of your first language.

Remember [Jonathan](http://en.wikipedia.org/wiki/Jonathan_livingstone_seagull) : the only limits of our mind are the limits imposed by ourselves.

<joke>BTW do you know why C++ hackers are paid more than java hackers? C++ has multiple inheritance </joke>

> The beauty of the language is in the developer's eyes...

exactly - and even the ugliest baby is pretty for his mom.

Different languages exist for a reason - use best tool for the job.

---

### Post by RedSquirrel on 2007-04-20
> **bicchi said:**
> I think that after one graduates you end up with limited programming knowledge considering how many languages and libraries are out there. You do have a high degree in solving problems and concentration. Its quite easy to switch from C to Java to something else provided that you have some basic programming knowledge. In the end its just syntax. 

IMO, it can be very difficult to switch to a new language, if only because one has too much confidence in their abilities based on the fact that they know some other languages. "I know language X, so for me to learn lightweight scripting language Y is going to be quite easy."... Until you find that language Y is more complicated than you thought and your previous knowledge is only helpful for about 20% of the new language and then there are all the differences. Sometimes experience hurts more than it helps. For example, there's the "unlearning" aspect that pmasiar mentioned.


> *The passion is what really makes a person stand out from the rest.*I'd say it's competence. 



> **pmasiar said:**
> 

I read somewhere that first language you learn shapes  your brain - and later you have hard time to use useful concepts from other languages not existing (or complicated, ugly-looking)  in your first, and you need to extend great amount of effort to *unlearn* limits of your thinking created by restrictions of your first language.

I agree. All languages you learn shape your brain and it's not always easy to think in new ways when it comes to learning a new programming language. Sometimes you'll see something in the new language and cringe: "Oh. I can't believe this language does *that*... and it doesn't do *this*."


Stoodle:

I would recommend doing the best you can with your Java course and then try some Python or C. Python seems to be highly recommended for beginners.

---

### Post by JT673 on 2007-04-20
Hmms...Agreed...

You were right about me drinking too much Java...While recompiling some of my older programs, I forgot I should use g++ instead of gcc...Go figure...

---

### Post by jbaldus on 2007-04-20
I'd like to echo Stoodle a little bit.  I can program well with C/C++ and I would like to contribute to the open source effort.  However, I'm also a first-year high school teacher with a two year old daughter and a kitchen that needs repainting.  This means that I can't really focus for long stretches of time.

There are a couple of things I would like some advice on.  First, I would really like to learn how to write programs for KDE.  I've played around with the projects that KDevelop generates, and I've tried to follow some online tutorials, but a lot seem to be pretty old.  Does anyone know of any resources for beginning KDE programming that rock?

I'd also like to get involved with contributing to an open source project.  I don't really know where to start or how to start.  I don't have the time to spend a year learning all of the API's and design of a super-complex application, or to spend 23 hours a day reading mailing list posts that are of-topic and unintelligible.  I'm thinking that a small utility-type program would be the best to start with--something like KCalc or KCharSelect, or something else with a 'K' at the beginning.  I've looked all over for tutorials about getting started contributing to an open source project, but haven't been able to find anything useful.  Does anyone have any suggestions about where to start and what to learn?

Thanks.  I know this is pretty vague, but I'm not too particular.

---

### Post by Stoodle on 2007-04-21
> I would recommend doing the best you can with your Java course and then try some Python or C. Python seems to be highly recommended for beginners.

I'll remember that. Thanks. So, you suggest just worrying about Java at the moment and then learn another language in a few months?

---

### Post by pmasiar on 2007-04-21
> **Stoodle said:**
> So, you suggest just worrying about Java at the moment and then learn another language in a few months?

Correct. Differences are few, and it is mostly just a syntax, but for now, syntax will be confusing and for no real gain. But when done with Java, over summer, do check Python for different language experience. Check links in sticky and in my sig. 

Second language is always easier to learn than first, but with Python as second language, you will be doing in a week or two the same stuff it took you couple months to learn in Java :-) You will be surprised how much simpler Python is!

---

### Post by RedSquirrel on 2007-04-22
> **Stoodle said:**
> I'll remember that. Thanks. So, you suggest just worrying about Java at the moment and then learn another language in a few months?

Yeah, just concentrate on one thing at a time for now. When you're done with that course and you have some free time, try Python. 

I tossed C in there because it's a good language to learn *eventually*. It's a small language (meaning not too much syntax) but it requires you to really know what you're doing. If you're curious about C, you could try reading "The C Programming Language" by Kernighan and Ritchie. I'm pretty sure most people would suggest you go with Python first, though.


> **pmasiar said:**
> 
Second language is always easier to learn than first

Have you tried learning Scheme *after* working with mostly imperative languages? :lolflag:

---

### Post by rplantz on 2007-04-22
> **pmasiar said:**
> 
I read somewhere that first language you learn shapes  your brain - and later you have hard time to use useful concepts from other languages not existing (or complicated, ugly-looking)  in your first, and you need to extend great amount of effort to *unlearn* limits of your thinking created by restrictions of your first language.


On the other hand, I have a friend who was a music professor. His first programming class (back in the early 80s) was in Pascal. He said that he just didn't get it. Then he took a class in LISP and he said it all made sense. He actually taught LISP in the CS Department for several years.

I'm just the opposite. I never quite got LISP. I can do Java, BASIC, FORTRAN, etc. The high-level language I'm best at though is C. But where I'm really in my element is in assembly language.

This is another reason for learning several languages. You may find that some are more natural for you than others.

---

### Post by pmasiar on 2007-04-22
> **rplantz said:**
> On the other hand, I have a friend who was a music professor. His first programming class (back in the early 80s) was in Pascal. He said that he just didn't get it. Then he took a class in LISP and he said it all made sense. 

Obviously, music wired his brain in LISP-compatible way, thats all. :-)

---

### Post by Mirrorball on 2007-04-23
> **pmasiar said:**
> Obviously, music wired his brain in LISP-compatible way, thats all. :-)
Now I know why I was never able to play the piano very well.

---

### Post by RedSquirrel on 2007-04-25
> **rplantz said:**
> On the other hand, I have a friend who was a music professor. His first programming class (back in the early 80s) was in Pascal. He said that he just didn't get it. Then he took a class in LISP and he said it all made sense. He actually taught LISP in the CS Department for several years.

I'm just the opposite. I never quite got LISP. I can do Java, BASIC, FORTRAN, etc. The high-level language I'm best at though is C. But where I'm really in my element is in assembly language.

This is another reason for learning several languages. You may find that some are more natural for you than others.

This is an excellent point. 

I sometimes forget that there are people who struggle with OO or imperative languages and excel at functional ones. (I had a friend who was a jazz musician and his skills with Scheme were excellent. Maybe there *is* a connection between music and LISP (and its dialects)... :) )

I think if one has worked with (and perhaps "mastered") one language without trying other languages, then their thinking patterns might be hard to break when they want to learn a second language. On the other hand, if they never "got" the first language, its effects would likely be minimal (well, that is, unless it scared them away from programming altogether).

Fortunately, the dangers of learning only one language and being tied to it are mitigated by the language choices we have today. Hey, all that hype is hard to resist!

---

