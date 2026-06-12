---
title: "Teaching my Brother C++ Under Ubuntu"
date: 2008-06-14
forum: Programming Talk
---

### Post by Xanderfoxx on 2008-06-14
As the title suggests, I really want to teach my brother how to program using these things:

Language: C/C++
Compiler: g++
Debugger: gdb
Editor: gedit or kate

What I want to know are two things:


[LIST=1]
[*]What are the commands I need to know, and
[*]What book aught I get to learn proper code to compile using g++?
[/LIST]
Thank you in advance.

P.S. I do not know how to code in c++, and I have no idea how to program in Linux. The farthest I go is some Java using gedit and Sun's own JDK tool set. I can do that. This shouldn't be much different, right?

---

### Post by issih on 2008-06-14
Quite different sadly...

You need to get a grasp of pointers and a few other concepts in order to program safely in c/c++, the syntax is going to be very similar, but c++ is far less forgiving than java.

Using the compiler is relatively simple, but you'd probably do better to learn how to use make (I know I keep meaning to :)).

gdb is meant to be very good, but not very user friendly, but I rarely use it so I won't comment.

gedit or kate can give you syntax highlighting and other such goodies, personally I tend to use jedit though as with a few plugins you can get class outlines and such niceties.

For a beginner, using an ide would probably be a good idea, I'm sure someone can recommend a good one for ubuntu, sadly I mostly work at the text file level as my work environment didn't have ides for the last few years, and its easiest to stick to one set up.

Generally though google for a guide to c++ programming, you yourself will have a fair bit to learn if you want to teach your brother. Is there any reason you want to go for c++ rather than sticking to java?

---

### Post by LaRoza on 2008-06-14
> **Xanderfoxx said:**
> As the title suggests, I really want to teach my brother how to program using these things:

Language: C/C++
Compiler: g++
Debugger: gdb
Editor: gedit or kate

What I want to know are two things:


[LIST=1]
[*]What are the commands I need to know, and
[*]What book aught I get to learn proper code to compile using g++?
[/LIST]
Thank you in advance.

P.S. I do not know how to code in c++, and I have no idea how to program in Linux. The farthest I go is some Java using gedit and Sun's own JDK tool set. I can do that. This shouldn't be much different, right?

Lots of problems here. First, you didn't decide a language. C or C++, which is it?

You don't need to know any commands, just how to use the compiler and debugger. The sticky has a link to a good thread on using them.

You don't need a book, just the internet. Check out my wiki for C++ or C references (yes, my wiki has a link named "C/C++" but that is because the references are for both languages)

If you don't know C++, how do you plan on teaching this? Also, the question arises, why are you trying to do this? (Especially C++...)

First, find out what your brother wants...

---

### Post by CptPicard on 2008-06-14
> **Xanderfoxx said:**
> I really want to teach my brother how to program ...  I do not know how to code in c++, and I have no idea how to program in Linux.

Okay, so first order of business is to teach yourself first and THEN teach your brother. Or maybe your brother is able to learn on his own. Or maybe you could learn together :)

---

### Post by pmasiar on 2008-06-14
poor kid will hate you for spoiling his summer by C++ :-) 

How old is your brother? Did you considered something more fun, like GameMaker?

---

### Post by Xanderfoxx on 2008-06-14
> **issih said:**
> Is there any reason you want to go for c++ rather than sticking to java?

He wants to code for multimedia-intensive applications, like games, and I think he would enjoy coding normal apps, like audio and video processors, as well as drivers and modules, eventually.

What I believe he would enjoy, is coding partially-proprietary games for Linux and FreeBSD, but who knows?

I want to learn how to crank out Elf binaries, myself, or at the very least, Win32 binaries optimized for WINE.

It may be that my brother doesn't want to learn, but at least I do. I will keep guiding him towards Linux, but I won't be too pushy.

---

### Post by days_of_ruin on 2008-06-14
Does he know any programming?If not then start on an easier
language like python.

---

