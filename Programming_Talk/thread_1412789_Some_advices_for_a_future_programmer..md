---
title: "Some advices for a future programmer."
date: 2010-02-21
forum: Programming Talk
---

### Post by aloprot on 2010-02-21
Well, I will start by saying I never had the chance to talk to real programmers about my problem. What can I say, I signed up on the forums to exchange an opinion/some words with other programmers that I hope it will help me achive my dream.
I will explain the problem as clear and short as I can. Since I was small I was into computers, I cut classes sometimes and went to saw networks and how they work and so on. Sadly I was forced to do what I didn't wanted to. My heart and soul belong among this field. I wasted many years learning and specializing in a subject I didn't wanted to follow. Finally after many years this has changed and I can do what I really wanted to.  What I'm scared of is the fear of not succeeding my dream. I have read a lot of programming books and tutorials and I know the theorethical stuff but If you put me write an aplication or something, I just don't know how to use my knowledge. If you can please, give me some advices,  I really don't know how to study well how to do things write.
Don't know in what order to start learning languages, what to do in order to improve my skills and think as a real computer programmer. Any advice, link anything...would be great.
Thank you very much!

---

### Post by Barrucadu on 2010-02-21
How much practical experience do you have? Knowing the theoretical concepts is all well and good, but writing tools for yourself (and/or others) is probably a better way to learn.

Find something that irritates you, or you think is missing, and write something for yourself.

---

### Post by aloprot on 2010-02-21
I don't have any experience. I love very much this field and as I told in the post I read a lot, but I feel that I read for nothing because I can't do anything. I just don't know how to learn and do things right. I tried php and C but no luck in learning them. I know only simple stuff like printf and so on. And I really want to work as a programmer but I don't really know how to get myself on the working step and really do something constructive and benefical for me and others.

---

### Post by Barrucadu on 2010-02-21
Hmm, C is probably a bit much for a beginner, and PHP (while pretty good and I like it) isn't the nicest of languages. [Python](http://python.org/) is good for beginners.

---

### Post by Hellkeepa on 2010-02-21
HELLo!

I've found that the only way to actually fail at programming, is doing one of two things:
[list][*]Thinking there is nothing more to learn, or that you've perfected your methods.
[*]Not trying.[/list]
That there will be bugs, errors, or other issues cropping up as you go along is all par for the course. No programmer has ever produced something without faults, and no-one will ever do this. Dealing with errors is an excellent way of learning the finer points of programming, btw. ;-)

So, just go ahead and start writing code. Start with something simple, to ensure that you're faimiliar with the syntax of your chosen language. Then move up in the complexity, as you're getting increasingly familiar with the tools.
Do keep in mind that planning is half the job, though, so you'll want to plan stuff properly before writing any code.

Happy codin'!

---

### Post by Imaginary-r4e- on 2010-02-21
The following link is to a very well-recommended course with both video-material, documentation, readings, syllabus, assignments and so on. Although you are going to need some skills in both math and English. It focuses on how to think as a programmer and uses the programming language Python.
[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2008/CourseHome/index.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2008/CourseHome/index.htm)

Here are a few more links:

[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html) - C/C++-tutorials.
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) - C++-tutorial
[http://google.com]("http://google.com/") - Google

*Best Regards, Imaginary-r4e-.*

---

### Post by Barrucadu on 2010-02-21
> **Hellkeepa said:**
> Do keep in mind that planning is half the job, though, so you'll want to plan stuff properly before writing any code.

Ah, now there I have to disagree ;)
I get a rough idea of what I want to do and then dive straight into coding&#8212;things usually turn out ok, with possibly a big rewrite or two during development, but it's more fun this way :D

Don't focus on making something useful for yourself **and others** at the moment. Your first programs will undoubtably be pretty trivial. Write things for yourself, and when you have more experience you'll be able to write things others would benefit from. Besides, the best projects always start from someone scratching their own itch and thinking "hmm, maybe others would like to use this, too".

---

