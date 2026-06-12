---
title: "Compiling some one elses program"
date: 2009-08-08
forum: Programming Talk
---

### Post by Cardale on 2009-08-08
I have some source code I want to compile and I needed some idea on how to get it done.  Here is the software [http://neveredit.sourceforge.net/cgi-bin/moin.cgi/NevereditDownloads](http://neveredit.sourceforge.net/cgi-bin/moin.cgi/NevereditDownloads)

I am trying to get the "neverscript" software compiled and working.  I am new to c++ and only have experience with php mainly.

---

### Post by Can+~ on 2009-08-08
Is there a makefile on the folder?

In fact, the normal thing is to have a README or INSTALL file that specifies how to compile (usually ./configure, make, make install).

---

### Post by Cardale on 2009-08-08
yeah there is a make file.  MakeFile.am

---

### Post by shadylookin on 2009-08-08
It's a python program so it shouldn't need compiling 

Anyway if you look at the README file there's a link [http://neveredit.sourceforge.net/cgi-bin/moin.cgi/RunningNevereditFromSource](http://neveredit.sourceforge.net/cgi-bin/moin.cgi/RunningNevereditFromSource)

---

### Post by Cardale on 2009-08-08
I tried make -f Makefile.am and it gives me this error 

"Makefile.am:42: *** missing separator.  Stop."

---

### Post by Can+~ on 2009-08-08
> **Cardale said:**
> I tried make -f Makefile.am and it gives me this error 

"Makefile.am:42: *** missing separator.  Stop."

You should read the link given by shadylookin.

(I wrongly assumed it was a C/C++ project)

---

### Post by Cardale on 2009-08-08
I also tried running from source and got run/neveredit --devel and it tells me that no such file or directory exists.

I am cd into the correct directory.

---

### Post by Can+~ on 2009-08-08
?????@???????:~/Desktop/neveredit$ ./run/neveredit --devel

Works for me, are you sure you downloaded the correct file?

---

### Post by s3a on 2009-08-08
1) cd *to the directory*
2) sudo apt-get install debhelper build-essential dh-make
3) dh_make --createorig
4) sudo apt-get build-dep *packagename*
5) dpkg-buildpackage

This will create .deb files for you to install. I don't know if I am missing anything in step 2 but try it out.

---

### Post by Cardale on 2009-08-09
> **s3a said:**
> 1) cd *to the directory*
2) sudo apt-get install debhelper build-essential dh-make
3) dh_make --createorig
4) sudo apt-get build-dep *packagename*
5) dpkg-buildpackage

This will create .deb files for you to install. I don't know if I am missing anything in step 2 but try it out.

So these steps will create an installer for this program?  Sorry these are totally new concepts to me.  I need to be lead like a small puppy...

---

### Post by s3a on 2009-08-09
That will create .deb files. These .deb files are like the .exe files (in comparison to Windows) in Ubuntu. Installing this way will ensure easy removal later and it will be detected and upgraded during system upgrades if the next version has that program in its repositories. If you have specific questions ask or you can even post all the commands you issued on your terminal. I am fairly new to this too but I've done this successfully several times so I should be able to help you.

---

### Post by Cardale on 2009-08-09
alright ill take you up on that let me get this stuff together and run it

---

### Post by shadylookin on 2009-08-09
> **Cardale said:**
> So these steps will create an installer for this program?  Sorry these are totally new concepts to me.  I need to be lead like a small puppy...

I don't think it's what you're looking for. Creating a .deb file won't run the program. 

Could you copy the exact terminal output of what you get when you run 

./run/neveredit --devel

from the neveredit folder

if you're like me and don't have the dependencies installed you should see this 

```

ERROR check_versions: couldn't import wx package - please install wxPython
Traceback (most recent call last):
  File "/home/shadylookin/neveredit/util/check_versions.py", line 13, in <module>
    import wx
ImportError: No module named wx
ERROR check_versions: couldn't import the numarray package - please install numarray
Traceback (most recent call last):
  File "/home/shadylookin/neveredit/util/check_versions.py", line 26, in <module>
    Numeric = Utils.getNumPy()
  File "/home/shadylookin/neveredit/util/Utils.py", line 22, in getNumPy
    import numarray
ImportError: No module named numarray
ERROR check_versions: couldn't import OpenGL package - please install pyopengl
Traceback (most recent call last):
  File "/home/shadylookin/neveredit/util/check_versions.py", line 40, in <module>
    import OpenGL
ImportError: No module named OpenGL
ERROR check_versions: Please see README for URLs to install missing packages reported
Sorry,You don't seem to have a proper installation of wxPython.
Get one from wxpython.org.
Traceback (most recent call last):
  File "/home/shadylookin/neveredit/ui/NeverEditMainApp.py", line 14, in <module>
    import wx
ImportError: No module named wx

```

---

### Post by nvteighen on 2009-08-10
Ok, creating a .deb will always work because it implicitly installs the stuff into the package's hierarchy... but that's overkil

Use the instructions at [http://neveredit.sourceforge.net/cgi-bin/moin.cgi/RunningNevereditFromSource](http://neveredit.sourceforge.net/cgi-bin/moin.cgi/RunningNevereditFromSource)

(But one thing has to be said: This developer insists in using a really uncommon way to handle installation...)

---

### Post by Cardale on 2009-08-11
After running 

command : ./neveredit --devel

I got this

```
ERROR __init__: couldn't import wx package - please install wxPython
Traceback (most recent call last):
  File "../../neveredit/util/check_versions.py", line 13, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
ERROR __init__: Please see README for URLs to install missing packages reported
Sorry,You don't seem to have a proper installation of wxPython.
Get one from wxpython.org.
Traceback (most recent call last):
  File "NeverEditMainApp.py", line 14, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
```

Using the ./run/neveredit --devel doesn't work is this strange?

---

### Post by shadylookin on 2009-08-12
> **Cardale said:**
> After running 

command : ./neveredit --devel

I got this

```
ERROR __init__: couldn't import wx package - please install wxPython
Traceback (most recent call last):
  File "../../neveredit/util/check_versions.py", line 13, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
ERROR __init__: Please see README for URLs to install missing packages reported
Sorry,You don't seem to have a proper installation of wxPython.
Get one from wxpython.org.
Traceback (most recent call last):
  File "NeverEditMainApp.py", line 14, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
```

Using the ./run/neveredit --devel doesn't work is this strange?

It's giving you an error message that you haven't installed all the necessary libraries. 

if what it's saying is true you need to install wxPython and libtiff.so.3(perhaps it's part of wxPython not sure)

---

