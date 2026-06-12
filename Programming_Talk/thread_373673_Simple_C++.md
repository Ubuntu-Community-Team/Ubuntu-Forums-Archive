---
title: "Simple C++"
date: 2007-03-01
forum: Programming Talk
---

### Post by iWill on 2007-03-01
What would you guys recommend for just some simple C++. I've installed Anjunta but I still prefer something along the lines Dev-C++ on windows..

---

### Post by Wybiral on 2007-03-01
I used to use Code::Blocks in Windows... It's a lot like dev-c++

I believe it is available for Linux.

---

### Post by iWill on 2007-03-01
> **Wybiral said:**
> I used to use Code::Blocks in Windows... It's a lot like dev-c++

I believe it is available for Linux.
Not out for PowerPC....does anyone know a good compiler for powerpc linux similar to dev-c++?

---

### Post by iWill on 2007-03-01
Anyone?

---

### Post by lnostdal on 2007-03-01
> **iWill said:**
> What would you guys recommend for just some simple C++. I've installed Anjunta but I still prefer something along the lines Dev-C++ on windows..

here's the setup i use:
[http://nostdal.org/~lars/writings/ubuntu-programming1.pdf](http://nostdal.org/~lars/writings/ubuntu-programming1.pdf)
[http://nostdal.org/~lars/writings/ubuntu-programming2.pdf](http://nostdal.org/~lars/writings/ubuntu-programming2.pdf)
[http://nostdal.org/~lars/writings/ubuntu-programming3.pdf](http://nostdal.org/~lars/writings/ubuntu-programming3.pdf)

(currently upgrading the last one to show how-to of glade-3 instead of glade-2)

it will work under ppc also .. heck; it'll even work under win32 ;)

---

### Post by iWill on 2007-03-02
> **lnostdal said:**
> here's the setup i use:
[http://nostdal.org/~lars/writings/ubuntu-programming1.pdf](http://nostdal.org/~lars/writings/ubuntu-programming1.pdf)
[http://nostdal.org/~lars/writings/ubuntu-programming2.pdf](http://nostdal.org/~lars/writings/ubuntu-programming2.pdf)
[http://nostdal.org/~lars/writings/ubuntu-programming3.pdf](http://nostdal.org/~lars/writings/ubuntu-programming3.pdf)

(currently upgrading the last one to show how-to of glade-3 instead of glade-2)

it will work under ppc also .. heck; it'll even work under win32 ;)
Lol Ok....isn't there just one simple app that would let me debug one simple .cpp file?
Everything seems to be so much of a hassle on linux

---

### Post by haricharan on 2007-03-02
Just doing it in command line is easier......using gcc for C programs and g++ for C++ programs.
However to compile u need the gcc and g++. Install build-essential for this
```
sudo apt-get install build-essential
```

---

### Post by Enselic on 2007-03-02
> **iWill said:**
> Lol Ok....isn't there just one simple app that would let me debug one simple .cpp file?
Everything seems to be so much of a hassle on linux

For debugging, checkout ddd or Kdbg.

When you compile, make sure you compile with the -g option if you use a command line interface.

---

