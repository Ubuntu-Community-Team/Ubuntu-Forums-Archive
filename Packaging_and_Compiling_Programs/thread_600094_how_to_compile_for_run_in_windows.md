---
title: "how to compile for run in windows"
date: 2007-11-01
forum: Packaging and Compiling Programs
---

### Post by HokeyFry on 2007-11-01
hi, i need to compile thunderbird from source...... but haha

small catch

i need to compile it for running in windows. how does one do this in linux, seeing as compiling from source in windows has always, ALWAYS, been a pain in the [rear] for me, unless i write the code myself.

Or if someone could tell me how to compile it via Dev C++ in windows that would be very much appreciated

---

### Post by jespdj on 2007-11-02
Cross-compiling for Windows is not easy, I don't know if it is even possible.

[This page](http://developer.mozilla.org/en/docs/Windows_Build_Prerequisites) says that you need Microsoft Visual Studio for compiling Thunderbird for Windows.

Maybe the easiest way to get this working is downloading [Microsoft Visual Studio Express Edition](http://msdn2.microsoft.com/en-us/express/default.aspx), which is the free version of Visual Studio, and see if you can compile it on Windows with that.

---

### Post by sq377 on 2007-11-08
I had to do this for my c++ class.  

sudo apt-get install mingw32
This will install gcc and g++ and alot of other tools you need for compiling.
Their naming convention is a little wierd, i586-mingw32msvc-(toolname such as g++ or gcc).

Go into the thunderbird makefile and make sure all tools point to the mingw alternatives.  Though thunderbird isn't exactly as light weight as my little c++ programs and it uses a gui so I dont know how all that works.  But hope this gives you a start.

---

