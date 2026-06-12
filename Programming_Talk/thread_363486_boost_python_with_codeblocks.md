---
title: "boost python with code::blocks"
date: 2007-02-17
forum: Programming Talk
---

### Post by CoMaNdore on 2007-02-17
Hey

I just moved from windows to ubuntu. And im already faling in love with the os :D
Anyway I desided to install boost python to start porting my current project to ubuntu.
My new ide of choice is "code::blocks".

Now I have installed the ubuntu-boost packets and the python-dev packet
*both version 2.4 & 2.5*

I have also installed a whole shibang of -dev stuff and boost stuff.

Now to the problem :D

I can compile a simple glfw appliaction using ie. lexical_cast but when I try to compile
a simple app that includes boost/python.hpp hell breaks lose.

*Uptil now I only added /usr/include/python2.4 to build options -> seach paths linker*
When I try to compile I get the following error:
```

/usr/include/boost/python/object_core.hpp:414: undefined reference to `_Py_NoneStruct'

```


Now I wonder what else to do in order to properly compile a boost::python app. (btw im trying to extend not embed python)

And like many others, im pretty fluent in c++ / python but im used to the easy visual studio enviroment. So please talk to me like im 3 years old :D

---

### Post by runningwithscissors on 2007-02-17
> **CoMaNdore said:**
> Hey

I just moved from windows to ubuntu. And im already faling in love with the os :D
Anyway I desided to install boost python to start porting my current project to ubuntu.
My new ide of choice is "code::blocks".

Now I have installed the ubuntu-boost packets and the python-dev packet
*both version 2.4 & 2.5*

I have also installed a whole shibang of -dev stuff and boost stuff.

Now to the problem :D

I can compile a simple glfw appliaction using ie. lexical_cast but when I try to compile
a simple app that includes boost/python.hpp hell breaks lose.

*Uptil now I only added /usr/include/python2.4 to build options -> seach paths linker*
When I try to compile I get the following error:
```

/usr/include/boost/python/object_core.hpp:414: undefined reference to `_Py_NoneStruct'

```


Now I wonder what else to do in order to properly compile a boost::python app. (btw im trying to extend not embed python)

And like many others, im pretty fluent in c++ / python but im used to the easy visual studio enviroment. So please talk to me like im 3 years old :D

Now, I've never used Code::Blocks so I don't really know the setup to build new python modules with it.

But if you're just trying to write a new module for python, you can use distutils to build your module. It takes care of the build options for your module. Here is a nice howto on how to build and package your module using distutils.
[Clicky!](http://docs.python.org/ext/building.html#building)

---

### Post by CoMaNdore on 2007-02-17
Well the thing is that Im not exactly new to building python modules.. its just under ubuntu

As I already have a python::boost codebase for windows ( im guessing ~3k LOC, its not that big but big enoght for me.. )

So im quite dependant of boost python.
Can I use boost python with this (as in the howto you posted) setup?

In case how? What files do I need to include/link under python?
*yeah I know this is a pretty ide dependant question and bare with me for that*


Already thanks for the help :D

---

### Post by Mirrorball on 2007-02-17
I probably didn't link to Python's shared library in your project. I'm not a code::blocks user either, so hopefully someone else will read this thread and tell you exactly how to do this, but it's probably what's causing that error. You'll probably have to write -lpython2.4 somewhere in your project configuration options.

---

### Post by runningwithscissors on 2007-02-17
Ouch! I didn't pay attention to the Boost libraries you're using.

I looked it up and writing C++ modules for python looks nasty. Boost recommends the use of its own build system, bjam. distutils won't work :(

Here is a small tutorial. See if it works for you. The site also has instructions on how to compile the whole of Boost.Python should you so wish.
Instructions for compiling a small module:
[Clicketty-click](http://www.boost.org/libs/python/doc/tutorial/doc/html/python/hello.html)
Just make the appropriate changes to the directory paths for Unix and it should work.

Sorry I couldn't help you better. I've never built modules with C++. :(

---

### Post by CoMaNdore on 2007-02-17
Well moving on there seems to be a error with the boost packets that ubuntu suplies.. ( or somthing like that)

basicly I ran into the same problem as this guy:
[http://www.nabble.com/-C++-sig--Newbie-trouble-with-Boost.Python-tutorial-on-Ubuntu-t2926390.html]("http://www.nabble.com/-C++-sig--Newbie-trouble-with-Boost.Python-tutorial-on-Ubuntu-t2926390.html")

And this guy:
[http://mail.python.org/pipermail/c++-sig/2006-August/011020.html]("http://mail.python.org/pipermail/c++-sig/2006-August/011020.html")

I forgott the notion of code::blocks and just tried to build the simple stample module
using bjam. 

As in the tutorial, I created a folder on my desktop and got hello.cpp Jamfile & Jamrules
from the tutorial ([http://www.boost.org/libs/python/example/tutorial/]("http://www.boost.org/libs/python/example/tutorial/") ) I put them into the same folder.

After that I edited the Jamrules file so that path-global pointed to /usr/include
like this:
path-global BOOST_ROOT : /usr/include ; 

then I try to build it:

ooki@COMANDORE:~/coding/myprojects/pybjam$ bjam sTOOLS=gcc
Failed to find the project root for directory '.'.
Did not find a project-root.jam file there or in any of its parent directories.
Please consult the documentation at 'http://www.boost.org'.


Since im not used to make files or bjam at all I would be greatefull if anyone would point me in the right direction.

*quick question about ubuntu and .so files: 
When I have a .so file and want to load it in python,will it seach the folder where the .py file is?
or do all the .so files need to be in some spesial directory?*

---

### Post by Mirrorball on 2007-02-17
Boost Python has always worked for me without bjam. In fact I didn't even know that it existed. Did you try my solution above for your problem with cold::blocks?
The .so file will load like any other Python module.

---

### Post by CoMaNdore on 2007-02-18
Well tbh im not sure how I get code::blocks to create a .so for me.
But adding -lpython2.4 seemed to fix it. somewhat, at least it compile now.

What compiler diretives do I need to add make it produce a .so?

---

### Post by Mirrorball on 2007-02-18
If you were running g++ from the command line, -shared -o whatever.so
Search for an option to build a *shared library.*

---

### Post by CoMaNdore on 2007-02-18
So what build system do you use with boost.python?


From the look of things atm it seems almost easier to get my hands dirty and just learn to 
create a good old makefile. 

Could you be so kind to post a example makefile that includes boost.python?
*so I have somthing to go after, and saves me some more stupid questions.*


Anyway thanks for the help so far.. Its seems like folks around here actually care to 
help each other :D

---

### Post by Mirrorball on 2007-02-18
My makefiles that use Boost Python are on my computer at work and I don't have them with me right now... You can take any Makefile as an example and add those options for shared libraries. But I'm pretty sure that Code::blocks will let you enter those options somewhere. Or you could post this question on the code::blocks forum.
[http://forums.codeblocks.org/](http://forums.codeblocks.org/)
They will know for sure how to build a shared library.

---

### Post by CoMaNdore on 2007-02-18
thanks, Mirrorball I got it working now. Just created a stample opengl app in c++ using glfw.
Interfaced it with boost.python

Compiled -> tested the python interface. And it all worked flawless :D ( all within code::blocks)

I dunno how stuff like this is handled here. Show I now write a howto so that others that have the same problem as me can more easely find a sulution? And if I do, where should I post it?

---

### Post by Mirrorball on 2007-02-18
I don't know. Others can always do a search and find this topic.

---

