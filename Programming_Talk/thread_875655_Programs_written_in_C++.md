---
title: "Programs written in C++?"
date: 2008-07-31
forum: Programming Talk
---

### Post by Syndacate on 2008-07-31
Hey,

I'm a software engineering student at RIT.

I know Java, and am currently reading a book on C++.  I don't know C.

I've been searching some of the open source, more common software, to see how software "interacts" with an OS (opposed to the mindless goal oriented terminal programs we create in classes), but it seems everything is written in C, which doesn't really help me b/c I don't know C.

Is there any common programs (that a lot of pple use) with open (public) source that's written in C++?  I'll admit I didn't do much searching, pidgin is written in C, not sure what else is on the "very commonly used" OSS list, was wondering if anybody could throw some suggestions out here?

I'm just trying to get an idea about how programs interact with certain aspects, like searching, browsing, filtering, daemons, minmizing to tray, etc.

Thanks in advance.

---

### Post by lisati on 2008-07-31
[www.programmersheaven.com](www.programmersheaven.com) might be a useful resource to check out - it has information for a variety of languages and platforms, including C++ and Linux.

---

### Post by mssever on 2008-07-31
Qt is the first thing that comes to mind. Also, I think I remember that OpenOffice is in C++.

---

### Post by era86 on 2008-07-31
I would try and understand C first, it will help with your C++ work. ;)

I would look into the QT library and see its implementation.  It's open source!

---

### Post by nvteighen on 2008-07-31
Firefox uses C++ (but not only).

---

### Post by Syndacate on 2008-07-31
> **era86 said:**
> I would try and understand C first, it will help with your C++ work. ;)

I would look into the QT library and see its implementation.  It's open source!

Is QT the system you need to add for Gentoo to work with KDE?

I was thinking of a more direct, single, program...like katapult or something easy to understand using it, therefore shouldn't be too difficult to try to learn how it ticks, y'know what I mean?

Like pidgin would be great if I was going at C, I know the program, I understand it's purpose, so looking at the source would help a great deal, since I already know what the source code does, y'know?

[quote=nvteighen]Firefox uses C++ (but not only).[/quote]

I didn't know you could mix and match languages - do you know off hand what else it's comprised of?

[quote=mssever]Qt is the first thing that comes to mind. Also, I think I remember that OpenOffice is in C++.[/quote]

Thanks, I'll add openoffice (word processor) to the list, maybe I can give that a whirl.  As far as QT, that's like a library backing, isn't it?  Not quite the direction I was headed.  I was more headed in the direction of <"common" - "simple" - "fully in C++"> - you know what I mean? (Sorry if this sounds picky, I'm obviously a newb.

[quote=lisati]www.programmersheaven.com might be a useful resource to check out - it has information for a variety of languages and platforms, including C++ and Linux.[/quote]

Thank you very much, I will check out that URL tomorrow.

<!--------->

Thank you all for your prompt responses.  Sorry if it sounds like I'm being nit picky, I'm just looking for how small, common, programs written in C++ are implemented into daily use of the operating system.

Like in class they gave us assignments like battleship, feeding frenzy, and a word search solver - all ran through the terminal (some had GUI's), all adheared to a strict standard.  I'm trying to figure out how they connect everything, like daemons and what not.

A friend of mine asked me if I could make him a program (he's a hardcore windows guy) that logs his usage on the computer.  So I was like "omg, I have no clue how to do this.  I need to make an installer, and then I need to make it somehow start when windows starts, then I need to make it run as a daemon, and respond, 'n there's really a quantum leap from typing "java frenzy 8" to double clicking on an icon and having it work with the system, y'know?  Obviously in linux it's a bit easier since you can just call the program from terminal if it's in the /bin folder.

OSS sparked a question, - I'm sorry, I'm sure there's is very off topic and I'm sure nobody here likes talking about windows.  Though when I looked at pidgin's source code, it's all .c (c source) and .h (I'm guessing that's compiled versions or something), but when you look at the program files of a windows program, it's all DLL's.  Now Java, C++, and C is what a lot of programs are written in and they're all dual platform (both on windows and linux).  But if C compiles to .o (object), and C++ compiles to whatever you name it, and in windows C++ compiles to .exe...then either there should be lots of executables in the program files or I'm definitely missing something here.

The differences can't be that radical, I mean azureus is the same for both platforms, am I to believe it was written in Java for linux, then completely restructed with DLL's and all for windows?

(wow, sorry about that tangent)

---

### Post by jimi_hendrix on 2008-07-31
Most comercial games are wrtitin in C or C++ but since your looking for open source that wont help you

---

### Post by WW on 2008-07-31
[Inkscape](http://www.inkscape.org/) is written in C++.

---

### Post by WW on 2008-07-31
> **Syndacate said:**
> 
Though when I looked at pidgin's source code, it's all .c (c source) and .h (I'm guessing that's compiled versions or something),

A .h file is a "header file"; both C and C++ use these.  It is part of the source code, not the compiled program.  Keeping reading your C++ book, and you'll get to it.
> **Syndacate said:**
> 
  But if C compiles to .o (object), and C++ compiles to whatever you name it, and in windows C++ compiles to .exe...then either there should be lots of executables in the program files or I'm definitely missing something here.

An intermediate step in compiling *both* C and C++ (and other languages) is to create a .o file, which is (roughly speaking) the compiled version of the source that has not yet been linked to create the final executable.  A .o file  does not correspond to a .exe file in windows.  In windows these are traditionally .obj files.

In windows, the final executable has the extension .exe, but in Linux, no special extension is required, and they typically have *no* extension.


For example, here's "Hello, world!" in C++:

hw.cpp
```

#include <iostream>

using namespace std;

int main()
    {
    cout << "Hello, world!" << endl;
    return 0;
    }

```
Here I compile it in two steps (compile then link), and run it:
```

$ ls
hw.cpp
$ g++ -c hw.cpp
$ ls
hw.cpp  hw.o
$ g++ hw.o -o hw 
$ ls
hw*   hw.cpp  hw.o
$ ./hw
Hello, world!
$ 

```
The first g++ command compiles the source code into hw.o.  hw.o is not an executable file; it has not been linked with all the required system libraries.  (For such a simple program, a single g++ command could have been used to create the executable, but I wanted to show that C++ also creates .o files.)

The final ls command shows three files. hw is the executable. (The * is not part of the file name; my ls command is set up to append a * to the names of executable files.)


I don't understand your conclusion about there being "lots of executables".

---

### Post by nvteighen on 2008-07-31
> **Syndacate said:**
> Is QT the system you need to add for Gentoo to work with KDE?

Qt is a GUI library used by some programs. KDE is formed by lots of programs working together mostly using Qt as their library. So, to have KDE in **any** OS, you'll need Qt.

The same for GNOME, but instead of Qt, it uses GTK+ (which is C).

> I didn't know you could mix and match languages - do you know off hand what else it's comprised of?

Yes, you can, though you need some tweaks to make the language work together. Firefox uses C++ and then some custom XML-based languages and Javascript to implement addons, if I'm not wrong. Look at [http://en.wikipedia.org/wiki/Firefox](http://en.wikipedia.org/wiki/Firefox)


> (...) I was more headed in the direction of <"common" - "simple" - "fully in C++"> - you know what I mean? (Sorry if this sounds picky, I'm obviously a newb.

(...) OSS sparked a question, - I'm sorry, I'm sure there's is very off topic and I'm sure nobody here likes talking about windows.  Though when I looked at pidgin's source code, it's all .c (c source) and .h (I'm guessing that's compiled versions or something), but when you look at the program files of a windows program, it's all DLL's.  Now Java, C++, and C is what a lot of programs are written in and they're all dual platform (both on windows and linux).  But if C compiles to .o (object), and C++ compiles to whatever you name it, and in windows C++ compiles to .exe...then either there should be lots of executables in the program files or I'm definitely missing something here.



Libraries are a bunch of functions in a single file you can call from another program, so you don't have to rewrite things already invented... (unless you explicitly want to rewrite, of course). DLLs and GNU/Linux's .so are functionally the same, the difference is that .so files are usually placed in /usr/lib or /lib, where Windows usually puts the DLLs in the same place where the EXE is.

C and C++ both compile into object in any system. The issue is that thoses object files are then linked together into an executable. The DLLs or .so files are compiled in a special way so that you can call the functions it contains from a running executable.

---

### Post by pmasiar on 2008-07-31
> **Syndacate said:**
> I'm just looking for how small, common, programs written in C++ are implemented into daily use of the operating system.

C++ is extension of C to manage huge complicated programs. Most people prefer to use (simpler) C for smaller programs :-)

---

### Post by mssever on 2008-07-31
> **Syndacate said:**
> A friend of mine asked me if I could make him a program (he's a hardcore windows guy) that logs his usage on the computer.  So I was like "omg, I have no clue how to do this.  I need to make an installer, and then I need to make it somehow start when windows starts, then I need to make it run as a daemon, and respond, 'n there's really a quantum leap from typing "java frenzy 8" to double clicking on an icon and having it work with the system, y'know?
This raises another interesting issue. If you decide to take on this project, you'll probably discover that it's bigger than you originally thought. I know that was the case when I started Net Responsibility (see my signature), which is broadly similar. You'd likely be happier writing such a program in a higher-level language that has cross-platform compatibility built in (such as Ruby or Python), because the difference in the amount of time it'll take to write will be huge, and raw execution speed won't matter much.
> Obviously in linux it's a bit easier since you can just call the program from terminal if it's in the /bin folder.
You can do something like that in Windows, too, if you want.

---

### Post by dribeas on 2008-07-31
> **pmasiar said:**
> C++ is extension of C to manage huge complicated programs. Most people prefer to use (simpler) C for smaller programs :-)

Don't get me started on that! :P C++ is much more than an extension of C.

   David

---

### Post by dribeas on 2008-07-31
> **pmasiar said:**
> C++ is extension of C to manage huge complicated programs. Most people prefer to use (simpler) C for smaller programs :-)

Don't get me started on that! :p C++ is much more than an extension of C.

   David

---

### Post by nvteighen on 2008-07-31
> **dribeas said:**
> Don't get me started on that! :p C++ is much more than an extension of C.

   David
Some here in the forums will say C++ is rather a perversion of C...

---

### Post by pmasiar on 2008-07-31
> **dribeas said:**
>  C++ is much more than an extension of C.

> **nvteighen said:**
> Some here in the forums will say C++ is rather a perversion of C...

Extension, perversion or more... Regardless, I know couple of smart hackers who prefer C over C++ for code under say 10KLOC.

And for code over that, IMNSHO Python + C libraries is often better OOP choice than C++ :-)

---

### Post by nvteighen on 2008-07-31
> **pmasiar said:**
> 
And for code over that, IMNSHO Python + C libraries is often better OOP choice than C++ :-)

Far better, at least from the code I've read.

---

### Post by Syndacate on 2008-07-31
As for other peoples' C++ vs C as an extension argument, blah.  From the sound of it, that's subject to opinion.

> **mssever said:**
> This raises another interesting issue. If you decide to take on this project, you'll probably discover that it's bigger than you originally thought. I know that was the case when I started Net Responsibility (see my signature), which is broadly similar. You'd likely be happier writing such a program in a higher-level language that has cross-platform compatibility built in (such as Ruby or Python), because the difference in the amount of time it'll take to write will be huge, and raw execution speed won't matter much.

Yeah, lol, I know that.  I probably won't take on the project.  This thread, to show the least, told me if anything, that I'm nowhere near ready to produce an application.

What do you mean by "higher level" - also, I know linux has high support for python, but does windows?  I mean I thought C++ was a popular language...well at least more popular than java...seems like everything I learned about it was useless..

> **nvteighen]Yes, you can, though you need some tweaks to make the language work together. Firefox uses C++ and then some custom XML-based languages and Javascript to implement addons, if I'm not wrong. Look at [http://en.wikipedia.org/wiki/Firefox](http://en.wikipedia.org/wiki/Firefox)[/quote]

Okay, well that's way over my head.

[quote=nvteighen]Libraries are a bunch of functions in a single file you can call from another program, so you don't have to rewrite things already invented... (unless you explicitly want to rewrite, of course). DLLs and GNU/Linux's .so are functionally the same, the difference is that .so files are usually placed in /usr/lib or /lib, where Windows usually puts the DLLs in the same place where the EXE is.[/quote]

Would that be similar to in java, the way they have us make a few different classes, like one that does the GUI, but maybe another class for calculating something that you pass some values to...so would those separate classes that aren't initially executed, but may be called upon in the program?  Or do I have the wrong idea of what you're trying to say?

As far as .so files vs DLLs - I gotcha, which would also explain why I don't see very many .so files, because I'm usually not hanging out in the /usr/lib area  said:**
> C and C++ both compile into object in any system. The issue is that thoses object files are then linked together into an executable. The DLLs or .so files are compiled in a special way so that you can call the functions it contains from a running executable

Can you elaborate on "a special way" - I learned primarily in Java, everything there compiles to class, so you can put functions there and call them from the main program.  Would those be the corresponding files for the .so and DLL libraries, or am I mixed up?  Or does Java have its own way of compiling special library types, and I just haven't learned it yet?

I think you mean they're compiled, basically, without a main method, so they're usually not ran, just accessed.  Or am I completely off my rocker trying to understand this?

> **WW]A .h file is a "header file" said:**
> 

Yeah, I dealt with header files when I built "Linux From Scratch" (LFS).  Didn't fully understand them, but you need them.  I'll keep reading, but I'm guessing it's just a file that contains the headers, so you can reference them from other files, instead of putting them explicitly into each file?

[quote=WW]An intermediate step in compiling both C and C++ (and other languages) is to create a .o file, which is (roughly speaking) the compiled version of the source that has not yet been linked to create the final executable. A .o file does not correspond to a .exe file in windows. In windows these are traditionally .obj files.

In windows, the final executable has the extension .exe, but in Linux, no special extension is required, and they typically have no extension.


For example, here's "Hello, world!" in C++:

```

```

The first g++ command compiles the source code into hw.o. hw.o is not an executable file; it has not been linked with all the required system libraries. (For such a simple program, a single g++ command could have been used to create the executable, but I wanted to show that C++ also creates .o files.)

The final ls command shows three files. hw is the executable. (The * is not part of the file name; my ls command is set up to append a * to the names of executable files.)


I don't understand your conclusion about there being "lots of executables".

Yeah, I found that out while googling how to work g++ (b/c the man sucked ;)).  I simply did:

```
$ g++ -c test.cpp -o test
```

So that compiled it and linked it, in one step...but why would I want to just create object files and not link them?

My conclusion of "*lots of executables*" simply meant that if a program was written in C++, and say you have 5 .cpp files (in one location), and compiled them all, you should wind up with 5 executables, but rather, you wind up with 1 executable and 4 DLL or .so files - I'm kinda confused on how that comes about.  I mean somebody up top said it's compiled differently, but then what's the difference of object files (.o) vs DLL/.so files?

Damn, this is confusing 4 me :(

Thanks guys, for all your help so far.

---

### Post by WW on 2008-07-31
> **Syndacate said:**
> 
Yeah, I found that out while googling how to work g++ (b/c the man sucked ;)).  I simply did:

```
$ g++ -c test.cpp -o test
```

So that compiled it and linked it, in one step...

Actually, that command did *not* link it. By giving the **-c** option, you specifically told g++ *not* to run the linker.  That command created an object file with the name **test**.  It is not an executable.  The name would have been **test.o**, but by using the **-o** option, you overrode the default output name.

---

### Post by mssever on 2008-07-31
> **Syndacate said:**
> What do you mean by "higher level" - also, I know linux has high support for python, but does windows?  I mean I thought C++ was a popular language...well at least more popular than java...seems like everything I learned about it was useless..
A higher level language moves you farther away from the hardware and enables you to accomplish what you want with less code and fewer bugs. In C++, you have to worry about memory management; in most higher level languages, that's taken care of for you already.

You can install Python on any platform. I'd recommend that you learn something like Python, because from your comments it appears that there are a lot of language-independent basics you haven't learned yet, and you'll probably find them easier to learn in a language like Python than C++. For example, virtually all languages have some form of library support, though the terms and the specifics differ. Python's term is *module*, and if you do much with Python, you'll end up using modules a lot. Once you understand that, than other languages libraries will be simple.

---

### Post by LaRoza on 2008-07-31
C++ was once an extension, now it is no longer that (it used to be a preprocessor for C)

---

### Post by nvteighen on 2008-07-31
> **Syndacate said:**
> A
Would that be similar to in java, the way they have us make a few different classes, like one that does the GUI, but maybe another class for calculating something that you pass some values to...so would those separate classes that aren't initially executed, but may be called upon in the program?  Or do I have the wrong idea of what you're trying to say?


You got the idea: they're the same. The only difference... well, see below :)

> Can you elaborate on "a special way" - I learned primarily in Java, everything there compiles to class, so you can put functions there and call them from the main program.  Would those be the corresponding files for the .so and DLL libraries, or am I mixed up?  Or does Java have its own way of compiling special library types, and I just haven't learned it yet?

I think you mean they're compiled, basically, without a main method, so they're usually not ran, just accessed.  Or am I completely off my rocker trying to understand this?

 
C and C++ compile to native machine code that directly relies on the operating system (and of course, the libraries). But, the issue is that a shared library is shared, i.e. it's only loaded once in memory (by the linker) and all programs that use it call it from the same place (to save memory... it's shared!). For achieving that, the library machine code is required to be in a special format (called [ Position Independent Code (PIC)]("http://en.wikipedia.org/wiki/Position_independent_code")). In summary, if you want to create a shared library, you have to pass some options to the compiler...

I don't know how Java works, but I guess that the reason is related to the fact that compiled class files have to be passed through the Java VM to be executed. So, the virtual machine should load things by need (as Python, which doesn't duplicate loaded modules?) and knows what's going on in all executed java programs...

---

### Post by Cygnus on 2008-07-31
> **Syndacate said:**
> Yeah, lol, I know that.  I probably won't take on the project.  This thread, to show the least, told me if anything, that I'm nowhere near ready to produce an application.