### Post by LaRoza on 2008-06-14
> **Xanderfoxx said:**
> He wants to code for multimedia-intensive applications, like games, and I think he would enjoy coding normal apps, like audio and video processors, as well as drivers and modules, eventually.

I want to learn how to crank out Elf binaries, myself, or at the very least, Win32 binaries optimized for WINE.


That is a common goal, but no one starts there. If he is going to do programming, he has to get the concepts down, before worrying about abstract virtual classes and memory management.

gcc can be used on Linux and Windows. It works the same way. The sticky has a guide to using it, it is simple.

---

### Post by CptPicard on 2008-06-14
> **Xanderfoxx said:**
> He wants to code for multimedia-intensive applications, like games, and I think he would enjoy coding normal apps, like audio and video processors, as well as drivers and modules, eventually.

If he wants to do such eventually such advanced stuff I am quite certain he will be capable of expressing this desire through a *lot* of self-initiated learning :D

> 
I want to learn how to crank out Elf binaries, myself, or at the very least, Win32 binaries optimized for WINE.

"At the very least?" Why not code for Windows then? ELF binaries aren't some harder superset of Win32 ones... getting them from gcc is actually trivial (it's the development part that is harder).

> It may be that my brother doesn't want to learn, but at least I do.

I have a feeling that you're projecting your own learning onto him for some reason... just learn yourself already.. :)

---

### Post by Xanderfoxx on 2008-06-14
> **LaRoza said:**
> Lots of problems here. First, you didn't decide a language. C or C++, which is it?[quote]


C++, but don't I learn C as well, when I learn C++, since C++ is stacked on top of C?

[quote=LaRoza;5187030]You don't need to know any commands, just how to use the compiler and debugger. The sticky has a link to a good thread on using them.

If you say so. I always thought that if I used a simple editor like gedit or kate that I would need to have a terminal open, and compile and run my apps there using textual commands to debug and test it. Perhaps I was wrong?

> **LaRoza said:**
> You don't need a book, just the internet. Check out my wiki for C++ or C references (yes, my wiki has a link named "C/C++" but that is because the references are for both languages)

I'll check it out.

> **LaRoza said:**
> If you don't know C++, how do you plan on teaching this? Also, the question arises, why are you trying to do this? (Especially C++...)

In my experience, teaching is the best way to learn, because it forces one to understand the material thoroughly in order to in turn pass that knowledge on. As I learn the material, I grind it in when I attempt to explain it to my brother.

If you have a better idea as to how to produce native ELF binaries for Linux, please, be my guest and tell me how. I'm sorry you don't like C/C++.

I don't want to code heavy 3D apps in Java, as the latency is still a consideration.

Otherwise, I would stick to Java. It is easier, and more fun to play and work with.

> **LaRoza said:**
> First, find out what your brother wants...

I have. I appreciate you concern, but he is really big into gaming, so spends the majority of his time playing computer and video games.

He recently graduated from high school, and wants to go into computer science in college. I'd say if he wanted to go through with that, he would need to learn C++. Also, I asked him up front, and he agrees that it makes sense to learn the language.

And so, I offered to teach both of us the language.

Please stop making assumptions about what is going on on my side of this network. 

Thank you very much.

---

### Post by Xanderfoxx on 2008-06-14
> **days_of_ruin said:**
> Does he know any programming?If not then start on an easier
language like python.

That is a good point.

Oh, while we're at it, just how fast is Python? Could one produce a fully fledged #D computer game with it, or is the latency not quite short enough for that.

I keep hearing it is too slow for something like that, but fine for anything else. Is that so?

---

### Post by Xanderfoxx on 2008-06-14
> **CptPicard said:**
> If he wants to do such eventually such advanced stuff I am quite certain he will be capable of expressing this desire through a *lot* of self-initiated learning :D

"At the very least?" Why not code for Windows then? ELF binaries aren't some harder superset of Win32 ones... getting them from gcc is actually trivial (it's the development part that is harder).

