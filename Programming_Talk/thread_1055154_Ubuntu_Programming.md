---
title: "Ubuntu Programming"
date: 2009-01-30
forum: Programming Talk
---

### Post by Wovaki on 2009-01-30
Hello!

I have just recently installed Ubuntu on my system, on Windows I have been working with Visual Basic.NET for almost a year, and I was wondering what would be a good programming language to learn for Ubuntu.

Please don't say look in the stickies, as I have already taken a look, but I would like some recommendations from some skilled Ubuntu programmers.

The main ones I can't decide between are Java, and C++. But I see Python seems to be really popular here.

So my question is:
Which programming language would you reccomend, and why?

For that programming language, which IDE, and where is a good place for me to start learning it?

[Edit]
I thought I would just mention, that this is mainly for a hobby, and I'm not planning to do anything specific with whatever language I learn for now.

Thanks in advance!
Wovaki

---

### Post by Sorivenul on 2009-01-30
First, thank you for reading the Stickies and browsing to see the trends here. Java, C++, and Python are all very popular around here.

If you are looking to do simple programming as a hobby, Java and C++ are, IMO, a bit intensive to learn. Python is widely used and supported here, but we are not a "Python-only" group. In the end it depends on what you want to do. What type of applications did you develop with VB.NET? Do you want to port them to some other language to use more easily on Ubuntu? Do you just want to learn for learning's sake and then possibly become more serious about development?

Of the three, I would say Python and C++ are probably more widely used in Ubuntu, and Linux in general. That said, since you've read the Stickies and hopefully some of the links included there, you know that Python works more easily cross-platform than C++, so if portability may become a concern down the road, Python may be the way to go. C++ offers some speed improvements over Python, but if you aren't doing a lot of floating-point calculations, using intensive algorithms, or other memory intensive operations, the factor of speed is, IMO, largely irrelevant.

In the end, the decision is yours. Editors and IDEs are covered many times in many threads, and the discussion regarding them is likely to cause a flame war. That said, as far as IDEs go, Code::Blocks and Anjuta are popular, dedicated C/C++ IDEs; SPE (Stani's Python Editor) and Eric are often recommended Python IDEs. As far as general-purpose IDEs, Geany is quite popular and rightfully so (it handles all three languages you are interested in and many more), and Eclipse with its plug-in system can do just about anything (especailly with Python, C/C++, and Java). 

Didn't mean to write a book. :D Good luck!

---

### Post by jimi_hendrix on 2009-01-30
> **Sorivenul said:**
> First, thank you for reading the Stickies and browsing to see the trends here. Java, C++, and Python are all very popular around here.

If you are looking to do simple programming as a hobby, Java and C++ are, IMO, a bit intensive to learn.

then i have to be absolutely insane because i normally mess around in C++ :)

also you can write VB.Net with mono i believe (though VB is generally considered evil)

java has powerful GUI design also

ide wise it is recommended to use an editor and command-line compiler for a little while before using IDE's...but java wise go for netbeans or eclipse, and C++ i hear anjuta, code::blocks, and eclipse with a plugin are nice

editor wise i use vim and gedit

---

### Post by Wovaki on 2009-01-30
Thanks for the replys.

I really don't have any specific ideas of what I want to make, I just like to mess around and play with programming. 

C++ I know can be hard to learn, how is Python?

Being able to make programs for both Windows and Linux would be nice, but that is not a big need.

If I were to deploy my Python projects, what prerequisites are needed for the user before they can use my app? I have seen a few python programs, and I always seen you needed to install and download stuff before using that app.

Also after this week, I will probably have no internet connection for 2-4 weeks. So it would be nice to have some language documentation, sort of like Microsoft's that comes with their IDE.

The main thing is, I want something **Easy to learn, fun, hopefully good GUI stuff, etc.**

Thanks!
Wovaki

---

### Post by shadylookin on 2009-01-30
I really enjoy java. I think it has a pretty gentle learning curve and a wealth of standard libraries. Plus it's portable so you can show off your work to all your windows friends.

c++ is used more for user applications and it's certainly not beyond anyones capability to learn.

python has a pretty easy syntax so it's pretty good for a hobbyist. It's bytecode also runs on other operating systems 

