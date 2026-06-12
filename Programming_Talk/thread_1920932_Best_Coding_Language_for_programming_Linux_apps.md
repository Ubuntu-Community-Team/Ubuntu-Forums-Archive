---
title: "Best Coding Language for programming Linux apps"
date: 2012-02-05
forum: Programming Talk
---

### Post by pgroves95 on 2012-02-05
I'm in the process of teaching myself C# using a *For Dummies* book. As far as linux is concerned, am I on the right track? Is there a simpler language I should learn first? I'm completely green, so recommendations, tips, software, any and all advice is helpful! 

I want to be able to write my own terminal-based software, if that helps you in your response.

---

### Post by lisati on 2012-02-05
*Thread moved to **Programming Talk**.*

---

### Post by korgoth28 on 2012-02-05
It completely depends on what you want to do. I've never had a reason to learn C#, all I know about it is that it was made by Microsoft.

C++ is great if you want speed. I often use it with curses to make Dwarf Fortress like games (that is, they only use ascii art in the terminal. This is also how you would make something like vi). You can do just about anything you want with C/C++. Literally anything if you do some assembly and intermediate language stuff to what the compiler spits out. It's appropriate for 2D interfaces with libraries like SDL, or 3D using something like Ogre.

Python is great if you want an easy language, or if you want to make 3D games using Blender. It's a great language both for learning about programming and for making software. If you want to automate system stuff, do complicated operations on lots of text files, etc., you should learn bash scripting.

---

### Post by r-senior on 2012-02-05
The most common programming languages for Ubuntu and GNU/Linux generally are C and Python. Both are good general purpose languages for terminal-based software. C lends itself better to low-level "system" programming. Python is a higher-level object-oriented language and coding can be easier and more productive.

I'd suggest you try both of these two and also learn some basic Bash scripting, which often comes in handy.

---

### Post by pgroves95 on 2012-02-05
Much appreciated! Your insight is quite helpful, all of you.

---

### Post by ve4cib on 2012-02-06
I'll also mention that C++ gets some pretty heavy use as well.  It's a little bit more flexible than C IMO (mainly it lets you program with classes, which can be a huge time-saver for certain types of program), but it also offers you that same low-level access that C has.

C# does get used for some Linux programs.  Mono, the open-source version of Microsoft's .NET framework, is reasonably stable, and gets used in programs like Gnome-Do and Banshee.  So if you want to stick with C# you can.  It's nowhere near as common in the Linux world as Python, C, or C++, but it's out there.

If you're very comfortable with one language (and its libraries) then you might choose to use that language for most tasks, regardless of what language the rest of the world might consider "best-suited" for the task.

If you're writing GUI application then C++, Python, or C# might be the best bets.  If it's some low-level kernel module, C is probably the way to go.

Ultimately the choice of "what's the best language" depends more on you, the programmer, and what the program you're writing is.

---

### Post by doobrie on 2012-02-06
If you're only interested in console apps, then I'd recommend starting with C.

If you want to do any GUI apps, then C++ may be a better choice, but you can always learn C++ after you've learnt C as the basics are the same.

C# is typically used on Microsoft systems, but again has its roots in C so if you learn C, then you should be able to pick up C# easily.  On the other hand, if you already know C# you may find that C seems a bit lacking in certain features.

---

### Post by Mosome on 2012-02-06
Codeblocks is also a great IDE for C++ programming related projects and easy to setup.  It's also compatible on both Linux and Windows so your programs will be portable.  You'll want to download and make sure you have a installed g++ or gcc, the GNU versions.  Everything else can be done in BASH, which is fairly simple and efficient.

---

### Post by directhex on 2012-02-06
I'm a big fan of C#, it's definitely my language of choice. The [MonoDevelop](apt:monodevelop) IDE gives you what you need to develop full GUI apps with C# like Tomboy or Banshee - or games like Spacechem

---

### Post by painejake on 2012-02-07
I also personally prefer C#, however that's my preference coming from Windows using .NET and having a large knowledge of different library's that are available having done the research already :)

---

### Post by doobrie on 2012-02-07
I like C# and its a fairly easy language to get to grips with.  There's plenty of documentation about for the starter developer also.

Having said that though, my personal preference for Linux development is C++ and GTK.

---

### Post by ibrahimtawbe on 2012-02-07
as mentioned above C and Python 
I think you should go with Python 