I do not want to learn Windows programing! I just heard that some programs run faster emulated over WINE, than their native ELF counterparts for some mysterious reason.

> **CptPicard said:**
> I have a feeling that you're projecting your own learning onto him for some reason... just learn yourself already.. :)

I may sound stupid for saying this, but I asked him, and he wants to learn, but he said that he has little knowledge of computers. He says he wants to learn programming, but I fear he doesn't have enough motivation, yet. If he says he does NOT want to learn how to program, I'll desist, and learn only for myself.

I am very self-aware, and I think I would know it if I was projecting my desires onto him, thank you very much, Prof. Freud.:lolflag:

---

### Post by LaRoza on 2008-06-14
> **Xanderfoxx said:**
> 
C++, but don't I learn C as well, when I learn C++, since C++ is stacked on top of C?

No, it doesn't work that way. C++ isn't a superset of C, it is another language. There is a language that is a strict superset of C, Objective-C.

> 
If you say so. I always thought that if I used a simple editor like gedit or kate that I would need to have a terminal open, and compile and run my apps there using textual commands to debug and test it. Perhaps I was wrong?

You can do that (gedit has a terminal plugin so you don't need to open a terminal separately. By "commands" I think internal Linux commands. g++ and gdb are programs that run in a terminal. 

> 
If you have a better idea as to how to produce native ELF binaries for Linux, please, be my guest and tell me how. I'm sorry you don't like C/C++.

It isn't that I don't like C **or** C++, I don't think C++ is a good language to start with. I feel I have a valid reason for thinking that, it was my first language.

> 
I have. I appreciate you concern, but he is really big into gaming, so spends the majority of his time playing computer and video games.

Playing video games is fun. Writing them isn't. In the link in my sig there are articles on making games. Game programming is a goal for many because they think it will be fun, but it isn't (for big games). For small projects, PyGame and other libraries make game programming easier, and many engines exist for free use.

> 
He recently graduated from high school, and wants to go into computer science in college. I'd say if he wanted to go through with that, he would need to learn C++. Also, I asked him up front, and he agrees that it makes sense to learn the language.

Please stop making assumptions about what is going on on my side of this network. 

If he goes, they will teach C++ most likely along the way. Learning programming is more important (and transcends a language), might as well learn a language that doesn't get in the way, and is useful immediately. It is your brother's choice (and your choice) so it doesn't matter. However, as someone who started with C++ I can say it isn't the best thing to study as a first language.

I make assumptions when information is lacking, like everyone else.

---

### Post by Xanderfoxx on 2008-06-14
> **pmasiar said:**
> poor kid will hate you for spoiling his summer by C++ :-) 

How old is your brother? Did you considered something more fun, like GameMaker?
My brother is 18 years old. I'm not trying to kill him. :)

---

### Post by LaRoza on 2008-06-14
> **Xanderfoxx said:**
> 
I may sound stupid for saying this, but I asked him, and he wants to learn, but he said that he has little knowledge of computers. He says he wants to learn programming, but I fear he doesn't have enough motivation, yet. If he says he does NOT want to learn how to program, I'll desist, and learn only for myself.


Show him my site and wiki, the rest will be easy.

---

### Post by LaRoza on 2008-06-14
> **Xanderfoxx said:**
> My brother is 18 years old. I'm not trying to kill him. :)

I was 18 when I started, it almost killed me (well, my interest in programming)

---

### Post by LaRoza on 2008-06-14
> **Xanderfoxx said:**
> 
Oh, while we're at it, just how fast is Python? Could one produce a fully fledged #D computer game with it, or is the latency not quite short enough for that.

I keep hearing it is too slow for something like that, but fine for anything else. Is that so?

Python is pretty fast. It has bindings for many toolkits and libraries and there are game engines available for it (3d game engines).

The game engines themselves are written in C (or C++). That is where the speed matters, in game engines. Most people don't write game engines.

---