since it's just a hobby you might as well just pick the one that interests you the most

---

### Post by snova on 2009-01-30
> **Wovaki said:**
> C++ I know can be hard to learn, how is Python?

Easy to pick up, yet applicable to nearly anything. :)

> If I were to deploy my Python projects, what prerequisites are needed for the user before they can use my app? I have seen a few python programs, and I always seen you needed to install and download stuff before using that app.

Python. :P But I wouldn't know.

> Also after this week, I will probably have no internet connection for 2-4 weeks. So it would be nice to have some language documentation, sort of like Microsoft's that comes with their IDE.

Official tutorial: [http://docs.python.org/tutorial](http://docs.python.org/tutorial)
Downloadable HTML: [http://www.python.org/doc/2.6/download](http://www.python.org/doc/2.6/download) (includes tutorial, reference, and all the rest!)

---

### Post by jimi_hendrix on 2009-01-30
> **Wovaki said:**
> Thanks for the replys.

I really don't have any specific ideas of what I want to make, I just like to mess around and play with programming. 

C++ I know can be hard to learn, how is Python?

i think thats a myth about C++ if you learn it correctly and in manageable chunks

python is simpilar than C++ and most will advise it as a first language (i personally dont like it...also check out the language ruby, its similar to python)

> 
Being able to make programs for both Windows and Linux would be nice, but that is not a big need.

If I were to deploy my Python projects, what prerequisites are needed for the user before they can use my app? I have seen a few python programs, and I always seen you needed to install and download stuff before using that app.


they would need a python interpreter and depending on the app some python libs

> 
The main thing is, I want something **Easy to learn, fun, hopefully good GUI stuff, etc.**

Thanks!
Wovaki

define fun and good GUI stuff (most languages are fun in some sense and have some type of GUI toolkit)

---

### Post by Wovaki on 2009-01-30
Well I want to be able to make GUI apps.
And I don't know, everyone would have different opinions about which language is fun or not.

---

### Post by jimi_hendrix on 2009-01-30
python, C++, and java can make GUI's

try netbeans IDE for java RAD gui's

and that is why we need you to define fun (for me it is problem solving with C++)

---

### Post by Wovaki on 2009-01-30
I think maybe I will give Java a try.

What's a good IDE for java, and a good place to start learning it?

---

### Post by jimi_hendrix on 2009-01-30
netbeans and eclipse are the main java ides

i hear netbeans is better for GUI's

sun has an official java tutorial which is great

---

### Post by CptPicard on 2009-01-30
> **Wovaki said:**
> 
C++ I know can be hard to learn, how is Python?

Python is easy to learn, but it is not just that... I know that there are some people around who try to refute all the more interesting intellectual qualities of higher-level languages (because they don't understand them), but don't listen to them -- Python gives you ability to abstract about stuff in interesting ways, and IMO it is more beneficial for you in terms of learning about how to think about programming than is satisfying some arbitrary syntactic requirements of lower-level languages.

> 
If I were to deploy my Python projects, what prerequisites are needed for the user before they can use my app?

Essentially you would just build a "package" which is the common distribution mechanism.

> **Easy to learn, fun, hopefully good GUI stuff, etc.**

That would be Python, definitely.

---

### Post by nvteighen on 2009-01-30
> **Wovaki said:**
> 
C++ I know can be hard to learn, how is Python?


Python is amazingly easy. It's a very simple language to start with.

> If I were to deploy my Python projects, what prerequisites are needed for the user before they can use my app? I have seen a few python programs, and I always seen you needed to install and download stuff before using that app.

Ok, what you need is the Python interpreter. It generally comes installed by default in Debian and Debian-based Linux distros like Ubuntu. Then, if a certain application needs a module (equivalent to a library), you'll have to supply that module too. In the Debian and Debian-based world, you can create a .deb package with the dependencies set according to your needs... or, as the majority of modules are Free Software, you can just redistribute them if needed.

> Also after this week, I will probably have no internet connection for 2-4 weeks. So it would be nice to have some language documentation, sort of like Microsoft's that comes with their IDE.

It probably is already installed by default in Ubuntu, but I'm not sure (I'm a Debian user). Open a terminal and type:
```

sudo apt-get install python-doc devhelp

```

Devhelp is a nice documentation browser for GNOME you can use for several documentations... After it is installed, look at it at Applications->Programming in GNOME. If you happen to use KDE or whatever, don't worry: open your web browser and go to file:///usr/share/doc/python-doc/

> The main thing is, I want something **Easy to learn, fun, hopefully good GUI stuff, etc.**

For GUI, Python is very convenient, as it is compatible with all GUI toolkits available for GNU/Linux: GTK+ (GNOME look), Qt (KDE look), wxWidgets, and if I'm not wrong also Tk.

---

### Post by Wovaki on 2009-01-30
I just downloaded a .zip file from Sun Java with tutorials in it, what IDE do I use for Python if I use it?

Also, should I use the netbeans IDE in the Add/Remove Programs (6.1) or the newest one (6.5?) from their website?

Thanks

---

### Post by jimi_hendrix on 2009-01-30
> **Wovaki said:**
> I just downloaded a .zip file from Sun Java with tutorials in it, what IDE do I use for Python if I use it?

Also, should I use the netbeans IDE in the Add/Remove Programs (6.1) or the newest one (6.5?) from their website?

Thanks

theres IDLE (the officle one) but ive heard most python users use some type of editor

---

### Post by nvteighen on 2009-01-30
> **Wovaki said:**
> I just downloaded a .zip file from Sun Java with tutorials in it, what IDE do I use for Python if I use it?

Also, should I use the netbeans IDE in the Add/Remove Programs (6.1) or the newest one (6.5?) from their website?

Thanks
You don't need an IDE for Python... at least not until you do GUI stuff (which is a bit more advanced). Use Gedit or any editor with syntax highlighting.

---

### Post by agim on 2009-01-30
Seriously, python is amazing. I like C++ as well, and sometimes I use java (but generally, only when forced to, just not my cup of tea). I am a hobbyist as well.
There is so much python can do, and quickly. For instance, when I first started programming a year ago, I was able to set up a program, with GUI, that would cull certain websites and give me back info about the 8 leading presidential candidates, strip the html, and save the body of the text to a file.

I was able to do this in something like 200 lines (it may have even been less, but it was a long time ago).

Good luck with whatever you choose.

---

### Post by Wovaki on 2009-01-30
Ok, I seem to be getting more comments about Python.

So, I just downloaded IDLE for Python and a PDF Tutorial from one of the links on the first page of this thread.

Is there anything else that I should have, or know before starting to learn Python. It would be nice to be able to do most of my learning offline if possible, since I usually don't have a lot of internet time.

---

### Post by jimi_hendrix on 2009-01-30
> **Wovaki said:**
> Ok, I seem to be getting more comments about Python.

this might have to do with the fact that the majority of the forum advocates python...they do it for a reason though

i say check java and python out (partially because i started with C#, which is microsoft's java (or VB.Net with C syntax))

---

### Post by agim on 2009-01-30
There are some free programming books for python. Dive into Python and Thinking in Python come to mind.
Here are several more.
[http://www.freetechbooks.com/python-f6.html](http://www.freetechbooks.com/python-f6.html)

Edit: Dive into Python is supposed to be "For experienced programmers" according to the writer.

---

### Post by myrtle1908 on 2009-01-30
Python is always pushed heavily here.

After reading your initial post and subsequent replies and given your experience with VB.NET and MS style IDE with drag-drop GUI generation, then Java with NetBeans will definitely suit you best.

First install the Java 6 SDK then go to [http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html) and download the JavaSE version which is only 40MB for linux.  Installing is a breeze.  Start off with one of the New Project wizards for GUI applications.  You will be creating slick, fully functional forms in no time.  Just like Visual Studio, you place a widget on a form, double click it to add code etc.  Very very simple.

---

### Post by CptPicard on 2009-01-30
> **jimi_hendrix said:**
> this might have to do with the fact that the majority of the forum advocates python...they do it for a reason though


Yeah, we do it because we're right... ;)

Anyway, something one might try with Python is PyDev, an Eclipse plugin. But anyway most of the time you should be fine with a text editor.

---

### Post by Wovaki on 2009-01-30
Well I think I will learn Python.
Since it is heavily used on these forums, that should be good, and easy to get help if needed.

Does anyone have any tips/suggestions for me?

Thanks

---

### Post by jimi_hendrix on 2009-01-30
forget everything you learned about basic xD

---

### Post by Kilon on 2009-01-30
> **Wovaki said:**
> Thanks for the replys.


C++ I know can be hard to learn, how is Python?


 
I think that is a bit of a myth, C++ is not that hard to learn. I learned it when I was still quite noobish was not that bad. And I certainly would not discourage a beginner to learn the language. 

But when python comes which makes things alot easier , it is a temptation hard to resist. Of course python is not the only "easy" yet extremely powerful language out there. But I would agree that is probably the best implementation. 

The nice thing is that python , like java is very cross platform and that means your programms will work on ubuntu, windows and macos luckily without changing a line of code. 

If you interested in Java , there is is jython which is java and python united. I used it. I love it. I highly recommend it for anyone wanting to have the best of the two worlds.

---

### Post by Wovaki on 2009-01-30
I think I will try out Python.

I have IDLE for an IDE, and I downloaded some Python books.
I see there is a Python Interpreter on here already, so is there anything else I need?

Also, what exactly does a Python Interpreter do?

Thanks

---

### Post by jimi_hendrix on 2009-01-30
> **Wovaki said:**
> I think I will try out Python.

I have IDLE for an IDE, and I downloaded some Python books.
I see there is a Python Interpreter on here already, so is there anything else I need?

yes unless you want a specific library/module
> 
Also, what exactly does a Python Interpreter do?

Thanks

go to terminal and type python, then start entering python code, line by line...thats what it does, it reads your code and preforms actions based upon it (not the best description probably)...and when you do python code.py it reads in the entire file and does the same thing, line by line

---

### Post by Wovaki on 2009-01-30
So if I write my Python code in a text file, what do I use to compile it into an executable file?

Also, how do I make GUI apps?

Thanks

---

### Post by fiddler616 on 2009-01-30
> **Wovaki said:**
> I think I will try out Python.

I have IDLE for an IDE, and I downloaded some Python books.
I see there is a Python Interpreter on here already, so is there anything else I need?

Also, what exactly does a Python Interpreter do?

Thanks
The Python interpreter, well, lets you run Python programs (it's called by IDEs and stuff), but it's also a command-line utility that lets you execute a Python program, or do Python interactively (that will be explained in your tutorial).
Before you lose the internet (with its downloads and fora) I'd open up IDLE, make a new file, type in
[PHP]print "Hello World!"[/PHP]
and execute it. If a terminal comes up with 'Hello World!' on it, you're good to go, just make sure you downloaded the right tutorial :)
If for whatever reason the program doesn't run, report back here.

---

### Post by Wovaki on 2009-01-30
When I run IDLE, a window pops up called "Python Shell"
When I type in print "Hello World!" It just says Hello World! on a new line in "Python Shell"

---

### Post by fiddler616 on 2009-01-30
> **Wovaki said:**
> When I run IDLE, a window pops up called "Python Shell"
When I type in print "Hello World!" It just says Hello World! on a new line in "Python Shell"
To be honest, I used IDLE for about 30 seconds, decided I hated it, and forgot all about it. But I'm pretty sure there's a text-editing feauture on it--in fact I feel like I used it. Don't ask me how to get to it if all you're getting is the shell though (by the way, welcome to interactive Python).
There's always Geany, too (which is pretty much a text editor with code folding and a run button).

---

### Post by Wovaki on 2009-01-30
What does the Run button do.

And how do a I compile a python file (???.py???) into an executable file?

Thanks

---

### Post by jimi_hendrix on 2009-01-30
> **Wovaki said:**
> What does the Run button do.

run interperates your code i believe (never used idle)

> 
And how do a I compile a python file (???.py???) into an executable file?

Thanks

you dont on linux...on windows theres py2exe i believe

---

### Post by Wovaki on 2009-01-30
Ok I tried Geany, and I can execute the code, but when I compile it to a .pyc I cannot run it, it says there is no file to run it or something like that.

This is mainly what I meant for something simple, I liked bing able to write, run, and compile everything in one place :/

---

### Post by snova on 2009-01-30
> **Wovaki said:**
> When I run IDLE, a window pops up called "Python Shell"
When I type in print "Hello World!" It just says Hello World! on a new line in "Python Shell"

Exactly. It took your string, evaluated it, and... the result of evaluating a string is a string. So it printed the result back out. :)

As to what the interpreter does, it runs your code. Python is not a compiled language.

There are a few tools to compile Python for Windows, I think, but I'm not sure how many of these work on Linux- if any.

---

### Post by snova on 2009-01-30
> **Wovaki said:**
> Ok I tried Geany, and I can execute the code, but when I compile it to a .pyc I cannot run it, it says there is no file to run it or something like that.

You just discovered the trick of the thing- .pyc files are bytecode. Most of the time you'll never deal with these- they're transparently created by the interpreter to speed up loading. They are *not* compiled code.

> This is mainly what I meant for something simple, I liked bing able to write, run, and compile everything in one place :/

There's an extra step in there. ;)

---

### Post by Wovaki on 2009-01-30
Ok, so is Java a "compilation" language?

---

### Post by jimi_hendrix on 2009-01-30
kinda

it compiles into bytecode but this can be run on any computer that has java installed (just about every computer, every popular OS)

---

### Post by eragon100 on 2009-01-30
> **Wovaki said:**
> Ok, I seem to be getting more comments about Python.

So, I just downloaded IDLE for Python and a PDF Tutorial from one of the links on the first page of this thread.

Is there anything else that I should have, or know before starting to learn Python. It would be nice to be able to do most of my learning offline if possible, since I usually don't have a lot of internet time.

IDLE sucks, big time imho. Just download "spe" (Stani's Python Editor") it's very good and it's in add/remove applications ;)

---

### Post by jimi_hendrix on 2009-01-30
or just use vim :)

*ducks*

---

### Post by Wovaki on 2009-01-30
Well I would like something that compiles or whatever, because if I make a app that I use, I don't want to have to use another program to run it all the time, I would like to be able to just click a executable file or something

---

### Post by Wovaki on 2009-01-30
What is Vim?

---

### Post by snova on 2009-01-30
> **Wovaki said:**
> What is Vim?

An editor. And not a particularly friendly one...

---

### Post by hanniph on 2009-01-30
> **snova said:**
> An editor. And not a particularly friendly one...

But if you spend some time on it, you won't regret it :)

---

### Post by The Cog on 2009-01-30
For running python files, there are two techniques.

Firstly, you can invoke the interpreter directly like this:
**python myprog.py**

Secondly, you can make the python code file executable. This involves adding this line as the first line of the source file:
**#! /usr/bin/python**
and then marking the file executable like this:
**chmod +x myprog.py**

In both cases, the .py extension is optional. In the second case, you can launch the program by goving its name at a command prompt or by double-clicking it in nautilus.

In geany, the compile button really just does a module import to make the interpreter do a test for syntax errors.

---

### Post by jimi_hendrix on 2009-01-30
learning vim is regarded as a rite of passage in the *nix world...basically its an editor where you never need to take your hands off the keyboard if you know it well

---

### Post by jimi_hendrix on 2009-01-30
i believe (dont kill me) but .Net stuff (including VB) compiles to bytecode similarly to java...only its only as portable as MS wants

---

### Post by directhex on 2009-01-30
> **jimi_hendrix said:**
> i believe (dont kill me) but .Net stuff (including VB) compiles to bytecode similarly to java...only its only as portable as MS wants

It's as portable as anyone implementing the bytecode specification from ECMA 335 wants it to be

I write apps on i386 Ubuntu, and test them on Itanium Suse or AMD64 Ubuntu without so much as a recompile

---

### Post by Kilon on 2009-01-30
> **Wovaki said:**
> Well I would like something that compiles or whatever, because if I make a app that I use, I don't want to have to use another program to run it all the time, I would like to be able to just click a executable file or something

Peculiarly enough the way python behaves in ubuntu is abit diffirent to how it behaves in windows. For example in windows each time you double click a python file it just executes like any other programm. This does not happen in ubuntu because the os is not set up to behave like this. But it is not difficult to do. All you have to do is tell ubuntu that each time you double click a python file it should execute.  

Maybe someone here may show us how this is done , cause I am interested too.

---

### Post by directhex on 2009-01-30
> **Wovaki said:**
> I have just recently installed Ubuntu on my system, on Windows I have been working with Visual Basic.NET for almost a year, and I was wondering what would be a good programming language to learn for Ubuntu.

```
jms@destiny:/tmp$ cat >>hello.vb <<EOF
> Imports System
> 
> Public Module modmain
>    Sub Main()
>      Console.WriteLine ("Hello World using Visual Basic!")
>    End Sub
> End Module
> EOF
jms@destiny:/tmp$ vbnc hello.vb 
 version  (Mono 2.0 - r)



Assembly 'hello, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' saved successfully to '/tmp/hello.exe'.
Compilation successful
Compilation took 00:00:01.9543300
jms@destiny:/tmp$ mono hello.exe 
Hello World using Visual Basic!
jms@destiny:/tmp$ 
```

Any language you want. Including the one you already have experience with

By all means, learn something new like Java or Python or C++, but don't for a moment think that you're forced down that route

---

### Post by bruce89 on 2009-01-30
> **Kilon said:**
> Peculiarly enough the way python behaves in ubuntu is abit diffirent to how it behaves in windows. For example in windows each time you double click a python file it just executes like any other programm. This does not happen in ubuntu because the os is not set up to behave like this. But it is not difficult to do. All you have to do is tell ubuntu that each time you double click a python file it should execute.  

Maybe someone here may show us how this is done , cause I am interested too.

Shove a shebang in it, then set it executable.

```

#!/usr/bin/env python

```

---

### Post by Kilon on 2009-01-30
> **directhex said:**
> 
By all means, learn something new like Java or Python or C++, but don't for a moment think that you're forced down that route

I have not seen the OP post about VB .NET. If you learned quite alot from VB .NET then it will be better to stick with the .NET and maybe move to C#. You will be more familiar with it than python. Because you will be using the same library. Only the syntax is a bit diffirent.

---

### Post by HotCupOfJava on 2009-01-30
Yeah, I learned vim then used it to code my own editor! I wanted to be able to browse for files and then have the editor automatically complete quotes, brackets, braces and parenthesis for me. I could use an IDE for all of that but I wanted something much more lightweight.

---

### Post by Kilon on 2009-01-30
> **bruce89 said:**
> Shove a shebang in it, then set it executable.

```

#!/usr/bin/env python

```
 will i be asking too much to show me , in more detail the solution ?

Thanks.

---

### Post by jimi_hendrix on 2009-01-30
> **HotCupOfJava said:**
> Yeah, I learned vim then used it to code my own editor! I wanted to be able to browse for files and then have the editor automatically complete quotes, brackets, braces and parenthesis for me. I could use an IDE for all of that but I wanted something much more lightweight.

you could do the automatic stuff in vim

---

### Post by jimi_hendrix on 2009-01-30
> **Kilon said:**
> I have not seen the OP post about VB .NET. If you learned quite alot from VB .NET then it will be better to stick with the .NET and maybe move to C#. You will be more familiar with it than python. Because you will be using the same library. Only the syntax is a bit diffirent.

1) he said VB in OP

2) C# has nothing in common with VB other than they can use .Net libraries

---

### Post by Sorivenul on 2009-01-30
> **jimi_hendrix said:**
> then i have to be absolutely insane because i normally mess around in C++ :)
You may be, but that is your choice, based on your opinion. No matter how crazy it is... ;) 

