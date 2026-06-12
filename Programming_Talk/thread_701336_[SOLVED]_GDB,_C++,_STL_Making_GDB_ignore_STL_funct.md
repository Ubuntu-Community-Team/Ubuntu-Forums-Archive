---
title: "[SOLVED] GDB, C++, STL: Making GDB ignore STL functions"
date: 2008-02-19
forum: Programming Talk
---

### Post by Zugzwang on 2008-02-19
Hi all,

Imagine a command sequence of the following form (in C++ using STL):

```

std::vector<MyOwnClass> myObjects;
[...]
myObjects[myIndex]->myFunction();

```

Assume that I want to debug my code. When being in line 3, stepping into the line will cause a lot of steps in some STL functions before actually reaching the function MyOwnClass::myFunction(), but stepping over will not cause the debugger to "visit" the function. Since I of course do not want to debug the STL, I'd like the debugger to only stop at points in the code I wrote myself. Of course I could make a breakpoint in MyOwnClass::myFunction() but it is very tedious to do this all the time.

Do you know of any possibility to let GDB ignore certain source files (e.g. stl_vector.h) such that it will never stop at places in these files. The man pages of GCC and GDB didn't reveal any tricks (to me), neither did google.

I'm using G++ (with options -O0 and -g2 or -g3) and GDB under KDevelop. The system runs gutsy.

Oh, and no recommendations to use Python, please. :lolflag: Speed and memory consumption are important for the application I'm developing.

Thanks,
 Zugzwang

---

### Post by WitchCraft on 2008-02-19
i don't know how to do it with gdb, but the usual thing to do under this circumstances is to set a BREAKPOINT just before myfunction() is called.

I found the following page by searching google for gdb and breakpoint:

