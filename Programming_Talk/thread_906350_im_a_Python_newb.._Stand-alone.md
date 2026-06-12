---
title: "im a Python newb.. Stand-alone??"
date: 2008-08-31
forum: Programming Talk
---

### Post by artheus on 2008-08-31
Hey!
I'm a newb to Python, but I have been programming alot in Visual Studio, Flash(ActionScript), PHP and JavaScript earlier, so I'm not a newb in programming...

But my question is :

- In Ubuntu 8.04, I have installed Python IDLE. Can I through that compile my written programs to stand-alone programs? so that I can run them, not through IDLE, in Linux??

-Are there any good py-compilers for linux where you can compile to both Mac OSX and Windows, if needed??


Pre-Thanks ;),
Artheus

PS: I'm a little newb to linux too, so i don't even know if it is possible to make stand-alone executables for it (like in windows)

---

### Post by Yannick Le Saint kyncani on 2008-08-31
You don't need to compile it, python programs are interpreted at run-time.

---

### Post by mssever on 2008-08-31
In Python, you use whatever editor/IDE suits you, and your choice doesn't affect anyone else. Specifically, it doesn't affect compatibility in any way. You don't have to get everyone worshiping at the altar of a particular IDE.

---

### Post by fiddler616 on 2008-08-31
Eek, good question.
*subscribes*

---

### Post by nvteighen on 2008-08-31
Python is "interpreted" (actually, it's not... but let's leave that for now), meaning that you pass the code to a program that reads it an executes it. In Ubuntu, you can use any text editor (any, but there are better and worse ones) like Gedit (which supports syntax highlighting), write your code, save it as a .py and then, open a Terminal and write:

```

python myfile.py

```

Voilà!, there you have it...

There are Python interpreters for Windows and MacOS (see [http://www.python.org/](http://www.python.org/)) and they should work the same (or similarly) as in GNU/Linux.

By the way, if you used Visual Studio .NET languages, they aren't standalone, but they work more like Python or Java. Actually, there's no "absolute standalone" program except for operating systems :p

---

### Post by Wybiral on 2008-08-31
Along with just using "python myfile.py" as nvteighen mentioned, you can add a shebang and make it executable:

```

#!/usr/bin/env python
print "Hello %s!" % raw_input()

```

Then just run a "chmod +x myfile.py" in the terminal to give it executable permission. Then you can run it with "./myfile.py" or ever double-clicking (although this wont work well for terminal programs as they'll disappear when the program stops executing).

---

### Post by fiddler616 on 2008-08-31
If you read the OP carefully, I think the question was more along the lines of how he makes a file that, when clicked, opens a terminal and runs his program inside it automatically. He was also wondering if the file he made would work between platforms. (If this were Windows, I'd say he wanted to make a .exe out of his .py, but this isn't Windows, so I don't know the proper terminology yet. Sorry!)

---

### Post by nero1111 on 2008-08-31
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by fiddler616 on 2008-08-31
Reported nero1111's post as spam.

---

### Post by pmasiar on 2008-08-31
> **artheus said:**
> Can I through that compile my written programs to stand-alone programs? so that I can run them, not through IDLE, in Linux??

You don't need to. Exactly like .NET DLLs, Python uses runtime, which is already installed, and your code is compiled to .pyc files.

You can either run your sources using 'python myprogram.py' or using shebang trick, make your code executable and add special comment (called shebang) in first line to tell shell which "runtime system" should run this source: '#!/usr/bin/env python'

[http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

---

### Post by LaRoza on 2008-08-31
> **artheus said:**
> 
-Are there any good py-compilers for linux where you can compile to both Mac OSX and Windows, if needed??


py2exe and freeze can make the programs not need a separately installed interpreter, but it is usually not a problem to install Python.

---

### Post by newmanccc on 2008-08-31
[http://pyinstaller.python-hosting.com/](http://pyinstaller.python-hosting.com/)

---

### Post by mssever on 2008-09-01
> **fiddler616 said:**
> He was also wondering if the file he made would work between platforms.
To answer this specific question, Python is a good cross-platform language. Python experts, please correct me if I'm wrong, but I believe that within the standard library, everything works cross-platform except where the documentation explicitly says otherwise. Outside the standard library, most things are still cross-platform, but you have to decide how you'll make sure that the end user has all the required libraries installed.

---

### Post by LaRoza on 2008-09-01
> **mssever said:**
> To answer this specific question, Python is a good cross-platform language. Python experts, please correct me if I'm wrong, but I believe that within the standard library, everything works cross-platform except where the documentation explicitly says otherwise. Outside the standard library, most things are still cross-platform, but you have to decide how you'll make sure that the end user has all the required libraries installed.

There are a few OS specific standard libs, but they have no use in other OS's.

Most libraries (PyGame, wxWidgets, PyQT, PyGTK+, etc) are easily installed with an installer.

---