[LIST]
[*]It's easier for beginners
[*]You can use it as a scripting language
[*]You can also do GUI programs
[*]You can write some components of your Python program with C
[/LIST]

---

### Post by trent.josephsen on 2012-02-07
Well, lest the OP see consensus, I don't like C#, both because it's a proprietary Microsoft language and because it's just generally ugly like the Java clone it is.  (Mind you, I have very little practical experience with C#, standard disclaimer applies.)

My main criticism of Java, which I imagine applies just as well to C#, is that it's an enormous language and you need to know a lot of stuff to use it properly -- a lot of stuff you won't know as a beginner, and you won't understand the reasons for all of it until you've been programming for probably at least a few years.  Even C, in my not so humble opinion, would be better for beginners, and I don't recommend C because it's kind of overwhelming itself.  It's why you see so many recommendations for Python in threads like this.

---

### Post by satanselbow on 2012-02-07
> **trent.josephsen said:**
> It's why you see so many recommendations for Python in threads like this.

Yeah. Kinda surprised there isn't a little more love for python here myself - given that GTK/QT + python is the current ubuntu developer mantra :confused:

Likewise there is little love for Mono based apps - wasn't Mono why Banshee got bumped as default player a while back...

---

### Post by doobrie on 2012-02-07
> **trent.josephsen said:**
> Well, lest the OP see consensus, I don't like C#, both because it's a proprietary Microsoft language and because it's just generally ugly like the Java clone it is.  (Mind you, I have very little practical experience with C#, standard disclaimer applies.)

