---
title: "C Programming/Windows compiler"
date: 2009-08-05
forum: Programming Talk
---

### Post by hyperAura on 2009-08-05
Hi guys, i program in linux c,java,c++ so i dont know anything about any compilers in windows or nice gui software that can help someone program. 

I have a friend though that is not using linux and wants to write a program for a small company. He asked me for help on what programs he needs in order to program in c in windows.. 
 
So far he told me he was programming at uni in a program called codegear but this is not free.. 

Suggest please any compilers or software that you guys use for programming in c in windows that are free..

Thnx..

---

### Post by Majorix on 2009-08-05
Code::blocks, Eclipse, NetBeans...

---

### Post by credobyte on 2009-08-05
Visual C++ Express, Blodshed Dev-C++, CodeBlocks .. for a compiler without IDE, MinGW !

---

### Post by Majorix on 2009-08-05
> **credobyte said:**
> Visual C++ Express, **Blodshed Dev-C++**, CodeBlocks .. for a compiler without IDE, MinGW !

I don't think that one (in bold) is being actively developed anymore. I did use it in the past though, and it was ok.

---

### Post by hyperAura on 2009-08-05
well thnx both of u.. i am downloading netbeans atm.. 

Eclipse says:  IDE for C/C++ developers with Mylyn integration but since i dont know what Mylyn is and i am not using it, i am not gonna download it.. 

Visual C++ Express, does it have a compiler for C or is it just for C++?

---

### Post by Majorix on 2009-08-05
> **hyperAura said:**
> well thnx both of u.. i am downloading netbeans atm.. 

Eclipse says:  IDE for C/C++ developers with Mylyn integration but since i dont know what Mylyn is and i am not using it, i am not gonna download it.. 

Visual C++ Express, does it have a compiler for C or is it just for C++?

@Eclipse: I have never heard of that. Maybe you should just ignore it and try Eclipse? Because it is one of the most popular and functional IDE's out there.

And I don't know about the other question.

---

### Post by credobyte on 2009-08-05
> **Majorix said:**
> I don't think that one (in bold) is being actively developed anymore. I did use it in the past though, and it was ok.

More likely it's not being developed at all, however, IDE is still quite good ( except, MinGW should be replaced .. .exe's are detected as trojan horses :D ).
@ OP: Yes, Visual C++ supports C/C++.

---

### Post by Sockerdrickan on 2009-08-05
> **hyperAura said:**
>  Visual C++ Express, does it have a compiler for C or is it just for C++?
C++ includes almost everything of C if you didn't already know that...

---

### Post by hyperAura on 2009-08-05
C++ includes almost everything of C if you didn't already know that...

yes i know but if u r using the c++ compiler then u get different errors which could have not been errors if you were using c compiler.. as u said almost.. and almost isnt enough..:)

---

### Post by Sockerdrickan on 2009-08-05
Well it would be most pitiful if microsofts compiler couldn't compile pure C code.