### Post by Barrucadu on 2010-02-21
Maybe have a look at [Project Euler](http://projecteuler.net/) and the Beginner Programming Challenges here on Ubuntuforums for some practice.

---

### Post by Some Penguin on 2010-02-21
Think like a mathematician.  That is, what you need to understand is how to analyze and decompose problems into components instead of looking at things as monolithic... and how to logically a system and see what it's actually doing when it isn't doing what you thought it would.  An illogical decomposition is going to lead to disorganized code which is not easily understood, maintained or extended.

You also need to familiarize yourself with what references and tools there are.  For instance, for C, you should definitely have a copy of K&R, you should be comfortable with reading 'man' pages, and you should learn a bit about the tool chain (such as ld, ldd, gcc, ranlib, ar) and a debugger such as gdb.  For Java, you should probably have the latest Nutshell book as a reference, and be comfortable navigating the various online JavaDoc references, and the like.

What I would recommend against is trying to learn to program primarily by cutting-and-pasting without actually bothering to read up on what the language constructs actually mean.  

Try something simple and platform-independent first.  Say, implement a single-player game of Blackjack 21 -- the rules for the AI can be very simple (e.g. must stand on a hard 17 or higher, must hit anytime else) and it might be amusing to test.

---

### Post by aloprot on 2010-02-21
Thank you very very much. Your replies have helped me very much.
Again if you have other suggestions I'm open to listing them.

For real, thank you very much and excuse my English. It's not perfect but hey! :) It will be:popcorn:

---

### Post by Can+~ on 2010-02-21
Many skills improve your ability to be a programmer, as there are many ramifications in the field.

[LIST]
[*]Having a rational mind and good eye for patterns can help you create or decide which algorithm must be used in a particular situation. Most of the things in computing are related to "making repetitive work easy". Therefore, finding a "model" for things always helps getting to a solution. Even algorithms are categorized on families (Greedy, Dynamic Programming, Divide and Conquer, ...)
[*]Being obsessive with good code. Whenever writing code, some people are surprisingly lazy to do it, terrible comments, lack or abscence of order, etc. Not even that, but things as simple as whitespace haven an impact on the overall readability of the code. Do the exact opposite, be obsessive about details, later on, you'll write good and valid code without even looking at the screen.
[*]English. Spanish is my first language, yet I always code and comment in english, it's awkward to read things like "[FONT="Courier New"]if contador == 0: print 'Hola Mundo!'[/FONT]", when most of the statements are already in english.
[*]Willpower. It's easy to /ragequit when you're learning on yourself, there's no one forcing you to study, or tests to pass. Try setting small goals like: "I'll make the part that sends the email today". This keeps your morale up, but never lose the big picture.[/LIST]

When in terms of what to learn, it all boils down to "what you really want to do". Learn programming first, read the python docs, it's a good sauce. Then learn some new language to expand your paradigm. And later on, if you're interested in my path, pick up an Algorithm Book, like "Introduction to Programming" by H. Cormen, or "Algorithm Design" by Eva Tardos and Jon Kleinberg.

---

### Post by aloprot on 2010-02-21
Thank you so much. Well you opened my eyes with your post. It's true, that's the same thing that happened to me. Because there was no one with a big hammer+999critical chance on attack, I wasn't paying full attention to what I'm doing. Well probably my biggest goals are to contribute to the advance of a linux distribution/help open source movement and to earn money to feed myself and not depend on relatives and so on. This is like a general view, a programmer. I tend to go on the desktop side, writing software.

---

### Post by myrtle1908 on 2010-02-22
The best advice I can give is to never be afraid to ask questions, no matter how silly you think they may be.  This forum is remarkably tolerant of the beginner.

When I first embarked on this bumpy road many moons ago, it was because I could not live with the fact that I did not understand how computers and software worked.  It bugged me to no end that people could create "living" things on chunks of metal and I did not know (nor fathom in the slightest) how they did it.  It is this burning curiosity (frustration?) that will set you in good stead and push you towards your goal.

As another poster offered previously, find something that annoys you about your use of computers, slows you down or just seems plain dumb.  Try and find your own (improved) solution to this problem.

I think the first thing I ever wrote was a Perl script that scoured Usenet servers and articles for a subject that interested me.  This was quite a task but I was more than pleased in the end.

Good luck.

---

### Post by OgreProgrammer on 2010-02-22
Find some friends with a similar skill level that wish to learn. They dont have to be friends offline though... its probably easier if they are not. 

You will inspire each other and each can learn a little and share. 

There are many communities you can join online that will provide opportunities for friends like this. Look for forums that are about making the sort of software you wish to make.

Dont be afraid to take detours and make other types of programs too. Its those side journeys that will really teach you to think fluidly.

Good luck to you.

---

### Post by aloprot on 2010-02-22
Thank you so very much. You are really wonderful people. I never would have dreamed that you would answer me. I thought my post will be deleted in an instance because of the silly things I've stated in it.
Sadly I don't have any offline or online friends who I could learn from that's why I'm asking here. And I have never found someone to help in programming, contribute to projects and etc, voluntary, only to learn not to gain money from this work. I will try to make myself a schedule and set some goals. You see maybe I'm not so good at programming but one thing I know for shure. Life is to short to waste it. Every hour counts because you could never get it back.
Again thanks very much. As I said before if you have anything else to share with a beginner please do it or you know some sites with challenges like Project Euler or someone who I can help doing work and learn from it, again NO MONEY. Experience is what matters to me right now. I can earn money later to feed my self. But I can never get back the hours that passed.
Thank you!:popcorn:

---

### Post by doas777 on 2010-02-22
if you are thinking about a program, and don't know where to start, the "Systems Analysis and Design" is an area to study extensively. the problem is that it is boring. really important stuff though. I thought it was balderdash, until i was assigned my first project as an intern. SA&D teaches you how to go from knowing nothing except that they want you to write somthing, to having fully formed requirements, models of them for documentation, and a design for a functional application that fufills them. then you just have to code it.

---

### Post by Penguin Guy on 2010-02-22
Take a look at the [Python tutorial]("http://docs.python.org/tutorial/"), try writing a piece of code that uses what you've learned in each section. Just write anything that springs into your mind. Practice makes perfect - you need experience as well as theory.

---

### Post by aloprot on 2010-02-22
Thank you! I will read it and code as much as I can. Thanks!

---

### Post by Joe Ker1086 on 2010-02-22
I am also pretty new to programming....Started with C++ but I am thinking python may be a better place to start. I have been reading alot on python and playing around with it but have a couple questions. First, is there a better way to program with python than in a terminal window??? Second, how do I save what I have been working on....

---

### Post by doas777 on 2010-02-22
> **Joe Ker1086 said:**
> I am also pretty new to programming....Started with C++ but I am thinking python may be a better place to start. I have been reading alot on python and playing around with it but have a couple questions. First, is there a better way to program with python than in a terminal window??? Second, how do I save what I have been working on....

I use geany for editing python documents. just create a file, with a name that ends in .py
and fill it with your python code. if the file is to be executed directly, then add a shebang line at the top.
```

#!/usr/bin/env python

```

---

