---
title: "little g++  (mingw32) warnings annoying"
date: 2010-11-29
forum: Programming Talk
---

### Post by Søren on 2010-11-29
i dont think there is anything wring with my code but i get these warnings all the time even with a basic hello world. is there some way i can get rid of these or else what do i do to fix what it is warning me about? enable auto import whaa? 

```
c:/mingw/bin/../lib/gcc/mingw32/4.5.0/../../../../mingw32/bin/ld.exe: warning: a
uto-importing has been activated without --enable-auto-import specified on the c
ommand line.
This should work unless it involves constant data structures referencing symbols
 from auto-imported DLLs.
```

---

### Post by Arndt on 2010-11-29
> **Søren said:**
> i dont think there is anything wring with my code but i get these warnings all the time even with a basic hello world. is there some way i can get rid of these or else what do i do to fix what it is warning me about? enable auto import whaa? 

```
c:/mingw/bin/../lib/gcc/mingw32/4.5.0/../../../../mingw32/bin/ld.exe: warning: a
uto-importing has been activated without --enable-auto-import specified on the c
ommand line.
This should work unless it involves constant data structures referencing symbols
 from auto-imported DLLs.
```

I have no idea, but googling for "auto-importing mingw" brought up some pages that seemed to be relevant (and as usual, some forums with questions like yours and no answers).

---

### Post by Søren on 2010-11-29
yeah i tried the google. i just dont understand any of the things being talked about. thanks.

---

### Post by PaulM1985 on 2010-11-29
Just a guess, but have you tried adding --enable-auto-import to the command line where you are compiling?

---

### Post by Søren on 2010-11-29
> **PaulM1985 said:**
> Just a guess, but have you tried adding --enable-auto-import to the command line where you are compiling?

ok that gets rid of the warning. but i dont want to have to type that in every time i compile? surely mingw doesnt expect me to this? that's retarded. yeah i can just press up arrow to repeat my previous command but that's not the point. i just want a simple compile without being told about all this bu#lshit. i have all my includes set right. the code is extremely basic. why the hell do i have to type 86 characters to get it compiled? i reject this.

---

### Post by Søren on 2010-11-29
```
C:\Users\William_Wallace\Desktop>type cppprogram.cpp
#include <iostream>
using namespace std;

int main()
{
 cout << "as you can see this is a really complicated program\n";
return 0;

}
C:\Users\William_Wallace\Desktop>g++ cppprogram.cpp
Info: resolving std::cout  by linking to __imp___ZSt4cout (auto-import)
c:/mingw/bin/../lib/gcc/mingw32/4.5.0/../../../../mingw32/bin/ld.exe: warning: a
uto-importing has been activated without --enable-auto-import specified on the c
ommand line.
This should work unless it involves constant data structures referencing symbols
 from auto-imported DLLs.

C:\Users\William_Wallace\Desktop>
```

---

### Post by spjackson on 2010-11-29
I can't test any theories just at the moment, but I might have a go whenever I next boot Windows.

My guess is that you have a new gcc (obviously since 4.5.0 is pretty recent) and an old version of binutils (specifically ld).

Here is a detailed description of the issue and a patch (for cygwin) from Feb 2009. [http://sourceware.org/ml/binutils/2009-02/msg00341.html](http://sourceware.org/ml/binutils/2009-02/msg00341.html) I would expect that by now mingw's ld would be patched too.

If that's not it and there really is no fix available at this time for mingw, I would recommend using 'make' to compile, rather than retyping command line switches.

I am trying to help, and would appreciate it if you refrain from the sort of rant you resorted to in response to PaulM1985's genuine attempt at helping you, otherwise you might find that the list of people willing to help you dwindles away.

---

### Post by Arndt on 2010-11-30
> **spjackson said:**
> 
I am trying to help, and would appreciate it if you refrain from the sort of rant you resorted to in response to PaulM1985's genuine attempt at helping you, otherwise you might find that the list of people willing to help you dwindles away.

I don't know how PaulM1985 took it, and I don't know how Søren meant it, but it didn't strike me as an attack on PaulM1985; rather frustration with the perceived inadequacies of mingw. But I'm not the one to judge, of course.

---

### Post by spjackson on 2010-11-30
My mistake, it isn't fixed.

[LIST]
[*]This did not occur with Mingw g++ prior to 4.5.0.
[*]The warning is produced with the latest binutils.
[*]Static builds are not affected.
[/LIST]
If I was using 4.5.0 on Windows with shared libstdc++, I would update my Makefile to deal with it.

---

### Post by Søren on 2010-11-30
thanks spjackson for researching for solutions. apologies to yourself and PaulM1985 if l sounded ungrateful or beligerant.  as suer Amdt noted, the frustration is at mingw32 not you guys. 

i think im just going to bite the bullet and install msvc. id like to use free software but ill be doing a lot of litttle programs and i dont want to be producing makefiles all the time. it's just annoying.

---

### Post by PaulM1985 on 2010-12-01
Another option may be to create a batch script that will run at startup which assigns a doskey which is the name of the compiler and then the argument that you need to add to the command line.  Then use this doskey every time you compile.  (I am not 100% sure this will work because I don't completely know if you can add an argument to a doskey.)

If this doesn't work, maybe you could write a script to do something similar... or just use Visual Studio for Windows development.

Paul

---

### Post by lucasart on 2010-12-01
> **Søren said:**
> thanks spjackson for researching for solutions. apologies to yourself and PaulM1985 if l sounded ungrateful or beligerant.  as suer Amdt noted, the frustration is at mingw32 not you guys. 

i think im just going to bite the bullet and install msvc. id like to use free software but ill be doing a lot of litttle programs and i dont want to be producing makefiles all the time. it's just annoying.

If you're using Windows in the first place, then the free software debate is pointless, as you're already the prisonner of Microsoft, and distributing your *.exe files will only trap more users into the Microsoft empire.

So if you want to develop for Windows, you might as well use Visual C++ express from Microsoft website. Besides being proprietary, it's undoubtedly a very good software, and also helps a lot to do GUI devloppement (although if you touch that with MSVC, you must forget about portability).

Another choice is to use Ubuntu and g++, if you're ready to change operating system (or dual boot). There are also IDE's that are free softwares and of (almost) comparable quality to MSVC.

---

