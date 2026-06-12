---
title: "Automatically Install All Required C++ Compiling Files"
date: 2007-05-19
forum: Packaging and Compiling Programs
---

### Post by Jean Of mArc on 2007-05-19
Dear programmers,

I was wondering- every time that I start off in a fresh new installation of Linux, I always have to go through a ritual of searching for the development files and libraries required for compiling C++ files.... and usually this takes a while. I'll "./configure" a source, and it will give an error... then I search for that error to find out what to get. Then I "./configure" again, and now I have to update this, or change my $PATH for that... it's very annoying.

I was wondering if there was anything that existed, a package or whatever, that would allow me to just have everything that I'll be needing for C++ compilation installed automatically. My philosophy is that computers should be able to do as much manual labour as possible automatically- having to manually search for every error to find out how to fix it during a simple compile every time I start using a new install of linux seems a bit excessive to me.

Any ideas?

Thanks!!!

Jean Of mArc

---

### Post by RedSquirrel on 2007-05-22
In Ubuntu, for simple compilation you can just install the build-essential package:

```
sudo apt-get install build-essential
```

For nontrivial compilation, you may have to do a bit of investigation, such as reading the documentation that comes with the source code (for example, README, INSTALL) to see what you will need. If something is missing, the configure script will tell you.

On Ubuntu, the development libraries are not installed by default, but you can find them. Their package names end in "-dev".

---

### Post by u04f061 on 2007-05-29
It is my two year experience with ubuntu that never try to compile programs in ubuntu. this is the only thing i dislike in ubuntu. about 90% of the packages of mine are left uncompiled. even ./configure lists some info about the package , then i install it but when it lists some header and library files , i always fail to find them in apt.

---

### Post by kknd on 2007-06-07
There is no magic way, but (for example, apt-get build-dep gaim will download all the libs for building gaim (pidgim now)). This is very helpfull for build new versions of programs that arent packaged yet.

---

