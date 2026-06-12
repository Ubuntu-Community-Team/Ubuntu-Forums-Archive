---
title: "Application Development in Ubuntu"
date: 2007-09-04
forum: Programming Talk
---

### Post by shoaibnawaz on 2007-09-04
I am new to Linux based programming. I have no idea how to work on rapid application development in Ubuntu. Java and Mono.net are latest rapid application development platforms are available on Linux. But the performance of Java and Mono.net application can be slow. I want to write native programming code for Linux as I use Win32 APIs or MFC on Windows.

Which is the best Graphical User Interface Toolkit for Linux?
How to write c/c++ code and compile?
How to write cross platform application for Windows and Linux as Firefox?

---

### Post by eentonig on 2007-09-04
Most development in Ubuntu is done with python.

For improved speed, some modules can then be (re)written in C/c++ and integrated to your program.

---

### Post by Sensenseppl on 2007-09-04
You might want to check out "Eclipse", which should be installed on your Ubuntu system by default.
Eclipse is a great development environment for java, c++ and many other languages. It also spares you by-hand compiling of your code.

Writing cross-platform applications with java isn't that hard. Simply look out for things like file-separators and carriage returns. If you want to program something with a GUI, check out [http://www.eclipse.org/swt/](http://www.eclipse.org/swt/).

I hope I could help and didn't give too much information about things you already know or didn't want to know in the first place. :)

---

### Post by Compyx on 2007-09-04
> **shoaibnawaz said:**
> 
Which is the best Graphical User Interface Toolkit for Linux?

There's a whole bunch of 'em, I personally prefer Gtk+ as I hate KDE, but there's other toolkits such as QT (KDE's GUI toolkit) and wxWidgets.
> 
How to write c/c++ code and compile?

You're kidding, right?

First off, there is no C/C++, there is C and there is C++, although C++ derives from C it has become a completely different language. The 'right' way to do something in C is usually the wrong way to do it in C++, and vice-versa.

If you want to learn C, I would suggest buying "The C Programming Language, 2nd Edition"  by Brian Kernighan and Dennis Ritchie, commonly referred to as 'K&R2'. Another good book on C programming is "Expert C Programming - Deep C Secrets" by Peter van der Linden, an excellent read and humorous too.
For C++ you can't go wrong with "The C++ Programming Language, 3rd Edition" by Bjarne Stroustrup.

Don't try to learn C or C++ from reading tutorials on the internet because most of them are horrible. Usenet on the other hand is an excellent place to learn about programming.

The usual cycle of programming is:

1. fire up text-editor.
2. enter code.
3. try to compile and run if it compiles.
4. debug
5. goto 3.

Here's a few nice flags to pass to gcc when compiling C:
```

-Wall -Wextra -Wundef -Wshadow -Wpointer-arith -Wbad-function-cast \
-Wcast-qual -Wcast-align -Wwrite-strings -Wconversion \
-Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations \
-Wpadded -Wredundant-decls -Wunreachable-code -Wformat-nonliteral \
-Wnested-externs -g -pedantic -ansi -O2

```

> 
How to write cross platform application for Windows and Linux as Firefox?

Write portable code. :D

Although it's usually not that simple. Just try to keep the non-portable portions of your code separated from the portable code. If, for example, you need code that deals with input/output that the standard C library can't handle, you would have a file that #include's conio.h on Windows and #include's ncurses.h on just about any real operating system.

Libraries such as Gtk+ are portable across many systems and a library such as wxWidgets even makes your application look native on whatever system it supports.

---

### Post by fct on 2007-09-04
> **shoaibnawaz said:**
> 
Which is the best Graphical User Interface Toolkit for Linux?

There is no "best".

If you want portability, use wxwidgets, it's ported to many operating systems, while some toolkits might not be available in certain ones.

If you are not scared of advanced C development and want your applications to use the same toolkit as the standard desktop in Ubuntu (GNOME), you can use GTK+. There are also bindings for C++ (gtkmm) that ease the learning curve.

For a nice C++ toolkit you might be interested in Qt, the one used in the KDE desktop.

> How to write c/c++ code and compile?

Install build-essential for the command line compiler and basic libraries. To get the toolkit development libraries, you can look for packages with the name of the toolkit and a "-dev" ending. Those are the development libraries you want to install.

Then you can install an IDE and/or editor. There are tons here. For IDEs, the suggestions are KDEvelop, anjuta and I personally suggest installing codeblocks:

