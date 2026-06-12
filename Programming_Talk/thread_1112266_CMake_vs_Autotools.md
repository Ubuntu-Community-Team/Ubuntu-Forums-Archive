---
title: "CMake vs Autotools"
date: 2009-03-31
forum: Programming Talk
---

### Post by jfbilodeau on 2009-03-31
Hello World,

I've been using make/autotools for a couple of years now, and I feel quite comfortable using them. However, I'm starting to notice CMake, and recently learned that most (all?) of KDE moved to CMake.

I'm curious to know if anyone has had any experience with CMake / autotools / makefiles, and what you have to say.

J-F

---

### Post by Delever on 2009-03-31
I can say that it is annoying to learn new build systems. (sorry, OT)

---

### Post by jfbilodeau on 2009-03-31
> **Delever said:**
> I can say that it is annoying to learn new build systems. (sorry, OT)

That was my first reactions ;)

I'm trying to keep an open mind.

---

### Post by Max Carey on 2009-03-31
My only experience with CMake is wishing more people used it. I work on Linux and Windows machines, and trying to build third-party code natively on Windows is a huge pain using autotools. I think more and more projects are moving to CMake for this very reason (e.g. Trilinos).

---

### Post by monkeyking on 2009-03-31
The makefiles generated with cmake  actually has colors.

Some  people will tell you that cmake stands for cross compile make.
This is not true, it stands for color make. ;)

If you are writing your program for one compiler one os.
This funky color stuff will be the only real benifit.

If you however plan to use a windows system with your program then cmake should have support for various versions for visual studio,
which is the std on windows.

There are currently no free c/c++ 64bit c/c++ compilers for windows other than the visual studio. And as far as I can tell the autotools build system requires the gnu tool chain, which is not available on 64bit windows.

---

### Post by Zugzwang on 2009-04-01
> **monkeyking said:**
> There are currently no free c/c++ 64bit c/c++ compilers for windows other than the visual studio. And as far as I can tell the autotools build system requires the gnu tool chain, which is not available on 64bit windows.

That's not precisely true. As far as "free as in beer" is concerned, there's the "Borland C++ Compiler 5.5". Apart from that, you have the GNU toolchain available in Cygwin.

If you've got relatively simple makefiles (i.e., you are just compiling code and no resource files or whatsoever) and you want to compile for both Windows and Linux, qmake might also be an option (although it is a little bit out-dated).

---

### Post by monkeyking on 2009-04-01
> **Zugzwang said:**
> That's not precisely true. As far as "free as in beer" is concerned, there's the "Borland C++ Compiler 5.5". Apart from that, you have the GNU toolchain available in Cygwin.

There exists no 64 version of cygwin.

[http://www.cygwin.com/faq/faq-nochunks.html#faq.what.supported](http://www.cygwin.com/faq/faq-nochunks.html#faq.what.supported)
> 
Cygwin can be expected to run on all modern 32 bit versions of Windows, except Windows CE. This includes Windows 95/98/ME/NT/2000/XP/2003 and the WOW64 32 bit environment on released 64 bit versions of Windows. As far as we know no one is working on a native 64 bit version of Cygwin. 


There are also a nice sun studio compiler for c/c++ which is free as in beer and speach.
But the problem is that autotools require a gnu tool chain,
and that exists only as 32 bit on windows.
So if you use autotools, there are no way to compile 64bit on windows.

That is:
It might be possible,
but it is not supported,
and definently not recommend for large deployments.

---

### Post by svalovic on 2009-07-21
I use cmake in Debian to produce normal linux and win32 binary packages and .deb, .rpm, win32 setup packages with nsis of my little application (chessratingcalc.sourceforge.net). So far I am very satisfied with it. I have only one problem with the win32 setup, it doesn't create correct Start menu entry (application opens in console), but I am sure that this is my mistake. Now I plan to try cmake on ubuntu just to create deb packages for more popular ubuntu. I have never used autotools.

---

### Post by Sockerdrickan on 2009-07-21
> **monkeyking said:**
> There are currently no free c/c++ 64bit c/c++ compilers for windows other than the visual studio. And as far as I can tell the autotools build system requires the gnu tool chain, which is not available on 64bit windows.
bs [ftp://ftp.equation.com/gcc/gcc-4.5-20090521-64.exe](ftp://ftp.equation.com/gcc/gcc-4.5-20090521-64.exe)

---

### Post by dribeas on 2009-07-21
We use CMake extensively for our cross-platform applications, and I must say that I even use it for simple test applications due to the simplicity of use.

One of the great advantages we gain with CMake is that it can generate project files for different IDEs. I mostly develop with vi/make under linux and vi/make or xcode under macosx. Some coworkers prefere Eclipse-CDT or KDevelop in linux. With the appropriate 'generator' parameter, cmake will provide project files for each of those (and some other) IDEs.

Last CMakeLists.txt file I created was for a simple boost:: program_options test, and the full contents are this:

```

add_executable( test test.cpp )
target_link_libraries( test boost_program_options )

```

As you see it is rather simple (trick, boost is installed in the system path, else there would be a couple more lines to request the cmake system to locate boost, add the include and library path directives).

---