C++ takes a while to learn, also note that it can be quite confusing at first when people mix C/C++ code, so knowing C is a good thing because many C++ programs are quite C-ish.

By the way you can browse freshmet.net for open source projects written in C++: [http://freshmeat.net/browse/165/](http://freshmeat.net/browse/165/).

---

### Post by pmasiar on 2008-07-31
> **Syndacate said:**
> What do you mean by "higher level" - also, I know linux has high support for python, but does windows? 


Higher level: having operators, libraries and data structures which help accomplish more with less code.

Some higher-level languages/systems are specialized for specific tasks: SQL for databases, R for statistics, etc. Other systems are more generic but still more productive. It often comes with dynamic (late) binding of type info to name. And that's the reason why you should learn dynamically typed language, like Python.

Python has excellent support under Windows. Recently, Microsoft released own version of Python (IronPython) under open-source approved license (but not GPL or BSD compatible of course :-) ), which has superior support for .NET, and you can do tricks not possible in C# (due of dynamic typing in Python).

>  I mean I thought C++ was a popular language...well at least more popular than java...seems like everything I learned about it was useless..

C++ and java are popular languages - but not the only possible. They focus on generating effective (fast) code. In many areas, programmer's productivity is more important, so  developers are willing to sacrifice 30% hit on execution speed to get 10 times productivity. Especially for web apps, and in small companies and startups, dynamic languages rule.

Useless? Not exactly: lots of what you learned is language-independent. And if you want to reuse your knowledge of java libraries, and take advantage of productivity gain of dynamic languages, you can use Jython (Python on java) or JRuby.

Welcome to world of programming: as [http://en.wikipedia.org/wiki/Red_Queen](http://en.wikipedia.org/wiki/Red_Queen) said: "It takes all the running you can do, to keep in the same place." :-)

---

### Post by Syndacate on 2008-07-31
> **WW said:**
> Actually, that command did *not* link it. By giving the **-c** option, you specifically told g++ *not* to run the linker.  That command created an object file with the name **test**.  It is not an executable.  The name would have been **test.o**, but by using the **-o** option, you overrode the default output name.

Ah, that was a typo, I just double checked the syntax with the site I found yesterday and it didn't have the -c flag, so I must not have used it.

[http://www.cplusplus.com/forum/beginner/3048/](http://www.cplusplus.com/forum/beginner/3048/)
(is the site I found with example of how to use the g++ compiler)

I couldn't have, if I ran it, could I?

I ran it afterwords by typing:

```
./test
```

and it ran.  Can object files, *program name*.o be executed?  I guess not because I just tried compiling it without linking it and upon trying to run it it told me that binary files cannot be executed.

> **mssever]A higher level language moves you farther away from the hardware and enables you to accomplish what you want with less code and fewer bugs. In C++, you have to worry about memory management said:**
> 

So is that like Java, where the random garbage collector does memory management for you?

[quote=mssever]You can install Python on any platform. I'd recommend that you learn something like Python, because from your comments it appears that there are a lot of language-independent basics you haven't learned yet, and you'll probably find them easier to learn in a language like Python than C++. For example, virtually all languages have some form of library support, though the terms and the specifics differ. Python's term is module, and if you do much with Python, you'll end up using modules a lot. Once you understand that, than other languages libraries will be simple.

Alright, I'll head onto python when I'm done with this C++ book, that was my intended goal anyways.  They teach java at the school, so any programming knowledge I have is from that...and there isn't a lot of "half steps" like there is in C++ in java, every ".java" compiles to ".class" - no headers, no nothing.  I guess I see why they started with Java instead of C++.

Though I know python libs are very popular on linux systems, but do a lot of windows and/or mac systems utilize python as well?

[quote=nvteighen]C and C++ compile to native machine code that directly relies on the operating system (and of course, the libraries). But, the issue is that a shared library is shared, i.e. it's only loaded once in memory (by the linker) and all programs that use it call it from the same place (to save memory... it's shared!). For achieving that, the library machine code is required to be in a special format (called  Position Independent Code (PIC)). In summary, if you want to create a shared library, you have to pass some options to the compiler...

I don't know how Java works, but I guess that the reason is related to the fact that compiled class files have to be passed through the Java VM to be executed. So, the virtual machine should load things by need (as Python, which doesn't duplicate loaded modules?) and knows what's going on in all executed java programs...[/quote]

Alright, so the .so and .DLL files are just parts of code, functions, etc. (dynamic link library, guess that makes sense) that the executed part of the program uses?

[quote=Cygnus]C++ takes a while to learn, also note that it can be quite confusing at first when people mix C/C++ code, so knowing C is a good thing because many C++ programs are quite C-ish.

By the way you can browse freshmet.net for open source projects written in C++: [http://freshmeat.net/browse/165/](http://freshmeat.net/browse/165/)[/quote]

I'll check the site out, thanks.  As for learning C++, I chose it because it seemed a lot of programs were written in it, and I heard it's very similar to Java (which I learned/am learning in college).  Though now I'm wondering if I should have took a look at C instead.

[quote=pmasiar]Higher level: having operators, libraries and data structures which help accomplish more with less code.

Some higher-level languages/systems are specialized for specific tasks: SQL for databases, R for statistics, etc. Other systems are more generic but still more productive. It often comes with dynamic (late) binding of type info to name. And that's the reason why you should learn dynamically typed language, like Python.

Python has excellent support under Windows. Recently, Microsoft released own version of Python (IronPython) under open-source approved license (but not GPL or BSD compatible of course ), which has superior support for .NET, and you can do tricks not possible in C# (due of dynamic typing in Python).[/quote]

Gotcha.  So is Java considered a higher level programming language?

[quote=pmasiar]C++ and java are popular languages - but not the only possible. They focus on generating effective (fast) code. In many areas, programmer's productivity is more important, so developers are willing to sacrifice 30% hit on execution speed to get 10 times productivity. Especially for web apps, and in small companies and startups, dynamic languages rule.

Useless? Not exactly: lots of what you learned is language-independent. And if you want to reuse your knowledge of java libraries, and take advantage of productivity gain of dynamic languages, you can use Jython (Python on java) or JRuby.

Welcome to world of programming: as [http://en.wikipedia.org/wiki/Red_Queen](http://en.wikipedia.org/wiki/Red_Queen) said: "It takes all the running you can do, to keep in the same place." :)[/quote]

Alright, so what I'm getting out of this is Java and C++ are slower on execution, but they take less code to write - which makes sense, but then why is python so good if that's a higher programming language as well?

I like dynamic languages a lot (took a class in VB) more than object oriented, though it seems the world is based around object oriented programming.

So the only thing I'm confused about now is why would you compile something to an object file, and not link it to the executable?  Seems like that would be one of the main reasons for creating it (use with the executable) - and what would the difference be between object files and .so files?

Thanks a lot for your guys' help..this is pretty hard for me to wrap my head around.

---

### Post by imdano on 2008-07-31
> **Syndacate said:**
> Alright, so what I'm getting out of this is Java and C++ are slower on execution, but they take less code to write - which makes sense, but then why is python so good if that's a higher programming language as well?You have that backwards.  Java and C++ are faster on execution but take longer to write.  C++ is faster than Java in general, but is more difficult to code (pointers, manual memory management, complicated syntax once you get into things like templates).  Python is slower than both but you can write a fairly complicated app very quickly.

---

### Post by LaRoza on 2008-07-31
> **imdano said:**
> Python is slower than both but you can write a fairly complicated app very quickly.

Well, one can write the important parts in C (which is faster than Java or C++) and just use Python for the other.

---

### Post by mssever on 2008-07-31
> **Syndacate said:**
> So is that like Java, where the random garbage collector does memory management for you?Java was the language used in my first programming class, and I haven't touched it since, so I'm not a Java authority. But I'm pretty sure that Java's GC isn't random. Most higher-level languages have GC built in (there are several different types of GC in use).

> Though I know python libs are very popular on linux systems, but do a lot of windows and/or mac systems utilize python as well?Python has a large standard library that's guaranteed to be present in every Python install (barring differences between versions). If Python isn't installed on a particular system, it isn't difficult to install. There even exist programs to convert Python programs to Windows EXEs. I'm guessing MacOS includes Python, but that's only a guess, since I don't have access to a Mac. At any rate, it'd be faster to solve this problem than to write in C++ just for cross-platform compatibility.

> Alright, so what I'm getting out of this is Java and C++ are slower on execution, but they take less code to write - which makes sense, but then why is python so good if that's a higher programming language as well?Python is more flexible than Java and requires a whole lot less boilerplate code. The differences between static and dynamic typing have major implications. Java and C++ (and C and D, etc.) are static; Python and Ruby (and many more) are dynamic.

> I like dynamic languages a lot (took a class in VB) more than object oriented, though it seems the world is based around object oriented programming.Dynamism has nothing to do with OO. See Ruby for a good example of a language that's both dynamic and OO from the ground up. (Python is also thoroughly OO, but Python does some tricks to hide a certain amount of the OO and make the language a bit inconsistent.) Your opinion of OO has been jaded by Java and C++. :)

---

### Post by matja on 2008-07-31
> **Syndacate said:**
> 
So the only thing I'm confused about now is why would you compile something to an object file, and not link it to the executable?  Seems like that would be one of the main reasons for creating it (use with the executable)


The only purpose of an object file that I know of is just what you said - to link it into an executable or a library file. The reason for creating them explicitly is to save time when recompiling a large project.

Say we have a program consisting of two source files: a.cpp and b.cpp. The command
```
g++ a.cpp b.cpp -o myprog
```
is basically the same as
```

g++ -c a.cpp            # Compile a.cpp into object file a.o
g++ -c b.cpp            # Compile b.cpp into object file b.o
g++ a.o b.o -o myprog   # Link a.o and b.o into executable myprog
rm a.o b.o              # Remove the intermediate object files

```
Now if we make a change to a.cpp and want to recompile our program, the above command would do the same steps as before, i.e. compiling both a.cpp and b.cpp (which is also necessary since the object files were removed). But since only a.cpp has changed, we only need to recompile that file if we have saved b.o, since b.cpp and hence b.o will be the same. In this example, the fact that the above command recompiles b.cpp as well doesn't really matter (unless it's huge), but imagine if we have hundreds of source files and only modified one!

> **Syndacate said:**
> 
and what would the difference be between object files and .so files?


Well, I think previous posters have explained this better than I'm capable of, but I guess you could think of a .so file as a .o file that you don't include in your executable but place at a separate location, i.e. dividing your program into two parts. There would be no point to this if only one program was using it, especially since shared libraries add some overhead when loading the executable, but the trick with a dynamic/shared library is that many executables can use this same .so file instead of each one including its own copy (which they would have to do with a .o file). This has implications in the use of system memory, as well as the size of the executables, but I won't get into details because I not sure of them myself ;)

Good luck with your endeavors!

---

### Post by Syndacate on 2008-07-31
> **imdano said:**
> You have that backwards.  Java and C++ are faster on execution but take longer to write.  C++ is faster than Java in general, but is more difficult to code (pointers, manual memory management, complicated syntax once you get into things like templates).  Python is slower than both but you can write a fairly complicated app very quickly.

Oh, gotcha.  Thanks for the correction.  That makes a lot more sense, since C++ is "related" to C (I'm not going to go into how exactly, as that seems to be a touchy subject) which I heard is a base level programming language, then I also heard that Java was written in C++, so it makes sense that Java is slower than C++, and that a higher level programming language such as Python would run slower, yet be faster to write.  So I guess that begs a question of:  *Do you have more control with a lower level programming language?*

> **LaRoza]Well, one can write the important parts in C (which is faster than Java or C++) and just use Python for the other.[/quote]

Refer to my question above - is it fair to say that since python is a higher level programming language, you don't have the control you do with some of the lower level programming languages such as C, C++, and Java?

[quote=mssever]Java was the language used in my first programming class, and I haven't touched it since, so I'm not a Java authority. But I'm pretty sure that Java's GC isn't random. Most higher-level languages have GC built in (there are several different types of GC in use).[/quote]

Ah, okay, teachers just told us nothing we did controlled it, it would manage memory automatically and upon certain actions not specified by the programmer.

[quote=mssever]Python has a large standard library that's guaranteed to be present in every Python install (barring differences between versions). If Python isn't installed on a particular system, it isn't difficult to install. There even exist programs to convert Python programs to Windows EXEs. I'm guessing MacOS includes Python, but that's only a guess, since I don't have access to a Mac. At any rate, it'd be faster to solve this problem than to write in C++ just for cross-platform compatibility.[/quote]

Ah, I see, makes sense.

[quote=mssever]Python is more flexible than Java and requires a whole lot less boilerplate code. The differences between static and dynamic typing have major implications. Java and C++ (and C and D, etc.) are static said:**
> 

Boilerplate code?  What's that?

[quote=mssever]Dynamism has nothing to do with OO. See Ruby for a good example of a language that's both dynamic and OO from the ground up. (Python is also thoroughly OO, but Python does some tricks to hide a certain amount of the OO and make the language a bit inconsistent.) Your opinion of OO has been jaded by Java and C++.

Ah, that sux :( - What's the difference, you said java and C++ are static, assuming ur talking about the libraries they use?  As with Java and C++ use libraries in the same directory as the executable where python and Ruby have common directories to share files?

[quote=matja]The only purpose of an object file that I know of is just what you said - to link it into an executable or a library file. The reason for creating them explicitly is to save time when recompiling a large project.

Say we have a program consisting of two source files: a.cpp and b.cpp. The command

```
 
```

Now if we make a change to a.cpp and want to recompile our program, the above command would do the same steps as before, i.e. compiling both a.cpp and b.cpp (which is also necessary since the object files were removed). But since only a.cpp has changed, we only need to recompile that file if we have saved b.o, since b.cpp and hence b.o will be the same. In this example, the fact that the above command recompiles b.cpp as well doesn't really matter (unless it's huge), but imagine if we have hundreds of source files and only modified one![/quote]

Ah, gotcha, so it's basically so we can save time by only compiling one part instead of the entire thing.

So two questions about that.

A)  Say we have a.o, b.o, both linked to myprog.  Say we create a 3rd source file, and compile it to c.o, do we have to re-link all of them by typing:

```
g++ a.o b.o c.o -o myprog
```

or can we just link them by typing:

```
g++ c.o -o myprog
```

B)  After the objects are linked to the program, they don't seem to be necessary anymore.  So would it be fair to say that "linking" them kind of "inserts" the objects into a file executable?  As in "myprog" is made up of a.o, b.o, and c.o, combined?

[quote=matja]Well, I think previous posters have explained this better than I'm capable of, but I guess you could think of a .so file as a .o file that you don't include in your executable but place at a separate location, i.e. dividing your program into two parts. There would be no point to this if only one program was using it, especially since shared libraries add some overhead when loading the executable, but the trick with a dynamic/shared library is that many executables can use this same .so file instead of each one including its own copy (which they would have to do with a .o file). This has implications in the use of system memory, as well as the size of the executables, but I won't get into details because I not sure of them myself

Good luck with your endeavors![/quote]

Well if I'm understanding that right, that makes sense.

What thing I'm confused a bit on, if I'm understanding dynamic libraries vs static libraries, aren't MOST programs going to have static libraries, if they have dynamic libraries?  'Cause there's always going to be a few files that aren't shared, but are more specific to that program, which wouldn't be in the dynamic libraries, correct?

---

