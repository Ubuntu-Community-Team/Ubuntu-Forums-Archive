---
title: "installing shared object files"
date: 2009-09-04
forum: Packaging and Compiling Programs
---

### Post by Clive McCarthy on 2009-09-04
I have what might be a simple problem. I'm trying to put a shared-object:

    freeglut.so

into \user\lib -- and my crude attempts all result in permission denied.

I'm doing this because I've installed freeglut and linked my code to the library etc. but the shared object can't be found by the executable. It seems that

    sudo apt-get install freeglut3-dev

doesn't put the freeglut.so in the library directory but does put freeglut.h freeglut_std.h & freeglut_ext.h headers in the \user\include directory.
It also emits a message about manual installation...

Ultimately, I will be deploying the executable and necessary libraries to a small number of Ubuntu machines on my network. These machines are embedded applications: almost no user interface, just an on/off power button and a screen. So I'll need write a bash script to do all the repetitive tasks.

For now, I'd be happy if I can figure out how to manually install the shared-object on my local system.

---

### Post by meatpan on 2009-09-07
Where is the .so file?  The command 'dkpg -L freeglut3-dev' should show you the install location for each file in the package.  Once you find the install loc of the so, could you add the directory to the LD_LIBRARY_PATH in the users environment?  Verify your LD_LIBRARY_PATH is correct by running 'ldd' on the shipped executable.  If there is a missing lib, you should see a 'not-found' in the entry for glut.

As a personal preference, I install packages that don't conform to convention in /opt.  It's easier to keep track of dependencies and versioning info because the packages are grouped, but comes with the cost of maintaining a verbose setup of LD_LIBRARY_PATH, CLASSPATH, PATH, etc.., in the user/sys environment.

---