### Post by Xanderfoxx on 2008-06-14
> **LaRoza said:**
> No, it doesn't work that way. C++ isn't a superset of C, it is another language. There is a language that is a strict superset of C, Objective-C.

Cool. A technical difference I wasn't aware of. Anyways, is Python easy enough for a first language? I agree that C++ is difficult to learn, since I myself haven't managed it, yet. (I guess I'm just not the brightest bulb at Lowe's)

> **LaRoza said:**
> You can do that (gedit has a terminal plugin so you don't need to open a terminal separately. By "commands" I think internal Linux commands. g++ and gdb are programs that run in a terminal.

Sweet! I never knew.

> **LaRoza said:**
> It isn't that I don't like C **or** C++, I don't think C++ is a good language to start with. I feel I have a valid reason for thinking that, it was my first language.

Okay.

> **LaRoza said:**
> Playing video games is fun. Writing them isn't. In the link in my sig there are articles on making games. Game programming is a goal for many because they think it will be fun, but it isn't (for big games). For small projects, PyGame and other libraries make game programming easier, and many engines exist for free use.

Well, yeah, I know this, but I cannot stop him if he wants to learn how to code games. All I can hope to do is support him until he see for himself that there are many, many other people who got sucked into that, and I can hope I can guide him into something more practical, something more likely to make a paycheck, like working for Novell, Red Hat, or Sun, coding things like drivers, apps, and scripts.


> **LaRoza said:**
> If he goes, they will teach C++ most likely along the way. Learning programming is more important (and transcends a language), might as well learn a language that doesn't get in the way, and is useful immediately. It is your brother's choice (and your choice) so it doesn't matter. However, as someone who started with C++ I can say it isn't the best thing to study as a first language.

That is true.

> **LaRoza said:**
> I make assumptions when information is lacking, like everyone else.

As do we all. No problem, man.

---

### Post by issih on 2008-06-14
I agree with starting somewhere other than c/c++ if posible. Any modern language java/python/etc will give you the ability to achieve much more, far more rapidly. Yes the final code will not be that epically fast, but you really are not going to be producing code that will stress a modern pc for quite some time, honestly. When you start learning to code, you simply can't jump in and code a full fledged game. Take baby steps., when I learnt java the initial challenge was to make a version of freecell.

The first version was all text input and output, and was highly procedural.

That code was slowly improved until all the rules were enforced carefully.

I then began to learn to think in an oo style, and entirely rewrote the whole system, so that everything was written in a highly object oriented style, this process also involved creating rules for the automatic move systems.

Finally I built a gui front end onto this code (one that is virtually indistinguishable from windows one).

This whole process took at least a month if not longer. But by the end I had a set of objects and a gui system that could be rapidly re-purposed into other card games by simply changing the rules to do with transferring cards between piles.

You have to start small, and you will have to relearn a lot of what you think you know. with a low level language like c, you will not get the satisfaction of seeing a nice little gui app for a very long time.

---

### Post by CptPicard on 2008-06-14
>  As I learn the material, I grind it in when I attempt to explain it to my brother.

It's far better to be learning on your own than from a half-assed teacher who doesn't know what he's talking about. Don't abuse his learning experience for yours... talk to a mirror if you enjoy teaching.

Interestingly, when I was a student, I used to "give a lecture" to nobody on some topic just to go through it inside my head. Made me look like a madman talking to myself about information theory in sensor networks...

> 
I don't want to code heavy 3D apps in Java, as the latency is still a consideration.


Most of it is in the OpenGL library's side anyway. The only thing I might worry about is GC stuttering, but ... to begin with, you need to be able to program in the first place before worrying about coding heavy 3D apps. :)

> 
He recently graduated from high school, and wants to go into computer science in college. ... I may sound stupid for saying this, but I asked him, and he wants to learn, but he said that he has little knowledge of computers. He says he wants to learn programming, but I fear he doesn't have enough motivation, yet.

Look, he's a big boy. What is your interest here in maintaining *his* motivation on something that he is even considering going to study? He should be hacking on his own by now.

Something doesn't add up here...


> **Xanderfoxx said:**
> I do not want to learn Windows programing! I just heard that some programs run faster emulated over WINE, than their native ELF counterparts for some mysterious reason.

This and the Python question is what I like to call speed-kiddyism. First, emulation is always slower than native stuff, and second, even if in some freak case this was true, you'd never want to do anything weird like that anyway in real life for such a speed gain which will be minimal anyway.

You really have to focus on the basics of programming instead of worrying about stuff that will not be relevant to you until far into the future.

---

### Post by Xanderfoxx on 2008-06-14
> **CptPicard said:**
> Or maybe you could learn together :)