My main criticism of Java, which I imagine applies just as well to C#, is that it's an enormous language and you need to know a lot of stuff to use it properly -- a lot of stuff you won't know as a beginner, and you won't understand the reasons for all of it until you've been programming for probably at least a few years.  Even C, in my not so humble opinion, would be better for beginners, and I don't recommend C because it's kind of overwhelming itself.  It's why you see so many recommendations for Python in threads like this.
I feel as though I should defend Java (and to a lesser extent C#) here even though I don't believe its the best language for Linux devs. ;)

I don't believe the Java language is that much bigger than C++.  One of the main benefits of Java is that you don't need to worry about memory management - you can't say that for C++, which immediately makes Java much better for beginners.

Sure, there's a whole heap of different APIs for doing things in Java, but there again, what language doesn't have these.  I wouldn't say that writing a C++/GTK app was easier than a Java/Swing app, most probably the other way around.  You learn what you need to learn.  For example Java has plenty of support for XML handling, but the average desktop coder probably isn't going to need this and probably won't learn it.

The best coding language for Linux apps is not necessarily the best language for a beginner.  From my point of view the best language is C++, but I'll admit that I'm a novice with Python and that may well be better for some people.

---

### Post by Simian Man on 2012-02-07
> **ve4cib said:**
> If you're writing GUI application then C++, Python, or C# might be the best bets.  If it's some low-level kernel module, C is probably the way to go.
I agree mostly with this, but would definitely not include C++ as a good language for GUI development.  The rigidity of C++ along with the burden of memory allocation will make your job harder than it needs to be.  Also GUI apps rarely tax your CPU at all so the speed of C++ will be a non-factor.


> **doobrie said:**
> If you're only interested in console apps, then I'd recommend starting with C.

If you want to do any GUI apps, then C++ may be a better choice, but you can always learn C++ after you've learnt C as the basics are the same.
C is a good choice for console apps that require a great deal of performance, but these are actually very rare.  Something like Python is best for most console apps - especially for a beginner.  And, again, C++ is not a good choice for GUI apps at all.


> **trent.josephsen said:**
> Well, lest the OP see consensus, I don't like C#, both because it's a proprietary Microsoft language
Don't create a false impression.  C# was created by Microsoft, but is is an open standard and the Mono implementation is open source, mature and very good.

> **trent.josephsen said:**
> My main criticism of Java, which I imagine applies just as well to C#, is that it's an enormous language and you need to know a lot of stuff to use it properly -- a lot of stuff you won't know as a beginner, and you won't understand the reasons for all of it until you've been programming for probably at least a few years.  Even C, in my not so humble opinion, would be better for beginners, and I don't recommend C because it's kind of overwhelming itself.  It's why you see so many recommendations for Python in threads like this.
Actually Java is one of the simplest languages out there.  It gives you basically one programming construct - the class.  It doesn't have first-class functions, pointers, multiple inheritance, operator overloading, unsigned numbers, stack types, multiple dispatch, delegates, nested functions, free functions, tuples, pattern matching...I could go on.

If you think Java is "an enormous language", then you know nothing about programming languages.

To the OP, I would recommend sticking with C#.  You already started it, already have a book, and it's quite a decent language.  It even has some features that I miss in Java such as tuples, operator overloading, unsigned numbers, and stack types.  There is also the Monodevelop IDE and quite a few good libraries on Linux.

Happy coding.

---

### Post by doobrie on 2012-02-07
> **Simian Man said:**
> To the OP, I would recommend sticking with C#.  You already started it, already have a book, and it's quite a decent language

Very sensible approach.

---

### Post by ve4cib on 2012-02-07
> **trent.josephsen said:**
> Well, lest the OP see consensus, I don't like C#, both because it's a proprietary Microsoft language and because it's just generally ugly like the Java clone it is.  (Mind you, I have very little practical experience with C#, standard disclaimer applies.)

My main criticism of Java, which I imagine applies just as well to C#, is that it's an enormous language and you need to know a lot of stuff to use it properly -- a lot of stuff you won't know as a beginner, and you won't understand the reasons for all of it until you've been programming for probably at least a few years.  Even C, in my not so humble opinion, would be better for beginners, and I don't recommend C because it's kind of overwhelming itself.  It's why you see so many recommendations for Python in threads like this.

A Java developer was once quoted as saying "C# is what Java would be if Sun had the budget for it."  (Or words to that effect; I can't find the exact quote unfortunately.)

C#, the language, is not proprietary.  Portions of the .NET framework on which it tends to rely are, but the language itself is not.  And -- at the severe risk of running into a "Mono is evil!" "No, it isn't!" debate -- those few portions of the .NET framework that are at issue have been licensed for free use with Mono, so the proprietary-or-not debate is really a non-issue.

Personally I think C# is a lot cleaner than Java, and has some really nice features I wish Java had.  Things like iterators for for-loops:

C#:
```

String[] someStrings = { /*stuff here*/ };
for(String s in someStrings)
    doSomethingWithEachString(s);
```

versus Java:
```

String[] someStrings = { /*stuff here*/ };
for(int i=0; i<someStrings.length; i++)
    doSomethingWithEachString(someStrings[i]);
```

It's a minor difference, but the C# version is more intuitive to me.

There's also the nice feature of Properties in C#, instead of explicit Get/Set methods in Java:

C#
```
class SomeExampleClass
{
    private int mustBeEven;

    public int Value
    {
        get {return mustBeEven;}
        set {
            if(value % 2 == 0)
                mustBeEven = value;
        }
    }
}

...

SomeExampleClass foo = new SomeExampleClass(2);
Print(foo.Value);
foo.Value = 1;
Print(foo.Value);
foo.Value = 4;
Print(foo.Value);

```

Java:
```
class SomeExampleClass
{
    private int mustBeEven;

    public int getValue
    {
        return mustBeEven;
    }

    public void setValue(int v)
    {
        if(v % 2 == 0)
            mustBeEven = v;
    }
}

...

SomeExampleClass foo = new SomeExampleClass(2);
print(foo.getValue());
foo.setValue(1);
print(foo.getValue());
foo.setValue(4);
print(foo.getValue());

```

Anyway, that's just my take on the C# vs Java.  Java has its uses (e.g. Android development), but given a choice I would prefer to work with C#.

> I agree mostly with this, but would definitely not include C++ as a good language for GUI development. The rigidity of C++ along with the burden of memory allocation will make your job harder than it needs to be. Also GUI apps rarely tax your CPU at all so the speed of C++ will be a non-factor.

C++ with QtCreator is pretty nice for doing GUI programs.  Most of the really hard/annoying parts of laying out the GUI is done via a Visual Studio-style GUI builder.  Yes, there's the memory management issue to consider.  And that is a major factor for a lot of people.  Personally, I've done enough C++ that I'm comfortable with it, which is why I included it as a possible candidate for GUI applications.  It wouldn't be my first recommendation to most people, but it is a viable option that deserves mentioning.

Possibly the biggest advantage of using C++ for a GUI program is that you have very easy access to any C or C++ library you need.  And there are thousands (millions?) of those.  Yes, many of them have bindings for other languages, but some don't.  Or the other language bindings aren't complete, or have performance issues.  Something to consider at the very least, depending on what kind of program you're creating.

---

### Post by r-senior on 2012-02-07
> **ve4cib said:**
> Personally I think C# is a lot cleaner than Java, and has some really nice features I wish Java had.  Things like iterators for for-loops:

While I agree generally with your assessment, Java has had the same style of fast enumeration since 1.5. This works with primitive arrays and collections:

```
String[] someStrings = { /*stuff here*/ };
for(String s : someStrings)
    doSomethingWithEachString(s);
```

---

### Post by doobrie on 2012-02-07
The properties feature of C# is nice, but its not something that's overly important to me.  I believe it's been talked about for future version of Java, so, someday it'll be there also.

---

### Post by painejake on 2012-02-07
This thread might all be a lot for OP to take in all at once so to hopefully simplify it.

Java, C# and Python all high level with GC so you don't have to worry about memory leaks as such.

C and C++ while being good to know, do have a larger learning curve, whiles rewarding in the long run can be made simpler by learning a high level language first and understanding the principles of programming and moving on-wards and up-wards.

I would suggest investing in a beginners C# book (as it's what you've already started playing around with) and giving it a crack and working though it.

No matter which you choose once you have one under your belt though it will become a lot simpler to move to another in the future. 

:)

---

### Post by Rcihard Arnold on 2012-02-07
> **r-senior said:**
> The most common programming languages for Ubuntu and GNU/Linux generally are C and Python. Both are good general purpose languages for terminal-based software. C lends itself better to low-level "system" programming. Python is a higher-level object-oriented language and coding can be easier and more productive.

I'd suggest you try both of these two and also learn some basic Bash scripting, which often comes in handy.

Personally, i think C, although historically valuable, is just that... Old history. My suggestion is to learn C++ since it is widely supported by compilers and is relatively easy as far as syntax and code structure go...

---

### Post by trent.josephsen on 2012-02-07
Okay, I'm going to defend one point and apologize for one point, then I'm going to let this die.

[QUOTE=Simian Man]If you think Java is "an enormous language", then you know nothing about programming languages.[/QUOTE]

Okay, my mistake.  The Java *language* is, as you say, of quite reasonable size.  It's probably... oh, 1.5x to twice as "big" as C, syntactically speaking.  But much like C, you can't really claim to write Java unless you're familiar with at least a subset of the standard library.  And very unlike C, the part of Java's standard library that you need to know to not be totally useless as a programmer is pretty darn big.

> Don't create a false impression. C# was created by Microsoft, but is is an open standard and the Mono implementation is open source, mature and very good.
My mistake again.  I'm remembering when Mono was incomplete and unstable, wasn't aware how much had changed.

---

### Post by ve4cib on 2012-02-07
> **Rcihard Arnold said:**
> Personally, i think C, although historically valuable, is just that... Old history. My suggestion is to learn C++ since it is widely supported by compilers and is relatively easy as far as syntax and code structure go...

C is surprisingly important for a lot of things.  If you ever work with embedded systems you can't get away from it.  The Linux kernel is written in C.  And C has been popular enough over the years that it has enormous quantities of third-party libraries that will do pretty much anything you could want to do from high-performance mathematics to graphics to neural networks to file i/o.  And the beauty is that you can use those C libraries *inside* C++ programs, provided you know how to write and use C code.

I would not suggest C as a starting language for anyone, but it is good to learn at some point because if you do enough programming you will run into it eventually.

---

### Post by Simian Man on 2012-02-07
> **ve4cib said:**
> C++ with QtCreator is pretty nice for doing GUI programs.  Most of the really hard/annoying parts of laying out the GUI is done via a Visual Studio-style GUI builder.  Yes, there's the memory management issue to consider.  And that is a major factor for a lot of people.  Personally, I've done enough C++ that I'm comfortable with it, which is why I included it as a possible candidate for GUI applications.  It wouldn't be my first recommendation to most people, but it is a viable option that deserves mentioning.
You're right that C++ has been made to be pretty decent for GUIs by good tools, and there are often other advantages such as integration with other libraries or code bases.  Still if I didn't need to choose C++ for one of those reasons, I'd much rather do Python or C# for GUI work.

> **trent.josephsen said:**
> Okay, my mistake.  The Java *language* is, as you say, of quite reasonable size.  It's probably... oh, 1.5x to twice as "big" as C, syntactically speaking.  But much like C, you can't really claim to write Java unless you're familiar with at least a subset of the standard library.  And very unlike C, the part of Java's standard library that you need to know to not be totally useless as a programmer is pretty darn big.
Well the thing is that to write useful C programs, you need to use the standard library, plus a bunch of other libraries for the domain you're working with.  If you're writing network code, you need BSD sockets, if you're doing database stuff you need a database library, if you need a GUI you learn GTK+.  If you need threads, you have to use pthreads, and on and on.  You also need a library (or to roll your own) for any data structures other than arrays.

To write useful programs in C, you need to learn at least as much as you would for Java.  Worse the documentation for the libraries you'll need is all separate and they won't follow the same conventions.  Likewise to write toy programs in Java, you don't need to learn more than you would for C.

However, I don't personally like to use either C or Java because neither gives you a very good set of abstractions.  Don't mistake me for a Java fan :).

