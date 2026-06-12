---
title: "Is there a windowz compiler (cpp) that works thrugh wine?"
date: 2008-11-08
forum: Programming Talk
---

### Post by Pagh on 2008-11-08
Hey I was thinking of compiling a program I made for both winblowz n' linux.
But my problem is that I don't have a computer that is running windows so I'm thinking - is it possible to compile a program with a windows compiler through wine??

Ps. I'm only using the standard c++ library's like iostream and csdlib.   

Any help would be appreciated both concerning if it even possible but also on what compiler to use if it is!

---

### Post by slavik on 2008-11-08
look at mingw :)

---

### Post by WW on 2008-11-08
You are talking about "cross-compiling".  I show a simple example of cross-compiling a program in post 6 of [this thread](http://ubuntuforums.org/showthread.php?t=724495).  The example is C, but the mingw32 packages also provide a C++ cross-compiler.

---

### Post by Ferrat on 2008-11-08
from what I've heard code::blocks for windows should work great with wine and with that you could develop on Linux in code::blocks and then for Widows stuff just compile in the win version? 

this is hearsay(haven't tried it myself) but worth a look?

---

### Post by LaRoza on 2008-11-08
> **Pagh said:**
> Hey I was thinking of compiling a program I made for both winblowz n' linux.
But my problem is that I don't have a computer that is running windows so I'm thinking - is it possible to compile a program with a windows compiler through wine??

Ps. I'm only using the standard c++ library's like iostream and csdlib.   

Any help would be appreciated both concerning if it even possible but also on what compiler to use if it is!

You can use this in wine: [http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable)

In fact, you can use it on a flash drive on any Windows computer, or Linux computer with Wine. It may not be the best solution, cross compiling seems to be what you want, but it may be useful none the less.

It uses mingw.

---

### Post by samjh on 2008-11-09
There is no need to use wine for that.

Just install Mingw:
```
sudo apt-get install mingw32
```

To compile, use i586-mingw32msvc-g++ instead of just g++.  They accept the same parameter options (-O2, -Wall, etc.).

I have used Mingw under Wine (via Dev-C++), but it doesn't work properly.  Resulting software almost always results in a segfault (or in Windows, the "an error has occurred... yak yak yak" message).

---

### Post by Pagh on 2008-11-09
Thanks a lot it seems to be possible after all:-D I'll try a couple of the different solutions.

Edit: @samjh your solution worked perfectly Thanks a lot!!

---

