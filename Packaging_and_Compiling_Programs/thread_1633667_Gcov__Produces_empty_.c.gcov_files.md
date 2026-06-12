---
title: "Gcov : Produces empty .c.gcov files"
date: 2010-11-29
forum: Packaging and Compiling Programs
---

### Post by techtalk on 2010-11-29
Hi all,

I am trying to use gcov on a library (.so) with GCC 4.5. When I compile it does produce the .gcno file. When I run the test it does produce .gcda files corresponding to the library source files. But when I run gcov on source file it produces an empty .c.gcov file. 

Please help.

-techtalk

---

### Post by SevenMachines on 2010-11-30
can't think of anything off the top of my head, can you post some code/commands if possible?

---

### Post by techtalk on 2010-11-30
I cannot post the code. But I do the same procedure on the application and gcov does procude .c.gcov files which have the code coverage information.  

The problem only occurs for .so files.

One thing is that I am running on an x86 embedded system.  I build my files on my host.  Copy over those source files and .gcno files to the embedded system.  I run my application there.  And then copy over the .gcda files produced for the .so library to the host (where I originally compiled it).  Then I run gcov -f <file_name> and it produces a .c.gcov file which is empty.

I follow the same procedure for the application binary and that works fine.  

I have the following flags in the .so Makefile 

CFLAGS += --coverage -ftest-coverage -g -fprofile-arcs

I am dynamically linking the "my.so" to "libgcov.so" and the application is statically linking "my.so", "libgcov.so" in the "mybinary"

---

### Post by arun.channagiri on 2011-02-08
> **techtalk said:**
> Hi all,

I am trying to use gcov on a library (.so) with GCC 4.5. When I compile it does produce the .gcno file. When I run the test it does produce .gcda files corresponding to the library source files. But when I run gcov on source file it produces an empty .c.gcov file. 

Please help.

-techtalk
hi did u able to come out of this proble, am also facing similar problem in my project let me know if it solved for u

---