I am starting to enjoy Java more now that I'm not having to use it for coursework and can apply it as I see fit, but would not suggest it for the "hobbyist" programmer, again my opinion. C++ is pretty much the same story - disliked it for coursework, when applied myself it is much more enjoyable, but still not something I would have considered jumping into myself as my first language in the Linux world.

You, jimi_hendrix, are an anomaly. And I applaud you for it. =D>

---

### Post by jimi_hendrix on 2009-01-30
> **Sorivenul said:**
> You, jimi_hendrix, are an anomaly. And I applaud you for it. =D>

i also enjoy messing around with ASM and if there were better resources i would be debugging my own OS right now

---

### Post by Sorivenul on 2009-01-30
> **Kilon said:**
> will i be asking too much to show me , in more detail the solution ?

Note: I should have multi-quoted, sorry.

Add the shebang (#!/usr/bin/env python) at the beginning of the Python file, run a chmod +x on the Python file or just select the checkbox to enable it to run as an executable if you use a GUI method. Then double-click. Done. Not much more detail needed. 

As a list:
1.) Add #!/usr/bin/env python to the top of the Python file
2.) chmod +x /path/to/yourpyfile.py

Cheers!

---

### Post by nvteighen on 2009-01-31
> **Wovaki said:**
> Well I would like something that compiles or whatever, because if I make a app that I use, I don't want to have to use another program to run it all the time, I would like to be able to just click a executable file or something