---

### Post by ve4cib on 2012-02-07
> **Simian Man said:**
> You're right that C++ has been made to be pretty decent for GUIs by good tools, and there are often other advantages such as integration with other libraries or code bases.  Still if I didn't need to choose C++ for one of those reasons, I'd much rather do Python or C# for GUI work.

Same here.  I think I've written all of 2 GUI programs in C++, and one of them was cross-compiled for Maemo.  Most of the GUI programs I've done have been in C# (+GTK#), with a handful done in Python (Tk mostly).

---

### Post by Repgahroll on 2012-02-07
Well, imho, the best path one can take begins with Python. You learn the basics, get into OOP, and most importantly, it's traditional, fully documented, has lots of libraries you can use, and last but not least, there are plenty free top quality tools for debugging and coding. The fact is that the best platform for Python programming is Linux.

The problem with C++ is that it's very hard to program in Linux, if you're a beginner, it's kinda okay, because you don't need advanced tools, etc.. However, when it comes to professional programming, the productivity is bad.

For C++ programming, the best environment for productivity is by far the Microsoft's one. It's hard to admit, and most Linux users will never, but MSVC++ -plus those assistance plugins and debugger- is much better than any other C++ programming environment.

Linux really needs some C++ development tool as seen on Windows. It's a pity it doesn't have, and the ones it has are all evolving slowly, and always some steps behind MS. Examples are NetBeans, although slow, it has some quite neat features, the development seems to have stalled some time ago though; Eclipse also has some initial features, nothing advanced at all; Some minor IDEs like QtCreator, C::B, CodeLite, etc. also have some features.

