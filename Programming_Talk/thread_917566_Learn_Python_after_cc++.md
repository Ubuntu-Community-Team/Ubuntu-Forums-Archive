---
title: "Learn Python after c/c++?"
date: 2008-09-12
forum: Programming Talk
---

### Post by tuxerman on 2008-09-12
Hi all, I started off with programming when i learnt BASIC at school. I taught myself C++ a couple of years later, and then had to learn java(basic stuff) in school and c++ too(at school). Now I'm fairly okay in c++. I also learnt some basic linux scripting this year.

Now, I've heard a lot about Python. What I wanna know is whether it's good to learn Python after c++. Many people here seem to suggest the reverse order. What all does Python offer that C/c++ doesnt? And will it be beneficial to my career if I learn Python now?(I'm just into college for my BTech) Or is it better to stick to c/c++/java and polish my skills in them?

I might sound confused..but I really am confronted with mixed opinions :confused:

---

### Post by cb951303 on 2008-09-12
people recommend python before c++ because it's simpler and it's high-level thus a very good beginners language (not just for beginners ofcourse). However if you already know c++ there is nothing that holds you back from learning python. go for it:popcorn:

---

### Post by samjh on 2008-09-12
Go ahead and learn Python.  It's a language that is becoming quite popular in the open-source community, although there isn't much commercial demand for it compared to Java or .NET.  However if you're going to college, then perhaps Python will become commercially popular by the time you graduate.  Whatever the case, it will almost definitely be a worthwhile investment, and Python is quite a simple language to learn. so it shouldn't take long to become comfortable with it.

Python advantages compared to C++:
[list][*]Interpreted language - you can use the interpreter to test out snippets of code and "learn as you type".
[*]Dynamic typing can make handling data a little easier than static typing (which is what C++ and Java uses).
[*]High-level data structures (more abstract and simpler to use than C++) makes handling complex data and implementing algorithms easier than C++.
[*]Automatic memory management: no need to worry about memory leaks, because Python's garbage collector takes care of freeing memory for you.
[*]Comprehensive standard library - you'll find most of what you need without having to search for 3rd-party libraries, unlike C++'s relatively limited standard library.[/list]

Python's disadvantages compared to C++:
[list][*]Interpreted language - has a very big performance penalty. Some people will claim that you can reprogram performance bottlenecks using C, but reality is not so simple or easy. You should weigh up the pros and cons of having to maintain two different languages and whatever time-savings you might have with using Python instead of C++.
[*]Dynamic typing is a blessing, but carries the curse of inadvertently changing itself to a type you don't want, if your code is sloppy.  Easy to catch in static-typed languages, but harder in dynamic-typed ones.  Fortunately both C++ and Python have (reasonably) strong type-checking.
[*]Controversial syntax - whitespace actually means something in Python, and there are no distinctive block delimiters. Usually this isn't an issue, but some programmers don't like it. See for yourself.[/list]

Generally the advantages of Python outweigh the disadvantages, so go ahead and learn it.  It's quite different to C++ or Java, so you might gain a new perspective in the way you think about programming.

---

### Post by irrdev on 2008-09-12
Python is really just a powerful scripting language, with many of the capabilities of a full (compiled) programming language. It will never become commercially-popular for two reasons:
**1.** There is no way to keep your source "safe". After all, the python interpretor reads your source code directly. Imagine the piracy possibilities, not to mention the the possibilities for hackers! This is not a problem with open-source software, but it sure is with commercial products.

**2.** Distributing Python on Windows/Mac computers can be a nightmare! The base Python runtime doesn't provide a full-fledged GUI library, for example, so an application using wxPython must have the wxPython runtime manually installed in addition to the regular Python runtime. You have to manually setup environment paths and possibly install the wxwidgets library... the Java and .NET runtimes do this all for you, but not Python! There is a project call py2exe, which is supposed to bundle your python dependencies with your application into a single windows executable, but this is not well-tested and programmers can spend a lot of extra time setting this up. Also, py2exe noticeably slows down your application, as the executable has to extract the python runtime and application files each time it runs - it doesn't actually compile your python application into executable instructions. 

Linux, as both an open-source and package-based OS, doesn't suffer from either of the above problems. Package dependencies make installation a snap, and python and popular python libraries are available in the repositories of all major distros. As a result, Python is IMO a great language suited to Linux, but that is as far as it goes. I still far prefer using C++, even on Linux, as portability, speed, library support and complete OO support really matter to me. I know that many other users feel differently, but C++ and Java remain the commercial and cross-platform programmer's languages of choice. .NET may also be in the future, but Mono still has a way to go, especially on the Mac.

---

### Post by nvteighen on 2008-09-12
I learned Python **after** C and I can tell you that if you give it some serious time, you'll love it. Also, you'll learn it a breeze... I needed just a week and because I was coming from a non-OOP language. From C++ and Java it should be even easier, because you already know what inheritance is and so on.

The power of Python relies on its high power of expressing processes (*). This is based on the primitives it has, like lists and dictionaries, that allow you to create models in a very very easy way without declaring a "formal" class (actually, in Python everything is an object). Also, the basic functional programming features it provides are very useful too (and can help you to step into functional programming).

But the best feature, according to experts and me, is the interactive shell. IMO, the best way to learn Python is to play with that shell... and during development, the shell is a great place to test pieces.

(*) <propaganda>But nobody beats Lisp in that!</propaganda>

---

### Post by stevescripts on 2008-09-12
Spend a little time with Python (or Tcl, Ruby, etc) you will be glad you did.

Higher level languages allow the programmer to accomplish more, in less time,
with less code than compiled languages.

Steve

---

### Post by pmasiar on 2008-09-12
- Python increases productivity: I can finish my task about 5 times faster in Python (with less reading of docs)
- performance penalty - is important if code is production-critical. Most code people write is not.
- Dynamic typing (may cause typing errors)? That's why you write tests: and type checks are easiest to start with.
- Controversial syntax - whitespace: is not a problem after 15 minutes, and makes easier to read code of other people (and so collaboration). See [Python: Myths about Indentation](http:www.secnetix.de/olli/Python/block_indentation.hawk)

---

### Post by tuxerman on 2008-09-12
Thanks everyone.. the replies got me working :) I've got myself a book.. Will start today.

