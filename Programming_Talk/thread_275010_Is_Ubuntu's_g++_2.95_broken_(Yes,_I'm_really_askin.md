---
title: "Is Ubuntu's g++ 2.95 broken? (Yes, I'm really asking this)"
date: 2006-10-10
forum: Programming Talk
---

### Post by jmillikin on 2006-10-10
Before I begin, yes, I really am asking about a possible bug in a 5 year old compiler.

I'm trying to develop a library which will be used on a few systems, some of them running very old versions of G++. I'd obviously rather use Ubuntu as a main development machine, but to do that I need to be able to compile with G++ 2.95. I've found that the G++ 2.95 packaged for Ubuntu seems to be different from that on the other systems, and was hoping to find either a workaround or solution:

Basically, exceptions don't work. As soon as something is thrown, the program aborts. The following test case passes on the target systems, but not on my desktop - and until I get it working on my desktop, I can't use it for development.

```
#include <cstdio>

int main() {
  try {
    throw 0;
  } catch (...) {
    printf ("Passed!\n");
    return 0;
  }
}
```

EDIT: removed confusing throw specifier

---

### Post by po0f on 2006-10-10
jmillikin,

I'm not too familiar with the syntax of how to declare what kind of exceptions a function can throw, but according to [this](http://www.cplusplus.com/doc/tutorial/exceptions.html) (scroll to the very bottom), a function declared `int foo() throw();` can throw no exception.  Maybe that's why your sample prog is crashing?  ;)

---

### Post by jmillikin on 2006-10-10
It's not supposed to throw the exception out of the function, that was just a tiny sanity check I made. The exception is supposed to be caught by the catch(...), which prints out that the program passed.

---

### Post by ra.rochford on 2006-12-06
Unfortunately it seems so! 

I've just encountered the same problem in Ubuntu 6.06 with an almost identical program. (Wish I had found this post first.)

I have verified the program works on Hoary Ubuntu 5.04 so surely it *must* be a regression somewhere....


```
#include <iostream>

int main()
{
    try
    {
        throw int(1);
    }
    catch (...)
    {
        std::cerr << "caught it!" << std::endl;
    }
}
```

---

### Post by ra.rochford on 2006-12-06
More info.....

Here is running the above program from the commandline

```

$ ./a.out
Aborted (core dumped)

```

I copied across the library libstdc++-libc6.2-2.so.3 from my Hoary 5.04 machine and ran the above program

```

$ LD_PRELOAD=./libstdc++-3-libc6.2-2-2.10.0.so ./a.out
caught it!

```

Does this mean it's a problem with libstdc++-libc6.2-2.so.3?

Is this in the package libstdc++2.10-dev?

---

### Post by ra.rochford on 2006-12-06
I've added this bug....

[https://bugs.launchpad.net/distros/ubuntu/+source/gcc-2.95/+bug/74619](https://bugs.launchpad.net/distros/ubuntu/+source/gcc-2.95/+bug/74619)

---

### Post by -Rick- on 2006-12-06
I vaguely remember that older GCC's didn't enable exception support by default, maybe try the -fexceptions cflag?

---

### Post by ra.rochford on 2006-12-10
> **-Rick- said:**
> I vaguely remember that older GCC's didn't enable exception support by default, maybe try the -fexceptions cflag?

```

$ g++-2.95 -fexceptions x.cc
$ ./a.out
Aborted (core dumped)

```

I've tried this and it's still not working. I would have been surprised if it did work though - it would have been different from every other g++-2.95 machine i've tried. (Solaris 8, Solaris 10, other Linux's. The list goes on.)

---