In GNU/Linux (and I guess in the UNIX world too), using scripts that run on top of another application is quite common. If it's not Python, it's Perl or some shell script... You'd be surprised how much stuff in the OS is implemented that way.

Actually, the Python situation is almost the same as the VB.NET's: none of both compiles into native machine code, so you need something that runs that code. In the .NET case, it's the .NET Framework; in Java, the JVM; in Python, the interpreter; in Perl, perl (with lowercase); with Lisp, the corresponding Lisp VM, etc. In Windows, the difference is that the .NET interpreter starts without you noticing it.

So, unless you go for Assembly, C or C++, you never get a native executable... and even then, you'll need the aid of the corresponding Standard Library to make the thing work. In the end, the only really standalone application in a computer is the bootloader.

---

### Post by Kilon on 2009-01-31
> **Sorivenul said:**
> Note: I should have multi-quoted, sorry.

Add the shebang (#!/usr/bin/env python) at the beginning of the Python file, run a chmod +x on the Python file or just select the checkbox to enable it to run as an executable if you use a GUI method. Then double-click. Done. Not much more detail needed. 

As a list:
1.) Add #!/usr/bin/env python to the top of the Python file
2.) chmod +x /path/to/yourpyfile.py

Cheers!

I think you are amazing , I think you are a GOD ... I am going now to build you a church and worship you :D

