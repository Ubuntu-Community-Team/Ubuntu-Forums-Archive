---
title: "Cannot compile any c program with gcc"
date: 2007-11-01
forum: Packaging and Compiling Programs
---

### Post by mickey78 on 2007-11-01
Hey guys.

I am a bit new to ubuntu, and i tried to compiled this little program last night to make sure everything is working on my system. I run 7.10 server edition.

#include < stdio.h >

void main()
{
    printf("\nHello World\n");
}


with gcc, but it kept tellming me that error:  stdio.h : No such file or directory

I installed the "build-essential" package, and the stiod.h file is indeed in the /usr/include folder... I'm just a bit confuse what to try next.

Thansk for your help.

---

### Post by jaakan on 2007-11-01
what -dev's did you install?

like libc6-dev and libstdc++...-dev?

did you also install g++?

---

### Post by mickey78 on 2007-11-01
this is what get installed in the "build-essential" package

The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc gcc-4.1 gcc-4.1-base libc6-dev libstdc++6-4.1-dev
  linux-libc-dev make patch

---

### Post by mickey78 on 2007-11-01
you know what, i feel like a noob now... 

i had spaces near the brackets... stupid mistake, thanks anyways

---

### Post by HokeyFry on 2007-11-01
nah dont feel like a noob, everyone makes small mistakes in computers. i like to call it learning, myself lol

---

### Post by jaakan on 2007-11-02
It's Cool.
Happy compiling.

---

