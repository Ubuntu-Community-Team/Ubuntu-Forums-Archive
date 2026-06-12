---
title: "Installed bulid-essential package, still stdio.h is missing?"
date: 2007-07-03
forum: Programming Talk
---

### Post by Strid on 2007-07-03
I want to compile some code written in C. It think I've installed every package related to C I could find. Especially, I took care that build-essential is installed, because that is what I found in about every thread (seems to be a lot!) where other guys have the same problem.

```
anders@fx60:~$ cd Desktop/
anders@fx60:~/Desktop$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anders@fx60:~/Desktop$ gcc -o test HelloWorld.c
HelloWorld.c:1:20: error:  stdio.h: No such file or directory
HelloWorld.c: In function ‘main’:
HelloWorld.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
HelloWorld.c:4: warning: return type of ‘main’ is not ‘int’
anders@fx60:~/Desktop$ cat H
HelloWorld.c   HelloWorld.c~  Hold.txt~      
anders@fx60:~/Desktop$ cat HelloWorld.c
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}
anders@fx60:~/Desktop$ 

```

So build-essential is installed and I'm just trying to compile a sample "hello world" I snatched off a tutorial. What other packaged could I be missing? I even tried to reboot after installing build-essential. Still no dice. :(

This is on Feisty btw.

Cheers from a guy whos fluent in Python and Pascal but wants to get into C like all his cool mates. :popcorn:

---

### Post by runningwithscissors on 2007-07-03
There shouldn't be a space between the '<' character and stdio.h.

---

### Post by lisati on 2007-07-03
I had the same problem, also doing a "Hello world" program. If memory serves, I did something like this:
```

sudo apt-get remove gcc
sudo apt-get autoremove
sudo aptitude install gcc

```

Good luck!

---

### Post by lisati on 2007-07-03
> **runningwithscissors said:**
> There shouldn't be a space between the '<' character and stdio.h.
Well spotted! I had a similar message even though I didn't have the spurious space

---

### Post by Strid on 2007-07-03
> **runningwithscissors said:**
> There shouldn't be a space between the '<' character and stdio.h.

Ahh, thank you buggy C tutorial!! :p

Compiles like a charm without the space, lol, thank you. Very well spotted indeed!

---

### Post by Strid on 2007-07-03
[http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/](http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/)

This very good tutorial just have those spurious spaces everywhere!

---

### Post by jap1968 on 2007-08-28
The only package that you need to install is "**libc6-dev**", which contains the files with the standard C libraries.

---

### Post by fct on 2007-08-29
build-essential already installs libc6-dev:

```
$ apt-cache show build-essential
Package: build-essential
Priority: optional
Section: devel
Installed-Size: 48
Maintainer: Matthias Klose <doko@debian.org>
Architecture: i386
Version: 11.3
Depends: **libc6-dev** | libc-dev, gcc (>= 4:4.1.1), g++ (>= 4:4.1.1), make, dpkg-dev (>= 1.13.5)
```

---