The problem is that people are always reinventing the wheel. If they joined forces to make a single decent C++ IDE for Linux, instead of making dozens of useless ones, they would have something significant already.

Not to tell that GCC G++ is lagging behind the competition, and GDB has some genial features but doesn't have the most important things to actually help the programmer.

So, if you want to learn a language to become a "pro", learn Python, in a couple of years you'll be able to write an entire program with GUI and database without a single testrun.

If you want to become a C++ pro however, you will need to either ignore that the tool you're using is obsolete, or change the platform. That's why I'm not euphoric about C++ programming in Linux, cause I always want to use the best tool available for production, and this tool is not available for Linux in case of C++. :(

---

### Post by JDShu on 2012-02-08
> **Repgahroll said:**
> 
Not to tell that GCC G++ is lagging behind the competition, and GDB has some genial features but doesn't have the most important things to actually help the programmer.


Doesn't have the most important things to help a programmer? GDB has been instrumental in helping me understand massive code bases.

---

### Post by ve4cib on 2012-02-08
> **Repgahroll said:**
> The problem with C++ is that it's very hard to program in Linux, if you're a beginner, it's kinda okay, because you don't need advanced tools, etc.. However, when it comes to professional programming, the productivity is bad.

I'm doing my master's in CS and spend the majority of every day writing C++ code for Linux.  I don't know if it gets much more "advanced" than that (well, maybe PhD level research...).  What are these "advanced tools" of which you speak?  Debuggers?  Intellisense?  Please, enlighten me as to what I have been missing.