### Post by mssever on 2008-07-31
> **Syndacate said:**
> Oh, gotcha.  Thanks for the correction.  That makes a lot more sense, since C++ is "related" to C (I'm not going to go into how exactly, as that seems to be a touchy subject) which I heard is a base level programming language, then I also heard that Java was written in C++, so it makes sense that Java is slower than C++, and that a higher level programming language such as Python would run slower, yet be faster to write.  So I guess that begs a question of:  *Do you have more control with a lower level programming language?*Actually, C++ compiles to machine code, just like C does. Given an ideal compiler, any language that compiles to machine code should be equal in terms of raw speed. Of course, an ideal compiler probably doesn't exist. Java is compiled to bytecode and has to run inside a virtual machine. That's why it's slower. Basic Python isn't compiled to the same level, plus there's a lot more going on at runtime, so it's slower still. Although there are tricks you can do to speed Python upwhen necessary.

Yes, you have more control with a lower level language. Sometimes you need that control, but often that extra control translates into more opportunities for bugs to show up. And it almost always means writing more code.

> Ah, okay, teachers just told us nothing we did controlled it, it would manage memory automatically and upon certain actions not specified by the programmer.Which is different from random. I once was generating a report based on a logfile which involved most of the data in the file but sliced and diced into a totally different format. My initial implementation involved repeated string concatenations (I'd forgotten that Ruby strings are immutable). It worked OK until the logfile grew quite large. Suddenly, the process was consuming enormous amounts of memory and swapping continually. The reason I mention this is that I was watching a memory meter and it was clear that Ruby's mark-and-sweep GC was running every 0.5 second (possibly influenced by heavy swapping). I eventually changed the algorithm to push strings onto an array and did one join at the end, and my memory troubles were over.

Python's GC is different, I think. It uses reference counting, so I believe that it guarantees that objects will be garbage collected as soon as there are no more references to it.


> Boilerplate code?  What's that?That's code that you have to type all the time just to satisfy the compiler/interpreter. For example, here are two hello world programs; the first one is what I remember of Java from years ago. I hope it's correct!
```
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello world");
  }
}
```
And the equivalent in Ruby:
```
puts "Hello world"
```
Now, Ruby is an OO language, and you can create a class if you want: ```
class HelloWorld
  def initialize
    puts "Hello world"
  end
end
HelloWorld.new if __FILE__ == $0
```
But you don't have to do this if you don't need to. Notice how much less there is to type.

Python makes you type even less:
```
print 'Hello World'
# Or, as a class:
class HelloWorld:
    def __init__(self):
        print 'Hello world'
if __name__ == '__main__': HelloWorld()
```


> Ah, that sux :( - What's the difference, you said java and C++ are static, assuming ur talking about the libraries they use?  As with Java and C++ use libraries in the same directory as the executable where python and Ruby have common directories to share files?I'm referring to static versus dynamic typing. In Java and C++, you have to declare the type of everything. In Python and Ruby, the type is determined by whatever you assign to something, and can change whenever you want it to. You can also use duck typing by having certain objects expose certain similar methods so that you can then use those objects without having to care about their type.

---

### Post by nanotube on 2008-08-01
here's a list of 26311 (as of the time of this post) open source projects on sourceforge that are written [at least in part] in c++:
[http://sourceforge.net/softwaremap/trove_list.php?form_cat=165](http://sourceforge.net/softwaremap/trove_list.php?form_cat=165)

this ought to give you plenty of reference material. :)

---

### Post by bilijoe on 2008-08-01
> **Syndacate said:**
> Hey,
 
I'm a software engineering student at RIT.
 
I know Java, and am currently reading a book on C++. I don't know C.
 
I've been searching some of the open source, more common software, to see how software "interacts" with an OS (opposed to the mindless goal oriented terminal programs we create in classes), but it seems everything is written in C, which doesn't really help me b/c I don't know C.
 
Is there any common programs (that a lot of pple use) with open (public) source that's written in C++? I'll admit I didn't do much searching, pidgin is written in C, not sure what else is on the "very commonly used" OSS list, was wondering if anybody could throw some suggestions out here?
 
I'm just trying to get an idea about how programs interact with certain aspects, like searching, browsing, filtering, daemons, minmizing to tray, etc.
 
Thanks in advance. C++ ***_[COLOR=blue]IS[/COLOR]_*** C. The ++ was added to denote that a set of extensions had been added to a C compiler so it was exuipped to handle these extensions. The extensions simplify the creation, maintenance, and use of "objects", making the application of Object Oriented Techniques to programs written in C easier, and to standardize the way in which objects were implemented.
 
The ++ in C++ does nothing for object oriented programming, except provide a set of tools to make it easier, and to standardize it. Object oritntation is a subject unto itself, and if you don't understand it, the ++ isn't going to help you at all. Similarly, since C++ is an extension of C, I _*strongly*_ advise you learn C programming first, while reading up on exactly what object orientation is.
 
Object oriented programming in C can be accomplished without the use of a ++ enabled compiler. I am a retired software engineer. I am also ADD. Long before the advent of C++, I found it helpful (if not necessary, because of the way ADD affects one's thinking) to create a [large and fairly complex] set of Macros (as in Microsoft Macro Assembler), and a library of functions to support these macro extensions. It was written in a combination of Assembly Language and C, and I found it immensly helpful in allowing me to create state-of-the-art programs.
 
Together (C and my macro extensions and their accompanying library of functions), these allowed me to structure my code in a very efficient, modular, and reusable way. A good part of the inspiration, and the basic concepts I used were similar to an extended version of the Macro Assembler created by Berkekey Softworks, whch they called ESPIRE. This extended macro assembler served the function of facilitating a highly efficient programming paradigm, for programs written in assembly language.
 
When C++ started gaining popularity, I was so steeped in the use of C, along with the extensions I had added, that I didn't really have time to investigate C++; besides, my system was serving me well, and I had no problem producing programs that were, in every way, equal to or better than those produced by programmers who had switched to the C++ paradigm. 
 
Eventually, I decided that C++ was becoming such a big deal, I should find a good book on it, and study up a bit. What I found surprised me. Though I had been using a different programming environment (i.e., C, macro assembler, and my [many] macros and their support library), and though I was completely unfamiliar with the syntax, use, etc. of the ++ additions to C, what I found was that I had, in fact, been doing true object oriented progrmming for several years before C++ was even on the horizon.
 
I liked my implementation better, it seemed to me to be more efficient, and I was used to it, so, since there wasn't anything C++ would allow me to do that I hadn't already been doing for years, I never did make the switch from my own OO environment to C++. The only drawback was that other programmers had to be given about a 15 minute introduction to how the syntax of my system worked, in order to fully understand my code. Actually, my system was much more transperant than C++, so most programmers had no trouble reading, modifying, and maintaining my code, even without the formal intro. Most of them simply thought they were reading very tightly crafted, and efficient C code.
 
If you are truely interested in a high level programming career, I suggest you familiarize yourself with the Assembly Language for whatever archetcture is on the horizon (I don't think Intel x86 Assembly language will serve us much longer, what with the advent of RISC, etc.), learn the C language, and I mean *_**[COLOR=blue]LEARN[/COLOR]**_* it, in depth. Pay special attantion to things that you don't find in other languages (a FOR loop is a FOR loop is a FOR loop, and IF-THEN-ELSE constructs can be found in any language. The true power of C comes from structured DATA TYPES, its pointer DATA TYPE and all the things that spring from the extensive use of pointers, along with some of its other, more advanced DATA TYPES, and constructs. 
 
When interviewing programmer candidates, I used to ask them to bring in a sample of something they had written that was non-trivial, and which they felt they had done a good job of. Before getting much past the introductions, I would read through their header files (if there were no header files--if the code was one monolithic block, I was already done) for pointer declarations--especially for pointer to pointer declarations. If I found them, then I'd look through the code for the places where they were actually used, to see if the candidate really knew what pointers were for, or was just using them for some superficial task. 
 
I really didn't look at the rest of the code, except to scan it for comments and documentation. Some programmers think comments are a waste of time. I've watched so many of these guys sweat bricks, over code they themselves had written, when it came time to fix a bug, or change code to accomodate, for example, bigger hard drives (a constant challenge, back when I was in the game); trying to figure out, "Why'd I put that block of code there? What's it do? Do I really need to keep it? Why am I constantly checking this variable for a zero value?, etc., etc., etc." I kept statistics. Character for character, I usualy had 10% to 20% more comments, than code. But I never spent more than a minute, coming back up to speed, even on programs I'd written years ago, so I could make changes in minutes, instead of the days it often took for the "comments are a waste of time" crowd. 
 
Another admonishment I'd make is, DO IT NOW! With respect to error checking... Every programmer wants to see results; they want something on the screen that they can show off, ASAP. As a result many leave out the somewhat time consuming and tedious task of programming in error checking, thinking, "I'll come back and do it later--after I've got this piece working, so I can show it to my boss." Guess what? The error checking never goes in, or if it does, some of it gets overlooked, and the result is gnarly bugs that are unpredictable, hard to reproduce, and hard to find and fix. COMMENT, COMMENT, COMMENT, and ERROR CHECK, ERROR CHECK, ERROR CHECK! In a nut shell, that's the best advice I can give you on programming in general, regardless of language.
 
Also, learn the art of using pseudo-code, and "program" your project before you "code" it. Programming is the art (some still think it's a science--it's not, it's an art) of devising a plan for manipulating the input data so as to efficiently and accurately produce the required output. Coding, on the other hand, is translating that plan into a language that the computer (or assembler, or compiler, or interpreter) can understand. 
 
I used to tell programming teams "Don't assume you're going to code this in C, or C++, just create a program (with pseudo-code, flow charts, action diagrams--whatever works for you). Then, when the program is complete, we'll take a look at it and decide what language would lend itself best to coding this particular program. Sometimes [compiled] BASIC is actually a better choice than C, or Fortran. Sometimes you look at the program and see that you are so close to the heart of the machine so much of the time that, for efficiency's sake if nothing else, Assembly Language is the best choice." 
 
Do NOT confuse, as so many computer science students (and professionals) do, Programming with Coding. They are two completely separate diciplines, and not everybody who wants to be a computer scientist is good at both. Some can predictably come up with ingenious, imaginative, and efficient programs, but cannot code worth a damn. In other words, their exquisite programs fall into the bin of mediocher, because of less than expert coding. Others can produce a program that will work, but that is fraught with inefficiencies, redundancy, and confusing processes, but are brilliant, when it comes to turning a well written program into clean, readable, maintainable, upgradable code. 
 
Well, I'm sure I've gone well beyond what you expected from such a simple question, but after watching would-be programmers fall into the pit of despair, one after the other, because Universities *STILL* don't seem to know how to teach the art of creating computer programs. Most, if not all courses still do not differentiate between Programming and coding--starting right off with a textbook on coding in some language or other (usually, these days, it's C++), as if the code *was* the program. It's not. Not any more than the letters, numbers, etc., that the typesetter compiles to be sent to the printing press (they don't really do it that way any more, do they), to print a book are the same as the story. And, just as you can translate a story into other languages, so to can you code a computer program in more than one language, and get similar, in some cases, exactly the same results.
 
I don't know how serious a Computer Science student you are, or whether or not you are interested in some supplimental reading, but I'm going to end with a reading list, in two parts--programming, and coding. I will list the books in order of fundamental importance, so you can read as many or as few, in each category, as is your wont. Unless you intend on becoming a world-class programmer, or working for some high profile company writing data base engines, or specialized programs such as would be reauired by NASA and the like, I wouldn't expect you to read more than a couple of these books. If you read them all, then you will complete your education with a lot more insight into the *real* art of programming than 99% of successful CS students.
 
***[COLOR=green]_SUGGESTED_ _READING_ _REGARDING_ _THE_ _PROGRAMMING_ _ASPECT_ _OF_ _SOFTWARE_ _ENGINEERING:_[/COLOR]***
The Mythical Man Month - Frederick P. Brooks; Addison-Wesley, ISBN 0-201-83595-9
This book should be at the top of any programmer's reading list. It is a classic. Originally written in 1975, this foundation stone work was re-released as an Aniversary Edition in 1995--second edition. THough now 10 years out of date, the subject matter is eternal. Changes in technology, languages, etc., are not going to date this book. [COLOR=blue]HIGHLY RECOMMENDED[/COLOR]

[COLOR=black]Are Your Lights On?: How ToFigure Out What The Problem Really Is - Donald C. Gause and Gerald M. Weinberg; available from Amazon.com[/COLOR]
This is a delightful little book. It is an easy read, even entertaining, but it contains some of the most insightful reading on correctly assessing problems, I have ever come across. [COLOR=blue]HIGHLY RECOMMENDED[/COLOR]
 
Exploring Requirements: Quality Before Design - Donald C. Gause and Gerald M. Weinberg; available from Amazon.com
In my opinion, this is the Bible of 'getting it right the first time'. It's amazing how little attention some software houses give to project *requirements*. If your requirements document isn't correct, accurate, and clear, no matter how trivial the project may seem, it's likely to spiral out of control, sometimes to the point of having to start over. [COLOR=blue]I CANNOT RECOMMEND THIS BOOK HIGHLY ENOUGH![/COLOR]
 
Debugging The Development Proces - Steve Maguire; Microsoft Press; available from Amazon.com
A very worthwhile read, it includes a lot of aspects of developing a software product, most people, even experienced software engineers, fail to think about *before* the problems start to pile up. [COLOR=blue]RECOMMENDED[/COLOR]
 
Programming Productivity: McGraw-Hill Series in Software Engineering And Technology - Casper Jones; available from Amazon.com
This is very much a text book. No light reading here. But it's relatively small (5 X 7 inch format, 275 pages). This book deals with metrics usable for evaluating, as the title says, Programming Productivity. Only for those who are very serious about a top ranking position in the software industry. [COLOR=blue]RECOMMENDED FOR SERIOUS STUDENTS[/COLOR]
 
Handbook of Walkthroughs, Inspections, and Technical Reviews: Evaluating Programs, Projects, and Products - Daniel P. Freedman and Gerald P. Weinberg; available from Amazon.com
Written in a lighter style than Programming Productivity, this is still a non-trivial book, best suited for those who are aiming for a top position in the software industry. It is, however, packed with valuable information, useful to anyone who might find themselves on either side of a product evaluation, or technical review. In looking at my copy, I see I Highlighted about 15% of the text. [COLOR=blue]RECOMMENDED FOR SERIOUS STUDENTS[/COLOR]
 
Project Planning, Scheduling & Control: A Hands-On Guide to Bringing Projects In On Time and On Budget - James P. Lewis; 4th Edition available from Amazon.com
I have so many bookmarks in this book, it's hard to page through it. Though not for the casual programmer, this book is a Gold Mine of information for anyone who ever expects to be in charge of any [kind of] project or workgroup. It's principles apply to the art (some would say science) of project control, be it a software development project, or the building of a bridge or skyscraper, to the launching of a new business. Project Management is a field of study unto itself, and those who master it will have a great advantage over the also-rans. [COLOR=blue]RECOMMENDED READING, REGARDLESS OF DISIPLINE[/COLOR]
 
***[COLOR=#008000]_SUGGESTED_ _READING_ _REGARDING_ _THE_ _CODING_ _ASPECT_ _OF_ _SOFTWARE_ _ENGINEERING:_[/COLOR]***
Essential C++ - Stanley B. Lipman: C++ In-Depth Series, Bjarne Stroustrup; available from Amazon.com
Though any good introductory book on C++ would do here, this one covers all the bases, and is edited by Bjarne Stroustrup, the father of C++, making it most assuredly authoritative, and accurate. [COLOR=blue]RECOMMENDED[/COLOR]
 
Advanced C - John Thomas Bery, The Waite Group; available from Amazon.com
Though this book may seem dated, it's not. The fundamentals covered in this book have not changed, and will not, as long as there's a "C" in C++ (or C+++, or C+-+, ...). There are plenty of code examples throughout the book, and a section at the end on the design and implementation of a small data base manager, complete with code. [COLOR=blue]HIGHLY RECOMMENDED[/COLOR]
 
C Database Development, _2nd_ _Edition_ - Al Stevens, MIS Press, ISBN 1-55828-136-3
This book leads you, step by step, through the development, coding, and implementation of a non-trivial database manager. I'm tempted to say that half of what I know about programming that made me stand out from all the rest (my programming was often related to National Security, and my programs have been in use by Governments, Intelligence agencies, the Military, Law Enforcement agencies, and major industrial companies around the world), I learned from this one book. It is packed with code examples, and does, in fact, walk you through the design, coding, and implementation of a potentially very powerful Database Manager. The author leaves it to the reader to deal with the User Interface (though a crude but usable one is included, so it can be used "right out of the box"), but the engine developed by following this book is non-trivial, indeed. It has roughly the indexing, cross-rferencing, storage and retrieval capabilities as the long-time standard Fox-Pro--the database manager the US Military depends on for combat deployment. [COLOR=blue]I CANNOT RECOMMEND THIS BOOK HIGHLY ENOUGH (unfortunately, it's getting hard to find)[/COLOR]
 
And last, but not least - The C++ Programming Language: Special 3rd Edition - Bjarne Stroustrup, the Creator of C++; available from Amazon.com
This is it! The pentultimate reference on the C++ language, from the man himself. There is nomore authoritative reference than this one, period. Maybe not so much a book to be read, as one to keep on your shelf, as a reference. However, reading this book will tell you pretty much everything there is to know about C++. I didn't put this higher up in the list, because, despite its nature as the absolute be all, and end all in books on C++, it is not a trivial read. Some of the lighter reading should provide a less demanding introduction to the language. This book has many many code snippets in it, as examples, but no complete programs. It's also somewhat textbookish, in that it contains exercises, at appropriate points throughout the book. This IS the C++ Bible. [COLOR=blue]VERY HIGHLY RECOMMENDED[/COLOR]
 
I've probably overwhelmed you--I tend to do that, especialy regarding subjects I am passionate about, and I am passionate about the C language (not so much the ++ part, but that's just me). Elegance is the word that I think best describes the language, and any artfully code written in this language.
 
Good luck in your studies.

---

### Post by nvteighen on 2008-08-01
> **Syndacate said:**
> 


Ah, gotcha, so it's basically so we can save time by only compiling one part instead of the entire thing.

So two questions about that.

A)  Say we have a.o, b.o, both linked to myprog.  Say we create a 3rd source file, and compile it to c.o, do we have to re-link all of them by typing:

```
g++ a.o b.o c.o -o myprog
```

or can we just link them by typing:

```
g++ c.o -o myprog
```

The second won't work because you're telling to create an executable only from c.o, which may lead you into undefined reference errors (= "I don't know where function x is", because it is in a.o, for example). So, yes, you have to re-link all of them.

> B)  After the objects are linked to the program, they don't seem to be necessary anymore.  So would it be fair to say that "linking" them kind of "inserts" the objects into a file executable?  As in "myprog" is made up of a.o, b.o, and c.o, combined?

I believe the linker doesn't insert anything, but actually links. No, I'm not kidding you: your question makes sense and I also had it some time ago... But, the issue is that if you "reinserted" c.o, you would have two versions of the same object file inside the executable, something that would surely go wrong. I'm pretty sure the executable doesn't keep any information of how many/which object files there were at the beginning, so anything that gets "inside" will unrecoverable (in an easy way... a dissasembler maybe can...?).


> What thing I'm confused a bit on, if I'm understanding dynamic libraries vs static libraries, aren't MOST programs going to have static libraries, if they have dynamic libraries?  'Cause there's always going to be a few files that aren't shared, but are more specific to that program, which wouldn't be in the dynamic libraries, correct?

Exactly. But don't confuse yourself: a static library (.a) is only an archive file containing a lot of .o files... like a .tar.gz or .zip, but not compressed. You can even extract them!

```

mkdir libm_extracted && cd libm_extracted
ar x /usr/lib/libm.a

```

(This will extract the math library into a newly created folder "libm_extracted". To remove it, just delete the folder)

And you can create an .a file with whatever data you want... but nowadays, people prefer .tar files for that. Read "man ar"... ar is the archiver that creates .a files.

So, in conclusion whatever .o files you use will act as static libraries, no matter if written by yourself or by someone else. So, if you write some functions for a program and then you see they could be useful for another one, you just link to that object file... and violà, precious developing time saved!

> **bilijoe said:**
> C++ ***_[COLOR=blue]IS[/COLOR]_*** C. (...)

(Trimmed for obvious reasons...)

I prefer C over C++, it's elegant and gives you enough hardaches because of that... In some way, it forces you to elegancy and order to build a good program. And OOP can be achieved in C, like GTK+ does and other not-so-esoteric libraries.

But: to learn C, and with little (or zero) previous programming experience may be really hard. C is a language whether you learn it seriously or you just don't learn it, and it doesn't forgive you when something goes wrong.

And pointers... are just a variable holding a memory address, not a magic wand. Of course, you can use it for stupid things or in an interesting way, like anything in any other programming language. The "magic" of C, in my short experience with it (some months), is actually it's overwhelming simplicity, which allows its extensibility.

---

### Post by dribeas on 2008-08-01
> **LaRoza said:**
> C++ was once an extension, now it is no longer that (it used to be a preprocessor for C)

To be precise, C++ was designed as a language in itself, never as an extension of C (ask Stroustrup). Some of the initial implementations of C++ where language translators to C, just as there are language translators between all .NET languages. That does not mean that C# is an extension of VB (just to use a simple example, but take any other two languages for which translators exists: Python-Java, Ruby-Java).

   David

From 'The Design and Evolution of C++', Bjarne Stroustrup, Chapter 3:
> ``I picked C++ because it was short, had nice interpretations, and wasn't of the form "adjective C."' In C, ++ can, depending on context, be read as "next," "successor," or "increment," though it is always pronounced "plus plus." The name C++ and its runner up ++C are fertile sources for jokes and puns -- almost all of which were known and appreciated before the name was chosen. The name C++ was suggested by Rick Mascitti. It was first used in December of 1983 when it was edited into the final copies of [Stroustrup,1984] and [Stroustrup,1984c].

The "C" in C++ has a long history. Naturally, it is the name of the language Dennis Ritchie designed. C's immediate ancestor was an interpreted descendant of BCPL called B designed by Ken Thompson. BCPL was designed and implemented by Martin Richards from Cambridge University while visiting MIT in the other Cambridge. BCPL in turn was Basic CPL, where CPL is the name of a rather large (for its time) and elegant programming language developed jointly by the universities of Cambridge and London. Before the London people joined the project "C" stood for Cambridge. Later, "C" officially stood for Combined. Unofficially, "C" stood for Christopher because Christopher Strachey was the main power behind CPL.''

---

### Post by pmasiar on 2008-08-01
> **Syndacate said:**
> Alright, I'll head onto python when I'm done with this C++ book,

In some controlled experiments in high school teaching, learning Java **after** Python was more productive: because Python is less confusing, so you can learn basic language-independent concepts easier without clouding it in java specific syntax vinegar. As C++ is more complex than java, this effect could be even more pronounced. Just FYI.

> Though now I'm wondering if I should have took a look at C instead.

To have better idea what is happening down at CPU level. 

> but then why is python so good if that's a higher programming language as well?

Even if python code executes slower, you can get to valid program faster. If you run your program not often (say less than each minute), you may not care. Also, Python is popular in apps where CPU performance is not the bottleneck (that is, majority of apps), like desktop apps (mostly waiting for input of user), web apps (limited by database response time).

---

### Post by Syndacate on 2008-08-01
> **pmasiar said:**
> In some controlled experiments in high school teaching, learning Java **after** Python was more productive: because Python is less confusing, so you can learn basic language-independent concepts easier without clouding it in java specific syntax vinegar. As C++ is more complex than java, this effect could be even more pronounced. Just FYI.

> Though now I'm wondering if I should have took a look at C instead.

To have better idea what is happening down at CPU level. 

> but then why is python so good if that's a higher programming language as well?

Even if python code executes slower, you can get to valid program faster. If you run your program not often (say less than each minute), you may not care. Also, Python is popular in apps where CPU performance is not the bottleneck (that is, majority of apps), like desktop apps (mostly waiting for input of user), web apps (limited by database response time).

Okay, so basically python is more productive, C is faster, yet more code?

It seems that's the trade off on lower level vs higher level languages, as described here.

Gotcha, yeah, guess it makes sense where other things (such as a database) have to catch up, since the speed differences won't matter as much.

[quote=nvteighen]The second won't work because you're telling to create an executable only from c.o, which may lead you into undefined reference errors (= "I don't know where function x is", because it is in a.o, for example). So, yes, you have to re-link all of them.[/quote]

Alright.

[quote=nvteighen]I believe the linker doesn't insert anything, but actually links. No, I'm not kidding you: your question makes sense and I also had it some time ago... But, the issue is that if you "reinserted" c.o, you would have two versions of the same object file inside the executable, something that would surely go wrong. I'm pretty sure the executable doesn't keep any information of how many/which object files there were at the beginning, so anything that gets "inside" will unrecoverable (in an easy way... a dissasembler maybe can...?).[/quote]

Right, so since you're able to remove the object files afterwards, I think it's fair to say it "combines" them when you "link" them?

I mean "link" implies that the object file needs to exist for the program to run, but it doesn't seem like that's the case, it seems like they're just needed for the executable's compilation.

[quote=nvteighen](This will extract the math library into a newly created folder "libm_extracted". To remove it, just delete the folder)

And you can create an .a file with whatever data you want... but nowadays, people prefer .tar files for that. Read "man ar"... ar is the archiver that creates .a files.

So, in conclusion whatever .o files you use will act as static libraries, no matter if written by yourself or by someone else. So, if you write some functions for a program and then you see they could be useful for another one, you just link to that object file... and violà, precious developing time saved![/quote]

Gotcha.

[quote=bilijoe][/quote]

Guess you got a good point there, well more than one good point.  I was focusing a lot on syntax differences 'n the like when I should have been looking for differences in data structures.

Ha, I'm one of those guys that doesn't like lots of comments, only a few, to keep it knowing what's going on.

I don't think I'm good enough at the actual data structures and coding yet to focus on productivity of programming, y'know?  I think that'll come later, when I get more basic programming under my belt.

It seems C is a necessary language to learn, I mean lots of applications are written in C (I thought more were written in C++, but apparently I was wrong), I even believe Linus originally designed the linux kernel in C.  The only reason I picked up this C++ book was that I heard it had a lot of similarities to Java (which I know fairly well), and wanted to pick up the syntaxing/design of C++ before moving onto a completely different language.  Though it seems now I have to focus on the datastructure differences between languages, not just the syntaxing.  I never picked up this introductory book to be a C++ master, just to get a basic understanding of the differences vs Java.

So I'm almost done with this book - now the question is, should I look at python next, or C?  Obviously they both have a solid place in the Linux world, IMO it seems that python is not used as much in Windows, which states something (not exactly sure what), but I was kind of going for languages that aren't dependent on OS, so they could be run on Win or *nix, like Java...obviously Java's different because it runs inside a VM, but you get what I mean, Java is universal.

So from what I'm getting out of this:
> Python can turn code into a program very fast, it's a higher level, slower, but more efficient programming language.
> C on the other hand is more direct, faster, but will require more code, though somebody brought up a point that it's amazingly simple.

If I decide to look at higher level languages first (and the general consensus seems to be I should look at C, first), should I look at Ruby or Python first?  It seems most pple say Python, but I'm still having trouble telling the difference in their target goal.

---

### Post by pmasiar on 2008-08-01
Very good post (even if I disagree with some parts :-) ). bilijoe, consider splitting it to parts and posting them to relevant parts of FAQ, it will be forgotten here. Or maybe this post and surrounding discussion could be moved somewhere to FAQ?

> **bilijoe said:**
> If you are truely interested in a high level programming career,
I suggest you familiarize yourself with the Assembly Language

Today, C plays the role in architecture-independent ASM for most "serious" programmers. But many people who use programming are not "serious" programmers, thay are experts in own area who use programs to solve own problems (without need to explain "serious" programmer what the problem is, and what approaches are used)

> Also, learn the art of using pseudo-code, 

Some people say that dynamically typed language like Python is "executable pseudocode" :-)

