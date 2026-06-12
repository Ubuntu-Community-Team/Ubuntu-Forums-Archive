---
title: "gcc is the fritz :("
date: 2007-03-18
forum: Programming Talk
---

### Post by MarieTeresa on 2007-03-18
Hey All,
I think I would be significantly happier with my life if gcc would just work. Whenever I try to compile anything, I get a message 

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Which is lame sauce. I've tried marking gcc and libgcc for reinstallation in synaptic, but running that hasn't fixed anything either :(

Anyone know what's wrong?

---

### Post by MarieTeresa on 2007-03-18
Let's say RTF...F?
One post down I see
"sudo apt-get install build-essential" and all my problems are solved.
so uh... n/m. :)

---

### Post by WW on 2007-03-18
You are not the first to have this problem, and you won't be the last. :)

There should be a sticky thread with the subject: "Can't compile C/C++? Install the package **build-essential**"

---

### Post by Lux Perpetua on 2007-03-19
> **WW said:**
> You are not the first to have this problem, and you won't be the last. :)

There should be a sticky thread with the subject: "Can't compile C/C++? Install the package **build-essential**"Actually, we really should have a FAQ sticky in this forum because there is a small subset of issues that just keeping coming up, this being a great example.

---

### Post by j_g on 2007-03-19
Or maybe Ubuntu needs a "Standard C++/C development" package that doesn't install anything itself, per se, but does "depend" upon gcc, build-essentials, and anything else that would be expected in a practical C++/C development environment. In this way, a developer would install one package instead of chasing down several packages just to compile even a "hello world" program.

---

### Post by Lux Perpetua on 2007-03-19
Doesn't build-essential already cover that? It doesn't include the man pages, but it includes the compilers themselves.

---

### Post by WW on 2007-03-19
Yes, **build-essential** is a meta-package. It depends on gcc, g++, make, dpkg-dev, and either libc6-dev or libc-dev. (Most folks probably don't need dpkg-dev.)  Installing build-essential is sufficient to compile a "Hello, world" program in C or C++.

As Lux points out, build-essential does not include the manpages for the C/C++ libraries,so you will probably also want to install **manpages**, **manpages-dev**, and **manpages-posix-dev**. (This tip taken from lnostdal's guide to programming in Ubuntu: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/))

---

### Post by Wybiral on 2007-03-19
I added it to the "How to start programming - guides and links for many languages" sticky thread a while ago in the C++ section: [http://www.ubuntuforums.org/showthread.php?t=333867](http://www.ubuntuforums.org/showthread.php?t=333867)

But I don't think people look for that kind of stuff first...

A simple "gcc help compile" brings up a ton of threads that mention it. But people would probably rather ask first, search later.

---

