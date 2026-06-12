---
title: "undefined reference to `main'"
date: 2005-08-26
forum: Programming Talk
---

### Post by Svartvit on 2005-08-26
My computer is acting strange. Sometimes, in no particular pattern, g++ won't let me compile even the simplest of Hello World codes, and sometimes everything works as smooth as it comes. The complete error message I get is:
```
dogen@zazen:~/programming/s2gdb$ g++ s2gdb.cpp -o s2gdb
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o(.text+0x18): In function `_start':
../sysdeps/i386/elf/start.S:98: undefined reference to `main'
collect2: ld returned 1 exit status
```
which doesn't make any sense to me at all, since I have plenty of main() function in my HelloWorld.cpp. Googling is futile. What the heck?

PS. Jaegermeister and Beer rocks. \\:D/

---

### Post by LordHunter317 on 2005-08-26
You didn't tell it to complie HelloWorld.cpp, hence it didn't try and didn't find a main().

---

### Post by Svartvit on 2005-08-26
[QUOTE=LordHunter317]You didn't tell it to complie HelloWorld.cpp, hence it didn't try and didn't find a main().[/QUOTE]
No, you're right, I told it to compile s2gdb.cpp

---

### Post by tommie-lie on 2005-08-27
Is there a main function (with the correct signature) in s2gdb.cpp?

---

### Post by rfrayer on 2008-11-04
its funny ive seen this error all opver the place for varioue programs for me i get that exact same error trying to compile any version of gyachi and variouse other errors similer that there just isnt any answers for when it comes to other programs.

This is with Ubuntu Ibex mind you. Now im not by any means saying ibex sucks or anything because it does run nice and smooth... no boot errors etc. But there is a problem. Ive seen a load of bug reports just flat closed and say answered with absolutely no answer to them so obviousely someone must know a fix to this because as time goes on and hardy looses its upgrade support and attention and we (Paying Dell Customers) caugh cagh have to upgrade in order to continue getting support. This situation will suck on so many levels.

---

### Post by escapee on 2008-11-04
rfrayer, all that error means is that the source containing the main function was not linked against the rest of the code.  It is not an error in Ibex, settle down.  Nothing is wrong, someone just forgot link in the file or the makefile you are using is broken.

---

### Post by rfrayer on 2008-11-05
oh dont get me wrong im not hyped about it. Ive successfully compiled the exacdt same source code in hardy, gutsy, breezy etc and that error didnt exist. Im allmost wondering if i need to maybe export a different gcc version before i click make or something or if maybe it has something installed extra that checks for errors in the make file that were automaticly skipped in hardy.

Im allmost wondering if this might help anyways im gonna try it later and see

export CC=gcc-3.4 or 2.0 one of em


Ubuntu ingeneral even ibex is still by far the best linux distro in my opinion and Im sure we would all agree blows winblows xp, vesta etc out of the water.

---