> Programming is the art (some still think it's a science--it's not, it's an art) 

Science has laws - programming has only "rules of thumb". But art is based on the opinions only, does not have objective measure of anything, programming results can be measured. Programming is a craft, engineering discipline: use science where you have them, rules of thumb and experience where you can, and use trial/error on the rest (and design your system to be as fault-tolerant as you can). Craft is learned by observing masters and doing as they do.

Good design can be beautiful (Golden Gate Bridge was designed sturdy, and happened to be beautiful) but it is not major goal as in art.

> Universities *STILL* don't seem to know how to teach the art of creating computer programs. 

... because programming is a craft, not science? :-)

I browsed over recommended books: requirements to design to code is [http://en.wikipedia.org/wiki/Waterfall_model](http://en.wikipedia.org/wiki/Waterfall_model) , considered obsolete. More modern approach is [http://en.wikipedia.org/wiki/Agile_software_development](http://en.wikipedia.org/wiki/Agile_software_development)  which is iterative and incremental (and test driven).

Seems that I am little younger than bilijoe: old enough to appreciate the info, but young enough to see where "state of the art" changed since.

---

### Post by pmasiar on 2008-08-01
> **Syndacate said:**
> Java is slower than C++, and that a higher level programming language such as Python would run slower, yet be faster to write.  So I guess that begs a question of:  *Do you have more control with a lower level programming language?*

Refer to my question above - is it fair to say that since python is a higher level programming language, you don't have the control you do with some of the lower level programming languages such as C, C++, and Java?

It depends on the language: **with more power comes more responsibility** :-) [http://en.wikipedia.org/wiki/Forth_%28programming_language%29](http://en.wikipedia.org/wiki/Forth_%28programming_language%29) is a language which gives you more power than most other high-level languages - for the price of programmer being responsible for lots of checking which is done by system in other languages. 

Python is interesting for couple reasons:
- seems to have good balance between language expresiveness, type flexibility, and rich libraries: Perl has complex syntax because makes part of language stuff which might be better as library (like regular expressions), which complicates further language development
- is object oriented but not object-obsessed as java is (some stuff is simpler to understand as generic functions - and not every stupid thing has to be class)
- Python is first language which focuses on communication between humans, on readability of the code. Standard code structure is part of the syntax, and late binding and dynamic typing make metaprogramming simpler, even if it makes CPU work harder.

---

### Post by slavik on 2008-08-01
One thing that you have to keep in mind is when building a large software system, you have to decide how the various parts will communicate with one another (how the data will flow through the program). Sometimes, late changes to the specification may make your pipeline inneficient.

Agile development is good for the "release early, release often" mantra (to keep your project in public view).

One thing you still have to do is plan. Lack of planning cannot be mitigated by any amount of code additions, because if you try to do it, you will get an ungodly mess that nobody will understand.

---

### Post by Syndacate on 2008-08-01
> **pmasiar said:**
> Very good post (even if I disagree with some parts :-) ). bilijoe, consider splitting it to parts and posting them to relevant parts of FAQ, it will be forgotten here. Or maybe this post and surrounding discussion could be moved somewhere to FAQ?



Today, C plays the role in architecture-independent ASM for most "serious" programmers. But many people who use programming are not "serious" programmers, thay are experts in own area who use programs to solve own problems (without need to explain "serious" programmer what the problem is, and what approaches are used)

> Also, learn the art of using pseudo-code, 

Some people say that dynamically typed language like Python is "executable pseudocode" :-)

> Programming is the art (some still think it's a science--it's not, it's an art) 

Science has laws - programming has only "rules of thumb". But art is based on the opinions only, does not have objective measure of anything, programming results can be measured. Programming is a craft, engineering discipline: use science where you have them, rules of thumb and experience where you can, and use trial/error on the rest (and design your system to be as fault-tolerant as you can). Craft is learned by observing masters and doing as they do.

Good design can be beautiful (Golden Gate Bridge was designed sturdy, and happened to be beautiful) but it is not major goal as in art.

> Universities *STILL* don't seem to know how to teach the art of creating computer programs. 

... because programming is a craft, not science? :-)

I browsed over recommended books: requirements to design to code is [http://en.wikipedia.org/wiki/Waterfall_model](http://en.wikipedia.org/wiki/Waterfall_model) , considered obsolete. More modern approach is [http://en.wikipedia.org/wiki/Agile_software_development](http://en.wikipedia.org/wiki/Agile_software_development)  which is iterative and incremental (and test driven).

Seems that I am little younger than bilijoe: old enough to appreciate the info, but young enough to see where "state of the art" changed since.

Yeah, we learned about that stuff (the first one) in class, 'cept they called it the software life-cycle.

I get what you/him mean by "*make the idea first, then execute it in code*" - I also get why Python is often referred to as "*executable pesudo code*" - They teach us to use pseudo code - and I often I do, I just don't write it down...some (teachers) claim there's a difference, not me, I get an idea stored in my head and it's enough to work off of that idea.

[quote=pmasiar]It depends on the language: with more power comes more responsibility  [http://en.wikipedia.org/wiki/Forth_%...ng_language%29](http://en.wikipedia.org/wiki/Forth_%...ng_language%29) is a language which gives you more power than most other high-level languages - for the price of programmer being responsible for lots of checking which is done by system in other languages.

Python is interesting for couple reasons:
- seems to have good balance between language expresiveness, type flexibility, and rich libraries: Perl has complex syntax because makes part of language stuff which might be better as library (like regular expressions), which complicates further language development
- is object oriented but not object-obsessed as java is (some stuff is simpler to understand as generic functions - and not every stupid thing has to be class)
- Python is first language which focuses on communication between humans, on readability of the code. Standard code structure is part of the syntax, and late binding and dynamic typing make metaprogramming simpler, even if it makes CPU work harder.[/quote]

Makes sense.

[quote=slavik]One thing that you have to keep in mind is when building a large software system, you have to decide how the various parts will communicate with one another (how the data will flow through the program). Sometimes, late changes to the specification may make your pipeline inneficient.

Agile development is good for the "release early, release often" mantra (to keep your project in public view).

One thing you still have to do is plan. Lack of planning cannot be mitigated by any amount of code additions, because if you try to do it, you will get an ungodly mess that nobody will understand.[/quote]

True.

I'm still stuck on what I should turn to after I finish this book, if anybody has any suggestions.

---

### Post by mssever on 2008-08-01
> **Syndacate said:**
> If I decide to look at higher level languages first (and the general consensus seems to be I should look at C, first), should I look at Ruby or Python first?  It seems most pple say Python, but I'm still having trouble telling the difference in their target goal.
I'm one of the few Ruby users around here. Ruby and Python both occupy a similar niche. Here are some random things I like about Ruby:

[LIST]
[*]Scoping is determined by variable name, so there's no confusion.
[*]The way Ruby uses blocks. ```
File.open('somefile') do |file|
  file.each_line { |line| puts line.gsub(/python/i, 'Ruby') }
end
# the file is automatically closed
``` Python's new with statement helps Python catch up in this area.
[*]Ruby consistently uses OO idioms, instead of hiding OO in magic methods (something.length vs. len(something)).
[*]Ruby's core and standard library API documentation format
[*]Syntax-level regexp support
[*]The unless statement
[/LIST]
Random things I dislike about Ruby:

[LIST]
[*]You have to [FONT=Courier New]require 'English'[/FONT] to use sensible names for some things. What does $/ mean?
[*]Too many globals
[*]No name spaces
[*]Array#[] and Hash#[] return nil when you access an invalid index/key. They should raise exceptions. Array#fetch and Hash#fetch are the workarounds.
[*]While the documentation format is great, sometimes the documentation itself isn't so great. Ruby's docs are particularly unfriendly to beginners.
[*]Small standard library
[/LIST]
Random things I like about Python:

[LIST]
[*]Name spaces
[*]Huge, high quality standard library
[*]List comprehensions
[*]Python's use of whitespace
[*]```
from __future__ import braces
```
[*]docstrings
[*]Large number of users
[/LIST]
Random things I dislike about Python:

[LIST]
[*]Python's scoping rules
[*]```
", ".join([1, 2, 3, 4])
```join should be a method of iterable objects, not strings.
[*]Python's inconsistencies. This is a little unfair, though, because Ruby has different inconsistencies; they just don't bother me as much, for some reason.
[*]The requirement to explicitly provide the first argument in methods, despite the fact that it's called self by vary strong convention, and despite the fact that method calls handle that implicitly. By the way, the whole "explicit is better than implicit" mantra is rather silly. There are a number of things that Python does implicitly and Ruby does explicitly. And vice versa.
[/LIST]
You may notice that most of these things are rather minor in the grand scheme of things. My preference for Ruby ultimately comes down to the fact that it feels more natural to me. Your experience may vary. Read introductory material on both, and choose (or learn both).

---

### Post by nvteighen on 2008-08-01
I'll give you **my** personal views on C and Python. 

First, some background about me :) : I've been learning C since some months ago, coming from BASIC like languages and some Javascript + a failed attempt at C++. It's currently my preferred language. In the other hand, I've been learning some Python for a week, but not as the usual beginner, following a tutorial, but just experimenting with its most particular features in the shell... and today I wrote my first Python program.

**C**
I love it because it's minimalist (what I meant for "overwhelming simplicity"). The language doesn't include any feature except loops, conditionals, some very basic data types (based on lengths in bytes, not in what the content is... keep that always in mind!)... but it has the structure to make the language grow to whatever layer of abstraction.

That minimalism gives a lot of freedom. The C philosophy equals the UNIX philosophy (C and UNIX were developed side-by-side by the same people), where simplicity is the rule and everything is composed by small pieces interacting together. You are able to plug anything in, and also to unplug it if you don't like it. Do you like linked lists? You can either create it or use a library for that. Do you want to connect to the internet? Link to a socket library or do it by yourself!

But, that freedom comes from C being a very low-level language. So, anything has to be done by hand and that means a lot of "auxiliary" work, In other words, you'll spend more time in implementing a data type and its assoicated functions just to end up writing a tiny main() function that uses the data type and spits a result in a few lines of code. I like that kind of "backstage" programming, but other people, specially those used to create applications, may hate it.

So, knowing about data structures is a must in C. Without them, you'll be probably lost.

Also, that minimalism comes to the extreme point where you have to link to a library just to print "Hello World!" to the screen. I'm not kidding: printf() is not built into the language, but it's inside a library (the Standard Library, which is always linked automatically...). Also, you have to manage memory by hand, which can lead to dissastrous results (memory leaks, memory corruption and system complains)... and of course, through a library.

So, go for C if you want something challenging to create things from the very bottom. 

**Python**
It's simple in the "other sense": intuitive, has a shell where you can play with the language, portable and has a lot of stuff built into the language. You have lots of tools, data types and functions you'll probably never use so you just code the problem and not that much "backstage" work. But the best is that all that is correctly connected into a system where you can reuse parts in a very coherent way. So, if you want to put a certain kind of list here and then you know that a function accepts that kind of list, just use it and it will most probably work.

And, you can still extend the language using other people's "modules". Or create your own; so, it gives you also freedom to do what you want...

..but, I find it a bit overwhelming and confusing... for example, you can find out the length of "Hello World!" with "Hello World!".__len__()... everything is an object and will work that way, so in theory you could call a constructor for "Hello" ("Hello".__init__())... the question is: for what reason?? And some functionality is certainly duplicated: len("Hello World!") will also give you the string length. There are some essential features I really don't know how a beginner with no programming experience could manage (why can I return a string and apply the string's method to that function?).