[http://vmlinux.org/crash/mirror/www.objsw.com/docs/gdb_29.html](http://vmlinux.org/crash/mirror/www.objsw.com/docs/gdb_29.html)

What you need is either
break function 
or
break filename:linenum

---

### Post by lnostdal on 2008-02-19
> **Zugzwang said:**
> 

```

std::vector<MyOwnClass> myObjects;
[...]
myObjects[myIndex]->myFunction();

```

Assume that I want to debug my code. When being in line 3, stepping into the line will cause a lot of steps in some STL functions before actually reaching the function MyOwnClass::myFunction(), but stepping over will not cause the debugger to "visit" the function. Since I of course do not want to debug the STL, I'd like the debugger to only stop at points in the code I wrote myself. Of course I could make a breakpoint in MyOwnClass::myFunction() but it is very tedious to do this all the time.


split line 3 into two separate lines and use a function pointer ( [http://www.newty.de/fpt/index.html](http://www.newty.de/fpt/index.html) ) to call the method 

..then use "Step Over" on line 3 .. and "Step Into" on your new line 4

> 
Oh, and no recommendations to use Python, please.  Speed and memory consumption are important for the application ..


yeah, well -- do what you want .. i'd never mention this if you did not mention your reasons, "time and space" as if this was not available elsewhere - but here we go

to maintain sanity, hair and an interest in programming as something beautiful and elegant i dropped C++ and i now use C (with [http://library.gnome.org/devel/glib/stable/](http://library.gnome.org/devel/glib/stable/) as a container library) for the "low-level stuff"      ....way .. less .. problems

..and there are other languages out there that are compiled and fast and i actually use them instead of C most of the time - even for "critical stuff".. they are actually faster than C in some cases

..if i still find that i'd like to try to optimize parts of my software by rewriting them in C i can - because most languages can easily communicate with software written in C (which is not the case for software written in C++ - it *can't even* communicate nicely with *itself* as you see by the function pointers needed for methods for instance)

good luck anyhow .. i stopped bending over and taking **** from C++ a long time ago after function pointer (or other unfixable or un-flexible problem) nr. 10 000 - and i never looked back

---

### Post by dwhitney67 on 2008-02-20
> **lnostdal said:**
> 
..if i still find that i'd like to try to optimize parts of my software by rewriting them in C i can - because most languages can easily communicate with software written in C (which is not the case for software written in C++ - it *can't even* communicate nicely with *itself* as you see by the function pointers needed for methods for instance)


I'm not quite sure what you mean here?  Perhaps you had a bad experience integrating C++ and C.  Trust me... it can be done... and often is.

As for the OP's question, it is quite likely that the debugging symbols from the C++ libraries (and other libraries too) were not stripped away after they were built by the Ubuntu curators.  I verified that the same is true with Fedora.  Perhaps some people prefer to have these symbols available.

When source packages are used to build libraries, often the -g compiler option is enabled, and thus the resulting libraries are "polluted" with debugging symbols.  One way to remove these is to run the following bash command (not that I would recommend it on Ubuntu!):

```
/bin/find /{,usr/}{bin,lib,sbin} -type f -exec /bin/strip --strip-debug '{}' ';' 
```

I use a similar command when I build a Cross-Compiled Linux From Scratch (CLFS) distro.

Back to the OP, simplify your code to make it easier to debug.  For instance:

[PHP]vector< MyOwnClass * > myObjects;
//...
MyOwnClass *temp = myObjects[ myIndex ];
temp->myFunction();   // set a break-point on this line[/PHP]

Also I recommend using "ddd".  It is the GUI front-end to "gdb".

```
sudo apt-get install ddd
```

---

### Post by lnostdal on 2008-02-20
> I'm not quite sure what you mean here? Perhaps you had a bad experience integrating C++ and C. Trust me... it can be done... and often is.

no, that is not what i'm talking aboutt .. but never mind -- it is off topic and not that interesting

---

### Post by Zugzwang on 2008-02-20
Thanks to everybody for your answers. :KS

@dwhitney67: The STL is a template library define in header files, so their symbols are so to speak always available. But I'll try stripping them selectively from my executable somehow. That might be a nice tip. Also I'm already using KDevelop as debugging GUI.

@WitchCraft: The problem with this approach is that commands are always executed as a whole. So I cannot selectively step into the second part of the evaluation ("myFunction()") while leaving out stepping into the first part ("myObjects[myIndex]"). Since the "[]" operator is overloaded this is actually a function.

@lnostdal: Ok, this is a nice but straight-forward trick. :-) Hopefully the compiler optimizes such lines for compiling the "release" version. BTW: I simply can't image why you prefer C: No variable definitions in the middle of the line, the possibility to call functions without prototype given beforehand and no automatic destructor calling. I do not know why you prefer this even though you *can* have all the C goodies in C++ as well (well, except for these unchecked stuff). No one forces you to use classes that overload operators, etc. I can only imagine that your "kernels" (how short pieces of code that are executed extremely often and therefore need to be optimized) are quite small, so it doesn't matter.

---

### Post by lnostdal on 2008-02-20
> **Zugzwang said:**
> 
BTW: I simply can't image why you prefer C: <snip>  I do not know why you prefer this even though you *can* have all the C goodies in C++ as well   .


if i while programming C start to miss some of the "high level" features C++ try to offer i am close to the point where i should be switching back to my original higher-level language 

..at that point C++ is not an option for me .. it has fooled me too many times with its lies about ability to abstract and handle complexity in a scalable, sane and safe manner .. i solve the same problems over and over and over and over again in C++; just at different "layers" in my code! ..  no matter how much templates, meta-programming and whatnot i throw at it i ultimately never escape its backward-compatibility with C ... 

come to think of it, maybe the backward compatibility thing you mention as an assert actually  is the real or fundamental reason why i do not use C++ or the reason for its problems, but i haven't thought hard about this in a long time .. anyway i regard it as an unnecessary hybrid that tries to both be high-level and low-level at the same time and fails at it .. i see no need for it at all really

people and organizations that have more or less unlimited time or resources to throw at it might succeed using it .. but i do not and i have not .. disregarding this i see almost no beauty in it and this is also important to me

> **Zugzwang said:**
> 
I can only imagine that your "kernels" (how short pieces of code that are executed extremely often and therefore need to be optimized) are quite small, so it doesn't matter.


yes, inner or maybe main loops written in C .. then i have callbacks, handlers or event-handlers in the higher-level code that take all the hard complex decisions before returning control back to the C side .. it works well, and i do not miss C++ at all

---

### Post by Zugzwang on 2008-02-20
> **lnostdal said:**
> ..at that point C++ is not an option for me .. it has fooled me too many times with its lies about ability to abstract and handle complexity in a scalable, sane and safe manner .. i solve the same problems over and over and over and over again in C++; just at different "layers" in my code! ..  no matter how much templates, meta-programming and whatnot i throw at it i ultimately never escape its backward-compatibility with C ... 

Well, you're right as far as this strange mixture of abstraction and low-level programming is concerned - Its reason lies in the main idea: "High level but without notifiable speed reduction (if you really use all the tools the language provides)". But once you got used to it... :-)

_**Solution to the original problem**_
After your good tips I've managed to write a small Python script that strips the STL symbols (and some more C++ stuff) from the executable:

[PHP]
#!/usr/bin/python
#
# Strips all STL symbols from the object file %1

import os
import sys

if sys.argv.__len__()!=2:
    print "stl_debug_symbol_remove: Expected precisely the object file"
    sys.exit()

info = os.popen("nm "+sys.argv[1]+" -a -l -s")

cmdLine = "strip"

try:
    for line in info:
	stuff = line.strip().replace('\t',' ').split(" ")        
	if stuff.__len__()==4:
	    if stuff[3].count("/usr/include/c++/")>0:
		cmdLine = cmdLine + " -N "+stuff[2]

    # Strip symbols
    cmdLine = cmdLine + " " + sys.argv[1]
    print "stl_debug_symbol_remove.py: Calling: " + cmdLine
    os.system(cmdLine)

finally:
    info.close()[/PHP]    

Hey, my first Python script *ever*! :-) Since I did it without really going through the tutorials, it might be ugly but works. Simply adding it to the makefile to be called after making the executable solves the problem.

---

### Post by lnostdal on 2008-02-20
> ... but once you get used to it ...

mh, i don't need this talk from you or anyone else

i'm gonna move on to another thread now .. (edit: or well, get back to what i should be doing really)

---

