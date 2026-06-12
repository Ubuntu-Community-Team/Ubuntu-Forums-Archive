---
title: "Python Compiler for Linux"
date: 2006-11-14
forum: Programming Talk
---

### Post by gerowen on 2006-11-14
I've heard of a Linux equivalent of py2exe called freeze, but that the only way to get it is to compile the Linux version of python from source.  Is there a way to add this to python that was installed from the repos?  I would like to keep my python installation from the repos b/c I don't have to worry about keeping up with updates that way, synaptic tells me when it has an update and that's it.

The reason I want to compile python files into Linux executable binaries is because sometimes I use libraries that do not come standard with python.  One example is the graphics library I got accustomed to using because we went over it in my CS class as a frontend for tk.  In this instance I would like to be able to compile the file so that it includes all of the information used, libraries and all(just like p2exe), so that I don't have to worry about packaging the non-default library with the application.

---

### Post by dwblas on 2006-11-14
This is the freeze wiki
[http://wiki.python.org/moin/Freeze](http://wiki.python.org/moin/Freeze)
and the py2exe wiki has others
[http://wiki.python.org/moin/Py2Exe](http://wiki.python.org/moin/Py2Exe)

---

### Post by tzulberti on 2006-11-14
Great links. I was looking for that

---

### Post by abdullah21 on 2009-12-27
thanks for your link, but i'm usually use **geany** to compile python source code.

---

### Post by The Secret on 2009-12-27
> **abdullah21 said:**
> thanks for your link, but i'm usually use **geany** to compile python source code.

Geany isn't a compiler.

---

### Post by pedrotuga on 2009-12-27
Why not simply ship whatever libraries you need with your app?
You do not need to compile into a native binary to solve library dependences AFAIK.

---

### Post by CptPicard on 2009-12-27
Why not do what any reasonable person would do and create an actual .deb file which knows of the dependencies?

Btw, necromancy...

---

### Post by Jacks0n on 2009-12-27
You're probably not looking for a "compiler" per se, but one of the tools that bundles your Python code + libraries into a binary that you can execute.

Try [Python Packager]("http://python-packager.com") ([http://python-packager.com]("http://python-packager.com") - I'm the creator :-)), or PyInstaller ([http://www.pyinstaller.org/](http://www.pyinstaller.org/)).


Jackson

---

### Post by cariboo on 2009-12-27
This thread is over 3 years old, start a new thread with your problem. This thread is closed

---