Of course, it's a great language for beginners and to do quick job... and also applications (see pmasiar's sig for GameBaker). It gives you the power of having a lot of tools, and if you learn them, you'd probably combine them to an interesting result. You'll like the language if you like to work on a good base of already existing tools.

So, in summary:
If you're a paranoic minimalist that wants to do all by hand, like me: C
If you're not the above: Python.
If you're smart and love learning: both! (why not?)

---

### Post by pmasiar on 2008-08-01
> **mssever said:**
> Ruby and Python both occupy a similar niche.

Not exactly. Although both are flexible dynamically typed languages (and more fun to program in than say Java), Ruby is almost exclusively used for web apps (with excellent and innovative Rails framework, since replaiced in Python (Django and TurboGears) and even in Java (Stripes)). Python is widely popular outside of web app, has even SciPy conference separate from PyCon.

> Ruby consistently uses OO idioms, instead of hiding OO in magic methods (something.length vs. len(something)).

len(something) is generic function, more "obvious" for beginner, IMHO.

> Syntax-level regexp support

that is influence of Perl - and too much features pulled into syntax stifle both language and library development.

One strong argument for Python is support from huge company: Google. Python is here to stay :-)

---

### Post by pmasiar on 2008-08-01
Re-reading Python FAQ:

> **mssever said:**
> 
Random things I dislike about Python:
```
", ".join([1, 2, 3, 4])
```join should be a method of iterable objects, not strings.

[4.8   Why is join() a string method instead of a list or tuple method?](http://www.python.org/doc/faq/general/#why-is-join-a-string-method-instead-of-a-list-or-tuple-method)

> The requirement to explicitly provide the first argument in methods, despite the fact that it's called self by vary strong convention,

[4.5   Why must 'self' be used explicitly in method definitions and calls?](http://www.python.org/doc/faq/general/#why-must-self-be-used-explicitly-in-method-definitions-and-calls)

---

### Post by slavik on 2008-08-01
why is join part of the string object in Python? Simply because strings in Python are immutable, just like Java. Hence, the joining of strings works a bit differently than for lists ... (since a new object must be created, whereas with lists, one of the lists can be modified).

IMO, each class should have it's own join method (just how every object has it's own toString() implicitly) and the generic join() would simply look at the types of objects to join and call the class' join method unless they are different (then it has to convert them to the same type/class))

as for regexp as part of the core language stifling development, I have to disagree on this point. We can then argue that arithmetic operations as part of the language also stifle development of the language/libraries (in LISP, arithmetic operations are functions).

---

### Post by Syndacate on 2008-08-01
I think after reading your responses C would be better for me.

I'm not really a minimalist nutjob, but that's kinda the way I learned with Java.  I mean yeah, some refer to Java as doing most of the work for you, such as memory management and such.  Though Java is a very rigid, structured, non-forgiving language.  I **LOVE** its syntaxing, like the way it calls methods stringVarName.length() - but then again, I don't really have any experience with any other languages, so I guess I have nothing to compare it to.

Though I'm not much of a web designer, I plan on learning PHP at some point b/c PHP scripts come in mad handy when trying to do some trivial web things, but when I make webpages, I do it old fashioned style (gedit + refresh on a browser).  Though with Java I do the opposite (I use an IDE called Eclipse).  So I think it's fair to say I can rule out perl or Ruby anytime in the near future (I don't have the artistic skill needed for web design).  So then it just becomes the original, C or Python.

I think C would be better to learn, and then from there, once I got good implementation of it, move onto Python...I think...I'm not sure if that's the smart way to do it, anybody have input on how I should approach that?

Like I said, the only reason I'm doing a quick book on C++ (it's a beginners book) is because it's similar to Java, and I just wanted to get the syntaxing & data structures down, as I **incorrectly thought** it was often used.

Like I'm about to make a very trivial program (after I take a 30 minute nap :-D), and though the program is very trivial (basically a small executable database) I'm going to make it in Java, because if I make it in C++, then compile it (I'm not letting the source go free), then it'll be compiled for linux, and I need this to heavily work on Windows machines, as well as Macs, so the Java VM will come in handy here.  The lack of compatibility kinda annoys the piss out of me.  Not everybody has python installed, that's for damn sure.

<!------------->

For linux it's easy as cake, because all the libraries are packaged and readily available via aptitude.  So it's very easy to make something in any language due to the commonality of the libraries.

Though if it's going to be distributed outside of the GNU/Linux scene, more targeted at Windows users, what should I do?  I mean I know C++ is pretty good in Windows, so is C, so is Java.  Don't know how C/C++ is for Mac, but Java is good there, too.

I'm thinking Java or C++ - I just realized for C++ I can still copy the source code into dev bloodshed C++ and compile it there for windows users (**** mac users).  So is that my best bet?

---

### Post by days_of_ruin on 2008-08-01
Whats with all the talk about Qt?
I don't think it would be very fun looking at toolkit code.
Find something higher level.

---

### Post by LaRoza on 2008-08-01
> **pmasiar said:**
> 
One strong argument for Python is support from huge company: Google. Python is here to stay :-)

And MS to a degree.

> **days_of_ruin said:**
> Whats with all the talk about Qt?
I don't think it would be very fun looking at toolkit code.
Find something higher level.
QT libraries can take the place of all C++ standard libs and the STL and provide GUI, networking and other functions I believe.

---

### Post by days_of_ruin on 2008-08-01
> **Syndacate said:**
> I think after reading your responses C would be better for me.

I'm not really a minimalist nutjob, but that's kinda the way I learned with Java.  I mean yeah, some refer to Java as doing most of the work for you, such as memory management and such.  Though Java is a very rigid, structured, non-forgiving language.  I **LOVE** its syntaxing, like the way it calls methods stringVarName.length() - but then again, I don't really have any experience with any other languages, so I guess I have nothing to compare it to.

Though I'm not much of a web designer, I plan on learning PHP at some point b/c PHP scripts come in mad handy when trying to do some trivial web things, but when I make webpages, I do it old fashioned style (gedit + refresh on a browser).  Though with Java I do the opposite (I use an IDE called Eclipse).  So I think it's fair to say I can rule out perl or Ruby anytime in the near future (I don't have the artistic skill needed for web design).  So then it just becomes the original, C or Python.

I think C would be better to learn, and then from there, once I got good implementation of it, move onto Python...I think...I'm not sure if that's the smart way to do it, anybody have input on how I should approach that?

Like I said, the only reason I'm doing a quick book on C++ (it's a beginners book) is because it's similar to Java, and I just wanted to get the syntaxing & data structures down, as I **incorrectly thought** it was often used.

Like I'm about to make a very trivial program (after I take a 30 minute nap :-D), and though the program is very trivial (basically a small executable database) I'm going to make it in Java, because if I make it in C++, then compile it (I'm not letting the source go free), then it'll be compiled for linux, and I need this to heavily work on Windows machines, as well as Macs, so the Java VM will come in handy here.  The lack of compatibility kinda annoys the piss out of me.  Not everybody has python installed, that's for damn sure.

<!------------->

For linux it's easy as cake, because all the libraries are packaged and readily available via aptitude.  So it's very easy to make something in any language due to the commonality of the libraries.

Though if it's going to be distributed outside of the GNU/Linux scene, more targeted at Windows users, what should I do?  I mean I know C++ is pretty good in Windows, so is C, so is Java.  Don't know how C/C++ is for Mac, but Java is good there, too.

I'm thinking Java or C++ - I just realized for C++ I can still copy the source code into dev bloodshed C++ and compile it there for windows users (**** mac users).  So is that my best bet?

I think it makes sense to learn easier languages first (Python) before
learning the harder ones(C,C++,etc)

---

### Post by days_of_ruin on 2008-08-01
> **LaRoza said:**
> And MS to a degree.


QT libraries can take the place of all C++ standard libs and the STL and provide GUI, networking and other functions I believe.

I got the impression that he would be looking at the actual qt source code.
Not programs that use it.Maybe I am wrong tho.

---

### Post by imdano on 2008-08-01
> **Syndacate said:**
> Like I said, the only reason I'm doing a quick book on C++ (it's a beginners book) is because it's similar to Java, and I just wanted to get the syntaxing & data structures down, as I **incorrectly thought** it was often used.Hmm, if I understand you correctly, you think C++ isn't used very often?  [That's not exactly true,](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html) though its usage seems to be on the decline.  I wouldn't expect it to become obsolete anytime soon, either way.

---

### Post by mssever on 2008-08-01
> **pmasiar said:**
> Re-reading Python FAQ:I'm aware of the Python FAQ. But just because Python does things a certain way doesn't mean I have to like it. Sometimes there are several reasonable options, and different people prefer different options.


> [4.8   Why is join() a string method instead of a list or tuple method?]("http://www.python.org/doc/faq/general/#why-is-join-a-string-method-instead-of-a-list-or-tuple-method")If that's what makes the most sense for Python developers, fine. But I should point out  that Ruby's approach is equally valid. In Ruby, you ask an enumerable object to turn itself into a string with some other string in between the elements. So this is simply a special case of casting the object to a string (e.g., Array#to_s). And I think Ruby's approach makes more sense semantically, though others obviously disagree.

> [4.5   Why must 'self' be used explicitly in method definitions and calls?]("http://www.python.org/doc/faq/general/#why-must-self-be-used-explicitly-in-method-definitions-and-calls")Again, there's a different approach, dictated by differences between Python and Ruby. Because Ruby uses explicit scoping, there's little ambiguity. And in the few ambiguous cases, you can explicitly name self (which is normally called implicitly). Incidentally, AFAIK ambiguous cases in Ruby and Python are similar:

[LIST]
[*]Ruby: If you have a method and local variable with the same name, Ruby will assume you meant the local variable. You can call self.method_name to disambiguate. This is also necessary if a method name is the same as a keyword (e.g., to get a reference to the current class, you have to call self.class, because class is a keyword).
[*]Python: If you have an instance variable that shares a name with a method, you have to disambiguate. Actually, I don't know if this is even legal in Python.
[/LIST]
 
> **slavik said:**
> why is join part of the string object in Python? Simply because strings in Python are immutable, just like Java. Hence, the joining of strings works a bit differently than for lists ... (since a new object must be created, whereas with lists, one of the lists can be modified).But that's just a design decision. Ruby strings are immutable, too.

> IMO, each class should have it's own join method (just how every object has it's own toString() implicitly) and the generic join() would simply look at the types of objects to join and call the class' join method unless they are different (then it has to convert them to the same type/class))That's like Ruby, except there's no need for a generic join method. Just use duck typing and call join directly. Works great in Ruby.

> as for regexp as part of the core language stifling development, I have to disagree on this point. We can then argue that arithmetic operations as part of the language also stifle development of the language/libraries (in LISP, arithmetic operations are functions). The thing is, regexps are so common, that it makes for more readable code to have syntax-level support. Look at all the situations that benefit from syntax-level support (using overly-simple regexps for clarity of illustration):
```
string.gsub /Python/, 'Ruby'
if string =~ /Ruby/
  # do something
end
case some_object
  when 1
    do_something
  when 'foo'
    do_something_else
  when /Ruby/
    try_again
end
```These situations require a bit more code in Python and would be harder to read (even if Python did have a case statement).

EDIT: Don't  take this as a criticism of Python. It's not. It's just a statement of differences. Python and Ruby have different philosophies.

---

### Post by slavik on 2008-08-02
either way, to know how software interracts with the OS, everytime you do malloc in C (new calls malloc), you are interracting with the OS. printf and scanf also make system calls for I/O.

---

### Post by Syndacate on 2008-08-02
> **days_of_ruin said:**
> I got the impression that he would be looking at the actual qt source code.
Not programs that use it.Maybe I am wrong tho.

Yeah, that's the impression I got from what he said.

[quote=imdano]Hmm, if I understand you correctly, you think C++ isn't used very often? That's not exactly true, though its usage seems to be on the decline. I wouldn't expect it to become obsolete anytime soon, either way.[/quote]

I wouldn't expect it to become obsolete anytime soon either, though I thought a lot more was written in C++ than it actually is, and most programs that I found written in C++ (or Java for that matter) have a second, third, etc. language - they're not just by themselves.

@mssever
So you're obviously a Ruby man - but since I won't (at least initially) be aiming at web apps, Python would be the better choice, or if you were me, would you still have a look at Ruby?

PS @ ALL:
A lot of talk about scope in here - I've dealt with the strict scope in Java - SCOPE BLOWS.  All variables should be global, and static, they should be able to be referenced from anywhere in the program.

You have no idea how many issues I've had relating to scope, or an extra class I had to create to pass it an object just so the variable would be in scope.  God I hate scope.  There's enough letter/number permutations to use more than one variable!

---

### Post by Jessehk on 2008-08-02
> **mssever said:**
> 
[*]No name spaces


That's not entirely true.

```

module Foo
  def Foo.greeting(person)
    puts "Hello #{person}."
  end
end

module Bar
  def Bar.greeting(person)
    puts "Bonjour #{person}."
  end
end

Foo::greeting("Joe")
Bar::greeting("Joe")

```

I think Ruby is the better language, but Python is more standardized and has a better implementation (and I absolutely **hate** web development, so Rails is out).

> **LaRoza said:**
> 
QT libraries can take the place of all C++ standard libs and the STL and provide GUI, networking and other functions I believe.

It's not an acronym. Qt is a proper name (like Java, or Linux).

---

### Post by pmasiar on 2008-08-02
> **Syndacate said:**
> I've dealt with the strict scope in Java - SCOPE BLOWS.  All variables should be global, and static, they should be able to be referenced from anywhere in the program.

... and everybody should just switch to COBOL and be done with that! You cannot be serious? Did you ever tried to debug a system with more than 100KLOC? Can you imagine what a mess it would be with all variables global?

---

### Post by imdano on 2008-08-02
> **Syndacate said:**
> PS @ ALL:
A lot of talk about scope in here - I've dealt with the strict scope in Java - SCOPE BLOWS.  All variables should be global, and static, they should be able to be referenced from anywhere in the program.

You have no idea how many issues I've had relating to scope, or an extra class I had to create to pass it an object just so the variable would be in scope.  God I hate scope.  There's enough letter/number permutations to use more than one variable!Once you have a little more experience and deal with some large programs you're going to want to take this back.  If all variables were static, how would you have multiple instances of the same class?  Not to mention how unmanageable a program with nothing but global variables is.

---

### Post by CptPicard on 2008-08-02
Hush, imdano!

You are being evil and demeaning to a noob... as we all know, we're all entitled to our opinion and actual experience doesn't matter... ;) ;)

---

### Post by Syndacate on 2008-08-02
> **pmasiar said:**
> ... and everybody should just switch to COBOL and be done with that! You cannot be serious? Did you ever tried to debug a system with more than 100KLOC? Can you imagine what a mess it would be with all variables global?

No, Obviously I wouldn't be posting here if I have dealt with programs with over 100,000 lines of code.

Scope pisses me off, I guess it's natural to some people, it's just an obstacle in the code for me :(.

[quote=imdano]Once you have a little more experience and deal with some large programs you're going to want to take this back. If all variables were static, how would you have multiple instances of the same class? Not to mention how unmanageable a program with nothing but global variables is.[/quote]

Eh, I guess you got a good point, if everything is static then it couldn't be multi-threaded.  Damn, I never think of that stuff.  That **** comes natural to everybody but me.

Few terms I could do without:
- public
- private (and all the variations of them)
- final (wtf's the difference of that vs a constant)
- INTERFACES (used 'em god knows how many times by command, still don't understand why they're useful)

And I haven't programmed in awhile so I can't think of all the ones that annoy the crap outta me.

Damn.

---

### Post by Syndacate on 2008-08-02
Yo, I got another question.

It's slightly off topic, but I mean this whole topic is off topic so whatever.

Is it normal to feel lost in notepad?

My friend got me into Eclipse (a kick-*** Java IDE) like my 3rd week of programming, and actually this computer's so slow (P4 3.0Ghz w/ 1Gb@400) that Eclipse is starting to lag on it, I type the whole line before it shows up.  Anyways, so I was always a big eclipse user when I programmed on my mac (yeayea) laptop.  Though that's a media server till the end of summer and I'm on my Desktop (specs above) and now I need to program in Java again, but Eclipse is lagging, so I turn to gedit.

Now I feel lost.  Like I can't remember simple things like the capitalization of certain methods and the like because Eclipse's auto-complete features, obviously find myself relying heavily on javadocs, but even more just for methods 'n ****.  It's like being naked, I just feel like I'm not equipped to do anything in a basic text editor.  The CS dept. insisted we use emacs, but after it messed up a few times too many, and my recent discovery of eclipse, I said "screw that."  

So was it wrong of me to use Eclipse?  Or does it not matter since running into computers that are ancient like my Desktop is becoming more and more rare?  Or are the true colors of my skill showing?  Or is this normal when using a text editor when used to using an IDE?

Input?  Plz.  I feel like a retard now.

---

### Post by pmasiar on 2008-08-02
> **Syndacate said:**
> No, Obviously I wouldn't be posting here if I have dealt with programs with over 100,000 lines of code.

Well, not having that experience did not prevented you to have strong opinion about dumping all namespaces and scope and use only globals. At least you admitted that your opinion is based on ignorance and prejudice, not experience ... :-)

---

### Post by mssever on 2008-08-02
> **Syndacate said:**
> @mssever
So you're obviously a Ruby man - but since I won't (at least initially) be aiming at web apps, Python would be the better choice, or if you were me, would you still have a look at Ruby?It's a common misconception that Ruby is just for webapps. Actually, I've found the Rails documentation to be inadequate, so I'm switching (for now, at least) to Python for webapps. But I love Ruby as a general purpose language. I use Ruby where I used to use shell scripts and where many people use Perl (or Python). I've got one larger project in Ruby, though Ruby's smaller library has limited me somewhat and I've ended up writing a few bits in Python.

Given what you've said about scope, both Ruby and Python won't have some of the things that bug you about scope (final, anyone?) and there are no Javaesque interfaces to worry about. You might especially appreciate Ruby's explicit scope rules, because Ruby's scope is obvious at a glance (Ruby enforces a simple set of naming conventions and uses those conventions to determine scope). In Python, you occasionally  have to read a bit to code to understand a particular variable's scope (though this usually isn't a problem in practice).

So sure, read up on both languages, and pick one (or both). You'll find more help on this forum for Python than Ruby, because there are only a few Rubyists around here. Note: Ruby takes more effort to learn than Python, which is why I don't think it's an ideal first language. But I do think that the payoff is worth it.

EDIT: I'm not a Java programmer, but Java programmers seem to like Ruby quite a bit.

> **Syndacate said:**
> Is it normal to feel lost in notepad?
Join the club. When I'm forced to use Windows, I install Notepad++. It's much better (and open source).

---

### Post by Syndacate on 2008-08-03
> **pmasiar said:**
> Well, not having that experience did not prevented you to have strong opinion about dumping all namespaces and scope and use only globals. At least you admitted that your opinion is based on ignorance and prejudice, not experience ... :-)

