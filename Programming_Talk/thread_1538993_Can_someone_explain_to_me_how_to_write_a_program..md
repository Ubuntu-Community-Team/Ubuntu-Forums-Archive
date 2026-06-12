---
title: "Can someone explain to me how to write a program."
date: 2010-07-26
forum: Programming Talk
---

### Post by ayyork on 2010-07-26
Can some one explain to me what programing is. It may seem like a dumb question, but that is some thing that i have always wanted to know how to do. So if you can help me learn how to do build a program or show me how. It would be nice thanks you.

---

### Post by cariboo on 2010-07-26
You need to learn a programming language, before you can write programs. I would suggest python, as it uses almost plain english syntax.

For a tutorial, have a look [http://docs.python.org/tutorial/]("http://docs.python.org/tutorial/")

---

### Post by Gryph0n on 2010-07-26
If you want a quick look at what's involved, there are plenty of [youtube videos](http://www.youtube.com/results?search_query=python+programming&aq=f) that would give you a bit of insight.

I wouldn't recommend them for actually learning though.

---

### Post by ayyork on 2010-07-27
thanks for the tips

---

### Post by lisati on 2010-07-27
Have a look here: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by VH-BIL on 2010-07-27
You can start with scripting if you already know some terminal commands. You can do some simple GUI scripts using zenity.

Here is an example of a sleep timer script I did for someone (It needs to be run with sudo)
```
#!/bin/bash
echo "Sleep Timer."
TimeMinutes=$(zenity --entry --title "Sleep Timer" --text "How long before shutdown? (minutes)" --entry-text "30");
TimeSeconds=$(($TimeMinutes * 60))
if [ $TimeMinutes = 1 ]
  then
    echo "System power off in 1 minute. ($TimeSeconds seconds)"
  else
    echo "System power off in $TimeMinutes minutes. ($TimeSeconds seconds)"
fi
sleep $TimeSeconds
echo "powering off now..."
poweroff
```

Once you learn how a program 1 language it is quite easy to learn  program others.

---

### Post by NightwishFan on 2010-07-27
Here are some links. I also recommend Python, it is very easy to see real results with it, even if you are a bit of an idiot like me. :)

