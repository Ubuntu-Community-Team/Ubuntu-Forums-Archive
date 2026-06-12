---
title: "Running my Ubuntu-made C program in Windows"
date: 2009-06-10
forum: Programming Talk
---

### Post by rixmaestro on 2009-06-10
Hi. How can I make my own C program run in Windows without using CygWin or the likes? Do I need to make some dll's or installers? If yes, how? Sorry if I have too much questions.

---

### Post by amingv on 2009-06-10
What sort of program is it? A program written in Ubuntu with standard C would only need to be compiled with a Windows compiler to run there.

If that's the case, try compiling it with [Mingw](http://www.mingw.org/) in Windows.

---

### Post by rixmaestro on 2009-06-10
yup, it's just a simple program written in C. So I still need to compile using Mingw in Windows.  But, is it possible to compile my program in Ubuntu, rename with .exe, then run it in Windows?

---

### Post by amingv on 2009-06-10
> **rixmaestro said:**
> yup, it's just a simple program written in C. So I still need to compile using Mingw in Windows.  But, is it possible to compile my program in Ubuntu, rename with .exe, then run it in Windows?

No. It won't work.

If you must compile it in Ubuntu, your best bet would be to use a Virtual Machine, or install Mingw through wine.

---

### Post by Habbit on 2009-06-10
Ubuntu has a mingw compiler package, it's called "mingw32". Install it, then build your executables with "i586-mingw32msvc-gcc" instead of gcc. The output executables will be Windows binaries, you will need Wine to run them on your Ubuntu install.

---

### Post by The Cog on 2009-06-10
Habbit is right. 

To compile for windows:
install package mingw32
Compile with:
i586-mingw32msvc-gcc -Wall -o myprog.exe myprog.c

I did it a couple of weeks ago with help from this forum. Works a treat.

---

### Post by Krupski on 2009-06-10
> **rixmaestro said:**
> Hi. How can I make my own C program run in Windows without using CygWin or the likes? Do I need to make some dll's or installers? If yes, how? Sorry if I have too much questions.

If your code is relatively simple console mode stuff (and written in ANSI-C without all the non-standard bells and whistles), then you can simply recompile your code into native Win32 format with a Windows based compiler.

Now, here's a NICE compiler for Windows... and it's free!

[[COLOR="Blue"]**_CLICK HERE_**[/COLOR]]("http://www.q-software-solutions.de/downloaders/get_name") then click the "Get me to the downloads" button.

Download "LCC-WIN32" and "USER MANUAL".

LCC also has a nice built in IDE and debugger... in fact I develop most of my C programs (small utilities in console mode) in LCC, then re-compile the working code with GCC in Linux.

Good luck!

-- Roger

---

### Post by Sockerdrickan on 2009-06-11
Actually the best solution really would be to download a nice build of the latest GCC from [http://www.equation.com/servlet/equation.cmd?call=fortran](http://www.equation.com/servlet/equation.cmd?call=fortran) you get gcc, g++ make gdb etc I believe, all latest and greatest

---

