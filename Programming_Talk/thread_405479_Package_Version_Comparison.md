---
title: "Package Version Comparison"
date: 2007-04-09
forum: Programming Talk
---

### Post by jerryrw on 2007-04-09
Does anyone know either where in the dpkg or apt sources the version comparison routines are or a good algorithm do it?

I've got this far in my research:

```
    The General Form for a version number is E:M.m.r-XubuntuY
     where     E = epoch
               M = Major Version
               m = Minor revision
               r = Revision
               X = Debian Version
               Y = Ubuntu Version
```

But this is no where near universal by any means and I would like to do this WITHOUT invoking re.  From what I can tell many programmers far better than I have struggled with this problem so I'm sure there is an easy way out.

My first thought was to split on periods and dashes but I found some real oddball version numbers in the database:
```
1.2-1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1
2.0.6ubuntu1-5ubuntu1
3.10+debian~pre0-4build1
3:3.3.8really3.3.7-0ubuntu4
2:1.firefox2.0.0.3+1-0ubuntu1
```

The Debian package guide says to basically do a string comparison left to right but it also mentions splitting.

I am trying to write a Python script to do basically an 'apt-get -d update' that will run under windows to fetch packages for Linux systems that have no internet connection so I can't use any libs or system calls to accomplish this.

Python is preferred for portability but I am capable of at least reading most languages.

Thanks

---

### Post by WW on 2007-04-13
The python module **apt_pkg** has the **VersionCompare** function.  From the little that I saw after poking around and googling, I think it does what you want, but I didn't find any actual documentation of the module.  There is also an **apt** module, which I think uses apt_pkg.

---

### Post by jerryrw on 2007-04-15
Thanks for the pointer.  I've already checked that and several others.  Most of the interfaces rely on access to the libapt and libdpkg library routines.  I'm targeting this for windows and hence don't have that luxury.  trying to reinvent this in pure python is ugly at best as the dpkg routine these libs rely on uses some pointer magic that isn't easy(at least for me) to duplicate  in python.  Alas I may have to swig the dpkg source.

---

### Post by EXCiD3 on 2009-07-05
In case anyone is interested, I ported dpkg's vercmp algorithm to Python for a couple of projects I'm working on.

You can find the code here: [http://bitbucket.org/excid3/winlibre/src/00458f7e8856/wpkg/vercmp.py](http://bitbucket.org/excid3/winlibre/src/00458f7e8856/wpkg/vercmp.py)

and the project it'll be used in is Keryx ([http://keryxproject.org](http://keryxproject.org)), a multi-platform package downloader like Synaptic and apt-get for offline machines.

---

