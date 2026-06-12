---
title: "libXt-dev package problem, I think..."
date: 2010-10-21
forum: Programming Talk
---

### Post by ladasky on 2010-10-21
Hi.  I posted this yesterday and I didn't receive any replies, possibly because my title was not descriptive enough.  I've also made a little progress since I last posted.
 
I'm tearing my hair out trying to solve a package dependency problem.  I'm running Karmic.
 
I'm trying to make use of a non-canonical package called [pymacs]("http://wwwuser.gwdg.de/~dseelig/pymacs.html").  This is not the package which provides an interface between EMACS and Python, it's an interface between Python and GROMACS.  Wouldn't you know it, the Linux universe is so dense with software that the same name got used twice.
 
Anyway, I've installed pymacs and tried to import it from my Python interpreter.  Here's what I get:
 
```
IDLE 2.6.4      ==== No Subprocess ====
>>> from pymacs import *
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    from pymacs import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/__init__.py", line 23, in <module>
    from molecule import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/molecule.py", line 37, in <module>
    from atomselection import *
  File "/usr/local/lib/python2.6/dist-packages/pymacs/atomselection.py", line 24, in <module>
    import _pymacs
ImportError: /usr/local/lib/python2.6/dist-packages/pymacs/_pymacs.so: undefined symbol: XtManageChild
```
 
I've never received a build-style error message from inside a Python import call before.
 
I went searching for information on the XtManageChild function, and trust me, that wasn't as easy to find as I would have hoped.  My best bet in the past has been to go a Google search in packages.ubuntu.com using the function name as the search term.  XtManageChild appears in the search, in the filelist of package libxt-dev, for [Hardy]("http://packages.ubuntu.com/hardy/i386/libxt-dev/filelist") and for [Lucid]("http://packages.ubuntu.com/lucid/i386/libxt-dev/filelist") -- but not for Karmic.

I don't know why Google doesn't turn up [http://packages.ubuntu.com/karmic/i386/libxt-dev/filelist](http://packages.ubuntu.com/karmic/i386/libxt-dev/filelist), but I guessed that URL after seeing the names of the other two web pages.  The page exists, and it too lists XtManageChild.
 
I checked my manifest of installed packages on Karmic.  I already had libxt-dev installed.  I tried reinstalling it in case it got corrupted somehow.  This did not fix the error.

Any advice would be appreciated!  Thanks!

---

### Post by dwhitney67 on 2010-10-21
XtManageChild is part of the Xt library.  I believe you can get that if you install **libxt6**.  If not, then try libmotif3.

Strange thing, though, is that I would have expected that your system would already have it installed.

---

### Post by ladasky on 2010-10-22
Thanks for the reply, dwhitney67.
 
I already had *libxt6* installed, but not *libmotif3*.  I tried installing the latter.  Unfortunately, it changed nothing.  My Python interpreter still generates the ImportError.
 
There's also *libmotif3-dev*...

Is there any systematic way to determine the name of a package where you can find a missing function?  I've had to hunt before.  Eventually I find what I need to know on some obscure web page -- but not this time, not so far.

---

### Post by dwhitney67 on 2010-10-22
libxt6 is the correct package for the *compiled version* for XtManageChild().  Unless you plan to develop X/Motif apps, you do not require the development package(s).

You can list what is in libxt6 using apt-file (note, you may need to install this utility).  To my surprise, /usr/lib/libXt.so is not included; the closest is /usr/lib/libXt.so.6.

Personally I do not know anything about GROMACS, nor can I deduce whether you installed everything correctly so that Python is happy.  Obviously something is afoul.

Maybe creating a symbolic link for /usr/lib/libXt.so is all that is required?
```

cd /usr/lib
sudo ln -s libXt.so.6 libXt.so

```
If after creating the link, Python still fails, then destroy the link, for I guess it is then not necessary.

---

### Post by ladasky on 2010-10-22
> **dwhitney67 said:**
> 
Personally I do not know anything about GROMACS, nor can I deduce whether you installed everything correctly so that Python is happy.  Obviously something is afoul.


My Python installation is the standard v2.6 build for Karmic.  I've added a few site packages to it, but I haven't tinkered with it in any other way.
 
GROMACS is working flawlessly for me, at least from bash.  GROMACS is not a graphical application, and thus I do not expect it to depend on X windows in any way.
 
Pymacs is installed using Python's distutils.  I initially encountered a build problem when I installed pymacs, but installing libfftw3-dev corrected it.

> **dwhitney67 said:**
> 
Maybe creating a symbolic link for /usr/lib/libXt.so is all that is required?
```

cd /usr/lib
sudo ln -s libXt.so.6 libXt.so

```

 
It looks like I already have symbolic links with both of those names:

```
16:17:40 -> ls -l libXt*

-rw-r--r-- 1 root root 436044 2009-04-11 12:43 libXt.a
lrwxrwxrwx 1 root root     14 2010-10-20 23:47 libXt.so -> libXt.so.6.0.0
lrwxrwxrwx 1 root root     14 2010-09-10 02:07 libXt.so.6 -> libXt.so.6.0.0
-rw-r--r-- 1 root root 338980 2009-04-11 12:43 libXt.so.6.0.0
lrwxrwxrwx 1 root root     16 2010-09-10 02:09 libXtst.so.6 -> libXtst.so.6.1.0
-rw-r--r-- 1 root root  22076 2009-03-26 23:52 libXtst.so.6.1.0
```

Thanks for sticking with me, even though I'm still mystified.  I may contact the author of pymacs, and see what I can learn from him.

---

