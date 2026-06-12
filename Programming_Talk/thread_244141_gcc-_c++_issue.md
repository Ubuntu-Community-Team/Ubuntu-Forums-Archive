---
title: "gcc- c++ issue"
date: 2006-08-26
forum: Programming Talk
---

### Post by human42 on 2006-08-26
First, I would like to say that i Love ubuntu. (native support for my laptop's wireless card was what sold me.)
But i have a bit of a problem. 
When i first set it up, GCC was not installed. I tried compiling from source, but that didn't work, i'll go into that later.
Using applications- - add/remove, i installed some additional software, including emacs and several other programs. Shortly afterwards, i tried gcc again and- wallah! it was there. I assumed it was a dependancy that came with one of the programs i downloaded.
(note- the version of gcc thus installed is 4.0.3.)
the first problem that arose was this: I typed a standard hello world program:
#include <stdio.h>
int main(int argc, char **argv)
{
printf("hello world\n");
return 0;
}
and saved it as hello.c, gcc hello.c -o hello worked fine.
but then i saved it as hello.cpp, and ran gcc hello.cpp -o hello
and got the following error:
gcc: installation problem, cannot exec cc1plus: no such file or directory
(note: i'm not sure if the syntax of my program is correct for c++, rather than c, but that would not explain the error.)
So i downloaded the latest stable gcc, 4.1.1, ./configure, make bootstrap.
it gave me an error message: does not have makeinfo, part of texinfo.
So i download texinfo, ./configure, make, make install. texinfo did not compile because of and undefined variable. (I don't recall exactly what thevariable was).

So- sorry about the long post, BTW- am i making a dumb mistake regarding how to compile a c++ program, or do i need to reinstall gcc,and if so how should i go about that?

additionally, when attempting to install LZO library 2.02, it gave me an error message something like:
checking to see if cpp is sane...
error: cpp is not sane.
i assumed that that problem would also be solved if i reinstalled gcc?

Sorry about the long, probably dumb post, i am a n00b, and i apologize.
I do appreciate any advice.
love and peace
-J (H42)

---

### Post by toojays on 2006-08-26
Two mistakes:

1) To compile C++ files, it's like "g++ -o hello hello.cpp".

2) It doesn't sound like you have g++ installed anyway. What you should do is install a package called "build-essential", which will install the basic build toolchain for you properly.

---

### Post by human42 on 2006-08-26
thank you. and no, i do not have g++ installed. So that should fix it, thanks!
J (H42)

---

