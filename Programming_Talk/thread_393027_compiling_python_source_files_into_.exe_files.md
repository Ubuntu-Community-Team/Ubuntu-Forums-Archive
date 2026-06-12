---
title: "compiling python source files into .exe files"
date: 2007-03-25
forum: Programming Talk
---

### Post by liviubero on 2007-03-25
Hello to all,
I am a newbie with Ubuntu and would have a question.
I am now learning Python and the problem is that, when I want to send my scripts to some friends, the scripts wont work, because not everyone has Python installed. So I would need to convert the Python source files into executables for windows.
I searched with Synaptic for an utility which could do this job, but didn't found anything.
Or perhaps I didn't searched for the right thing. And even if I find on the web some programmes  for Linux which could do this, I have no idea how to install them (for instance PyInstaller) because I can only use Synaptic (due to my ignorance regarding installing applications without Synaptic).

Would you know any package which could be installed with Synaptic and which could convert the .py files into .exe files?
Or perhaps you have some suggestion to this issue?
Thank you.

---

### Post by ghostdog74 on 2007-03-25
[Pyinstaller ]("http://freshmeat.net/projects/pyinstaller/") or [py2exe]("http://www.py2exe.org/") is what you are looking for

---

### Post by liviubero on 2007-03-25
Yes, but I cannot find them with Synaptic.

---

### Post by enopepsoo on 2007-03-25
that just means that they aren't in synaptic.  you would have to install them manually.

---

### Post by liviubero on 2007-03-25
I am lost here. How should I install them manually?
All I know about the terminal is how to open it and two commands: "cd" and "rm", that's it.

---

### Post by tkjacobsen on 2007-03-25
From pyinstaller README

```
_PyInstaller 1.3_
=================

Use
===
 See doc/Tutorial.txt

Installation in brief
=====================
 Non-Windows users should:
    cd source/linux

    python ./Make.py

    make

 Everyone should:
    python Configure.py

    python Makespec.py /path/to/yourscript.py

    python Build.py /path/to/yourscript.spec

    .done.

Major changes in this release
=============================
 See doc/CHANGES.txt

```

---

### Post by pmasiar on 2007-03-25
> **liviubero said:**
> All I know about the terminal is how to open it and two commands: "cd" and "rm", that's it.

Maybe easier than learning commandline tricks would be to ask your friends to install Python. Then you all can share sources, learn Python, helping each other.

---

### Post by liviubero on 2007-03-25
> **pmasiar said:**
> Maybe easier than learning commandline tricks would be to ask your friends to install Python. Then you all can share sources, learn Python, helping each other.

Thanks, but this is hard to realize with friends who are .NET fans.

I just used PyInstaller under Windows and it works. I had to set up the path variable. Now I have to figure out how to use it under Linux.

How do I unpack the tar.gz archive?

---

### Post by JensenDied on 2007-03-25
there are two ways with the command line, and other gui's which can vary by persons usage.

$ gunzip foo.tar.gz 
$ tar -xvf foo.tar

$ tar -xzvf foo.tar.gz

.gz is the extension for gzip'ed files, it can also appear as .tgz or .tar.gz if they are in a tar archive. gzip <filename> and gunzip <filename> compress and decompress files respectively.

tar can extract -x and create -c tar archives. -v is for verbose so you can see what files it is extracting. -f <filename> is for telling tar what file to work on.

---

### Post by pmasiar on 2007-03-25
> **liviubero said:**
>  this is hard to realize with friends who are .NET fans.?

You would be surprised - some .NET fans very appreciate Python for .NET, aka IronPython. Microsoft  hired one of top Python developers and released [IronPython](http://en.wikipedia.org/wiki/Ironpython) under somewhat Open Source compatible license - unique for MS. And because IronPython has Python shell, and has access to most .NET internal system calls, you can do from IronPython commandline shell tricks what may require writing page of scaffolding code in C#.

Sorry for off-topic rambling.

---

### Post by blanky on 2007-03-25
Yep, IronPython is great :D Then there's also it's cousing (Okay maybe not it's cousin :P ), Boo :D

---

### Post by linea on 2007-10-11
[B]I install PyInstaller 1.3 base on README.txt.


_PyInstaller 1.3_
=================

Use
===
 See doc/Tutorial.txt

Installation in brief
=====================
 Non-Windows users should:
    cd source/linux

    python ./Make.py

    make

 Everyone should:
    python Configure.py

    python Makespec.py /path/to/yourscript.py

    python Build.py /path/to/yourscript.spec

    .done.

Major changes in this release
=============================
 See doc/CHANGES.txt


But I try to 

    cd source/linux

    python ./Make.py

then 

Warning: could not find python static library at :/usr/lib/python2.5/config/libpython2.5.a

Now run "make" to build the targets: ../../support/loader/run ../../support/loader/run_d

I can't find libpython2.5.a. Where can I download the "libpython2.5.a"?

Please help. Thanks.[/B]

---

### Post by Tuna-Fish on 2007-10-11
The name of the package in synaptic is python2.5-dev

---

### Post by Alestan on 2009-05-23
Py2exe doesn't work from Linux, or at least I don't think it does.  Pyinstaller works great... if the destination computer is Linux.  It does not compile from Linux to Windows, or from Windows to Linux.  According to the website, it is possible, in theory, however it is not supported, nor is it high priority.  Anyway, what is ironPython?

--Alestan

---

