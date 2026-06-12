---
title: "Ubuntu 64 bit compiling question"
date: 2011-10-24
forum: Programming Talk
---

### Post by luishasbon on 2011-10-24
Greetings respected comunity.

I'm new to 64 bit computing, I just installed ubuntu 10.04 64 bit edition, I was wondering how to compile with gcc or g++ 32 bit apps in ubuntu 64 bit, which package do I need for this? which libraries? If you have time, please, also tell me, the packages that appear at the universe using apt-get in the terminal, all of them are configured or compiled for 64 bit architecture? thank you.

---

### Post by Bachstelze on 2011-10-25
You need at least gcc-multilib, plus 32-bit versions of the libraries your program uses, if any. gcc-multilib installs some, you will also find a lot of them in ia32-libs (but if you use an "exotic" library, you might have to install a 32-bit version of it manually).

How to compile depends on the build system your program uses. For simple programs, using the -m32 flag should be sufficient.

```
gcc -m32 -o foo foo.c
```

---

### Post by gnometorule on 2011-10-25
Embarrassing as it is, I had assumed the standard gcc handles 64 bits, sort of by default flipping on the most modern system architecture. Do you happen to have a link that discusses this? It's not in the old gcc book, for all I know.

---

### Post by Bachstelze on 2011-10-25
> **gnometorule said:**
> Embarrassing as it is, I had assumed the standard gcc handles 64 bits, sort of by default flipping on the most modern system architecture. Do you happen to have a link that discusses this? It's not in the old gcc book, for all I know.

Excuse me? On a 64-bit system, gcc does compile 64-bit code by default, that's why you have to pass the -m32 flag if you want 32-bit code...

---

### Post by gnometorule on 2011-10-25
Could you instead add a link how to learn to read carefully and properly? :)

---

### Post by 11jmb on 2011-10-25
[http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html](http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html)

---

