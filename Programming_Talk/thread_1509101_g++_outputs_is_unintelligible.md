---
title: "g++ outputs is unintelligible"
date: 2010-06-13
forum: Programming Talk
---

### Post by Frozenport on 2010-06-13
I installed a copy of Ubuntu Server for my own private, edumacational reasons. I installed enlightenment and am using Eterm. I am having a little annoyance with g++ output. Specifically some characters, the nonstandard set, appear as dotted boxes. I have only been using English. Now, I am unsure what package will fix my problem.

---

### Post by Frozenport on 2010-06-19
Any hope?

---

### Post by lisati on 2010-06-19
Edumacational? Hmmmmmm......

Is this a programming question or a server question?

---

### Post by Frozenport on 2010-06-19
The platform is ubuntu server. I installed it on a vm and am trying to use it as a test server for some socket server stuff I wrote.The code I wrote is from windows and I am porting it to linux.

_This is not a programming question_. This is me trying to read what g++ spits out. Hell, this has been irking me so much I am current using another distro. Although I want to switch back because vmware makes a very efficient installation of ubuntu.

---

### Post by lisati on 2010-06-19
Well, since it's got nothing to do with programming, do you mind if I remove all the references to g++? :) (Just kidding!)

If it's a server question, then this should be in the server section. Since you are *porting code from Windows to Linux* I've moved this to "Programming Talk"

---

### Post by ibuclaw on 2010-06-19
Why are you using Eterm?

There are other terminal emulators out there that could output the symbols you need to see correctly. :)

---

### Post by trent.josephsen on 2010-06-19
GCC's output is in the default locale, which is probably UTF-8 or ISO-8859-1.  You need a font that supports it and a terminal that knows how to use it.  Eterm is probably adequate, but I don't really know.  Xterm works.  DejaVu Sans Mono is a nice monospaced font that works with UTF-8.

*Edit:*  Or you could export LC_ALL=C, which will make gcc output in the C standard character set.

---

