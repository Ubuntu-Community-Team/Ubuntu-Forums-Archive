---
title: "NetBeans C/C++ on Windows"
date: 2009-10-19
forum: Programming Talk
---

### Post by kavon89 on 2009-10-19
I've grown accustomed to using NetBeans to compile Java & C++ code on Linux. However, some circumstances have made me switch back to Windows and I don't know how to compile my code. I don't mind using another compiler etc, as long as I could configure it in NetBeans, however I would rather not use Visual Studio.

I know I should probably ask this in a NetBeans forum, but I dislike making throwaway accounts and I figure someone must know how to install a complier on Windows. :(

(I tried Cygwin and after compiling hello world it complained that I was missing a .dll if I moved the binary into another folder.)

---

### Post by OpenGuard on 2009-10-19
Cygwin folder needs to be added to your Path list ( environment tables ). For distribution, you'll need to pack your program with cygwin.dll ( if I remember right ), otherwise, no one will be able to run it.

P.S. - I would go for VS C++ 2008 Express.

---

### Post by kavon89 on 2009-10-19
> **OpenGuard said:**
> Cygwin folder needs to be added to your Path list ( environment tables ). For distribution, you'll need to pack your program with cygwin.dll ( if I remember right ), otherwise, no one will be able to run it.

P.S. - I would go for VS C++ 2008 Express.

Yea, having to pack a cygwin.dll pissed me off so I removed cygwin. I found a tutorial [here]("http://www.netbeans.org/community/releases/67/cpp-setup-instructions.html#mingw") to install MinGW, hopefully that doesn't require something extra other than the binary to run, otherwise I'll just bite the bullet and use Visual C++ Express.

---

### Post by OpenGuard on 2009-10-19
> **kavon89 said:**
> Yea, having to pack a cygwin.dll pissed me off so I removed cygwin. I found a tutorial [here]("http://www.netbeans.org/community/releases/67/cpp-setup-instructions.html#mingw") to install MinGW, hopefully that doesn't require something extra other than the binary to run, otherwise I'll just bite the bullet and use Visual C++ Express.

MinGW make is incompatible with NetBeans ( that's why you need Cygwin or MSYS ).

---

### Post by froggyswamp on 2009-10-19
I understand it's offtopic, sorry, but can you please say what "circumstances" made you switch back to windows? Just curious, no other intentions. PM would also be fine.

---

### Post by kavon89 on 2009-10-19
> **froggyswamp said:**
> I understand it's offtopic, sorry, but can you please say what "circumstances" made you switch back to windows? Just curious, no other intentions. PM would also be fine.


I'd like the ability to develop programs for Windows because of the larger audience and also play games natively from time to time. (Plus two larger projects I'm working on, although developed in Java and using Swing, are targeting Windows platforms currently.)

Since Linux and other operating systems are much lighter and I have a hard time settling on one distro, I could easily virtualize Linux and any other OS I feel like trying/developing for like FreeBSD and Solaris.

> MinGW make is incompatible with NetBeans ( that's why you need Cygwin or MSYS ).

I managed to get MinGW, MSYS, and GDB working with NetBeans and it was quite easy, Cygwin blows. ;)

---