This is the idea. (Sheesh.)

Sorry I like Linux so much, guys, I just want to see my 18-year-old brother succeed.

He just moved in, and I haven't seen him in, like, forever.

I just wanted to do something fun AND practical/useful together. I guess I'll go with Python.

---

### Post by CptPicard on 2008-06-14
> **Xanderfoxx said:**
> This is the idea. (Sheesh.)


Okay, good. Go for it. You just sound strangely patronizing :) I mean... if you want to argue for some point with him -- such as the Linux one -- you should just do that...

---

### Post by LaRoza on 2008-06-14
> **Xanderfoxx said:**
> Cool. A technical difference I wasn't aware of. Anyways, is Python easy enough for a first language? I agree that C++ is difficult to learn, since I myself haven't managed it, yet. (I guess I'm just not the brightest bulb at Lowe's)

As do we all. No problem, man.

Don't ask me, ask the internet. Check out my home page and go to the language selector and ask it instead :-)

Or woman...

---

### Post by lavinog on 2008-06-14
If you have little programming experience I think gambas would be a nice place to start.  It is based on the visual basic language. It also has a very user friendly IDE.
Alot of the people that try learn computer programing have a hard time with basic logic. Breaking down thought processes into algorithms.
Once you get past that barrier, most of the languages are the same with exception to syntax.

Another issue is people try to design their programs as they write them. Doing this may seem easier, but you will find that you will waste many hours rewriting parts of code for work arounds.

Worrying about which language to use and picking a language because one is faster than the other is pointless if you are not familiar with efficient coding techniques.
If you or your brother want to get into serious programming you better be good at math.

---

### Post by CptPicard on 2008-06-14
> **lavinog said:**
> If you have little programming experience I think gambas would be a nice place to start. It is based on the visual basic language.

No, it's not a nice place to start, because of the reason given in the last sentence. One might just as well start with a modern and usable high level language such as Python... that way there is no need to "migrate away" as soon as the training wheels start feeling restrictive.

> Alot of the people that try learn computer programing have a hard time with basic logic. Breaking down thought processes into algorithms.

And using some GUI-centric programming environment is not going to help with that at all. It's a crutch that causes bad programming habits to develop.

> 
Another issue is people try to design their programs as they write them. Doing this may seem easier, but you will find that you will waste many hours rewriting parts of code for work arounds.

Actually, with a proper dynamic high level language, an agile development process is quite workable. The only way to learn programming is to actually write code, and you don't do that if you minimize your programming by drawing UML diagrams. :)

To borrow a well known adage from physicists, "programming is to designing as sex is to masturbation".

Of course coding requires some forethought, but personally I am quite fond of replacing parts of my program with new kinds of parts as I go, slowly adapting the solution into something closer and closer to perfection. Lisp for example allows this sort of a bottom-up, replace-parts sort of development model.

---

### Post by pmasiar on 2008-06-14
> **Xanderfoxx said:**
> Oh, while we're at it, just how fast is Python? Could one produce a fully fledged #D computer game with it, or is the latency not quite short enough for that.

I keep hearing it is too slow for something like that, but fine for anything else. Is that so?

Python is fast enough - most of time is spend in game engine calls, which are in C. And if you need it, you can compile to binaries - most people does not care because Python is fast enough without it. 

And especially for learner, you should be more concerned of speed of development (from idea to implementation) than speed of your 3D physics effects. 

