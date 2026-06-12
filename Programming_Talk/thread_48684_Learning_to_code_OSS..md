---
title: "Learning to code OSS."
date: 2005-07-13
forum: Programming Talk
---

### Post by jaardsi on 2005-07-13
I've been programming for about 2 to 3 years, depending how you count. I think myself as a quite promising young coder, even if not in a technical kind of sense. I used Windows back when I started, but about a year ago moved to Linux, which I've been now loving since then.

Now after using Linux and other open source projects for nearly a year, I want to start contributing back to open source software by programming. But a problem looms in the distance...

I'm a total slacker and have hard time learning a programming language I have no use for. I do Perl quite fluently, mainly because I use it to solve most of my everyday Linux problems. I've tried C++, but never get past beginning. I have simply nothing interesting to code! ](*,) 

So my question is: What is the easiest way for a lazy guy like me to get into C++ and start contributing to OSS? Should I start a small project of my own or what? Help me!

---

### Post by Kimm on 2005-07-13
I suggest that you first off try and find something that you want to do :P
Personaly I have way to many projects at the same time and cant possibly keep track of them all, I allways have the ideas but maby not the ability to make them reality.

When you know what you want to do, you can eighter make a project of your own or perhaps try and find a similar project and join in.

There is nothing forcing anyone to contribute to Open Source Software I'm sure you'll be inspired by something  in the future and that drives you into writing a program that does just what you want it to :)

I'm sure you'll find something! ^^

---

### Post by virgule on 2005-07-13
I, for one, would join a project I find interesting and contribute there as we dont need yet-another-file-manager ;)

---

### Post by trivialpackets on 2005-07-13
[QUOTE=jaardsi]I've been programming for about 2 to 3 years, depending how you count. I think myself as a quite promising young coder, even if not in a technical kind of sense. I used Windows back when I started, but about a year ago moved to Linux, which I've been now loving since then.

Now after using Linux and other open source projects for nearly a year, I want to start contributing back to open source software by programming. But a problem looms in the distance...

I'm a total slacker and have hard time learning a programming language I have no use for. I do Perl quite fluently, mainly because I use it to solve most of my everyday Linux problems. I've tried C++, but never get past beginning. I have simply nothing interesting to code! ](*,) 

So my question is: What is the easiest way for a lazy guy like me to get into C++ and start contributing to OSS? Should I start a small project of my own or what? Help me![/QUOTE]
 I'm working on a gradebook.  It was a group project for an introductory C++ class that has grown out of control  :)  We're well beyond the class and still improving it, and I'm beginning to read up on using QT to make it graphical rather than the console based.  It's a huge undertaking, as our code is quite robust and over 4000 lines so far, and I'm unsure as to how I'll manipulate our linked lists of structs that it is all built upon :)  within the GUI.  I want to be able to distribute it with local schools/teachers when it is complete.  That's what I'm getting ready to work on.  Also considering GTK, as I've no real experience with it yet.  Any suggestions would be great.

---

### Post by kamstrup on 2005-07-13
**eric.proctor**
GTK vs QT (and if QT would it be qt3 or qt4?) is a tough choice... If you're familiar with C++ QT would be the natural choice (since it's pure c++) but remember there are also really good C++ bindings for GTK in the GTKmm package. Although I may tend a little towards GTK myself, I think that QT might just be a little bit easier to get started with (mostly because of excellent documentation).

**jaardsi**
It is quite understandable that you choke on C++. If you ask me C++ is unparalleled the most difficult programming language on this planet. It is good - don't get me wrong - but *difficult*.

Being the lazy type I'd suggest Python. It is really easy both to learn and debug. As a bonus to this is the fantastic GTK bindings that makes GUI programming a breeze (the package is called python-gtk2 or pygtk). If you really want to do some hardcore coding go for C over C++ - atleast to begin with [1]

Your un-interest in coding probably stems from your lack of succes - which is understandable. I guarantee that the Python/GTK will make you productive really fast. As an extra argument Python is also officialy supported by  Ubuntu.

If you're still with me Eric, it might also be an option for you to wrap you stuff in Python and use pygtk..?

[1]: The language definition for C++ is over **900 pages**, while it's a little over 100 for C.

---

### Post by trivialpackets on 2005-07-13
[QUOTE=kamstrup]**eric.proctor**
GTK vs QT (and if QT would it be qt3 or qt4?) is a tough choice... If you're familiar with C++ QT would be the natural choice (since it's pure c++) but remember there are also really good C++ bindings for GTK in the GTKmm package. Although I may tend a little towards GTK myself, I think that QT might just be a little bit easier to get started with (mostly because of excellent documentation).

**jaardsi**
It is quite understandable that you choke on C++. If you ask me C++ is unparalleled the most difficult programming language on this planet. It is good - don't get me wrong - but *difficult*.

Being the lazy type I'd suggest Python. It is really easy both to learn and debug. As a bonus to this is the fantastic GTK bindings that makes GUI programming a breeze (the package is called python-gtk2 or pygtk). If you really want to do some hardcore coding go for C over C++ - atleast to begin with [1]

Your un-interest in coding probably stems from your lack of succes - which is understandable. I guarantee that the Python/GTK will make you productive really fast. As an extra argument Python is also officialy supported by  Ubuntu.

If you're still with me Eric, it might also be an option for you to wrap you stuff in Python and use pygtk..?

[1]: The language definition for C++ is over **900 pages**, while it's a little over 100 for C.[/QUOTE]
 For me, I'm doing it mainly as a way to keep progressing with C++, and as I don't have any real experience with python yet, I'm going to probably go with attempting the coding with c++.  Python is something I am interested in knowing, but I figure it's kind of why I started with slackware before coming to Ubuntu, it made the transition easier.  I may look into python later, but not now. Thanks for the tip though.

---

### Post by m87 on 2005-07-14
[QUOTE=kamstrup]**eric.proctor**
GTK vs QT (and if QT would it be qt3 or qt4?) is a tough choice... If you're familiar with C++ QT would be the natural choice (since it's pure c++) but remember there are also really good C++ bindings for GTK in the GTKmm package. Although I may tend a little towards GTK myself, I think that QT might just be a little bit easier to get started with (mostly because of excellent documentation).[/QUOTE]

GTK-- is PAIN to use, it handles signals through sigc++ with IMHO is bloody complicated. Therefore, despite my KDEphobia I think that QT is the best C++ choice. Although I would suggest GTK# for C#, which are awesome bindings!

[QUOTE=kamstrup]**jaardsi**
It is quite understandable that you choke on C++. If you ask me C++ is unparalleled the most difficult programming language on this planet. It is good - don't get me wrong - but *difficult*.

Being the lazy type I'd suggest Python. It is really easy both to learn and debug. As a bonus to this is the fantastic GTK bindings that makes GUI programming a breeze (the package is called python-gtk2 or pygtk). If you really want to do some hardcore coding go for C over C++ - atleast to begin with [1][/QUOTE]

I agree. C++ has always been an unlucky language, in my opinion.

[QUOTE=kamstrup]Your un-interest in coding probably stems from your lack of succes - which is understandable. I guarantee that the Python/GTK will make you productive really fast. As an extra argument Python is also officialy supported by  Ubuntu.

If you're still with me Eric, it might also be an option for you to wrap you stuff in Python and use pygtk..?

[1]: The language definition for C++ is over **900 pages**, while it's a little over 100 for C.[/QUOTE]

Well, I bet Mono's worth a try. And C# is a really good language. You can dive into it, you'll like it :)

---

### Post by kamstrup on 2005-07-15
You're absolutely right m87. Mono/GTK# is also thoroughly documented. That is invaluable!

---

