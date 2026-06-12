---
title: "Problem with Cmake"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-05
Hi, all:

I'm trying to compile plasmoids, and I'm getting this error when I try to run "sudo make"

make: *** No targets specified and no makefile found.  Stop.


What does this mean?

---

### Post by Cypher on 2008-11-05
The error is kinda self-explanatory, you have one of two possible issues. You are in a directory where there is a "makefile" or "Makefile" which tells "make" how to compile your program. Or, the "makefile" exists, but it doesn't contain the right information (targets) for "make" to compile your program.

So for starters, ensure you are in the right directory and and check for the existing of "Makefile" with "ls -l". 

Also, you don't need "sudo" in front of the "make" command, once the "make" finishes, you usually install the program using "make install" which copies the program to /usr/local/bin. For this process you'll want to use "sudo make install".

Also, you can use a program called checkinstall instead of doing "sudo make install" and this will create a .DEB package that you can install using "sudo dpkg -i <package-name>.deb", and that way if you want to remove the program, you can do so nicely and cleanly. Some program do include the "sudo make uninstall" option, but not all..

---

### Post by ellgor on 2008-11-05
Hi again,

Just in case youre still having bother and it is "cmake" you are using then try this:

cd to the directory as normal, instead of typing "./configure Etc.," type "cmake ." as seen, put the dot after the cmake, hope this helps.

Regards, Ellgor.

---

### Post by tarahmarie on 2008-11-06
I have tried each of your solutions, and I'm still getting the original error.  It seems to be working fine for everyone else installing this plasmoid; do I need to install a package for make to work?

---

### Post by tarahmarie on 2008-11-07
You know, make worked fine in Hardy; I've got Intrepid now.  What's the diff as far as make is concerned?

---

### Post by tarahmarie on 2008-11-09
I'm still wondering what the difference between Hardy and Intrepid are when it comes to building plasmoids.  I have build-essential installed, and I'm following the exact same directions I did to build plasmoids under Intrepid.  Has anyone else had this same problem?

---

### Post by tarahmarie on 2008-11-09
Ah--for anyone else having the same problem, install the packages found at this howto: [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3096596.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3096596.0)

libkonq5-dev, libkonq5, cmake, libplasma-dev, kdelibs5-dev, kdebase-dev-kde4 as well as gcc-3.3base, and g++

It works for me now.

---

