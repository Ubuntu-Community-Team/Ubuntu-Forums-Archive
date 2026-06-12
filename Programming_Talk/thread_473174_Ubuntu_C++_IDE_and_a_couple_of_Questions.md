---
title: "Ubuntu C++ IDE and a couple of Questions"
date: 2007-06-13
forum: Programming Talk
---

### Post by DjKritical on 2007-06-13
Hi there,

I'm looking for a nice GUI for developing C++ however I have a few prerequisites and simple questions. :D

Firstly I am interested in what IDE's are available for Gnome?

-  Must work under Ubuntu...
-  The IDE must be GUI based...
-  Preferably some sort of debugging available...

Secondly I have a couple of questions regarding c++ development:

- Is it possible to write a Win32 program under linux using wine?
- Is there a standard set of libraries or something similar to Perls CPAN?

Basically I want to start development on a program which I want to run on Windows.. but I don't want to boot into windows... (I could possibly use VirtualBox... maybe... I'm low on ram though)...

Any ideas or suggestions would be greatly appreciated, ;)

Cheers

---

### Post by danhm on 2007-06-13
Take a look through the sticky about favorite IDEs for more suggestions, but both Code::Blocks and Anjuta have what you are looking for. Of the two, I'd recommend Code::Blocks (it's not in the repo, but its site has debs). I've never used the debugger in either, so I don't know how well it works. Eclipse with CDT might be good for you too, but I'm not sure if it has a debugger or not.


To write a win32 program, you'd just have to run an IDE/compiler in Wine -- Code::Blocks is available for Windows, too.

I know next to nothing about Perl but a quick Google search makes it seem like CPAN is a bunch of pre-existing code. C++, being one of the most popular and prevelant programming langauges, has quite an extensive standard library and there is plenty of code to look at. Is that what you are looking for?

---

### Post by cwmoser on 2007-06-13
Never heard of "Code Blocks"

Never was able to get the newest version of Ajunta to install -- just the older version in Ubuntu Synaptic.

Was able to use Monodevelop - a very good embedded RAD with a GTK# GUI designer.   I use it to write C# programs.  Not as good as the Windows based VB.NET RAD but still a very usable RAD.

Carl

---

### Post by DjKritical on 2007-06-13
> **danhm said:**
> I know next to nothing about Perl but a quick Google search makes it seem like CPAN is a bunch of pre-existing code. C++, being one of the most popular and prevelant programming langauges, has quite an extensive standard library and there is plenty of code to look at. Is that what you are looking for?

Pretty much that's right, Perl has a lot of inbuilt functionality... but some things get done so many times it's like reinventing the wheel...

CPAN is a collection of handy modules to do almost anything imaginable... the end product being extremely rapid development...

The last time I played with C++ I remember having to write a lot of stuff from scratch so I was wondering if there is anything similar to CPAN... a collection of C++ classes which have been developed by professionals....

I know that planetsourcecode.com has a lot of useful code... any others you know about?

---

