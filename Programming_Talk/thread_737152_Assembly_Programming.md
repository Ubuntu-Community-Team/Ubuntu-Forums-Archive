---
title: "Assembly Programming"
date: 2008-03-27
forum: Programming Talk
---

### Post by swatto on 2008-03-27
Hey all :)

I would like to be able to look into programs to know how they work but not actually create my own applications - would assembly language be the necessary step to achieve this?

Thanks in advance

---

### Post by Wybiral on 2008-03-27
I believe what you're looking for is called "Open Source" :)

---

### Post by piousp on 2008-03-27
Assembly could be very frustrating if you dont know much about it. I would recomend some higher level language: C++, Python, etc.

---

### Post by Nemooo on 2008-03-27
[Assembly]("http://en.wikipedia.org/wiki/Assembly_language") is a low-level programming language, which is told to be "closer" to the computer, so you only need to know assembly, if you want to look at assembly code.

[Open Source]("http://en.wikipedia.org/wiki/Open_source") programs are what you're looking for. Open Source means that the program's code is free to look at (in some cases only if you've bought the program). I guess this is what you mean as you can only know how a program works, if you look at its source.

Hope that helps you out :)

---

### Post by piousp on 2008-03-27
Yep, opensource apps are what you are looking for.
Try for something in C++, Java, Python, Perl... just to give you some examples of what can you look for.
Personally, i would go with Java, but thats just me ;)
By the way, what kind of apps are you looking for??

---

### Post by swatto on 2008-03-27
I was just thinking - after reading Wybirals' reply, it will probably be c++ source code I would be intrested in because  ive got a book that I haven't touched called: Accelerated C++ which I will have a look at as I think it has many program examples in there.

Thankyou to all who have replied so far :)

---

### Post by Wybiral on 2008-03-27
It seemed like your original question was about reverse engineering, correct? If that's the case, then the answer is "no". Reverse engineering is a terrible way to find out how a program runs. When something is compiled, all of the useful information is lost (variable names, function labels, etc) and since modern compilers sometimes apply complex optimizations, the code that comes out is usually very far from the code that went in. In other words, it's not worth it unless you need to modify or port a binary where the source is unobtainable (and even then, it doesn't always help very much).

Open source, on the other hand, is an excellent way to learn to program and make use of code that you didn't write. And unlike reverse engineering, most open source projects have a great community that will help you understand the code you're trying to figure out.

---

### Post by pmasiar on 2008-03-27
If you want to learn programming, Python is the best first language for beginners - see sticky FAQ for poll.

If you want later to program "closer to the metal", C is best choice: It is almost as effective as ASM, but portable, and protects you from many errors which are easy to do in ASM. But don't start with C, start with Python. See wiki in my sig, and sticky FAQ.

ASM is not required at all - and even C is not required, unless you are obsessed with speed of your code. The higher the language you use, the more computer does for you and the harder it works for you: you trade your productivity in writing code to effectiveness of the resulting code. Because computers are fast and becoming faster 9and have nothing better to do, idling most of the time), it is good bargain.

---

### Post by Nemooo on 2008-03-27
Don't listen to pmasiar. He's working for Python and his cruel mission is to spread Pyton to as many as possible without telling them about the hidden virus that's secretly being deployed into all Python applications and soon will be released ;)

Trust your instincts and go with C++; it's fast, danish and executables are easily made.

---

### Post by Wybiral on 2008-03-27
> **Nemooo said:**
> Trust your instincts and go with C++; it's fast, danish and executables are easily made.

I disagree (as in, I agree with pmasiar). For someone learning how to program, or someone who doesn't plan to invest too much of their time into programming, a language like Python is a WAY better choice. Even if you do want to invest your time, Python is the way to go :)

Making executables isn't a perk, it's a flaw. It means you have to spend more time waiting for code to compile, manage more files (binary, source, build files) and you also have to compile the binary for every platform you plan to support! I don't know why anyone would want to mess with executables.

And as far as speed goes, Python has all kinds of ways to increase performance (psyco, cython, pyrex, swig, ctypes, weave, ...) to the point that performance is hardly an issue for most Python code (and even without those tools, performance is rarely an issue anyway).

---

### Post by Lord Illidan on 2008-03-27
I'd go with python. It's by far the easiest programming language I've ever used.

---

### Post by Nemooo on 2008-03-27
I was being sarcastic.

I get your point about concerning executables, and must admit I see why you prefer Python. Can you explain to me how you distribute Python apps when they can't be directly converted to executables? Are they implemented into C?

And I'm aware of the small difference in performance between C++ and Python, but I still think it's relevant information.

