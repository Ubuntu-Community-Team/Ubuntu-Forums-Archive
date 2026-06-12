---
title: "Development libraries &amp; tools for n00bs (like me!)"
date: 2008-02-03
forum: Programming Talk
---

### Post by shaggy999 on 2008-02-03
So I've been studying C++ and writing some smallish programs and getting used to the STL, but now I'm interested in writing some real applications. The one thing I'm not interested in doing is re-inventing the wheel. That's what open source is for!! So I call on peoples for information regarding good libraries/frameworks for application development so newbies don't have to filter through all the crud. I'm mostly interested in open source AND cross-platform libraries. I just spent... like... **8 hours** scrolling through synaptic and noting packages that look interesting. My hope is that by posting what I've found others can comment on their experience with these packages or offer alternatives.

So here we go....

**Open Dynamics Engine** - ODE is an open source, high performance library for simulating rigid body dynamics. It is fully featured, stable, mature and platform independent with an easy to use C/C++ API. It has advanced joint types and integrated collision detection with friction. ODE is useful for simulating vehicles, objects in virtual reality environments and virtual creatures. It is currently used in many computer games, 3D authoring tools and simulation tools. [http://www.ode.org/]("http://www.ode.org/")  **[BSD LICENSE]**

**Allegro** - Allegro is a game programming library for C/C++ developers distributed freely, supporting the following platforms: DOS, Unix (Linux, FreeBSD, Irix, Solaris, Darwin), Windows, QNX, BeOS and MacOS X. It provides many functions for graphics, sounds, player input (keyboard, mouse and joystick) and timers. It also provides fixed and floating point mathematical functions, 3d functions, file management functions, compressed datafile and a GUI. [http://alleg.sourceforge.net/]("http://alleg.sourceforge.net/")
**[GPL LICENSE?]**

**Simple DirectMedia Layer** -  Simple DirectMedia Layer is a cross-platform multimedia library designed to provide low level access to audio, keyboard, mouse, joystick, 3D hardware via OpenGL, and 2D video framebuffer. It is used by MPEG playback software, emulators, and many popular games, including the award winning Linux port of "Civilization: Call To Power."

SDL supports Linux, Windows, Windows CE, BeOS, MacOS, Mac OS X, FreeBSD, NetBSD, OpenBSD, BSD/OS, Solaris, IRIX, and QNX. The code contains support for AmigaOS, Dreamcast, Atari, AIX, OSF/Tru64, RISC OS, SymbianOS, and OS/2, but these are not officially supported.

SDL is written in C, but works with C++ natively, and has bindings to several other languages, including Ada, C#, D, Eiffel, Erlang, Euphoria, Guile, Haskell, Java, Lisp, Lua, ML, Objective C, Pascal, Perl, PHP, Pike, Pliant, Python, Ruby, Smalltalk, and Tcl. [http://www.libsdl.org/]("http://www.libsdl.org/") **[GPL LICENCE]**

**OpenAL** - OpenAL is a cross-platform 3D audio API appropriate for use with gaming applications and many other types of audio applications. [http://www.openal.org/]("http://www.openal.org/") **[GPL LICENCE]**

**POCO** - POCO, the C++ Portable Components, is a collection of open source C++ class libraries that simplify and accelerate the development of network-centric, portable applications in C++. The libraries integrate perfectly with the C++ Standard Library and fill many of the functional gaps left open by it. [http://pocoproject.org/]("http://pocoproject.org/") **[BOOST LICENSE]**

**Xerces-C++** - Xerces-C++ is a validating XML parser written in a portable subset of C++. Xerces-C++ makes it easy to give your application the ability to read and write XML data. [http://xerces.apache.org/xerces-c/]("http://xerces.apache.org/xerces-c/") **[APACHE LICENSE]**

**MESA** - Mesa is an open-source implementation of the OpenGL specification - a system for rendering interactive 3D graphics. [http://www.mesa3d.org/]("http://www.mesa3d.org/") **[MESA LICENSE?]**

**GLUT** - GLUT (pronounced like the glut in gluttony) is the OpenGL Utility Toolkit, a window system independent toolkit for writing OpenGL programs. It implements a simple windowing application programming interface (API) for OpenGL. GLUT makes it considerably easier to learn about and explore OpenGL programming. GLUT provides a portable API so you can write a single OpenGL program that works across all PC and workstation OS platforms. [http://www.opengl.org/resources/libraries/glut/]("http://www.opengl.org/resources/libraries/glut/") **RESTRICTIVE LICENSE!! - Just heard about freeglut, maybe that instead**

**wxWidgets** -  	

wxWidgets lets developers create applications for Win32, Mac OS X, GTK+, X11, Motif, WinCE, and more using one codebase. It can be used from languages such as C++, Python, Perl, and C#/.NET. [http://www.wxwidgets.org/]("http://www.wxwidgets.org/") **[[wxWindows LICENSE]**

I had found some others, but forgot to write them down. I'm interested in anything... debugging and unit testing, frameworks, etc.

---

### Post by Lster on 2008-02-03
I use SDL, OpenAL and OpenGL and would recommend them.

Some other stuff that may interest you:

[http://www.gnu.org/software/libc/](http://www.gnu.org/software/libc/)

[https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)

---

### Post by aks44 on 2008-02-03
[boost]("http://www.boost.org/") may be of great interest for you.

It is a large collection of portable C++ libraries which is generally regarded as the "unofficial" STL. If you don't want to reinvent the wheel then using boost is almost unavoidable.



Also, check the [Adaptive Communication Environment (ACE)]("http://www.cs.wustl.edu/~schmidt/ACE.html") which is aimed at concurrent communication software.> The communication software tasks provided by ACE include event demultiplexing and event handler dispatching, signal handling, service initialization, interprocess communication, shared memory management, message routing, dynamic (re)configuration of distributed services, concurrent execution and synchronization.

---

### Post by shaggy999 on 2008-02-03
Thanks for the input! Boost was one of the ones I forgot to write down. What's the best unit testing framework? Also what's a good cross-platform threading library? What do open source professionals use to allow scripting in their setups? I heard about one professional game that used Java as a scripting language...

---

### Post by CptPicard on 2008-02-03
> **shaggy999 said:**
> What do open source professionals use to allow scripting in their setups? I heard about one professional game that used Java as a scripting language...

Using Java sounds like a remarkably bad idea, and I'm not really even sure how that is supposed to work... integrating the JVM into your code must be extremely difficult.

Python is very popular, and they say Lua is also a good choice -- it's explicitly meant as an extension language...

---

### Post by aks44 on 2008-02-03
> **shaggy999 said:**
> Also what's a good cross-platform threading library?
boost, POCO and ACE all have threading libraries, and they're all portable. So the choice really is yours. :)


> **CptPicard said:**
> Python is very popular, and they say Lua is also a good choice -- it's explicitly meant as an extension language...
I had the occasion to write some Lua scripts, and I have to say the language didn't impress me at all, I found it quite clumsy. YMMV though.

Now when it comes to Python, boost has a specific library for [C++ / Python interoperability]("http://www.boost.org/libs/python/doc/index.html"). How useful it is exactly, I can't tell, but it may be worth looking into it.

---

### Post by shaggy999 on 2008-02-03
I'm not exactly sure how it works either. I'm assuming the attraction to Java as a scripting language lies in that it is very type-safe, memory management, all of that while also probably faster due to the compiled bytecode vs a full-on translation of code at runtime.

But for reference it was apparantly used in Vampire: The Masquerade and Chrome among others.

I figured someone would mention Python, I will look into Lua, thanks!

---

