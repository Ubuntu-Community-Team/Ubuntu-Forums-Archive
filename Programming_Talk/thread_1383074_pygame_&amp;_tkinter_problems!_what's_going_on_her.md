---
title: "pygame &amp; tkinter problems! what's going on here?"
date: 2010-01-16
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2010-01-16
I posted that yesterday that I was having problems with the pygame library, and now I am having problems with tkinter.  I'm using python3, and have installed the programs through apt-get, and reinstalled through synaptic, and everything seems fine except for when I try to use the libraries, I get errors that they don't exist.

```

/home/matthew/Documents/python/gui :python3 gui.py
File "/usr/lib/python3.0/tkinter/__init__.py", line 40, in <module>
    import _tkinter
ImportError: No module named _tkinter

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "gui.py", line 1, in <module>
    from tkinter import *
  File "/usr/lib/python3.0/tkinter/__init__.py", line 42, in <module>
    raise ImportError(str(e) + ', please install the python-tk package')
ImportError: No module named _tkinter, please install the python-tk package

``````

/home/matthew/Documents/python/gui :sudo apt-get install python3-tk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3-tk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 91 not upgraded.
/home/matthew/Documents/python/gui :

```Same goes for pygame. Any one know what's going here???

---

### Post by lavinog on 2010-01-17
Did you try installing the python-tk package?

Why are you using python3?
You could use python 2.6.  When you need to convert to ver 3 use the 2to3 program.
It doesn't look like pygame is available for version 3 yet in the repos.

---

### Post by LucidNovelty on 2010-01-17
What Python are you using? 32 or 64 bits? 

I just came across this thread while looking for a solution for a similar problem with Python 2.6 and tkinter while trying to enable a specific plugin for Blender. The info related to that plugin is limited, but on the site was mentioned that 

'you should use both Python & Blender 32 bit versions since 64 bits has known issues with tkinter'

I've looked further but could not really confirm that statement (tkinter having issues with 64 bits Python). 

Still I am having the exact message as you have using Python 2.6 64 bits, python-tk is installed but it give an eror similar like yours:

```
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/home/henk/blender_scripts/primstar/add_mesh_sculpt_mesh.py", line 50, in <module>
    from Tkinter import *
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 42, in <module>
    raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: /usr/lib/python2.6/lib-dynload/_tkinter.so: undefined symbol: PyFPE_jbuf, please install the python-tk package

```I'll monitor this thread and if I find a solution will post as well.

---

### Post by c0mput3r_n3rD on 2010-01-17
Thanks of the help guys.  I got tkinter working thankfully, but I'm still having a problem with pygame in python3.  If I don't use python3 every is fine with it, but then I can use tkinter, i'm trying to use them both at the same time!  I'm using python3 cause that's what this book I'm reading is teaching us.  My machine is 64bits so I'm assuming I'm using the 64bit version of python (i used apt-get to install it).  Thanks for your guys help

> **LucidNovelty said:**
> What Python are you using? 32 or 64 bits? 

I just came across this thread while looking for a solution for a similar problem with Python 2.6 and tkinter while trying to enable a specific plugin for Blender. The info related to that plugin is limited, but on the site was mentioned that 

'you should use both Python & Blender 32 bit versions since 64 bits has known issues with tkinter'

I've looked further but could not really confirm that statement (tkinter having issues with 64 bits Python). 

Still I am having the exact message as you have using Python 2.6 64 bits, python-tk is installed but it give an eror similar like yours:

```
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/home/henk/blender_scripts/primstar/add_mesh_sculpt_mesh.py", line 50, in <module>
    from Tkinter import *
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 42, in <module>
    raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: /usr/lib/python2.6/lib-dynload/_tkinter.so: undefined symbol: PyFPE_jbuf, please install the python-tk package

```I'll monitor this thread and if I find a solution will post as well.

Definitely let me know what's going in that thread, or link the thread to me so I can keep an eye on it, either way, I would apppreciate it.

@lavinog:  I've been thinking that pygame is available for python3 either, except this book says to use pygame with python3!!! I really have no idea what's going on here... I switched to python because I didn't want to have these types of problems.

