---
title: "32 bit to 64 bit"
date: 2012-07-24
forum: Packaging and Compiling Programs
---

### Post by gayathris on 2012-07-24
I have done a c++ program on ubuntu(32 bit) and is compiling perfectly. My server is of 64 bit. On putting in server, I get an error that " size of curl is negative". I think it is because of change in bits. 
 
How should I change it from 32 to 64 to make it run on server? Or do I need to add some library in server? if so which ones? 
 
Please help out.

---

### Post by Cheesemill on 2012-07-24
You need to recompile it for the correct target architecture (amd64).

Or you could try installing ia32-libs on the server to allow it to run 32-bit programs.

---

### Post by nehalem04 on 2012-07-24
The size of data types(int, float etc.) should be different in 32bit and 64bit OS. You've to recompile your program in 64bit OS to use the executable there.

---

### Post by Bufeu on 2012-07-24
> **gayathris said:**
> I have done a c++ program on ubuntu(32 bit) and is compiling perfectly. My server is of 64 bit. On putting in server, I get an error that " size of curl is negative". I think it is because of change in bits. 
 
How should I change it from 32 to 64 to make it run on server? Or do I need to add some library in server? if so which ones? 
 
Please help out.Yes, it's possible to compile (but not run!) 64 bit programs on a 32 bit system, if you are using a cross-compile (like GCC) and the full set of header files and libraries for the target platform. [http://ubuntuforums.org/showthread.php?t=518979](http://ubuntuforums.org/showthread.php?t=518979)

---

### Post by oldos2er on 2012-07-24
Moved to Packaging and Compiling Programs.

---

