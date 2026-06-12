---
title: "Best programming language for Ubuntu?"
date: 2011-08-03
forum: Programming Talk
---

### Post by QuantumMonkey on 2011-08-03
I really like making programs to extend my knowledge of computers and to help people, and I recently moved from Windows 7 to Ubuntu, and I was wondering what programming language I should start with for Ubuntu.

If it matters, I know quite a lot of C#, but I know that it's only for windows since it requires the .net framework :P

---

### Post by worseisworser on 2011-08-03
With regards to C# there's Mono: [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

With regards to "best language for the Ubuntu or Linux platform"; this totally depends on what you want to do.

---

### Post by nmaster on 2011-08-03
> **QuantumMonkey said:**
> I really like making programs to extend my knowledge of computers and to help people

to extend your knowledge, learn assembly: [http://www.cafepress.com/bartlettpublish.8640017](http://www.cafepress.com/bartlettpublish.8640017) 
full text: [http://download.savannah.gnu.org/releases/pgubook/](http://download.savannah.gnu.org/releases/pgubook/)
there are other books available; i've never used this one and don't really have any specific recommendations

to write useful applications easily... there are a lot of options and it depends on what you want to do.  lots of people are going to suggest python and its a fine choice. just remember that a programming language is a tool and you should always choose the right choose for the task at hand.

---

### Post by cgroza on 2011-08-03
I know python is used a lot in Ubuntu. If you look around, many applets, tools and apps are written in python. C and C++ are popular too.

---

### Post by DangerOnTheRanger on 2011-08-03
I'd go with Python, mainly because not only does it work [pretty much everywhere]("http://www.python.org/download/other/") (like C/C++), it:

[LIST]
[*]Does what you tell it to do
[*]Tells you what went wrong without a debugger (instead of just printing "Segmentation fault" and giving up the ghost)
[*]Almost looks like regular English
[*] Has the best design-to-production time of any language I've seen
[/LIST]

---

### Post by karlson on 2011-08-03
> **QuantumMonkey said:**
> I really like making programs to extend my knowledge of computers and to help people, and I recently moved from Windows 7 to Ubuntu, and I was wondering what programming language I should start with for Ubuntu.

If it matters, I know quite a lot of C#, but I know that it's only for windows since it requires the .net framework :P

You are going about it from the wrong end.  You should be asking what is the best language for the problem you are trying to solve.  Ubuntu has the ability to compile or interpret quite a bit of different programming languages.

So for some problems C++ might be the answer, C for others, C# for others, Fortran, Python, Ruby, Perl, Erlang, R, Haskell.....

---

### Post by nvteighen on 2011-08-03
Read the stickies, please.

---

### Post by llanitedave on 2011-08-03
Best programming language for Ubuntu?

All of them.

---

### Post by Bachstelze on 2011-08-03
> **llanitedave said:**
> Best programming language for Ubuntu?

All of them.

        If the Tao is great, then the operating system is great.  If the
operating system is great, then the compiler is great.  If the compiler
is great, then the application is great.  If the application is great, then
the user is pleased and there is harmony in the world.
        The Tao gave birth to machine language.  Machine language gave birth
to the assembler.
        The assembler gave birth to the compiler.  Now there are ten thousand
languages.
        Each language has its purpose, however humble.  Each language
expresses the Yin and Yang of software.  Each language has its place within
the Tao.
        **But do not program in COBOL if you can avoid it.**
                -- Geoffrey James, "The Tao of Programming"

---

### Post by fdrake on 2011-08-03
I am not sayng is the most important language to use n ubuntu but is the one that you HAVE to know/learn if you want to use linux: BASH

---

### Post by Bachstelze on 2011-08-03
> **fdrake said:**
> I am not sayng is the most important language to use n ubuntu but is the one that you HAVE to know/learn if you want to use linux: BASH

I have used Linux for 5+ years, and I know zero Bash.

*EDIT:* Unless you include POSIX sh in it, of course.

*EDIT 2:* And even of that, I don't know a lot. I've never written a shell script containing more than 20 lines. The knowledge of shell scripting is far from essential to anyone who is not a sysadmin (which, thank goodness, I am not).

---

### Post by fdrake on 2011-08-03
> **Bachstelze said:**
> I have used Linux for 5+ years, and I know zero Bash.

*EDIT:* Unless you include POSIX sh in it, of course.

well, what i meant is the use of the terminal for every-day's tasks.

---

### Post by Bachstelze on 2011-08-03
> **fdrake said:**
> well, what i meant is the use of the terminal for every-day's tasks.

Then that's not really Bash. ;) Any shell works, and generally when people mention shell in programming contexts, they mean writing programs in the form of shell scripts. It's useful to know the basics, but not to go too deep in it unless you have a good reason to. It's not even all that interesting (yes, this is subjective).

---

### Post by stchman on 2011-08-04
Java would be a good choice.  Since you know a lot of C# it wouldn't be a big stretch for you.

Java can create truly platform independent programs as well.

---

### Post by directhex on 2011-08-04
> **QuantumMonkey said:**
> I really like making programs to extend my knowledge of computers and to help people, and I recently moved from Windows 7 to Ubuntu, and I was wondering what programming language I should start with for Ubuntu.

If it matters, I know quite a lot of C#, but I know that it's only for windows since it requires the .net framework :P

There are three C# apps by default on Ubuntu. If you like C#, you can stick with it.

---

### Post by directhex on 2011-08-04
> **stchman said:**
> Java would be a good choice.  Since you know a lot of C# it wouldn't be a big stretch for you.

Java can create truly platform independent programs as well.

C# can create truly platform independent programs. So can Java. C# can create single-platform apps. So can Java. The devil's in the details.

---

### Post by stchman on 2011-08-04
> **directhex said:**
> C# can create truly platform independent programs. So can Java. C# can create single-platform apps. So can Java. The devil's in the details.

My biggest thing is that C# is a Microsoft proprietary programming language while Java is more open source friendly.  The JDK (either openJDK or SUN/Oracle) was specifically made for Linux while Mono is a reverse engineered (very well done) .NET framework.

---

### Post by cgroza on 2011-08-04
> **stchman said:**
> My biggest thing is that C# is a Microsoft proprietary programming language while Java is more open source friendly.  The JDK (either openJDK or SUN/Oracle) was specifically made for Linux while Mono is a reverse engineered (very well done) .NET framework.
The C# language is open source. It has an ISO specification. Maybe you mean the .NET implementation of the C# language is closed source.

---

### Post by directhex on 2011-08-04
> **stchman said:**
> My biggest thing is that C# is a Microsoft proprietary programming language while Java is more open source friendly.  The JDK (either openJDK or SUN/Oracle) was specifically made for Linux while Mono is a reverse engineered (very well done) .NET framework.

C# is a spec registered with multiple international standards bodies. Java isn't.

---

### Post by DependencyHell on 2011-08-05
[QUOTE= by Bachstelze ]Then that's not really Bash. :wink:  Any shell works, and generally when people mention shell in programming  contexts, they mean writing programs in the form of shell scripts. It's  useful to know the basics, but not to go too deep in it unless you have  a good reason to. It's not even all that interesting (yes, this is  subjective). 	[/QUOTE]

Hmm...i am just getting into shell and C combination (i know well only C++ and C for now). 
But this combination looks very powerful to me! I believe that one must choose the language most intuitive for one's reasoning.

---

### Post by Bachstelze on 2011-08-05
> **DependencyHell said:**
> I believe that one must choose the language most intuitive for one's reasoning.

Certainly. And shell has never been intuitive for me. To each their own. ;)

---

