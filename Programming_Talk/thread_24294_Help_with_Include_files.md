---
title: "Help with Include files"
date: 2005-04-06
forum: Programming Talk
---

### Post by jsradley on 2005-04-06
Hi,
I have apt-get build-essentials, and have gcc working with the standard Helloworld.c program.

My problem is with #Includes for other packages.
For example, take Python. I have apt-get the Python Dev package, and can see the Python.h is located in /usr/include/python2.4/Python.h (from memory as I am in my lunch hr at work!)

If I add #include <Python.h> to hello.c, the compiler can't find it.

So what is done to tell the compiler where all the includes are?
Do I create my own Environment variable, or is their a built in solution that I haven't done or found yet.

Thanks
John

---

### Post by thumper on 2005-04-06
You need to pass the include directories to the compiler on the command line.  This is normally done through the makefile, but on the command line you can use -I <include dir>.

> gcc -I /usr/include/python2.4 hello.c 

I think that the -I flag might be deprecated for gcc 4, but the 3.x versions should be OK.

Tim

---

### Post by jsradley on 2005-04-07
Hi,
Many thanks for your comment - it pointed me in the right direction.
In fact the old rpm I was trying to compile had Python 2.2 specified in the ./configure, but I didn't notice as it wasn't echoed in it's verbose output !
Anyway, an edit to Python2.4 solved that problem.

Thanks again
John

---