And if you yourself are not expert programmer, both of you will be better off following some decent Python book (many are free) than trying to make sense from a hard language like C++. 

Python is excellent for learners because it does not force OOP on beginner, and takes care of memory management and types. Yes, you pay 20% of CPU cycles for that, but that's irrelevant in most apps, it you wait for database or web server response.

---

### Post by slavik on 2008-06-15
Does he know any programming?If not then start on an easier
language like Perl.

NOTE: shamelessly ripped from days of ruin and run through s/python/Perl/sgi

---

### Post by LaRoza on 2008-06-15
> **slavik said:**
> Does he know any programming?If not then start on an easier
language like Perl.

NOTE: shamelessly ripped from days of ruin and run through s/python/Perl/sgi

"like Perl":

Perl/Python/Ruby

We need an easy way to write that...

---

### Post by descendency on 2008-06-15
If you would rather learn C++, a good set of tutorials can be found: [http://msdn.microsoft.com/en-us/beginner/cc305129.aspx](http://msdn.microsoft.com/en-us/beginner/cc305129.aspx)

Ignore the MS propoganda. You don't need visual studio express or any other like IDE. You need a C++ compiler (GCC/G++) and a text file creator (to create .cpp/.h files). 

I don't remember it talking about any "windows only" header files. (ie windows.h). All of the code should compile on any c++ compiler.

edit: C++ is a more difficult language to learn initially because you must learn both the programming aspects (loops, branching, etc) and a less newbie friendly structure to the language. For example:

[PHP]#include <iostream>
using namespace std;

int main(int argsc, char* argsv[])
{
  cout << "Hello, World!" << endl;
  return 0;
}[/PHP]

outputs "Hello, World!" to the console box. (terminal, dos box, etc) It can be learned very quickly however after you master the concepts with either languages to learn like QBasic or Python (from what I hear)

---

### Post by nvteighen on 2008-06-15
First, it's not wise to talk about things yourself don't master. You may give your brother a big delusion and probably kill his interests by the way. But, learning both together instead can be really a great idea... I bet you'll have a lot of fun that way and have some good brother-time too (which is even more important).
 
Second, as someone (CptPicard?) said in these forums some time ago (sadly, I don't remember where...), programming is a craft and crafts are learned by doing. Whatever programming language you two start to learn, never stop coding... Always set yourself small and achievable projects: each "stupid" program you finish and make work is more important than any "serious" project you haven't finished.

Last, I'd recommend you not go for C++ without programming experience... neither C: you'll be struggling with programming basics as if-loops simultaneously to C or C++ particular difficulties.

Happy learning!

---

### Post by Wybiral on 2008-06-15
> **descendency said:**
> It can be learned very quickly however after you master the concepts with either languages to learn like QBasic or Python (from what I hear)

Did you just group QBasic and Python into the same category?

---

### Post by descendency on 2008-06-15
> **Wybiral said:**
> Did you just group QBasic and Python into the same category?

In terms of being super easy to learn, yes.

---

### Post by slavik on 2008-06-15
> **LaRoza said:**
> "like Perl":

Perl/Python/Ruby

We need an easy way to write that...

the code is in the post :P

---

### Post by balagosa on 2008-06-17
the first programming language i learned was QBasic. then Visual Basic, C, Java, C#, PHP.

question guys, where to look for C++ reference manuals, that are free to read. (sorry if this would be an insult to OP, for hijacking his thread)

---

### Post by pmasiar on 2008-06-17
where docs are? did you tried sticky FAQ?

---

### Post by balagosa on 2008-06-18
> **pmasiar said:**
> where docs are? did you tried sticky FAQ?

yeah tried it. but i preferred the downloadable ones because i am not onlie 24/7.

---

### Post by LaRoza on 2008-06-18
> **balagosa said:**
> yeah tried it. but i preferred the downloadable ones because i am not onlie 24/7.

Save the web pages, like I did when I was learning and didn't have the internet.

---

