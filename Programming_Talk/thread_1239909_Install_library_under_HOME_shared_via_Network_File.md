---
title: "Install library under HOME shared via Network File System"
date: 2009-08-14
forum: Programming Talk
---

### Post by flylehe on 2009-08-14
Hi,

My Home directory is shared among several linux computers via Network File System.
I would like to install some C C++ library from source under my Home directory, and wish they can be used under all the linux computers.

Do I have to install different versions of the library under different directories of my Home for different computer?

Assuming I have a C C++ program that calls these libraries, how do I specify different include and link files and directories for different computer in Makefile? Is it to determine the directories based on the hostname of the computer?

Is it possible to combine the different versions of the .a and .so files and header files of the libary for different linux computers so that the include and link files and directories of the libary are the same for all the computers and I don't have to specify different directories for different computer in the Makefile of my C C++ program?

Thanks and regards!

---

