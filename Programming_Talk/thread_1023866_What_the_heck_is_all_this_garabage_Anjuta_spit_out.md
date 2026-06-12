---
title: "What the heck is all this garabage Anjuta spit out?"
date: 2008-12-28
forum: Programming Talk
---

### Post by Arukas on 2008-12-28
I finally got Anjuta to compile and run a program.  I am a little bit distressed though.

My source code consisted of a 90 byte "Hello" program  And my project directory has 54 files totally at 3.0 Megas in it!!!!  The excuteable is only 10 kBits itself.  

No wonder I had trouble trying to get it to work.  What is all this garbage?

---

### Post by slavik on 2008-12-28
it's not garbage, it's automake stuff. all projects use it.

---

### Post by Arukas on 2008-12-28
For a simple Hello, it all unnessary.  Is there a good tutorial or something that explains all this automake stuff and makes sense.  It might help if I knew what it meant.  

Also, in code::blocks it did not have the 52 additional files for my simplistic Hello project, I created.

---

### Post by slavik on 2008-12-28
code::blocks does not use automake, afaik ...

personally, I wouldn't worry about it, since it is not integral to your projects.

Also, I tend to use Geany for single file type of programs.

---

### Post by rich1939 on 2008-12-28
> **Arukas said:**
> I finally got Anjuta to compile and run a program.  I am a little bit distressed though.

My source code consisted of a 90 byte "Hello" program  And my project directory has 54 files totally at 3.0 Megas in it!!!!  The excuteable is only 10 kBits itself.  

No wonder I had trouble trying to get it to work.  What is all this garbage?

I too tried to use Anjuta was appalled by the number of cryptic files that were generated when I created a new project. I also was able to compile the "Hello" program, but when I decided to move on and add a new library to the build, I was unable to find a way to do so.

I finally switched to **Code::Blocks** and am a happy programmer. I use Glade as my interface designer and have added Pre-build command to automatically convert Glade's XML file to an XML that's compatible with GtkBuilder.

Everything is simpler with Code::Blocks (and it's cross-platform, too!).

---

### Post by snova on 2008-12-28
It has nothing to do with Anjuta and everything to do with Autotools.

Autotools = Autoconf + Automake + Atonmore

Autoconf takes an input file, configure.ac, and runs it through a macro processor to generate configure. Several more files are produced as side-effects. Then when you run configure it generates several more files!

Automake takes Makefile.am files and generates Makefile.in files. Then configure takes those and generates Makefile's! Both of these generated files get quite long.

Then there's config.h.in and config.h. The latter is auto-generated. Come to think of it, so is the former, but by the IDE.

libtool, as I recall, builds all of your libraries twice- static and shared. Some are put in hidden folders (in the plural!).

Code::Blocks generates a single, custom Makefile. Nothing more.

Now do you know why the system is sometimes called Autohell? :P

---

### Post by cl333r on 2008-12-28
> **slavik said:**
> it's not garbage, it's automake stuff. all projects use it.

NetBeans uses less than 100KB (the whole project!) for a hello world Gtk program written in C. So it's either a wrong configuration of Anjuta or ... eh.. why not switch to Eclipse or NetBeans they don't create such a lot of stuff for such a little reason

---

### Post by snova on 2008-12-28
> **cl333r said:**
> NetBeans uses less than 100KB (the whole project!) for a hello world Gtk program written in C. So it's either a wrong configuration of Anjuta or ... eh.. why not switch to Eclipse or NetBeans they don't create such a lot of stuff for such a little reason

Because they use their own, custom build systems. And then you'd need the entire IDE installed just to compile from source.

Autotools is a gigantic mess, but it does a pretty good job of building correctly on different platforms. That takes infrastructure, and that has to be put somewhere.

One of the reasons you get such a large project with Autotools is that it includes all the necessary stuff with it. On the up side, you don't have to install anything else to build the software- only the -dev packages. On the down side, it's a lot bigger.

Alternative tools, like SCons, CMake, and so on simply move the infrastructure out of the project and into the engine- which is not included.

(Technically, you *could* include these engines with the project. SCons even has a 'local' build for this purpose that adds about 300 KB or so, archived. CMake, on the other hand, is C++, so no go.)

---

### Post by ProgramErgoSum on 2008-12-28
I can understand the idea behind this question. For a significant project, all those files are important. But, to me, as a learner of C, I am also surprised at the number of files required. It is confusing...

---

### Post by slavik on 2008-12-29
Well, in all fairness you do not need to set up an automake project. You just need whatever source and header files you write and a simple makefile. But automake does do a nice job of checking for libraries and where they are such.

---

### Post by Arukas on 2008-12-29
So in its simplist form, what automake do?  At one point, I will probably work on bigger projects.  I would like to be some what active in the opensource community.

---

### Post by slavik on 2008-12-30
it read where libraries are installed, figures out what libraries are missing, where to place files when installing, what the standard compiler is, whether different tools accept certain flags ...

I am pretty sure that is only scratching the surface.

---

### Post by snova on 2008-12-30
> **slavik said:**
> it read where libraries are installed, figures out what libraries are missing, where to place files when installing, what the standard compiler is, whether different tools accept certain flags ...

I am pretty sure that is only scratching the surface.

Technically, that's Autoconf, not Automake...

Autoconf does as slavik said- prepares for building.

Automake generates template files for Autoconf to process into Makefiles.

---

### Post by Jonas thomas on 2008-12-31
> **snova said:**
> It has nothing to do with Anjuta and everything to do with Autotools.

Autotools = Autoconf + Automake + Atonmore

Autoconf takes an input file, configure.ac, and runs it through a macro processor to generate configure. Several more files are produced as side-effects. Then when you run configure it generates several more files!

Automake takes Makefile.am files and generates Makefile.in files. Then configure takes those and generates Makefile's! Both of these generated files get quite long.

Then there's config.h.in and config.h. The latter is auto-generated. Come to think of it, so is the former, but by the IDE.

libtool, as I recall, builds all of your libraries twice- static and shared. Some are put in hidden folders (in the plural!).

Code::Blocks generates a single, custom Makefile. Nothing more.

Now do you know why the system is sometimes called Autohell? :P

In case anyones interested, there is a very interesting pdf [tutorial]("http://www.lrde.epita.fr/~adl/autotools.html") on the Autohell stuff...
(It's best viewed with Adobe, so you can get the animation affect when your going page to page).. 
+1 on C::B

---

### Post by monkeyking on 2009-01-03
> **Jonas thomas said:**
> In case anyones interested, there is a very interesting pdf [tutorial]("http://www.lrde.epita.fr/~adl/autotools.html") on the Autohell stuff...
(It's best viewed with Adobe, so you can get the animation affect when your going page to page).. 
+1 on C::B

I've been using this, but it's a wobbling 557 pages long...

I have been looking for at quick guide for using this autotools,
and I couldn't find any.
But I've written a small guide for using autotools 
[http://ubuntuforums.org/showthread.php?p=6489794#post6489794](http://ubuntuforums.org/showthread.php?p=6489794#post6489794)
You basicly only need to create two Makefile.am's, one configure.ac and a README.

---