> For C++ programming, the best environment for productivity is by far the Microsoft's one. It's hard to admit, and most Linux users will never, but MSVC++ -plus those assistance plugins and debugger- is much better than any other C++ programming environment.

Really?  I've only used MSVC++ a few times, but I never found it terribly good.  It kept throwing cryptic errors at me and took me far longer to debug anything that it ever did on a Linux system.

Microsoft dev tools for C# and VB (namely Visual Studio) are fantastic!  But I'm definitely not sold on their C++ tools.  I think I'd rather use GCC or G++ and Cygwin than fight with MSVC++ again.

> Linux really needs some C++ development tool as seen on Windows. It's a pity it doesn't have, and the ones it has are all evolving slowly, and always some steps behind MS. Examples are NetBeans, although slow, it has some quite neat features, the development seems to have stalled some time ago though; Eclipse also has some initial features, nothing advanced at all; Some minor IDEs like QtCreator, C::B, CodeLite, etc. also have some features.

The problem is that people are always reinventing the wheel. If they joined forces to make a single decent C++ IDE for Linux, instead of making dozens of useless ones, they would have something significant already.

I half agree with you there.  Having Linux dev tools like Visual Studio for *any* language would be great.  But to call QtCreator, CodeBlocks, Eclipse, and Netbeans "useless" is a pretty gross exaggeration.  You are aware that Eclipse is used heavily in the professional world for development?  No, the Linux IDEs are not as polished as VS, but they're pretty good and get the job done very well.

> Not to tell that GCC G++ is lagging behind the competition, and GDB has some genial features but doesn't have the most important things to actually help the programmer.

Again, how about some specifics?  What exactly are GCC, G++, and GDB missing?  What are these "most important things to actually help a programmer?"  You like to use hyperboles, and then you never back them up with anything.

> If you want to become a C++ pro however, you will need to either ignore that the tool you're using is obsolete, or change the platform. That's why I'm not euphoric about C++ programming in Linux, cause I always want to use the best tool available for production, and this tool is not available for Linux in case of C++. :(

Or you could learn to use the tools available (GCC is pretty much the de-facto standard C compiler -- hardly what I would call "obsolete").  C++ is a *language* not an IDE, and not a compiler.  You can learn the language using whatever tools you want.  In fact, learning C++ by using a basic text editor and a command-line compiler might teach you *more* about C++ than you would learn using a giant IDE that silently corrects your mistakes.

---

### Post by lisati on 2012-02-08
*aside*
I think I have only ever made one GUI program using C++, and note that (a) it was for Windows 98SE, (b) a significant portion of the code looked more like C than C++, (c) it was made with Borland's C++ Builder, and (d) it wasn't particularly well done. If I were to attempt a similar project these days I'd probably do it differently.
*aside ends*

---

### Post by Repgahroll on 2012-02-10
> **JDShu said:**
> Doesn't have the most important things to help a programmer? GDB has been instrumental in helping me understand massive code bases.
> **ve4cib said:**
> Again, how about some specifics?  What exactly are GCC, G++, and GDB missing?  What are these "most important things to actually help a programmer?"  You like to use hyperboles, and then you never back them up with anything.

In fact I was being exaggerated :). Some useful features that GDB doesn't have are the ability to edit the code during the execution - this is fantastic imho because it's like debugging a script, and things like showing the variables values in source, and proper code navigation (jumping to definitions, etc.) are little things that actually increase productivity in my case. The thing is totally integrated into the IDE to provide the best visual feedback. Although GDB is pretty good and have some cool features, I just don't find them that important, I think my priorities are just different. GDB is still a good competitor here, though lagging behind imho.

MS compiler generates much better binaries imho - (according to my experience) it compiles dramatically faster (kinda 3-4x), the generated binary tends to be "much" faster (like 15%) and a little bit smaller also (like 20%). So, imho it generates better binaries overall, and I think one can find plenty of benchmarks that backup my experience here.


> Really?  I've only used MSVC++ a few times, but I never found it terribly good.  It kept throwing cryptic errors at me and took me far longer to debug anything that it ever did on a Linux system.
I never found a single undecipherable error in MSVC, although I agree that GDB text feedback is better.