[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

The next step, of course, is googling for tutorials of the chosen tools.

> How to write cross platform application for Windows and Linux as Firefox?

Choose a multiplatform toolkit and get acquainted with the differences in the other libraries that you will use, not to mention the different ways to do things in each OS. It's a nice idea to make abstractions for operations that will be different in each OS, like writing the configuration to the registry in Windows versus using GConf in the GNOME desktop.

---

### Post by LaRoza on 2007-09-04
> **shoaibnawaz said:**
> I am new to Linux based programming.

Which is the best Graphical User Interface Toolkit for Linux?
How to write c/c++ code and compile?
How to write cross platform application for Windows and Linux as Firefox?

0. See my wiki, some GUI stuff in there, especially Python
1. No "best", follow the other's advice
2. Use gcc, search the forums or web, plenty of info on that
3. Use a cross platform language, Python or Java, or code carefully in C or C++

---

### Post by pmasiar on 2007-09-04
> **shoaibnawaz said:**
> how to work on rapid application development in Ubuntu. Java and Mono.net are latest rapid application development platforms are available on Linux. But the performance of Java and Mono.net application can be slow. I want to write native programming code for Linux as I use Win32 APIs or MFC on Windows.

Looks like I have different definiton of "Rapid" in "rapid application development". For me, "rapid" means: I want to develop application quickly, even if performance will be not as good as if done in C. This is why I use high level language like Python. And in my case, web-based database apps, most of time is spent outside of my control, so Python **is** the "rapid" choice: Python works harder for me than any other language (wants less details for the same results). 

I am not sure how "rapid" is developing with more strict and picky languages, like Java or C#. "Rapid development" compared to what? C or assembler? Sure Java/C# code will run faster than Python code, but **development** will be slower. That's the whole point of switching to "rapid application development languages like Python or Ruby (or even Perl), IMHO. Do you have different experience?

---

### Post by shoaibnawaz on 2007-09-05
Thanks for all the friends who helped me.
Initially I downloaded Eclipse for Java and C, C++ programming. Both IDEs are installed on Ubuntu 7.04. But I think I need some kind of plugins for Eclipse and GCC Compiler for C/C++ and JDK for Java. I have to face a problem each time when I download some kind of .deb package. That is dependencies. On Windows platform we don't face such problems. How to tackle with these.

Shortly a DEB package has many dependencies those are not shipped along with the package. How can we analyze the complete list of dependencies and how to save time searching, downloading and then installing.

I faced this problem for Ubuntu deb package of GCC compiler.

I hope any one will help me to permanently adopt this OS for my personal and professional carrier.

Sho@ib Nawaz

---

### Post by LaRoza on 2007-09-05
> **shoaibnawaz said:**
> On Windows platform we don't face such problems. How to tackle with these.


On Windows, you don't even have the option, if you want freeware, you have to do a "search, hope, and pray".

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Tomosaur on 2007-09-05
> **shoaibnawaz said:**
> Thanks for all the friends who helped me.
Initially I downloaded Eclipse for Java and C, C++ programming. Both IDEs are installed on Ubuntu 7.04. But I think I need some kind of plugins for Eclipse and GCC Compiler for C/C++ and JDK for Java. I have to face a problem each time when I download some kind of .deb package. That is dependencies. On Windows platform we don't face such problems. How to tackle with these.

Shortly a DEB package has many dependencies those are not shipped along with the package. How can we analyze the complete list of dependencies and how to save time searching, downloading and then installing.

I faced this problem for Ubuntu deb package of GCC compiler.

I hope any one will help me to permanently adopt this OS for my personal and professional carrier.

Sho@ib Nawaz

Eclipse is available in the repositories, as are the various tools for C/C++ development:

Either use Synaptic to download eclipse and build-essential, or open up a terminal and type the following:

```

sudo apt-get install eclipse build-essential

```

Linux uses a 'package manager'. Stick to the repositories and you will be fine. If a piece of software is not in the repositories, then you will need to download and install it from the project website. If they have provided a .deb file, then this makes your life a little easier - they should tell you which dependencies you need and where to get them from.

---

### Post by gnusci on 2007-09-05
You first need to prepare your Ubuntu for developing, in the case of GCC you need to install some packages:

**$ sudo apt-get install build-essential** (compiling tools)
**$ sudo apt-get install freeglut3-dev**   (open gl)
**$ sudo apt-get build-dep xorg-dev**    (x11 for developing)

and maybe some extra libs:

**$ sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2**

I will recommend you to use FLTK for GUI development, it is very easy and fast tool kit:

[http://fltk.org/](http://fltk.org/)

You can download the last branch of FLTK 1.0.7 which is the most stable.

---

### Post by pmasiar on 2007-09-05
> **shoaibnawaz said:**
>  I have to face a problem each time when I download some kind of .deb package. That is dependencies. On Windows platform we don't face such problems. How to tackle with these.

I stick with Synaptic, and everything **just works**. I only wish installing on Windows was as simple as Ubuntu/Synaptic!

---

### Post by fct on 2007-09-05
> **shoaibnawaz said:**
> Shortly a DEB package has many dependencies those are not shipped along with the package. How can we analyze the complete list of dependencies and how to save time searching, downloading and then installing.

You don't do that if the package is in the repositories.

Then, as said before, you can use synaptic. Or, from the command line:

$ apt-cache search packagename
(look at the results, choose the package)
$ apt-get install package
(list of dependencies)
This extra packages will be downloaded and installed, are you sure? [Y/n]

And done. :)

With a downloaded .deb you can do:

$ dpkg -i package.deb
(Error about dependencies not installed)
$ apt-get -f install

And then if the required packages are in the repositories, they will be installed as in the above example.

If not, well, just repeat. But I only face those problems when using unstable software, like the codeblocks nightly builds that require you to add a repository for the latest wxwidgets libraries.

---

### Post by moephan on 2007-09-05
This should be easy to answer. Use:

1. Glade for your GUI layout
2. Python for your language and libraries
3. Gedit for your editor
4. pdb for your debugger
5. distutils for packaging

Cheers, Rick

---

