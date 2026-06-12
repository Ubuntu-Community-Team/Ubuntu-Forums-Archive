---
title: "Ubuntu 8.04 + Intel C++ Compiler 10.1"
date: 2008-07-22
forum: Programming Talk
---

### Post by dribeas on 2008-07-22
I have just downloaded and installed Intel ICPC (free for non-commercial use). I already have g++ 3.4 and g++ 4.2 installed. It seems as if intel compiler does not have its own STL but uses g++'s (in this case 4.2, which is the default compiler) and does not quite like that version:

```

$ source iccvars.sh # load Intel compiler variables
$ icpc -o hello hello.cpp # plain hello world, includes iostream
/usr/include/c++/4.2.3/ext/atomicity.h(51): error: identifier "__sync_fetch_and_add" is undefined
    { return __sync_fetch_and_add(__mem, __val); }
             ^

/usr/include/c++/4.2.3/ext/atomicity.h(55): error: identifier "__sync_fetch_and_add" is undefined
    { __sync_fetch_and_add(__mem, __val); }

```

Has anyone run into this problem? solved it? Thanks in advance.

   David

P.S. This does compile fine:
```

int main() {}

```
But as soon as I add #include <iostream> I get the previous error.

---

### Post by dwhitney67 on 2008-07-22
Are you sure that 'icpc' is the C++ compiler?  It could be the compiler for C code, similar to how 'gcc' is used for C, and 'g++' is used for C++.

---

### Post by samjh on 2008-07-22
> **dwhitney67 said:**
> Are you sure that 'icpc' is the C++ compiler?  It could be the compiler for C code, similar to how 'gcc' is used for C, and 'g++' is used for C++.

icc = C
icpc = C++


@ dribeas:

Have a look at
[http://softwarecommunity.intel.com/isn/Community/en-US/forums/thread/30251474.aspx](http://softwarecommunity.intel.com/isn/Community/en-US/forums/thread/30251474.aspx)
[http://bugs.gentoo.org/show_bug.cgi?id=201596](http://bugs.gentoo.org/show_bug.cgi?id=201596)

---

