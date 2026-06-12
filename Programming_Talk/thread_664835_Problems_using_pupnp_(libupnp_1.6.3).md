---
title: "Problems using pupnp (libupnp 1.6.3)"
date: 2008-01-11
forum: Programming Talk
---

### Post by ishaypeled on 2008-01-11
Hi, 
First off,  this post may indicate poor knowledge of Linux shared libraries on my side.
Having said that, I'm programming a NAS system with an embedded Linux system.
For the interface of this system, I need UPnP support, and I chose libupnp 1.6.3 to provide the UPnP stack.
After a successful configure, make and make install commands, I wanted to test the new library.
The problem is, simply, that when I include the header file of this library, and try to compile, I get lots of compilation errors that imply missing methods/constants/...
When I compile the sample applications the are included with the package by typing g++ <cpp file> I get similar errors, but when I run the Makefile for those applications everything compiles just fine.
I know it's probably just missing knowledge on my side about using external libraries in Linux, and that the solution is probably simple, but I since I couldn't put my finger on what the problem is, I couldn't Google it.
Any help is very much appreciated.

---

### Post by geraldm on 2008-01-12
It is best to use a Makefile. 

You are probably omitting information usually put into "CFLAGS" within the Makefile.  That information needs to be supplied in the command line if you are not using the Makefile.

There should also be some information supplied in "LIBS" or an equivalent name in the Makefile.  These are needed for proper linking.

Look at the Makefile that compiled correctly for you.  That should give you some idea of what needs to be in a Makefile to work.  

If you get stuck, do not hesitate to post.  There should be some helpful information to programmers new to linux, and some HOWTOs may need to be made available in more obvious places if you cannot find them.

Gerald

---

