---
title: "Trying to learn D, simple programs give segfaults"
date: 2008-10-15
forum: Programming Talk
---

### Post by Starlight on 2008-10-15
Hi! I found out about the D programming language today, and it made me curious, so I wanted to try some simple programs in it. However, it seems that whenever I try to display some variable on the screen, the program segfaults... for example, this simple program works well:

```

import std.stdio;

void main() {
  writefln("Hello World!");
}

```
I save it in hello.d, compile with gdc hello.d -o hellod, and run with ./hellod and it correctly displays "Hello World!". But when I want it to display some variable, like this:

```

import std.stdio;

void main() {
  int i = 1;
  writefln("Hello World! %d", i);
}

```
the compiler doesn't give any errors or warnings, but the program gives me a Segmentation Fault error.

If I add the line writefln("Meep!"); before the Hello World one, it displays Meep! and then segfaults, which shows that the problem is with the last line...

I looked at some D tutorials and examples, and I think that I'm doing everything correctly. I even tried compiling and running some examples from tutorials, and they segfault as well when trying to display a variable on the screen. And it happens with all types of variables... Can someone help me make it work? I'm really curious about the D programming language, so I'd love to learn at least the basics :)

---

### Post by geirha on 2008-10-15
Indeed, they both compile and run for me, but running them through valgrind shows they got memory leaks. Since a simple search indicates that those programs should be good d code, it seems like it must be a bug with the compiler or the libraries.

There's a bug report on it on launchpad [https://bugs.launchpad.net/ubuntu/+source/gdc-4.2/+bug/235955](https://bugs.launchpad.net/ubuntu/+source/gdc-4.2/+bug/235955)

---

### Post by Starlight on 2008-10-15
Thanks for the link! I hope they fix it soon. And in the meantime, I can try using gdc 4.1 :)

---