---

### Post by jimi_hendrix on 2009-01-31
> **Kilon said:**
> I think you are amazing , I think you are a GOD ... I am going now to build you a church and worship you :D

you didnt know about the shebang?
who tought you python?
also whats the dif between using /user/bin/env python and /usr/bin/python (what i normally do)

---

### Post by directhex on 2009-01-31
> **nvteighen said:**
> In Windows, the difference is that the .NET interpreter starts without you noticing it.

You can get the same results on Linux if you like

```
jms@destiny:/tmp$ dpkg -l binfmt-support
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  binfmt-support 1.2.11         Support for extra binary formats
jms@destiny:/tmp$ ./hello.exe 
Hello, World!
```

---

### Post by nvteighen on 2009-01-31
> **jimi_hendrix said:**
> 
also whats the dif between using /user/bin/env python and /usr/bin/python (what i normally do)

The difference is that /usr/bin/env python allows this behaivor in systems where python is installed elsewhere. What it does is to check the location of Python looking at the environment variables.

> **eye208 said:**
> C.

Recently I heard someone say: "C is the rock upon which the church of IT is built."

And it's true. The vast majority of applications and libraries for Linux is written in C. Linux itself is written in C. C remains the most popular programming language, especially for open source projects. And by "popular" I mean: the most frequently _used_ one. You may hear lots of talk about languages such as Python for sure, but talk is not code. Check out your favorite applications. Which language was used to build them? There's a 95% chance that it wasn't Python.


