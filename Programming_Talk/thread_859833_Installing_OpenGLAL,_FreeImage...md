---
title: "Installing OpenGL/AL, FreeImage.."
date: 2008-07-14
forum: Programming Talk
---

### Post by yahn on 2008-07-14
I love Ubuntu, but I figured that it would come with development things pre-installed.  I guess I was wrong.

One of the reasons that I was so excited to start developing on Linux instead of Windows is that I was put under the impression that is actually easier to use.  I guess I was wrong again.

It took me a while, but I finally got OpenGL installed.  For something as common as OpenGL to take as long as it took to get installed, I'm really starting to wonder if I should just stick to windows to develop.

I don't know if I installed something wrong, but I've been looking at guides on the internet to install these things and none of them are working.

wxWidgets and OpenAL installed very easily, however.  So maybe there are just a few things that are a little harder than I expected.

For example, Installing LADM (Django instead of PHP) is simply not working when I follow guides word for word.

Am I under the wrong impression that developing for Linux is easier than developing for Windows?  Does anyone know where I can find some really good information about developing from the start for Linux (that includes how to install everything from OpenGL/AL, FreeImage, Vorbis, Object Oriented Input System, Python, LUA, Django, etc?

It seems like there are ten thousand extremely well written guides on the internet on how to install a LAMP.  I guess that is largely because of their popularity.  Do guides not exist for other things, or am I just looking in the wrong place?

---

### Post by hod139 on 2008-07-15
> **yahn said:**
> 
Am I under the wrong impression that developing for Linux is easier than developing for Windows?  Does anyone know where I can find some really good information about developing from the start for Linux (that includes how to install everything from OpenGL/AL, FreeImage, Vorbis, Object Oriented Input System, Python, LUA, Django, etc?

When searching for development libraries, make sure you install the foo-dev packages.  The -dev will pull in the headers and libraries for a package.  
1) OpenG/AlL: libgl1-mesa-dev and libalut-dev (you probably also want libglu so also install libglu1-mesa-dev)
2) FreeImage: libfreeimage-dev
3) Vorbis: libvorbis-dev
4) Object Oriented Input System: ??
5) Python: Already installed
6) LUA: liblua5.1-0-dev (or a different version if you want, there are many available)
7) Django: Not sure, I'm guessing python-django

You can always use synaptic or apt to search for packages.  For example:
```

apt-cache search django

```Returns
```

cakephp-instaweb - Development webserver for CakePHP applications
libmapnik-dev - C++/Python toolkit for developing GIS applications (devel)
libmapnik1d - C++/Python toolkit for developing GIS applications (libraries)
mapnik-plugins - C++/Python toolkit for developing GIS applications (plugins)
mapnik-utils - C++/Python toolkit for developing GIS applications (utilities)
python-django - A high-level Python Web framework
python-jinja - small but fast and easy to use stand-alone template engine
python-mako - hyperfast and lightweight templating for the Python platform
python-mapnik - C++/Python toolkit for developing GIS applications (python)

```

---

### Post by yahn on 2008-07-15
Wow, Thanks for the quick reply.  Maybe this is as easy as I thought it was going to be.

Now, Object Oriented Input System you put question marks by.  Judging by your informative response, I'm guessing that you know what your doing.  Do you just use wxWidgets for input or what do you use?  I'm guessing it's probably better than OIS if you have never heard of it.

---

### Post by hod139 on 2008-07-15
> **yahn said:**
> 
Now, Object Oriented Input System you put question marks by.  Judging by your informative response, I'm guessing that you know what your doing.  Do you just use wxWidgets for input or what do you use?  I'm guessing it's probably better than OIS if you have never heard of it.

I put question marks only because I've never used OIS and wasn't 100% sure what package you would need.  A quick search in apt though finds the package:
```

apt-cache search  object oriented input system

```
```

libio-multiplex-perl - object-oriented interface to select() for perl
libois-dev - Object Oriented Input System library (C++ development headers)
libois1 - Object Oriented Input System library (C++)
tads2-dev - TADS version 2 development tools
tads3-dev - TADS version 3 development tools

```
Looks like you need to install the package libois-dev.

---

### Post by yahn on 2008-07-15
I see.  Thank you again for all the help.

---

### Post by Sockerdrickan on 2008-07-15
You do NOT want openal that is in Ubuntu 8.04 or earlier, trust me. get this [http://kcat.strangesoft.net/openal.html](http://kcat.strangesoft.net/openal.html) or use 8.10

You are lucky I warned you! That version doesn't suffer from bad audio quality and has all the functions you need to get developing!

---

### Post by yahn on 2008-07-15
I'll probably just wait for 8.10.  What exactly is wrong in 8.04 that causes it to be so messed up?

---

### Post by Sockerdrickan on 2008-07-16
alSourcei() is not there in Ubuntus 8.04's(or earlier) OpenAL implementation

---