### Post by danhm on 2007-06-14
I really like [C++ Reference](http://cppreference.com/). It has every function in the standard library, tells you what it does, what headers need to be included, and provides a short example. If I need a longer example, I can usually find something quickly enough just be searching around -- I haven't used a certain website for that.

---

### Post by slavik on 2007-06-14
If you need to write Windows code, then use Windows.

My main OS at work is Ubuntu, but I started learning VBScript (for admin tasks) and thus have VMWare Server running with Windows in it. (I do have 2GB RAM in that system though).

---

### Post by DjKritical on 2007-06-14
> **danhm said:**
> I really like [C++ Reference](http://cppreference.com/). It has every function in the standard library, tells you what it does, what headers need to be included, and provides a short example. If I need a longer example, I can usually find something quickly enough just be searching around -- I haven't used a certain website for that.

Ahh cheers, that's exactly what I need, that and a good book :)

> **slavik said:**
> If you need to write Windows code, then use Windows.

My main OS at work is Ubuntu, but I started learning VBScript (for admin tasks) and thus have VMWare Server running with Windows in it. (I do have 2GB RAM in that system though).

Yeah I must admit I was thinking about it and you're probably correct, especially considering one of my projects needs to run as a windows service... but yeah... not all of my projects are getting developed for Windows and where possible I will be using Ubuntu (Considering it's my main OS)

Thanks for the help everyone

---

### Post by adityakavoor on 2007-06-16
I'm searching for the x86_64  version of code::blocks .deb file 
does anyone know

---

### Post by Paul820 on 2007-06-16
Try here:[http://www.esnips.com/web/CodeBlocks]("http://www.esnips.com/web/CodeBlocks")
 The original link is here: [http://forums.codeblocks.org/index.php/topic,6184.0.html](http://forums.codeblocks.org/index.php/topic,6184.0.html), packages were made by Xaviou.

---

### Post by bvanpelt on 2007-06-18
> **DjKritical said:**
> Hi there,

- Is there a standard set of libraries or something similar to Perls CPAN?



Check out boost

---

### Post by WW on 2007-06-18
> **DjKritical said:**
> 
- Is it possible to write a Win32 program under linux using wine?


You can use the cross-compiler mingw32 to develop Windows programs from within Ubuntu.  The packages to install are **mingw32**, **mingw32-binutils**, and **mingw32-runtime**. Just be aware that if you want to use any libraries (outside the standard C/C++ libraries provided by mingw32), you will have to build them with mingw32.

I have a directory called $(HOME)/WinCrossCompile/local where I store my cross-compiled libraries.  This directory contains, among a few others, the subdirectories "include" and "lib".

For example, I have a program that uses libtiff.  Here is the sequence of commands that I used to cross-compile it.  This sequence is run in the directory in which I have extracted the libtiff tarball.  Note that the "make check" command will report some errors because it tries to run cross-compiled programs locally without wine.
```

$ ./configure --host=i586-mingw32msvc --prefix=$HOME/WinCrossCompile/local --disable-zlib --disable-jpeg
$ make
$ make check
$ make install

```

For developing a program with a GUI, I have used FLTK.  I wasn't able to cross-compile the FLTK library, but I found a pre-compiled "DevPak" and used that instead. I used the DevPak fltk-1.1.7-1cyd:  [http://devpaks.org/details.php?devpak=111](http://devpaks.org/details.php?devpak=111)
This provides the FLTK headers and libraries, compiled for Windows. I didn't keep notes about how I installed this.  However, the file fltk-1.1.7-1cyd.DevPak is just a tar file with bzip2 compression. You can extract the contents with the command
```

tar xvjf fltk-1.1.7-1cyd.DevPak

```
This will create several subdirectories, including the FL directory that contains the header files, and the lib directory that contains the compiled libraries.  I think I just copied the library files (libfltk*.a) to $(HOME)/WinCrossCompile/local/lib, and I copied the header subdirectory FL to $(HOME)/WinCrossCompile/local/include.

I use a Makefile, called Makefile.win32xc, to compile my FLTK program. Here is a simplified example.  Suppose your FLTK program has two C++ source files, say foo.cpp and func.cpp, and a header file foo.h.  Also, foo uses the library libtiff, cross-compiled as above. To cross-compile the program, you can use a Makefile something like this:

```

#
# Makefile.win32xc
#
# For cross-compiling foo
#
MINGWLIB=/usr/i586-mingw32msvc/lib
WINLIBS=$(MINGWLIB)/libgdi32.a $(MINGWLIB)/libole32.a $(MINGWLIB)/libuuid.a $(MINGWLIB)/libcomctl32.a $(MINGWLIB)/libwsock32.a
WINXCDIR=$(HOME)/WinCrossCompile/local

OBJFILES = foo.obj func.obj

foo.exe: $(OBJFILES)
        i586-mingw32msvc-g++ $(OBJFILES) $(WINXCDIR)/lib/libfltk.a $(WINXCDIR)/lib/libtiff.a $(WINLIBS) -mwindows -o foo.exe

foo.obj: foo.cpp foo.h
        i586-mingw32msvc-g++ -c -o foo.obj -I$(WINXCDIR)/include foo.cpp

func.obj: func.cpp foo.h
        i586-mingw32msvc-g++ -c -o func.obj -I$(WINXCDIR)/include func.cpp

```

Note that I explicitly listed all the required Windows libraries in the macro WINLIBS.  In theory, this information could be provided by the fltk-config command, but DevPak doesn't have it (and even if it did, I'm not sure if it would work in a cross-compile environment).

To compile foo, run the command:
```

$ make -f Makefile.win32xc

```
To run the program in Linux:
```

$ wine foo.exe

```

---

