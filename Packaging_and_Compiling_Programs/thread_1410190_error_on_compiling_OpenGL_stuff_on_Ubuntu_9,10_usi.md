---
title: "error on compiling OpenGL stuff on Ubuntu 9,10 using Code::Blocks"
date: 2010-02-18
forum: Packaging and Compiling Programs
---

### Post by wcharm1987 on 2010-02-18
Hello.
I got some sources from book and tried to compile it on Ubuntu using Code::Blocks..
However, I got an error message as following:

---------------------------------------------------------------------------------------
error: windows.h: No such file or directory
---------------------------------------------------------------------------------------

I know the problem but do not know how to fix it.. I tried to find statement "#define WIN32_" but there were no definition like that in all of my source and header files.
Here is my main.cpp source.. It should run code after 'else' statement, but it runs codes after '_WIN32', which shouldn't be.

---------------------------------------------------------------------------------------
#define WIN32_LEAN_AND_MEAN
#define WIN32_EXTRA_LEAN

#define GLX_GLXEXT_LEGACY //Must be declared so that our local glxext.h is picked up, rather than the system one

#ifdef _WIN32
#include <windows.h>
#include "glwindow.h"
#else
#include "glxwindow.h"
#endif

#include "example.h"

#ifdef _WIN32
int WINAPI WinMain(HINSTANCE hInstance,
                   HINSTANCE hPrevInstance,
                   LPSTR cmdLine,
                   int cmdShow)
{
#else
int main(int argc, char** argv)
{
#endif
----------------------------------------------------------

Anyone know how to avoid WIN32_ ?
Thanks

---

### Post by dearingj on 2010-02-24
Look in your project's build options. Under the 'compiler settings' tab, there should be a tab labeled '#defines', which may be where _WIN32 is being defined.

---

