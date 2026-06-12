---
title: "Please suggest a C++ project for a newbie open source developer"
date: 2007-01-31
forum: Programming Talk
---

### Post by kvorion on 2007-01-31
Hi All,

I professionally work on Microsoft's .NET platform, but I want to do some open source development on linux. I would prefer C/C++ for this purpose. I am not able to decide what libraries to use or what project to start with. Could anybody suggest me a good IDE, library and project that I can work on?

I have ubuntu breezy badger and xubunty edgy eft installed on my machine. The breezy OS has anjuta installed on it, while I dont have an IDE on the xubuntu box cos I dont know what IDE to install there as it is suggested to use only GTK apps in it and avoid Gnome/KDE.

Thanks

---

### Post by Tomosaur on 2007-01-31
You can still run GTK programs on XFCE as long as you have the GTK libraries installed. There should be no problem. I have only ever expreienced 'problems' using KDE apps on Gnome, and they were only because they interfaced with other KDE apps. If I installed those, it would have been fine.

As for a project, it's pretty much best to just go on what interests you. Which programs do you really like, or use regularly but think there could be something better done to it?

---

### Post by Stephen Howard on 2007-01-31
Your question is a trifle broad.  Most developers (or patch submitters) do what they do because they have an itch to scratch.  For instance, maybe they've used an application, game or utility and they've thought it could be tweaked to be made just that bit better.  They download the source, patch it and submit the change to the developer.

That said, for the .NET developer, the [MONO project]("http://www.mono-project.com/Main_Page") (.NET for linux) is the first stop.  The Free Software Foundation also has a .NET clone [dotGNU]("http://www.dotgnu.org/").

Mono bundles  a development environment, but you should also try [Eclipse]("http://www.eclipse.org/") which is both professional and cool.

---

### Post by kvorion on 2007-01-31
I think I am not gonna get involved in mono as yet. I want to do something on C/C++ on linux. It is true that most developers/patch submitters tweak their favourite programs and get started that way. 

I havent been able to get hold of a logical sequence of steps that will get me coding on linux. (in terms of pre-requisites). I am good at C/C++ in general. What other things are required before I can actually start creating applications?

---

### Post by Null Reference Exception on 2007-01-31
Some things to consider:

 - You've already chosen the language to implement a solution before working out what program/solution you will be tackling...

- Given that you are a professional developer, I think you know what steps are required if you think about it, something along the lines of:

  - Find a project/problem that interests you, can make money from, get recognition for, etc.
  - Determine what already exists, do you need to modify existing code, start from scratch, port something from another language, etc.
  - Design it
  - Choose the technology for implementation, get  the APIs you need, other components, etc.
  - Implement, document and test it
  - Release

something like that...

Im sure once you start going through this more questions will come up, eg. what IDE, compiler, version of APIs, how do I create an installer, how do i create man pages, what testing tools exist on linux, etc. etc. plus others that I have overlooked.

What language is Mono developed in... if C/C++perhaps you could contribute to Mono directly as opposed to using Mono to develop an application

---

### Post by Stephen Howard on 2007-01-31
> I havent been able to get hold of a logical sequence of steps that will get me coding on linux.

If you're looking for the compilers etc, do:  
```
sudo apt-get install build-essential
```
That will install the following packages:

> dpkg-dev (>= 1.13.5)    package building tools for Debian

g++ (>= 4:4.1.1)    The GNU C++ compiler

gcc (>= 4:4.1.1)    The GNU C compiler

libc6-dev    GNU C Library: Development Libraries and Header Files
or libc-dev Virtual package

make    The GNU version of the "make" utility. 

Once you've got the basic compiling system installed, there's still a whole bunch of other software from which programmers can choose: [Ubuntu Software Development Packages]("http://packages.ubuntu.com/edgy/devel/") - take your pick.

You'll also need a [programmers editor]("http://packages.ubuntu.com/edgy/editors/").  Again take your pick.

Every programming language under the sun is available - from scripting languages like perl, up to Ada etc.  Ruby is all the fashion at the moment.

---

### Post by Stephen Howard on 2007-01-31
If you're looking for a project to contribute to, [browse freshmeat]("http://freshmeat.net") - it has thousands of projects, big and small.  There's something there for everyone looking to contribute.

---

### Post by jblebrun on 2007-01-31
Ok, this question has become a FAQ, lately. However, it's a pretty good question. I propose we start a sticky topic, titled, perhaps:

"Getting started with coding in the open source community"

Here we can propose lots of suggestions, like
*Review BUG/TODO lists for your favorite programs, to see if you can help
*small projects that might be suitable for a beginner
*Small projects that have been orphaned, of which someone new and fresh could take over maintance.
*Our own projects for which we might like the help of developers

---

### Post by kvorion on 2007-02-03
> **Null Reference Exception said:**
> Some things to consider:

 - You've already chosen the language to implement a solution before working out what program/solution you will be tackling...



I guess I get your point. I said C/C++ because I am comfortable with those languages right now and did not want to spend time learning a new language before I start coding. But its true that some languages are more suitable for solving a certain kind of problems than other languages.

@Stephen
I have those packages installed

@jblebrun
That sounds like a good idea


Thanks all

---

