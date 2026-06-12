---
title: "conio and getch not there?"
date: 2009-10-06
forum: Programming Talk
---

### Post by abhilashm86 on 2009-10-06
is there a reson getch(), clrscr and conio.h not supported in linux?there was discussion in college, so why exactly these funcyions not there,
also will ./a.out got from program either c/c++, will run in windows?? how to do it?

---

### Post by Zugzwang on 2009-10-06
Because they are non-standard. Linux supports the POSIX standard plus everything that is defined by its libraries (plus some system stuff that portable software shouldn't use). Portable software shouldn't use it anyway, so there is no real need to have it. 

conio.h basically contains some stuff the people at Borland(?) made up themselves. 

Actually, there was some project to have a "libconio" in Linux, but it was abandoned for some reason: [http://sourceforge.net/projects/libconio/](http://sourceforge.net/projects/libconio/)

---

### Post by Tony Flury on 2009-10-06
To answer your other question - running gcc or g++ (or any compiler) on linux and creating the a.out executable will not generate a executable that will run on Windows. To do that you will need research cross-compiling and cross-linking. Cross compiling is the term used to describe using one system (for instance Linux) to build an application to be executed on another (for instance Windows).

The other way to achieve what you want to do, is use entirely standard POSIX libraries (such as stdio - not conio) and then just move the source code and compile it on the target system - however I am not sure how POSIX compliant MS Windows is - so this might not work, and you might have to do some rework to move the source code between Linux and MS Windows.

---

### Post by nvteighen on 2009-10-06
You're confusing POSIX compliance with compliance to the ISO C Standard. POSIX-compliance is related to stuff declared e.g. in unistd.h or headers placed in sys/...

Remember that GNU/Linux is not 100% POSIX compliant either, but UNIX systems (like Mac OS X) are. ([http://en.wikipedia.org/wiki/POSIX#POSIX-oriented_operating_systems](http://en.wikipedia.org/wiki/POSIX#POSIX-oriented_operating_systems))

Always try to use the C Standard Library as your base development framework if you plan to cross-compile... POSIX functions may be used if you're sure the target system complies to them...

---

### Post by Can+~ on 2009-10-06
conio.h is not part of the C standard, nor POSIX.

The closest thing I can think of is ncurses.

---

### Post by abhilashm86 on 2009-10-07
oh now i get the point, i've heard gcc is there in windows also, also gcc behaves same as in linux, so if i create executable in linux, can i run that on windows? 
(i think only some programs work in windows, if we use fork() and other linux system calls, it'll totally blank for windows!!)

---

### Post by wmcbrine on 2009-10-07
I'd just like to add that your college was irresponsible for teaching you conio, at least without also teaching you that it was archaic, proprietary and non-portable. (It *is* simple, which I guess was their main concern.)

You cannot under any circumstances compile a single executable that will run natively under both Windows and Linux. However, you can certainly write a program that can be compiled for either platform with no changes to the source code. To do this, you'll probably want to stick to ANSI C, though as mentioned you could try curses as a substitute for conio. (There are also some projects to map conio to curses, for porting purposes. But you shouldn't be writing any new code for conio. Please file it under "things that were a waste of time learning", and move on.)

---