---

### Post by nvteighen on 2008-03-27
Let me disagree with all of you and suggest JavaScript.

1) You don't deal with compilers and executable formats. You'll just need a browser.
2) It's syntax resembles C/C++ and Java, so if you plan to step into any of those languages, you'll be a bit more familiar with some methods. (which is what happened to me).
3) It's very high level, even more than Python, if I'm not wrong.

Maybe a defect could be that it doesn't teach you how to manage memory wisely (as it uses dynamic memory allocation).

---

### Post by Wybiral on 2008-03-27
> **nvteighen said:**
> 1) You don't deal with compilers and executable formats. You'll just need a browser.You also have to juggle with the annoyingly unstandardized implementations of the language between each browser (it is a pain to write good, portable, Javascript. Ask any web developer).


> **nvteighen said:**
> 2) It's syntax resembles C/C++ and Java, so if you plan to step into any of those languages, you'll be a bit more familiar with some methods. (which is what happened to me).This is more of a flaw, IMO, not a perk.

> **nvteighen said:**
> 3) It's very high level, even more than Python, if I'm not wrong.More than Python? How so? It has a choppy class implementation, a lack of true associative arrays, a lack of generators / list comprehension, no concept of namespaces, and other than those flaws it doesn't really offer anything that Python doesn't.

---

### Post by mssever on 2008-03-27
> **nvteighen said:**
> Let me disagree with all of you and suggest JavaScript.And I'll disagree with you. :)

> 1) You don't deal with compilers and executable formats. You'll just need a browser.You don't need compilers and executable formats for many languages, such as: Python, Ruby, Perl <shudder>, PHP, etc.
> 2) It's syntax resembles C/C++ and Java, so if you plan to step into any of those languages, you'll be a bit more familiar with some methods. (which is what happened to me).Syntax isn't all that important. Syntax is easy to learn; learning the library takes more time.
> 3) It's very high level, even more than Python, if I'm not wrong.No, it's not.

> Maybe a defect could be that it doesn't teach you how to manage memory wisely (as it uses dynamic memory allocation).The defects are: poor documentation (most tutorials use severely outdated techniques; if you see document.write, run fast), lots of differences between browsers and outright bugs (thanks a lot, Microsoft), and an unusual object model that doesn't translate to any other common language.

Python's a good choice, as is my personal favorite, Ruby.

---

### Post by Wybiral on 2008-03-27
> **Nemooo said:**
> Can you explain to me how you distribute Python apps when they can't be directly converted to executables? Are they implemented into C?

Python is most commonly distributed via source :) Most platforms these days have the interpreter already installed, so distributing is usually just a matter of bundling up your source code.

> **Nemooo said:**
> And I'm aware of the small difference in performance between C++ and Python, but I still think it's relevant information.

It can be an issue. But one neat thing about Python is how easy it is to write modules for using languages like C and C++. There's SWIG (which takes C or C++ code and generates a Python interface for it), PyRex / Cython (which allow you to mix Python code with explicit type declarations that get compiled into C code), ctypes (a Python module that allows you to easily interface with external DLL's).

And that's only if psyco doesn't speed up your code (psyco is a Python module that performs JIT compilation on your code... Without you having to modify any of your original source).

---

