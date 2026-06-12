---
title: "&#12304;how to compile 32-bit apps using autoconf&#12305;"
date: 2012-02-13
forum: Packaging and Compiling Programs
---

### Post by zcnnbb on 2012-02-13
When calling ./configure, what param should I use to compile a 32bit app under 64bit os?

In fact, I searched the web before, someone says that I should add arguments like --host=i386-linux or --build=xxxxxx

I have tried both params, but it doesn't work.

Thx!

---

### Post by oldos2er on 2012-02-13
Moved to Packaging and Compiling Programs.

---

### Post by SevenMachines on 2012-02-13
This kind of thing often works for simple programs
```
$ ./configure CC='gcc -m32' CXX='g++ -m32'
```

Cross compiling can be a pain though, a virtual system is generally easier I find. Ubuntu does have i386 lib installation enabled these days so it might be much better.

---