[http://www.google.se/search?hl=sv&rlz=1G1GGLQ_SVXX248&q=visual+c%2B%2B+express+%22compile+c%22&btnG=S%C3%B6k&meta=](http://www.google.se/search?hl=sv&rlz=1G1GGLQ_SVXX248&q=visual+c%2B%2B+express+%22compile+c%22&btnG=S%C3%B6k&meta=)

---

### Post by Lila_IT_CMU on 2009-08-05
hello...

where can i download c++ tutorials for linux?


thanks

---

### Post by credobyte on 2009-08-05
> **Lila_IT_CMU said:**
> hello...

where can i download c++ tutorials for linux?


thanks

[http://www.cprogramming.com/tutorial.html#c++tutorial](http://www.cprogramming.com/tutorial.html#c++tutorial) ( however, you should consider using *Search* function .. it'll save your/our time ).

---

### Post by Drone022 on 2009-08-05
```
sudo apt-get teh-Internetz
```

---

### Post by ToyImp on 2009-08-05
NetBeans! Its all that you'll ever need. 
Also get rid of windows. :P

---

### Post by hyperAura on 2009-08-05
Well as i said its not for me m8.. i am tryin to help a friend that is not familiar with computers at all.. only thing he knows is a couple of programming languages he was taught.. well i am installing netbeans on my machine now, if everything works right, i am gonna do it on his pc..

---

### Post by abhilashm86 on 2009-08-05
what about Borland Turbo c compiler, in my college, they use it only...........

---

### Post by Sockerdrickan on 2009-08-05
> **abhilashm86 said:**
> what about Borland Turbo c compiler, in my college, they use it only...........
[SIZE=4]**-_-**[/SIZE]

if you just want a compiler get gcc for windows

---

### Post by Tux118 on 2009-08-05
> **hyperAura said:**
> Hi guys, i program in linux c,java,c++ so i dont know anything about any compilers in windows or nice gui software that can help someone program. 

I have a friend though that is not using linux and wants to write a program for a small company. He asked me for help on what programs he needs in order to program in c in windows.. 
 
So far he told me he was programming at uni in a program called codegear but this is not free.. 

Suggest please any compilers or software that you guys use for programming in c in windows that are free..

Thnx..

There is a bunch of good software for windows but they all cost money. :(

---

### Post by abhilashm86 on 2009-08-05
> **Tux0r said:**
> [SIZE=4]**-_-**[/SIZE]

if you just want a compiler get gcc for windows

oh cool, good to see gcc in windows, i don't use windows, just in college, no one can question, college is kinda propreity and lab people don't know linux!!!! i'm linux user @ home:)

---

### Post by Sockerdrickan on 2009-08-05
> **abhilashm86 said:**
> oh cool, good to see gcc in windows, i don't use windows, just in college, no one can question, college is kinda propreity and lab people don't know linux!!!! i'm linux user @ home:)
Oh, ok. Check this out and get it for your school [http://www.equation.com/servlet/equation.cmd?fa=fortran](http://www.equation.com/servlet/equation.cmd?fa=fortran)

---

### Post by hyperAura on 2009-08-05
well guys i did install netbeans.. after that i installed Gzip for Windows and  LibArchive for Windows, TAR.. I had to install these two, to be able to install MiniGW which files are in format .gz and .tar .. The problem now is that as im installing MiniGW i'm gettin the following message:

File already exists - skipping mingwrt-3.15.2-mingw32-dev.tar.gz
File already exists - skipping w32api-3.13-mingw32-dev.tar.gz
File already exists - skipping binutils-2.19.1-mingw32-bin.tar.gz
File already exists - skipping gcc-core-3.4.5-20060117-3.tar.gz
File already exists - skipping gcc-g++-3.4.5-20060117-3.tar.gz
File already exists - skipping gcc-g77-3.4.5-20060117-3.tar.gz
File already exists - skipping gcc-ada-3.4.5-20060117-3.tar.gz
File already exists - skipping gcc-java-3.4.5-20060117-3.tar.gz
File already exists - skipping gcc-objc-3.4.5-20060117-3.tar.gz
File already exists - skipping mingw32-make-3.81-20080326-2.tar.gz
Create folder: C:\MinGW
Extract: C:\MinGW\installed.ini... 100%
Extracting mingwrt-3.15.2-mingw32-dev.tar.gz
untgz::extract -d 'C:\MinGW' -z 'C:\Users\Mario\Desktop\mingwrt-3.15.2-mingw32-dev.tar.gz' 
Writing doc/runtime/CONTRIBUTORS
Writing doc/runtime/DISCLAIMER
Writing doc/runtime/README
....
Writing lib/libmsvcr70.a
Writing lib/libmsvcr70d.a
Writing lib/libmsvcr71.a
Writing lib/libmsvcr71d.a
Writing lib/libmsvcr80.a
Writing lib/libmsvcr80d.a
Writing lib/libmsvcr90.a
Writing lib/libmsvcr90d.a
Writing lib/libmsvcrt.a
Writing lib/libmsvcrtd.a
Writing lib/txtmode.o
Writing share/man/man3/basename.3
Writing share/man/man3/dirname.3
Writing bin/mingwm10.dll
extraction complete.
Extracting w32api-3.13-mingw32-dev.tar.gz
untgz::extract -d 'C:\MinGW' -z 'C:\Users\Mario\Desktop\w32api-3.13-mingw32-dev.tar.gz' 
tgz_extract: bad header checksum
Error: Failure reading from tarball.

and the installation fails.. i removed the file and downloaded it again but it wont open.. the file is corrupted.. did anyone else have this problem?

---

### Post by hyperAura on 2009-08-05
atm im tryin to install several packages through cygwin and ive also marked MiniGW packages, hopefully it wont be the same directory that the packages are going to be downloaded from..

---

### Post by Sockerdrickan on 2009-08-05
Just install what I posted and you've got everything you need except text editor [www.gedit.org]("http://www.gedit.org")

---

### Post by hyperAura on 2009-08-05
well thnx ive been using gedit for a long time now for writing my programs in c/c++.. although i did not know it existed for windows.. as for the gcc compiler im waitin for cygwin to finish installation.. if it does not work im gonna use ur post..

---

### Post by Sockerdrickan on 2009-08-05
> **hyperAura said:**
> well thnx ive been using gedit for a long time now for writing my programs in c/c++.. although i did not know it existed for windows.. as for the gcc compiler im waitin for cygwin to finish installation.. if it does not work im gonna use ur post..
Yeah and it works great on Windows ;) dude don't use cygwin you get lots of weird dependencies, gcc that I posted compiles native windows binaries.

---

### Post by hyperAura on 2009-08-05
well ive installed cygwin and soon as i type startx, i get a screen which looks like AnotherLevelUp but i dont like the look of it.. im gonna try gcc later on today..

---

