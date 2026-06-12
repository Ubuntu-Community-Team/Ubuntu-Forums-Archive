---
title: "Natty Narwhal: cannot find -lgcc_s (broken gcc/g++)"
date: 2011-05-05
forum: Programming Talk
---

### Post by genjix on 2011-05-05
Hey,

I upgraded to Natty Narwhal and the compiler is broken. :(  not being able to compile = expensive paper-weight.

```
$ gcc blaa.c
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
```

It can work if I do:

```
$ g++ blaa.cpp -L /usr/lib/gcc/i686-linux-gnu/4.6/
```

Any ideas how to get this to work?

---

### Post by slavik on 2011-05-05
use g++ to compile C++ code, not gcc. gcc is for C.

---

### Post by genjix on 2011-05-06
> **slavik said:**
> use g++ to compile C++ code, not gcc. gcc is for C.

That has nothing to do with the errors I'm getting with both g++/gcc. The linker is failing to find gcc_s.

```
genjix:/tmp$ echo "int main() { return 0; }" > main.c && gcc main.c 
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
genjix:/tmp$ echo "int main() { return 0; }" > main.cpp && g++ main.cpp
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
genjix:/tmp$ echo "int main() { return 0; }" > main.c && gcc main.c -L /usr/lib/gcc/i686-linux-gnu/4.6/
genjix:/tmp$ echo "int main() { return 0; }" > main.cpp && g++ main.cpp -L /usr/lib/gcc/i686-linux-gnu/4.6/

```

WTH? Why is Natty Narwhal so broken?

---

### Post by dwhitney67 on 2011-05-06
EDIT:

Never mind what I wrote below.  Can you verify that you have the following directory on your system: /usr/lib/gcc/i686-linux-gnu/4.6/


--------------------------------------------------

Try running /sbin/ldconfig, as shown below:
```

sudo /sbin/ldconfig -v | grep "/usr/lib/gcc/i686-linux-gnu/4.6"

```
What I am interested in knowing is whether the path above is configured in your ld-cache.  How did you install the development tools?

---

### Post by genjix on 2011-05-06
Hey,

Thanks for your reply. The directory did indeed exist with the libgcc_s.so inside it.

But I use this computer for work so I simply wiped it clean and reinstalled Ubuntu... Need to code and that's the path of least resistance.

---

### Post by dwhitney67 on 2011-05-06
> **genjix said:**
> Hey,

Thanks for your reply. The directory did indeed exist with the libgcc_s.so inside it.

But I use this computer for work so I simply wiped it clean and reinstalled Ubuntu... Need to code and that's the path of least resistance.

Did you install the package "build-essential"  (maybe plural with an 's' at the end)?

---

### Post by olness on 2011-05-09
I upgraded from 10.10 to 11.04 and the link to libgcc_s was broken in the upgrade.
The bad link was:  /lib/i386-linux-gnu/libgcc_s.so.1
The correct lib was:  /usr/lib/gcc/i486-linux-gnu/3.4.6/libgcc_s.so
I re-created the link and this fixed my problem.

sudo ln -s  /lib/i386-linux-gnu/libgcc_s.so.1  /usr/lib/gcc/i486-linux-gnu/3.4.6/libgcc_s.so

---

### Post by caspin on 2011-05-11
I was having genjix's same problem.  I could compile on maverick, but was unable to do so on natty.  ld was unable to find libgcc_s.

The root of the problem was the libgcc_s package failed to upgrade.  I had been using a ppa repo for the latest gcc when I was using maverick.  Unfortunately the libgcc_s package had a version string that was newer than natty's version of libgcc_s.

The fix was simple.  download maverick's default libgcc_s from packages.ubuntu.com and install it with `dpkg -i`.

---

