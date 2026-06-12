---
title: "Python: how can I create a bin file of a python program?"
date: 2007-10-17
forum: Packaging and Compiling Programs
---

### Post by holihue on 2007-10-17
Is there a way to create a bin file of a Python program?

I want a bin file like when you compile a program from source.



Thanks

---

### Post by Foxmike on 2007-10-18
Since python is a scripting language, it doesn't produces binaries.  It is compiled at run-time.
 
Tho, you still can get some .pyc files, as I understood those are semi-compiled files.  Unless you want to close the sourcre from being seen/edited, I don't see why someone would do such a thing, tho.

---

### Post by holihue on 2007-10-19
> **Foxmike said:**
> Since python is a scripting language, it doesn't produces binaries.  It is compiled at run-time.
 
Tho, you still can get some .pyc files, as I understood those are semi-compiled files.  Unless you want to close the sourcre from being seen/edited, I don't see why someone would do such a thing, tho.

OK, Thank you.:)

---

### Post by pmasiar on 2007-10-19
Binary for which platform? There are compilers, which can compile .pyc further to real binaries (like psyco), but not many people bothers with it. Why you need it?

BTW .pyc files are compiled to intermediate code, so they can be executed rather efficiently. They are not interpreted at the runtime like classic "scripting" language do, whatever "scripting" means. :-)

---

### Post by holihue on 2007-10-21
> **pmasiar said:**
>  Why you need it?


I have a project on sf.net, and I wanted more versions of it...

---

### Post by pmasiar on 2007-10-22
> **holihue said:**
> I wanted more versions of it...

this is not your business goal. What you want to accomplish?

---

### Post by Foxmike on 2007-10-23
> **pmasiar said:**
> Binary for which platform? There are compilers, which can compile .pyc further to real binaries (like psyco), but not many people bothers with it. Why you need it?

BTW .pyc files are compiled to intermediate code, so they can be executed rather efficiently. They are not interpreted at the runtime like classic "scripting" language do, whatever "scripting" means. :-)
 Thanks for the precision!:)

---

### Post by evymetal on 2007-10-29
There are python "compilers" out there that wrap up all your modules and the interpreter into an executable. I've found this useful for distributing software to Windows users, although you can also get "compilers" for linux,BSD,OSX etc.

One thing you do need to be aware of if you are thinking of distributing .pyc files is that the .pyc file format is interpreter-dependent, so if you have python 2.4 and you give your pyc files to someone with python 2.1 they probably won't run.

This can also be a problem for code, Python is a fairly new language and as such it's changing constantly. The only way to ensure your app will continue to run on later versions of python is to package it as above so it is run on the correct interpreter. Of course, most apps should continue to run fine (unless they do decide to remove lamda: and map.)


p.s. Psyco isn't a packager, but a JIT compiler that kind of reduces the cost of python's dynamic typing.

---

### Post by Amaranth on 2007-10-31
Python is actually 16 years old.

---

### Post by master_kernel on 2007-11-01
There is a setup.py script out there... I use it for KernelCheck.

---

### Post by calande on 2007-11-04
On Windows there is py2exe ([http://www.py2exe.org](http://www.py2exe.org)), there's gotta an equivalent for Unix...

---

### Post by RAOF on 2007-11-04
> **calande said:**
> On Windows there is py2exe ([http://www.py2exe.org](http://www.py2exe.org)), there's gotta an equivalent for Unix...

Probably not.  Unlike windows, we have an actual software manager, so applications tend not to ship their dependencies (which is precisely what py2exe is doing).

The real question is "why do you want it" :).

---

### Post by evymetal on 2007-11-05
There is a version for *nix - I think pyinstall may do it. If not have a search.

There is one major bonus of packaging a python app like this - you know what version of the interpreter modules you are going to be running on. 

All that the "compilers" do is wrap your code and an interpreter in a single package, load your code into RAM and run it through the standard compiler, so don't expect any speed gains (in fact, it'll probably take slightly longer to load). You can use psyco too, and package that with it.


Re: Python is 16 years old

Wow, time flies.

---

