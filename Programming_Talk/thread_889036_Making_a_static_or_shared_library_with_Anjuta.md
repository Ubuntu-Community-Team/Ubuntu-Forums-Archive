---
title: "Making a static or shared library with Anjuta"
date: 2008-08-13
forum: Programming Talk
---

### Post by kevinchannon on 2008-08-13
Hi, I also posted this on the Anjuta forum on sourceforge, but have had no response in a couple of days.  A was wondering if anyone here can answer this...
 
I'm using Anjuta 2.4.1 on Ubuntu Hardy with gcc 4.2.3 
 
I wish to compile a program into a library (static or shared, I don't think it's important at this stage). I have made a project using the "new -> project -> generic C++ wizard", say it's called "libmylib", which has a bunch of source and header files in the src directory created by the wizard. I want to create a library and a test program to debug and test the library as I'm writing it, so I have created two targets in the src directory (which is where the default target made by the wizard went) called, say, libmylib.a and testMyLib. Most of the files in the src directory are used by libmylib.a and the rest (main.cc and libmylib.hpp) by testMyLib. Now, my files compile correctly and I can see that the object files are created in src and ranlib is run to produce libmylib.a. main.cc is also compiled, but when linking begins (at least that's what I think it is, it's the bit where *.o is made into an excecutable) there are a whole bunch of error messages saying that all the functions in the library are undefined. I have been banging my head against this wall for two days now and I don't know how to get past it. I think that it must be something to do with something in the project options dialogue or the options dialogue for testMyLib, but I can't seem to find what I should type into which field! Any help would be greatly appreciated. If my description is not clear enough, I can send a tar.gz with the contents of the project for someone to examine as I'm sure that this is a very simple problem but I am missing a key point. I just need to get past this configuration problem so that I can start coding again! :-) 
 
Thanks again, 
Kevin

---

### Post by Darkhack on 2008-08-13
This should explain everything in detail.  It provides all the commands to compile as a static or dynamic library and even has example code.

[http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html](http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html)

---

### Post by kevinchannon on 2008-08-14
Thanks Darkhack, but I already know how to get gcc to do the things that are mentioned in that link.  What I can't do is get Anjuta to make gcc do them for me :-(  I think it's that I don't know how to configure Anjuta properly.

Thanks anyway though :-)

---

### Post by Darkhack on 2008-08-14
Anjuta is a great code editor but I've also never been able to figure out how to make it work properly.  For some reason, Anjuta always messes up my makefiles and I have to create them manually.  Even the project wizard where I select "GTK+ Project" doesn't link my GTK+ libs to my project correctly and I have to go into the makefile to change it.  The lesson is, don't let Anjuta manage your makefiles.  It always ends painfully.

---

