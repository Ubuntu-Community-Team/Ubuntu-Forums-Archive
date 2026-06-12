---
title: "developing and compiling c,c++ programs"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by zyandeep on 2013-01-14
i am an absolute newbie to ubuntu! please guide me in how to compile and run c,c++ programs in ubuntu. and also tell me which is the best c,c++ IDE for ubuntu.
 
currently, i am using ubuntu 12.10

---

### Post by Impavidus on 2013-01-14
You need **gcc** (the compiler, should be installed by default) and development versions of libraries to get the header files. Some should be installed by default, but not the development versions of all libraries installed on your computer. Next write your source code, write a Makefile (ask google if you don't know how, for small programs I call gcc directly), use **make** and it should compile (or give you an error). The standard debugger is **gdb**.

Concerning IDEs: I've never used one as I prefer separate programs running in terminals, but there are IDEs available. In that case you don't need to write a Makefile and use a separate debugger, because they are integrated in your IDE.

---

### Post by john rosswrock on 2013-01-14
you can use eclipse...it is a good platform and great app that runs c,c++,java,and many more... search for eclipse classic for linux on google from there you can get the download link and the best part is eclipse is an open source software.....   And happy programming..:)

---

### Post by tlhIngan on 2013-01-14
> **john rosswrock said:**
> you can use eclipse...it is a good platform and great app that runs c,c++,java,and many more...
Ooh! Can't eclipse compile to run on Android phones as well?
\\:D/

---

### Post by john rosswrock on 2013-01-14
> **tlhIngan said:**
> Ooh! Can't eclipse compile to run on Android phones as well?
\\:D/

you need to install android-sdk for that and link it with eclipse

---

### Post by squakie on 2013-01-14
It's all just opinion, so I'll throw my favorite out there - don't claim it's any better than anything else (for all I know it could be worse ;) ), I use CodeBlocks - like others I'm sure it has built in debugger, etc., and can be used for multiple languages.

BTW - while the package description doesn't say so any more, your best bet is to install the build-essential package.  It has as dependencies the compilers, etc., so all of that will automatically be installed.  I have seen previous posts here where gcc, g++ where supposedly installed by default, but they were missing some of the things that are included as dependencies when you install build-essential.  It's all of those dependancies you want.

---

### Post by zyandeep on 2013-01-14
**Thanx to all the buddies for their support... :)**
 
but one thing i want to know, all those compilers running in windows, can directly be installed in ubuntu???

---

### Post by von Corax on 2013-01-14
> **zyandeep said:**
> **Thanx to all the buddies for their support... :)**
 
but one thing i want to know, all those compilers running in windows, can directly be installed in ubuntu???
For the most part, no, nor would there be much point. Compilers that run under Windows build executables that run under Windows, and compilers that run under Linux build executables that run under Linux, and never the twain shall meet.

The closest you're likely to get is gcc on Cygwin on Windows, or gcc on minGW on Windows, as both those packages provide a Unix-*like* environment for programs to execute in.

---

### Post by squakie on 2013-01-15
> **von Corax said:**
> For the most part, no, nor would there be much point. Compilers that run under Windows build executables that run under Windows, and compilers that run under Linux build executables that run under Linux, and never the twain shall meet.

The closest you're likely to get is gcc on Cygwin on Windows, or gcc on minGW on Windows, as both those packages provide a Unix-*like* environment for programs to execute in.

I've done some cross-platform development using GTK for the GUI functions, then installed both minGW and Cygwin along with the GTK for Windows package and taken the same source over and just compiled in minGW.  Fortunately the programs I have done were able to then execute in the normal Windows environment so I didn't have to (or the other users) run them in a psuedo-Linux environment like minGW, etc..

---

### Post by RedRat on 2013-01-15
I note that both Eclipse and CodeBlocks are in the Synaptic Repos.

---

### Post by squakie on 2013-01-15
Yep - I believe there are several.  I just stuck with the one I liked for what eve reasons.

---

