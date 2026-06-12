---
title: "Basics of programming"
date: 2010-02-08
forum: Programming Talk
---

### Post by 289531.EXE on 2010-02-08
I would  like to learn the basics of programming. Like understanding the language and how to read and create simple codes that work. Are there any programs that are free to dl that have step by step instructions on how to program and write codes?

---

### Post by azagaros on 2010-02-08
Pick up a thin book on learning to program a language, like Basic, Pascal, C/C++ or Java.  This might get you started and suggest the tool path that the books are based on.

Most of these books give basic code examples that are programs that work in the various languages.  The biggest trick to programming is learning the tools to make a program run and finding the tools your most comfortable with.

I hope this is some help.  It isn't like the old days when you had a few choices and they were dependent on the platform you start on.

---

### Post by doas777 on 2010-02-08
print is not yet dead. 
google whatever langague you want followed by "tutorial". 

and really, if you are starting out, buy a book and take a class. you'll get far more out of it.

---

### Post by 289531.EXE on 2010-02-08
Well, no money fro a class of any kind at the moment.

As far as looking up tutorials, is there anything I  can work with on ubuntu?

Any dl's that i can work with while learning how to read these 'languages'?...I have my own way of learning how to do new things.

Any recommendations? Any 'language' I could start with, just to get the feel for this?

---

### Post by 289531.EXE on 2010-02-08
or any books i should look for? something "simple"

---

