---
title: "Python IDE"
date: 2007-07-26
forum: Programming Talk
---

### Post by sparks0548 on 2007-07-26
Alright, I'll make this easy.  Growing up I never had the greatest of math skills.  I had to get tutored in Algebra and Trig.  I've been a Senior Systems Engineer for about 10 years now, extracting and preserving data for Litigations as a data forensics specialist.  I got into database specifically MS SQL Server and got pretty good at it.  Moved on to some Visual C#.NET, pretty easy drag and drop some objects, code them up and watch the application.

Now I am at a cross roads, I've come to a point where I have plenty of time to get into the real meat and potatoes, so to speak, of programming.  I figured I would start with Python.  I downloaded and have been reading through a of the Dive into Python book....good stuff, yet can't seem to get past the bells and whistles of VS C#.NET.  I looked around for IDE's and see all these great applications written in Python and have been like "How is that done".  I'm checking out Eric Python IDE now, and maybe I should read more.....for me it's tough to get past the whole VS.NET mystery.  The math aspect scares the hell out of me to.  I mean I can extract data all day long, pull from any mail server, reconstruct 0's and 1's if necessary and some of my cases have proved guilt and put people in jail.  

I think I'm missing middle ground here somehow, and have been able to learn by just reading....but looking around these posts in this forum and seeing all the Algebra posts kinda has my head spinning a little bit.

Guess this is what I get for wanting to learn some real programming.

I'm looking for a little perspective on this, I guess.  I've built and managed 240+ server data centers with TB's of storage, now the opporunity arises to do more Database work, more web stuff..and I can do it in the comfort of my own home...and spend more time with the fam.  Sounds too good to pass up.

---

### Post by Smygis on 2007-07-26
Eclipse + PyDev plugin

But unlike Microsoft® Visual© IDE, There is no drag-oh-Drop of "some objects". If you want a GUI, You will have to learn a GUI toolkit. Like PyGTK or wxWidgets. And perhaps a GUI designer like glade.

---

### Post by Nekiruhs on 2007-07-26
> **sparks0548 said:**
> Alright, I'll make this easy.  Growing up I never had the greatest of math skills.  I had to get tutored in Algebra and Trig.  I've been a Senior Systems Engineer for about 10 years now, extracting and preserving data for Litigations as a data forensics specialist.  I got into database specifically MS SQL Server and got pretty good at it.  Moved on to some Visual C#.NET, pretty easy drag and drop some objects, code them up and watch the application.

Now I am at a cross roads, I've come to a point where I have plenty of time to get into the real meat and potatoes, so to speak, of programming.  I figured I would start with Python.  I downloaded and have been reading through a of the Dive into Python book....good stuff, yet can't seem to get past the bells and whistles of VS C#.NET.  I looked around for IDE's and see all these great applications written in Python and have been like "How is that done".  I'm checking out Eric Python IDE now, and maybe I should read more.....for me it's tough to get past the whole VS.NET mystery.  The math aspect scares the hell out of me to.  I mean I can extract data all day long, pull from any mail server, reconstruct 0's and 1's if necessary and some of my cases have proved guilt and put people in jail.  

I think I'm missing middle ground here somehow, and have been able to learn by just reading....but looking around these posts in this forum and seeing all the Algebra posts kinda has my head spinning a little bit.

Guess this is what I get for wanting to learn some real programming.

I'm looking for a little perspective on this, I guess.  I've built and managed 240+ server data centers with TB's of storage, now the opporunity arises to do more Database work, more web stuff..and I can do it in the comfort of my own home...and spend more time with the fam.  Sounds too good to pass up.
Sorry bout the algebra posts.... that was part of a challenge open to the forums. But, depending on how serious you need your IDE, either go with Geany for a lightweight, powerful IDE, or Eclipse w/ PyDev plugin for the IDE that has everything but the kitchen sink. heres a chart.

                                    
Code completion:Geany  yes    Eclipse yes
Code folding:      Geany  yes     Eclipse yes
Syntax Correction: Geany no   Eclipse  yes
Startup Time*:     Geany 5 sec    Eclipse   45 sec
Syntax Highlighting:  Geany yes   Eclipse  yes
Revision Control: Geany no    Eclipse yes
Remote code editing: Geany no   Eclipse   yes

