---
title: "SCons vs CMake vs Autotools"
date: 2008-02-10
forum: Programming Talk
---

### Post by mb108 on 2008-02-10
What can I say, I was inspired by the CVS vs SVN thread. :)

 I know the ultimate answer to this is probably "It depends", or maybe "use an IDE and don't worry about it", but consider indulging the question for discussion's sake.

Personally, I need to choose one for a cross-platform project in C++, but I'm also interested in hearing what people think of these tools in general.

---

### Post by -Rick- on 2008-02-10
When I tried autotools I found it to be one big mess, and switched to SCons as soon as I found it. SCons is nice because it's using python: simple, flexible and cross platform.

I never really tried CMake though, but seeing that KDE is using it (or switching to it?) I guess it might be nice aswell :)

---

### Post by lnostdal on 2008-02-10
i'd say go for either cmake or scons .. i know and have used scons, but i've heard cmake is good and it does seem to be the "next thing" so i will look at cmake for my next project

auto* and make etc. is a vile piece of crap .. i cringe every time i see people struggle with it .. "but, but, but .. everyone else is using it!" -- dude -- cmake/scons is portable, ok? ..... :)
 
using cmake or scons you don't need an IDE that generates the nasty, huge and unmaintainable auto*/make stuff .. because the build-file you'll be editing "manually" is simple, small and to the point

---

### Post by hod139 on 2008-02-10
As others have said, stay away from the auto-tools.  Not only are they difficult to use, but they are not even cross platform.

As for Scons versus cmake, this probably comes down to preference.  Scons uses python, so if you already know python then the syntax is one less barrier. 

However, the philosophy behind the two build systems is different.  Scons produces executables on the native system.  Whereas cmake produces native build chain (e.g. makefile on linux, visual studio solution file on Windows).  Scons can optionally produce some of these two, but it wasn't initially designed to.  I also know that cmake is super easy to install on windows and Mac OSX, not sure about scons, haven't had to do it.

As for kde, they originally tried scons but were having a lot of trouble with it and switched to cmake.  (Note: I might be slightly biased since I know several people that work at kitware).

---

### Post by mb108 on 2008-02-11
Thanks for the info!
Just to add to the discussion, I found these recently:

[_Scons vs Others (no mention of CMake)_]("http://www.scons.org/wiki/SconsVsOtherBuildTools")
[_Why KDE switched to CMake_]("http://lwn.net/Articles/188693/")


I have been wanting to learn Python, but CMake looks very good + I'm sure I can find another excuse to learn Python.

---

### Post by hod139 on 2008-02-12
The fact that Scons uses python has it pros and cons.  If you know python, syntax is not a barrier.  However, this also means that Scons is dependent on python so:
1) users must install python (not an issue on ubuntu, but on other OSs it may be)
2) updates to python may break your scons scripts
3) updates to scons may break your scons scripts

Cmake on the other hand, has no dependencies (except c++, but since you are using this to build c++ not a problem).  It's syntax is simple, so learning that is not a problem.  

And remember, the philosophy behind the two systems is different, cmake generates native buildsystem files (which I prefer, but you may not), scons generates the native binaries.

---

### Post by pmasiar on 2008-02-12
This is good discussion, when new FAQ will be up and running, consider submitting it to "Compare developer's tools" section.

---