[https://help.ubuntu.com/8.04/programming/C/learning-howto-program.html](https://help.ubuntu.com/8.04/programming/C/learning-howto-program.html)
[https://help.ubuntu.com/community/Programming/Python](https://help.ubuntu.com/community/Programming/Python)

Software written in python:

[_Exaile Music Player_]("http://en.wikipedia.org/wiki/Exaile")
[_Anaconda (Fedora Installer)_]("http://en.wikipedia.org/wiki/Anaconda_%28installer%29")
[_Emesene Messenger_]("http://en.wikipedia.org/wiki/Emesene")
[_Pitivi Video Editor_]("http://en.wikipedia.org/wiki/PiTiVi")
[_Ubuntu Software Center_]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center")

---

### Post by slooksterpsv on 2010-07-27
> **NightwishFan said:**
> Here are some links. I also recommend Python, it is very easy to see real results with it, even if you are a bit of an idiot like me. :)

[https://help.ubuntu.com/8.04/programming/C/learning-howto-program.html](https://help.ubuntu.com/8.04/programming/C/learning-howto-program.html)
[https://help.ubuntu.com/community/Programming/Python](https://help.ubuntu.com/community/Programming/Python)

Software written in python:

[_Exaile Music Player_]("http://en.wikipedia.org/wiki/Exaile")
[_Anaconda (Fedora Installer)_]("http://en.wikipedia.org/wiki/Anaconda_%28installer%29")
[_Emesene Messenger_]("http://en.wikipedia.org/wiki/Emesene")
[_Pitivi Video Editor_]("http://en.wikipedia.org/wiki/PiTiVi")
[_Ubuntu Software Center_]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center")

You just showed me how powerful Python can be, I just switched to Exaile as Rhythmbox seemed "bulky" and Pitivi is awesome, just so much python no wonder I love it.

Python is easy

---

### Post by ayyork on 2010-07-27
how many different languages are there?

---

### Post by ayyork on 2010-07-27
is there the names of the converters that are really good  on the 10.04

---

### Post by Res2216firestar on 2010-07-27
> **ayyork said:**
> how many different languages are there?

Tons. The ones that come to mind for me are Python, Perl, Ruby, PHP, C, and C++.

---

### Post by VH-BIL on 2010-07-27
There are many languages and many different spins of those languages.

There are languages that are not compiled and interpreted at run time.

There are languages that are compile to an "Intermediate Language" (IL) which enables many languages to use the same libraries, components and become cross platform.

There are compiled languages that are for use with a specific OS and CPU type.

---

### Post by slooksterpsv on 2010-07-27
C, C++, C#, Python, Ruby, Perl, HTML, Javascript, Java, Haskell, ADA, Gambas, PHP, XML, ASP, tons and tons thats just a partial list not even 1/4 of them that are out there.

[php]
//main.cpp
#include <iostream.h>

using namespace std;

int main()
{
 cout << "Hello World!" << endl;
 return 0;
}
[/php]

That's hello world written in C++ and you'd compile like so:
g++ main.cpp
then run:
./a.out

---

### Post by ayyork on 2010-07-28
thanks i am between java and python

---

### Post by Chris1274 on 2010-07-28
> **slooksterpsv said:**
> 
[php]
//main.cpp
#include <iostream.h>

using namespace std;

int main()
{
 cout << "Hello World!" << endl;
 return 0;
}
[/php]That's hello world written in C++ and you'd compile like so:
g++ main.cpp
then run:
./a.out

Now compare that with Python:
```
#!/usr/bin/python3.1
print('Hello World!')
```
:p

---

### Post by Goolie on 2010-07-28
Look for a course at a local college, unless you're good at learning on your own, check out your local library, they'd definetely have something on programming.

Whatever your first language porting the knowlege will be simple onto another language.

---

### Post by t0p on 2010-07-28
If you want to learn how to program, I seriously advise you to check out the [MIT Introduction to Computer Science and Programming]("http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/").  This MIT OpenCourseWare gives you everything you'll need to learn python from scratch - lecture videos, lecture notes, plus assignments and exams (that you mark yourself - you don't have to keep to a structured timetable or anything like that).  And by the time you finish, you'll know how to program in python *plus* you'll be able to learn other languages pretty quickly.  And it's all completely free!!

This is genuine MIT undergraduate-level material.  Check it out, it is brilliant!

---

### Post by jschmeau on 2010-07-28
There are many programming languages.
Here is a great place to get stared with python.
[http://docs.python.org/tutorial/index.html]("http://docs.python.org/tutorial/index.html")

In my experience with programming, patience is everything.  Do not expect to code Exaile2 right off.

---

### Post by lisati on 2010-07-28
Moved to "Programming talk"

There are a lot of different programming languages. Some of the popular ones have already been mentioned.

---

### Post by interval1066 on 2010-07-28
> **Chris1274 said:**
> Now compare that with Python:
```
#!/usr/bin/python3.1
print('Hello World!')
```
:p
Python's great... until you need to write a driver or kernel module.

---

### Post by Chris1274 on 2010-07-28
> **interval1066 said:**
> Python's great... until you need to write a driver or kernel module.

Well, I'll leave that sort of thing to you Neo's out there who see the world in binary code. :smile:

---

### Post by trent.josephsen on 2010-07-28
> **interval1066 said:**
> Python's great... until you need to write a driver or kernel module.

Maybe it's just me, but in all my years of programming experience I have never written a driver nor a kernel module.

Of course Python's not good for that.  Why would you expect it to be?  Are you implying that there is some other language, equally easy to learn and high-level, which is also suitable for low-level systems programming?  Please, enlighten me.

All languages have strengths and weaknesses.  Python, in my opinion, is great for learning to program in and has a lot of powerful tools for getting real work done; it's the first language I recommend to new coders.

---

### Post by splicerr on 2010-07-28
> **interval1066 said:**
> Python's great... until you need to write a driver or kernel module.

Yes and a hammer is also a great tool... until you need to cut some wood or trees :rolleyes:

---

### Post by slooksterpsv on 2010-07-28
> **splicerr said:**
> Yes and a hammer is also a great tool... until you need to cut some wood or trees :rolleyes:

If the saw is dull you could use the hammer to pound the saw through hehe, find different ways to use the tools you have to make what you want to do easier, just like Linux =D.

---

### Post by ayyork on 2010-07-29
The college is not a option i am abit under age for collage. But i will check my local library .
 So you all would suggest that i go with python . I have heard that there was a larger job market for java , and later in life i would like to try to write driver and kernel module. Which language should i learn after python so it will let me do that.

---

### Post by Some Penguin on 2010-07-29
If you're going to rely on other people answering basic questions for you and not do your own research and decision-making, I don't think it really matters what languages you learn.

---

### Post by phrostbyte on 2010-07-29
> **trent.josephsen said:**
> Maybe it's just me, but in all my years of programming experience I have never written a driver nor a kernel module.

Of course Python's not good for that.  Why would you expect it to be?  Are you implying that there is some other language, equally easy to learn and high-level, which is also suitable for low-level systems programming?  Please, enlighten me.

All languages have strengths and weaknesses.  Python, in my opinion, is great for learning to program in and has a lot of powerful tools for getting real work done; it's the first language I recommend to new coders.

Technically you can write drivers in Python, it has a libusb binding. :)

---

### Post by ayyork on 2010-07-29
thanks for your help

---

### Post by interval1066 on 2010-07-30
> **trent.josephsen said:**
> Maybe it's just me, but in all my years of programming experience I have never written a driver nor a kernel module.

Yeah, I think its just you. Its rare for a linux shop to not need custom drivers.

> **trent.josephsen said:**
> Of course Python's not good for that.  Why would you expect it to be?  Are you implying that there is some other language, equally easy to learn and high-level, which is also suitable for low-level systems programming?  Please, enlighten me.

Calm down. I'm not implying anything. You're rather defensive. You know you can always learn systems programming if you feel your personal skill set is lacking...

> **trent.josephsen said:**
> All languages have strengths and weaknesses.  Python, in my opinion, is great for learning to program in and has a lot of powerful tools for getting real work done; it's the first language I recommend to new coders.

I agree. But I wouldn't write a driver with it. Regardless of the other opinion later given. I don't believe python is sufficient for systems programming. Show me a python kernel however and I'll probably change my tune.

---

### Post by p.s. on 2010-07-30
> **ayyork said:**
> thanks for your help

I would agree with the folks here that Python is a great starter. Also, making yourself us the command line is helpful for getting into the sort of "programmery" mode of thinking. I wouldn't worry about job markets too much, either, you can always learn another language and become $$$$$$rich$$$$$$$!

One thing that's fine is going over some of the basic game-design stuff you can do with sprites in Python. Plenty of resources available online, and a particularly fun project for starting off.

---

### Post by wangkeit on 2010-07-30
> **ayyork said:**
> Can some one explain to me what programing is. It may seem like a dumb question, but that is some thing that i have always wanted to know how to do. So if you can help me learn how to do build a program or show me how. It would be nice thanks you.
 I recommend to learn C language programming in linux,
for exmaple :
#include <stdio.h>
main(){
         printf("Helo-Helo-World\n");
}

---

### Post by ayyork on 2010-07-31
Ok so start with python and work my way into the other languages. I am 14 by the way about to be 15.

---

### Post by jon zendatta on 2010-07-31
aah the world is your oyster. i first started learning C @ the prime age of 37:KS

---

### Post by the_scientist on 2010-07-31
> **ayyork said:**
> how many different languages are there?


There are hundreds of programming languages ..... C , Java , Python ,perl the list goes on and on ...... I think Python and perl are good languages to start with ....

---

### Post by lisati on 2010-07-31
> **jon zendatta said:**
> aah the world is your oyster. 
+1 :D

If memory serves me correctly my first effort was in Fortran, well over 30 years ago. I haven't had much use for Fortran since, but have dabbled with a handful of other languages over the years, including COBOL (yuck, too verbose!), BASIC, a couple of different flavours of assembler, PL/1, Pascal, and C.

My $0.02: focus on one language at a time, and learn to do it well. Having snippets of the "wrong" language pop into your head while you're tackling a project can be annoying and distracting.

---

### Post by slooksterpsv on 2010-07-31
> **lisati said:**
> +1 :D

If memory serves me correctly my first effort was in Fortran, well over 30 years ago. I haven't had much use for Fortran since, but have dabbled with a handful of other languages over the years, including COBOL (yuck, too verbose!), BASIC, a couple of different flavours of assembler, PL/1, Pascal, and C.

My $0.02: focus on one language at a time, and learn to do it well. **Having snippets of the "wrong" language pop into your head while you're tackling a project can be annoying and distracting.**

Amen, I can remember how I did something in VB and tried to type it in Python, yeah didn't work of course it was something simple that took me an hour to figure out. I think it was String Manipulation or something like that.

---

### Post by ayyork on 2010-08-01
I am  very fast learner. That is what i believe is going to end up happening to me. I have looked at videos of python i like it. It seems simple and easy to learn , but i am still scared that i will mess something up . How does it transform into a picture after it is all over and done? Here is another thing that is still confusing me to. How can you write your own language?

---

### Post by howlingmadhowie on 2010-08-02
> **ayyork said:**
> I am  very fast learner. That is what i believe is going to end up happening to me. I have looked at videos of python i like it. It seems simple and easy to learn , but i am still scared that i will mess something up . How does it transform into a picture after it is all over and done? Here is another thing that is still confusing me to. How can you write your own language?

don't worry about writing your own language for now.

i'd say that programming nowadays consists of 2 things:
1/ what you want to do and
2/ expressing that in a particular language.

both of these things get better with practice.

in step 1 you formulate your thoughts into actions in such a way that someone could perform the actions without thinking. and in step 2 you translate these actions idiomatically and syntactically into the target language.

as an example you can consider a shuffled deck of cards which you want to sort. you can imagine yourself sorting the cards, but how would you explain to someone else what you are actually doing?

---

### Post by ayyork on 2010-08-02
thanks for your help if any one know another good thing post it

---

### Post by wkhasintha on 2010-08-03
> **ayyork said:**
> Can some one explain to me what programing is. It may seem like a dumb question, but that is some thing that i have always wanted to know how to do. So if you can help me learn how to do build a program or show me how. It would be nice thanks you.

programing is the scheme of instructing the computers(Machines) to do things.

---

### Post by ayyork on 2010-08-03
ok How would you go about writing those instructions if it was you?

---

### Post by Bachstelze on 2010-08-03
> **ayyork said:**
> ok How would you go about writing those instructions if it was you?

In a programming language. ;)

---

### Post by Some Penguin on 2010-08-03
Reading the sticky threads before asking ridiculously vague questions would be an improvement.

---

### Post by ayyork on 2010-08-03
> **Some Penguin said:**
> Reading the sticky threads before asking ridiculously vague questions would be an improvement.


I i have read most of them i ask how he would go about it.

---

### Post by wkhasintha on 2010-08-04
> **ayyork said:**
> ok How would you go about writing those instructions if it was you?

Using High level Programming language (Java,C++,C#) or a scripting language (Python,Ruby etc.)

---

### Post by interval1066 on 2010-08-04
Asking "How do I write programs?" is like asking "How do I make a cake?" except you probably have some vague notion that it involves flour, eggs, some kind of whisking motion with probably a spoon or a spatula, and an oven set on "really hot". Writing programs is as little more complicated. If you're coming to programming with NO prior experience then you need to familiarize your self a little more about how computers work so you can have your expectations regarding what a modern computer is capable of. BASIC is a nice introduction to programming, or just tinkering around with a shell (this question is on a linux derivative forum, so I assume you've access to a linux machine), just "man bash", look for setting a shell variable, and you'll get started.

---

### Post by StunnerAlpha on 2010-08-06
> **ayyork said:**
> I am  very fast learner. That is what i believe is going to end up happening to me. I have looked at videos of python i like it. It seems simple and easy to learn , but i am still scared that i will mess something up . How does it transform into a picture after it is all over and done? Here is another thing that is still confusing me to. How can you write your own language?

Ey man, not meaning to nit-pick or anything, but while you learn how to program it would be VERY WISE to also work on your writing skills as it is extremely important these days since most programming projects are collaborative(are done with other programmers). This means you need to know how to make comments in your code effectively and efficiently, and the ability to better communicate with others will only help you in this world.

And yes definitely go with python. I was first exposed to programming in a fast-paced college course learning C and as a result I didn't really grasp programming/get really interested in it until I learned python which reinforced things that my professors went over for C and C++(things like objects and modular programming and whatnot).

---

### Post by nvteighen on 2010-08-06
A program is a piece of text written in a programming language (a formal-logical artificial language) in order to describe **something** that usually a computer can later understand for you... but not only a computer: for example, another person that also knows the language will be able to "run" the program in his head... I put emphasis on the fact that program describes things or realities rather than only processes because this might help you in the future to understand ways to program that not necessarily need to describe "processes" (just for you to know: the Prolog programming language and also other database-related ones work by telling the computer how the data is related instead of what to do with the data).

There exists a distinction between "high abstraction level languages" ("high-level", "HLL" for short) and "low abstraction level languages" ("low-level", "LLL" for short). This has nothing to do with "better" and "worse", it's about what are languages designed for. A language is said to be "lower-level" if it makes you deal with computer internal stuff such as the CPU registers, memory management and requires you to have knowledge of the platform you're working on. These languages tend to be really efficient but in my (and others') opinion, really hard to master if you don't know how to program. High-level languages on the other hand make you deal with stuff that's more conceptual or abstracted (from the computer's point)... for example, in Python you have lists and that's a concept you know from real life and a very useful one. 

As learning how to program is basically learning how to rationalize and formalize things, many people recommend high-level languages as starter languages because it makes the beginner focus on that specific skill without making him to worry about stuff that ok, he has to learn, but aren't part of the logical skills needed for **any** kind of programming. I tell you this so you see that's there a reason why people (like myself) have recommended Python to you.

Others believe that low-level languages are better for teaching how to program because they show you how stuff works under the hood. While that's true, it's also true that when you program you usually try to forget how things work in order to focus on what your own specific problem is.

No matter what you do: please, learn at least Python and C (I suggest you that order). Afterwards, learning languages will be really easy (except for some cases) because a lot of languages are more or less based on C.

Now to the technical issue: you always need to "translate" that code into binary. Roughly said, this can be made in two ways: by "translating" it on the fly or by "translating" the whole thing first and then run it. Curiously, Python uses a technique that lies in the middle, but for simplicity's sake let's say it is in the first group, while C or C++ are in the second. So, what you **essentially** need for programming is just a text editor and the program that is able to read the programming language of your choice.

But, of course, programmers use tools that help them to work faster and are specially designed for them: programming-targeted text editors like vim, emacs, Geany... or full-fledged IDEs (Integrated Development Environment) that can automate stuff a lot. It's very legimate to use them, but always having clear in mind that those are support tools and not the essence. A Java IDE like Eclipse isn't "Java"... I could use nano or even MS Notepad to write my Java application and then call javac (the Java compiler) manually, although of course, it'd be a nightmere.

---

### Post by lordhaworth on 2010-08-06
Someone asked how many programming languages there are:
[http://en.wikipedia.org/wiki/List_of_programming_languages](http://en.wikipedia.org/wiki/List_of_programming_languages)

gives a reasonable indication of the scale. 
There is a similar page of hello world programs, though a lot of the entries are dodgy

[http://en.wikibooks.org/wiki/List_of_hello_world_programs](http://en.wikibooks.org/wiki/List_of_hello_world_programs)

---

### Post by lordhaworth on 2010-08-06
Also, I wouldnt let it get to you if you don't really know *how* everything works. It wont stop you writing programs and experimenting - I doubt there are many programmers who truly understand the inner workings of the computer, thats why programming languages are useful, because you are not subjected to the extreme difficulties of machine code... or worse, electronics!

Just play about, reading into more depth makes for good background and is genuinely interesting but not a scratch on diving into hello world.

---

### Post by realzippy on 2010-08-06
The way I started:

[Learn Python The Hard Way]("http://learnpythonthehardway.org/home")

by Zed A. Shaw

---

### Post by achron on 2010-08-06
Programming Language is something I think of as a 'tool du jour'...

Today, while writing WebServices here at work, I use C#/.net in MS Visual Studio.  I also write Transactions called by those services in another language which talks to our enterprise database. At times, when writing hard-core analytical modules, I drop to C/C++.  Different languages are better at different things, generally speaking.  

I once looked at Python, but I guess I don't have a python-esque brain (unless you're counting Monty Python in that definition).

And at home, and as a sideline, I work in Ruby on Rails to build web applications. Why work in RoR when I have all these other tools available? Ruby (and the rails framework) just sings (to me at least), which makes it a pleasure to work in.

The most important part of programming is learning to think appropriately. The basic problem decomposition and design skills you develop working in any language should translate across to other language syntaxes and libraries quite readily.

So try a couple, and find the one that fits for you.

---

### Post by ayyork on 2010-08-07
Thank you all so very much. it is helping me a lot. programming is some thing that seems like every one should know a thing or two about.

---

### Post by slooksterpsv on 2010-08-09
> **ayyork said:**
> Thank you all so very much. it is helping me a lot. programming is some thing that seems like every one should know a thing or two about.

Well, I can say I know people who are very proficient in Excel data; they program if statements (and next them) so they get values that are needed for figuring calculations such as sales, revenue, etc. - I know how to do if statements, but it gets confusing to me after the first few ifs (easily get lost), but Python, C, C++, I can next tons of if statements just fine.

Some people, if they can immediately see the data or change, they like "programming" in that sense. Some like the, program, test it and see if it works method.

I guess my comment related to yours is, some people do know a thing or two in ways others may not think possible. Just need to get the right tools (for you) to express what you want to do. - Which is why I like VB.NET, but feel limited, so I'm expanding by learning C#, Python, etc.

---

### Post by ayyork on 2010-08-16
so python is  the easiest to learn for a beginner if any one else has any thing to add feel free to post some thing

---

### Post by worksofcraft on 2010-08-17
lol - well I learnt to program in assembler... that means specifying the actual instructions that your processor will be performing.

Many modern programming languages like Python are 'interpreted'. That means the processor is in reality mostly processing your program source files instead of processing your data!

Python is a great little language for learning to program and I strongly recommend it. However, when you feel ready, do have a look at a compiled language like C/C++. These are translated into machine code by a compiler. Thus they can run hundreds of times faster!

---

### Post by GenBattle on 2010-08-17
The easiest language to start with is definitely python. It is simple to set up, and you can literally program line-by-line with the console and experiment. It will also force you to do proper code indentation.

Some things i would suggest you make a component of your general knowledge if you haven't already;
[LIST]
[*]Algebra (yes, maths); this will help you wrap your mind around what variables are and how to use them, as well as some of the maths involved in computing.
[*]Boolean and bitwise logic; know the difference between the two, and how and why to use both.
[*]Learn the general idea of how computers work; Turing machines, fetch/execute or fetch/decode/execute cycles, etc.
[/LIST]

There's probably plenty of other things you should learn depending what you want to do with programming, but those are the ones that i think will help you to understand why/how a computer works. Personally i think knowing the why is just as important as the how.

Set yourself up with a project, no matter how crazy or outlandish it seems, and attack it. I think my first project was when i was about 12, attempting to create a virtual pet game in Visual Basic.

---

