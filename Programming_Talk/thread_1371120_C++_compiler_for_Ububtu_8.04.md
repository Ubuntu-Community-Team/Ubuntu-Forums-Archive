---
title: "C++ compiler for Ububtu 8.04"
date: 2010-01-03
forum: Programming Talk
---

### Post by Don Quixote on 2010-01-03
IS there any C++ compiler that runs in Ubuntu 8.04? I tried turbo C++,it didn't work.I even tried Dev C++.The program was installed and even compiled but didn't run.Someone plz help me.

---

### Post by kjohri on 2010-01-03
sudo apt-get install g++

---

### Post by lovinglinux on 2010-01-03
> **kjohri said:**
> sudo apt-get install g++

I think is better to run:

```
sudo apt-get build-essential
```

> 
This package contains an informational list of packages which are
considered essential for building Debian packages.  This package also
depends on the packages on that list, to make it easy to have the
build-essential packages installed.

Anyway, you should read the stickies of the [Development & Programming](http://ubuntuforums.org/forumdisplay.php?f=310) and [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39)  sub-forums. BTW, programming questions are better placed there.

---

### Post by GregBrannon on 2010-01-03
Yes, the terminal commands and reading the cited stickies will help.  Based on the actions already taken, I'm guessing the OP is interested in more than just a compiler, perhaps a C++ IDE.

Don Q, you will find much discussion and more opinions than you'll want on which IDE is best for specific tasks in the Programming forums and at other online programming resources.

When you've narrowed down your search and want help making the final selection or have specific questions about the many fine IDEs available, ask more questions in the Programming forum.

---

### Post by bapoumba on 2010-01-03
Moved to PT.

---

### Post by Can+~ on 2010-01-03
> **Don Quixote said:**
> IS there any C++ compiler that runs in Ubuntu 8.04? I tried turbo C++,it didn't work.I even tried Dev C++.The program was installed and even compiled but didn't run.Someone plz help me.

Oh the classical IDE == compiler dilemma.

Compiler: It takes the source and compiles it (duh) into binary. Mostly a command line utility.
IDE: Built over the compiler to provide an easier interface.

You can compile the typical helloworld example directly from the terminal (once build-essential is installed, read the above responses):

```
g++ helloworld.cpp -o helloworld
./helloworld
```

And for an IDE, install geany.

```
sudo apt-get install geany
```

---

