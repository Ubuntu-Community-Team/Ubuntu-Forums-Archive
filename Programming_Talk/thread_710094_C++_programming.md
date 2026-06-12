---
title: "C++ programming"
date: 2008-02-28
forum: Programming Talk
---

### Post by vishnumrao on 2008-02-28
Hi All,

I am very new to programming in linux. So please forgive me for my ignorance and thanks in advance for you patience.

I am trying to use linux machine at work instead of my Windows machine. Towards that goal, I need to port a inhouse developed toolkit(written in C++) that uses COM objects to linux. 

1. I am trying to use Eclipse + the CDT for this purpose. In the toolkit source code, there are .dsw files which, open up the project in MSDEV environment. How can I open up the equivalent project in eclipse? 

2. After talking to a few friends, I decided to use the Orbit2 implementation of CORBA. The original author says, it uses very little of COM object binding. How can I compile the project with the CORBA stuff?

Thanks,
Vishnu Rao

Edit: I tried this tutorial at eclipse. But it did not help me. Th e project that I created did not show any of my .cpp or .hpp files.

---

### Post by the_unforgiven on 2008-02-28
> **vishnumrao said:**
> 
1. I am trying to use Eclipse + the CDT for this purpose. In the toolkit source code, there are .dsw files which, open up the project in MSDEV environment. How can I open up the equivalent project in eclipse? 
No, eclipse + CDT doesn't support Visual Studio workspaces.
You'd have to create a new project in eclipse and manually import all the souce code. The other option would be to export a Makefile from VS and try and import that Makefile in eclipse.

Mind you, the Makefile exported by VS is not a standard UNIX makefile - it's an NMake Makefile. I don't know how effectively eclipse can handle that.

> **vishnumrao said:**
> 
2. After talking to a few friends, I decided to use the Orbit2 implementation of CORBA. The original author says, it uses very little of COM object binding. How can I compile the project with the CORBA stuff?

Thanks,
Vishnu Rao

Edit: I tried this tutorial at eclipse. But it did not help me. Th e project that I created did not show any of my .cpp or .hpp files.
You can take a look at XPCOM project:
[http://www.mozilla.org/projects/xpcom/](http://www.mozilla.org/projects/xpcom/)
It stands for Cross Platform COM - an implementation of COM that works on windows, Linux and other operating systems too.

HTH :)

---

### Post by pmasiar on 2008-02-28
Are you new to programming, or to Linux? Do you have other programing experience? Is C++ hard requirement? 

Python is much easier to learn for beginners than C++. See sticky FAQ and wiki in my sig.

---

### Post by vishnumrao on 2008-02-28
> **pmasiar said:**
> Are you new to programming, or to Linux? Do you have other programing experience? Is C++ hard requirement? 

Python is much easier to learn for beginners than C++. See sticky FAQ and wiki in my sig.

pmasiar,

Yes, C++ is a hard requirement. I am merely trying to port a toolkit written for Windows to Linux. 

I have been programming in Visual C++ for about 2 years. But totally new to programming in Linux.

the_unforgiven,

Thanks for your suggestion and will look into xpcom.

Vishnu Rao.

---

