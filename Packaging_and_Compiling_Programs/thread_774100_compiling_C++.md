---
title: "compiling C++"
date: 2008-04-29
forum: Packaging and Compiling Programs
---

### Post by akimatsu123 on 2008-04-29
hi,

i wrote a C++ program on gedit. i know that i can also use IDE, but since im just learning i would just like to write programs, and compile them to make sure they run. 

i know that i can compile/build a program to run under ubuntu by using
```

g++ FILENAME.cpp -o FILENAME

```

i can then run this program using the command

```
./FILENAME
```

i have two questions. first of all, what exactly does the "./" mean? what am i doing exactly? does it mean "run this program"? quite an odd syntax if it does.

secondly, how do i compile/build into a .exe file for windows that runs under command prompt?

thanks,

---

### Post by ivze on 2008-04-29
1. ./means that you will to run NAMELY this programm, located in you current working dir. In comparisson, when you run g++, it's not where you work, but in some dir, included in $PATH. 
This has been done to prevent situations when a user thinks, he/she launches a standart utility (e.g. ls), but actually launches some programm named ls, placed in current working dir by somebody, trying to attack the user.

2.hmm... =) i am not competent enough!

---

### Post by akimatsu123 on 2008-04-29
> **ivze said:**
> 1. ./means that you will to run NAMELY this programm, located in you current working dir. In comparisson, when you run g++, it's not where you work, but in some dir, included in $PATH. 
This has been done to prevent situations when a user thinks, he/she launches a standart utility (e.g. ls), but actually launches some programm named ls, placed in current working dir by somebody, trying to attack the user.

ooohhh i see. that makes sense. thank you!

anyone wit help for compiling .exe?

---

### Post by Compyx on 2008-04-29
> **akimatsu123 said:**
> anyone wit help for compiling .exe?

```
g++ FILENAME.cpp -o FILENAME.exe
```
;)

Or do you mean compiling a Windows executable on a Linux box? That's opening a huge can of worms. I think you'd better stick to writing programs in portable C++ and learning the language and its standard library.

If you stick to portable code, you can always compile your program on Windows later. I think Microsoft has a version of their C and C++ compiler available for 'free' (NOT the FSF definition of free).

Cheers.

---

### Post by WW on 2008-04-29
Creating a Windows exe file from within Linux is called cross-compiling.  Here are a couple relevant threads:
[http://ubuntuforums.org/showthread.php?t=724495](http://ubuntuforums.org/showthread.php?t=724495)
[http://ubuntuforums.org/showthread.php?t=734799](http://ubuntuforums.org/showthread.php?t=734799)

---

### Post by noerrorsfound on 2008-04-30
Didn't read all replies...

---

### Post by kenono on 2008-09-06
For creating .exe from your cpp files I used to use [Dev-C++]("http://www.bloodshed.net/devcpp.html"). It's a good program that I found really easy to use.
It's Windows only I believe but then you need to be on Windows to run the .exe file generally anyway.

---

### Post by sallywon on 2008-09-06
I think you should download eclips IDE and then install it's C++ plugin, so if your program has problem it show to you if not it will compile your program easily.

---

