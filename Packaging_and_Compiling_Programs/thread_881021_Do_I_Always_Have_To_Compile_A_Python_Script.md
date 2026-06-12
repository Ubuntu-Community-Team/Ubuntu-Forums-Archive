---
title: "Do I Always Have To Compile A Python Script?"
date: 2008-08-05
forum: Packaging and Compiling Programs
---

### Post by mikeMarek on 2008-08-05
Is there a way to make an executable or some other type of file that I can just click on instead of compiling a Python script every time. I have some games downloaded on Ubuntu and they are made completly made in Python. Something similar to that.

Best regards,
-Mike

---

### Post by wdaniels on 2008-08-05
> **mikeMarek said:**
> Is there a way to make an executable or some other type of file that I can just click on instead of compiling a Python script every time.

I'm not quite sure what you mean. You don't have to compile python scripts, you just run them interpreted and they get compiled into bytecode automatically as needed. You can compile them first if you want, but the only reason to do that is if you want to deploy them in a location that the interpreter will not have permission to save the compiled bytecode to.

---

### Post by tamoneya on 2008-08-05
why dont you just add this to the top of the file:```
#!/usr/bin/python
```That way you can just execute it by clicking on it.

Also I agree with mikeMarek in not quite understanding what you are asking for since python is interpreted.

EDIT:  Sorry mixed up users i meant wdaniels.

---

### Post by wdaniels on 2008-08-05
> **tamoneya said:**
> why dont you just add this to the top of the file:```
#!/usr/bin/python
```That way you can just execute it by clicking on it.

Now that you said it, I think that must be what he wants. Probably he is just a little mixed up about the terminology.

---

### Post by mikeMarek on 2008-08-05
Thanks, I'll try **#!/usr/bin/python**!

And what I mean for "not always compiling" is that, for example, when compiling a c++ script, the compiler generates an executable (or a.out on Linux) that you can click on to run, instead of always having to re-compile your code from your compiler. What I needed is something that will create a file or auto-compile the script when I click on it.

Cheers,
-Mike

---

### Post by OutOfReach on 2008-08-05
Well, this might not be exactly what you want but try this: Right click on the .py files and select Properties, and goto the Permissions tab, and enable Allow executing file as program. Now when you double-click the .py file you have options to Display, Run, Run in Terminal, or Cancel.

---

### Post by Vishal Agarwal on 2008-08-05
is Python a compiler ? I think it is an interpreter like PHP ?

---

### Post by tamoneya on 2008-08-05
if it helps you can look for the .pyc files(python compiled).  When you interpret a python file it typically generates this pyc file.

What is your purpose for wanting to do this?  Are you trying to minimize CPU load or something?  The overhead is very small.

---

### Post by OutOfReach on 2008-08-05
Yeah Python is an interpreted language.

---

### Post by wdaniels on 2008-08-06
> **mikeMarek said:**
> And what I mean for "not always compiling" is that, for example, when compiling a c++ script, the compiler generates an executable (or a.out on Linux) that you can click on to run, instead of always having to re-compile your code from your compiler.

> **tamoneya said:**
> if it helps you can look for the .pyc files(python compiled).  When you interpret a python file it typically generates this pyc file.

As tamoneya said, the interpreter creates precompiled .pyc files when you run the .py script, so it doesn't have to be recompiled the next time you run it. This is a "bytecode" however that is executed by the python runtime (CPython), which is not the same as a C/++ compiler which compiles to native processor instructions (and in the case of executables it also adds the necessary bootstrap code for setting up a stack and so on). Python is more like Java and .NET in that it uses an intermediary bytecode language instead. I don't know if there are any native machine code compilers for python...perhaps somebody else can answer that one?

---

### Post by tamoneya on 2008-08-06
> **wdaniels said:**
> As tamoneya said, the interpreter creates precompiled .pyc files when you run the .py script, so it doesn't have to be recompiled the next time you run it. This is a "bytecode" however that is executed by the python runtime (CPython), which is not the same as a C/++ compiler which compiles to native processor instructions (and in the case of executables it also adds the necessary bootstrap code for setting up a stack and so on). Python is more like Java and .NET in that it uses an intermediary bytecode language instead. I don't know if there are any native machine code compilers for python...perhaps somebody else can answer that one?

The only native machine code compiler that I know of for python is py2exe which as you can guess by its name makes exe files which is a windows solution.  Therefore instead of running with CPython you would be running through wine which is probably worse than CPython.

---

### Post by mikeMarek on 2008-08-06
What I want to do is create different programs (eg. a notepad with user-defined keywords) that I can store on my USB and run them from computer-to-computer and use those programs on computers who might not have Python.

---

### Post by tamoneya on 2008-08-06
> **mikeMarek said:**
> What I want to do is create different programs (eg. a notepad with user-defined keywords) that I can store on my USB and run them from computer-to-computer and use those programs on computers who might not have Python.

Are these computers windows, linux or both?

---

### Post by tamoneya on 2008-08-07
If you are just doing windows you could do two things: Make exe files with py2exe or you could use portable python: [http://www.portablepython.com/site/home/](http://www.portablepython.com/site/home/)

If you are using both I dont think you cant have code that is native in both platforms so I would use portable python for windows compatibility and then just hope that the linux computers have python (python is more common on linux computers than windows).

---

### Post by wdaniels on 2008-08-08
> **tamoneya said:**
> I dont think you can have code that is native in both platforms

Indeed, you can't. The bootstrap code on executables does all the stuff like loading dynamic libraries, opening input/output steams and setting up a stack in memory for function calls etc. Though the general process is similar between all operating systems, the specific instructions are completely different.

If you think that few of the machines on which your program needs to run will have the Python VM already installed, you might consider compiling to one of the more ubiquitous bytecode languages (see IronPython for CIL (.NET/Mono) and Jython for Java). But I suggest you stick with the standard Python and resolve the deployment dependency on CPython via an installation package as is normal.

---

### Post by indecisive on 2008-08-15
How about Pyrex?

---

### Post by wdaniels on 2008-08-15
> **indecisive said:**
> How about Pyrex?

That looks interesting, though I guess you would still have to modify the C to make it into an executable (rather than just a Python module extension), then compile it to numerous different executable images for each platform/architecture. Also, it still depends on the CPython runtime (unless I'm misunderstanding what it does), so I don't think it would be useful for the OP. To answer the OP more clearly:

[LIST]
[*]You can't make an executable that will work on any platform and architecture and without needing any runtime environment installed.

[*]If all your machines have .NET/Mono you could use C# or compile Python to CIL using IronPython.

[*]If all your machines have Java (JRE) you could use Java or compile Python to Java bytecode using Jython.

[*]Otherwise, if you can't install or assume the existence of any runtime environment, use C or C++ and compile to as many different executables as needed for all the platforms and architectures you expect to encounter.
[/LIST]

---

### Post by modmadmike on 2010-08-23
I know that this is an old thread, but to help anyone who still needs to do this use freeze.py (usually inside the python examples package) to make it into a series of c files (along with a makefile) next you just type ```
make
``` and end up with an native executable in the directory.

---