Ha, no, my opinion is based on me *experiencing* it.

Damn scope.

I'm just lashing out.  I know it has its purpose, but I have yet to find it useful (except for "for" loops) and it gets in the way of everything I try to do.

That gets and the way, and the fact that you need to pass things to different classes to link them.   You have no idea how many work arounds me and (an experienced java programmer) a friend had to pull to get me out of jams because of stupid crap like not being able to pass this to that, for whatever reason.  Between "passing" and "scope" it's like "omg wtf!!"

[quote=mssever]It's a common misconception that Ruby is just for webapps. Actually, I've found the Rails documentation to be inadequate, so I'm switching (for now, at least) to Python for webapps. But I love Ruby as a general purpose language. I use Ruby where I used to use shell scripts and where many people use Perl (or Python). I've got one larger project in Ruby, though Ruby's smaller library has limited me somewhat and I've ended up writing a few bits in Python.

Given what you've said about scope, both Ruby and Python won't have some of the things that bug you about scope (final, anyone?) and there are no Javaesque interfaces to worry about. You might especially appreciate Ruby's explicit scope rules, because Ruby's scope is obvious at a glance (Ruby enforces a simple set of naming conventions and uses those conventions to determine scope). In Python, you occasionally have to read a bit to code to understand a particular variable's scope (though this usually isn't a problem in practice).

So sure, read up on both languages, and pick one (or both). You'll find more help on this forum for Python than Ruby, because there are only a few Rubyists around here. Note: Ruby takes more effort to learn than Python, which is why I don't think it's an ideal first language. But I do think that the payoff is worth it.

EDIT: I'm not a Java programmer, but Java programmers seem to like Ruby quite a bit.[/quote]

So if Ruby takes more effort to learn, and its libraries are smaller so it has its limitations, and the documentation sucks, why would that be anywhere near as good of a choice as Python?

[quote=mssever]Join the club. When I'm forced to use Windows, I install Notepad++. It's much better (and open source).[/quote]

No, it's not that.  I'm in Ubuntu, using Gedit, Gedit is very similar to notepad++ in terms of what it does syntax highlighting wise.  I use notepad++ in there, also, but I'm usually not in there... 

I think I totally screwed myself by becoming so highly aquainted with Eclipse.  I mean yeah it's a must for huge projects, or maybe I simply haven't had enough experience yet...blah :(

---

### Post by slavik on 2008-08-03
variables on the stack are freed automatically when the function ends. it also has to do with other functions (running at the same exact time) editing those values by mistake.

all functions of your program have free reign on any variable, so hope that you and whoever you write your code with don't pick the same variable name and make both global ... could lead to interesting things.

and another thing: passing a variable down allows you to track back, like when you traverse a tree and build up a string.

---

### Post by mssever on 2008-08-03
> **Syndacate said:**
> So if Ruby takes more effort to learn, and its libraries are smaller so it has its limitations, and the documentation sucks, why would that be anywhere near as good of a choice as Python?
I didn't say the documentation is bad. I actually like Ruby's documentation better than Python's. But Ruby is a bit like the command line. Show a Linux noob a command line and he/she won't know what to do with it. But show my a command line, and I'll say that there are vary many tasks that are faster from the CLI than a GUI. Or take man pages. Newbies sometimes complain that they're hard to use, but experienced users like them. Ruby's documentation is usually great for those who already know the language. But it's not so great for newbies.

I laid out some of my reasons for preferring Ruby in a [previous post]("http://ubuntuforums.org/showpost.php?p=5503706&postcount=42"). I think that the positives outweigh the negatives. For me, coding in Ruby just feels more natural than Python (of course, this is my subjective opinion).

There are many people who prefer Python over Ruby, and that's fine. But Ruby has some very nice features that Python doesn't.

---

### Post by imdano on 2008-08-03
> **Syndacate said:**
> Eh, I guess you got a good point, if everything is static then it couldn't be multi-threaded. Damn, I never think of that stuff. That **** comes natural to everybody but me.

Few terms I could do without:
- public
- private (and all the variations of them)
- final (wtf's the difference of that vs a constant)
- INTERFACES (used 'em god knows how many times by command, still don't understand why they're useful)Having instance (non-static) variables is important in single-threaded programs too.  Otherwise, you could never have more than one instance of a class.  Say you make a Student class:
[php]public class Student {
    private String name;
    private int gradYear;

    public Student(String name) {
        // If there was no concept of scope this would
        // not be possible.
        this.name = name;
        this.gradYear = 2008;
    }
}[/php]
Now say some other application wanted to use this Student class
[php]public static void main(String[] args) {
Student s1 = new Student("Alice");
Studnet s2 = new Student("Bob");
// Do some useful stuff here
}[/php]If the variables declared in the Student class were static, The name and gradYear stored in s1 would be overwritten when s2 was instantiated, essentially making the class useless.

Having public and private scope is important too.  Sometimes you don't want someone using your class to have direct access the the variables inside it.  Again, it can be hard to see why when you first start, but once you get some more experience it makes sense.  You may find that every time you want to access or mutate a variable inside a class, you also want to do something else, like perform a check on the value to make sure it's legal.  If the variable is public, you can't guarantee your check gets made.  For example, say you want to make sure the year given in the Student class is valid:
[php]public class Student {
    private String name;
    private int gradYear;

    public Student(String name) {
        // If there was no concept of scope this would
        // not be possible.
        this.name = name;
        this.gradYear = 2008;
    }

    public void setGradYear(int year) {
        if (year < 2008) {
            System.out.println("Invalid grad year!");
        }
        else {
            gradYear = year;
        }
    }
}[/php]If gradYear is declared as public inside the Student class, this would be allowed:
[php]public static void main(String args[]) {
    Student s1 = new Student("Eve");
    s1.gradYear = -25;
}
[/php]Obviously -25 isn't a real year, but declaring the variable as public allows that assignment to be made.

"final" is just the java keyword for declaring something as a constant.  There is no difference.

Interfaces are very useful.  It was hard for me to understand why they were important when I first started learning as well, but when I started writing and working with fairly large java apps it started making sense to me.  [This article](http://www.javaworld.com/javaworld/jw-08-1999/jw-08-interfaces.html) does a pretty good job explaining the benefits.

---

### Post by nvteighen on 2008-08-03
Scope and interfaces both exist for the same reason: modularity/structured programming.

For instance, avoiding globals lets you know exactly that only the internal variables and parameters will be able to affect a given function's behaivor. So, any misbehaivor in that function will be exclusively related to those variables and not something else.

Of course, there are exceptions, but for things like errno in C (#include <errno.h>), which catches the last error code produced in the program so you can easily test for that in any place, and reserve the function's return value for something else.

Interfaces actually are the same: they define what you can access from outside and what not. There are things that you shouldn't be able to call by any mean so you don't affect the internal workings of a given class or function. Otherwise, you should be trying to catch errors for any possible misuse of any function you write!

Also, in a compiled language like C or C++, the only way to have access to a binary library is to have a header file (.h) that defines the interface. (In some way, header files are the machine-readable APIs)

---

### Post by CptPicard on 2008-08-03
@Syndacate,

I just read more of this thread and saw you wondering about lowlevel vs. highlevel and control... this is *such* a common topic here. Do read the "highlevel vs. lowlevel megathread", there is a lot of good stuff in there, and I'm not going to start repeating it here.

Briefly put, the people who most foam at the mouth at the "power" of lowlevel languages know nothing but lowlevel languages, and people who know more languages have a broader perspective and appreciate the expressive power of higher-level languages. Of course the low-level people have a very visceral reaction to this because their leetness is threatened by something they do not understand, so it must be defended violently. Of course arguing for the "non-existence" of something you don't understand yourself is doomed to fail :)

@bilijoe -- I don't think I would get hired by you then because I would tell you in the interview that pointers are the equivalent of indices to an array and they serve no other real purpose except to be the pass by reference primitive in C plus storing memory addresses when you really need them for the hardware.

From the software point of view, you get the "distance in RAM" effect by subtracting indices, and higher-level references take care of the pointer's other function.

(I understand that for lower-level programming geeks the pointer is somehow magical but I personally never really understood why)

---

### Post by tixpix on 2008-08-03
> **mssever said:**
> Qt is the first thing that comes to mind. Also, I think I remember that OpenOffice is in C++.

But i knew Openoffice is in java! :confused:

---

### Post by nvteighen on 2008-08-03
> **CptPicard said:**
> 
(I understand that for lower-level programming geeks the pointer is somehow magical but I personally never really understood why)

Quite annoying, really. A pointer is a useful thing, specially to have a short-cut to a variable, yes... but it's as useful as an if-block: it's a part of the language you have available to do some stuff.

pointer : symbolic link = memory address : inode.

---

### Post by pmasiar on 2008-08-03
> **Syndacate said:**
> Damn scope...I have yet to find it useful (except for "for" loops) and it gets in the way of everything I try to do.

You are like 3 week old puppy - could run much faster, except is stumbling by it's own legs :-)

I still find it curious that this new generation of 'freshly baked programmers' feels right to have opinion, even if they know it is based on ignorance, not knowledge - and even trying to influence with this mis-opinion people in the know (and who knows why that opinion is wrong -- because that problem was solved long time ago, before you even were born). When I was learning, I tried to understand what expert's opinion is, and why, not trying to prove them that they are wrong :-) [at least I *hope* I did so :-) ]

Seriously, you will have hard time to learn and understand if you prefer your own misconceptions over opinion based on experience. Programming is not art, you cannot define your own new style by ignoring and negating predecessors, like in painting, music, or dress code. Programming is engineering, rules are based on experience you don't have. Of course sometimes you have to break the rules - but first you need to understand what the rules are, and why, only then you can start thinking when they might not apply, and what to do then.

---

### Post by nvteighen on 2008-08-03
> **pmasiar said:**
> 
Seriously, you will have hard time to learn and understand if you prefer your own misconceptions over opinion based on experience. Programming i not art, you cannot define your own new style by ignoring and negating predecessors, like in paining, music, or dress code. Programming is engineering, rules are based on experience you don't have. Of course sometimes you have to break the rules - but first you need to understand what the rules are, and why, only then you can start thinking when they might not apply, and what to do then.

I disagree in one point :): in art you also can't ignore the previous masters' experience. Any good masterpiece will inherit something from somewhere else, either accepting the canon (traditionalism) or rejecting it (vanguardism). You can't negate without knowing what you're negating, so Picasso, when creating cubism, did it knowing Da Vinci very well.

(If you can smell Harald Bloom behind me is because I like his ideas on this.)

And programming is an art... Because engineering is an art ;) (quoting a friend of mine).

No, actually, pmasiar is right: if something that basic as scope is present in that much different languages is because it has a reason to exist or it wouldn't have survived too much. In any engineering-based discipline, if it's useless it has to die, because it's all about solving problems, not creating them for fun... (that's the mathematicians job). So, if it's there for a long time and you think it's useless, think twice and research a bit.

---

### Post by Wybiral on 2008-08-03
> **nvteighen said:**
> So, if it's there for a long time and you think it's useless, think twice and research a bit.

Yes, and with something like this, experience is the only way to really understand. If you've worked on something more than a couple of files large, scope and modules/namespaces isn't a question, it's a way of life (and sanity). I imagine you can't gain that appreciation without trying them both out.

So, without that experience, you should take a lead from the majority of experienced developers before you.

---

### Post by Lster on 2008-08-03
[QUOTE=pmasiar]I still find it curious that this new generation of 'freshly baked programmers' feels right to have opinion, even if they know it is based on ignorance, not knowledge - and even trying to influence with this mis-opinion people in the know (and who knows why that opinion is wrong -- because that problem was solved long time ago, before you even were born).[/QUOTE]

An opinion is not falsifiable.

I agree with some of it but I would say that learning things again, without being formally taught them, is amazingly insightful. In most subjects, there is a lot of generally held opinion that is not optimal by any means - the conventions so far might not be the best.

---

### Post by pmasiar on 2008-08-03
> **Lster said:**
> An opinion is not falsifiable.

Yes, but... opinion of a clueless noob going against experience of generations of experts at least could be suspicious? Are you ready to switch all your variables to globals as that poster advised? :-) If not, why not? Did you managed to falsify that opinion?

---

### Post by Syndacate on 2008-08-04
> **mssever said:**
> I didn't say the documentation is bad. I actually like Ruby's documentation better than Python's. But Ruby is a bit like the command line. Show a Linux noob a command line and he/she won't know what to do with it. But show my a command line, and I'll say that there are vary many tasks that are faster from the CLI than a GUI. Or take man pages. Newbies sometimes complain that they're hard to use, but experienced users like them. Ruby's documentation is usually great for those who already know the language. But it's not so great for newbies.

I laid out some of my reasons for preferring Ruby in a [previous post]("http://ubuntuforums.org/showpost.php?p=5503706&postcount=42"). I think that the positives outweigh the negatives. For me, coding in Ruby just feels more natural than Python (of course, this is my subjective opinion).

There are many people who prefer Python over Ruby, and that's fine. But Ruby has some very nice features that Python doesn't.

I see.  Yeah, despite me being a newb, I've used the command line for so long, with so many different OS's, that it doesn't bother me anymore.  Granted with some programs you can look over a huge manual page in terminal and still not know the correct syntaxing, but that's usually not the case.

> **imdano]If the variables declared in the Student class were static, The name and gradYear stored in s1 would be overwritten when s2 was instantiated, essentially making the class useless.

Having public and private scope is important too. **Sometimes you don't want someone using your class to have direct access the the variables inside it**. Again, it can be hard to see why when you first start, but once you get some more experience it makes sense. You may find that every time you want to access or mutate a variable inside a class, you also want to do something else, like perform a check on the value to make sure it's legal. If the variable is public, you can't guarantee your check gets made. For example, say you want to make sure the year given in the Student class is valid:[/quote]

Yeah, that's what they said way back in CS1, but I haven't come across an instance where that would be a problem (somebody using another (new) class to edit your variables).  I'm sure I'll find something out about it at some point.

[quote=nvteighen]Scope and interfaces both exist for the same reason: modularity/structured programming.

For instance, avoiding globals lets you know exactly that only the internal variables and parameters will be able to affect a given function's behaivor. So, any misbehaivor in that function will be exclusively related to those variables and not something else.

Of course, there are exceptions, but for things like errno in C (#include <errno.h>), which catches the last error code produced in the program so you can easily test for that in any place, and reserve the function's return value for something else.

Interfaces actually are the same: they define what you can access from outside and what not. There are things that you shouldn't be able to call by any mean so you don't affect the internal workings of a given class or function. Otherwise, you should be trying to catch errors for any possible misuse of any function you write!

Also, in a compiled language like C or C++, the only way to have access to a binary library is to have a header file (.h) that defines the interface. (In some way, header files are the machine-readable APIs)[/quote]

Yeah, but that's stuff I don't get.  Why should you need to "list" what you're going to use for implementations?  Say you want more?  Say you want less?  It just seems ultra-redundant.

Parent-classes make sense...because there's actual code there...interfaces don't...it just seems like a formality or something.

[quote=CptPicard]@Syndacate,

I just read more of this thread and saw you wondering about lowlevel vs. highlevel and control... this is such a common topic here. Do read the "highlevel vs. lowlevel megathread", there is a lot of good stuff in there, and I'm not going to start repeating it here.

Briefly put, the people who most foam at the mouth at the "power" of lowlevel languages know nothing but lowlevel languages, and people who know more languages have a broader perspective and appreciate the expressive power of higher-level languages. Of course the low-level people have a very visceral reaction to this because their leetness is threatened by something they do not understand, so it must be defended violently. Of course arguing for the "non-existence" of something you don't understand yourself is doomed to fail

@bilijoe -- I don't think I would get hired by you then because I would tell you in the interview that pointers are the equivalent of indices to an array and they serve no other real purpose except to be the pass by reference primitive in C plus storing memory addresses when you really need them for the hardware.

From the software point of view, you get the "distance in RAM" effect by subtracting indices, and higher-level references take care of the pointer's other function.

(I understand that for lower-level programming geeks the pointer is somehow magical but I personally never really understood why)[/quote]

I'll read that thread, thanks.

[quote=pmasiar]You are like 3 week old puppy - could run much faster, except is stumbling by it's own legs

I still find it curious that this new generation of 'freshly baked programmers' feels right to have opinion, even if they know it is based on ignorance, not knowledge - and even trying to influence with this mis-opinion people in the know (and who knows why that opinion is wrong -- because that problem was solved long time ago, before you even were born). When I was learning, I tried to understand what expert's opinion is, and why, not trying to prove them that they are wrong [at least I *hope* I did so ]

Seriously, you will have hard time to learn and understand if you prefer your own misconceptions over opinion based on experience. Programming is not art, you cannot define your own new style by ignoring and negating predecessors, like in painting, music, or dress code. Programming is engineering, rules are based on experience you don't have. Of course sometimes you have to break the rules - but first you need to understand what the rules are, and why, only then you can start thinking when they might not apply, and what to do then.[/quote]

That opinion seems to be pretty contradictory to other (experienced) peoples' opinion of programming, who see it as a flexible art.

So I have an opinion, so what?  I have an opinion now, with experience, it may change.  I realize these things have a purpose, but a lot of the purpose I don't see as a problem yet, maybe I will in the future, maybe I won't, some people use different methods than others.  I've seen lots of experienced programmers argue over methods to do things as to "which way is proper" vs "which way is faster."

As of now, scope just gets in my way, I haven't found use for it.  Though I'm sure that will change.  Just because I have an opinion doesn't make it final.

[quote=nvteighen]No, actually, pmasiar is right: if something that basic as scope is present in that much different languages is because it has a reason to exist or it wouldn't have survived too much. In any engineering-based discipline, if it's useless it has to die, because it's all about solving problems, not creating them for fun... (that's the mathematicians job). **So, if it's there for a long time and you think it's useless, think twice and research a bit.**[/quote]

