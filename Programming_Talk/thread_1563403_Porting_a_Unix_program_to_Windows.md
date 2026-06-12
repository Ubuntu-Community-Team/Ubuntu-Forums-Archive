---
title: "Porting a Unix program to Windows"
date: 2010-08-29
forum: Programming Talk
---

### Post by James78 on 2010-08-29
Hi, I'm making a program, and was wondering exactly how I would port it to work on Windows.

1) I'm using CMake to configure the build environment. I'm using some findfoo.cmake modules, which are finding /usr/lib/libfoo.so, and linking it when the program is built.

2) I included the header file(s) into the program, and link the library, and that allows me to use the libraries functions.

Now, my goal is this:
[LIST]
[*]To cross compile the program to Windows executable (32/64 bit) format, easy to do with Ming.
[*]To link the windows version of the library (.dll) with the program, if I am using Ming to compile, and have the library be inside the same directory as the executable, and of course have the program work.
[/LIST]

To do this, I'd obviously need to modify the CMake files to link with the .dll's instead, but ONLY if I'm compiling with Ming, or if the platform is Windows. Also, I'm not sure if the program would correctly load the .dll's if they're in the same directory, I don't know how that exactly works, but my guess is leading towards: It will work fine.

So, it needs to link to a dll with a specified path (we can probably do this in the findfoo.cmake module, but I need to know how to detect when compiling with Ming or if we're on the Windows platform), then have CMake copy it to the directory the executable is output in (should be easy, just edit the CMakeLists.txt that outputs the executable, it _should_ copy the dll's over to the right place as well)

My ideas aren't perfect here, but they should convey what I mean and what I need to do to get this to work. Anyways, does anyone have any ideas where to start? Tutorials, etc (perhaps if this will even work at all)? Help will be greatly appreciated. :)

---