### Post by doas777 on 2010-02-08
ahh. it sounds like python is a good place to start.
[http://www.google.com/search?q=learn+python&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=learn+python&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)


python will run just fine on ubuntu. far better than on windows in fact.

---

### Post by Saghaulor on 2010-02-08
> **289531.EXE said:**
> or any books i should look for? something "simple"

A Byte of Python

It's free and pretty easy to read.

[http://www.swaroopch.com/notes/Python](http://www.swaroopch.com/notes/Python)

Dive Into Python

It's also free and easy to read.

[http://diveintopython.org/](http://diveintopython.org/)

---

### Post by Dayofswords on 2010-02-08
**[SIZE="6"]Library [/SIZE]**

rocks more than you think

---

### Post by Saghaulor on 2010-02-08
My suggestion is to pick the language that would best suite your goals.

I'm learning Python because I hear it's pretty powerful and easy to learn.

Here is a list comparative list of languages.

[http://en.wikipedia.org/wiki/Comparison_of_programming_languages]("http://en.wikipedia.org/wiki/Comparison_of_programming_languages")

---

### Post by 289531.EXE on 2010-02-08
> **Dayofswords said:**
> **[SIZE=6]Library [/SIZE]**

rocks more than you think

Hahaha, good point! Not feeling too motivated to go out with the impending doom of Armageddon!:lol:

---

### Post by 289531.EXE on 2010-02-08
I want to be able to read EVERY page of this "book". I want to know what I'm looking at when I go browsing my laptop so that I don't feel like I'm on someone elses computer. I want to know whats going on in my laptop. And I want to know what all these random  codes and  commands really mean and how to create my own customize this thing.

---

### Post by t0p on 2010-02-08
The University of Washington offer a great course on learning C and the basics of computer programming, called **CSE 142 TVI**.  This course is available in an online format: you can download video files of the lectures, plus the slides that accompany each lecture.  There are also exam papers you can download, plus the keys to the exams.  **And it's all free!**  

The videos and slides are available to download [here]("http://www.cs.washington.edu/education/courses/142/99wi/TVI.html").  Other course material, such as handouts, homework and homework solutions, quizzes and solutions, exams and solutions, are available [here]("http://www.online.cs.washington.edu/cse142/").  Searching the web for "CSI 142 TVI" will turn up other material.   I've recently started following the course and I think it's great.  It doesn't just teach you C - it also teaches the fundamentals of programming.  Check it out!

---

### Post by azagaros on 2010-02-08
a simple language, the old basics aren't around anymore. Unless there is a programmer to revive some thing like "10 PRINT "Hello World"...run...."

C -- 
[PHP]
#include "stdio.h"

void main()
{
    printf("Hello World\n");
    return 0;
}
[/PHP]

C++
[PHP]
#include <iostream>

void main()
{
    std::cout<<"Hello World" << std::endl;
}
[/PHP]

Pascal/Object pascal/Delphi
[PHP]
program Helloworld
begin
   writeln('hello world');
end.
[/PHP]

I don't know what language would be my preference to learn anymore.  Java isn't much different from C/C++ programming it simplifies the more advance programming structures out there.

Learning a language would be dependent on the goals you had for programming.  Any language would start you in the same basic locations.  Like the "hello World" code listed above.

---

### Post by blur xc on 2010-02-08
I'm playing w/ python.  So far, it looks like a nice mix of basic-esque simplicity, and some pretty powerful features...

```
sudo aptitude install python
```and then enter 

```
python
```into the terminal to enter the python interactive shell.

You can write your programs in any text editor (I use vi, just cuz) but gedit is good and has a python setting for syntax highlighting.  You can run them by entering

```
python porgramname.py
```on the command line or add the

```
#!/usr/bin/python
```

to the first line of your code and making it executable by

```
chmod u+x programname.py
```in the terminal and then run it with

```
./programname.py
```If you are a glutton for punishment, you can give bash scripting a whirl.  The syntax can be challenging (at least it is to me).  The bash terminal in itself is a pretty powerful language.

BM

---

### Post by Saghaulor on 2010-02-08
> **289531.EXE said:**
> I want to be able to read EVERY page of this "book". I want to know what I'm looking at when I go browsing my laptop so that I don't feel like I'm on someone elses computer. I want to know whats going on in my laptop. And I want to know what all these random  codes and  commands really mean and how to create my own customize this thing.

Don't we all. Good luck.

I hear ubuntu runs on a lot of python, so good luck.

---

### Post by Saghaulor on 2010-02-08
> **t0p said:**
> The University of Washington offer a great course on learning C and the basics of computer programming, called **CSE 142 TVI**.  This course is available in an online format: you can download video files of the lectures, plus the slides that accompany each lecture.  There are also exam papers you can download, plus the keys to the exams.  **And it's all free!**  

The videos and slides are available to download [here]("http://www.cs.washington.edu/education/courses/142/99wi/TVI.html").  Other course material, such as handouts, homework and homework solutions, quizzes and solutions, exams and solutions, are available [here]("http://www.online.cs.washington.edu/cse142/").  Searching the web for "CSI 142 TVI" will turn up other material.   I've recently started following the course and I think it's great.  It doesn't just teach you C - it also teaches the fundamentals of programming.  Check it out!

MIT also has their Open Courseware program. I'm learning comp sci for free from MIT. Thanks MIT!

[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/index.htm]("http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/index.htm")

---

### Post by Saghaulor on 2010-02-08
> **t0p said:**
> The University of Washington offer a great course on learning C and the basics of computer programming, called **CSE 142 TVI**.  This course is available in an online format: you can download video files of the lectures, plus the slides that accompany each lecture.  There are also exam papers you can download, plus the keys to the exams.  **And it's all free!**  

The videos and slides are available to download [here]("http://www.cs.washington.edu/education/courses/142/99wi/TVI.html").  Other course material, such as handouts, homework and homework solutions, quizzes and solutions, exams and solutions, are available [here]("http://www.online.cs.washington.edu/cse142/").  Searching the web for "CSI 142 TVI" will turn up other material.   I've recently started following the course and I think it's great.  It doesn't just teach you C - it also teaches the fundamentals of programming.  Check it out!

MIT also has their Open Courseware program. I'm learning comp sci for free from MIT. Thanks MIT!

[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/index.htm]("http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/index.htm")

---

### Post by 7raTEYdCql on 2010-02-08
Getting started with programming shouldn't take time. Pick up any language, i'd suggest python, cause it is easy to grasp for beginners.

The important point which distinguishes a good programmer from an ordinary one, is his ability to design efficient algorithms. So stress on algorithm design, the symantics of the language will set in after time. In order to improve coding skills, i'd suggest you start solving some algorithm based problems loads of them are available at site like [http://www.spoj.pl/](http://www.spoj.pl/)

A good place to get started with algorithm design is "Introduction to algorithms" by Cormen [http://www.amazon.com/Introduction-Algorithms-Second-Thomas-Cormen/dp/0262032937](http://www.amazon.com/Introduction-Algorithms-Second-Thomas-Cormen/dp/0262032937)

You can also find some tutorials @ [http://code.google.com/edu/](http://code.google.com/edu/)

---

### Post by durand on 2010-02-08
I'm strongly recommending python. Try dive into python, which is a great book and if you feel that you want to programme more python, try SPE, which I've linked in my signature. It's a really, really nice python dev environment which will really help with programming.

---

### Post by cbabbage on 2010-02-08
Python is an ideal language for learning programming. The python homepage at [www.python.org](www.python.org) has good tutorials for beginners.

---

### Post by Ravenshade on 2010-02-08
> **doas777 said:**
> print is not yet dead. 
google whatever langague you want followed by "tutorial". 

and really, if you are starting out, buy a book and take a class. you'll get far more out of it.

classes are a load of rubbish. I took a degree in Java...came out not knowing how the hell to print a line of text. ( printl. something or other...)

I then picked up C++ supposedly harder, yet I'm finding it easier and a helluva lot more logical.

---

### Post by wmcbrine on 2010-02-09
> **Ravenshade said:**
> classes are a load of rubbish. I took a degree in Java...came out not knowing how the hell to print a line of text. ( printl. something or other...)

I then picked up C++ supposedly harder, yet I'm finding it easier and a helluva lot more logical.Wait till you try Python! :D

```
print 'Hello World!'
```

That's a complete Python program -- the 2.x version. Python 3.x version:

```
print('Hello World!')
```

But seriously, classes aren't rubbish -- C++ has them, too, as you know, and so does Python. They have their place, and can be extremely useful. [It's just Java that's rubbish.](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)

---

### Post by durand on 2010-02-10
> **wmcbrine said:**
> Wait till you try Python! :D

```
print 'Hello World!'
```

That's a complete Python program -- the 2.x version. Python 3.x version:

```
print('Hello World!')
```

But seriously, classes aren't rubbish -- C++ has them, too, as you know, and so does Python. They have their place, and can be extremely useful. [It's just Java that's rubbish.](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)

I think Ravenshade was going for classes as in sessions where you get taught by a teacher as opposed to OO programming..

---

### Post by doas777 on 2010-02-10
> **Ravenshade said:**
> classes are a load of rubbish. I took a degree in Java...came out not knowing how the hell to print a line of text. ( printl. something or other...)

I then picked up C++ supposedly harder, yet I'm finding it easier and a helluva lot more logical.


obviously your class was rubbish, since they didn't even cover a hello world. what school did you go to?  is it accredited?

personally I think learning entire new sets of concepts is aided by courses. learning a new langague is easy enough to do on your own, once you have one under your belt, but learning the very basics of what programming is, takes some paradigm shifts that can be aided by instructors, peers, and curricula.

lastly, c++ is not "harder", just more time consuming. java is written to reduce programmer time, so it tries to be quicker to develop in, and in many ways it succeeds.

---

### Post by peace.gangsta on 2010-02-11
> **Ravenshade said:**
> classes are a load of rubbish. I took a degree in Java...came out not knowing how the hell to print a line of text. ( printl. something or other...)

I then picked up C++ supposedly harder, yet I'm finding it easier and a helluva lot more logical.
I agree on some points with Ravenshade.Its not like Python is too easy and C/C++ is like highway through hell.What you should learn is the semantics , once you get a hang of the semantics syntax can easily be gewgled!!
And once you have the basics of programming clear in any good language(preferably the older ones like c/c++) learning others won't be a difficult thing.
I personally suggest you to go through few video lectures by some MIT or Stanford(or any other nice uni) profs and get a hold of programming.Also follow some book for background study.It ll take about 2 months of an hour of work everyday to learn the language and then years of practice to gain perfection.
I learned C++ some 2years back.I plunged into programming again since I am experiencing surplus amount of free time.Even though I don't remember the syntax,library etc clearly but I remember the concepts well and so what you need to learn is those concepts.Function ..libraries are all available you just need to apply them.
Also Python is a lot slower isn't it.Most of the professional programming is done in C++ cause it is fast and efficient.So better start with something which helps you in near future.

---

### Post by Some Penguin on 2010-02-11
> **peace.gangsta said:**
> 
I personally suggest you to go through few video lectures by some MIT or Stanford(or any other nice uni) profs and get a hold of programming.Also follow some book for background study.It ll take about 2 months of an hour of work everyday to learn the language and then years of practice to gain perfection.


I'd add that mathematics is a good area to study -- specifically, logic and proving systems.  Programming tends to devolve into problem decomposition followed by implementation -- and *most* concepts that you're likely to use often are readily implementable in *most* high-level programming languages.  What varies the most is what's built-in.

> I learned C++ some 2years back.I plunged into programming again since I am experiencing surplus amount of free time.Even though I don't remember the syntax,library etc clearly but I remember the concepts well and so what you need to learn is those concepts.Function ..libraries are all available you just need to apply them.
Also Python is a lot slower isn't it.Most of the professional programming is done in C++ cause it is fast and efficient.So better start with something which helps you in near future.

One caveat to keep in mind is that most programming work is done in teams, and if somebody isn't an expert, well, C and C++ being pretty low-level languages are fairly easy in which to simultaneously fail subtly and hard courtesy of misguided writes.  It is far harder for even mediocre programmers to do this in Java, because it's much harder for code to randomly overwrite some other structure's data (or, for that matter, the stack).

---

### Post by CptPicard on 2010-02-12
Both of you guys weren't around a few years back when the MegaThread was authored, so let's show you this... [http://ubuntuforums.org/showthread.php?t=851794](http://ubuntuforums.org/showthread.php?t=851794) so I don't need to rehash the "what languages should one start with and why" ideas from the high-level language side ;)


> **peace.gangsta said:**
> What you should learn is the semantics , once you get a hang of the semantics syntax can easily be gewgled!!

This is very, very true. Syntax is generally totally superficial, and it serves only as the first layer visual and mental parsing tool. As long as it is not actively hindering the understanding of a piece of code, syntax itself is not relevant. Underlying semantics are.

However,

> 
And once you have the basics of programming clear in any good language(preferably the older ones like c/c++) learning others won't be a difficult thing.

Let me guess that you've only programmed in a "C-derivative", right? :)

If you learn a really old one, Lisp, you have essentially covered all the elements you're likely to find in any other programming language... they either already are there, or the small core of the language allows for their easy and logical construction from the basics.

> 
I personally suggest you to go through few video lectures by some MIT or Stanford(or any other nice uni) profs and get a hold of programming.Also follow some book for background study.

In particular, one should check out the Abelson-Sussman lectures for "Structure and Interpretation of Computer Programs". Uses Scheme :p


> 
It ll take about 2 months of an hour of work everyday to learn the language and then years of practice to gain perfection.

[http://norvig.com/21-days.html](http://norvig.com/21-days.html)

> 
Also Python is a lot slower isn't it.Most of the professional programming is done in C++ cause it is fast and efficient.So better start with something which helps you in near future.

I would take the opposite position. Python "helps you in the near future" much more easily (assuming a learner here), and the things that are in C++ specifically but not in Python are fairly easily learnable afterwards. In addition, I really would like to see a beginning programmer to pick up a higher-level language mindset early on; for example functional programming seems to feel unnatural to people who come to it after an imperative programming mindset has cemented itself into their brain.

> **Some Penguin said:**
> and *most* concepts that you're likely to use often are readily implementable in *most* high-level programming languages.

+1, but do go much further -- *more* concepts are readily implementable, even rather elegantly, in high-level languages than in low-level languages. In a low-level language you'd have to essentially hack up the legendary "[half of Common Lisp]("http://en.wikipedia.org/wiki/Greenspun%27s_Tenth_Rule")" to get them...

> well, C and C++ being pretty low-level languages are fairly easy in which to simultaneously fail subtly and hard courtesy of misguided writes.

Yeah, and this is exactly also why a beginning programmer is needlessly stumped by those languages. And mind you, in my books simply avoiding those misguided writes etc does not make anyone an "expert programmer" ;)

---

### Post by Saghaulor on 2010-02-23
> **durand said:**
> I think Ravenshade was going for classes as in sessions where you get taught by a teacher as opposed to OO programming..

Semantic Error!

---

### Post by JDShu on 2010-02-23
As a beginner, I have found that the best way to learn programming is just to write programs. Whatever you're interested in, write a program for it. Armed with Google, these forums (or another programming forum) and an objective, the basics will become second nature.

---