---

### Post by pmasiar on 2008-09-12
> **irrdev said:**
> Python is really just a powerful scripting language, with many of the capabilities of a full (compiled) programming language.

You obviously do not know Python enough to know even such basic thing that Python is compiled to bytecode, exactly like Java is. Difference is how bytecode is handled: IronPython bytecode is compiled. It's matter of resources. Java spent millions on development and marketing. If Python get this far with little or no institutional help, it says volumes how excellent the language is.

> It will never become commercially-popular 

LOL, even heard of "small" companies like Google, YouTube ILM who use Python extensively?

Python is popular with startups, because you need productivity to beat averages (se my FAQ for link)

> There is no way to keep your source "safe". ... Imagine the piracy possibilities, not to mention the the possibilities for hackers! This is not a problem with open-source software, but it sure is with commercial products.

In your logic, closed source compiled system like Windows is unbreakable? Or am I missing something? :-)

> Distributing Python on Windows/Mac computers can be a nightmare! The base Python runtime doesn't provide a full-fledged GUI library [...] You have to manually setup environment paths and possibly install the wxwidgets library... the Java and .NET runtimes do this all for you, but not Python! 

exactly like on Windows, you need to install libraries once (on Win, it is preinstalled, so invisible). Use good installer which sets environment, and ignore the FUD.

> py2exe, ... is not well-tested 

because only people who have religion of compiling (solving wrong problem) use it.

> .NET may also be in the future, 

... and it includes IronPython for .NET. Best of both worlds: write app in Python, libraries in C#.

---

### Post by LaRoza on 2008-09-12
> **pmasiar said:**
> 
LOL, even heard of "small" companies like Google, YouTube ILM who use Python extensively?

I heard about Nasa too. I hear they were pretty small.

> 
> There is no way to keep your source "safe". ... Imagine the piracy possibilities, not to mention the the possibilities for hackers! This is not a problem with open-source software, but it sure is with commercial products.

Exactly what is "safe"? OS X uses an open source kernel and has no "validation", yet piracy isn't as rampant as Windows which does the opposite. HP uses Python extensively in their OEM installs, yet there is no outbreak of HP computer issues. (Compaq also).

Open Source doesn't help crackers, and hackers are the one who wrote it in the first place probably.

(Quoting pmasiar's quote, there)

> 
exactly like on Windows, you need to install libraries once (on Win, it is preinstalled, so invisible). Use good installer which sets environment, and ignore the FUD.

To add: [http://www.python.org/doc/2.3.5/inst/inst.html](http://www.python.org/doc/2.3.5/inst/inst.html)

> 
because only people who have religion of compiling (solving wrong problem) use it.

I agree. It is much easier to ship the Python install for the minority of OS's that do not have it installed by default, then to try to force Python into an .exe.

> 
... and it includes IronPython for .NET. Best of both worlds: write app in Python, libraries in C#.

Also, Python (Jython) works on the Java platform. C# and Java cannot boast of this, but Python can and you get all the Pythonic goodness.

---