*Startup time done on my machine with 2 GB ram, 2gb Swap, 2.5Ghz 64bit processor, 32 bit Ubuntu 7.04

There you go.

---

### Post by apoth on 2007-07-26
Glade-3 + GVim. Not exactly an IDE but it does the job well.

---

### Post by pmasiar on 2007-07-26
> **sparks0548 said:**
> I've been a Senior Systems Engineer for about 10 years now, extracting and preserving data for Litigations as a data forensics specialist.  ... I figured I would start with Python. 

Very good choice. 

For you, flexibility of the processing, rapid development, and readability/ease of maintenence and enhancement is *much* more important than raw processing speed. Python will scale up for you.

> for me it's tough to get past the whole VS.NET mystery.  The math aspect scares the hell out of me to.  

> I think I'm missing middle ground here somehow, and have been able to learn by just reading....but looking around these posts in this forum and seeing all the Algebra posts kinda has my head spinning a little bit.

Don't worry about algebra. Algebra is just easy way for kids get some input transformation. 

I graduated 25 years ago in math, with lots of calculus and algebra, but I started forgetting calculus in university - and never ever used it since. Integers, money, strings - that is all you need, just relax.

> now the opporunity arises to do more Database work, more web stuff..and I can do it in the comfort of my own home.

TurboGears is excellent web app framework. It scales up, or you may just skip over most of it and use Pylons - new TG2 will be Pylons based. Django is another decent web app framework, but is less flexible (approach is: do everything at home and do it well). TG goal is to be flexible (approach is: front-to-end integration of best available modules).

You did not mentioned OS. Is it Linux?

Many best code hackers do not use IDE: they use powerful editor instead, and use it for all languages and for many years. IDEs are mostly available for mainstream languages - and perl never had any.

Python has couple IDEs. It comes with half-decent IDLE (best on Win, on Linux it looks kinda uglier), and SPE (Stani's Python Editor) is very good too. 

For most simple editing I use extremely lightweight SciTE (syntax support for all languages I know, and much more) which starts in less than second, immediately.

For big edits, and longer files, I use SPE, which generates nice code outline, and has more flexible colorization schemes than Eclipse (so colors can relay more info to you) - but heck, even IDLE has more color options than Eclipse :-)

But if you want to switch to Linux 100%, you have to learn vi/vim, no way around it, to at least passable level. vim is excellent editor, with 30 years worth of improvements, and all timesaving tricks, and you can write your own extensions also in Python.

Compared to languages with more convoluted syntax, like Java, there is less need for IDE for python: you don't need IDE to generate closing brackets and required parens in for loop, etc. After using Eclipse and  Visual Studio for some time, i realized that those IDEs allow you to write more code easier, but they are less useful for refactoring -- as a result, its easier to write more code than refactor old, and you have more code instead of less and cleaner code.

If you want to get some fun learning Python without too much algebra, try PythonChallenge website - and you will learn couple cool modules on the way. Wiki in my sig has also some training tasks which ho not require algebra, but designing flexible data structures.

---

### Post by sparks0548 on 2007-07-26
Thanks for all the great information.  I've been playing with ActivePython on my Windows system at work and have IDLE setup on my Ubuntu system now.  I'll grab the eclipse packages with the Python plugins and start messing around with those when I am done with the Dive into Python book.

Again thanks for the great input.

---

### Post by tc101 on 2007-07-26
One other thought.  It sounds like you might classic math anxiety.  This is a psychological condition that can exist even in people with high math ability.  There is some treatment for it, but I don't know anything about it.  Do a google on "math anxiety" and you might find some useful information.

---

### Post by pmasiar on 2007-07-26
One more IDE, not mentioned yet: ActiveState's Komodo. Has free version, and paid Pro version.

---

### Post by sparks0548 on 2007-07-27
Thanks alot for all the great posts.  I've downloaded Geany and going to spend some time getting to know each other.

By the way I looked up "Math Anxiety", first thinking my chain was being pulled....Long behold, look what I find:

[http://www.mathacademy.com/pr/minitext/anxiety/](http://www.mathacademy.com/pr/minitext/anxiety/)

Interesting stuff.

---

