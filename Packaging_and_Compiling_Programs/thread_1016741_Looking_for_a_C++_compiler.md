---
title: "Looking for a C++ compiler"
date: 2008-12-20
forum: Packaging and Compiling Programs
---

### Post by davideotape on 2008-12-20
Hi, I am just starting to learn c++, but the book I am learning from only suggests windows compilers. The compiler needs to be able to compile .cpp files so they can be run under ubuntu 8.10.

All help appreciated :D

---

### Post by jpmelos on 2008-12-20
Ubuntu has a C++ compiler built in by default.

Assuming you have a file called main.cpp use this command line:

```
g++ main.cpp -Wall -o main
```

Hope it helps you!

---

### Post by japtar10101 on 2008-12-20
> **jpmelos said:**
> Ubuntu has a C++ compiler built in by default.

Assuming you have a file called main.cpp use this command line:

```
g++ main.cpp -Wall -o main
```

Hope it helps you!

To add to that, it may help to know what's going on with this command.

*g++*: the program name.
*main.cpp*: your file you are trying to compile
*-Wall*: a "flag" (an indicator) to G++ to print all warnings.
*-o*: a flag that says, "make the executable to the name provided."
*main*: the generated executable.

To run your newly-created executable, simply run the command line:

```
./main
```

Assuming you used cout or printf, it'll print in the terminal your output.

---

### Post by gmclachl on 2008-12-21
Not sure if it is in there by default you might need to install build-essential.

---

### Post by davideotape on 2008-12-22
Thanks a lot guys, that works a treat :)

---

### Post by iharrold on 2008-12-29
David,

Just remember if you book is making MS Windows API calls they will not compile on the Ubuntu System.  Start of by making only [POSIX]("http://en.wikipedia.org/wiki/POSIX") compliant and [Standard C++]("http://www.cplusplus.com/reference/") function calls.  This will get you the basics of what you need to accomplish.

Other Libraries of note which I use:
[Poco]("http://pocoproject.org/")
[Boost]("http://www.boost.org/")
[glib]("http://library.gnome.org/devel/glib/2.18/")

Ubuntu Windowing API's which I use:
[wxWidgets]("http://www.wxwidgets.org/")

For C++ programming, I personally recommend, ["The C++ Programming Language"]("http://www.research.att.com/~bs/3rd.html") by Bjarne Strousstrupp

For wxWidgets programming, I personally recommend, ["Cross-Platform GUI Programming with wxWidgets"]("http://www.wxwidgets.org/docs/book/") by Smart and Hock.

Libraries like poco, boost and glib, posix and std::C++ can be cross compiled to different hardware architectures very easily... i.e. X86 to ARM-9 for example.  And I don't need to change my code to make them work on the different architecture.  [there are some caveats of course... ]

Hope this helps!

---