### Post by Nemooo on 2008-03-27
What about Windows (even if we don't like our software should be compatible with it, right?), it doesn't support Python, does it?

---

### Post by nvteighen on 2008-03-27
> **Wybiral said:**
> You also have to juggle with the annoyingly unstandardized implementations of the language between each browser (it is a pain to write good, portable, Javascript. Ask any web developer).

Yup, you're right... I've forgotten that "little" detail...

> This is more of a flaw, IMO, not a perk.

I disagree. If you started from BASIC and then wanted to step into C, you would be forced to learn it from scratch. From JavaScript you get some very basics you **can** also apply to C. (e.g., how local and global variables are defined, the use of functions and how they're called).

> More than Python? How so? It has a choppy class implementation, a lack of true associative arrays, a lack of generators / list comprehension, no concept of namespaces, and other than those flaws it doesn't really offer anything that Python doesn't.

Yes, you're right, but the OP is just starting and won't be too much worried on those flaws, I think. (Well, maybe the array flaw could be serious).

---

### Post by Wybiral on 2008-03-27
> **Nemooo said:**
> What about Windows (even if we don't like our software should be compatible with it, right?), it doesn't support Python, does it?

[Yep]("http://python.org/download/"). Even the Windows people can use it.

---

### Post by Lord Illidan on 2008-03-27
> **Nemooo said:**
> What about Windows (even if we don't like our software should be compatible with it, right?), it doesn't support Python, does it?

Ironically, advanced c/c++ apps are probably harder to port to Windows than python apps..

---

### Post by Wybiral on 2008-03-27
> **nvteighen said:**
> I disagree. If you started from BASIC and then wanted to step into C, you would be forced to learn it from scratch. From JavaScript you get some very basics you **can** also apply to C. (e.g., how local and global variables are defined, the use of functions and how they're called).

As mssever said:

[quote=mssever]
Syntax isn't all that important. Syntax is easy to learn; learning the library takes more time.
[/quote]

But more than just the library, the very semantics of the language. Javascript and C have nothing in common other than the fact that they use curly braces and lines end in semicolons.

C is statically typed, Javascript is dynamically typed.
Javascript supports lambdas / dynamic functions, C doesn't even come close
C requires manual memory management, Javascript handles this for you
Javascript has (as limited as it is) an object system, C does not (sure you can emulate OOP, but C doesn't have an object system)
C doesn't forgive you (ever smashed the stack or overflowed a buffer?), Javascript is *relatively* safe

I could keep going on. My point is that the little details like braces and semicolons don't matter... The languages are VERY different.

And even if Javascript were more like C, that wouldn't help you learn a language like Lisp, Haskell, Python, etc... It would only help you learn Javascript and C :) (my point is, why do you even need to learn C next?)

---

### Post by Nemooo on 2008-03-27
> **Wybiral said:**
> [Yep]("http://python.org/download/"). Even the Windows people can use it.

I knew it could be downloaded and used in a Windows enviroment, but per default you can't run Python apps, and that's unpractical as most Windows users don't have a clue about what Python is.

On a similar topic:

Why aren't executable files in Ubuntu executable as in Windows? In Windows I could just doubleclick the .exe and it'd run, why not/how in Ubuntu?

---

### Post by mssever on 2008-03-27
> **nvteighen said:**
> I disagree. If you started from BASIC and then wanted to step into C, you would be forced to learn it from scratch. From JavaScript you get some very basics you **can** also apply to C. (e.g., how local and global variables are defined, the use of functions and how they're called).
A common mistake that newbies make (I once made it myself) is assuming that syntax has a big role in learning a language; it doesn't. See Wybiral's post for what I was about to write.

---

### Post by Wybiral on 2008-03-27
> **Nemooo said:**
> I knew it could be downloaded and used in a Windows enviroment, but per default you can't run Python apps, and that's unpractical as most Windows users don't have a clue about what Python is.

It's a small download, you can give your users the option of including it with your product. But I had Python installed when I was a Windows user. Oh, I forgot to mention [IronPython]("http://en.wikipedia.org/wiki/IronPython") too, which is definitely supported in Windows :)

> **Nemooo said:**
> On a similar topic:

Why aren't executable files in Ubuntu executable as in Windows? In Windows I could just doubleclick the .exe and it'd run, why not/how in Ubuntu?

I prefer not to download programs in top-secret compiled EXE form :) Source is much safer and more convenient (I can build it specifically for my machine, and alter it when I need to)

Linux's executable format is ELF, Windows uses PE (Portable Executable, ironically not portable at all). But you can run Windows executables using Wine in Linux (there are also emulators for Linux on Windows too). They most likely use different formats because Microsoft doesn't want you to run Linux executables on their machine (and they don't want us to run EXEs).

---

### Post by LaRoza on 2008-03-27
> **Nemooo said:**
> I knew it could be downloaded and used in a Windows enviroment, but per default you can't run Python apps, and that's unpractical as most Windows users don't have a clue about what Python is.

On a similar topic:

Why aren't executable files in Ubuntu executable as in Windows? In Windows I could just doubleclick the .exe and it'd run, why not/how in Ubuntu?

Windows uses file extensions to determine what a file is, and will execute anything it can without warning. (Try it, get a text file, give it a ".exe", or ".vbs" extension and see what happens. Do not put anything in the file)

Linux uses a more secure and sensible approache of using MIME types and permissions. You can make it so files marked as executable are run with a simple double click, but do you really want that?

---

### Post by mssever on 2008-03-27
Isn't there also a library that can convert any Python program into a stand-alone EXE which embeds a python interpreter?

---

### Post by LaRoza on 2008-03-27
> **mssever said:**
> Isn't there also a library that can convert any Python program into a stand-alone EXE which embeds a python interpreter?

Yes, py2exe : [http://www.py2exe.org/](http://www.py2exe.org/)

Very handy, although I would say that installing ActiveState's Python is much easier for people who plan on using Python apps.

(HP and Compaq computers come with Python as well.)

Seeing how Python is by default found on Linux, OS X, and many OEM machines, Windows is just the oddball. With IronPython, perhaps Python will be a "universal" language.

---

### Post by Nemooo on 2008-03-27
> **LaRoza said:**
> Linux uses a more secure and sensible approache of using MIME types and permissions. You can make it so files marked as executable are run with a simple double click, but do you really want that?

Probably not. But then, what is the smartest way to distribute C++ apps for Linux?

---

### Post by mssever on 2008-03-27
> **Nemooo said:**
> Probably not. But then, what is the smartest way to distribute C++ apps for Linux?
As source. :) Let the distros package it according to their own package manager's conventions.

---

### Post by LaRoza on 2008-03-27
> **Nemooo said:**
> Probably not. But then, what is the smartest way to distribute C++ apps for Linux?

You have several options:

[list]
[*]Source Tarballs
[*]Package them, in whatever format your target user uses. 
[/list]

Most of the time, you will see source tarballs, and pre packaged installers.

---

### Post by Nemooo on 2008-03-27
So generally the source should be distributed as source.tar.gz or source.pkg.tar.gz?

---

### Post by pmasiar on 2008-03-27
> Why aren't executable files in Ubuntu executable as in Windows? In Windows I could just doubleclick the .exe and it'd run, why not/how in Ubuntu?

Of course it is valid question... And I still blush when recalling my first contribution to usenet discussions... :-)

But.... Isn't if funny that person with glaring holes in understanding can so easily dismiss advice from far more knowledgeable people, without even understanding what that person just dismissed? For real expert, often dismissing is much harder (because it has to be based on facts, not feelings and prejudices).

@OP: Be very careful accepting advice from random strangers on internet. You want to make sure that your so called "expert" is not just a script kiddie with big ego and little knowledge.

BTW it is trivial to create association between .py files and installed Python, in fact ActiveState Python windows installer  does it automagically.

---

### Post by nvteighen on 2008-03-28
> **mssever said:**
> A common mistake that newbies make (I once made it myself) is assuming that syntax has a big role in learning a language; it doesn't. See Wybiral's post for what I was about to write.
Then, I should consider myself a newbie and keep learning a bit more in this very informative forums! :)

---

### Post by swatto on 2008-03-28
I did start learning Python - read 'A Byte of Python' and wrote all of the programs in the document but that is as far as I have got as I had a bit of trouble understanding how/when to use Classes in my programs.

Also it is a bit inconvenient because I do not have a hard-copy python book and I prefer to read things without having to stare at my computer (i should really get a printer)

---

### Post by ruy_lopez on 2008-03-28
> **swatto said:**
> Also it is a bit inconvenient because I do not have a hard-copy python book and I prefer to read things without having to stare at my computer (i should really get a printer)

I've struggled to find a good python book. "Learning Python" (oreilly) puts me to sleep. "Programming Python" (oreilly) is a bit better, but is written by the same author as "Learning Python". I find his writing style tedious.

If you find a good Python book, let me know.

---

### Post by swatto on 2008-03-28
If I continue with Python I would first have to find a book that is similar to Accelerated C++ where it gives you useful programs and explains each part of the program source code bit by bit.

---

### Post by Wybiral on 2008-03-28
I found Python to be the easiest language I've ever learned. I just grabbed a few tutorials from the web and "went to town" on the interactive interpreter. The language itself is easy, the hard part is getting used to not having to write everything on your own :) Before you code something, step back and search the [standard modules]("http://docs.python.org/lib/") (as well as the popular third party modules) and make sure it hasn't been done (because it usually has).

One tip I have for using the interactive interpreter is this: use the "dir" and "help" builtins, they rock! For instance, open up the terminal and type:
```

import math
help(math)

```
And you'll get an explanation of each component of the module. You can also type "help(math.sqrt)" to get info on one specific function. This works for all of the standard modules, and any other module that uses doc-strings properly (hopefully your own code too). This makes learning new libraries a breeze (I usually keep an active terminal up when I'm writing something in Python just so I can use these builtins and test out snippets as I'm writing).

---

### Post by pmasiar on 2008-03-28
Also, you can instantiate an object x, and use dir(x) to see all the methods available. Then you can use help(x.methodname) to get help, if name is not obvious enough. And try it in shell, one line at a time. Priceless!

---

### Post by swatto on 2008-03-28
Just ordered Core PYTHON Programming by Wesley Chun - hopefully should do the trick for me :)

---