Of course: C is the best language for creating software that is meant to set up a computer to do something. But that's not programming, it's just a part of what programming is! Programming is to describe some knowledge (usually a process) that then you simulate in a computer. In other words, what we usually call a "system utility" or an "application" is to describe a computer-specific issue and then run it in a computer... Yeah, C is great for that and so we have the Linux kernel, the GNU tools, etc.

But what if I want to describe something that's not computer-specific? C then becomes an obstacle in most of the times because it starts too low in the abstraction continuum... Yes, there are libraries, but those libraries don't transform the language's pilars, so you still are using pointers (an implementation detail) to heck around a lot of stuff... The result is a weird soup of low-level and high-level code that would be much easier to write/read in another languages.

The application's argument is a bit tricky, IMO. Yeah, the 95% of the applications you used is written in C (or C++) because those are meant to be computer-related... But what about the webpages you look? There you have Javascript, Java, PHP, Perl, Python, ASP.NET, etc. and you can't say that's not important and those are also computer-specific stuff.

---

### Post by Sorivenul on 2009-01-31
> **Kilon said:**
> I think you are amazing , I think you are a GOD ... I am going now to build you a church and worship you :D
I most definitely am not, and you certainly don't have to, but the sentiment is sweet. On that note, a nice, ranch-style house in northern Arizona, US would be preferred to a church. ;)