No normal, sane, person I know uses an iterator opposed to something simple along the lines of "i++ said:**
> Yes, and with something like this, experience is the only way to really understand. If you've worked on something more than a couple of files large, scope and modules/namespaces isn't a question, it's a way of life (and sanity). I imagine you can't gain that appreciation without trying them both out.

So, without that experience, you should take a lead from the majority of experienced developers before you.

Yeah, even in working with a lot of files - in Java there is no namespace, I first saw that in C++ - or maybe it's in Java and I just never heard of it :-?.  I'm sure I'll learn to appreciate some of the stuff that I don't appreciate now given time, also.

---

### Post by nvteighen on 2008-08-04
> **Syndacate said:**
> 

Yeah, but that's stuff I don't get.  Why should you need to "list" what you're going to use for implementations?  Say you want more?  Say you want less?  It just seems ultra-redundant.

Parent-classes make sense...because there's actual code there...interfaces don't...it just seems like a formality or something.

Think about this: you have a certain module (file) written that implements a sorting algorithm. OK, to sort something you'll need to use some "helper" functions to resize memory or sanity checks, for example, that are only important for internal work, not for the module's purpose. So, when you turn that module into a library and make it available for people to use, you have to give them an interface to work with, so they know what's available for them and what's not.

Why not include code in the interface? Because the interface should also work if you only have the binary for the library, where you have zero access to the source code. Or when the developer has designed a way to do something to avoid some errors, so you're forced to do things as they're meant to be used... (if you don't like it, change the source).

If you want more, you'll have to change the library's source code. If you want less, you can trim the header file (and this is a common practice for the C Standard Library).

But, I think you may also be tricked by C++'s and Java's stupid way to create interfaces. Actually, C does it much better, as you don't have to mention the private functions (called "static functions") and they remain absolutely "private".

> No normal, sane, person I know uses an iterator opposed to something simple along the lines of "i++;" - That is 100% useless.  Though they simply haven't gotten rid of it.  Cuts down on difficulty, memory usage, and code amount.  There's a lot of programmers that don't even know they exist.

Ehmm... if and only if your language supports something like i++ :) In Python I'd rather prefer an iterator than a counter variable; it's actually much easier to use in that language.

> Yeah, even in working with a lot of files - in Java there is no namespace, I first saw that in C++ - or maybe it's in Java and I just never heard of it :-?.  I'm sure I'll learn to appreciate some of the stuff that I don't appreciate now given time, also.

Are you sure in Java namespace isn't defined at file-level? In C, you don't have "explicit" namespaces, but each file lives on its own unless you connect them through an interface. (It's actually much more related to how the compiler works than to something else).

---

### Post by pmasiar on 2008-08-04
> **Syndacate said:**
> That opinion seems to be pretty contradictory to other (experienced) peoples' opinion of programming, who see it as a flexible art.

Art has no objective measurement of quality, programming (as engineering discipline) has.

> So I have an opinion, so what?  I have an opinion now, with experience, it may change.  ... some people use different methods than others. 

Yup, some people use it right, some not :-)

> As of now, scope just gets in my way, I haven't found use for it.  Though I'm sure that will change.  Just because I have an opinion doesn't make it final.

And just because we are friendly to beginners here, if you happens to express an opinion that I know for sure is wrong, I will not let it stay uncontested and let other beginners be confused by it :-) As I said, programming is not art, you cannot start your own 'school of thought' by picking any random set of rules - some approaches are more useful in practice than others, even if you do not understand that yet.

---

### Post by Lster on 2008-08-04
> **pmasiar]Yes, but... opinion of a clueless noob going against experience of generations of experts at least could be suspicious?[/QUOTE]

Be nice.  said:**
> Are you ready to switch all your variables to globals as that poster advised? If not, why not? Did you managed to falsify that opinion?

Definitely not. But all the same, his opinion is not wrong. It's nice to be able to only worry about the variables in a particular segment, but if he finds something beneficial in ignoring that... I see no problem in it. These "rules" seem to, all-to-oftenly, take the place of common sense.

So in a sense, I'm saying it is great to know what is conventional, and there are definitely times when conventions should be followed, but they shouldn't be limiting... If it's worth doing, there's a good chance that someone learning programming will pick it up anyway! :)

---

### Post by CC_machine on 2008-08-04
Cube and Cube II are free, open source, and written entirely in C++(well, the network code is in C, but that's only a tiny portion of the code) with SDL and OpenGL, although they are very complex. [http://cubeengine.com](http://cubeengine.com)

for learning graphical functions with SDL, i recommend [http://lazyfoo.net/](http://lazyfoo.net/)



*edit: ah sorry this is probably not what you asked for, sorry for spamming

---

### Post by mssever on 2008-08-04
> **Lster said:**
> So in a sense, I'm saying it is great to know what is conventional, and there are definitely times when conventions should be followed, but they shouldn't be limiting...
That's true, but it takes experience to know when breaking convention is a Good Thing and when it's a Bad Thing. And conventions are there for a reason. They represent the best way to do something for the usual cases. So newbies can't know when to violate convention and should therefore follow convention until they gain more experience. Even then, it's wise to think thrice before violating a convention.

See also this statement from Python's [FONT=Courier New]import this[/FONT]: "Special cases aren't special enough to break the rules. Although practicality beats purity."

---

### Post by Lster on 2008-08-04
Mostly agreed; I don't know if it's about knowing when to violate conventions as just a little analysis! If I can break out of a loop easily and simply with a goto, why use a flag or something else?

Here's some made up pseudocode which is difficult to replace the goto without messing the code up:
[PHP]i = 0
while i <= s:
	j = i
	while j <= t:
		if 3*i == something(j):
			goto done;
		j += 1
	i += 1

done:
print(i*j)
[/PHP]

---

### Post by mssever on 2008-08-04
> **Lster said:**
> Here's some made up pseudocode which is difficult to replace the goto without messing the code up:
[php]i = 0
while i <= s:
    j = i
    while j <= t:
        if 3*i == something(j):
            goto done;
        j += 1
    i += 1

done:
print(i*j)
[/php]
In some languages (such as PHP if my memory serves me right), the break statement can take an argument for the number of levels to break out of. So, modifying your pseudocode:
[php]i = 0
while i <= s:
    j = i
    while j <= t:
        if 3*i == something(j):
            break(2)
        j += 1
    i += 1

print(i*j)[/php]
Personally, I think that using flags in such cases can be clearer.

---

### Post by Lster on 2008-08-04
That code is arguably still using gotos.

[QUOTE=mssever]Personally, I think that using flags in such cases can be clearer.[/QUOTE]

Agreed. :)

---

### Post by nvteighen on 2008-08-04
> **Lster said:**
> Mostly agreed; I don't know if it's about knowing when to violate conventions as just a little analysis! If I can break out of a loop easily and simply with a goto, why use a flag or something else?

Here's some made up pseudocode which is difficult to replace the goto without messing the code up:
[PHP]i = 0
while i <= s:
	j = i
	while j <= t:
		if 3*i == something(j):
			goto done;
		j += 1
	i += 1

done:
print(i*j)
[/PHP]

Without flags and without goto, just reseting the counters to their limit; this way, they're afterwards incremented and the conditions of each while returns false, thus stoping the loop:
[PHP]i = 0
while i <= s:
	j = i
	while j <= t:
		if 3*i == something(j):
			z = i # make a copy so we can print later
			w = j # see above
			j = t
			i = s
		j += 1
	i += 1

print(z*w)
[/PHP]

---

### Post by Lster on 2008-08-04
Nicely done. :)

Round two?

[PHP]
i = 0
while (i+j)%2 == 0:
	j = 0
	while (i+j)%2 == 1:
		if good(i*j+i+j):
			break(2)
		
		j += step(j, i)
	
	i += step(i, j)

print i*j
[/PHP]

:D

---

### Post by nvteighen on 2008-08-04
> **Lster said:**
> Nicely done. :)

Round two?

[PHP]
i = 0
while (i+j)%2 == 0:
	j = 0
	while (i+j)%2 == 1:
		if good(i*j+i+j):
			break(2)
		
		j += step(j, i)
	
	i += step(i, j)

print i*j
[/PHP]

:D

Revise the algorithm, because if, I'm not wrong, it never gets to the second while (you're always reseting j = 0, so step will just double i and that's always an even number).

---

### Post by Lster on 2008-08-04
The step function is magic. It does anything and may even use global variables... ;)

---

### Post by Wybiral on 2008-08-04
> **slavik said:**
> why is join part of the string object in Python? Simply because strings in Python are immutable, just like Java. Hence, the joining of strings works a bit differently than for lists ... (since a new object must be created, whereas with lists, one of the lists can be modified).

Well, it's for a reason... The string join IS special, not because strings are immutable, but because you might want a separator.

```

print ", ".join(["hello", "world"])

```

As far as the lists go, I wouldn't want them to join on one list TBH (I would prefer the immutability any day). There are generic joining constructs if you need them, you could always use "reduce(add, lst)" or whatever predicate you need for joining things. That would work for any iterable object.

---

### Post by Lster on 2008-08-04
But why not:

```
print ['hello', 'world'].join(', ')
```

It looks so much nicer and seems more intuitive to me. It's not a deal breaker though. :)

---

### Post by nvteighen on 2008-08-04
> **Lster said:**
> The step function is magic. It does anything and may even use global variables... ;)

Ah, I thought it was a step like the used in a for-loop?

No, there you can't do it with a shortcut, you win :) because the condition is an expression, not a variable. Anyway, using a flag could be trivial.

Now, to the theory: there's nothing bad with a goto used the way you described. The problem is when you use a goto that breaks the general program flow and breaks the whole structure into pieces. Using it to escape from multiple nested loops will only break that flow and nothing else, like a break or a continue also do.

---

### Post by Wybiral on 2008-08-04
> **Lster said:**
> But why not:

```
print ['hello', 'world'].join(', ')
```

It looks so much nicer and seems more intuitive to me. It's not a deal breaker though. :)

Because it's not part of the list class...

```

print " ".join(x for x in something)

```

---

### Post by Lster on 2008-08-04
But it, in my opinion at least, makes more sense like that. Why isn't that function given to all iterables?

---

### Post by Wybiral on 2008-08-04
> **Lster said:**
> But it, in my opinion at least, makes more sense like that. Why isn't that function given to all iterables?

Because I can define my own iterable... The only requirement is an __iter__ and a next method. IMO, it would make more sense as "join(', ', itr)" but it's still not that much better... If any. Especially since it IS a string related operation (it's only joining strings, it won't work if the iterable spits out other types, the point is that it's a string join).

---

### Post by pmasiar on 2008-08-04
> **Lster said:**
> If I can break out of a loop easily and simply with a goto, why use a flag or something else?

Because 
1) properly closing loops releases resources, which likely will not happen after GOTO? 
2) sometimes later target of GOTO might be moved, say inside a loop or something? Trivial examples are trivial, but in RL target of GOTO might be 5 pages away
3) zillion other "surprises". 

Decent language should have "structured GOTO": "continue" and "leave" the loop. If not, designers were not up to snuff.

---

### Post by Lster on 2008-08-04
I see where it's coming from but it's never gonna' seem right. ;)

---

### Post by Wybiral on 2008-08-04
> **Lster said:**
> I see where it's coming from but it's never gonna' seem right. ;)

If you wanted a more general way to join things, just do something like this (using a general wedge function to insert the separators):

```

[color=#008000]**from**[/color] [color=#0000FF]**operator**[/color] [color=#008000]**import**[/color] add

[color=#008000]**def**[/color] [color=#0000FF]wedge[/color](separator, seq):
    seq [color=#666666]=[/color] [color=#008000]iter[/color](seq)
    [color=#008000]**yield**[/color] seq[color=#666666].[/color]next()
    [color=#008000]**for**[/color] i [color=#AA22FF]**in**[/color] seq:
        [color=#008000]**yield**[/color] separator
        [color=#008000]**yield**[/color] i

lst [color=#666666]=[/color] [[color=#BA2121]"hello"[/color], [color=#BA2121]"world"[/color], [color=#BA2121]"goodbye"[/color]]
[color=#008000]**print**[/color] [color=#008000]reduce[/color](add, wedge([color=#BA2121]"|"[/color], lst))

```

---

### Post by Lster on 2008-08-04
[QUOTE=pmasiar]1) properly closing loops releases resources, which likely will not happen after GOTO?[/QUOTE]

In which languages do you mean? I'd be very suprised if this was the case in languages like Python, C and Java.

In C at least, the only thing that should need doing is popping old variables off the stack. I *imagine* this is done when you jump anywhere...

---

### Post by Syndacate on 2008-08-04
> **nvteighen said:**
> Think about this: you have a certain module (file) written that implements a sorting algorithm. OK, to sort something you'll need to use some "helper" functions to resize memory or sanity checks, for example, that are only important for internal work, not for the module's purpose. So, when you turn that module into a library and make it available for people to use, you have to give them an interface to work with, so they know what's available for them and what's not.

Why not include code in the interface? Because the interface should also work if you only have the binary for the library, where you have zero access to the source code. Or when the developer has designed a way to do something to avoid some errors, so you're forced to do things as they're meant to be used... (if you don't like it, change the source).

If you want more, you'll have to change the library's source code. If you want less, you can trim the header file (and this is a common practice for the C Standard Library).

But, I think you may also be tricked by C++'s and Java's stupid way to create interfaces. Actually, C does it much better, as you don't have to mention the private functions (called "static functions") and they remain absolutely "private".

Maybe, the only one I really know is Java, and even that, I'm no expert at.  It's a bit diff in Java though, privates != static, you can have public statics.  Maybe I'll simply get a better understanding of it when I get to C, or headers in C++.


> **nvteighen said:**
> Ehmm... if and only if your language supports something like i++ :) In Python I'd rather prefer an iterator than a counter variable; it's actually much easier to use in that language

I don't know much (anything) about python, but in Java it's absolutely retarded to use an actual iterator instead of a variable incremental in a loop.  The iterator's "next" function has to be inside a loop too, so all it does is make your code longer, more complex (the syntaxing for iterators is weird), and it takes up more memory as an object opposed to an integer.  Maybe it's different with Python, dunno.

Not to mention, even if the language doesn't support a stepper like "i++" per-se, it'll most likely support something like "i = i + 1;"

