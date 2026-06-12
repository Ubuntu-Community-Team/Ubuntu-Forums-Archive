---
title: "what is porting?"
date: 2008-07-06
forum: Programming Talk
---

### Post by pavel989 on 2008-07-06
What's the idea of porting? i mean like C++ is C++ on any operating system, but what about like sending an operating system to a mobile device? why is that such a task? is it because its dependent on the processor involved?

if so, how do ppl know what to do?

---

### Post by lisati on 2008-07-06
It's not just the processor, but each OS has its own style too.

---

### Post by henchman on 2008-07-06
> C++ is C++ on any operating system

Not completely true. Not all 'important' tasks can be done using standartized C++. For example File/Networking functions are platform (os) specific. 

So when you port a c++ Program from Windows to Linux, you have to replace the windows-specific File/Networking parts of it with a Linux-specific implementation. GUIs are another example.

When porting one OS to a different cpu-architecture, the OS sourcecode has to be assemblered to code which consists of commands specific for that cpu. All the standard libraries of that os have to be ported to the new architecture and every piece of code which was written in assembler and not a higher level language, may have to be rewritten, so to say, ported.

edit: another reason is that different cpu-architectures have a different amount of registers which may vary in length...

---

### Post by CptPicard on 2008-07-06
> **pavel989 said:**
> What's the idea of porting?

All platforms are not the same of course so you will have to alter the code in parts where it is not compatible.

> is it because its dependent on the processor involved?

That and all the rest of the hardware. The OS is after all the interface between hardware and application programs.

Then again, Linux for example is a good example of an operating system kernel where design has been modularized so that as much as possible is "just C" which is the same everywhere. You still have to rewrite the parts that aren't, of course.

> if so, how do ppl know what to do?

Well, let's just say that some people are very skilled and know what they're doing :)

---

### Post by pavel989 on 2008-07-06
ok im starting to get it all now. but like how do you get all the information neccessary to compile programs for an architecture?(guess im going really in depth)

---

### Post by slavik on 2008-07-06
> **pavel989 said:**
> ok im starting to get it all now. but like how do you get all the information neccessary to compile programs for an architecture?(guess im going really in depth)
you need the manual for the CPU (namely, the instruction codes)

---

### Post by Frak on 2008-07-06
Porting can be an issue for a various number of reasons. While it is true that a simple hello world program will run on any platform it is compiled under, something that relays hello world over the network would require multiple ports of the program to meet the need of the OS.

Also, some programs are written with proprietary libraries (such as .NET), and must then be ported to satisfy another OS (as such because Linux does not have .NET libraries). This usually involves foregoing the simple path of using libraries and manually detailing it out. This is usually why most .NET programs are not ported to Linux.

---

### Post by henchman on 2008-07-06
what about mono as being a vm for cil-code... isn't mono that far the be used widespread?

---

### Post by Frak on 2008-07-06
> **henchman said:**
> what about mono as being a vm for cil-code... isn't mono that far the be used widespread?
It's still very limited.

---

### Post by Master Chief on 2008-07-06
Here ya go: [http://en.wikipedia.org/wiki/Porting](http://en.wikipedia.org/wiki/Porting)

---

### Post by ceclauson on 2008-07-06
Just wanted to reply to the question about what parts of a program are platform dependent.

Some parts of it may be hardware issues, but you might have an issue with a platforms specific API.  An example of this would be if you're trying to write a GUI (graphic user interface) in C.  If you're writing it for a Windows machine, you'd program the Win32 API.  It has a library that you link against, a header file that you include (windows.h), along with a number of data types and function calls that allow you to create and interact with buttons, text boxes, check boxes, and all the parts that make up a GUI.

However, the program wouldn't work on linux.  If you wanted to port it to linux, you'd need to program a GUI API that works on, say, X, like GTK+.  This consists of a different library that you link against, header file that you include (GTK/GTK.h), and its own set of data types and function calls to manipulate equivalent "widgets".  So porting the program would consist of translating all of the Win32 types and calls to GTK types and calls in the source code.

---

### Post by pavel989 on 2008-07-06
hm fun stuff

---