---

### Post by bruce89 on 2009-01-31
> **Kilon said:**
> will i be asking too much to show me , in more detail the solution ?

Shove the shebang in the first line of a Python script.

```
chmod +x script.py
```

Done.

> **Sorivenul said:**
> Note: I should have multi-quoted, sorry.

Add the shebang (#!/usr/bin/env python) at the beginning of the Python file, run a chmod +x on the Python file or just select the checkbox to enable it to run as an executable if you use a GUI method. Then double-click. Done. Not much more detail needed. 

As a list:
1.) Add #!/usr/bin/env python to the top of the Python file
2.) chmod +x /path/to/yourpyfile.py

Cheers!

Oops.

> **eye208 said:**
> It's all there, even the most obscure stuff that you have never heard of before. For example, just recently I had to deal with SSA subtitle files, and guess what, there is already a C library for rendering them. None of that high level language fluff (Python etc.) would have helped me out there. If you want to get things done in Linux, you have to learn C. And then, optionally, C++.


As [http://www.theregister.co.uk/2009/01/21/open_source_projects_08/](http://www.theregister.co.uk/2009/01/21/open_source_projects_08/) suggests, C was used by almost half (47%) of all new FOSS projects last year. Java had a resurgence (28%), and Python wasn't first or even second in scripting languages.

---

### Post by slavik on 2009-02-01
Was the OP's question ever answered? If so move on. If you are not intending on answering the OP's questions (whatever they may be) move on.

---

### Post by Wovaki on 2009-02-02
Well I haven't had a chance to really look at any programming stuff in detail, but I have the Monodevelop program, and I was playing around with it, but I think I would rather learn something that works better on Linux.

I'm at school right now, so I'm limited in what I can do, but I was looking at Java a little bit.

Mainly I want to be able to make GUI app's, and right now its mainly just for fun.

Right now, since I'm not very advanced I was hoping for something fairly simple, in terms of compilation and stuff. I'm used to Microsoft's Visual Studio for VB.NET. I was hoping for something where I can write my code, click a button, and have a executable file. I'm open to learning new things, but I only have internet at school right now, so I'm somewhat limited.

---

### Post by jimi_hendrix on 2009-02-02
> **Wovaki said:**
> I was hoping for something where I can write my code, click a button, and have a executable file. I'm open to learning new things, but I only have internet at school right now, so I'm somewhat limited.

just because it's a script doesnt mean its not executable ;)

pick an ide (geany for python for example or netbeans for java) and click away

---

### Post by Wovaki on 2009-02-03
Sorry to be bouncing back and forth between languages, but hopefully soon I can find one that I like.

What do you guys think would be better to learn, C or C++?

Thanks

---

### Post by directhex on 2009-02-03
> **Wovaki said:**
> Sorry to be bouncing back and forth between languages, but hopefully soon I can find one that I like.

What do you guys think would be better to learn, C or C++?

Thanks

To what end? C++ is "better" in that it offers OO, both share the same upsides & downsides. C is common for GTK aps, C++ for Qt apps. Both will force you to spend a lot of time mangling your memory by hand.

---

### Post by Kilon on 2009-02-03
> **directhex said:**
> To what end? C++ is "better" in that it offers OO, both share the same upsides & downsides. C is common for GTK aps, C++ for Qt apps. Both will force you to spend a lot of time mangling your memory by hand.

100% agree with this statement

---

### Post by Wovaki on 2009-02-04
Alright...maybe I should just wait and learn Java when I go to school.

Thanks

---