> **nvteighen said:**
> Are you sure in Java namespace isn't defined at file-level? In C, you don't have "explicit" namespaces, but each file lives on its own unless you connect them through an interface. (It's actually much more related to how the compiler works than to something else).

Oh, I'm sure it might have them "*under the hood*" or something, but it's nothing you have to deal with, Java does it for you (like memory management).  You need to explicitly state like "using namespace std;" or "std::cout <<" in C++, but in Java you don't need anything like that for standard IO.

[quote=pmasiar]Art has no objective measurement of quality, programming (as engineering discipline) has.[/quote]

While I agree, there has to be something qualitative about art that makes those art nut-jobs think certain accidental splashes of art look better and are worth 300,000 dollars opposed to other certain accidental splashes of art.

[quote=pmasiar]Yup, some people use it right, some not [/quote]

That's very objective.  I've seen seasoned programmers argue about methods of doing stuff all the time, each presenting a list of reasons about which one is better and why.  It's not a matter of "right" and "wrong" - some people develop their own coding styles, and niches in a language that they like.  Or at least that's my experience seeing other people argue about different methods in Java, or comparing my code to others, and the way they did it seems retarded to me (and I'm sure my way sounds retarded to them).

[quote=pmasiar]And just because we are friendly to beginners here, if you happens to express an opinion that I know for sure is wrong, I will not let it stay uncontested and let other beginners be confused by it As I said, programming is not art, you cannot start your own 'school of thought' by picking any random set of rules - some approaches are more useful in practice than others, even if you do not understand that yet.[/quote]

Your statement that programming is not art conflicts with other peoples' (not including myself) opinion that it is a type of art.  It's always argued over, even in this thread.

I didn't say my opinion was right, infact I said it was wrong and will probably change with more experience, though as of now, I can't have an opinion on something my opinion's against, can I?  I'm sure it's great and comes in handy in tons of places, but of now, I hate it.  I never said I intend to change it or anything, I said just the opposite, that my opinions will probably change.

[quote=Lster]Definitely not. But all the same, his opinion is not wrong. It's nice to be able to only worry about the variables in a particular segment, but if he finds something beneficial in ignoring that... I see no problem in it. These "rules" seem to, all-to-oftenly, take the place of common sense.

So in a sense, I'm saying it is great to know what is conventional, and there are definitely times when conventions should be followed, but they shouldn't be limiting... **If it's worth doing, there's a good chance that someone learning programming will pick it up anyway**![/quote]

That's a good point.  Better techniques and methods will be better picked up and appreciated overtime.  It's like anything else.  Do it long enough, and you find new ways for going about things.  Though at the same token, I should notice and observe the proper conventions/techniques.  Just something to keep an eye out for, if nothing else.

[quote=CC_machine]Cube and Cube II are free, open source, and written entirely in C++(well, the network code is in C, but that's only a tiny portion of the code) with SDL and OpenGL, although they are very complex. [http://cubeengine.com](http://cubeengine.com)

for learning graphical functions with SDL, i recommend [http://lazyfoo.net/](http://lazyfoo.net/)



*edit: ah sorry this is probably not what you asked for, sorry for spamming [/quote]

Ah, alright, that actually helps a lot, thanks.

[quote=Lster]Mostly agreed; I don't know if it's about knowing when to violate conventions as just a little analysis! If I can break out of a loop easily and simply with a goto, why use a flag or something else?

Here's some made up pseudocode which is difficult to replace the goto without messing the code up:[/quote]

In Java I think you can just put "break;" and it'll work fine.  Though I'm pretty sure that's not the proper way of doing it.

---

### Post by pmasiar on 2008-08-04
> **Syndacate said:**
> While I agree, there has to be something qualitative about art that makes those art nut-jobs think certain accidental splashes of art look better and are worth 300,000 dollars opposed to other certain accidental splashes of art.

Often that "qualitative something" is death of the author: while alive, author can often create many copies, devaluing the original. Rarely is art of a live author valuable.

> Your statement that programming is not art conflicts with other peoples' (not including myself) opinion that it is a type of art.  It's always argued over, even in this thread.

Even if is argued often it does not change a iota on a fact that other opinions are wrong :-)

It's not my opinion (ie I read it somewhere). Those other people do not bother to define art, craft, and science. If they did, they would realize that programming is engineering-like craft, not a science, and not art.

BTW I found it confusing your habit to merge different subthreads (about different issues) into single answer. More text to trim - and most people do not bother to quote or trim :-)

> In Java I think you can just put "break;" and it'll work fine.  Though I'm pretty sure that's not the proper way of doing it.

"break" is exactly that structured "leave" I was talking about.

---

### Post by pmasiar on 2008-08-04
> **Lster said:**
> [GOTO as un-structured LEAVE pollutes stack]

In which languages do you mean? I'd be very suprised if this was the case in languages like Python, C and Java.

In C at least, the only thing that should need doing is popping old variables off the stack. I *imagine* this is done when you jump anywhere...

In C, nothing prevents you to GOTO out of the loop, do some calculations, and GOTO back (because it might be valid ASM code). So my hunch is (and I would be surprised if I am wrong) that compiler DOES NOT try to clear stack without direct request. Any C hacker volunteers willing to try to look at the generated ASM code, and tell us the facts, instead of Lster's and mine's WAGs?

---

### Post by nanotube on 2008-08-04
> **Lster said:**
> I see where it's coming from but it's never gonna' seem right. ;)

after a couple hundred times you do it, it'll start seeming right. :)

---

### Post by Syndacate on 2008-08-04
> **pmasiar said:**
> Often that "qualitative something" is death of the author: while alive, author can often create many copies, devaluing the original. Rarely is art of a live author valuable.

> Your statement that programming is not art conflicts with other peoples' (not including myself) opinion that it is a type of art.  It's always argued over, even in this thread.

Even if is argued often it does not change a iota on a fact that other opinions are wrong :-)

It's not my opinion (ie I read it somewhere). Those other people do not bother to define art, craft, and science. If they did, they would realize that programming is engineering-like craft, not a science, and not art.

BTW I found it confusing your habit to merge different subthreads (about different issues) into single answer. More text to trim - and most people do not bother to quote or trim :-)

> In Java I think you can just put "break;" and it'll work fine.  Though I'm pretty sure that's not the proper way of doing it.

"break" is exactly that structured "leave" I was talking about.

Oh, it's a convenient way, whether it's proper or not.  I suppose there's many instances like that.  I've seen all sorts of shortcuts that don't necessarily abide by the rules but do the job 100% anyway.  That's up to the programmer.

Sorry about the way I multi-quote messages, it makes it easier IMO to find out who I'm talking to, regarding which post(s).

---

### Post by nvteighen on 2008-08-05
> **Syndacate said:**
> 
I don't know much (anything) about python, but in Java it's absolutely retarded to use an actual iterator instead of a variable incremental in a loop.  The iterator's "next" function has to be inside a loop too, so all it does is make your code longer, more complex (the syntaxing for iterators is weird), and it takes up more memory as an object opposed to an integer.  Maybe it's different with Python, dunno.

In Python, you have an operator ("in") that makes your life easier. A regular for-loop in that language would look like this:
```

for x in object:
    # do something

```

Of course, object has to be iterable. But most built-in data types are already and creating one in a custom class is easy.

> **pmasiar said:**
> In C, nothing prevents you to GOTO out of the loop, do some calculations, and GOTO back (because it might be valid ASM code). So my hunch is (and I would be surprised if I am wrong) that compiler DOES NOT try to clear stack without direct request. Any C hacker volunteers willing to try to look at the generated ASM code, and tell us the facts, instead of Lster's and mine's WAGs?

Let's see:
```

int main(void)
{
    int i = 0;
    while (i < 4)
    {
        int j = 0;
        if((i + j) == 2)
        {
            goto hell;
            j++;
        }
            
        i++;
    }
    
    hell:
    i += 2;

    return 0;
}

```

```

(gdb) disassemble main
Dump of assembler code for function main:
0x08048344 <main+0>:	lea    0x4(%esp),%ecx
0x08048348 <main+4>:	and    $0xfffffff0,%esp
0x0804834b <main+7>:	pushl  -0x4(%ecx)
0x0804834e <main+10>:	push   %ebp
0x0804834f <main+11>:	mov    %esp,%ebp
0x08048351 <main+13>:	push   %ecx
0x08048352 <main+14>:	sub    $0x10,%esp
0x08048355 <main+17>:	movl   $0x0,-0x8(%ebp)
0x0804835c <main+24>:	jmp    0x8048376 <main+50>
0x0804835e <main+26>:	movl   $0x0,-0xc(%ebp)
0x08048365 <main+33>:	mov    -0xc(%ebp),%eax
0x08048368 <main+36>:	add    -0x8(%ebp),%eax
0x0804836b <main+39>:	cmp    $0x2,%eax
0x0804836e <main+42>:	jne    0x8048372 <main+46>
0x08048370 <main+44>:	jmp    0x804837c <main+56>
0x08048372 <main+46>:	addl   $0x1,-0x8(%ebp)
0x08048376 <main+50>:	cmpl   $0x3,-0x8(%ebp)
0x0804837a <main+54>:	jle    0x804835e <main+26>
0x0804837c <main+56>:	addl   $0x2,-0x8(%ebp)
0x08048380 <main+60>:	mov    $0x0,%eax
0x08048385 <main+65>:	add    $0x10,%esp
0x08048388 <main+68>:	pop    %ecx
0x08048389 <main+69>:	pop    %ebp
0x0804838a <main+70>:	lea    -0x4(%ecx),%esp
0x0804838d <main+73>:	ret    
End of assembler dump.

```

All stacks are popped after the jle to <main+26>, which represents the jump to the beginning of the loop. So, j is not destroyed when performing the goto.

---

### Post by Lster on 2008-08-05
Confirmed on a 64bit computer too. Also, the fact that the information is left behind is not enough to prove the data has not been freed. It hasn't though because new variables are allocated at offset-12 instead offset-8 which would suggest that the data was cleared.

Messing around with optimizations, however, is a little tricky to conclude anything over. For trivial programs it kind of "cheats" and for more complex programs the stack isn't used - it allocates variables to registers. I'm gonna' have a little more of a play around with optimization as this is quite interesting stuff.

---

### Post by pmasiar on 2008-08-05
> **Syndacate said:**
> Oh, it's a convenient way, whether it's proper or not. ....

Sorry about the way I multi-quote messages, it makes it easier IMO to find out who I'm talking to, regarding which post(s).

Sorry, my next pet issue: when you quote, trim!

I have no idea to what your "it's a convenient way" refers to. Trim out parts which you do not respond, read links in my sig, and make internet a better place :-)

---

### Post by Syndacate on 2008-08-06
> **nvteighen said:**
> In Python, you have an operator ("in") that makes your life easier. A regular for-loop in that language would look like this:
```

for x in object:
    # do something

```

Of course, object has to be iterable. But most built-in data types are already and creating one in a custom class is easy.

Yeah, I don't understand that syntaxing :(.  Though I don't think there's anything like that in Java...I could be wrong...

> **nvteighen said:**
> 

Let's see:
```

int main(void)
{
    int i = 0;
    while (i < 4)
    {
        int j = 0;
        if((i + j) == 2)
        {
            goto hell;
            j++;
        }
            
        i++;
    }
    
    hell:
    i += 2;

    return 0;
}

```

```

(gdb) disassemble main
Dump of assembler code for function main:
0x08048344 <main+0>:	lea    0x4(%esp),%ecx
0x08048348 <main+4>:	and    $0xfffffff0,%esp
0x0804834b <main+7>:	pushl  -0x4(%ecx)
0x0804834e <main+10>:	push   %ebp
0x0804834f <main+11>:	mov    %esp,%ebp
0x08048351 <main+13>:	push   %ecx
0x08048352 <main+14>:	sub    $0x10,%esp
0x08048355 <main+17>:	movl   $0x0,-0x8(%ebp)
0x0804835c <main+24>:	jmp    0x8048376 <main+50>
0x0804835e <main+26>:	movl   $0x0,-0xc(%ebp)
0x08048365 <main+33>:	mov    -0xc(%ebp),%eax
0x08048368 <main+36>:	add    -0x8(%ebp),%eax
0x0804836b <main+39>:	cmp    $0x2,%eax
0x0804836e <main+42>:	jne    0x8048372 <main+46>
0x08048370 <main+44>:	jmp    0x804837c <main+56>
0x08048372 <main+46>:	addl   $0x1,-0x8(%ebp)
0x08048376 <main+50>:	cmpl   $0x3,-0x8(%ebp)
0x0804837a <main+54>:	jle    0x804835e <main+26>
0x0804837c <main+56>:	addl   $0x2,-0x8(%ebp)
0x08048380 <main+60>:	mov    $0x0,%eax
0x08048385 <main+65>:	add    $0x10,%esp
0x08048388 <main+68>:	pop    %ecx
0x08048389 <main+69>:	pop    %ebp
0x0804838a <main+70>:	lea    -0x4(%ecx),%esp
0x0804838d <main+73>:	ret    
End of assembler dump.

```

All stacks are popped after the jle to <main+26>, which represents the jump to the beginning of the loop. So, j is not destroyed when performing the goto.

Oh.

:confused:

[quote=Lster]Confirmed on a 64bit computer too. Also, the fact that the information is left behind is not enough to prove the data has not been freed. It hasn't though because new variables are allocated at offset-12 instead offset-8 which would suggest that the data was cleared.

Messing around with optimizations, however, is a little tricky to conclude anything over. For trivial programs it kind of "cheats" and for more complex programs the stack isn't used - it allocates variables to registers. I'm gonna' have a little more of a play around with optimization as this is quite interesting stuff.[/quote]

Oh, aight.

[quote=pmasiar]Sorry, my next pet issue: when you quote, trim!

I have no idea to what your "it's a convenient way" refers to. Trim out parts which you do not respond, read links in my sig, and make internet a better place [/quote]

lol.  Alright.

I usually just bold it, but I usually also respond to different parts.

I'll try to watch it =).

---

### Post by imdano on 2008-08-06
> **nvteighen said:**
> In Python, you have an operator ("in") that makes your life easier. A regular for-loop in that language would look like this:
```

for x in object:
    # do something

```

[QUOTE=Syndacate;5533653]Yeah, I don't understand that syntaxing :(.  Though I don't think there's anything like that in Java...I could be wrong...Java does have something like that.  It's new in Java 5 or 6 (I think it was 5...).
```

List<Integer> list = new LinkedList<Integer>()
list.add(new Integer(2));
list.add(new Integer(45));
for (Integer x : list) {
    System.out.println(x);
}
```
Running that would print ```
2
45
```

The Python equivalent would be
```

lst = []
lst.append(2)
lst.append(45)
for x in lst:
    print x
```

---

### Post by pmasiar on 2008-08-06
> **imdano said:**
> 
The Python equivalent would be
```

lst = []
lst.append(2)
lst.append(45)
for x in lst:
    print x
```

That would be rather ugly Python! :-) You can write cleaner, more readable code, using powerful literals and overloaded operators, which I miss in Java the most:

```

lst = []
lst += [2, 45]
for x in lst:
    print x
```

---

### Post by Lster on 2008-08-06
[QUOTE=pmasiar]You can write cleaner, more readable code, using powerful literals and overloaded operators, which I miss in Java the most[/QUOTE]

Indeed, I'm using Java at the moment for a project that requires the use of BigIntegers and BigDecimals. It is such a pain to write code like:

[PHP]x = x.multiple(y)[/PHP]

As opposed to:

[PHP]x *= y[/PHP]

The BigDecimal class also seems to be missing a few features like non-integral powers so I have had to implement an Nth-root algorithm which is quite an effort indeed.

---

### Post by nvteighen on 2008-08-06
> **pmasiar said:**
> That would be rather ugly Python! :-) You can write cleaner, more readable code, using powerful literals and overloaded operators, which I miss in Java the most:

```

lst = []
lst += [2, 45]
for x in lst:
    print x
```
Thank you very much, because I was going to post a thread about that asking what's better practice in Python. For some reason, I intuitively used your approach in some learning app I'm doing.

---

### Post by Wybiral on 2008-08-06
Java may have iterators, but can it do this? :)

```

from itertools import izip

def fibonacci_numbers():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b


def prime_numbers():
    yield 2
    a = 3
    plist = []
    while True:
        for b in plist:
            if not(a % b):
                break
        else:
            yield a
            plist.append(a)
        a += 2


def take(n, seq):
    return (x for i, x in izip(xrange(n), seq))


# Sum of first 1000 prime numbers
print "Primes: ", sum(take(1000, prime_numbers()))

# Sum of first 1000 fibonacci numbers
print "Fibs: ", sum(take(1000, fibonacci_numbers()))

```

Without having to build a single list (and still be reusable)?

You have to love those generators...

---

### Post by Lster on 2008-08-06
My language, Easy, still wins:

[PHP]print sum of first 1000 primes
print sum of first 1000 Fibonacci numbers[/PHP]

The only problem is there isn't a compiler... yet! ;)

---

### Post by Wybiral on 2008-08-06
> **Lster said:**
> My language, Easy, still wins:

[PHP]print sum of first 1000 primes
print sum of first 1000 Fibonacci numbers[/PHP]

The only problem is there isn't a compiler... yet! ;)

:p

You know, if you change the "take" function to be "first", it would be pretty similar to the Python one...

---

### Post by Lster on 2008-08-06
...But then it wouldn't be grammatically correct. :(

And what's more, let's see Python (or any language) do this:

[PHP]print sum of primes[/PHP]

> &#8734;

Neat! :KS

---

### Post by nvteighen on 2008-08-06
> **Wybiral said:**
> Java may have iterators, but can it do this? :)

(...)

Without having to build a single list (and still be reusable)?

You have to love those generators...

Very nice! And you've helped me to understand generators... Thank you!

---

### Post by imdano on 2008-08-06
> **pmasiar said:**
> That would be rather ugly Python! :-) You can write cleaner, more readable code, using powerful literals and overloaded operators, which I miss in Java the most:

```

lst = []
lst += [2, 45]
for x in lst:
    print x
```Yes, I know. I was trying to make it look as much like the java code as possible.  Really, the most readable way would just be:
```

lst = [2, 45]
for x in lst:
    print x
```Or, if you didn't need to do anything else with the list, this:
```

for x in [2, 45]:
    print x
```

---

### Post by CptPicard on 2008-08-06
> **Wybiral said:**
> Java may have iterators, but can it do this? :)


Actually it sort of can, but you have to explicitly code a sort of "producer" class that implements Iterator. So you can't just nicely "yield" from the algorithm as a kind of return, like you can in Python.

I *could* hack up a kind of "yieldable" base class that would even contain its own thread -- threads can be used to emulate continuations because they have their own stack -- but I am not sure if that would approach the situation of an ugly hack ;)

---

### Post by Syndacate on 2008-08-07
> **imdano said:**
> In Python, you have an operator ("in") that makes your life easier. A regular for-loop in that language would look like this:
```

for x in object:
    # do something

```

**Java does have something like that.  It's new in Java 5 or 6 (I think it was 5...).**
```

List<Integer> list = new LinkedList<Integer>()
list.add(new Integer(2));
list.add(new Integer(45));
for (Integer x : list) {
    System.out.println(x);
}
```
Running that would print ```
2
45
```

The Python equivalent would be
```

lst = []
lst.append(2)
lst.append(45)
for x in lst:
    print x
```

Ah **** ur right, I used that method ONCE.  And it was only because somebody (a higher programmer) told me about it while I was doing it, it happened to co-inside well with what I was doing...and I think that format was on a test for CS2 as "an alternative syntax for a for loop."

Blah

[quote=Lster]Indeed, I'm using Java at the moment for a project that requires the use of BigIntegers and BigDecimals. It is such a pain to write code like:

```
x = x.multiple(y) 
```

As opposed to:
```
x *= y
```
The BigDecimal class also seems to be missing a few features like non-integral powers so I have had to implement an Nth-root algorithm which is quite an effort indeed.[/quote]

Yeah, I definitely know what you mean.  I had to do the same.  Complete pain in the *** syntax wise, but otherwise basic, just using objects instead of primitive data types.

[quote=imdano]Yes, I know. I was trying to make it look as much like the java code as possible. Really, the most readable way would just be:

```
lst = [2, 45]
for x in lst:
    print x
```

Or, if you didn't need to do anything else with the list, this:
Code:

```
for x in [2, 45]:
    print x
```[/quote]

Ha, I'm the type that would do it the first way each time, just for structure.  Probably a bad thing because then sometimes I have trouble reading "shortcutted" code, if you know what I mean.  I tend not to super-wrap things in Java, like some people do & end up with

```
.method)))))
```

---

