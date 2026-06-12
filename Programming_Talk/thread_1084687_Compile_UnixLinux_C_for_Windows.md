---
title: "Compile Unix/Linux C for Windows?"
date: 2009-03-02
forum: Programming Talk
---

### Post by funkadelic on 2009-03-02
I would very much like to "port" dadadodo ([http://www.jwz.org/dadadodo/](http://www.jwz.org/dadadodo/)) to Windows. It is command-line only and "it should be fairly portable ANSI C" ...

How difficult would this be for a (mostly) novice programmer? Could someone point me in the right direction to get started?

Many thanks.

---

### Post by loganwm on 2009-03-02
You can start by downloading the source code and noting which libraries it uses to function.

IF there's one for example that doesn't work on Linux (or Vice Versa) you would need to rewrite that section using a comparable library or technique to attempt the same function.

I'm not very good at porting, but I understand the principles behind it, and after taking a look at this program it looks like a lot of universal functions which should port very nicely.

---

### Post by Simian Man on 2009-03-02
[Cygwin]("http://www.cygwin.com/") is your friend.

---

### Post by stevescripts on 2009-03-02
Along with cygwin - take a look at mingw/msys

---

### Post by monkeyking on 2009-03-02
yes go with mingw,
but you should know that there exist no gnu toolchain for win64.

---

### Post by Krupski on 2009-03-02
> **funkadelic said:**
> I would very much like to "port" dadadodo ([http://www.jwz.org/dadadodo/](http://www.jwz.org/dadadodo/)) to Windows. It is command-line only and "it should be fairly portable ANSI C" ...

How difficult would this be for a (mostly) novice programmer? Could someone point me in the right direction to get started?

Many thanks.

You may like this:

[COLOR="Blue"]**[http://www.q-software-solutions.de/downloaders/get_name](http://www.q-software-solutions.de/downloaders/get_name)**[/COLOR]

Then click "Get me to the downloads".

LCC Win32 is a nice 32 bit C/C++ compiler and IDE for Windows. 

I write small, simple utilities in C and usually develop and debug them in LCC (because it has a nice IDE and debugger), then I carry the code over to Linux.

Most time, it compiles just fine as-is under GCC.

Granted, what I write is VERY simple, console mode ANSI compatible stuff. More complex code may not port over so easily.

Give it a try and see if you like it. Be sure to get the "manual.exe" and the online documentation for it.

-- Roger

---

