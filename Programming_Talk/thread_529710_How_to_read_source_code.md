---
title: "How to read source code"
date: 2007-08-19
forum: Programming Talk
---

### Post by MiCovran on 2007-08-19
I tried to read some source code before, but I just couldn't. I don't know where to start. I recently ran into [this]("http://ubuntuforums.org/showthread.php?t=528847") thread about contributing to projects. I'm in a similar situation like laxmanb, I would like to learn and contribute too. Reading all those posts I realized I really do need to start reading some code.

It's just that I don't know how. I downloaded rhythmbox and gcalctool source codes. I always thought that every program should begin with "main" function, but I can't find it with grep and I really don't know how to start.

---

### Post by pmasiar on 2007-08-19
Yes, reading code of other people is important skill which is not easy to gain. And as everything in programming, you gain the skill by doing it.

I don't want to belittle you, but if you don't know how to read the code from a big project, maybe you are not ready to contribute to it. As I said in linked thread, train  your kata before going for kumite :-)

You need to write couple training projects before you will be ready to face real-word project. Also, using high-level language like Python helps here too, because you have less code to read and comprehend, and there is smaller mental distance between problem and algorithm code using higher abstractions.

I cannot give more than generic advice because I don't know your age, experience, skill level, and interests. What language is your goal? What project? There are many ways to learn it, and we can help, but we cannot learn instead of you. 

As they say, you can bring horse to water, but you cannot make it drink. :-)

---

### Post by Geekkit on 2007-08-19
Take a programming course or if you feel that you are highly disciplined, start reading through tutorials on a programming language.

---

### Post by MiCovran on 2007-08-19
> I don't want to belittle you, but if you don't know how to read the code from a big project, maybe you are not ready to contribute to it. As I said in linked thread, train your kata before going for kumiteI am aware of this. First of all, I want to learn. Contributing is a goal for future. And by contributing, I mean small things. I'm not very ambitious. :)
> Also, using high-level language like Python helps here too, because you have less code to read and comprehend, and there is smaller mental distance between problem and algorithm code using higher abstractions.First, some highlights on my programming history:
In 5th grade of elementary school (11 years old) I went to my first computer science class. I had a great teacher who interested me into Logo. I liked it and there my love for coding began. Next year, he taught me QBASIC and I got a hang of it, too. I've been practicing it until 8th grade, only using it for algorithm problems.
Then I started going to high school (15 years old). Over there, I've learned Pascal and started going to algorithm competitions. Those competitions are for Pascal/C/C++ and, because C++ has STL, it has an advantage over Pascal. So I used my summer holiday to learn C++ with books and tutorials. I've been using it since now (17 years old, 3rd grade of high school), still only for algorithm competitions.

Now why am saying all this? It's just to tell you that I love programming and algorithm competitions, but I'm just getting a little bit tired of doing nothing useful in real world. I would like to learn how real programming looks like. I know that Python is a better beginners language, but I hope you understand that I don't wish to learn another language now. I think I can read C/C++ with good understanding now and I believe this mental distance shouldn't be a problem. The most important reason is, actually, that most of the programs are written in C (as far as I know). Sure, I will learn Python. It's just that I would like to DO something first, if you understand what I mean.

> I cannot give more than generic advice because I don't know your age, experience, skill level, and interests. What language is your goal? What project? There are many ways to learn it, and we can help, but we cannot learn instead of you.So here it goes in short:
Age: 17
Experience: algorithm problems only
Skill level: good knowledge of C++, but only language, no GUI or any other additional skills
Interests: I like to know how stuff works, doing something useful and finding logic everywhere (not just in programming)
Project: I thought I could find some projects (like gcalctool or rhythmbox mentioned before) and learn how they work in basics first (like how rhythmbox uses XML to store data and, most important, where do those programs begin!?)

Thank you for your helpful tips and please, correct me where I'm wrong. Sorry for this loooong post.

---

### Post by pmasiar on 2007-08-19
> **MiCovran said:**
> So I used my summer holiday to learn C++ with books and tutorials. 

Wow, you are pretty ambitious and with a drive - learning C++ by yourself - all you need is to get a chance! 

Wiki in my sig has couple training task, which don't require GUI. You can continue with C++ and solve it in C++  (they are language independent), or pick Python - with your background, picking up Python should be a week or so. BTW, I read somewhere that in South Africa (where Mark Shuttleworth is from), Python is also allowed in those competitions, and about half of top 10 solution was in Python, so take a look at it. And yes, using Python over C++ is really unfair advantage, but if you can get it, why not? :-)

Another good training kata you can get at pythonchallenge.com : 30 tasks with increasing complexity, teaching you different parts of the language, with separate forum for every level. Couple months of good fun solving them all!

Another excellent environment to learn programming is [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) - it is Windows only, but really intuitive and fun. You will learn many tricks of event-driven programming without really writing much code. With your C++ background it may seem little childish, but it's simplicity is deceiving: you can create pretty interesting games in it! Deceiving also because you have to handle all the same problems you will have to handle in C++, just on much higher level (so more obvious) And because it is so high-level, you can do it in short time (hours, days and weeks, not months).

Keep us posted about your progress, and ask for help if stuck.

---

### Post by Tuna-Fish on 2007-08-19
> **MiCovran said:**
> 
Project: I thought I could find some projects (like gcalctool or rhythmbox mentioned before) and learn how they work in basics first (like how rhythmbox uses XML to store data and, most important, where do those programs begin!?)


The gcalctool source is in (gcalctool source dir)/gcalctool. from that dir, look up makefile.am. it's a file for automake that tells what all files are used for compiling what binaries. The line 17 "bin_PROGRAMS = gcalctool" tells us that there is one executable file, gcalctool. Below it is a list of all the files used in it. grep those files for 'main', right in the middle is gtk.c, line 486.

gtk.c is, however, just a file for the initialization of gtk, the graphical interface. The beginning of the actual program is called on line 523, and it resides on line 1150 in calctool.c

(all line numbers are for the version of gcalctool that I just grabbed using apt-get source gcalctool on feisty)

---

### Post by MiCovran on 2007-08-20
> The gcalctool source is in (gcalctool source dir)/gcalctool. from that dir, look up makefile.am. it's a file for automake that tells what all files are used for compiling what binaries. The line 17 "bin_PROGRAMS = gcalctool" tells us that there is one executable file, gcalctool. Below it is a list of all the files used in it. grep those files for 'main', right in the middle is gtk.c, line 486.
I wonder how I missed it. Thanks, now I know where to look for (makefile.am). I made a mistake searching for "int main" instead of just "main". I found only a prototype in calctool.h.
> Wiki in my sig has couple training task, which don't require GUI.Sorry, but I can't find them.
> Another excellent environment to learn programming is [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) - it is Windows only, but really intuitive and fun. You will learn many tricks of event-driven programming without really writing much code. With your C++ background it may seem little childish, but it's simplicity is deceiving: you can create pretty interesting games in it! Deceiving also because you have to handle all the same problems you will have to handle in C++, just on much higher level (so more obvious) And because it is so high-level, you can do it in short time (hours, days and weeks, not months).I'll check it out.

---

### Post by hdanak on 2008-04-27
For anyone else who is having this problem (I certainly was) I recommend that you check out the book *Code Reading: The Open Source Perspective* By Diomidis Spinellis.
Good Luck.

---