> I half agree with you there.  Having Linux dev tools like Visual Studio for *any* language would be great.  But to call QtCreator, CodeBlocks, Eclipse, and Netbeans "useless" is a pretty gross exaggeration.  You are aware that Eclipse is used heavily in the professional world for development?  No, the Linux IDEs are not as polished as VS, but they're pretty good and get the job done very well.
I'm aware that Eclipse is used professionally for Java development, however, I don't know a single professional that uses Eclipse CDT as its main C++ development environment.
In fact, 99% of all C++ professionals that I know uses MSVC for C++ development - there's one guy that uses Anjuta.

The most important tool Linux needs is a decent and modern C++ IDE. Forget the other languages.

I don't know C#, but once i fired up Visual Studio, looked a basic C# example (in wikipedia i think) and i managed to make a nice graphical calculator in a matter of 30 minutes. Not even in Python someone can achieve this kind of ease and productivity on Linux, first you have to choose either tkinter which is extremely simple and ugly or something like Qt which has a nice designer, then you need to learn the basics of Python itself, learn QtDesigner, design, convert, edit, if you made mistakes, have to go back and convert again. It takes at least 30+ hours to produce your first graphical calculator in Python if you have only C++/Java experience. Not to tell that the performance is like 300 times slower than C# on Windows, it may not run on other distros, because some have Python v3, some v2, almost certainly it will be necessary to install dependencies, and the list goes on.

On Windows, you just fire up MSVS, click, click, code, click, and ta-daam: You end up with a 'binary' that will look consistent and will run properly on practically every windows install, and even better, the user (in most cases) will not even know that you are a completely noob and programmed using a beginner's language.

> Or you could learn to use the tools available (GCC is pretty much the de-facto standard C compiler -- hardly what I would call "obsolete").  C++ is a *language* not an IDE, and not a compiler.  You can learn the language using whatever tools you want.  In fact, learning C++ by using a basic text editor and a command-line compiler might teach you *more* about C++ than you would learn using a giant IDE that silently corrects your mistakes.
Of course, and for learning I recommend a text editor with a good syntax highlighting (maybe basic autocompletion also).

--

On Windows, as a C++ programmer, i feel "welcome", it's like going to a place where people help you, if you made a mistake, just try again, it's simple and easy, it will help you to do everything, and I don't think the suggestions are evil, because they actually help me to code faster and better, using less brainpower :).

On Linux, it's like military school, if you don't have the basics, which are pretty high already, you don't even begin, you're not welcome, you have no friends, no one will help you, you need focus 100% of the time, because the entire thing has to be in your head, stop a minute and you will get lost. 

Even worse, Linux 'commanders' seems to be assuming that we need more advanced tools, we don't even have basic visual feedback, but we need an ultra-advanced programmable debugger, we don't have shoes to walk, but we need a spacecraft.

I'm telling you guys this is wrong! Bring the noobies! Make tools that allow people to begin producing simple programs easily, make them like the Linux, some of them will eventually become programmers and will take the tools to a higher level. I thought this is what open source was about. Now i see that it's becoming an exclusivist group of people that learned the hard way something different.


An over-exaggerated analogy:

We're visiting friends on the other side of the city, your options are:

Windows: Bicycle, Car, Bus, Airplane
Linux: You can choose one of the 100 models of square-wheel bicycles, or you can enter the space program and begin to learn how to pilot a spacecraft.

Man! Lemme use a car or a bus, lemme achieve my current objective and if I ever need to go to the moon, then I'll make a spacecraft. It's another problem.

It's like thinking about colonizing mars when we don't even live properly here on earth. It's a nonsense, you solve the problems when they comes up, not target the problems that seems to be ahead, if you can't even reach them.

--

Sorry if i sounded rude or something. I just think that the open source community is so chaotic and unorganized, it's extremely divided, a lot of capable people are just losing their time developing things that will never get any attention.

We have dozens of major distros, hundreds of forks, and thousands of "unnofficial" sub-versions, and almost every version has its own peculiarity, and it's not only a collection of softwares, any decent distro has its own scripts.

We have dozens or hundreds of options for almost everything, the problem is that their quality varies dramatically, and almost always the best one isn't good as the middle-quality proprietary option.

If there were a kind of artificial intelligent software merger, then we would have the best softwares ever, because it would merge all the 78921323 distros and make a single very user-friendly one that runs on any hardware and installs any prepacked software. Merge the 789343 office suites and make a single decent one. All the 7893213 C++ IDEs, all the Debuggers, Compilers, etc...

