---
title: "compiling dev c++"
date: 2008-02-28
forum: Packaging and Compiling Programs
---

### Post by DAC1138 on 2008-02-28
I've searched the web and haven't found any definitive guide to compile and install dev c++. I just see people posting replies, "this app is better," or "this app is native to linux and windows and just as good." I don't want those replies here. Sorry. I want people who are willing to help.

I've tried anjuta, netbeans, geany, code::blocks, and kdevelop. I have a goal: I want to install dev c++. Code::blocks is nice, but steady stable releases are not very steady.

Dev c++ has a native linux port, but any documentation on how to compile it cannot be found. Can someone show me where to begin and help guide me through this?

---

### Post by Runn3r.cze on 2008-03-02
usually you need just  three commands to compile from source...
download the package and unpakc it, do to its folder and type
```
./configure
```
```
make
```
```
sudo make install
```

this is the normal way to install from source, but i've never tried to install dev c++ on linux, so i'm not sure if it works or not...

---

### Post by DAC1138 on 2008-03-08
I've compiled apps before, and dev c++ is unlike anything I've ever compiled. From the looks of it you need to compile the interface separate from the compiler, and then there looks like a third app to compile. Problem is, there's no way to ./configure or make the programs. This is why I'm stumped.

---

### Post by WW on 2008-03-08
According to the Bloodshed web page, [Dev-C++](http://www.bloodshed.net/dev/devcpp.html) is written in [Delphi](http://en.wikipedia.org/wiki/Borland_Delphi), a Pascal-like language from [Borland](http://www.borland.com).  You'll need a Delphi compiler to build it; maybe [Lazarus](http://www.lazarus.freepascal.org)?

---

### Post by Can+~ on 2008-03-08
> I've tried anjuta, netbeans, geany, code::blocks, and kdevelop. I have a goal: I want to install dev c++. Code::blocks is nice, but steady stable releases are not very steady.

Try eclipse with C/C++ plugin, both things on the repositories. I know you told everyone not to give you more substitutes, but, if everything else fails... Eclipse! Besides, eclipse is java, so you could install it on any platform when you need a proper IDE.

---

### Post by Jinx-Wolf on 2008-03-11
I'm also trying to get dev-c++ for Linux, but haven't had much luck so far.

However, dev-c++ for Windows installs fine through WINE, and is working perfectly (so far).

I still want to try and get the Linux version working though.

---

### Post by DAC1138 on 2008-03-11
> **Jinx-Wolf said:**
> I'm also trying to get dev-c++ for Linux, but haven't had much luck so far.

However, dev-c++ for Windows installs fine through WINE, and is working perfectly (so far).

I still want to try and get the Linux version working though.

Yeah, I know that much, but it's kind of useless when you compile the apps and it comes out as a windows binary file :\ Guess it's okay for multiplatform development.

---

