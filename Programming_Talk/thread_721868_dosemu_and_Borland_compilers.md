---
title: "dosemu and Borland compilers"
date: 2008-03-11
forum: Programming Talk
---

### Post by ganoderma on 2008-03-11
I have been trying to learn C and C++ , and have found the GNU C and C++ compilers too advanced, although [http://www.cprogramming.com/](http://www.cprogramming.com/) is very helpful.  There are many introductory texts available for Borland and MS compilers that are MS based.  I installed Borland's (Turbo C++) TC Lite compiler in dosemu, and it works very well. A copy (TCLite 1.0.1) is available free as a Borland archive - i don't know if that works, as my copy of TCLite was purchased a long time ago. If you download dosemu from the ubuntu respository, freedos comes installed with it, and you can run dosemu as a normal user. (Enter C:\command com at the prompt.)  If you download and install dosemu and freedos from their sourceforge sites, you will have to run dosemu as root.  Borland's TCLite compiler works well, but I haven't been able to get Borlands Turbo C++ 3.0 compiler for DOS to work in dosemu.  I haven't tried substituting MSDOS system files for the freedos system files yet, but I may do that to try to get the 3.0 compiler to work.  TCLite does install in dosbox, but I haven't been able to get it to work  yet there at all.

---

### Post by Zugzwang on 2008-03-12
> **ganoderma said:**
> [...]  but I haven't been able to get Borlands Turbo C++ 3.0 compiler for DOS to work in dosemu.  [...]

"It doesn't work" isn't very specific - you could please tell us *what* doesn't work? Any error messages, etc.?

---

### Post by ganoderma on 2008-03-23
Thanks Zugzwand for replying to my post.  When I try to execute the Borland C++ 3.0 program (by entering tc.exe) in dosemu 1.4.0, nothing happens, even though the same program with the same setup (same files in same directories) runs without a hitch in dos after leaving Windows 98SE.  The Borland setup program said to be sure to have files=20 in config.sys  - I have files=40 in the dosemu config.sys, - so I don't think that is a problem, and there is no autoexec.bat  file at  all when I'm running the program under Windows 98SE dos (7.10).  Redirection for my D: drive is deleted, and the notation "The D: drive in dosemu is redirected to my home directory.'  I haven't yet tried to substitute msdos.sys and io.sys for the freedos versions.

Any help you might suggest will be much appreciated.

Thanks!

Ganoderma

---

### Post by bruce89 on 2008-03-23
What's so "advanced" about gcc and g++? Compiling a C program is as simple as
```
gcc -g -Wall -o prog source.c
```
*-g* means "add debugging info", *-Wall* means "Warn about everything".

Using a DOS program and emulating it seems a bit much.

---

### Post by stevescripts on 2008-03-23
> **bruce89 said:**
> 
Using a DOS program and emulating it seems a bit much.

+1 ...

for the OP - is your end desire to build DOS programs on Ubuntu?

Using gcc and friends is not as hard as it appears in the beginning.

Steve

---

### Post by ganoderma on 2008-03-23
Yes, it is, and i've used the gcc and g++ compliers, and they're ok,  However, I'm trying to learn C and/or C++, and almost all of the texts available to me assume an MSDOS base.  When I try to use conio.h, I'm told to use ncurses or one of its derivatives - I don't know what ncurses is, and the explanations on sourceforge and similar places are mystifying. I don't like running windows - I'm running Gutsy as my preferred OS - and I need to understand some of the ins and outs of C /C++ . Yes, I'm able to find some linux files sometimes and am able to get around in linux. i just don't have the books and explanations that I need to understand and use the g++ and/or gcc compliers.

Ganoderma

---

### Post by Wybiral on 2008-03-23
> **ganoderma said:**
> Yes, it is, and i've used the gcc and g++ compliers, and they're ok,  However, I'm trying to learn C and/or C++, and almost all of the texts available to me assume an MSDOS base.  When I try to use conio.h, I'm told to use ncurses or one of its derivatives - I don't know what ncurses is, and the explanations on sourceforge and similar places are mystifying. I don't like running windows - I'm running Gutsy as my preferred OS - and I need to understand some of the ins and outs of C /C++ . Yes, I'm able to find some linux files sometimes and am able to get around in linux. i just don't have the books and explanations that I need to understand and use the g++ and/or gcc compliers.

Ganoderma

Are you trying to learn C or C++? Whichever one of those, are you trying to learn the language or how to use conio.h? If you're trying to learn the language, then use a tutorial or book that teaches _standard_ C or C++, not some platform specific garbage.

---

### Post by stevescripts on 2008-03-24
I have been sitting here and pondering my next reponse for well over a half-hour.

The C and C++ standards, are not written with different guidance for different platforms.  As pointed out by Wybiral, it would be a good idea to focus on one or the other in the beginning.  

A *good* programming book/tutorial (especially for those just learning) should contain little to no platform specific code and headers, and will point out differences along the way in the event that they do.

cin and cout, and printf() and scanf() could care less what platform they are going to be built for.  

I understand the problem with books and tutorials that are highly MSDOS/Windows oriented, in fact, I ran into the same thing some years back, when I decided to (re)learn programming.  (I am *old*, my initial computer programming classes were FORTRAN II - circa 1968...)  

You need to learn about types, pointers, data structures and such things, more than you need to learn about system specific function calls and headers. Again, I understand the beginners penchant for wanting to use things like system(pause) and system(cls)... (I may well be forgetting the exact syntax here)

Please understand, we are not trying to be some sort of elitists here.  We want to help you focus on learning the language of your choice.  (and if you have lurked/searched around here much, you know that many of us would have suggested starting with a higher level language)

You say you like Gutsy, and don't care for windows.  Focus on using the programming language to solve problems first, and learn to interact with the OS and user interface later.  

Much more on my mind, but getting late here.  Again, we don't mean to be discouraging, the Ubuntu community is a very helpful place. (Heck, even the programmers here hardly even flame each other over our differences ;) )

Steve

---