Sum the features of all opensource vector drawing tools, and you'll end up with a list that surpasses the best proprietary software, the difference is that it's one software, very tested thus stable, against tens of unstable and used-only-by-its-creator softwares.

--

Its a matter of Divide and Conquer: Go on Microsoft, we did you a favor and divided ourselves as an effect of our selfish behaviour. Now you just have to conquer. - [facepalm] Ouch... forget that, for a moment I forgot that you've already conquered the entire world and now is just fighting some reminiscent diehards.

---

### Post by ofnuts on 2012-02-10
> **Repgahroll said:**
> 
On Windows, you just fire up MSVS, click, click, code, click, and ta-daam: You end up with a 'binary' that will look consistent and will run properly on practically every windows install, and even better, the user (in most cases) will not even know that you are a completely noob and programmed using a beginner's language.
Working code isn't automatically good code. VS only helps producing noob code faster.

I'm currently trying to "enhance" a piece of VB written by a former project manager who was very proud of it. I'm very glad this code is only used for project management and not part of the real code.

---

### Post by brpylko on 2012-02-10
> **ve4cib said:**
> Personally I think C# is a lot cleaner than Java, and has some really nice features I wish Java had.  Things like iterators for for-loops:

C#:
```

String[] someStrings = { /*stuff here*/ };
for(String s in someStrings)
    doSomethingWithEachString(s);
```versus Java:
```

String[] someStrings = { /*stuff here*/ };
for(int i=0; i<someStrings.length; i++)
    doSomethingWithEachString(someStrings[i]);
```It's a minor difference, but the C# version is more intuitive to me.

Actually there are iterators in Java:

```

String[] someStrings = { /*stuff here*/ };
for(String s : someStrings){
    doSomethingWithEachString(s);
}

```And for Linux  console applications, I would recommend bash. It is much more powerful than Microsoft's batch and you can even create basic GUIs (using Zenity).

No to watch slews of protest about why you shouldn't use bash. :popcorn:

---

### Post by Simian Man on 2012-02-10
> **Repgahroll said:**
> In fact I was being exaggerated :). Some useful features that GDB doesn't have are the ability to edit the code during the execution - this is fantastic imho because it's like debugging a script, and things like showing the variables values in source, and proper code navigation (jumping to definitions, etc.) are little things that actually increase productivity in my case. The thing is totally integrated into the IDE to provide the best visual feedback. Although GDB is pretty good and have some cool features, I just don't find them that important, I think my priorities are just different. GDB is still a good competitor here, though lagging behind imho.
Being able to edit your code while it's being debugged is pretty cool.  I didn't know the MS debugger could do that.  But gdb and ddd can do all of the other things you mentioned.  You can jump to any function or line in any file and show the values of all variables.  ddd in particular is fantastic at displaying linked data structures in its graph area.  I've never seen another debugger do that as well.  gdb and ddd also allow you to call arbitrary functions in your program while it's being debugged.  This is great for displaying complex data structures during debugging or testing complicated invariants etc.  I don't think the MS C++ debugger can do that.  I also *love* the fact that ddd gives you the command window (with full tab completion) of gdb directly.  When I was a beginner, I mostly used the GUI, but I'm far more productive with the console.  I use the debugger *a lot* and ddd is the most productive one I've ever used - though the motif interface is incredibly ugly.


> **Repgahroll said:**
> MS compiler generates much better binaries imho - (according to my experience) it compiles dramatically faster (kinda 3-4x), the generated binary tends to be "much" faster (like 15%) and a little bit smaller also (like 20%). So, imho it generates better binaries overall, and I think one can find plenty of benchmarks that backup my experience here.
It is a little better, but there's no way it's even close to the numbers you made up.  I'd say in the neighborhood of 5% better code or so.  And if it's 3-4X faster, then your gcc build process is horribly inefficient.


> **Repgahroll said:**
> 
I never found a single undecipherable error in MSVC, although I agree that GDB text feedback is better.
Really?  You've never had the dreaded "Internal Compiler Error"?  Gcc has much better compiler errors, though once you get into advanced template expansions, both compilers suck :).

I'm not going to comment on the rest of what you said because it's all just bad analogies, hyperbole and made up "statistics".

---

### Post by The Cog on 2012-02-12
I'm going to have to go for more popcorn soon.

---

