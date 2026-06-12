---
title: "How can I Cross-Compile a program"
date: 2009-06-22
forum: Programming Talk
---

### Post by Ferralll on 2009-06-22
I have a simple program that I have been writing and would like to be able to compile it on my linux box in to a .exe file, and be able to use it at work on my windows computer.

For the life of me, I can not figure out how to do this.  It is either very difficult, or very easy. Either way, I just can not seem to find the answer. 


I have written a FORTRAN 77 program, and use g77 to compile it normally.  
I would like to find a way to compile it in to a .exe, or change the normal a.out in to a .exe


The program just gets data, crunches some numbers, and spits it back out. 

Also, there is no chance that I can download any sort of compiler or any programs on to my windows computer (very strict no free ware policy at work...)

---

### Post by Mirge on 2009-06-22
Compile it on Linux, then on a Windows computer of your own if available (or borrow a friend's).. compile on Windows.

Or compile in Windows, and run it using wine on linux.

---

### Post by Habbit on 2009-06-22
```
$ sudo apt-get install mingw32
```This will install a MinGW cross compiler that targets the Windows platform. You can build programs with the usual commands (gcc, etc.) by prefixing "i586-mingw32msvc-" to the command name, then run them with Wine. For example: ```
$ i586-mingw32msvc-g++ hello.cc -o hello.exe
$ wine hello.exe
Hello World!
```

---

### Post by Ferralll on 2009-07-13
Thanks Habbit for the help...

And I think I am almost there.  The "apt-get install mingw32" gave me a wonderful cross-compiler for C++ and those things... but I can not figure out how to do the same thing for FORTRAN 77.  

I am trying to figure it out, but so far have had no luck.

---

### Post by pepperphd on 2009-07-13
Can I link to third party, unsupported software that I've never tested or researched ever, like the following FORTRAN to C converter I found on Google?  [http://www.freedownloadscenter.com/Programming/C_and_C___Tools_and_Components/Fortran_to_C_Converter__f2c_.html](http://www.freedownloadscenter.com/Programming/C_and_C___Tools_and_Components/Fortran_to_C_Converter__f2c_.html)

---

### Post by Ferralll on 2009-07-13
I might just be retarded... but I can not figure out how the f2c program works. 

I have tried using f2c on some programs (including a 3 line helloworld) and I can not get c++, g++ or gcc to compile it.  My c++ is very rusty, but I looked at the code that it spit out, and I have no idea what the heck it is saying. 

But I saw that mingw has a g77 compiler that can be used with it... I just have no idea how to get it on to my computer.  (Not to mention... I have very little idea of how the mingw32 works. The website says that it is for windows and not for linux, so it is of little help to me)

---

### Post by jpkotta on 2009-07-13
[http://ubuntuforums.org/showthread.php?t=643778](http://ubuntuforums.org/showthread.php?t=643778)

Kind of old, and I haven't tried it, but I'll bet it will work with minimal hiccups.

---

### Post by Ferralll on 2009-07-14
jpkotta >>  Thankyou very much for the link.  

I followed the directions on that page, and it worked perfectly.  Now I do not have to learn C so that I can cross compile (which I was about ready to give up and do) and I can use my F77.

Thanks again!!

---