---

### Post by Can+~ on 2010-01-17
**About Pygame**
> Does Pygame work with Python 3?

Release 1.9.0 does. Pygame from SVN builds as is with Python 3.0 and later. But Python 3 support is incomplete and still in the development stage. Not all modules have been ported. No scrap, for instance. And Numeric support will never happen, though NumPy suppot should be available when NumPy is itself ported. The Pygame successor, pgreloaded (Pygame Reloaded) also supports Python 3.

[pygame wiki]("http://www.pygame.org/wiki/FrequentlyAskedQuestions#Does%20Pygame%20work%20with%20Python%203?").

Current version on repository: Version: 1.8.1release-1ubuntu1

And checking [Lucid Lynx]("https://launchpad.net/ubuntu/lucid/+source/pygame/1.9.1release-0ubuntu1") entry, we'll be getting pygame 1.9.1 in the next version.

**As for TK**

I had the exact same errors, for the exception that, as soon as I installed python3-tk, everything worked fine.

I tested with python3, latest version in the repository, on Ubuntu 9.10 (Karmic Koala) amd64. **What version are you running?** (edit: Seems that you're still running Jaunty)

My advice: As I told you before, you should stick with python2.6, use "from future import <stuff>", read on [this]("http://docs.python.org/whatsnew/2.6.html#python-3-0"). Python2.6 is forward compatible with python3, so stick with the old and good.

> I switched to python because I didn't want to have these types of problems.

Python is a good choice indeed, the problem is that you picked a early release, with unstable libraries on an unstable environment. That's just asking for trouble. You should sometimes favor old and stable instead of new and shiny, that's an advice that works especially well in the business (maybe too well, old Jurassic software is problematic too).

---

### Post by c0mput3r_n3rD on 2010-01-17
> **Can+~ said:**
> **About Pygame**


[pygame wiki]("http://www.pygame.org/wiki/FrequentlyAskedQuestions#Does%20Pygame%20work%20with%20Python%203?").

Current version on repository: Version: 1.8.1release-1ubuntu1

And checking [Lucid Lynx]("https://launchpad.net/ubuntu/lucid/+source/pygame/1.9.1release-0ubuntu1") entry, we'll be getting pygame 1.9.1 in the next version.

**As for TK**

I had the exact same errors, for the exception that, as soon as I installed python3-tk, everything worked fine.

I tested with python3, latest version in the repository, on Ubuntu 9.10 (Karmic Koala) amd64. **What version are you running?** (edit: Seems that you're still running Jaunty)

My advice: As I told you before, you should stick with python2.6, use "from future import <stuff>", read on [this]("http://docs.python.org/whatsnew/2.6.html#python-3-0"). Python2.6 is forward compatible with python3, so stick with the old and good.



Python is a good choice indeed, the problem is that you picked a early release, with unstable libraries on an unstable environment. That's just asking for trouble. You should sometimes favor old and stable instead of new and shiny, that's an advice that works especially well in the business (maybe too well, old Jurassic software is problematic too).


Alright awesome that's very helpful thank you.  I feel like a have enough now to stop bothering you guys with my pygame problems! :)   Of course, if any one has any other suggestions or the same problem with a fix let me know.  I'll try switching over to python2.6   Just curious, are there any other good sound libraries to use instead of the pygame.mixer   And does python refer to there libraries as modules?

---

### Post by cariboo on 2010-01-18
> ImportError: No module named _tkinter

I'm looking at the same book, use:

```
Tkinter
```

---

### Post by dogtato on 2012-04-14
> **Can+~ said:**
> I had the exact same errors, for the exception that, as soon as I installed python3-tk, everything worked fine.
This was it, thanks. The python exception says to install pytion-tk but the trick is to install python3-tk.
Seems like the error could be a little more helpful.

---

### Post by LeNath on 2012-08-09
```
sudo apt-get install python3-tk

```
Also did it for me... Using Python3 and with this book [http://openbookproject.net/thinkcs/python/english3e/](http://openbookproject.net/thinkcs/python/english3e/)

Cheers,
N.

---

