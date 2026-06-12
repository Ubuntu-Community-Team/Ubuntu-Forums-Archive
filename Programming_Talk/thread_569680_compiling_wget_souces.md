---
title: "compiling wget souces"
date: 2007-10-07
forum: Programming Talk
---

### Post by castudil on 2007-10-07
Hi there:


I have access to an account, and I want to use wget (Or lynx) from there. 

The problem: neither wget nor lynx are intalled there.

I tried to install wget from the sources but no C compiler is installed on the machine.

 I though in some alternatives:

+ an application similar to lynx or wget ready to use (standalone without compilation)
+ install a c compiler in my account and compile the wget sources with that.

I don't know how to do that so I ask for help, maybe if you know the right application, compiler, etc... anyone know a solution for my problem?

Thanks a lot.

---

### Post by dwhitney67 on 2007-10-07
You can "wget" all day long source packages, but without the a compiler you will never be able to compile them.  (Btw, you will need a compiler to build gcc... I know... it seems strange!)

Thus I would focus on getting a compiler installed onto your system.  Consult with the system administrator on installing that package.  And while you are at it, have him/her install wget.

Alternatively, if you have a personal system with a similar architecture to the other one you access, it is possible to compile source code on your system and then transfer the binaries to the other.  The only thing to be wary about is whether both systems have compatible versions of glibc and gcc libraries.

---

### Post by castudil on 2007-10-07
Thank you for you answer, I will see if that works

---

### Post by gnusci on 2007-10-08
Which system do you have?... I think it is very simply to compile:

[http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)
[ftp://ftp.gnu.org/pub/gnu/wget/wget-1.10.tar.gz](ftp://ftp.gnu.org/pub/gnu/wget/wget-1.10.tar.gz)

I would recommend you to get GCC installed:

[http://gcc.gnu.org/](http://gcc.gnu.org/)

so you can also compile Lynx:

[http://lynx.browser.org/](http://lynx.browser.org/)

---

### Post by castudil on 2007-10-08
Hi fellows:

I have been thinking on my problem and now I have reach to the following facts:

+ there is one linux server to want I can connect in the university. it doesn't have gcc neither wget.

+ there is  a computer there wich I have access. It has Windows installed. I have installed in that machine a ssh server, I can connnect to that windows machine within the campus.

my idea is:

- install wget in the windows machine,
- connect to the linux server with my account
- connect from there to the windows machine
- use wget!

do these steps have any meaning to you?
from your point of view, are there better ways?

Additionally I have found precompiled version of gcc
[http://gcc.gnu.org/install/binaries.html](http://gcc.gnu.org/install/binaries.html) 
but none is suitable for this linux server.

thank you!

---

### Post by xtacocorex on 2007-10-08
There is a version of wget for Windows.

---

